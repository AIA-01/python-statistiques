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

1. Fusionnez les données item_properties_part1 et item_properties_part2 en un seul DataFrame : `concat`.
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

```python
import pandas as pd
events = pd.read_csv('data/events.csv')

# Partie 1
# Sachant que l'utilisateur a mis son produit dans le panier on calcule le taux d'achat 
addtocart_conversions = transaction_events[ transaction_events['visitorid'].isin(users_addtocart)]['visitorid']
addtocart_total_users = len(users_addtocart)

addtocart_conversion_rate = len( addtocart_conversions ) / addtocart_total_users * 100
print(f"Taux de conversion des utilisateurs ayant ajouté des produits au panier : {addtocart_conversion_rate:.2f}%")


# Partie 2 
# Calcul le taux des produits uniquement vus et achetés 
users_addtocart = addtocart_events['visitorid'].unique()
users_transaction = transaction_events['visitorid'].unique()

view_only_conversions = view_events[ ~view_events['visitorid'].isin(users_addtocart) & view_events['visitorid'].isin(users_transaction)]
['visitorid']

view_only_users = events[  ~events['visitorid'].isin(users_addtocart) ]

view_only_total_users = len( view_only_users )

view_only_conversion_rate = len(view_only_conversions)/ view_only_total_users * 100
print(f"Taux de conversion des utilisateurs ayant seulement vu des produits : {view_only_conversion_rate:.3f}%")
```

### Partie 3 - faire un document détaillé sur les champs des DataFrames étudiés

Expliquez les champs du DataFrame.


### Partie 4  - graphique

1. **Visualisation de la distribution des événements** :
   Créez une visualisation pour afficher le nombre d'occurrences de chaque type d'événement (par exemple, "view", "addtocart", "transaction") dans le DataFrame `events`. Utilisez un graphique en barres pour montrer la répartition de ces événements.
     - *Indications :* Utilisez la fonction `sns.countplot()` pour créer le graphique en barres. N'oubliez pas d'ajouter un titre ainsi que des labels pour les axes afin de rendre le graphique plus lisible.

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd

events = pd.read_csv('data/events.csv')

plt.figure(figsize=(10, 6))
sns.countplot(data=events, x='event') 
plt.title('Distribution des événements')
plt.xlabel('Type d\'événement')
plt.ylabel('Nombre d\'occurrences')
plt.xticks(rotation=45)
plt.show()
```


2. **Affichage d'un graphique circulaire des événements** :
   Créez un graphique en camembert pour visualiser la distribution des événements dans le DataFrame `events`. 
     - *Indications :* Utilisez `plt.pie()` pour créer le graphique circulaire. Explosez légèrement certaines tranches pour les mettre en évidence et affichez les pourcentages avec `autopct='%1.1f%%'`. Ajoutez un titre pour clarifier ce que le graphique montre.

```python
event_counts = events['event'].value_counts()

# Créer un graphique circulaire
plt.figure(figsize=(8, 8))
plt.pie(event_counts, labels=event_counts.index, autopct='%1.1f%%', explode=[0.1] * len(event_counts))  # Explose légèrement chaque tranche
plt.title('Répartition des événements')
plt.show()
```

1. **Personnalisation du graphique** :
   En utilisant le graphique en camembert créé précédemment, assurez-vous que l'aspect du graphique est circulaire (c'est-à-dire que l'axe est égal). Que faites-vous dans le code pour garantir que le graphique ait une forme circulaire ?
     - *Indications :* Utilisez la fonction `plt.axis('equal')` pour vous assurer que le graphique circulaire a un aspect proportionnel et bien centré.

```python
plt.figure(figsize=(8, 8))
plt.pie(event_counts, labels=event_counts.index, autopct='%1.1f%%', explode=[0.1] * len(event_counts))  # Explose légèrement chaque tranche
plt.title('Répartition des événements')
plt.axis('equal')  # Assurer que le graphique soit circulaire
plt.show()
```

1. **Comparaison entre les types d'événements** :
   Après avoir créé le graphique en barres et en camembert, quelle conclusion pouvez-vous tirer sur la répartition des événements dans le DataFrame ? Quel événement semble être le plus fréquent, et comment cela pourrait-il être utile pour l'analyse du comportement des utilisateurs ?
     - *Indications :* Analysez la fréquence des événements `view`, `addtocart`, et `transaction`, et discutez de l'importance de ces événements dans l'analyse de la conversion et de l'engagement des utilisateurs.
  
Beaucoup de visiteurs consultent les produits sans les acheter.

### Partie 5 - analyse d'autres fichiers

1. Analyse des catégories de produits

   1. Visualisez le nombre de sous-catégories pour chaque catégorie principale.
   2. Listez les catégories sans parent (racines).
   3. Identifiez les catégories ayant le plus de sous-catégories.

```python
category_tree = pd.read_csv('data/category_tree.csv')

# parentid est null
principals_categories = category_tree[category_tree['parentid'].isnull()]['categoryid']

# les catégories ayant des sous-catégories  
appear_as_parent = principals_categories[principals_categories.isin(category_tree['parentid'])]

if not appear_as_parent.empty:
    print(appear_as_parent.tolist())

# sous catégories
sub_categories = category_tree[category_tree['parentid'].notnull()]['parentid']
sub_categories.value_counts()
```

---

1. Analyse des produits

   1. Affichez le nombre de produits par catégorie.
   2. Listez les propriétés disponibles pour les produits.
   3. Trouvez, si il(s) exist(ent) les produits appartenant à plusieurs catégories.

---

3. Exploration croisée des catégories et des produits

   Travaillez sur le DataFrame `items` (ensembles des produits).

   1. Quels types de property sont associés aux produits ?. Utilisez la méthode `apply` et `unique` sur le DataFrame.
   2. Identifiez les produits associés à des categoryid spécifiques.

---
