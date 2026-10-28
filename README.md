# Prédire la région d'un individu à partir de ses goûts musicaux

Projet Data Science – Télécom Paris, Kit Data Science
Groupe : Sara, Philippe, Mihary, Eleonore

---

## 1. La problématique

Est-ce qu'on peut deviner dans quelle région française vit quelqu'un juste en sachant quels genres de musique il écoute ?

C'est une question de classification. La variable à prédire (la cible) est la **région**. Les variables explicatives sont les **préférences musicales** déclarées par chaque personne.

---

## 2. Les données

### Source

Nous avons utilisé l'enquête **HADOPI 2020** sur les pratiques musicales des Français.

- Lien vers les données : `https://www.data.gouv.fr/datasets/pratiques-decoute-de-musique-en-ligne-2020`
- Les fichiers bruts sont rangés dans `documentation/` (`hadopi-2020-musique-data.csv`, `.ods`)
- Un descriptif des jeux de données est disponible dans `documentation/datasets.md`

Les données ont été téléchargées directement depuis le site. Il n'y a donc pas de script de collecte.

### Ce qu'on a gardé

Après nettoyage, le jeu de données final (`Dataset/dataset_musique_region.csv`) contient :

| Élément | Valeur |
|---|---|
| Nombre de personnes | 1 986 |
| Variables explicatives | 13 genres musicaux (0 = n'écoute pas, 1 = écoute) |
| Variable cible | la région (12 régions) |

Les 13 genres : Variété française, Pop/Rock, Rap/Hip-Hop, Classique, Jazz, Dance, Électronique, Métal, R&B, Soul, Reggae, Musiques du monde, Autres genres.

---

## 3. Organisation du dépôt

```
data-science-project/
├── Dataset/
│   └── dataset_musique_region.csv     # données nettoyées, prêtes pour la modélisation
├── documentation/                     # données brutes + descriptif
├── notebooks/
│   ├── exploration.ipynb              # première découverte des données
│   ├── nettoyage.ipynb                # nettoyage
│   ├── transformation.ipynb           # transformations / encodage
│   ├── nettoyage_transformation.ipynb # version regroupée nettoyage + transformation
│   └── A_COMPLETER_FICHIER_FINAL.ipynb # entraînement et évaluation des modèles
├── scripts/                           # scripts .py
├── requirements.txt
└── README.md
```

---

## 4. Processus expérimental

On a suivi quatre étapes, dans cet ordre.

### Étape 1 – Explorer la donnée (`exploration.ipynb`)

L'idée : comprendre ce qu'on a entre les mains avant de toucher à quoi que ce soit.

Ce qu'on a regardé :
- la taille du jeu (`.shape`), les types de colonnes (`.info()`), les statistiques (`.describe()`)
- les valeurs manquantes (`.isna().sum()`)
- le sens de chaque colonne, y compris la colonne de **poids** de l'enquête
- quelles colonnes servent vraiment notre problématique

**Répartition des répondants par région**

![Répartition des répondants par région](images/repartition_regions.png)

On voit tout de suite un déséquilibre. L'Île-de-France compte environ 440 répondants, alors que le Centre-Val de Loire en a moins de 100. Ce point compte pour la suite : un modèle pourrait avoir tendance à prédire « Île-de-France » par défaut.

**Part des personnes qui écoutent chaque genre, par région**

![Heatmap genres par région](images/heatmap_genres_regions.png)

C'est le graphique le plus parlant du projet. Les couleurs sont presque identiques d'une ligne à l'autre. La Variété française et la Pop/Rock dominent partout, le Métal et les « Autres genres » sont faibles partout. Autrement dit, **les goûts musicaux se ressemblent beaucoup d'une région à l'autre**. Ça annonce déjà que la prédiction sera difficile.

### Étape 2 – Nettoyer (`nettoyage.ipynb`)

Le jeu fait environ 2 200 lignes, donc **pandas** suffit largement.

Ce qu'on a fait :
- sélection des colonnes utiles (genres musicaux + région)
- gestion des doublons
- gestion des valeurs manquantes
- renommage des colonnes pour qu'elles soient lisibles

**Valeurs manquantes : suppression ou remplacement ?**

On a testé les deux méthodes.

Choix retenu : **suppression** des lignes incomplètes. Les deux méthodes donnaient le même nombre de lignes au final (1 986), donc la suppression était la plus simple et n'introduisait pas de valeurs inventées.

![Vérification méthode valeurs manquantes](images/verif_valeurs_manquantes.png)

### Étape 3 – Transformer (`transformation.ipynb`)

- **Encodage des genres** : chaque genre devient une colonne binaire (0/1)
- **Encodage de la région** : la région est transformée en étiquette numérique pour les modèles
- `[normalisation]`

Le fichier final est exporté dans `Dataset/dataset_musique_region.csv`.

### Étape 4 – Prédiction & Entraînement  (`A_COMPLETER_FICHIER_FINAL.ipynb`)

1. Séparation du jeu en **train** et **test** `[ex. 80 % / 20 %]`
2. Entraînement de plusieurs modèles :
   - **Random Forest**
   - **Régression logistique**
   - **K-Means** (non supervisé, pour voir si des groupes de goûts se dessinent)
3. Comparaison avec plusieurs métriques :
   - **Accuracy** : part de bonnes prédictions
   - **Précision / Recall / F1-score** : plus fiables que l'accuracy quand les classes sont déséquilibrées
   - **Matrice de confusion** : pour voir quelles régions sont confondues entre elles

---

## 5. Résultats

| Modèle | Accuracy | F1-score | Recall |
|---|---|---|---|
| Random Forest | `[À COMPLÉTER]` | `[À COMPLÉTER]` | `[À COMPLÉTER]` |
| Régression logistique | `[À COMPLÉTER]` | `[À COMPLÉTER]` | `[À COMPLÉTER]` |
| Hasard (référence, 1 chance sur 12) | ≈ 8 % | – | – |

![Matrice de confusion](images/matrice_confusion.png)

**Ce qu'on en retient** `Nous avons clairement pas assez de données pour pouvoir répondre à notre problématique initiale.`

---

## 6. Difficultés rencontrées

- **Des goûts très homogènes** : la heatmap montre peu de différences entre régions. Le signal à exploiter est faible.
- **Des classes déséquilibrées** : l'Île-de-France pèse beaucoup plus que les autres régions. L'accuracy seule peut donner une image trop optimiste.
- **Des variables pauvres** : 13 colonnes binaires (écoute / n'écoute pas), c'est peu d'information pour distinguer 12 régions.
- **Travail en groupe** : plusieurs versions de notebooks sur des branches différentes, à fusionner proprement avec Git.

---

## 7. Conclusion

`Problématique beaucoup trop vaste en vue des données qu'on avait au départ. On a remarqué beaucoup de désiquilibre sur certaine régions comme l'Ile-de-france et l'Auvergne. A COMPLETER !!!!!!!!!!!!!!!`

Piste de réflexion : si les résultats sont proches du hasard, ce n'est pas un échec du modèle. C'est un résultat en soi. Il montre que, dans ces données, les préférences musicales ne suffisent pas à situer quelqu'un géographiquement.

**Pistes d'amélioration**
- ajouter d'autres variables (âge, taille de la ville, fréquence d'écoute)
- regrouper les régions en grandes zones (Nord / Sud / Est / Ouest / IDF) pour simplifier la cible
- rééquilibrer les classes (pondération, sous/sur-échantillonnage)

---

## 8. Lancer le projet

```bash
git clone https://github.com/felipemarzin-oss/data-science-project.git
cd data-science-project
pip install -r requirements.txt
```

Puis ouvrir les notebooks dans l'ordre : exploration → nettoyage → transformation → modélisation.