### La méthode `apply` en Pandas

La méthode `apply()` en **Pandas** est extrêmement puissante et permet d'appliquer une fonction à chaque élément d'une **série** ou d'un **DataFrame**. 

Elle est particulièrement utile lorsque vous souhaitez effectuer des opérations complexes sur des données ou appliquer des fonctions personnalisées sans avoir à recourir à des boucles explicites.

#### 1. **Utilisation de `apply()` avec une Série** :

Lorsque vous avez une **Série** (colonne d'un DataFrame) et que vous souhaitez appliquer une fonction à chaque élément de cette série, vous pouvez utiliser `apply()`. Cela vous permet de transformer les données de la colonne ou d'effectuer des calculs complexes.

**Exemple** :
Supposons que vous avez une série de nombres et que vous souhaitez calculer le carré de chaque élément.

```python
import pandas as pd

# Création d'une série
data = pd.Series([1, 2, 3, 4, 5])

# Appliquer une fonction pour calculer le carré de chaque élément
squared_data = data.apply(lambda x: x ** 2)

print(squared_data)
```

**Sortie** :
```
0     1
1     4
2     9
3    16
4    25
dtype: int64
```

Ici, nous utilisons `apply()` pour appliquer une fonction lambda qui calcule le carré de chaque valeur dans la série.

#### 2. **Utilisation de `apply()` avec un DataFrame** :

Lorsqu'on travaille avec un **DataFrame**, la méthode `apply()` permet d'appliquer une fonction sur chaque **colonne** ou chaque **ligne** (selon l'axe spécifié). Par défaut, `apply()` s'applique aux colonnes (axe=0), mais vous pouvez spécifier l'axe pour appliquer la fonction sur les lignes (axe=1).

**Exemple 1 : Appliquer une fonction sur chaque colonne** :
Supposons que vous ayez un DataFrame avec des valeurs numériques et que vous souhaitiez calculer la somme de chaque colonne.

```python
df = pd.DataFrame({
    'A': [1, 2, 3],
    'B': [4, 5, 6],
    'C': [7, 8, 9]
})

# Appliquer une fonction sur chaque colonne
column_sum = df.apply(sum)
print(column_sum)
```

**Sortie** :
```
A     6
B    15
C    24
dtype: int64
```

Ici, nous appliquons la fonction `sum()` à chaque colonne du DataFrame. Comme la somme est la fonction par défaut, cela donne directement la somme de chaque colonne.

**Exemple 2 : Appliquer une fonction sur chaque ligne** :
Vous pouvez également appliquer une fonction sur chaque ligne. Par exemple, si vous voulez calculer la somme des valeurs sur chaque ligne.

```python
# Appliquer une fonction sur chaque ligne
row_sum = df.apply(sum, axis=1)
print(row_sum)
```

**Sortie** :
```
0    12
1    15
2    18
dtype: int64
```

Ici, nous avons spécifié `axis=1` pour indiquer que nous voulons appliquer la fonction sur chaque ligne (et non sur chaque colonne).

#### 3. **Application de fonctions personnalisées avec `apply()`** :

Vous pouvez appliquer des fonctions personnalisées avec `apply()`. Cela permet de réaliser des opérations plus complexes.

**Exemple : Fonction personnalisée pour calculer la différence entre deux colonnes** :

```python
df = pd.DataFrame({
    'A': [1, 2, 3],
    'B': [4, 5, 6]
})

# Appliquer une fonction personnalisée pour calculer la différence
def calculate_difference(row):
    return row['B'] - row['A']

difference = df.apply(calculate_difference, axis=1)
print(difference)
```

**Sortie** :
```
0    3
1    3
2    3
dtype: int64
```

Ici, la fonction `calculate_difference()` soustrait les valeurs de la colonne `'A'` de celles de la colonne `'B'` pour chaque ligne.

#### 4. **Optimisation avec `apply()`** :

L'utilisation de `apply()` peut parfois être moins performante que les opérations vectorisées directes de Pandas, car elle applique une fonction sur chaque élément ou chaque ligne, ce qui peut être plus lent sur de grands ensembles de données. Cependant, elle reste très utile pour les calculs personnalisés.

### Conclusion

La méthode `apply()` est un outil puissant de Pandas qui vous permet d'appliquer des fonctions complexes à des séries ou des DataFrames de manière flexible. Voici les points clés à retenir :

- `apply()` permet d'appliquer une fonction à une série ou à un DataFrame.
- Vous pouvez appliquer une fonction à chaque **élément** d'une série, ou sur **chaque ligne/colonne** d'un DataFrame.
- Vous pouvez utiliser des fonctions standard comme `sum()`, ou des fonctions personnalisées que vous définissez.
- Faites attention à la performance : pour des calculs simples, privilégiez les opérations vectorisées de Pandas lorsque cela est possible.

La méthode `apply()` est idéale pour des transformations ou calculs plus complexes que ceux que vous pouvez effectuer avec les fonctions vectorisées classiques.


### Exercice

1. Créez une fonction `extract_numbers_starting_with_n` qui extrait les valeurs numériques du dataset `items` du projet.

```python
# première version sans re (re == expression régulière dans Python)
def extract_numbers_starting_with_n(value):
    # le join prend une liste et joint avec une chaine de caractères les valeurs de la liste
    # attention le séparateur est dans la chaine au début avant la méthode elle-meme "".join(l)
    return " ".join( [ e for e in value.split() if e[0] == 'n' ])

itemsSearch = items[ (items['property'] != 'available' )  & (df['property'] != 'categoryid' ) ]

itemsSearch['value'].apply( extract_numbers_starting_with_n )

# deuxième version 
import re

def extract_numbers_starting_with_n(value):
    result = re.findall(r'n[\d\.]+', value)

    return "".join( result )

dfSearch['value'].apply(extract_numbers_starting_with_n)

itemsSearch = items[ (items['property'] != 'available' )  & (df['property'] != 'categoryid' ) ]

itemsSearch['value'].apply( extract_numbers_starting_with_n )
```