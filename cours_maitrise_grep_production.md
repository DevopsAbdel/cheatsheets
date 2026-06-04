# Cours Complet : Maîtrise de la commande Grep en Production (DevOps & SysAdmin)
## Résolution d'Incidents de la Gestion Manuelle à l'Analyse Avancée des Logs

---

## Module 1 : Le Contexte Réel en Production – Le Cauchemar des Fichiers de 15 Go

Dans le monde professionnel de la gestion d'infrastructures Linux (Production) depuis plus de 15 ans, un scénario de discorde classique se répète inlassablement entre les équipes de **Support Application** et les **Développeurs** (ceux qui écrivent le code).

### Le Problème Traditionnel (L'approche inefficace) :
1. L'application tombe en panne ou subit une coupure (Outage).
2. Le développeur contacte le support et demande : *"Je veux les logs"*.
3. L'équipe support ou DevOps cherche le fichier sur le serveur et découvre qu'il pèse **10 Go ou 15 Go**.
4. **Perte de temps massive :** Télécharger un fichier de 15 Go depuis le serveur pour le donner au support, qui le transmet ensuite au développeur, consomme énormément de bande passante et de temps, retardant la résolution de l'incident. 
5. Au final, le développeur va simplement chercher les erreurs (`errors`) dans ce fichier pour identifier la cause (Problème de base de données ? Manque de ressources ? Problème d'API ?).

### La Solution Ingénierie :
L'idéal est de disposer d'un système de gestion centralisée des logs (Centralized Logging Dashboard comme ELK ou Grafana Loki) accessible via une interface web sans rien télécharger. Cependant, en l'absence de ces outils ou lorsqu'aucun agent de collecte n'est installé sur le serveur, la commande **`grep`** devient votre outil de secours ultime.

> **Note technologique :** Même les outils d'IA modernes les plus avancés (comme Gemini, Claude, CodeX) exécutent en arrière-plan des outils Bash et des commandes `grep` pour réaliser l'analyse de fichiers et vous retourner des résultats structurés.

---

## Module 2 : Préparation de l'Environnement et Génération des Fichiers Démo

Pour appliquer ce cours concrètement (car regarder sans pratiquer ne permet pas d'apprendre), nous allons créer un dossier de simulation contenant des fichiers de configuration et des logs d'erreurs.

### Étape 1 : Créer le dossier et le script de génération
Exécutez les commandes suivantes sur votre machine Linux :
```bash
mkdir -p grep-demo/demo-files
cd grep-demo/demo-files
nano generate_demo_files.sh
```

### Étape 2 : Insérer le code de simulation
Copiez et collez le script Bash suivant dans le fichier `generate_demo_files.sh` :

```bash
#!/bin/bash
# Création des sous-dossiers
mkdir -p logx config

# Génération d'un fichier de logs applicatifs (App Logs)
cat << 'EOF' > logx/app.log
[2026-06-04 10:00:00] INFO: Application started successfully.
[2026-06-04 10:01:15] INFO: Connecting to database...
[2026-06-04 10:01:16] ERROR: Database connection failed. Timeout reached.
[2026-06-04 10:02:00] WARNING: High memory usage detected.
[2026-06-04 10:05:22] error: payment failed for user_id 4042.
[2026-06-04 10:06:01] INFO: Retry connection to DB...
[2026-06-04 10:06:02] ERROR: Database connection failed again.
[2026-06-04 10:07:10] supererror: critical system component crashed.
[2026-06-04 10:10:00] INFO: User login attempt from IP 192.168.1.50
EOF

# Génération d'un fichier de configuration Nginx
cat << 'EOF' > config/nginx.conf
server {
    listen 80;
    server_name centirio.business;
    
    location / {
        proxy_pass http://localhost:8080;
        # DB_HOST=db.production.local
    }
}
EOF

# Génération d'un fichier de logs Nginx Access
cat << 'EOF' > logx/nginx_access.log
192.168.1.1 - - [04/Jun/2026:10:01:00] "GET / HTTP/1.1" 200 3426
192.168.1.50 - - [04/Jun/2026:10:02:15] "POST /login HTTP/1.1" 404 124
192.168.1.99 - - [04/Jun/2026:10:05:00] "GET /api/pay HTTP/1.1" 500 2341
EOF

# Génération d'un fichier de logs d'authentification (Auth Logs)
cat << 'EOF' > logx/auth.log
Jun  4 10:00:10 server sshd[1234]: Failed password for invalid user admin from 203.0.113.5 port 49152 ssh2
Jun  4 10:01:15 server sshd[1235]: Failed password for root from 203.0.113.5 port 49153 ssh2
Jun  4 10:02:22 server sshd[1236]: Accepted password for devopsabdel from 192.168.1.10 port 49154 ssh2
EOF

echo "✔ Fichiers démo générés avec succès !"
```

### Étape 3 : Rendre le script exécutable et le lancer
```bash
chmod +x generate_demo_files.sh
./generate_demo_files.sh
```

---

## Module 3 : Les Fondations et l'Usage Élémentaire de `grep`

La commande `grep` est installée nativement sur toutes les distributions Linux. Son rôle est de rechercher un motif ou un texte spécifique (Pattern) dans un ou plusieurs fichiers.

### 3.1 Structure de base d'une commande `grep`
```
grep [OPTIONS] PATTERN [FICHIER...]
```
* **PATTERN :** Le texte ou l'expression régulière recherchée.
* **FICHIER :** Le chemin du fichier dans lequel effectuer la recherche.
* **OPTIONS (Flags) :** Modifient le comportement de recherche.

### 3.2 Recherche simple d'erreurs
Pour rechercher le mot exact "ERROR" (en majuscules) dans le fichier de log de l'application :
```bash
grep "ERROR" logx/app.log
```

### 3.3 Ignorer la casse (Case Insensitivity) avec `-i`
En production, un log peut contenir "ERROR", "error" ou "Error". Pour forcer `grep` à ignorer les distinctions majuscules/minuscules, utilisez le flag `-i` :
```bash
grep -i "error" logx/app.log
```

### 3.4 Afficher les numéros de lignes avec `-n`
Pour indiquer précisément au développeur où se situe l'erreur dans un fichier massif sans qu'il cherche à l'aveugle, utilisez le flag `-n` :
```bash
grep -n "ERROR" logx/app.log
```

### 3.5 Recherche dans plusieurs fichiers simultanément
Vous pouvez lister plusieurs fichiers ou utiliser des jokers (`*`) :
```bash
grep "ERROR" logx/app.log logx/nginx_access.log
# Ou pour cibler tous les fichiers qui se terminent par .log :
grep "Failed" logx/*.log
```

---

## Module 4 : Filtrage Avancé et Extraction Ciblée

### 4.1 Recherche récursive dans les dossiers avec `-r` ou `-R`
Si vous ne savez pas dans quel fichier se trouve une variable de configuration ou une erreur, vous pouvez chercher récursivement dans tout le répertoire courant :
```bash
grep -r "DB_HOST" .
```

### 4.2 Afficher uniquement les noms de fichiers avec `-l`
Si vous cherchez à savoir *quels fichiers* contiennent un motif spécifique (par exemple, localiser où est stocké un mot de passe ou une clé de configuration) sans afficher le contenu textuel :
```bash
grep -rl "DB_HOST" .
```

### 4.3 Compter le nombre d'occurrences avec `-c`
Si vous avez besoin d'une statistique rapide (ex: savoir combien d'échecs de paiement ou de connexions ont eu lieu) :
```bash
grep -c "ERROR" logx/app.log
grep -c "Failed" logx/auth.log
```

### 4.4 Inverser la recherche (Exclure un motif) avec `-v`
Lorsque vous analysez des logs de 15 Go, 95% des lignes sont souvent des messages d'information standard (`INFO`). Pour les masquer et ne voir que le reste :
```bash
grep -v "INFO" logx/app.log
```

### 4.5 Correspondance exacte de mot avec `-w`
Si vous cherchez le mot exact "error" et que vous voulez exclure les mots composés comme "supererror" ou "errorcodes" :
```bash
grep -w "error" logx/app.log
```

### 4.6 Correspondance exacte de ligne entière avec `-x`
Si vous voulez isoler une ligne qui contient uniquement et strictement le motif recherché :
```bash
grep -x "MotifExact" fichier.txt
```

---

## Module 5 : Maîtrise du Contexte (Afficher les lignes adjacentes)

Lors d'un plantage en production, la ligne d'erreur brute ne suffit pas. Le problème réel s'est souvent produit quelques lignes *avant* (ex: début d'un timeout) ou se poursuit quelques lignes *après* (ex: stack trace de plantage).

