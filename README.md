# Data Portfolio : Excel vers Power BI

![Diagramme animé Excel vers Power BI](assets/images/kaggle_to_powerbi.gif)

Ce projet présente la construction d’un tableau de bord Power BI à partir de données Excel sur les principaux créateurs YouTube du Royaume-Uni en 2024, afin d’orienter une stratégie marketing efficace.

---

## Sommaire

- [Objectif](#objectif)
- [Source des données](#source-des-données)
- [Étapes du projet](#étapes-du-projet)
- [Conception](#conception)
  - [Maquette](#maquette)
  - [Outils utilisés](#outils-utilisés)
- [Développement](#développement)
  - [Pseudocode](#pseudocode)
  - [Exploration des données](#exploration-des-données)
  - [Nettoyage des données](#nettoyage-des-données)
  - [Transformation](#transformation)
  - [Création de la vue SQL](#création-de-la-vue-sql)
- [Tests](#tests)
- [Visualisation](#visualisation)
  - [Résultats du dashboard](#résultats-du-dashboard)
  - [Mesures DAX](#mesures-dax)
- [Analyse](#analyse)
- [Recommandations](#recommandations)
- [Conclusion](#conclusion)

---

## Objectif

Le but est d’aider une équipe marketing à choisir les meilleurs créateurs YouTube UK avec lesquels collaborer en 2024, grâce à un tableau de bord interactif regroupant :
- le nombre d’abonnés
- le nombre total de vues
- le nombre de vidéos publiées
- des métriques d’engagement

### Cas utilisateur

En tant que responsable marketing, ce dashboard me permet d’identifier rapidement les chaînes les plus performantes pour maximiser la visibilité et l’impact des campagnes.

---

## Source des données

- Jeu de données issu d’un fichier Excel disponible sur Kaggle (Top 100 Influenceurs UK 2024).
- Les colonnes utilisées : channel_name, total_subscribers, total_views, total_videos.

---

## Étapes du projet

- Conception du tableau de bord
- Préparation et nettoyage de la donnée
- Contrôles qualité et validation
- Visualisation sous Power BI
- Analyse et recommandations

---

## Conception

### Questions posées par le dashboard

- Qui sont les 10 chaînes avec le plus d’abonnés ?
- Quelles chaînes ont publié le plus grand nombre de vidéos ?
- Quelles sont les chaînes avec le plus de vues accumulées ?
- Quels sont les meilleurs ratios vus/vidéo, vus/abonné et taux d’engagement ?

### Maquette

- Tableaux de classement
- Treemap
- Indicateurs clé
- Graphique à barres horizontal

![Maquette du dashboard](assets/images/dashboard_mockup.png)

### Outils utilisés

| Outil      | Utilisation principale                |
|------------|--------------------------------------|
| Excel      | Exploration et prétraitement         |
| SQL Server | Nettoyage, tests, préparation        |
| Power BI   | Visualisation et analyse             |
| GitHub     | Suivi version et documentation       |
| Mokkup AI  | Création rapide de maquette          |

---

## Développement

### Pseudocode

1. Importer les données sources
2. Explorer rapidement sous Excel
3. Charger dans SQL Server et nettoyer
4. Vérifier la qualité des données (lignes, colonnes, doublons…)
5. Créer la vue pour l’analyse
6. Réaliser les visualisations dans Power BI
7. Documenter et publier sur GitHub

### Exploration des données

- Vérification : colonnes disponibles, présence d’erreurs ou d’incohérences, doublons, noms de colonnes à harmoniser.
- Extraction du nom réel de la chaîne à partir de l’identifiant présent avec «@».

### Nettoyage des données

Le jeu de données propre doit respecter :
- Garder uniquement channel_name, total_subscribers, total_views, total_videos
- Types adaptés (texte, entier)
- Aucune valeur manquante

Schéma attendu :

| Colonne            | Type      | Obligatoire |
|--------------------|-----------|-------------|
| channel_name       | texte     | oui         |
| total_subscribers  | entier    | oui         |
| total_views        | entier    | oui         |
| total_videos       | entier    | oui         |

**Exemple SQL pour transformer :**
```
SELECT
    SUBSTRING(NOMBRE, 1, CHARINDEX('@', NOMBRE) -1) AS channel_name,
    total_subscribers,
    total_views,
    total_videos
FROM
    top_uk_youtubers_2024
```

**Création de la vue :**
```
CREATE VIEW view_uk_youtubers_2024 AS
SELECT
    CAST(SUBSTRING(NOMBRE, 1, CHARINDEX('@', NOMBRE) -1) AS VARCHAR(100)) AS channel_name,
    total_subscribers,
    total_views,
    total_videos
FROM
    top_uk_youtubers_2024
```

---

## Tests

Contrôles mis en place :
- Correspondance du nombre de lignes attendu
- Présence/absence de colonnes superflues
- Adaptation des types
- Absence de doublons

---

## Visualisation

### Résultats du dashboard

![Aperçu dashboard Power BI](assets/images/top_uk_youtubers_2024.gif)

Classement des chaînes YouTube selon l’indicateur choisi avec filtres et graphiques dynamiques.

### Exemples de mesures DAX

```
-- Abonnés (en millions)
Total Subscribers (M) = DIVIDE(SUM(view_uk_youtubers_2024[total_subscribers]), 1000000)

-- Vues (en milliards)
Total Views (B) = ROUND(SUM(view_uk_youtubers_2024[total_views]) / 1000000000, 2)

-- Moyenne de vues par vidéo (en millions)
Average Views per Video (M) =
VAR sumViews = SUM(view_uk_youtubers_2024[total_views])
VAR sumVideos = SUM(view_uk_youtubers_2024[total_videos])
RETURN DIVIDE(sumViews, sumVideos, BLANK()) / 1000000
```

---

## Analyse

- Classement des chaînes par : abonnés, nombre de vidéos, total de vues, moyennes, ratios.
- Calculs simples pour estimer la rentabilité potentielle en fonction de différents scénarios de campagnes (exemple : diffusion de produit, contrat d’influence, mini-série sponsorisée).

---

## Recommandations

- Priorité à une collaboration avec **Dan Rhodes** pour la visibilité maximale.
- Les chaînes ultra-productives (comme GRM Daily, Manchester City, Yogscast) sont à retenir si le budget le permet, mais leur taux de rentabilité est parfois inférieur.
- Penser aussi à **NoCopyrightSounds** et **DanTDM** pour leur potentiel d’engagement et leur forte communauté.
- Suivre et évaluer en continu la rentabilité réelle selon les performances.

### Exemples de ROI calculés

- **Dan Rhodes** : +1 065 000 $ / vidéo en bénéfice potentiel
- **Mister Max** : +1 276 000 $ / campagne influenceur
- **NoCopyrightSounds** : +642 000 $ / vidéo

### Plan d’action

1. Contacter en premier Dan Rhodes
2. Adapter la négociation au budget et aux KPIs de chaque action
3. Lancer les campagnes et suivre les résultats
4. Affiner la stratégie en s’appuyant sur la donnée et le feedback

---

## Conclusion

Ce projet montre comment exploiter simplement des données publiques pour sélectionner objectivement les meilleurs influenceurs vidéo d’un marché, et maximiser l’efficacité des campagnes marketing grâce à la donnée et à la visualisation.
