# HR Analytics Dashboard

**Pilotage des effectifs, de l’absentéisme et du recrutement**

Entrepôt de données RH sous SQL Server et tableau de bord Power BI pour **Contosso**, entreprise de services informatiques.


---
## Aperçu

| Élément | Détail |
|---|---|
| Base de données | `HRAnalyticsDW` (SQL Server) |
| Restitution | Power BI Desktop, 4 pages |
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

| KPI | Définition |
|---|---|
| Effectif | Collaborateurs présents au dernier snapshot de la période |
| Taux de rotation | Départs ÷ effectif moyen |
| Taux d’absentéisme |
| Délai de recrutement |
| Coût par embauche | Coût total de recrutement ÷ recrutements réalisés |
| Taux de conversion | Recrutements réalisés ÷ candidatures |

Les autres mesures sont décrites dans le guide du projet.


