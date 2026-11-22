# HR Analytics Dashboard

**Pilotage des effectifs, de l’absentéisme et du recrutement**

Entrepôt de données RH sous SQL Server et tableau de bord Power BI pour **Contosso**, entreprise de services informatiques.


---
## Aperçu

| Élément | Détail |
|---|---|
| Base de données | `HRAnalyticsDW` (SQL Server) |
| Restitution | Power BI Desktop, 3 pages |
## Contenu du dépôt

```text
.
├── sql/
│   └── DB_HRproject.sql          # Création de la base, données fictives, index, requêtes
├── powerbi/
│   └── HR_Analytics.pbix         # Rapport Power BI (4 pages)
├── docs/
│   └── Guide_Projet_HR_Analytics.docx
└── README.md
```






**Connecter Power BI** : *Obtenir les données > SQL Server*, saisir le serveur et la base `HRAnalyticsDW`, mode Import, cocher les 10 tables.
**Configurer le modèle** : relations un-à-plusieurs, `DimDate` marquée comme table de dates.
Le détail pas à pas est dans le [guide du projet](docs/Guide_Projet_HR_Analytics.docx).

## Indicateurs clés

| KPI | Description |
|---|---|
| Effectif | Nombre total de collaborateurs dans l’entreprise. |
| Taux de rotation | Pourcentage de collaborateurs ayant quitté l’entreprise. |
| Taux d’absentéisme | Pourcentage d’absences des collaborateurs. |
| Délai de recrutement | Durée moyenne nécessaire pour recruter un candidat. |
| Coût par embauche | Coût moyen nécessaire pour recruter un nouveau collaborateur. |
| Taux de conversion | Pourcentage de candidats passant d’une étape à une autre du processus de recrutement. |

Les autres mesures sont décrites dans le guide du projet.


