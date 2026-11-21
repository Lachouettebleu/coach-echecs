# ♞ Coach d’échecs

Site 100 % statique (un seul fichier `index.html`) : jouer contre un coach, mode classé (Elo), analyse de parties PGN avec Stockfish, bilan de partie façon chess.com, ouvertures à débloquer, problèmes tactiques, statistiques et six coachs au choix.

## Publier sur GitHub Pages (5 minutes, sans ligne de commande)

1. Créez un compte sur <https://github.com>, puis **New repository** : nom `coach-echecs`, **Public**, **Create repository**.
2. Cliquez sur **uploading an existing file**, glissez `index.html`, `README.md` et `.nojekyll`, puis **Commit changes**.
3. **Settings → Pages → Build and deployment → Source : Deploy from a branch**, branche **main**, dossier **/(root)**, **Save**.
4. Après 1 à 2 minutes, le site est en ligne : `https://VOTRE-PSEUDO.github.io/coach-echecs/`.

Pour modifier le site plus tard : ouvrez `index.html` sur GitHub, crayon ✏️, modifiez, **Commit changes**.

## Le coach IA, comment ça marche hors de Claude ?

Dans Claude, la page appelait Claude directement. Sur un site GitHub ce n’est plus possible, il y a donc trois niveaux :

| Niveau | Fonctionnement | Coût |
|---|---|---|
| **Sans IA** (par défaut) | Le jeu, Stockfish, le bilan, les ouvertures et les problèmes marchent. Chaque coach garde ses phrases types pour commenter les coups. | gratuit |
| **Bouton « Ouvrir dans Claude »** | Les boutons « Demander à Claude… » ouvrent claude.ai avec la question toute prête (position, coup, profil, personnalité du coach). La réponse s’affiche dans Claude. | gratuit (compte Claude) |
| **Clé API personnelle** | Onglet **Coach** → collez votre clé Anthropic. Les avis, explications et la discussion s’affichent directement dans le site. | facturé à l’usage sur votre compte Anthropic |

La clé est stockée dans le navigateur de la personne (localStorage) et n’est jamais écrite dans le code. **Ne mettez jamais votre clé dans `index.html`** : le site est public, tout le monde pourrait la lire et l’utiliser. Si vous voulez qu’un site public ait un coach IA pour tous sans clé personnelle, il faut un petit serveur intermédiaire (Cloudflare Workers, Vercel…) qui garde la clé et limite l’usage ; je peux vous le préparer.

## Stockfish

Par défaut le site charge Stockfish.js et chess.js depuis cdnjs (internet requis). Si Stockfish ne peut pas se charger, un moteur intégré plus léger prend le relais.
Pour héberger Stockfish vous-même (plus fiable) : téléchargez
`https://cdnjs.cloudflare.com/ajax/libs/stockfish.js/10.0.2/stockfish.js`, mettez-le dans un dossier `stockfish/` du dépôt (`stockfish/stockfish.js`) : le site l’utilise en priorité. Stockfish est sous licence **GPLv3** : dans ce cas, ajoutez aussi un fichier de licence GPLv3 à votre dépôt.

## Sauvegarde

Profil, Elo, parties analysées, points et ouvertures débloquées sont enregistrés dans le **navigateur** de chaque visiteur (localStorage). Changer d’appareil ou vider les données du navigateur les efface : utilisez **Exporter / Importer** en bas de page pour garder une copie.

## Licences

chess.js (BSD-2), Stockfish.js (GPLv3). Les coachs sont des personnages simulés, inspirés du style public de leurs modèles ; ce ne sont pas leurs vraies paroles.
