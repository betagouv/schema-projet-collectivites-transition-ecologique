# Changelog

## 0.1.1 (2025-04-16)
### Améliorations
- Ajout des référentiels comme ressources dans le data package
  - Référentiel des compétences des collectivités M57 (JSON)
  - Référentiel des leviers SGPE de la transition écologique (CSV)
- Mise à jour des schémas pour utiliser les référentiels
  - Suppression des enums hardcodés
  - Ajout des foreign keys appropriées
- Enrichissement des exemples de données
  - Ajout de cas d'utilisation variés pour les projets (tous les statuts)
  - Utilisation des sous-compétences M57
  - Ajout d'exemples pour tous les types de collectivités
  - Plus de combinaisons de leviers

### Corrections
- Suppression des références externes vers GitHub
- Migration des référentiels vers des fichiers locaux
- Documentation mise à jour pour refléter la nouvelle structure

## 0.1.0 (2025-04-15)
- Initial version with schema for projects and collectivities
- Structure using dedicated folders for each entity (projets and collectivites)
- Example CSV files for both entities