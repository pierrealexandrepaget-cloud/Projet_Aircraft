# projet_aircraft
Projet de formation en data analytics visant à construire une pipeline complète sur des données aéronautiques. Il combine Snowflake, dbt et une EDA sous Deepnote pour créer un workflow robuste et reproductible, permettant d’analyser l’activité des avions, compagnies aériennes et aéroports.


________________________________________
📁 Table of Contents
•	Contexte

•	Objectifs du projet

•	Stack technique

•	Architecture du projet

•	Modèles dbt

•	Questions métier traitées

•	Analyse exploratoire (EDA)

•	Compétences mises en avant

•	Installation & exécution

•	Données

•	Auteurs


________________________________________


🧠 Contexte

Le secteur aérien génère de nombreuses données : vols, passagers, aéroports, capacités, kilométrage…


L'objectif est de construire un workflow analytique reproductible, permettant de répondre à plusieurs questions business clés, comme :

•	Quels avions volent le plus ?

•	Quels aéroports transportent le plus de passagers ?

•	Quelles compagnies performent le mieux en termes de RPM ou de croissance ?


Ce projet démontre une approche complète de l’ingestion à la modélisation, jusqu’à l’analyse visuelle des résultats.
________________________________________
🎯 Objectifs du projet
1. Charger les données dans Snowflake
•	Création d'un environnement (database, schema, warehouse)
•	Import des tables brutes depuis aircraft_db.sql
•	Vérification et exploration initiale
2. Construire un modèle analytique avec dbt
•	Définition des sources
•	Création des niveaux de transformations :
o	staging
o	dimensions
o	facts
o	marts analytiques
•	Enrichissement des modèles pour répondre aux questions business
3. Réaliser une EDA sous Deepnote
•	Connexion à Snowflake
•	Requêtes SQL et visualisations
•	Validation et illustration des insights produits par dbt
________________________________________
🧰 Stack technique
Domaine	Outils
Data Warehouse	Snowflake
Modélisation SQL	dbt Core
Analyse exploratoire	Deepnote
Langages	SQL, Jinja (dbt)
Documentation	dbt docs, Markdown
________________________________________
🏗️ Architecture du projet
├── models/
│   ├── staging/
│   ├── dims/
│   │   ├── dim_aircraft.sql
│   │   ├── dim_airline.sql
│   │   └── dim_airport.sql
│   ├── facts/
│   └── marts/
├── analyses/
├── snapshots/
├── seeds/
├── dbt_project.yml
└── README.md
(Adaptable selon ton project tree réel)
________________________________________
🧱 Modèles dbt
Voici un résumé des modèles principaux :
Type de modèle	Nom	Rôle
Staging	stg_aircraft, stg_airlines, stg_airports, stg_flight_summary_data, stg_individual_flights	Nettoyage, normalisation, colonnes uniformisées
Dimensions	dim_aircraft, dim_airline, dim_airport	Tables de référence enrichies
Facts	fact_flights, fact_passenger_flow, etc.	Calculs agrégés sur les vols et passagers
Marts	aircraft_analytics_overview	Résumé pour analystes BI
Je peux aussi générer un schema.yml propre si tu veux.
________________________________________
💼 Questions métier traitées
1. ✈️ Quel aircraft a le plus volé ?
•	Comptage des vols dans individual_flights
•	Jointure avec la table des appareils
•	Ajout aux modèles dbt pour exploitation BI
2. 🛫 Quel aéroport transporte le plus de passagers ?
•	Calcul : nombre de vols × capacité avion
•	Attribution à chaque aéroport (départ + arrivée)
3. 📈 Quel est la meilleure année en RPM pour chaque compagnie ?
•	Agrégation des RPM Domestic / International
•	Remplacement des valeurs nulles par 0
•	Extraction du meilleur millésime
4. 📊 Quelle compagnie a eu la meilleure croissance ?
•	Utilisation de l’ASM comme indicateur principal
•	Calcul du AVG(ASM_Domestic) par année
•	Identification de la meilleure année de croissance
________________________________________
📊 Analyse exploratoire (EDA)
Réalisation via Deepnote :
•	Chargement des données Snowflake
•	Requêtes SQL exploratoires
•	Création de visualisations :
o	histogrammes
o	bar charts
o	courbes de tendance par année
•	Validation des KPIs définis dans dbt
•	Comparaison des résultats via différents angles business
________________________________________
🧩 Compétences mises en avant
•	Data engineering
o	ingestion Snowflake, pipelines SQL, optimisation
•	dbt
o	sources, staging, dimensions, facts, tests, documentation
•	Modélisation analytique
o	KPI aéronautiques (RPM, ASM, capacities, passengers)
•	SQL avancé
o	CTE, jointures complexes, agrégations, normalisation
•	Exploratory Data Analysis
o	visualisations, statistiques descriptives
•	Data storytelling
o	capacité à rendre une base brute exploitable pour les équipes business
________________________________________
⚙️ Installation & exécution
1. Cloner le repo
git clone https://github.com/ton-user/aircraft-analytics.git
cd aircraft-analytics
2. Configurer dbt
dbt debug
dbt deps
3. Lancer les modèles
dbt run
dbt test
dbt docs generate
4. Visualiser la documentation dbt
dbt docs serve
________________________________________
📦 Données
Les données proviennent du fichier SQL fourni :
src/aircraft_db.sql
Elles contiennent :
•	avion ✔️
•	compagnie ✔️
•	aéroport ✔️
•	vols individuels ✔️
•	métriques aéronautiques (RPM, ASM, etc.) ✔️
________________________________________
👤 Auteurs
PAGET Pierre-Alexandre
Data Analyst — Formation Jedha
📫 Contact : pierre.alexandre.paget@gmail.com
