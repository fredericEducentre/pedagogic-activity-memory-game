# 🧠 Memory Game — Hackathon JS

## 📌 Présentation

Ce projet est une implémentation évoluée du **jeu Memory**, réalisée en JavaScript dans le cadre d’un hackathon.  
Le joueur doit retrouver les paires de cartes en fonction du mode de jeu.

Le système supporte désormais **trois types de paires** :

### **🟦 Cas 1 — Image + Question / Image + Réponse**
- Carte 1 : image + question  
- Carte 2 : image + réponse  

### **🟩 Cas 2 — Image / Image**
- Carte 1 : image seulement  
- Carte 2 : image seulement  

### **🟧 Cas 3 — Question / Réponse**
- Carte 1 : question  
- Carte 2 : réponse  

Le fichier `img.json` permet d'activer automatiquement l’un ou l’autre de ces modes selon les données fournies.

---

## 🗂 Structure du projet

```
hackathon-algo-js/
│
├── game/                    # Dossier principal du jeu
│   ├── index.html           # Interface du jeu (plateau, cartes…)
│   ├── style.css            # Styles du plateau et des cartes
│
├── img.json                 # Liste des cartes (images, questions, réponses…)
├── index.html               # (Optionnel) Page d’accueil ou redirection
└── README.md                # Documentation du projet
```

---

## 🎴 Format des cartes (`img.json`)

Le fichier JSON peut contenir **trois formats différents**, automatiquement reconnus :

### ✅ **Cas 1 — Image + Question/Réponse (mode pédagogique visuel)**

```json
{
  "id": 1,
  "img": "https://cdn.leonardo.ai/...giraffe.jpg",
  "question": "Quel animal a un très long cou ?",
  "answer": "La girafe"
}
```

→ Produit deux cartes :

- Carte A = image + question  
- Carte B = image + réponse  

---

### ✅ **Cas 2 — Image seule**

```json
{
  "id": 2,
  "img": "https://cdn.leonardo.ai/...lion.jpg"
}
```

→ Produit deux cartes **identiques** contenant seulement l'image.

---

### ✅ **Cas 3 — Question / Réponse**

```json
{
  "id": 3,
  "question": "2 + 2 ?",
  "answer": "4"
}
```

→ Produit :

- Carte A = question  
- Carte B = réponse  

---

### 🧠 Détection automatique

Le script identifie automatiquement le mode à utiliser en fonction des clés présentes :

| Présent dans JSON | Mode activé |
|-------------------|-------------|
| `img` + `question` + `answer` | Cas 1 |
| `img` seul | Cas 2 |
| `question` + `answer` sans `img` | Cas 3 |

---

## 🎮 Règles du jeu

1. Toutes les cartes commencent face cachée.  
2. Le joueur retourne **deux cartes** :
   - si elles correspondent → paire trouvée,  
   - sinon → elles se retournent après un délai.  
3. Le jeu se poursuit jusqu'à ce que toutes les paires soient trouvées.  
4. Un **écran de victoire** affiche le score et les coups effectués.  

---

## ⚙️ Fonctionnement du code

### 🔄 Initialisation

Le script :

- charge dynamiquement `img.json`,
- détermine automatiquement le mode de chaque carte,
- génère deux cartes par élément JSON selon les 3 cas,
- mélange l’ensemble,
- affiche la grille.

### 🧠 Construction des cartes

Selon le contenu, la carte peut afficher :

- une image seule,
- une image + texte,
- du texte seul (question ou réponse).

### 🖱 Logique de clic

- Gestion complète des clics (blocage pendant animation),
- Comparaison par `id`,
- Désactivation des paires trouvées,
- Mise à jour du score et du compteur de coups.

### 🏁 Fin de partie

Un écran de victoire s’affiche avec :

- le score final,
- le nombre total de coups,
- un bouton pour relancer une nouvelle partie.

---

## ⚡ Intégration Educentre (optionnelle)

Le jeu expose deux fonctions globales :

### ✔ **startMemoryGame(images)**  
Permet à Educentre d'envoyer un dataset personnalisé.

### ✔ **onMemoryGameEnd(result)**  
Callback permettant d’obtenir les résultats :

```json
{
  "score": 80,
  "moves": 12,
  "matchedPairs": 8,
  "totalPairs": 8,
  "timestamp": 1732342045500
}
```

Compatible également avec `postMessage` si le jeu est intégré dans un `<iframe>`.

---

## ▶️ Comment lancer le jeu

### 1. Cloner le projet

```bash
git clone https://github.com/ElieMyl/hackathon-algo-js
```

### 2. Aller dans le dossier

```bash
cd hackathon-algo-js
```

### 3. Lancer le jeu

Ouvre directement :

```
game/index.html
```

➡️ Aucun serveur n’est nécessaire.

### Option serveur local (recommandé pour fetch JSON)

```bash
cd game
python3 -m http.server 5500
```

Puis ouvrir :

```
http://localhost:5500
```

---

## 🤝 Contribuer

1. Créer une branche :

```bash
git checkout -b feature/documentation
```

2. Commit :

```bash
git add .
git commit -m "Added documentation for project"
```

3. Push :

```bash
git push origin feature/documentation
```

4. Ouvrir une Pull Request.

---

## 📜 Licence

Projet open-source, libre d’utilisation dans un cadre éducatif ou expérimental.