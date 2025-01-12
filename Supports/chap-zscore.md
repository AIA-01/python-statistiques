# **Introduction au Z-Score**

Le **z-score** (ou score standard) est une mesure statistique qui quantifie combien d'écarts-types une donnée est éloignée de la moyenne d'un ensemble de données. 

>[!NOTE]
> En standardisant les données, il facilite leur comparaison, même si elles proviennent de distributions ou d'échelles différentes.

### Remarques

Le z-score est particulièrement utile lorsque les données suivent une distribution normale (ou quasi-normale). Cela permet de comparer les valeurs d'un jeu de données par rapport à la moyenne de manière significative.

Cependant, même si les données ne sont pas parfaitement normales, le z-score peut être utilisé comme une mesure relative pour évaluer l'éloignement d'une valeur par rapport à la moyenne.

#### **Formule du Z-Score**

La formule pour calculer le z-score est :

$z = \frac{X - \mu}{\sigma}$

Où :
- $X$ : la valeur de la donnée,
- $\mu$ : la moyenne de l'ensemble de données,
- $\sigma$ : l'écart-type de l'ensemble de données.

#### **Interprétation** :
- **z = 0** : La donnée est égale à la moyenne.
- **z > 0** : La donnée est supérieure à la moyenne.
- **z < 0** : La donnée est inférieure à la moyenne.
- Un z-score éloigné de 0 (positif ou négatif) indique que la donnée est loin de la moyenne.

---

### **Concepts Préalables : Moyenne et Écart-Type**

Avant de calculer un z-score, il est crucial de comprendre deux concepts fondamentaux :

#### 1. **Moyenne ($\mu$)**  
La moyenne représente la valeur centrale des données. Elle est calculée comme suit :

$\mu = \frac{1}{n} \sum_{i=1}^{n} X_i$

#### 2. **Écart-Type ($\sigma$)**  
L'écart-type mesure la dispersion des données autour de la moyenne. Plus $\sigma$ est grand, plus les données sont dispersées. La formule est :

$\sigma = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (X_i - \mu)^2}$

---

### **Exemple Pratique : Calcul du Z-Score avec NumPy**

Nous allons illustrer le calcul du z-score avec la bibliothèque **NumPy**.

#### **Étapes** :
1. Calculer la moyenne des données ($\mu$).
2. Calculer l'écart-type ($\sigma$).
3. Utiliser la formule du z-score pour chaque donnée.

#### **Code Python**

```python
import numpy as np

# Exemple de données
data = np.array([10, 12, 9, 14, 13, 11, 15, 8, 7, 12])

# Calcul de la moyenne et de l'écart-type
mean = np.mean(data)
std_dev = np.std(data)

# Calcul des z-scores
z_scores = (data - mean) / std_dev

# Affichage des résultats
print(f"Les données : {data}")
print(f"Moyenne : {mean}")
print(f"Écart-type : {std_dev}")
print(f"Z-scores : {z_scores}")
```

---

### **Applications Pratiques du Z-Score**

#### 1. **Détection des Outliers**  
Les données avec un z-score supérieur à 3 ou inférieur à -3 sont souvent considérées comme des **valeurs aberrantes**.

#### Exemple :

```python
data = np.array([5, 15, 22, 28, 50, 75, 60, 52, 40, 90, 100, 150, 900])

mean = np.mean(data)
std_dev = np.std(data)

z_scores = (data - mean) / std_dev

# Identification des outliers
outliers = data[np.abs(z_scores) > 3]

print(f"Z-scores : {z_scores}")
print(f"Valeurs aberrantes : {outliers}")
```

#### 2. **Normalisation des Données**  
Le z-score permet de transformer des données pour qu'elles aient une moyenne de 0 et un écart-type de 1, ce qui est essentiel dans certains algorithmes de machine learning.

```python
# Normalisation avec z-score
normalized_data = (data - mean) / std_dev
print(f"Les données normalisées : {normalized_data}")
```

---

### **Pourquoi $z > 3$ ou $z < -3$ est un Seuil Courant ?**

La règle des **68-95-99.7** pour les données suivant une distribution normale explique pourquoi un seuil de 3 écarts-types est utilisé :
- **68 %** des données sont dans l'intervalle $[-1\sigma, +1\sigma]$,
- **95 %** des données sont dans l'intervalle $[-2\sigma, +2\sigma]$,
- **99.7 %** des données sont dans l'intervalle $[-3\sigma, +3\sigma]$.

Par conséquent, les données en dehors de cet intervalle ($z > 3$ ou $z < -3$) sont extrêmement rares, représentant moins de 0.3 % des observations.

---

### **Résumé**

Le **z-score** est une méthode simple mais puissante pour :
1. Identifier les valeurs aberrantes.
2. Normaliser des ensembles de données.
3. Comparer des distributions différentes.

Grâce à NumPy, vous pouvez rapidement calculer les z-scores et les appliquer dans des contextes variés comme le machine learning, l'analyse de données ou la détection d'anomalies.
