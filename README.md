# People Analytics : tableau de bord RH de bout en bout (SQL Server → Power BI)

## Objectif

Partir d'un entrepôt de données RH (`HRAnalyticsDW`), l'auditer sans le modifier, fiabiliser le modèle sémantique, puis produire un rapport de pilotage pour une direction RH. Questions auxquelles le rapport répond :

- Combien de salariés, comment évolue l'effectif, quel est le turnover ?
- Où et quand l'absentéisme est-il le plus élevé, et quel effort de formation est consenti ?
- Quelles sources de recrutement convertissent le mieux, et à quel coût ?

## Aperçu du rapport

Rapport de 4 pages, thème personnalisé (`theme/HR_Analytics_Theme.json`) et filtres synchronisés (Année, Département, Genre, Niveau de poste, Type de contrat, selon la pertinence de chaque page).

## Stack technique

| Couche | Outils |
|---|---|
| Stockage | SQL Server, base `HRAnalyticsDW`, schéma `dbo` |
| Modélisation | Power BI Desktop, modèle en étoile autour de l'employé |
| Calcul | DAX : 33 mesures et une bibliothèque avancée |
| Restitution | Rapport Power BI de 4 pages |

## Modèle de données

10 tables : 6 dimensions (`DimDate`, `DimEmployee`, `DimDepartment`, `DimJob`, `DimRecruitmentSource`, `DimAbsenceType`) et 4 faits (`FactEmployeeSnapshot`, `FactAbsence`, `FactRecruitment`, `FactTraining`).

Corrections apportées après l'audit (détail dans [`docs/model.md`](docs/model.md)) :

- suppression de 4 relations redondantes qui créaient des chemins de filtre ambigus ;
- 3 relations de date un-à-un bidirectionnelles remplacées par du plusieurs-à-un en sens unique ;
- activation des relations vers `DimEmployee` et `DimDepartment` ;
- `DimDate` marquée comme table de dates, tri chronologique des mois ;
- date d'ouverture des postes : relation inactive activée par `USERELATIONSHIP`.

## Indicateurs clés

Les 33 mesures sont dans [`dax/measures.dax`](dax/measures.dax), regroupées en 5 dossiers.

| Thème | Exemples |
|---|---|
| Effectifs | Effectif (snapshot de fin de période), effectif moyen, variation vs N-1, départs, taux de turnover, masse salariale, ancienneté moyenne |
| Absences | Jours d'absence, taux d'absentéisme, % maladie, durée moyenne |
| Recrutement | Candidatures, taux de conversion, délai moyen, coût par recrutement |
| Formation | Heures, coût, salariés formés, taux de participation, % en ligne |
| Qualité | Part des absences datées un week-end |

Choix de méthode à connaître : l'absentéisme se calcule sur « effectif moyen × jours ouvrés du calendrier » car la colonne `WorkingDays` est constante ; les mesures de recrutement utilisent la date d'ouverture du poste pour rester comparables entre elles.



## Structure du dépôt

```
sql/          Contrôles qualité, vues, requêtes analytiques avancées
dax/          Mesures du modèle et bibliothèque DAX
docs/         Documentation du modèle
screenshots/  Captures du rapport
theme/        Thème Power BI (JSON)

```










