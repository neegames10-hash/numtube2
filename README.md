# NumSocial : les réseaux sociaux sur NumWorks

**NumSocial met YouTube, Snapchat, l'écran de ton ordinateur et Minecraft en
multijoueur sur une calculatrice NumWorks.**
La calculatrice reste branchée en USB à un ordinateur (Mac ou Windows), qui fait
passerelle. Tout se passe sur la calculatrice : on cherche une vidéo et on la
regarde, on lit ses messages Snapchat et on y répond depuis le clavier, ou on
pilote l'ordinateur entier (souris, clavier, jeux) depuis la calculatrice.

| Appli | Ce qu'elle fait | Dépôt |
| --- | --- | --- |
| **NumTube** | YouTube : recherche, lecture 320×180 à ~15 images/s, sous-titres | [derim00/numtube](https://github.com/derim00/numtube) |
| **NumChat** | Snapchat : conversations, réponses avec accents, emojis, snaps photo et vidéo | [derim00/numchat](https://github.com/derim00/numchat) |
| **NumScreen** | l'écran de l'ordinateur sur la calculatrice ; souris avec les flèches, clavier avec les touches (shift, alpha), mode jeu | [derim00/numscreen](https://github.com/derim00/numscreen) |
| **NumBlocks** | Minecraft 1.8.8 (NumBlocks de NumPlay, par Mason Chen) avec un mode **multijoueur en ligne** : ouvre ton monde ou rejoins celui de n'importe qui | [derim00/numblocks-multiplayer](https://github.com/derim00/numblocks-multiplayer) |
| **NumSocial** | l'appli principale : installe les applis de ton choix en un clic, et fait passerelle pour toutes | ce dépôt |

## Ce qui marche aujourd'hui

- ✅ **YouTube sur la calculatrice** avec NumTube : la vidéo est décodée sur
  l'ordinateur, compressée en blocs de 4×4 pixels et envoyée image par image ;
  les sous-titres remplacent le son, que la NumWorks n'a pas.
- ✅ **Snapchat sur la calculatrice** avec NumChat : liste des conversations,
  messages en direct, saisie avec majuscules et accents, emojis en couleur,
  snaps photo et vidéo affichés sur demande.
- ✅ **L'écran de l'ordinateur sur la calculatrice** avec NumScreen : l'image
  du PC en 320×200 à environ 15 images/s, la souris aux flèches, tout le clavier
  de la calculatrice (shift, alpha, majuscules) tape sur l'ordinateur, et un
  mode jeu pour bouger et sauter (Roblox...).
- ✅ **Minecraft en multijoueur** avec NumBlocks : la liste publique des
  parties ouvertes, « Open to LAN » pour ouvrir ton monde, les autres joueurs
  visibles avec leur pseudo, blocs et chat partagés, depuis chez chacun (tout
  passe par Internet).
- ✅ **Une seule appli pour tout installer** : elle lit la version de la
  calculatrice, laisse choisir les applis et les installe sans toucher au
  firmware officiel.
- ✅ **Mac et Windows** : l'appli se compile pour les deux, dans ta copie privée
  de ce dépôt.

## Feuille de route

| | Fonction | Idée |
| --- | --- | --- |
| 🔜 | **Discord** | Lire et écrire dans tes messages privés et tes salons, sur le modèle de NumChat |
| 🔜 | **WhatsApp** | Tes discussions WhatsApp sur la calculatrice, à travers WhatsApp Web |

Chaque nouvelle appli rejoindra le même firmware et la même appli NumSocial : à
l'installation, tu coches celles que tu veux.

## Installation (l'appli principale)

### 1. Obtenir l'appli NumSocial

Depuis juillet 2021, le code d'Epsilon (le logiciel de la NumWorks) n'est plus
sous licence libre. NumSocial ne publie donc **aucun code ni aucun firmware de
NumWorks** : seulement un **patch** (`patches/numsocial-epsilon.patch`) et son
propre code. Le firmware se compile chez toi, à partir des sources officielles
de NumWorks.

**Sans rien compiler (Windows ou Mac)**

1. En haut de cette page : **Use this template** > **Create a new repository**,
   coche **Private** (obligatoire : la compilation refuse de tourner dans un
   dépôt public, pour que le firmware ne soit pas téléchargeable par tous).
2. Dans ta copie : onglet **Actions** > **Build NumSocial** > **Run workflow**.
3. Environ 15 minutes plus tard, en bas de la page de la compilation, télécharge
   **NumSocial-windows** ou **NumSocial-mac**, et décompresse.
4. Windows : lance `NumSocial\NumSocial.exe` (SmartScreen : « Informations
   complémentaires » > « Exécuter quand même »). Mac : clic droit sur
   `NumSocial.app` > **Ouvrir**.

**En compilant sur ton Mac**

```bash
git clone https://github.com/derim00/numsocial.git && cd numsocial
./scripts/build-firmware.sh          # télécharge Epsilon, applique le patch, compile
.venv/bin/python3 app/build.py       # fabrique l'appli
open app/dist/NumSocial.app
```

### 2. Installer sur la calculatrice

1. Branche la calculatrice : elle affiche « Calculatrice connectée » (sinon :
   reset au dos, puis rebranche).
2. Sur la page de NumSocial (`http://127.0.0.1:8737`), coche **NumTube**,
   **NumChat**, **NumScreen** et/ou **NumBlocks**.
3. Clique **Installer sur la calculatrice** (environ 1 minute).

Le firmware officiel reste en place dans l'autre emplacement de la mémoire : un
reset au dos le ramène.

### 3. Utiliser

Laisse NumSocial ouvert sur l'ordinateur, puis ouvre l'appli voulue sur la
calculatrice. Les modes d'emploi détaillés sont dans chaque dépôt :

- **[Tutoriel NumTube](https://github.com/derim00/numtube#utilisation)**
- **[Tutoriel NumChat](https://github.com/derim00/numchat#tutoriel--première-connexion-à-snapchat)**
  (première connexion à Snapchat, touches, snaps)
- **[NumBlocks multijoueur](https://github.com/derim00/numblocks-multiplayer#ce-que-fait-le-multijoueur)**
  (rejoindre une partie, ouvrir ton monde)
- **[Tutoriel NumScreen](https://github.com/derim00/numscreen#tutoriel--autorisations-sur-mac)**
  (autorisations Mac, touches, jeux) ; le résumé est juste en dessous

## NumScreen : l'écran de l'ordinateur sur la calculatrice

### Autorisations (Mac, une seule fois)

macOS demande deux autorisations pour qu'une appli voie l'écran et pilote la
souris. Dans **Réglages Système > Confidentialité et sécurité** :

1. **Enregistrement de l'écran** (ou « Enregistrement de l'écran et audio ») :
   active **NumSocial**, puis quitte et relance NumSocial.
2. **Accessibilité** : active **NumSocial**.

Tant qu'il en manque une, la calculatrice l'écrit en bas de l'écran. Sous
Windows, il n'y a rien à autoriser.

### Touches

Ouvre **NumScreen** sur la calculatrice : l'écran du PC s'affiche en haut, le
mode et l'état de shift/alpha en bas.

| Touche | Mode souris | Mode jeu |
| --- | --- | --- |
| flèches | déplacent la souris (maintenir : de plus en plus vite) | flèches du clavier |
| `OK` | clic (deux fois vite : double clic ; maintenir : glisser) | `Espace` (sauter) |
| boîte à outils | clic droit (maintenu + flèches : tourner la caméra) | clic droit |
| `alpha` + `▲` `▼` | molette | |
| `x,n,t` | passer en mode jeu | revenir en mode souris |

Dans les deux modes :

| Touche | Sur l'ordinateur |
| --- | --- |
| lettres | par défaut : les lettres écrites au-dessus des touches |
| `shift` | passe aux chiffres, puis revient aux lettres |
| `alpha` | une majuscule (deux fois : majuscules verrouillées) ; en chiffres : le symbole jaune `[ ] { } _ = < >` |
| `var` | `Z` `Q` `S` `D` sur `8` `4` `5` `6`, pour jouer en AZERTY (`var` à nouveau : retour) |
| `EXE` / `retour` / `⌫` | `Entrée` / `Échap` / `Retour arrière` |
| `Ans` / `×10ˣ` | `Espace` / apostrophe |
| en chiffres : `exp` / `ln` / `log` | `Maj` / `Ctrl` / `Alt` de l'ordinateur |
| maison | arrêter le partage |

Une touche maintenue sur la calculatrice reste maintenue sur l'ordinateur.

**Pour jouer** (Roblox par exemple) : `x,n,t` passe en mode jeu, `var` met
`Z` `Q` `S` `D` sur `8` `4` `5` `6`, `OK` fait sauter. L'image fait 320×200 à
environ 15 images/s, avec un peu de retard : assez pour naviguer et jouer
tranquillement, pas pour un jeu de réflexes.

## Ce qu'il faut

- Une NumWorks **N0120** ou **N0115** en version officielle **26.4.0** (testé)
- Un câble USB qui transfère les données
- Un **Mac** (testé avec une calculatrice) ou un **PC Windows 10/11** (compilé
  et vérifié par GitHub, pas encore essayé avec une calculatrice)
- Pour NumChat : **Google Chrome** (ou Microsoft Edge sous Windows) et un compte
  Snapchat

## Comment c'est construit

```
            ┌──────────────────────── calculatrice NumWorks ────────────────────────┐
            │  Epsilon officiel + patch NumSocial : NumTube, NumChat, lien USB      │
            └───────────────────────────────┬───────────────────────────────────────┘
                                            │ USB (libusb, trames TMIA + CRC-16)
            ┌───────────────────────────────┴───────────────────────────────────────┐
            │  appli NumSocial (ordinateur) : installeur + passerelle                │
            │   ├─ NumTube : yt-dlp, ffmpeg, codec 4×4, sous-titres                  │
            │   ├─ NumChat : Playwright → Chrome (profil dédié) → Snapchat Web       │
            │   ├─ NumScreen : capture d'écran (mss), souris et clavier du système   │
            │   └─ NumBlocks : serveur de partie, liste publique (MQTT)             │
            └────────────────────────────────────────────────────────────────────────┘
```

- **Un seul firmware** pour toutes les applis. L'installeur y inscrit la
  version officielle de la calculatrice (sinon le noyau refuse de démarrer) et
  un masque qui cache les applis que tu n'as pas cochées.
- **Lien USB** repris de [Termia](https://github.com/Matinthereal/termia), avec
  deux corrections (débordement d'un tableau de requêtes, fin d'envoi jamais vue
  pendant une réception continue).
- **Pas de pilote à installer** : interface USB propriétaire avec descripteurs
  Microsoft OS (WinUSB) pour Windows.
- **NumBlocks** est une appli externe : le firmware NumSocial affiche les
  applis externes et leur prête son lien USB. L'ordinateur de celui qui ouvre
  son monde sert la partie ; les ordinateurs se trouvent par un broker MQTT
  public (aucun compte, aucun réglage de box). Le jeu, sous GPL, est compilé à
  partir de [son dépôt](https://github.com/derim00/numblocks-multiplayer) pendant la compilation de NumSocial.
- **NumScreen** reprend le codec de NumTube (blocs de 4×4 pixels, seuls ceux
  qui changent sont envoyés). La calculatrice envoie chaque appui et chaque
  relâchement de touche ; shift, alpha et la souris sont gérés par
  l'ordinateur, avec les interfaces du système (CoreGraphics sur Mac,
  SendInput sous Windows).

Ce dépôt contient le même code que [NumTube](https://github.com/derim00/numtube),
[NumChat](https://github.com/derim00/numchat) et [NumScreen](https://github.com/derim00/numscreen) : patch complet, appli, scripts,
tests.

## Avertissements

- Projet non officiel, sans lien avec NumWorks, YouTube, Snap Inc., Discord,
  Meta, Roblox, Mojang ou Microsoft. Les noms cités sont des marques de leurs propriétaires.
- Télécharger des vidéos avec yt-dlp va à l'encontre des conditions
  d'utilisation de YouTube.
- Piloter Snapchat Web automatiquement va à l'encontre des conditions
  d'utilisation de Snapchat et peut faire **verrouiller ton compte** : essaie
  d'abord avec un compte secondaire.
- Un firmware non officiel ne peut pas passer en mode examen.

## Licence

Le code de ce dépôt est sous licence
[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.fr),
comme Termia dont il reprend le lien USB. Voir [LICENSE](LICENSE).