```
[Ligne Avant - b]
[Ligne Avant - a]
██████████████████  <- Ligne contenant le PATTERN
[Ligne Après - a]
[Ligne Après - b]
```

### 5.1 Afficher les lignes APRÈS (After) avec `-A`
Pour afficher la ligne contenant l'erreur ainsi que les **3 lignes qui la suivent** :
```bash
grep -A 3 "Database connection failed" logx/app.log
```

### 5.2 Afficher les lignes AVANT (Before) com `-B`
Pour inspecter ce qui a déclenché l'erreur en affichant les **3 lignes qui précèdent** :
```bash
grep -B 3 "Database connection failed" logx/app.log
```

### 5.3 Afficher le Contexte global (Avant et Après) avec `-C`
Pour obtenir une vue d'ensemble (ex: 5 lignes avant et 5 lignes après) :
```bash
grep -C 5 "Database connection failed" logx/app.log
```

---

## Module 6 : Combinaisons en Production (Pipes, Docker & Processus)

La puissance de `grep` se décuple lorsqu'elle est combinée avec d'autres commandes Linux à travers le mécanisme des tubes ou pipes (`|`).

### 6.1 Inspecter les processus en cours
Pour vérifier en temps réel si votre serveur web Nginx est démarré :
```bash
ps aux | grep nginx
```
*Astuce DevOps :* Pour éliminer la ligne du processus de recherche `grep` lui-même des résultats :
```bash
ps aux | grep nginx | grep -v grep
```

