# 🎮 The Loom Arcade

Outil de jeux de vocabulaire anglais-français pour le secondaire. Un seul fichier HTML, aucune installation, aucun serveur à gérer. **Une connexion Internet est nécessaire à l'ouverture** : l'application charge React et Babel depuis un service externe.

Fait partie de la [Lesson Loom Suite](https://lessonloom.fr).

---

## Démo

Ouvrir `the-loom-arcade.html` dans un navigateur. C'est tout.

---

## Principe

1. **Le prof** crée des listes de paires (ex: *dog → chien*)
2. **Le prof** partage un lien vers une liste
3. **L'élève** ouvre le lien et joue à 10 jeux différents avec cette liste

---

## 10 jeux

### Classiques

| Jeu | Description |
|---|---|
| 🃏 **Memory** | Retourner les cartes pour associer les paires EN ↔ FR |
| 🎴 **Flashcards** | Carte FR → clic pour retourner → EN, auto-évaluation |
| 💀 **Le pendu** | Deviner le mot anglais lettre par lettre, 6 vies |
| 🟩 **Word Guess** | Style Wordle — 6 essais, clavier AZERTY coloré (vert/jaune/gris) |
| 🔍 **Mots mêlés** | Grille auto-générée, 8 directions, choix du nombre de mots |

### Arcade

| Jeu | Description |
|---|---|
| ⚡ **Word Rush** | QCM chronométré avec combo 🔥 et vitesse croissante |
| 🧱 **Word Breaker** | Casse-briques — casse les lettres dans l'ordre pour former le mot |
| 👻 **Vocab Maze** | Ramasse les lettres sur une grille en évitant le fantôme |
| 🔨 **Whack-a-Word** | Tape la bonne taupe avant qu'elle disparaisse |
| 🧺 **Word Catcher** | Attrape la bonne traduction française avant qu'elle touche le sol |

La plupart des jeux demandent de retrouver le mot anglais. **Word Catcher fait l'inverse** : le mot anglais est affiché, l'élève attrape sa traduction française — un travail de compréhension, quand les autres exercent la production.

---

## Fonctionnalités

### Saisie rapide
- **Collage instantané** : colle une liste depuis Word, Excel, un site… les paires sont détectées automatiquement
- Séparateurs reconnus : `tab` `;` `:` `→` `=` `–` ou 2+ espaces
- Saisie manuelle aussi disponible (champ par champ)

> **Un conseil sur le côté anglais : préférez un seul mot.**
>
> Quatre jeux — Word Guess, Mots mêlés, Vocab Maze et Word Breaker — font construire le mot lettre par lettre. Ils retirent les espaces : `a dog` y devient `ADOG`, et l'élève voit une orthographe qui n'existe pas.
>
> Écrivez donc `dog → chien` plutôt que `a dog → un chien`. Pour un verbe à particule ou une expression figée — `get up`, `look after`, `a lot of` — l'espace est inévitable : ces entrées restent parfaites pour Memory, Flashcards, Word Rush, Whack-a-Word, Word Catcher et le pendu, qui les affichent en entier. Évitez simplement de les envoyer aux quatre jeux de lettres.

### Scoring
- **3 étoiles par mot** (critères adaptés par jeu)
- Écran récap coloré avec grille de maîtrise par mot
- Bouton **"Rejouer les ratés"** pour relancer uniquement les mots ≤ 1 étoile
- **Bilan de session** cumulé (remis à zéro si on quitte la page)

### Word Catcher — le sens inverse
Le mot anglais reste affiché en haut ; quatre traductions tombent du ciel, une seule est la bonne, les autres sont tirées de votre propre liste. L'élève déplace un panier aux flèches ou au doigt.

- Attraper le bon mot fait passer au suivant ; attraper un mauvais coûte une vie, sur les trois disponibles
- Laisser tomber le bon mot ne coûte pas de vie : il revient **une fois**, puis il est compté sans étoile
- La vitesse augmente d'un cran tous les cinq mots réussis, jusqu'à un plafond
- **Quatre paires minimum** dans la liste, puisqu'il faut une bonne réponse et trois leurres crédibles

### Guide d'accueil
Un guide s'affiche au premier lancement côté professeur : créer une liste, jouer, partager par fichier ou par lien, prévisualiser en mode élève. Il ne réapparaît plus ensuite, et reste accessible par le bouton **Guide** de la barre du haut. Les élèves arrivant par un lien partagé ne le voient jamais.

### Mode prof / élève
- **Prof** : crée et gère des listes sauvegardées (localStorage), accès à tous les jeux
- **Élève** : arrive via un lien partagé, voit uniquement les jeux pour cette liste
- Bouton 👁️ pour prévisualiser en mode élève
- Bouton 🔗 pour copier le lien de partage

### Partage
Le lien de partage encode la liste en base64 dans l'URL (`#shared=...`). Aucun serveur, aucune base de données — tout est dans le lien.

---

## Limites

- **Une connexion Internet est nécessaire à chaque ouverture**, y compris pour un fichier téléchargé. Sans connexion, la page reste blanche.
- **Certains réseaux d'établissement filtrent les services externes** : testez depuis votre poste avant de diffuser à vos élèves.
- **Les entrées à plusieurs mots sont mal rendues dans quatre jeux** : Word Guess, Mots mêlés, Vocab Maze et Word Breaker suppriment les espaces, ce qui transforme `get up` en `GETUP`. Le pendu, lui, conserve l'espace correctement. Les cinq autres jeux affichent le mot entier.
- **Au-delà d'une cinquantaine de paires**, le lien de partage devient très long — environ 3 000 caractères pour 50 paires, 6 200 pour 100 — et certaines messageries ou ENT le coupent. Un lien coupé donne une liste vide : préférez alors le fichier téléchargé.

---

## Installation

Il n'y en a pas. C'est un fichier HTML unique.

### Option 1 : en local
Télécharger `the-loom-arcade.html` et l'ouvrir dans un navigateur.

### Option 2 : sur un site
Héberger le fichier sur n'importe quel serveur web ou GitHub Pages.

```html
<a href="https://votre-site.fr/the-loom-arcade.html" target="_blank">
  🎮 The Loom Arcade
</a>
```

### Option 3 : GitHub Pages
1. Forker ce repo
2. Activer GitHub Pages (Settings → Pages → Source: main branch)
3. Le jeu est accessible à `https://votre-username.github.io/the-loom-arcade/the-loom-arcade.html`

---

## Stack technique

- **React 18** via CDN (pas de build, pas de node_modules)
- **Babel standalone** pour la transpilation JSX dans le navigateur
- **localStorage** pour sauvegarder les listes du prof
- **Aucune dépendance serveur** — tout tourne côté client

---

## Structure du projet

```
the-loom-arcade/
├── the-loom-arcade.html   ← le fichier unique, prêt à l'emploi
├── README.md              ← ce fichier
└── LICENSE                ← AGPLv3
```

---

## Personnalisation

Le fichier est auto-contenu. Pour modifier :

- **Couleurs / design** : chercher l'objet `C = {` en haut du script (tokens de design)
- **Ajouter un jeu** : créer un composant React, l'ajouter au tableau `GAMES` et à l'objet `GM`
- **Changer la langue** : tous les textes FR sont en dur dans le code

---

## Crédits

- Design inspiré de l'univers Mario Bros (nuages, tuyaux, couleurs)

---

## Licence

**GNU Affero General Public License v3 (AGPLv3)** — © 2026 Maïwena Gadegbeku

Vous êtes libre d'utiliser, d'étudier, de modifier et de redistribuer cet outil. En contrepartie, toute version modifiée qui est redistribuée **ou mise à disposition sur un serveur** doit être publiée sous cette même licence, code source compris.

Une condition supplémentaire s'ajoute, au titre de l'article 7(b) : toute version modifiée diffusée publiquement doit créditer visiblement l'autrice originale, dans l'interface ou dans la documentation :

> "Based on The Loom Arcade by Maïwena Gadegbeku"

Ce crédit ne peut être ni retiré, ni dissimulé aux utilisateurs.

Voir le fichier [LICENSE](LICENSE) pour le texte complet, et <https://www.gnu.org/licenses/agpl-3.0.html> pour la licence officielle.
