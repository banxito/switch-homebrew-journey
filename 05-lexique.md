# 5. Lexique

| Terme | Définition |
|---|---|
| **CFW** | *Custom Firmware*, système modifié qui permet de lancer du homebrew (ici Atmosphère). |
| **Hekate** | Bootloader : le menu qui s'affiche au démarrage, avec des outils (USB, partitions, payloads). |
| **Payload** | Petit programme `.bin` lancé avant le système (ex. Lockpick). |
| **sysMMC / sysNAND** | Le système d'origine, dans la mémoire interne. |
| **emuMMC / emuNAND** | Copie du système sur la carte SD, utilisée avec le CFW. |
| **Stock / OFW** | Démarrage sans CFW, comme une console normale. |
| **hbmenu** | Le Homebrew Menu, qui liste les applications `.nro`. |
| **NRO** | Format des applications homebrew. |
| **ROM** | Copie d'un jeu sous forme de fichier (de *Read-Only Memory*). |
| **XCI** | *NX Card Image* : image complète d'une cartouche physique. |
| **NSP** | *Nintendo Submission Package* : format eShop (jeux, mises à jour, DLC). |
| **NSZ / XCZ** | Versions compressées de NSP / XCI. |
| **NCA** | Les fichiers chiffrés qui composent un jeu (dans `Nintendo/Contents/registered`). |
| **prod.keys** | Clés de chiffrement propres à la console, nécessaires pour lire ses jeux. |
| **Archive bit** | Attribut FAT32 qui permet à la Switch de traiter un dossier de morceaux comme un seul gros fichier. |
| **CRC32** | Somme de contrôle qui permet de vérifier qu'un fichier est identique à l'original. |
| **qlaunch** | Le menu HOME de la Switch (`0100000000001000`). |
| **ARM64** | Architecture des processeurs de la Switch, des iPhone et des Mac Apple Silicon. |
| **MIPS** | Ancienne architecture RISC (N64, PS1, PS2). |
| **NCE** | *Native Code Execution* : un émulateur exécute directement le code ARM64 du jeu sur le processeur hôte. |
