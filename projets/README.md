# Schéma des projets de transition écologique

Ce schéma permet de décrire les projets de transition écologique menés par les collectivités territoriales françaises.

## Modèle de données

Un projet de transition écologique est caractérisé par les informations suivantes :

| Nom du champ | Type | Description | Exemple |
|--------------|------|-------------|---------|
| id | uuid | Identifiant unique du projet | 01890e30-5a80-7c22-9842-8263d0d0d890 |
| createdAt | datetime | Date de création du projet | 2025-04-15T14:30:00.000Z |
| updatedAt | datetime | Date de dernière mise à jour | 2025-04-15T14:30:00.000Z |
| nom | string | Nom du projet | Rénovation énergétique des bâtiments publics |
| description | string | Description détaillée du projet | Projet de rénovation énergétique des écoles et bâtiments administratifs... |
| budgetPrevisionnel | integer | Budget prévisionnel en euros | 450000 |
| dateDebutPrevisionnelle | string | Date prévue de début du projet (YYYY-MM-DD) | 2025-03-01 |
| phase | string | Phase actuelle du projet | Idée, Étude, Opération |
| phaseStatut | string | Statut actuel de la phase | En cours, En retard, En pause, etc. |
| programme | string | Programme ou service d'origine | CRTE |
| porteurCodeSiret | string | Code SIRET du porteur | 21690123400019 |
| porteurReferentEmail | string | Email du référent | marie.dupont@ville-exemple.fr |
| porteurReferentTelephone | string | Téléphone du référent | 0472123456 |
| porteurReferentPrenom | string | Prénom du référent | Marie |
| porteurReferentNom | string | Nom du référent | Dupont |
| porteurReferentFonction | string | Fonction du référent | Directrice des services techniques |
| competences | array | Liste des compétences | ["90-21", "90-413"] |
| leviers | array | Liste des leviers de transition écologique | ["Rénovation (hors changement chaudières)", "Electricité renouvelable"] |
| mecId | string | Identifiant sur MEC | MEC-7652 |
| tetId | string | Identifiant sur TET | 12345 |
| recocoId | string | Identifiant sur Recoco | - |
| collectiviteIds | array | Identifiants des collectivités associées | ["01890e30-5a80-7c22-9842-8263d0d0d123"] |

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

Les champs `competences` et `leviers` contiennent des listes de valeurs standardisées qui permettent de catégoriser les projets selon :
- Les compétences des collectivités mises en œuvre
- Les leviers de transition écologique activés

### Référentiels

Les valeurs utilisées sont issues des référentiels suivants :
- **Compétences** : [Référentiel des compétences M57](https://github.com/betagouv/communs-de-la-transition-ecologique-des-collectivites/blob/main/api/src/shared/const/competences-list.ts) qui définit les codes et libellés des compétences des collectivités.
- **Leviers** : [Référentiel des leviers](https://github.com/betagouv/communs-de-la-transition-ecologique-des-collectivites/blob/main/api/src/shared/const/leviers.ts) qui liste les différents leviers d'action de transition écologique disponibles pour les projets.

La liste complète des valeurs possibles est disponible dans le fichier schema.json.

## Relations

Le champ `collectiviteIds` établit une relation many-to-many avec la table des collectivités. Un projet peut être associé à plusieurs collectivités (commune, EPCI).

## Exemple de données CSV

```csv
id,createdAt,updatedAt,nom,description,budgetPrevisionnel,dateDebutPrevisionnelle,phase,phaseStatut,programme,porteurCodeSiret,porteurReferentEmail,porteurReferentTelephone,porteurReferentPrenom,porteurReferentNom,porteurReferentFonction,competences,leviers,mecId,tetId,recocoId,collectiviteIds
01890e30-5a80-7c22-9842-8263d0d0d890,2025-04-15T14:30:00.000Z,2025-04-15T14:30:00.000Z,"Rénovation énergétique des bâtiments publics","Projet de rénovation énergétique des écoles et bâtiments administratifs pour réduire la consommation d'énergie et améliorer le confort thermique.",450000,2025-03-01,Étude,"En cours",CRTE,21690123400019,marie.dupont@ville-exemple.fr,0472123456,Marie,Dupont,"Directrice des services techniques","[""90-21"",""90-41""]","[""Rénovation (hors changement chaudières)"",""Electricité renouvelable""]",MEC-7652,12345,,"[""01890e30-5a80-7c22-9842-8263d0d0d123""]"
```

## Validation des données

Pour valider des données contre ce schéma, vous pouvez utiliser les outils de la suite Frictionless :

```bash
frictionless validate --schema=schema.json donnees.csv
```