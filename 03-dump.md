# 3. Dump de mes jeux

Objectif : créer une copie de **mes propres cartouches** pour les utiliser sur d'autres appareils.

## Étape 1 : extraire les clés de la console

Les jeux sont chiffrés. Pour les lire, il faut les clés de **sa propre console**, extraites avec un payload Lockpick.

1. Copier le `.bin` de Lockpick dans `bootloader/payloads/` sur la carte SD.
   - ⚠️ Sur Mac, ne pas glisser le dossier `bootloader` entier : ça remplacerait celui de Hekate.
   - Le dépôt original a été retiré par DMCA. Prendre une version récente qui gère son firmware, depuis une source reconnue, et se méfier des clones au hasard.
2. Hekate → **Payloads** → choisir le `.bin`.
3. **Dump from SysNAND** (ou EmuNAND si l'emuMMC a un firmware plus récent). Volume = déplacer, Power = valider.
4. Le fichier `prod.keys` est créé dans `switch/` sur la carte SD.

> 🔒 `prod.keys` ne se partage **jamais**. À sauvegarder en lieu sûr.

## Étape 2 : installer nxdumptool (version rewrite)

1. Télécharger `nxdt_rw_poc.nro` depuis la release **rewrite-prerelease** de [nxdumptool](https://github.com/DarkMatterCore/nxdumptool/releases).
2. Supprimer toute ancienne version (`nxdumptool.nro`).
3. Copier le `.nro` dans `switch/`.
4. `dot_clean`, éjecter.

## Étape 3 : dumper la cartouche en XCI

1. Hekate → Launch → **Atmosphère emuMMC**.
2. Garder **R** et lancer un jeu → Homebrew Menu → nxdumptool.
3. **Gamecard** → dump XCI, avec ces réglages :

| Option | Valeur |
|---|---|
| prepend key area | no |
| keep certificate | no |
| trim dump | no (ou yes pour gagner environ 2 Go) |
| calculate checksum | **yes** |
| output storage | sdmc |

4. Noter le **CRC** affiché à la fin.

Résultat pour BotW : environ 6 minutes 30, fichier dans `nxdt_rw_poc/Gamecard/`.

## Étape 4 : rassembler le fichier sur le Mac

Sur une carte FAT32, les fichiers de plus de 4 Go sont découpés en morceaux (`00`, `01`, …). Après copie sur le Mac :

```sh
cd ~/Downloads
cat "NOM_DU_DOSSIER.xci"/* > Zelda_BotW.xci
```

## Étape 5 : vérifier

```sh
crc32 ~/Downloads/Zelda_BotW.xci
```

Le résultat doit être identique au CRC affiché par nxdumptool. ✅ Dans mon cas, il était identique : j'ai pu supprimer les morceaux.

## Ce qu'il reste à faire

- [ ] Dumper la mise à jour du jeu en NSP (nxdumptool → titres installés).
