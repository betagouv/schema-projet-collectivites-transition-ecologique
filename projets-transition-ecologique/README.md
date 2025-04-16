# Schéma des projets de transition écologique

Ce schéma permet de décrire les projets de transition écologique menés par les collectivités territoriales françaises.

## Phases et statuts

Les projets peuvent être dans une des phases suivantes :
- **Idée** : Le projet est au stade d'idéation ou de concept
- **Étude** : Le projet est en phase d'étude (faisabilité, conception, etc.)
- **Opération** : Le projet est en phase de réalisation concrète

Les statuts possibles pour chaque phase sont :
- **En cours** : La phase progresse normalement
- **En retard** : La phase prend du retard sur le planning initial
- **En pause** : La phase est temporairement mise en pause
- **Bloqué** : La phase est bloquée par un obstacle
- **Abandonné** : Le projet a été abandonné
- **Terminé** : La phase est terminée

## Compétences et leviers

Les champs `competences` et `leviers` permettent de catégoriser les projets selon :
- Les compétences des collectivités mises en œuvre
- Les leviers de transition écologique activés

### Référentiels

Les valeurs utilisées sont issues des référentiels suivants :
- **Compétences** : Référentiel des compétences M57 (`reference-data/competences-collectivites.json`)
- **Leviers** : Référentiel des leviers de transition écologique (`reference-data/50_leviers_SGPE_03_2025.csv`)

La liste complète des valeurs possibles est disponible dans ces fichiers de référence.

## Relations

Le champ `collectiviteIds` établit une relation many-to-many avec la table des collectivités. Un projet peut être associé à plusieurs collectivités (commune, EPCI).

## Validation des données

Pour valider des données contre ce schéma, vous pouvez utiliser les outils de la suite Frictionless :

```bash
frictionless validate --schema=schema.json donnees.csv
```