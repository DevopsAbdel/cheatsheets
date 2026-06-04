# Guide Complet d'Expert : Sécuriser un Serveur Linux VPS

Ce guide pratique réunit l'ensemble des étapes et configurations indispensables pour transformer un serveur Linux (VPS) vulnérable en une véritable forteresse numérique. En l'absence de sécurisation, un VPS s'expose à des milliers de tentatives de connexion malveillantes automatisées chaque jour.

---

## Sommaire
1. [Module 1 : Modification du Port SSH par Défaut](#module-1--modification-du-port-ssh-par-défaut)
2. [Module 2 : Gestion des Utilisateurs et Privilèges Sudo](#module-2--gestion-des-utilisateurs-et-privilèges-sudo)
3. [Module 3 : Protection Automatisée avec Fail2Ban](#module-3--protection-automatisée-avec-fail2ban)
4. [Module 4 : Authentification stricte par Clés SSH](#module-4--authentification-stricte-par-clés-ssh)
5. [Outils Recommandés pour l'Administration](#outils-recommandés-pour-ladministration)

---

## Module 1 : Modification du Port SSH par Défaut

Le port par défaut (**22**) est la cible permanente des scripts et bots automatisés parcourant le web. Le modifier permet de réduire immédiatement le bruit de fond des attaques de force brute.

### Étape 1 : Choisir et vérifier la disponibilité d'un port
Sélectionnez un numéro de port compris dans la plage des ports privés : **1024 à 65535** (ex: `4422`).
Avant de l'attribuer, assurez-vous qu'aucune application active ne l'utilise sur votre machine grâce à la commande :
```bash
sudo ss -tln
```

### Étape 2 : Configurer le service SSH
1. Éditez le fichier de configuration principal du démon SSH :
   ```bash
   sudo nano /etc/ssh/sshd_config
   ```
2. Repérez la ligne contenant `#Port 22` ou `Port 22`. 
3. Supprimez le symbole `#` (dièse) si présent pour activer la directive, puis remplacez `22` par le port choisi :
   ```text
   Port 4422
   ```
4. Sauvegardez le fichier (`Ctrl + O` ou `Ctrl + S`, puis validez avec `Entrée`) et quittez l'éditeur (`Ctrl + X`).

### Étape 3 : Mise à jour du Pare-feu (UFW) et Redémarrage
Si vous utilisez le pare-feu **UFW** (Uncomplicated Firewall), vous devez **impérativement** autoriser le nouveau port en protocole TCP avant d'appliquer les changements, sous peine de bloquer vos futurs accès :
```bash
sudo ufw allow 4422/tcp
```
Une fois le pare-feu ajusté, redémarrez le service SSH pour appliquer la configuration :
```bash
sudo systemctl restart ssh
# ou selon la distribution :
sudo systemctl restart sshd
```

> ⚠️ **ATTENTION CRITIQUE :** Ne fermez **jamais** votre session SSH actuelle avant d'avoir testé avec succès la connexion dans une toute nouvelle fenêtre de terminal. Si une erreur a été commise, votre session active restera votre unique moyen de corriger le fichier.

### Étape 4 : Tester la nouvelle configuration
Ouvrez un nouveau terminal et essayez de vous connecter en spécifiant explicitement le nouveau port à l'aide de l'argument `-p` :
```bash
ssh -p 4422 root@IP_DE_VOTRE_SERVEUR
```
*Note : Si vous essayez de vous connecter sur le port 22 standard, la connexion doit désormais être immédiatement refusée (`Connection refused`).*

---

## Module 2 : Gestion des Utilisateurs et Privilèges Sudo

L'utilisation directe et exclusive du compte `root` constitue un risque majeur. Son nom d'utilisateur est universellement connu, ce qui facilite de moitié le travail des attaquants.

### Étape 1 : Créer un utilisateur standard
Ajoutez un nouvel utilisateur doté d'un nom personnalisé :
```bash
sudo adduser mon_nouvel_utilisateur
```
Saisissez un mot de passe robuste lorsque le système vous le demande et validez les informations requises.

### Étape 2 : Accorder les privilèges d'administration (Sudo)
Ajoutez l'utilisateur nouvellement créé au groupe `sudo` pour lui permettre d'exécuter des commandes administratives :
```bash
sudo usermod -aG sudo mon_nouvel_utilisateur
```

### Étape 3 : Tester l'accès de l'utilisateur
Ouvrez un nouveau terminal et connectez-vous avec votre nouvel identifiant :
```bash
ssh -p 4422 mon_nouvel_utilisateur@IP_DE_VOTRE_SERVEUR
```
Vérifiez que vous pouvez utiliser les privilèges d'administration en lançant par exemple une mise à jour des paquets : `sudo apt update`.

### Étape 4 : Désactiver l'accès distant au compte Root
Une fois que vous avez la certitude que votre utilisateur standard fonctionne correctement et dispose des droits sudo :
1. Ouvrez à nouveau le fichier de configuration SSH :
   ```bash
   sudo nano /etc/ssh/sshd_config
   ```
2. Modifiez la directive `PermitRootLogin` pour lui attribuer la valeur `no` :
   ```text
   PermitRootLogin no
   ```
3. Sauvegardez et quittez l'éditeur.
4. Redémarrez le service SSH pour valider la restriction :
   ```bash
   sudo systemctl restart ssh
   ```
*Désormais, toute tentative de connexion directe en tant que `root` sera rejetée par un message d'erreur de permission.*

---

## Module 3 : Protection Automatisée avec Fail2Ban

**Fail2Ban** est un service de sécurité qui analyse en temps réel les journaux d'accès (logs) de votre serveur. Dès qu'il repère une adresse IP effectuant des échecs de connexion répétés dans un intervalle de temps donné, il génère une règle de pare-feu pour bannir cette IP.

### Étape 1 : Installation du paquet
Exécutez l'installation automatique :
```bash
sudo apt install fail2ban -y
```

### Étape 2 : Créer un fichier de configuration local
Par défaut, Fail2Ban utilise le fichier `/etc/fail2ban/jail.conf`. Cependant, lors des mises à jour logicielles, ce fichier peut être écrasé. Il faut donc créer une copie de configuration locale nommée `jail.local` qui aura la priorité absolue :
```bash
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

### Étape 3 : Personnalisation des règles de sécurité
Ouvrez le fichier de configuration locale :
```bash
sudo nano /etc/fail2ban/jail.local
```
Faites défiler le fichier jusqu'à la section par défaut (`[DEFAULT]`) pour ajuster les variables critiques suivantes selon les recommandations d'expert :

* `bantime = 1h` : Durée pendant laquelle l'IP attaquante sera totalement bannie et bloquée (ici, 1 heure).
* `findtime = 10m` : Fenêtre de temps durant laquelle les échecs de connexion sont comptabilisés (ici, 10 minutes).
* `maxretry = 3` : Nombre maximal de tentatives infructueuses autorisées avant le bannissement immédiat (ici, 3 essais).
* `ignoreip = 127.0.0.1/8 [VOTRE_IP_MAISON]` : Permet de placer en liste blanche l'interface locale ainsi que votre propre adresse IP publique fixe de confiance, afin de vous prémunir de tout auto-bannissement accidentel en cas d'erreur de frappe.

### Étape 4 : Activer et redémarrer le service
Activez Fail2Ban pour qu'il se lance automatiquement à chaque démarrage du serveur, puis redémarrez-le :
```bash
sudo systemctl enable fail2ban
sudo systemctl restart fail2ban
```

### Étape 5 : Consulter l'état des bannissements
Pour surveiller l'activité de Fail2Ban et voir en temps réel le nombre de bots bloqués sur le protocole de sécurisation SSH, utilisez la commande cliente suivante :
```bash
sudo fail2ban-client status sshd
```

---

## Module 4 : Authentification stricte par Clés SSH (Sans Mot de Passe)

L'authentification par paire de clés cryptographiques (une clé publique stockée sur le serveur et une clé privée conservée jalousement sur votre ordinateur) représente le plus haut standard de sécurité existant pour le protocole SSH.

### Étape 1 : Générer une paire de clés (Exemple sous Windows)
1. Ouvrez l'utilitaire **PuTTYgen**.
2. Cliquez sur le bouton **Generate**.
3. Déplacez votre souris de manière aléatoire sur la zone vide supérieure pour injecter de l'entropie et générer de l'aléa cryptographique.
4. **Recommandation non négociable :** Saisissez une phrase de passe forte (**Passphrase**) dans les champs *Key passphrase* et *Confirm passphrase*. Cela permet de chiffrer votre clé privée sur votre disque dur et la rend inutilisable si un individu parvenait à vous voler le fichier.
5. Cliquez sur **Save private key** pour sauvegarder votre clé privée (fichier au format `.ppk`, ex: `private_key.ppk`).
6. Sélectionnez l'intégralité du texte affiché dans le grand encadré textuel supérieur nommé *"Public key for pasting into OpenSSH authorized_keys file"* et copiez-le dans votre presse-papiers.

### Étape 2 : Installer la clé publique sur le VPS
Connectez-vous à votre serveur avec votre compte utilisateur standard configuré au Module 2, puis créez le répertoire `.ssh` et sécurisez ses droits d'accès :
```bash
# Créez le dossier caché s'il n'existe pas
mkdir -p ~/.ssh

# Modifiez les permissions pour que seul votre utilisateur y ait accès
chmod 700 ~/.ssh

# Créez ou ouvrez le fichier de clés autorisées
nano ~/.ssh/authorized_keys
```
Collez le contenu exact de la clé publique copiée depuis PuTTYgen à l'intérieur de ce fichier. Sauvegardez et quittez (`Ctrl + X`, puis `Y`, puis `Entrée`).

Ajustez strictement les permissions du fichier pour empêcher toute modification par un tiers :
```bash
chmod 600 ~/.ssh/authorized_keys
```

### Étape 3 : Configurer votre client SSH pour se connecter par clé
Avant de désactiver quoi que ce soit, vérifiez que la clé fonctionne :
* **Avec PuTTY :** Chargez votre session sauvegardée, allez dans le menu de gauche dans `Connection` ➔ `SSH` ➔ `Auth` ➔ `Credentials`. Dans le champ dédié à la clé privée (*Private key file for authentication*), cliquez sur *Browse* et sélectionnez votre fichier `.ppk`. Revenez sur la page *Session*, cliquez sur *Save*, puis sur *Open*. Le serveur doit vous demander votre nom d'utilisateur puis la phrase de passe de votre clé, sans jamais requérir le mot de passe de l'utilisateur Linux.

### Étape 4 : Désactivation totale des mots de passe
Une fois la connexion par clé validée et pleinement opérationnelle, vous pouvez interdire purement et simplement toute authentification classique par mot de passe. Cela rend les attaques par force brute totalement obsolètes.

1. Ouvrez le fichier de configuration :
   ```bash
   sudo nano /etc/ssh/sshd_config
   ```
2. Modifiez ou ajoutez les directives suivantes pour qu'elles correspondent exactement à ceci :
   ```text
   PasswordAuthentication no
   PubkeyAuthentication yes
   ChallengeResponseAuthentication no
   KbdInteractiveAuthentication no
   UsePAM no
   ```
3. Sauvegardez le fichier et appliquez les configurations en redémarrant le service SSH :
   ```bash
   sudo systemctl restart ssh
   ```

*Toute tentative de connexion sans clé SSH valide se soldera immédiatement par un refus catégorique de connexion (`Permission denied (publickey)`).*

---

## Outils Recommandés pour l'Administration

Pour gérer sereinement vos serveurs au quotidien, voici la panoplie recommandée :

* **PuTTY & PuTTYgen** : Les utilitaires classiques et légers sous Windows pour la génération de clés robustes et l'établissement de sessions de terminal.
* **Termius (ou Termius Desktop)** : Une solution moderne multiplateforme idéale pour gérer plusieurs serveurs VPS simultanément. Il permet d'organiser ses machines et de synchroniser de manière hautement sécurisée ses clés privées pour basculer facilement d'un serveur à un autre.
* **UFW (Uncomplicated Firewall)** : L'outil idéal sous Debian/Ubuntu pour configurer un pare-feu réseau de manière claire et simplifiée.
