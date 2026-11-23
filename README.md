# 🏠 Analyse des ventes immobilières en France (2021 – 2023)

Un projet de **data science** qui explore, nettoie et prépare plus de **3 millions de ventes immobilières** réalisées en France entre 2021 et 2023.


---

## 💡 C'est quoi, ce projet ?

Quand on achète ou vend un bien, l'État enregistre la transaction : prix, surface, type de bien, adresse, date… Ces informations sont publiques (base **DVF**, *Demandes de valeurs foncières*).

Le problème : les données brutes sont **énormes, incomplètes et pleines d'anomalies** (doublons, prix à 0, valeurs extrêmes…).

Ce projet répond à trois questions simples :

1. À quoi ressemblent les prix et les surfaces des biens vendus ?
2. Comment les prix ont-ils évolué entre 2021 et 2023, selon le type de bien ?
3. Comment transformer ces données brutes en un fichier **propre**, prêt pour du machine learning ?

---

## 📦 Les données

| Élément | Détail |
|---|---|
| Source | [Real Estate Dataset – Kaggle](https://www.kaggle.com/datasets/nechbamohammed/real-estate-dataset) |
| Période | 2021, 2022, 2023 (un fichier par an) |
| Taille brute | environ 3,1 millions de lignes et 41 colonnes |
| Variables principales | `valeur_fonciere` (prix), `surface_reelle_bati`, `surface_terrain`, `nombre_pieces_principales`, `type_local`, `nom_commune`, `date_mutation` |

> ⚠️ **Les fichiers de données ne sont pas dans ce dépôt** : ils sont beaucoup trop lourds pour GitHub (de 180 Mo à 660 Mo chacun). Il faut les télécharger soi-même (voir plus bas).

---

## 📁 Organisation du projet

```
projet/
├── Analyse des ventes immobilières en France.ipynb        # Le notebook : toute l'analyse, expliquée pas à pas
├── README.md              # Ce fichier
├── .gitignore             # Empêche d'envoyer les gros fichiers sur GitHub
└── dataset/               # À créer vous-même (non versionné)
    ├── full_2021.csv
    ├── full_2022.csv
    └── full_2023.csv
```

---

## 🔎 Ce que fait le notebook

Le notebook est organisé en 7 parties, chacune introduite par un petit texte explicatif :

| # | Étape | En clair |
|---|---|---|
| 1 | **Chargement** | Lecture des 3 fichiers et fusion en un seul tableau |
| 2 | **Statistiques descriptives** | Moyenne, médiane, écart-type… du prix et des surfaces |
| 3 | **Valeurs aberrantes** | Repérage des ventes « hors norme » avec la méthode IQR |
| 4 | **Visualisations** | Boxplots, nuages de points, matrice de corrélation |
| 5 | **Nettoyage** | Suppression des doublons, remplissage des valeurs manquantes, correction des incohérences |
| 6 | **Évolution des prix** | Prix moyen par année et par type de bien |
| 7 | **Préparation finale** | Encodage, normalisation et export du CSV propre |

### Les choix de nettoyage

- **Doublons** : supprimés (plus de 220 000 lignes identiques détectées).
- **Valeurs manquantes** : médiane pour les colonnes numériques, valeur la plus fréquente pour les colonnes de texte.
- **Incohérences** : on garde seulement les ventes avec un prix supérieur à 0 et des surfaces positives ou nulles.
- **Nouvelle variable** : `prix_m2` (prix ÷ surface bâtie).
- **Encodage** : `type_local` transformé en colonnes 0/1 (*one-hot*).
- **Normalisation** : `RobustScaler`, choisi parce qu'il résiste bien aux valeurs extrêmes, très nombreuses ici.

---

## 📊 Quelques constats

- Le **prix médian** est d'environ **150 000 €**, alors que la **moyenne** dépasse **350 000 €** : quelques ventes très chères tirent la moyenne vers le haut.
- Les distributions sont **très asymétriques** : beaucoup de petites ventes, quelques ventes énormes.
- La **corrélation** entre le prix et les surfaces est **faible** : la surface seule n'explique pas le prix.
- Parmi les types de biens, les **locaux industriels ou commerciaux** ont de loin le prix moyen le plus élevé, et il augmente chaque année.

*(Ces chiffres sont ceux affichés dans le notebook ; ils peuvent varier selon l'ordre d'exécution des cellules.)*

---

## 🚀 Lancer le projet chez vous

### 1. Récupérer le projet

```bash
git clone https://github.com/MalakSaidani26/NOM_DU_DEPOT.git
cd NOM_DU_DEPOT
```

### 2. Installer Python et les bibliothèques

Python 3.10 ou plus récent est recommandé.

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Télécharger les données

1. Allez sur [la page Kaggle du dataset](https://www.kaggle.com/datasets/nechbamohammed/real-estate-dataset).
2. Téléchargez `full_2021.csv`, `full_2022.csv` et `full_2023.csv`.
3. Créez un dossier `dataset/` à côté du notebook et placez-y les trois fichiers.

### 4. Adapter les chemins dans le notebook

Dans le code, les chemins pointent vers l'ordinateur de l'auteure :

```
C:\Users\malek saidani\Desktop\python DSSD\projet ds\dataset\full_2021.csv
```

Remplacez-les par le chemin de **votre** dossier, par exemple `dataset/full_2021.csv`. Le chemin d'export du fichier final (dernière cellule de code) est à adapter de la même façon.

### 5. Ouvrir le notebook

```bash
jupyter notebook projet_ds.ipynb
```

Puis exécutez les cellules **dans l'ordre**, de haut en bas.

> 💾 **Mémoire :** les trois fichiers fusionnés pèsent plusieurs Go en mémoire. Prévoyez un ordinateur avec au moins 8 Go de RAM (16 Go, c'est mieux).

---

## 🛠️ Technologies utilisées

- **Python**
- **pandas** et **NumPy** pour manipuler les données
- **Matplotlib** et **Seaborn** pour les graphiques
- **scikit-learn** pour la normalisation (`RobustScaler`)
- **Jupyter Notebook**

---



## 👩‍💻 Auteure

**Malak Saidani** 

🔗 [LinkedIn](https://linkedin.com/in/malak-saidani-019b68334)
