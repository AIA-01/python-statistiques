## **Cours Pandas : Retail Rocket Dataset**

### **1. Introduction à Pandas**
Pandas est une bibliothèque Python essentielle pour l'analyse de données. Elle fournit des structures de données puissantes, comme les DataFrames et les Series, pour manipuler, nettoyer, et analyser des données efficacement.

#### **Installation**
Si Pandas n'est pas installé, utilisez la commande suivante :
```bash
pip install pandas
```

---

### **2. Chargement des données**
Nous allons travailler avec le dataset Retail Rocket, qui contient trois fichiers principaux :
- **events.csv** : contient des informations sur les interactions des utilisateurs avec les produits.
- **item_properties_part1.csv** et **item_properties_part2.csv** : contiennent les propriétés des articles.

#### **Charger un fichier CSV**
```python
import pandas as pd

# Charger les fichiers
events = pd.read_csv("events.csv")
item_properties1 = pd.read_csv("item_properties_part1.csv")
item_properties2 = pd.read_csv("item_properties_part2.csv")

# Aperçu des données
print(events.head())
print(item_properties1.head())
```

---

### **3. Exploration des données**
Pandas fournit plusieurs méthodes pour explorer et comprendre vos données.

#### **Dimensions et types de données**
```python
# Taille des DataFrames
print(events.shape)
print(item_properties1.info())

# Statistiques descriptives
print(events.describe())
```

#### **Aperçu rapide**
- `shape` donne le nombre de lignes et colonnes.
- `info()` montre les types de données (int, float, object).
- `describe()` fournit des statistiques basiques pour les colonnes numériques.

---

### **4. Filtrer et sélectionner des données**
#### **Accès aux colonnes**
```python
# Sélectionner une colonne
print(events["event"].head())

# Sélectionner plusieurs colonnes
print(events[["timestamp", "event"]].head())
```

#### **Filtrer les lignes**
```python
# Filtrer les événements "view"
view_events = events[events["event"] == "view"]
print(view_events.head())
```

---

### **5. Manipulation des données**
#### **Créer de nouvelles colonnes**
```python
# Convertir les timestamps en format lisible
events["datetime"] = pd.to_datetime(events["timestamp"], unit="ms")
print(events.head())
```

#### **Joindre deux DataFrames**
Fusionner les deux fichiers de propriétés d'articles :
```python
item_properties = pd.concat([item_properties1, item_properties2])
print(item_properties.shape)
```

#### **Regrouper les données**
Analyser les événements par type :
```python
event_counts = events.groupby("event").size()
print(event_counts)
```

---

### **6. Nettoyage des données**
#### **Gestion des valeurs manquantes**
```python
# Vérifier les valeurs manquantes
print(item_properties.isnull().sum())

# Supprimer les lignes avec des valeurs manquantes
item_properties_cleaned = item_properties.dropna()
```

#### **Supprimer les doublons**
```python
# Supprimer les doublons
item_properties_cleaned = item_properties.drop_duplicates()
```

---

### **7. Visualisation avec Pandas**
Pandas peut générer des graphiques simples pour analyser rapidement les données.

#### **Histogramme**
```python
events["event"].value_counts().plot(kind="bar", title="Types d'événements")
```

#### **Courbe temporelle**
```python
events.set_index("datetime")["event"].resample("D").count().plot(title="Événements par jour")
```

---

### **8. Sur nos données à étudier**

Reprenez nos données kaggle 

#### Partie 1 - Formatage des données

```python
import datetime
import pandas as pd

# Charger les fichiers CSV dans des DataFrames Pandas
category_tree = pd.read_csv('data/category_tree.csv')
events = pd.read_csv('data/events.csv')
item_properties_part1 = pd.read_csv('data/item_properties_part1.csv')
item_properties_part2 = pd.read_csv('data/item_properties_part2.csv')
```

1. Fusionnez les données en un seul DataFrame.
2. Conversion des timestamps en datetime : utilisez `to_datetime` de Pandas
3. Ajoutez le jour de la semaine dans le DataFrame fusionné.

#### Partie 3 - Taux de conversion

Avec le DataFrame `events`

L'objectif est de comparer les taux de conversion des deux groupes et de voir si les utilisateurs qui ajoutent des produits au panier ont un taux de conversion plus élevé que ceux qui se contentent de visualiser les produits. Cela peut aider à comprendre l'impact de l'ajout au panier sur les décisions d'achat.

1. Sélectionner les événements "view" et "addtocart".
2. Créer un DataFrame des utilisateurs ayant ajouté un produit au panier
3. Créer un DataFrame des utilisateurs ayant seulement vu des produits
4. Créer un DataFrame des événements "transaction" pour calculer les conversions
5. Calculer le taux de conversion pour les deux groupes

### Partie 3 - faire un document détaillé sur les champs des DataFrames étudiés

Expliquez les champs du DataFrame.


