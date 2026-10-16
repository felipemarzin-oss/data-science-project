# kit-data-science-project
Projet Data Science – Livrables à rendre avant le 20 octobre : scripts Python de collecte, nettoyage et transformation des données (.py), notebooks d'exploration et d'entraînement des modèles (.ipynb), requirements.txt et README.md présentant le processus expérimental, les choix méthodologiques et les résultats.

PROBLEMATIQUE : Prédire la localisation géographique d'un individu à partir de ses préférences musicales

ORGA PROJET

- Le code pour avoir la donnée.py
        - question au prof ? 
- Vos notebook pour explorer la donnée .ipynb
        - .describe()
        - .shape()
        - .info()
        - .isnull() / .isna().sum()
        - voir le type de chaque colonne & le nom 
        - voir à quoi correspond le poid 
        - filtrer uniquement sur les colonnes qui nous interessent
Objectif : Voir quelles colonnes garder ? Quelle decision on prend pr les valeurs nulles ? 

- Le code pour nettoyer / transformer la donnée.py
        -> pandas ? 2 200 lignes donc pandas 
        - gérer les doublons 
        - gérer les valeurs NULL / NaN / 0 / vide 
        - scinder la zone géo (longitute / latitude) 
        - standardisation / normalisation sur les styles de musique 
        - encoder les styles de musique & la loc
        - renommer les colonnes 
        - maybe créer un index / identifiant ? 
        - PCA 
        - creation d'un fichier propre une fois nettoyé data_cleaned.ipynb


- les notebooks pour entrainer vos modèles .ipynb
        - clusteriser les differents style de musique 
        - clusteriser sur la loc des individus 
        - métriques :
            - regression
            - acc 
            - F1
            - recall 
            - matrice de confusion
        - choix de plusieurs modèles : randome forest, regression linéaire/logistiqu, clustering 
        - comparer les métriques des modèles 
        - Scinder le dataset en train et en test 
        - Entrainer les modèles 
            
- requirement.txt 
- README.md
    - Décrire votre processus experimental
    - Vox choix
    - Vos résultats 