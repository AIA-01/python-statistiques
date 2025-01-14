### **Complément avec Pandas, Matplotlib et Seaborn**

Nous allons travailler avec un nouveau jeu de données fictif qui contient des informations sur les ventes de produits dans une boutique en ligne. Ce jeu de données inclut les colonnes suivantes :

- `product_id` : L'identifiant unique de chaque produit.
- `category` : La catégorie du produit (par exemple, électronique, vêtement, etc.).
- `price` : Le prix de chaque produit.
- `quantity_sold` : Le nombre d'unités vendues.
- `date` : La date de la vente.
- `region` : La région où la vente a eu lieu.

#### **1. Chargement et Préparation des Données**

Avant de visualiser nos données, nous devons les charger et les préparer. Voici comment nous pourrions faire cela :

```python
import pandas as pd

# Charger un jeu de données fictif
data = {
    'product_id': [101, 102, 103, 104, 105, 106, 107, 108, 109, 110],
    'category': ['Electronics', 'Clothing', 'Electronics', 'Home', 'Clothing', 'Electronics', 'Home', 'Clothing', 'Electronics', 'Clothing'],
    'price': [150, 40, 200, 50, 30, 180, 60, 45, 220, 55],
    'quantity_sold': [30, 50, 25, 40, 60, 20, 35, 45, 15, 70],
    'date': pd.to_datetime(['2025-01-01', '2025-01-02', '2025-01-03', '2025-01-04', '2025-01-05', '2025-01-06', '2025-01-07', '2025-01-08', '2025-01-09', '2025-01-10']),
    'region': ['North', 'South', 'East', 'West', 'North', 'South', 'East', 'West', 'North', 'South']
}

# Convertir en DataFrame
df = pd.DataFrame(data)
```

---

### **2. Histogramme pour Visualiser la Répartition des Prix des Produits**

Un **histogramme** est une excellente visualisation pour observer la distribution des valeurs dans une série numérique. Dans cet exemple, nous allons visualiser la distribution des prix des produits dans le jeu de données.

```python
import matplotlib.pyplot as plt

# Histogramme pour les prix des produits
plt.figure(figsize=(8,6))
plt.hist(df['price'], bins=5, color='lightblue', edgecolor='black')
plt.title("Distribution des Prix des Produits")
plt.xlabel("Prix des Produits")
plt.ylabel("Nombre de Produits")
plt.show()
```

**Explication du code :**
- **`plt.hist()`** : Crée un histogramme avec les prix des produits.
  - **`bins=5`** : Détermine le nombre de barres dans l'histogramme (ici, 5 plages de prix).
  - **`color='lightblue'`** : Spécifie la couleur des barres.
  
Cet histogramme permet de visualiser comment les prix des produits sont répartis dans la boutique.

---

### **3. Graphique à Barres pour la Répartition des Catégories de Produits**

Un **graphique à barres** est idéal pour comparer la fréquence des différentes catégories de produits. Nous allons visualiser la répartition des produits par catégorie.

```python
import seaborn as sns

# Graphique à barres pour la répartition des catégories
plt.figure(figsize=(8,6))
sns.countplot(x='category', data=df, palette='Set2')
plt.title("Répartition des Produits par Catégorie")
plt.xlabel("Catégorie de Produit")
plt.ylabel("Nombre de Produits")
plt.show()
```

**Explication du code :**
- **`sns.countplot()`** : Crée un graphique à barres pour compter le nombre d'occurrences de chaque catégorie.
  - **`palette='Set2'`** : Choisit une palette de couleurs pour le graphique.

Ce graphique vous permet de comprendre quelles catégories sont les plus représentées dans le dataset.

---

### **4. Graphique Linéaire pour les Ventes au Fil du Temps**

Les **graphique linéaire (séries temporelles)** sont parfaits pour observer les tendances dans le temps. Ici, nous allons examiner l'évolution du nombre d'unités vendues par jour.

```python
# Total des ventes par date
sales_by_date = df.groupby('date')['quantity_sold'].sum()

# Graphique linéaire des ventes par jour
plt.figure(figsize=(10,6))
plt.plot(sales_by_date.index, sales_by_date.values, marker='o', color='green')
plt.title("Ventes Totales par Jour")
plt.xlabel("Date")
plt.ylabel("Nombre de Ventes")
plt.xticks(rotation=45)
plt.grid(True)
plt.show()
```

**Explication du code :**
- **`groupby('date')['quantity_sold'].sum()`** : Agrège les ventes totales par date.
- **`plt.plot()`** : Crée un graphique linéaire des ventes au fil du temps.
  
Ce graphique montre l’évolution des ventes par jour et peut être utile pour analyser les tendances saisonnières ou les promotions.

---

### **5. Boîte à Moustaches (Boxplot) pour les Prix des Produits par Catégorie**

Un **boxplot** est un excellent moyen d’explorer la distribution des prix au sein de chaque catégorie et de repérer les valeurs aberrantes (outliers).

```python
# Boxplot pour les prix par catégorie
plt.figure(figsize=(8,6))
sns.boxplot(x='category', y='price', data=df, palette='Set3')
plt.title("Distribution des Prix des Produits par Catégorie")
plt.xlabel("Catégorie de Produit")
plt.ylabel("Prix des Produits")
plt.show()
```

**Explication du code :**
- **`sns.boxplot()`** : Crée un boxplot pour visualiser la distribution des prix par catégorie.
  - **`x='category'`** et **`y='price'`** : Définissent les axes pour les catégories et les prix.
  - **`palette='Set3'`** : Choisit une palette de couleurs.

Le boxplot aide à visualiser la médiane des prix, les quartiles et les valeurs aberrantes dans chaque catégorie.

---

### **6. Graphique en Nuage de Points (Scatter Plot) pour les Ventes en Fonction du Prix**

Un **nuage de points** permet de visualiser la relation entre deux variables continues. Par exemple, on peut vouloir examiner si le prix des produits a un impact sur le nombre d’unités vendues.

```python
# Scatter plot pour les ventes en fonction du prix
plt.figure(figsize=(8,6))
sns.scatterplot(x='price', y='quantity_sold', data=df, color='purple', s=100)
plt.title("Relation entre le Prix des Produits et les Ventes")
plt.xlabel("Prix des Produits")
plt.ylabel("Nombre de Ventes")
plt.show()
```

**Explication du code :**
- **`sns.scatterplot()`** : Crée un graphique à nuage de points.
  - **`x='price'`** et **`y='quantity_sold'`** : Définissent les variables pour les axes des x et des y.
  - **`s=100`** : Spécifie la taille des points.

Ce graphique permet d'observer la relation entre le prix des produits et leur popularité en termes de ventes.

---

### **Conclusion**

Dans ce cours, nous avons exploré différents types de visualisations utiles pour analyser des données avec **Pandas**, **Matplotlib**, et **Seaborn** :

1. **Histogramme** : Visualisation de la distribution des prix des produits.
2. **Graphique à barres** : Répartition des produits par catégorie.
3. **Graphique linéaire** : Tendances des ventes dans le temps.
4. **Boxplot** : Analyse des prix par catégorie et détection des valeurs aberrantes.
5. **Nuage de points** : Relation entre le prix et les ventes.
