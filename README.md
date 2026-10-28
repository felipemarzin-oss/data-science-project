# kit-data-science-project


Projet Data Science – Livrables à rendre avant le 20 octobre : scripts Python de collecte, nettoyage et transformation des données (.py), notebooks d'exploration et d'entraînement des modèles (.ipynb), requirements.txt et README.md présentant le processus expérimental, les choix méthodologiques et les résultats.

PROBLEMATIQUE : Prédire la localisation géographique d'un individu à partir de ses préférences musicales

ORGA PROJET

Le code pour avoir la donnée.py - où on a eu notre donnée ; si à partir d'un site en ligne pas besoin de code - mettre le lien de la donnée dans le README

Vos notebook pour explorer la donnée 1 : visualisations.ipynb - .describe() - .shape() - .info() - .isnull() / .isna().sum() - voir le type de chaque colonne & le nom - voir à quoi correspond le poid - filtrer uniquement sur les colonnes qui nous interessent Objectif : Voir quelles colonnes garder ? Quelle decision on prend pr les valeurs nulles ?

Le code pour nettoyer / transformer la donnée test.ipynb rendu.py -> pandas ? 2 200 lignes donc pandas - gérer les doublons - gérer les valeurs NULL / NaN / 0 / vide - scinder la zone géo (longitute / latitude) - standardisation / normalisation sur les styles de musique - encoder les styles de musique & la loc - renommer les colonnes - maybe créer un index / identifiant ? - PCA - creation d'un fichier propre une fois nettoyé data_cleaned.ipynb

les notebooks pour entrainer vos trainning_eval.ipynb - clusteriser les differents style de musique - clusteriser sur la loc des individus - variable cible : la region (la loc) - métriques : - acc (pas mal ds notre cas) - F1 - recall - matrice de confusion - choix de plusieurs modèles : on compare random forest à regression logistique, clustering (kmeans) - comparer les métriques des modèles - Scinder le dataset en train et en test - Entrainer les modèles

requirement.txt

README.md (fil rouge : difficultés, hypothèses, décisions, etc)

Décrire votre processus experimental
Vox choix
Vos résultats