### 6.2 Filtrer l'état des services système (`systemctl`)
Pour extraire uniquement le statut d'activité d'une ressource (comme SSH) :
```bash
systemctl status ssh | grep "Active"
```

### 6.3 Extraire l'adresse IP réseau
Pour lister rapidement vos cartes réseaux et isoler les lignes contenant les adresses IP (IPv4) :
```bash
ip addr | grep "inet "
```

### 6.4 Analyser les journaux Docker en temps réel
Si vos applications tournent dans des conteneurs isolés :
```bash
docker ps | grep nginx
docker logs <id_conteneur> 2>&1 | grep -i "error"
```

---

## Module 7 : Expressions Régulières Étendues (Regex)

Pour les recherches complexes où un simple mot clé ne suffit pas, activez les expressions régulières étendues avec le flag `-E` (équivalent à la commande historique `egrep`).

### 7.1 L'opérateur logique OU (`|`)
Chercher les lignes qui contiennent le mot "ERROR" **OU** le mot "WARNING" :
```bash
grep -E "ERROR|WARNING" logx/app.log
```

### 7.2 Cibler le début (`^`) et la fin (`$`) d'une ligne
* Pour afficher uniquement les lignes qui **commencent** par "Jun" :
    ```bash
    grep "^Jun" logx/auth.log
    ```
* Pour afficher uniquement les lignes qui **se terminent** par "ssh2" :
    ```bash
    grep "ssh2$" logx/auth.log
    ```

### 7.3 Filtrer des codes d'erreurs HTTP spécifiques (ex: 400 et 500)
Pour analyser vos fichiers d'accès Nginx et isoler les erreurs de requêtes :
```bash
grep -E " 40[0-9] | 50[0-9] " logx/nginx_access.log
```

---

## Module 8 : Automatisation et Productivité (Aliases personnalisés)

Pour éviter de retaper des commandes complexes lors d'une gestion de crise sur un serveur, vous pouvez créer des raccourcis durables (Aliases) dans votre fichier de configuration de shell (`~/.bashrc` ou `~/.zshrc`).

### 8.1 Forcer la coloration des résultats
Ajoutez cette ligne pour que les motifs recherchés apparaissent toujours en couleur claire :
```bash
alias grep='grep --color=auto'
```

### 8.2 Créer un alias de diagnostic d'erreur rapide
1. Ouvrez votre fichier de configuration (ex: `~/.zshrc` ou `~/.bashrc`) :
   ```bash
   nano ~/.zshrc
   ```
2. Ajoutez votre alias personnalisé tout en bas :
   ```bash
   alias check_errors="grep -E 'ERROR|failed|critical' --color=auto"
   ```
3. Sauvegardez, quittez et rechargez l'environnement :
   ```bash
   source ~/.zshrc
   ```

Maintenant, sur votre serveur, il vous suffit de taper une seule commande courte pour inspecter n'importe quel fichier de log volumineux instantanément :
```bash
check_errors logx/app.log
```

---
*Fin du cours. Ce document constitue une feuille de route complète pour automatiser et optimiser l'analyse de logs système sans saturer vos réseaux de transferts de fichiers inutiles.*
