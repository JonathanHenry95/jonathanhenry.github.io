# Jonathan Henry

Welcome to my Portfolio !

# Table of contents 

- [Objective](#objective)
- [Data Source](#data-source)
- [Étapes](#Étapes)
- [Design](#design)
  - [Mockup](#mockup)
  - [Tools](#tools)
- [development](#development)
  - [Pseudocode](#pseudocode)
  - [Data Exploration](#data-exploration)
  - [Data Cleaning](#data-cleaning)
  - [Transform the Data](#transform-the-data)
  - [Create the SQL View](#create-the-sql-view)
- [Testing](#testing)
  - [Data Quality Tests](#data-quality-tests)
- [Visualization](#visualization)
  - [Results](#results)
  - [DAX Measures](#dax-measures)
- [Analysis](#analysis)
  - [Findings](#findings)
  - [Validation](#validation)
  - [Discovery](#discovery)
- [Recommendations](#recommendations)
  - [Potential ROI](#potential-roi)
  - [Potential Courses of Actions](#potential-courses-of-actions)
- [Conclusion](#conclusion)



# Objective 

- Quelle est la problématique ?

Le responsable du marketing veut savoir qui sont les meilleurs YouTubers anglais en 2024 pour décider quels YouTubers seraient les mieux placés pour mener des campagnes de marketing pendant le reste de l'année.

- Quelle est la solution idéale ?

Créer un tableau de bord qui fournit des informations sur les meilleurs YouTubers britanniques en 2024, notamment sur leur
- nombre d'abonnés
- le nombre total de vues
- le nombre total de vidéos
- l'engagement rate

Cela aidera l'équipe marketing à prendre des décisions éclairées sur les YouTubers avec lesquels collaborer pour leurs campagnes marketing.

## User Story

En tant que responsable marketing, je souhaite utiliser un dashboard qui analyse les données des chaînes YouTube au Royaume-Uni.

Ce tableau de bord doit me permettre d'identifier les chaînes les plus performantes en fonction de paramètres tels que le nombre d'abonnés et le nombre moyen de vues.

Grâce à ces informations, je peux prendre des décisions plus éclairées sur les Youtubers avec lesquels il convient de collaborer, et donc maximiser l'efficacité de chaque campagne de marketing.

# Data source 

- Quelles sont les données nécessaires pour atteindre notre objectif ?

Nous avons besoin de données sur les principaux YouTubers britanniques en 2024, y compris leurs
- noms des chaînes
- le nombre total d'abonnés
- le nombre total de vues
- le nombre total de vidéos téléchargées


- D'où proviennent les données ? 
Les données proviennent de Kaggle (un extrait Excel), [voir ici pour le trouver] (https://www.kaggle.com/datasets/bhavyadhingra00020/top-100-social-media-influencers-2024-countrywise?resource=download).

# Étapes

- Conception
- Développement
- Test
- Analyse

# Design 

## Composants du dashboard

- Que doit contenir le tableau de bord sur la base des exigences fournies ?

Pour comprendre ce qu'il doit contenir, nous devons déterminer les questions auxquelles le tableau de bord doit répondre :

1. Qui sont les 10 premiers YouTubers ayant le plus d'abonnés ?
2. Quelles sont les 3 chaînes qui ont upload le plus de vidéos ?
3. Quelles sont les 3 chaînes qui ont le plus de vues ?
4. Quelles sont les 3 chaînes qui ont la moyenne de vues la plus élevée par vidéo ?
5. Quelles sont les 3 chaînes qui ont le plus grand nombre de vues par abonné ?
6. Quelles sont les 3 chaînes qui ont le taux d'engagement des abonnés le plus élevé par vidéo téléchargée ?

Pour l'instant, il s'agit de quelques-unes des questions auxquelles nous devons répondre, mais cela peut changer au fur et à mesure que nous avançons dans notre analyse.

## Dashboard mockup

- À quoi doit-il ressembler ?

Voici quelques-unes des données visuelles qui peuvent être utiles pour répondre à nos questions :

1. Tableau
2. Treemap
3. Tableau de bord
4. Diagramme à barres horizontal


![Maquette du tableau de bord](assets/images/dashboard_mockup.png)

## Tools 


| Tool | Purpose |
| --- | --- |
| Excel | Exploration des données |
| SQL Server | Nettoyage, test et analyse des données |
| Power BI | Visualisation des données via des dashboards interactifs |
| GitHub | Hébergement de la documentation du projet |
| Mokkup AI | Conception de la maquette du dashboard |


# Développement

## Pseudocode

- Quelle est l'approche générale pour créer cette solution ?

1. Obtenir les données
2. Explorer les données dans Excel
3. Charger les données dans le serveur SQL
4. Nettoyer les données avec SQL
5. Tester les données avec SQL
6. Visualiser les données dans Power BI
7. Générer des conclusions sur la base des informations recueillies
8. Rédiger la documentation et les commentaires
9. Publier les données sur GitHub

## Notes sur l'exploration des données

Il s'agit de l'étape au cours de laquelle vous examinez les données, les erreurs, les incohérences, les bogues, les caractères étranges et corrompus, etc.


- Quelles sont vos premières observations sur cet ensemble de données ? Qu'est-ce qui a attiré votre attention jusqu'à présent ?

1. Il y a au moins 4 colonnes qui contiennent les données dont nous avons besoin pour cette analyse, ce qui indique que nous avons tout ce dont nous avons besoin dans le fichier sans avoir à contacter le client pour obtenir d'autres données.
2. La première colonne contient l'ID du canal et ce qui semble être l'IDS du canal, séparés par un symbole @ - nous devons en extraire les noms des canaux.
3. Certaines cellules et certains noms d'en-tête sont rédigés dans une langue différente - nous devons confirmer si ces colonnes sont nécessaires et, si c'est le cas, nous devons les traiter.
4. Nous avons plus de données que nous n'en avons besoin, donc certaines de ces colonnes doivent être supprimées.









