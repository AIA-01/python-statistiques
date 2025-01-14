# Introduction à Pandas et les pivots

Pandas est une bibliothèque essentielle en Python pour manipuler, analyser et visualiser des données tabulaires (comme des feuilles Excel ou des bases de données SQL). Parmi ses nombreuses fonctionnalités, les pivots jouent un rôle central pour réorganiser et résumer les données.

Ce cours couvre :
- Les bases de Pandas : chargement et visualisation de données.
- Les pivots avec `pivot()` et `pivot_table()`.
- La gestion des doublons dans les données pivotées.

---

## 1. Bases de Pandas

### Chargement des données
Pour commencer, vous pouvez charger des données dans un DataFrame Pandas à partir d'un fichier CSV :

```python
import pandas as pd

data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'Alice', 'Bob'],
    'Subject': ['Math', 'Math', 'Math', 'History', 'History'],
    'Score': [85, 90, 95, 88, 79]
}

# Création d'un DataFrame
df = pd.DataFrame(data)
print(df)
```
**Sortie :**
```
      Name  Subject  Score
0    Alice     Math     85
1      Bob     Math     90
2  Charlie     Math     95
3    Alice  History     88
4      Bob  History     79
```

### Visualisation des données
Les principales méthodes pour inspecter un DataFrame sont :
- `df.head()` : affiche les 5 premières lignes.
- `df.info()` : donne un résumé des colonnes et types de données.
- `df.describe()` : fournit des statistiques descriptives pour les colonnes numériques.

---

## 2. Les pivots avec Pandas

### Fonction `pivot()`
La fonction `pivot()` permet de transformer les colonnes en lignes et inversement. Elle réorganise les données en trois dimensions principales :
- **Index** : les lignes du tableau.
- **Columns** : les colonnes du tableau.
- **Values** : les valeurs à remplir.

#### Exemple simple
```python
pivot_table = df.pivot(index='Name', columns='Subject', values='Score')
print(pivot_table)
```
**Sortie :**
```
Subject  History  Math
Name                  
Alice       88.0  85.0
Bob         79.0  90.0
Charlie      NaN  95.0
```
- `Name` devient l’index (les lignes).
- `Subject` devient les colonnes.
- `Score` remplit les cellules.

**Remarque** :
- Si une combinaison `index` + `columns` contient des doublons, `pivot()` génère une erreur.

---

### Fonction `pivot_table()`
La fonction `pivot_table()` est une version plus robuste de `pivot()` car elle gère les doublons en appliquant une fonction d’agrégation comme `mean`, `sum`, ou `max`.

#### Exemple avec des doublons
Données :
```python
# Nouveau DataFrame avec des doublons
data = {
    'Name': ['Alice', 'Bob', 'Alice', 'Bob', 'Alice'],
    'Subject': ['Math', 'Math', 'Math', 'History', 'History'],
    'Score': [85, 90, 88, 79, 82]
}
df = pd.DataFrame(data)
```
**Sortie :**
```
    Name  Subject  Score
0  Alice     Math     85
1    Bob     Math     90
2  Alice     Math     88
3    Bob  History     79
4  Alice  History     82
```

Si vous tentez un `pivot()` :
```python
pivot_table = df.pivot(index='Name', columns='Subject', values='Score')
```
**Erreur :**
```
ValueError: Index contains duplicate entries, cannot reshape
```

Pour corriger cela, utilisez `pivot_table()` avec une fonction d'agrégation :
```python
pivot_table = df.pivot_table(index='Name', columns='Subject', values='Score', aggfunc='mean')
print(pivot_table)
```
**Sortie :**
```
Subject  History  Math
Name                  
Alice       82.0  86.5
Bob         79.0  90.0
```
- Les doublons pour Alice en Math (85 et 88) ont été agrégés par la moyenne : **(85 + 88) / 2 = 86.5**.

### Autres fonctions d’agrégation
- **Somme des scores** :
  ```python
  df.pivot_table(index='Name', columns='Subject', values='Score', aggfunc='sum')
  ```
- **Valeur maximale** :
  ```python
  df.pivot_table(index='Name', columns='Subject', values='Score', aggfunc='max')
  ```
- **Nombre d’entrées (compte)** :
  ```python
  df.pivot_table(index='Name', columns='Subject', values='Score', aggfunc='count')
  ```

---

## 3. Identification et gestion des doublons

### Identifier les doublons
Vous pouvez vérifier s’il y a des doublons dans une combinaison de colonnes spécifique :
```python
duplicates = df[df.duplicated(subset=['Name', 'Subject'], keep=False)]
print(duplicates)
```
**Sortie :**
```
    Name Subject  Score
0  Alice    Math     85
2  Alice    Math     88
```

### Supprimer les doublons
Pour garder uniquement une occurrence par combinaison `Name` + `Subject` :
```python
df_no_duplicates = df.drop_duplicates(subset=['Name', 'Subject'], keep='first')
```

---

## 4. Récapitulatif

| Fonction         | Utilité                                                                 |
|------------------|------------------------------------------------------------------------|
| `pivot()`        | Réorganiser un DataFrame en spécifiant les lignes, colonnes, et valeurs. |
| `pivot_table()`  | Gérer les doublons avec une fonction d’agrégation.                            |
| `duplicated()`   | Identifier les lignes dupliquées dans le DataFrame.                         |
| `drop_duplicates()` | Supprimer les doublons selon des colonnes spécifiques.                      |

---