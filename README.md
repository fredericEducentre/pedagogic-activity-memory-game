# 🧠 Memory Game --- Hackathon JS

## 📌 Présentation

Ce projet est une implémentation simple et visuelle du **jeu Memory**,
réalisée en JavaScript pour un hackathon.\
Le joueur doit retrouver toutes les paires d'images.\
Le jeu utilise un fichier `img.json` contenant les images (hébergées en
ligne), ce qui évite d'avoir un dossier d'assets.

------------------------------------------------------------------------

## 🗂 Structure du projet

    hackathon-algo-js/
    │
    ├── game/                    # Contient les fichiers principaux du jeu
    │   ├── index.html           # Interface du jeu (plateau, cartes…)
    │   ├── style.css            # Styles du plateau et des cartes
    │
    ├── img.json                 # Liste des cartes (id + URL image)
    ├── index.html               # (Optionnel) Page d’accueil ou redirection
    └── README.md                # Documentation du projet

------------------------------------------------------------------------

## 🎴 Format des cartes (`img.json`)

Le fichier JSON contient la liste des cartes uniques :

``` json
[
  { "id": 1, "img": "https://cdn.leonardo.ai/...lion.jpg" },
  { "id": 2, "img": "https://cdn.leonardo.ai/...elephant.jpg" },
  { "id": 3, "img": "https://cdn.leonardo.ai/...dolphin.jpg" },
  { "id": 4, "img": "https://cdn.leonardo.ai/...giraffe.jpg" },
  { "id": 5, "img": "https://cdn.leonardo.ai/...monkey.jpg" },
  { "id": 6, "img": "https://cdn.leonardo.ai/...tiger.jpg" },
  { "id": 7, "img": "https://cdn.leonardo.ai/...rhino.jpg" },
  { "id": 8, "img": "https://cdn.leonardo.ai/...snake.jpg" }
]
```

### Comment le jeu utilise ce fichier ?

-   le script JS charge ce fichier,
-   **chaque carte est dupliquée** → création des paires,
-   les 16 cartes sont **mélangées** puis affichées dans la grille.

------------------------------------------------------------------------

## 🎮 Règles du jeu

1.  Toutes les cartes commencent face cachée.\
2.  Le joueur retourne **deux cartes** :
    -   si elles correspondent → paire trouvée,
    -   sinon → elles se retournent après un délai.
3.  Le jeu continue jusqu'à ce que **toutes les paires** soient
    trouvées.
4.  Un **écran de fin de partie** apparaît à la victoire.

------------------------------------------------------------------------

## ⚙️ Fonctionnement du code

### 🔄 Initialisation

Le script :

-   importe / charge le JSON,
-   duplique les objets,
-   mélange le tableau final,
-   génère dynamiquement les cartes dans le DOM.

### 🖱 Gestion des clics

-   Le joueur clique → carte révélée.
-   Le jeu stocke la première carte sélectionnée.
-   Lors du second clic :
    -   comparaison des `id`,
    -   validation ou remise face cachée,
    -   gestion du timing pour éviter les double-clics rapides.

### 🎯 Variables gérées

-   cartes retournées,
-   paires trouvées,
-   nombre d'essais,
-   fin de partie.

------------------------------------------------------------------------

## ▶️ Comment lancer le jeu

### 1. Cloner le projet

``` bash
git clone https://github.com/ElieMyl/hackathon-algo-js
```

### 2. Aller dans le dossier

``` bash
cd hackathon-algo-js
```

### 3. Lancer le jeu

Il suffit d'ouvrir :

    game/index.html

➡️ Aucun serveur n'est nécessaire.

Si tu préfères l'ouvrir via un serveur local :

``` bash
cd game
python3 -m http.server 5500
```

------------------------------------------------------------------------

## 🤝 Contribuer

1.  Créer une branche :

``` bash
git checkout -b feature/documentation
```

2.  Commit :

``` bash
git add .
git commit -m "Added documentation for project"
```

3.  Push :

``` bash
git push origin feature/documentation
```

4.  Ouvrir une Pull Request sur GitHub.

------------------------------------------------------------------------

## 📜 Licence

Projet open-source, utilisable librement dans un cadre éducatif ou
expérimental.