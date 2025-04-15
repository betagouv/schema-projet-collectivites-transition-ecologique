# Schéma des projets de transition écologique des collectivités

Ce dépôt contient les schémas de données standardisés pour décrire les projets de transition écologique menés par les collectivités territoriales françaises.

## Vue d'ensemble

Ce schéma permet de structurer les données relatives aux projets de collectivités en lien avec la transition écologique. Il facilite le partage, l'analyse et la valorisation de ces données entre différents services numériques de l'État français et les collectivités territoriales.

## Structure du schéma

Le schéma est organisé en deux tables principales :

1. **Projets** : Décrit les projets de transition écologique avec leurs caractéristiques (identifiant, nom, description, budget, planning, phase, etc.)
2. **Collectivités** : Décrit les collectivités territoriales (communes, EPCI) qui portent ces projets

Ces tables sont liées par une relation many-to-many, ce qui permet à un projet d'être associé à plusieurs collectivités et vice-versa.

## Utilisation

Ces schémas sont conçus pour être utilisés par différents services numériques qui accompagnent les collectivités dans leurs projets de transition écologique, comme :

- Mon Espace Collectivité (MEC)
- Territoires Engagés pour la Transition Écologique (TET)
- Recoco

## Format

Les schémas sont au format [Table Schema](https://specs.frictionlessdata.io/table-schema/) et [Data Package](https://specs.frictionlessdata.io/data-package/), conforme aux spécifications Frictionless Data, pour faciliter la validation et l'interopérabilité des données.

## Contenu du dépôt

- `datapackage.json` : Le descripteur principal du package de données
- `projets/` : Contient le schéma et les exemples pour la table des projets
- `collectivites/` : Contient le schéma et les exemples pour la table des collectivités

## Licence

Les schémas et la documentation sont sous [Licence Ouverte Etalab 2.0](https://www.etalab.gouv.fr/licence-ouverte-open-licence/).