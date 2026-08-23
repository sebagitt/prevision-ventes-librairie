# Analyse des ventes et segmentation client

Étude statistique et analyse de séries temporelles pour optimiser le catalogue produit et définir une stratégie marketing ciblée.

**Stack :** `Python 3.x`, `Pandas`, `SciPy`, `Statsmodels`, `Plotly`

## Vue d'ensemble
Lapage, librairie physique ayant ouvert une boutique en ligne, cherche à mieux comprendre ses dynamiques de vente. 
L'objectif est d'analyser plus de 640 000 transactions sur 36 mois pour identifier les anomalies de vente, évaluer la rentabilité du catalogue et segmenter la clientèle.

## Architecture et modèle de données
Le projet repose sur la réconciliation et le nettoyage de 3 tables relationnelles :
* **Transactions :** identifiants de session, dates, identifiants produits et clients.
* **Products :** prix et catégories (0, 1, 2).
* **Customers :** genre et année de naissance (âge calculé).

Un nettoyage approfondi a été mené : traitement des doublons, imputation des prix manquants par la moyenne de leur catégorie, et exclusion des transactions tests.

## Résultats et livrables
* **Analyse temporelle :** Identification d'un arrêt technique en octobre 2021 et contextualisation de la baisse de février 2023 (baisse de volume liée aux 28 jours, mais rythme quotidien stable à -2,7 %).
* **Audit du catalogue :** Mise en évidence du sur-stockage en catégorie 0 (volume d'invendus élevé) face à la forte rentabilité de la catégorie 2.
* **Détection B2B :** Isolation de 4 clients professionnels représentant 7,35 % du CA global pour éviter de biaiser les analyses grand public.
* **Validation statistique (B2C) :**
  * Pas de segment marketing pertinent sur le genre (Chi-2 significatif sur grand échantillon mais écarts réels négligeables).
  * Impact déterminant de l'âge sur le choix des catégories (ANOVA / Kruskal-Wallis, $\eta^2 = 0,11$).

## Contenu du dépôt
* `01_preparation_analyse_lapage.ipynb` : notebook complet (nettoyage, exploration, tests statistiques).
* `02_presentation_recommandations_Lapage.pdf` : support de présentation synthétique pour le CODIR.
* `pyproject.toml` : spécification de l'environnement (uv).

## Axes d'amélioration
- Automatisation du pipeline de nettoyage via des scripts modulaires (.py).
- Mise en place d'un modèle prédictif de séries temporelles pour anticiper les besoins en réapprovisionnement.
- Déploiement d'un tableau de bord de suivi (Power BI ou Streamlit).
