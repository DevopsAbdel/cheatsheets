# 🎓 Cours Complet : Sécurisation et Durcissement d'un Serveur Linux (VPS Hardening)

Ce cours est basé sur les meilleures pratiques de l'administration système Linux pour protéger un nouveau serveur virtuel privé (VPS) contre les cyberattaques automatisées dès sa mise en ligne.

---

## 📌 Introduction : Le mythe de l'invisibilité sur Internet

Dès qu'un serveur VPS obtient une adresse IP publique, il devient immédiatement la cible de scripts automatisés (*botnets*). En moins d'une minute, des scans de ports analysent la machine pour tenter des attaques par force brute (*Brute Force*), principalement sur le protocole SSH. L'objectif des attaquants est souvent d'exploiter les ressources du serveur pour du minage de cryptomonnaies ou de l'intégrer à un réseau de machines zombies.

> 💡 **Règle d'or :** La sécurité informatique n'est pas un produit qu'on installe une fois pour toutes, c'est un **processus itératif** qui demande une vigilance continue.

---

## 🛠️ Partie 1 : Infrastructure et Gestion Réseau

### 1. Environnement d'apprentissage et de test
* **Bonne pratique :** Ne testez jamais de nouvelles configurations de sécurité directement sur un serveur de production. Utilisez des plateformes proposant des crédits gratuits (DigitalOcean, Linode, Vultr, etc.) pour vous exercer sans risque.
* En production, utilisez des plateformes de comparaison comme *ServerHunter* pour analyser la réputation et les options de sécurité des différents hébergeurs.

### 2. Comprendre les Enregistrements DNS (DNS Records)
Pour mapper correctement et sécuriser l'accès à votre infrastructure, vous devez maîtriser les différents types d'enregistrements DNS :
* **A Record :** Assigne un nom de domaine à une adresse IPv4 physique (Le plus utilisé).
* **AAAA Record :** Assigne un nom de domaine à une adresse IPv6.
* **CNAME (Canonical Name) :** Crée un alias qui redirige un sous-domaine vers un autre domaine (ex: `www.votredomaine.com` vers `votredomaine.com`).
* **MX Record (Mail Exchanger) :** Spécifie les serveurs de messagerie responsables de la réception des e-mails pour le domaine.
* **TXT Record :** Utilisé pour insérer du texte brut, essentiel pour la sécurisation des e-mails contre l'usurpation d'identité via les protocoles **SPF (Sender Policy Framework)**, **DKIM (DomainKeys Identified Mail)**, et **DMARC**.

*🛠️ Outil de diagnostic :* Pour vérifier la bonne propagation et configuration de vos enregistrements DNS depuis votre terminal, utilisez la commande `dig` :
```bash
dig votredomaine.com A
dig @8.8.8.8 votredomaine.com TXT +short
```

---

## 🛡️ Partie 2 : Le Guide de Sécurisation en 10 Étapes

### 1️⃣ Mettre à jour les paquets du système (Update & Upgrade)
Dès votre première connexion au serveur, vous devez corriger les vulnérabilités existantes du système d'exploitation.
```bash
apt update && apt upgrade -y
```
* **Bonne pratique :** Si le système d'exploitation requiert un redémarrage (ce qui est signalé par l'apparition du fichier `/var/run/reboot-required`), effectuez un redémarrage immédiat avant d'installer la moindre application :
```bash
[ -f /var/run/reboot-required ] && reboot
```

### 2️⃣ Créer un utilisateur dédié et lui accorder les droits Sudo
L'utilisation directe du compte `root` pour la gestion quotidienne est une faille majeure. En cas d'erreur ou d'intrusion, l'attaquant dispose instantanément des privilèges maximaux.
```bash
# Création du nouvel utilisateur
adduser deploy

# Ajout de l'utilisateur au groupe sudo pour lui permettre d'élever ses privilèges
usermod -aG sudo deploy
```
* **Bonne pratique :** Testez immédiatement le bon fonctionnement de l'élévation de privilèges en basculant sur ce compte :
```bash
su - deploy
sudo whoami  # Doit renvoyer "root" après saisie de votre mot de passe
```

### 3️⃣ Configurer l'authentification par clé SSH (Key-Based Authentication)
Les attaques par force brute ciblent les mots de passe. L'authentification par paire de clés cryptographiques rend ces attaques totalement inefficaces.

