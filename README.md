# Prédisez la demande en électricité

## Table des matières
- [Description du projet](#description-du-projet)
- [Structure du projet](#structure-du-projet)
- [Jeu de données](#jeu-de-données)
- [Outils et bibliothèques](#outils-et-bibliothèques)
- [Nettoyage et préparation des données](#nettoyage-et-préparation-des-données)
- [Méthodologie d’analyse](#méthodologie-danalyse)
  - [Correction de l’effet température](#correction-de-leffet-température)
  - [Désaisonnalisation](#désaisonnalisation)
  - [Modélisation & Prédiction](#modélisation--prédiction)
- [Résultats clés](#résultats-clés)
- [Recommandations](#recommandations)

## Description du projet

Ce projet a été réalisé dans le cadre du parcours **Data Analyst** chez OpenClassrooms.  
Il vise à **modéliser et prédire la demande mensuelle d’électricité** pour Enercoop, une entreprise française spécialisée dans les énergies renouvelables.

L’objectif est de permettre à l’entreprise de **mieux anticiper les pics de consommation**, en tenant compte des **facteurs météorologiques** et de la **saisonnalité naturelle** de la demande.


## Structure du projet

**data/**  
- `data_projet9.csv`: Contient les données journalières de consommation électrique.
- les autres fichiers de type xlsx représentent les données météo (températures) utilisées pour le calcul du DJU (Degré Jour Unifié) de plusieurs régions.

**notebooks/**  
- `notebook.ipynb` : Prétraitement des données, correction de l’effet température, désaisonnalisation et modélisation (Holt-Winters, SARIMA).

**visualizations/**  
- Graphiques de correction par régression, décomposition de la série, prévisions, évaluation des modèles (MAPE, RMSE).

**présentation/**  
- `presentation.pptx` : Fichier PowerPoint utilisé lors de la soutenance pour présenter les objectifs, la méthodologie et les résultats.


## Jeu de données

- Données de **consommation journalière d’électricité**, agrégées au format **mensuel**
- Données **météo journalières**, utilisées pour corriger la consommation via le **Degré Jour Unifié (DJU)**


## Outils et bibliothèques

- Python  
- Pandas / Numpy  
- Statsmodels  
- Matplotlib / Seaborn  
- Jupyter Notebook  

## Nettoyage et préparation des données

- Agrégation des données journalières en mensuel
- Calcul du DJU (Degré Jour Unifié) à partir des températures
- Fusion des bases de consommation et météo
- Vérification des valeurs manquantes et normalisation


## Méthodologie d’analyse

### Correction de l’effet température
- Régression linéaire entre la consommation mensuelle et le DJU
- R² = 93.1 %, résidus normalement distribués

### Désaisonnalisation
- Décomposition additive de la série pour isoler la tendance et la saisonnalité

### Modélisation & Prédiction
- Modèle Holt-Winters (lissage exponentiel avec tendance et saisonnalité)
- Modèle SARIMA(0,1,0)(1,0,1)[12] validé statistiquement (stationnarité, bruit blanc, normalité)


## Résultats clés

- Les deux modèles prédisent correctement la tendance saisonnière
- Le modèle SARIMA présente de **meilleures performances** (MAPE et RMSE plus faibles)
- Les prévisions montrent des pics de consommation en **janvier et juillet**
- Modèles validés par les tests statistiques (normalité des résidus, bruit blanc)


## Recommandations

- Utiliser le modèle **SARIMA** pour anticiper les pics de consommation
- Adapter la production électrique en hiver et en été selon les prévisions
- Intégrer ces prévisions dans un outil d’aide à la décision pour les équipes opérationnelles


