# Compte Rendu - TP 01 : Installation Serveurs

## 1. Installation de la Machine Virtuelle

### 1.1 Récupération de l'ISO



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