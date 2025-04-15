# Schéma des collectivités

Ce schéma permet de décrire les collectivités territoriales qui sont associées aux projets de transition écologique.

## Modèle de données

Une collectivité est caractérisée par les informations suivantes :

| Nom du champ | Type | Description | Exemple |
|--------------|------|-------------|---------|
| id | uuid | Identifiant unique de la collectivité | 01890e30-5a80-7c22-9842-8263d0d0d123 |
| nom | string | Nom de la collectivité | Ville de Lyon |
| type | string | Type de collectivité (Commune ou EPCI) | Commune |
| codeInsee | string | Code INSEE de la commune | 69123 |
| codeDepartements | array | Codes des départements | ["69"] |
| codeRegions | array | Codes des régions | ["84"] |
| codeEpci | string | Code de l'EPCI | 200046977 |
| siren | string | Code SIREN de la collectivité | 216901234 |
| createdAt | datetime | Date de création de l'entrée | 2025-04-15T14:30:00.000Z |
| updatedAt | datetime | Date de dernière mise à jour | 2025-04-15T09:45:12.000Z |

## Types de collectivités

Le schéma prend en charge deux types de collectivités :
- **Commune** : Une commune française
- **EPCI** : Un Établissement Public de Coopération Intercommunale (métropole, communauté d'agglomération, etc.)

## Codes géographiques et administratifs

Plusieurs codes permettent d'identifier et de situer géographiquement les collectivités :

- **codeInsee** : Pour les communes, le code INSEE à 5 chiffres unique à chaque commune
- **codeEpci** : Pour les EPCI, le code SIREN à 9 chiffres unique à chaque EPCI
- **codeDepartements** : Les codes des départements sur lesquels la collectivité se situe
- **codeRegions** : Les codes des régions sur lesquelles la collectivité se situe

### Référentiels des codes

Les codes utilisés sont issus des référentiels officiels suivants :
- **INSEE** : [Référentiel des codes officiels géographiques](https://www.insee.fr/fr/information/2560452) pour les codes INSEE des communes
- **SIREN** : [Base SIRENE des entreprises](https://www.data.gouv.fr/fr/datasets/base-sirene-des-entreprises-et-de-leurs-etablissements-siren-siret/) pour les identifiants SIREN
- **EPCI** : [Référentiel des intercommunalités](https://www.collectivites-locales.gouv.fr/institutions/intercommunalite-et-metropoles) pour les codes EPCI

## Particularités selon le type de collectivité

Selon le type de collectivité, certains champs peuvent être vides ou non :

- Pour une **Commune** :
  - `codeInsee` est obligatoirement renseigné
  - `codeEpci` peut être renseigné pour indiquer l'EPCI de rattachement

- Pour un **EPCI** :
  - `codeEpci` est obligatoirement renseigné
  - `codeInsee` n'est pas renseigné

## Relations

Les collectivités sont liées aux projets dans une relation many-to-many. Un projet peut être associé à plusieurs collectivités, et une collectivité peut être impliquée dans plusieurs projets.

## Exemple de données CSV

```csv
id,nom,type,codeInsee,codeDepartements,codeRegions,codeEpci,siren,createdAt,updatedAt
01890e30-5a80-7c22-9842-8263d0d0d123,"Ville de Lyon",Commune,69123,"[""69""]","[""84""]",200046977,216901234,2025-04-15T14:30:00.000Z,2025-04-15T09:45:12.000Z
01890e30-5a80-7c22-9842-8263d0d0d124,"Métropole de Lyon",EPCI,,"[""69""]","[""84""]",200046977,210002600,2025-04-15T14:30:00.000Z,2025-04-15T09:45:12.000Z
```

## Validation des données

Pour valider des données contre ce schéma, vous pouvez utiliser les outils de la suite Frictionless :

```bash
frictionless validate --schema=schema.json donnees.csv
```