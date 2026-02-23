# 📈 Analyse Économétrique des Prix de l'Immobilier

![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-Econometrics-000000?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)

> **Projet de Statistiques et Économétrie - Université Paris 1 Panthéon-Sorbonne (2025-2026)**

---

## 🎯 Contexte & Objectif

Ce projet a pour but de comprendre les mécanismes de formation des prix immobiliers (en milliers d'euros) à travers une démarche économétrique complète, allant du nettoyage des données jusqu'à la prédiction via des modèles de Machine Learning.

L'analyse repose sur un échantillon final de **150 transactions** (obtenu après nettoyage des doublons et suppression des valeurs aberrantes via la méthode du Z-score > 3). Nous étudions l'impact des caractéristiques physiques (surface, nombre de chambres), de la localisation (distance au centre-ville) et de l'année de construction sur le prix de vente.

---

## ⚙️ Méthodologie & Modélisation

Le projet suit un pipeline analytique rigoureux, détaillé dans le fichier `projet.ipynb` et le rapport final :

### 1. Analyse Exploratoire (AED)
* Étude de la distribution des variables (Histogrammes, Boxplots).
* Analyse de la symétrie de la distribution des prix.
* Matrice de corrélation de Pearson pour détecter les premières relations linéaires.

### 2. Modélisation Économétrique (MCO)
* Estimation de modèles de Régression Linéaire Simple et Multiple (Méthode des Moindres Carrés Ordinaires).
* Utilisation d'erreurs standards robustes (HC1) pour fiabiliser l'inférence.

### 3. Diagnostics & Tests Statistiques
Pour garantir la validité de notre modèle, nous avons procédé aux tests suivants :
* **Multicolinéarité :** Calcul du VIF (Variance Inflation Factor).
* **Hétéroscédasticité :** Test de Breusch-Pagan.
* **Autocorrélation des résidus :** Test de Durbin-Watson.
* **Stabilité Structurelle :** Test de Chow pour identifier une éventuelle rupture structurelle liée à la crise du COVID-19 (comparaison pré/post 2020).

### 4. Modélisations Avancées
* **Endogénéité :** Utilisation de Variables Instrumentales (IV2SLS) pour corriger les biais potentiels.
* **Régularisation ML :** Implémentation de modèles Ridge (L2) et Lasso (L1) avec validation croisée (`RidgeCV`, `LassoCV`) pour améliorer la capacité de généralisation et sélectionner les variables pertinentes.

---

## 📊 Étude de Cas : Prédiction Immobilière

Application du modèle global (2015-2023) pour estimer la valeur d'un bien spécifique avec les caractéristiques suivantes :
* **Surface :** 120 m²
* **Chambres :** 3
* **Année de construction :** 2015
* **Distance au centre :** 5 km

**Résultats de la prédiction :**
* **Prix estimé :** 2 228.68 k€ *(soit environ 2,23 millions d'euros)*.
* **Intervalle de Confiance (95%) :** [2 186 k€ ; 2 271 k€] *(Incertitude sur la moyenne)*.
* **Intervalle de Prédiction (95%) :** [2 011 k€ ; 2 446 k€] *(Tient compte de la variabilité individuelle du bien)*.

---

## 💻 Stack Technique & Librairies

Le projet a été entièrement développé en **Python 3.10**.

* **Manipulation de données :** `pandas`, `numpy`
* **Visualisation :** `matplotlib.pyplot`, `seaborn`
* **Économétrie :** `statsmodels` (API formula & standard)
* **Tests statistiques :** `scipy.stats`
* **Machine Learning :** `scikit-learn` (`StandardScaler`, `Ridge`, `Lasso`, `train_test_split`)

---

## 📂 Structure du Répertoire

* `projet.ipynb` : Notebook Python contenant l'intégralité du code (nettoyage, régressions, tests, machine learning).
* `Rapport.pdf` : Rapport académique détaillé des résultats économétriques.
* `stats.pdf` : Support de présentation résumant les diagnostics et la prédiction.
