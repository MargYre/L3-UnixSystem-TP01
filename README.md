# Compte Rendu - TP 01 : Installation Serveurs

## 1. Installation de la Machine Virtuelle

note: le reboot se fait après le finish
/var/log 1G : nom ’les logs’
ext4, montage /tmp > Ce n'est pas tmp mais /var

## 2 Post-installation
### 2.1 configuration ssh
Etapes:
```span
apt update
apt search ssh
apt install openssh-server
systemctl status ssh

ref: cloriou.fr-Debian – Autoriser l’accès root via SSH/ serverpilot.io-How to Enable SSH Password Authentication/phoenixnap.com- How to Enable SSH on Debian 12/https://www.linuxtricks.fr-SSH : Installer et configurer un serveur SSH

```
### 2.2 Connection
Pour ce faire j'ai changé le port de ma vm
```span
ssh sara@192.168.0.31 > ssh root@localhost -p 2222
```
ref: conseil du professeur

### 2.3 Nombre de paquets
```span
dpkg -l | wc -l
```
J'ai 349 paquets

### 2.4 Space Usage
```span
    df -h
```
La racine / représente moins de 1 Go d’espace utilisé.

### 2.5 a indiquer dans le rendu et expliquer les commandes et le resultat obtenu
1. Langue du système
- Commande utilisée :
  ```bash
  echo $LANG
  ```
Résultat : `en_US.UTF-8`
Cette commande affiche la variable d'environnement `LANG`, qui indique la langue et les paramètres régionaux utilisés par le système.

2. Nom de la machine
- Commande utilisée :
  ```bash
  hostname
  ```
Résultat : `serveur1`

3. Nom de domaine
```bashNAME
       hostname - show or set the system's host name
       domainname - show or set the system's NIS/YP domain name
       ypdomainname - show or set the system's NIS/YP domain name
       nisdomainname - show or set the system's NIS/YP domain name
       dnsdomainname - show the system's DNS domain name
```
`root@serveur1:~# domainname -d
ufr-info-p6.jussieu.fr`
“root@serveur1:~# cat /etc/apt/sources.list | grep -v -E '^#|^$'
deb http://ftp.fr.debian.org/debian/ bookworm main
deb http://security.debian.org/debian-security bookworm-security main”

“root@serveur1:~#  cat /etc/passwd | grep -vE 'nologin|sync'
root:x:0:0:root:/root:/bin/bash”



fdisk est un programme piloté par dialogue pour la création et la manipulation de partitions tableaux. Il comprend les tables de partition GPT, MBR, Sun, SGI et BSD. 

-l, --liste Répertoriez les tables de partition pour les périphériques spécifiés, puis quittez. Si aucun périphérique n'est indiqué, les périphériques mentionnés dans /proc/partitions (si cela le fichier existe) sont utilisés. Les appareils sont toujours répertoriés dans l'ordre dans lequel ils sont spécifiés sur la ligne de commande ou par le noyau répertorié dans /proc/partitions. -x, --list-détails Comme --list, mais fournit plus de détails.



df - rapporter l'utilisation de l'espace du système de fichiers 
-h, --lisible par l'homme tailles d'impression en puissances de 1024 (par exemple, 1023M)


## 3 - Aller Plus Loin
### 3.1 installation automatique (Preseed)
Le pré-amorçage est une méthode permettant d'automatiser l'installation du système d'exploitation Debian et de ses dérivés. Les réponses aux questions d'installation, auxquelles un opérateur devrait normalement répondre de manière interactive, sont prédéterminées et fournies via un fichier de configuration (et parfois des paramètres de démarrage).
source: Wikipédia 

### 3.2 rescue mode
Etapes :
-Redémarrer et maintenir la touche Maj ou Échap après le BIOS.
-Démarrer en Rescue Mode.
-Monter le système de fichiers racine.
-Chrooter le système de fichiers.
-Réinitialiser le mot de passe root.
-Démonter et redémarrer.
Source : SpectralP.

### 3.3 redimentionnement partition
Pour redimmentionner ma partition racine sans reinstaller, il faut suive le tutoriel suivant:
https://debian-facile.org/atelier:chantier:redimensionner-la-partition-racine-a-chaud-sans-la-demonter

Etapes:
1-Vérifier l’espace disponible avec df -h. 
2-Redimensionner le volume logique avec lvresize pour ajuster la taille. 
3-Utiliser resize2fs pour adapter le système de fichiers à la nouvelle taille. 
4-Vérifier le résultat avec df -h pour s'assurer du succès.

source: Redimensionner la partition racine à chaud sans la démonter sur debian-facile.org

# Test
```span
df -h
```