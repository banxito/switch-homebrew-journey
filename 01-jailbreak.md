# 1. Jailbreak et emuMMC

## sysMMC et emuMMC

- **sysMMC** : le système d'origine, stocké dans la mémoire interne de la console.
- **emuMMC** : une copie complète de ce système, stockée sur la carte SD. C'est là que tourne le CFW.

Avantage : on garde un système « propre » (sysMMC) pour l'eShop et le jeu en ligne, et un système séparé (emuMMC) pour le homebrew.

Dans Hekate → **Launch** :
- **Stock** : sysMMC sans CFW, comme une console non modifiée ;
- **Atmosphère emuMMC** : le CFW sur la copie.

Pour savoir où l'on est : Paramètres → Système. `23.0.1` seul = Stock ; `23.0.1|AMS …|E` = Atmosphère sur emuMMC.

## Pourquoi ma carte de 128 Go n'affiche que 65 Go

Avec un emuMMC **sur partition**, Hekate repartitionne la carte SD (et l'efface) :
- une partition cachée de la taille de la mémoire interne de la console (environ 30 Go sur une Switch classique, environ 60 Go sur une OLED) reçoit l'emuMMC ;
- le reste est formaté en FAT32 pour les fichiers.

macOS n'affiche que la partie FAT32. Rien n'est perdu.

## Le dossier `Nintendo`

Avant le jailbreak, j'avais sauvegardé sur mon Mac le dossier `Nintendo` de la carte SD (81 Go). Il contient les **jeux, mises à jour et DLC installés**, pas les sauvegardes, qui sont dans la mémoire système.

Chaque système a son propre dossier :
- sysMMC : `/Nintendo`
- emuMMC : `/emuMMC/RAW1/Nintendo` (chemin indiqué dans `emuMMC/emummc.ini`)

Après le repartitionnement, les 81 Go ne rentraient plus dans les 65 Go restants.
