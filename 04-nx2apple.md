# 4. NX2Apple (à venir)

[NX2Apple](https://github.com/LNPANDY/NX2Apple) est une app macOS qui transforme un jeu Switch que l'on possède en app iOS/iPadOS.

## Le principe

Ce n'est pas un émulateur : le code du jeu est **recompilé** pour les puces Apple, et les shaders sont traduits vers Metal. Le résultat est un fichier IPA à installer sur iPhone/iPad.

La Switch et les puces Apple sont toutes les deux en ARM64, mais il faut quand même traduire tout ce qui touche au GPU (API NVN de Nvidia → Metal) et aux services du système de la Switch.

## Ce qu'il faut

- Mac Apple Silicon, macOS récent, **Xcode** (avec le SDK iOS)
- Ses propres dumps (jeu, mise à jour, DLC) et `prod.keys`
- iPhone/iPad récent
- Un outil de sideloading (AltStore, SideStore, Sideloadly…). Avec un compte Apple gratuit, l'app doit être re-signée tous les 7 jours.

## Notes

- Projet jeune : vérifier la liste des jeux compatibles avant de se lancer.
- L'app n'est pas notarisée : clic droit → Ouvrir au premier lancement.

## Journal

_À compléter._