*Sur votre machine locale (votre PC personnel) :* Générez une paire de clés hautement sécurisée (via l'algorithme Ed25519) et transmettez la clé publique au serveur.
```bash
# Génération de la clé sur votre PC
ssh-keygen -t ed25519 -C "votre_email@example.com"

# Copie de la clé publique vers le serveur VPS
ssh-copy-id -i ~/.ssh/id_ed25519 deploy@IP_DU_SERVEUR
```

### 4️⃣ Modifier la configuration du démon SSH (sshd_config)
Pour déjouer les outils de scan de masse, modifiez les paramètres par défaut du fichier `/etc/ssh/sshd_config`.

```bash
sudo vim /etc/ssh/sshd_config
```
Modifiez ou ajoutez les lignes suivantes :
```text
Port 4444                  # Remplacez le port 22 par un port aléatoire (ex: 4444)
PermitRootLogin no         # Interdit la connexion directe avec le compte root
PasswordAuthentication no  # Désactive totalement l'usage des mots de passe via SSH
PubkeyAuthentication yes   # Force l'utilisation des clés de chiffrement SSH
```

> ⚠️ **Alerte Piège (Cloud-init) :** Sur de nombreux environnements Cloud, un sous-dossier de configuration (`/etc/ssh/sshd_config.d/`) géré par les scripts d'initialisation de l'hébergeur peut écraser vos directives globales. Pensez à vérifier ces fichiers pour vous assurer que `PasswordAuthentication no` y est bien appliqué.

*Redémarrage du service :*
```bash
sudo systemctl restart ssh
```
🔴 **TRÈS IMPORTANT :** Ne fermez jamais votre terminal actuel. Ouvrez une nouvelle fenêtre et tentez de vous connecter avec votre clé et sur le nouveau port :
```bash
ssh -p 4444 -i ~/.ssh/id_ed25519 deploy@IP_DU_SERVEUR
```

### 5️⃣ Verrouiller le compte Root au niveau du système
Puisque vous utilisez désormais un utilisateur dédié doté des droits `sudo` et que l'accès SSH en root est proscrit, vous devez verrouiller le mot de passe système du compte root.
```bash
sudo passwd -l root
```

### 6️⃣ Configurer le pare-feu UFW (Uncomplicated Firewall)
La politique par défaut d'un pare-feu doit être stricte : bloquer tout le trafic entrant (*ingress*) et autoriser le trafic sortant (*egress*).
```bash
# Définition des politiques par défaut
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Autoriser le port SSH personnalisé avec protection contre le flood (limit)
sudo ufw limit 4444/tcp comment 'Port SSH Securise'

# Autoriser les ports Web standards si nécessaire
sudo ufw allow 80/tcp comment 'HTTP'
sudo ufw allow 443/tcp comment 'HTTPS'

# Activation du pare-feu
sudo ufw enable
```
* **Bonne pratique :** La directive `ufw limit` permet de limiter automatiquement le nombre de connexions à 6 tentatives toutes les 30 secondes par adresse IP, ralentissant drastiquement les scanners.

### 7️⃣ Installer et configurer Fail2Ban
`Fail2Ban` agit comme un système de prévention des intrusions. Il analyse en temps réel les journaux système (logs) et bannit via le pare-feu les adresses IP suspectes.
```bash
sudo apt install fail2ban -y
```
Créez un fichier de configuration locale pour surcharger les paramètres d'origine :
```bash
sudo vim /etc/fail2ban/jail.local
```
Ajoutez-y la configuration suivante pour votre port SSH :
```ini
[sshd]
enabled = true
port = 4444
filter = sshd
logpath = %(sshd_log)s
backend = systemd
maxretry = 3
bantime = 86400
findtime = 600
```
*Explications :* Si une adresse IP échoue `3` fois (`maxretry`) à se connecter dans un intervalle de `10 minutes` (`findtime`), elle est bannie pendant `24 heures` (`bantime`).

```bash
# Activer et démarrer le service
sudo systemctl enable --now fail2ban
# Vérifier le statut
sudo fail2ban-client status sshd
```

### 8️⃣ Activer les mises à jour automatiques de sécurité (Unattended Upgrades)
Pour maintenir votre serveur protégé contre les vulnérabilités de type *Zero-Day* sans intervention manuelle quotidienne, activez la mise à niveau automatique des paquets de sécurité.
```bash
sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure -plow unattended-upgrades # Sélectionnez "Oui" à l'invite
```
Pour affiner le comportement, éditez le fichier de configuration :
```bash
sudo vim /etc/apt/apt.conf.d/50unattended-upgrades
```
* **Bonne pratiques à configurer :**
  * Décommentez et passez à `true` la ligne `Unattended-Upgrade::Remove-Unused-Dependencies "true";` pour éviter l'accumulation de paquets obsolètes.
  * Configurer l'envoi d'alertes par e-mail en cas d'erreur (`Unattended-Upgrade::Mail`).
  * **Conseil de production :** Gardez la fonction `Automatic-Reboot` sur `false` pour éviter qu'un redémarrage imprévu au milieu de la nuit n'interrompe vos services de production sans supervision.

### 9️⃣ Mettre en place la traçabilité avec Auditd
`auditd` est le sous-système d'audit du noyau Linux. Il enregistre de manière sécurisée les événements système critiques.
```bash
sudo apt install auditd audispd-plugins -y
```
Ajoutez des règles pour surveiller les accès aux fichiers sensibles (comme `/etc/sudoers` ou les tentatives d'écriture sur les binaires d'authentification) :
```bash
sudo vim /etc/audit/rules.d/audit.rules
```
Exemple de configurations de règles :
```text
-w /etc/sudoers -p wa -k t_sudoers
-w /etc/passwd -p wa -k t_passwd
-w /var/log/auth.log -p wa -k t_authlog
```
*Chargez les nouvelles règles :*
```bash
sudo augenrules --load
```

### 🔟 Réaliser un audit de conformité avec Lynis
`Lynis` est un outil d'audit de sécurité open-source qui analyse l'ensemble de votre système Linux et vous attribue un score de durcissement global.
```bash
sudo apt install lynis -y
sudo lynis audit system
```
* **Bonne pratique :** À la fin du rapport, Lynis fournit une liste d'avertissements (*Warnings*) et de suggestions (*Suggestions*). Parcourez ces recommandations pour continuer à améliorer pas à pas le niveau de sécurité de votre serveur.

---

## 📝 Liste de contrôle de fin de projet (Documentation)

Une fois ces étapes franchies, documentez vos interventions dans un fichier sécurisé (hors de votre VPS). Cette documentation doit contenir :
* [ ] Le port SSH personnalisé configuré.
* [ ] Le nom de l'utilisateur dédié disposant des accès administrateurs.
* [ ] La localisation et la sauvegarde sécurisée de la clé privée SSH.
* [ ] La liste des règles de pare-feu initialement approuvées.
