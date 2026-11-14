# 2. Dépannage

Format : **symptôme → cause → solution**.

---

## Crash 2144-0001 (0x290) en ouvrant l'Album

**Symptôme :** écran d'erreur Atmosphère, programme `0100000000001000` (qlaunch, le menu HOME), en lançant le Homebrew Menu depuis l'Album.

**Cause probable :** quelque chose sur la carte SD qui modifie le menu HOME (thème, menu personnalisé) et qui n'est pas compatible avec le firmware, ou un `hbmenu`/`hbl` pas à jour.

**Solutions :**
1. Renommer `atmosphere/contents/0100000000001000/` pour désactiver le thème.
2. Recopier le zip complet d'Atmosphère (avec `hbl` et `hbmenu`).
3. **Contournement :** garder **R** enfoncé en lançant un jeu. Le Homebrew Menu s'ouvre à la place du jeu, avec beaucoup plus de RAM qu'avec l'Album.

---

## « Certaines données n'ont pas été trouvées » / « Une mise à jour est nécessaire »

**Symptôme :** en emuMMC, Zelda BotW refuse de se lancer et propose de se connecter.

**Cause :** l'emuMMC, cloné depuis la sysMMC, se souvient que le jeu était mis à jour, mais le dossier `Nintendo` qui contenait la mise à jour n'a pas été remis sur la carte.

**Solution :**
1. **Ne pas** accepter la connexion en emuMMC.
2. Démarrer en **Stock**, retélécharger uniquement les jeux/mises à jour voulus depuis l'eShop (ils vont dans `/Nintendo`).
3. Sur le Mac, **copier** (Cmd+C / Cmd+V, pas glisser) `/Nintendo` vers `/emuMMC/RAW1/`.
4. `dot_clean`, puis *Fix Archive Bit* dans Hekate (voir ci-dessous).

Ça fonctionne parce que l'emuMMC est un clone de la sysMMC : même clé de chiffrement de carte SD, même liste de jeux connus.

---

## « Données corrompues » après une copie depuis le Mac

**Cause :** macOS abîme deux choses sur une carte FAT32 :
- il ajoute des fichiers cachés `._` partout ;
- il perd le **bit d'archive** des dossiers qui représentent les fichiers de plus de 4 Go.

**Solution :**
```sh
dot_clean -m "/Volumes/SWITCH SD"
```
puis dans Hekate : **Tools → Arch bit • RCM • Touch → Fix Archive Bit**.

---

## « Impossible de copier l'élément Nintendo faute d'espace disponible »

**Cause :** voir [01-jailbreak.md](01-jailbreak.md). L'emuMMC sur partition occupe une partie de la carte.

**Solutions :** carte plus grande (256 Go), ou ne copier que les jeux nécessaires (retéléchargement sélectif en Stock).

---

## nxdumptool : « failed to open output file » avec un nom illisible

**Symptôme :** le jeu s'affiche sous le nom « E », et le dump échoue avec un nom de fichier plein de caractères aléatoires.

**Cause :** nxdumptool **v1.1.15** (2022) ne lit pas correctement les infos du jeu sur un firmware récent.

**Solution :** utiliser la version **rewrite** (`nxdt_rw_poc.nro`, release *rewrite-prerelease*) et supprimer l'ancienne.

---

## Commande suspecte trouvée en ligne

```
bash <<< $(echo "…base64…" | base64 -d)
```
Une fois décodée, elle télécharge un script depuis un domaine inconnu et l'exécute (`curl … | bash`). C'est un schéma classique d'arnaque « ClickFix » qui installe un voleur de données. **Je ne l'ai pas exécutée.**

**Règle :** aucun site légitime ne demande de coller une commande dans le Terminal pour « vérifier que tu es humain ».
