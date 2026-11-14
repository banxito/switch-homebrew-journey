# Switch Homebrew Journey

Carnet de bord de mon passage au homebrew sur Nintendo Switch : installation du CFW, dépannage, dump de mes propres cartouches, et la suite vers iPhone/iPad.

> ⚠️ Ce dépôt ne contient **aucun** fichier de jeu, aucune clé (`prod.keys`, `title.keys`) et aucun lien vers du contenu piraté. Tout ce qui est décrit ici concerne **mes propres jeux et ma propre console**.

## Ma configuration

| Élément | Version / détail |
|---|---|
| Console | Nintendo Switch (emuMMC sur partition) |
| Firmware | 23.0.1 |
| CFW | Atmosphère 1.12.2 |
| Bootloader | Hekate |
| Carte SD | 128 Go, FAT32 |
| Ordinateur | MacBook Pro (Apple Silicon) |

## Sommaire

1. [Jailbreak et emuMMC](01-jailbreak.md) : ce qu'est l'emuMMC et pourquoi ma carte SD « perd » 60 Go
2. [Dépannage](02-depannage.md) : les erreurs rencontrées et comment je les ai résolues
3. [Dump de mes jeux](03-dump.md) : clés avec Lockpick, nxdumptool, rassemblage et vérification du XCI
4. [NX2Apple](04-nx2apple.md) : faire tourner mes jeux sur iPhone/iPad (à venir)
5. [Lexique](05-lexique.md) : ROM, XCI, NSP, sysMMC, emuMMC, etc.

## Leçons principales

- **Ne jamais coller une commande inconnue dans le Terminal**, surtout si elle est en base64 ou finit par `| bash`.
- **Sur Mac, glisser un dossier qui existe déjà le remplace** au lieu de fusionner. Copier les fichiers un par un dans `bootloader/`, `atmosphere/`, etc.
- **Après chaque copie depuis un Mac** : `dot_clean` puis *Fix Archive Bit* dans Hekate.
- **L'emuMMC reste hors ligne.** Pour l'eShop et le jeu en ligne, démarrer en Stock (sysMMC sans CFW).
- **Sur un firmware récent, utiliser les outils à jour** (ex. nxdumptool *rewrite* plutôt que la v1.1.15).

## Outils utilisés

- [Atmosphère](https://github.com/Atmosphere-NX/Atmosphere) : le CFW
- [Hekate](https://github.com/CTCaer/hekate) : bootloader et outils (USB, partitions, archive bit)
- [nxdumptool](https://github.com/DarkMatterCore/nxdumptool) : dump des cartouches et contenus installés
- [NX Guide](https://switch.hacks.guide/) : le guide de référence
