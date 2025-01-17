### Introduction aux expressions régulières

Les **expressions régulières** (ou **regex**) sont des séquences de caractères qui définissent un motif de recherche. Elles sont utilisées pour trouver, manipuler ou remplacer des textes dans des chaînes de caractères.

### Fonction `re.findall()`

La fonction `findall()` de Python, du module `re`, permet de rechercher toutes les occurrences qui correspondent à un motif dans une chaîne donnée. Elle retourne une liste de toutes les sous-chaînes qui correspondent au motif.

```python
import re
result = re.findall(r"motif", "chaîne de texte")
```

Le motif peut être une expression régulière que l'on veut chercher dans le texte.

### Explication de l'expression régulière `r'n[\d\.]+'`

L'expression régulière `r'n[\d\.]+'` permet de rechercher des nombres qui commencent par la lettre `n` dans une chaîne de caractères.

1. **`n`** :
   - Ce caractère est littéral, il recherche exactement la lettre `n` dans la chaîne.
   
2. **`[\d\.]`** :
   - **`[]`** : Les crochets délimitent un groupe de caractères possibles à rechercher. Cela signifie "soit ce caractère, soit ce caractère".
   - **`\d`** : Ce caractère spécial représente **un chiffre** (0 à 9).
   - **`\.`** : Le point `.` dans une expression régulière a une signification spéciale (il peut correspondre à n'importe quel caractère). Ici, il est échappé par le **backslash (`\`)** pour signifier "le caractère point" et non n'importe quel caractère.
   - Donc, **`[\d\.]`** signifie "un chiffre ou un point".
   
3. **`+`** :
   - Le caractère **`+`** indique que le groupe qui précède (dans ce cas, les chiffres et les points) peut apparaître **une ou plusieurs fois**. Cela permet d'extraire des nombres avec plusieurs chiffres ou des nombres décimaux.
   
### Exemple d'utilisation avec `re.findall()`

Prenons un exemple où nous avons une chaîne de texte contenant des nombres qui commencent par `n`, et utilisons `re.findall()` pour extraire ces valeurs.

### Exemples 1:

```python
import re

# on cherche 1 dans le texte "n891 879 n785.90 n78.00 987 876" dès qu'il trouve un "1" il est retiré de la recherche 
result = re.findall(r"1", "n891 879 n785.90 n78.00 987 876")
# ['1']

# Autre exemple 12 ou 1 dans cet ordre si vous changez l'ordre 1 ou 12, cela changera la recherche
re.findall(r'12|1', "n891 112 12 879 n785.90 n78.00 987 876")
# ['1', '1', '12', '12']

motif = r'n[1-9]+\.[1-9]+|n[1-9]+' # une plage de valeur est définie par [1-9] le symbole + <=> de 1 à plusieurs 

"""
n[1-9]+\.[1-9]+|n[1-9]+
"""
n suivi d'un nombre compris entre 1 et 9 répété(s) de 1 à plusieurs fois, suivi d'un point . et d'un nombre compris 
entre 1 à 9 de 1 à plusieurs fois OU ( avec le | ) ...
"""

motif = r'12|[12]'
re.findall(motif, "n891 12 21" )

"""

re.findall(motif,  "n891 112 12 879 n785.91 n78.10 987 876" )
# ['1', '12', '2', '1']
```


### Exemple 2 :

```python
import re

# Exemple de chaîne contenant des nombres commençant par 'n'
value = "1116713 960601 n277.200 n552.000 n720.000 424566"

# Utilisation de re.findall pour extraire les nombres commençant par 'n'
numbers = re.findall(r'n[\d\.]+', value)

print(numbers)
```

### Résultat :

```
['n277.200', 'n552.000', 'n720.000']
```

### Explication du résultat :
- La fonction `re.findall()` parcourt la chaîne `value` et cherche toutes les correspondances qui commencent par `n` et sont suivies de chiffres et de points.
- Elle trouve trois correspondances : `n277.200`, `n552.000`, et `n720.000`.


## `search` 

`search` est une autre fonction de re qui permet de trouver la première occurence.

```python
import re

r = re.search(motif,  "n891 12 21"  )

# récupération de la valeur qui match si elle existe avec la méthode group
print( r.group() )
```

### Exercice d'application

```python
# capturer les nombres préfixés par x suivit d'un chiffre puis suivi d'une lettre
text = "n891 xbcacd 112 12 879 x12 x2 n785..91 n78.10 987 xa  876"

# Suivi d'un chiffre ou d'une lettre plusieurs fois 
motif = r'x[\da-zA-Z]+'
print( re.findall( motif, text ) )

# Suivi que d'un chiffre ou une lettre
motif = r'x[\da-zA-Z]'
print( re.findall( motif, text ) )

"""
['xbcacd', 'x12', 'x2', 'xa']
['xb', 'x1', 'x2', 'xa']
"""

```


### Cas d'usage

Cette expression régulière peut être utile dans de nombreux scénarios, comme par exemple :
- **Extraction de nombres spécifiques** dans des logs ou des chaînes de texte qui suivent un certain format.
- **Filtrage de valeurs particulières** dans des données textuelles où certaines informations sont précédées par un caractère particulier (comme ici `n`).



