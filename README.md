Analyse de données sur les animés 

Auteur : Aboulfaid Hafsa
Technologies : Python ; Pandas ; Matplotlib ; Jupyter Notebook

1. Présentation du projet

Ce projet consiste à explorer et analyser un dataset d’animés à l’aide de Python.
L’objectif est de comprendre :

La distribution des notes et des épisodes

Les studios les plus productifs

Les genres d’animés les plus populaires

La corrélation entre les épisodes (meilleurs/pire épisode) et la note globale

Le projet est réalisé sous forme de Jupyter Notebook, interactif et visuel, avec des graphiques colorés et des analyses simples à suivre.

2. Structure du projet
anime_project/
│
├─ data/
│   └─ anime_dataset.csv         # Dataset contenant les informations sur les animés
│
├─ notebooks/
│   └─ analyse_animes.ipynb      # Notebook principal contenant tout le code et les graphiques
│
├─ README.md                     # Ce fichier
└─ requirements.txt              # Dépendances Python

3. Contenu du notebook

Le notebook analyse_animes.ipynb contient les étapes suivantes :

3.1 Préparation de l’environnement

Installation des bibliothèques : pandas et matplotlib

Import des packages :

import pandas as pd
import matplotlib.pyplot as plt
plt.rcParams['figure.figsize'] = [10, 6]
plt.rcParams['axes.grid'] = True

3.2 Chargement et exploration des données

Lecture du CSV contenant les animés

Affichage des colonnes et des premières lignes

df = pd.read_csv('data/anime_dataset.csv')
print(df.head())
print(df.columns.to_list())


Statistiques descriptives des colonnes numériques :

df.describe().round(2)

3.3 Sélections et transformations

Sélection de colonnes clés : Anime, Note_Globale, Studio

Mise en majuscules des noms d’animés :

df['Anime'].str.upper()


Extraction du genre principal :

df['Genre_Principal'] = df['Genre_Tags'].str.split(' / ').str[0]


Conversion de Date_Pub en datetime et extraction de l’année :

df['Date_Pub'] = pd.to_datetime(df['Date_Pub'])
df['Annee'] = df['Date_Pub'].dt.year

3.4 Analyse des notes

Tri par Note_Globale

Sélection des animés avec note > 8.5

Identification du meilleur animé et du pire animé :

note_max = df['Note_Globale'].max()
meilleur = df[df['Note_Globale'] == note_max]['Anime'].values[0]


Répartition des animés par Status et par Studio

3.5 Visualisations

Histogramme des notes (couleur rose)

Barres par statut (couleurs rose, rouge, mauve)

Nuage de points : Note vs Nombre d’épisodes (vert)

Courbe du nombre d’animés par année

Top 10 des genres d’animés

Corrélation Note Globale vs Meilleur/Pire épisode

Exemple pour l’histogramme :

plt.hist(df['Note_Globale'], bins=10, color='#ff69b4', edgecolor='white')
plt.axvline(df['Note_Globale'].mean(), color='red', linestyle='--', label='Moyenne')
plt.title("Distribution des notes d'animés")
plt.xlabel("Note")
plt.ylabel("Nombre d'animés")
plt.legend()
plt.show()

4. Instructions pour lancer le projet

Cloner le projet ou télécharger le ZIP

git clone https://github.com/ton-utilisateur/anime_project.git
cd anime_project


Installer les dépendances

pip install -r requirements.txt


Ou installer manuellement :

pip install pandas matplotlib


Lancer le notebook

jupyter notebook notebooks/analyse_animes.ipynb


Explorer les graphiques et les analyses

Les cellules du notebook sont interactives et commentées pour faciliter la lecture.

Les graphiques utilisent des couleurs personnalisées pour une meilleure visualisation.

5. Fichiers importants

data/anime_dataset.csv : dataset source

notebooks/analyse_animes.ipynb : notebook avec tout le code et visualisations

requirements.txt : liste des bibliothèques Python nécessaires

6. Licence

Projet personnel – Aboulfaid Hafsa – 2026



