## OBSCOP 2025 — Opinion sur le changement climatique

**Source :** https://www.data.gouv.fr/datasets/enquete-dopinion-internationale-sur-le-changement-climatique-obscop-2025

**Contexte :** 
==> Enquête EDF/Ipsos dans 30 pays sur les préoccupations, les perceptions et les comportements face au changement climatique.

***Question***  :
Peut-on prédire l’adoption d’un comportement écologique à partir du profil d’une personne et de ses opinions sur le climat ?

- volume : 146 275 lignes (agrégée) 

- valeur manquante
- harmoniser les réponses
- prendre en compte les pondérations et les différents pays


**Types d'erreurs :**
- Réponses manquantes (colonne : echantillon, base ...)
- Différences de représentativité entre pays (colonne population (catastrophique))

A noter :
Le fichier fait plus de 146 000 lignes, a voir si c'est trop ou pas.


==> Sujet intéressant et volume ok, 
mais pour entraîner un modèle individuel, il faut utiliser la base répondant par répondant (interroger ligne par ligne)


## Accidents de la route en France (2005–2024)

**Source :** https://www.data.gouv.fr/datasets/bases-de-donnees-annuelles-des-accidents-corporels-de-la-circulation-routiere
**CSV :** quatre fichiers par année : Caractéristiques, Lieux, Véhicules et Usagers.
**Contexte :** 

==> Comporte des informations sur l’accident, les lieux, les véhicules et les personnes impliquées, la météo etc 
Elle décrit aussi la gravité parmi les accidents enregistrés 

on peut se poser comme question :
Peut-on prédire la gravité des blessures d’un usager à partir de son profil, du véhicule et du contexte de l’accident ? (plus facile)
Peut-on prédire si un accident corporel entraîne au moins un décès ou une hospitalisation à partir de son contexte et des véhicules impliqués ?
(plus dur mais plus interessant)

- enorme volume (choisir des années pas prendre 10 ans, maybe 3-4) 
- valeur manquantes 
- des colonnes presque vides 
- infos incompletes
- clé non unique

**types d'erreurs (à voir) :**
Grosse jointure 

**maybe un peu dur // conséquant mais vraiment interessant**



## Taxis de New York 
on connait ce dataset vu qu'on le fait en Hadoop 

***Question*** : prévoir le nombre de prises en charge par quartier et par heure
- beaucoup plus de ligne
- valeur manquantes 

***source***: https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

==> Comporte : les dates et heures de départ et d’arrivée, les zones, les distances, le nombre de passagers, les montants et les moyens de paiement etc
par mois (Parquet) 

Volume : 41 millions de courses en 2024
l'idéal : commencer avec 2-3 mois puis après essayer 6-7 mois etc 

beaucoup de jointure, feature etc 
très très gros volume 


## Logements F/G en France — DPE

**Source :** https://data.ademe.fr/datasets/dpe03existant
**Fichiers :** une table principale, accessible par API ou export. On peut extraire plusieurs départements séparément, puis assembler les fichiers

==> Comporte des informations sur les logements : surface, maison/appartement, période de construction, chauffage, énergie utilisée, isolation, fenêtres, localisation, etc

Chaque diagno donne une classe énergétique de A à G, l objectif est d’identifier les logements classés F ou G ==> les plus énergivores.

**Question :**
Peut-on prédire si un logement est classé F ou G à partir de ses caractéristiques et de son système de chauffage ?

- Volume : 15,8 millions
- Plusieurs diagnostics peuvent concerner le même logement.
- valeur manquante
- assembler les exports
- colonne pas trop renseignées
- valeur incohérente 

**Attention :** retirer des variables explicatives les consommations, émissions et autres résultats qui donnent directement la classe énergétique
=>le modèle a déjà accès à la réponse

Pas top si on doit enlever la réponse 
