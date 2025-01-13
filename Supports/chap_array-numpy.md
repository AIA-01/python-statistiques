## **Chapitre : Introduction aux Arrays avec NumPy**

### **1. Introduction aux Arrays**

>[!NOTE]
> Un array dans NumPy est **une structure de données optimisée** pour effectuer des calculs numériques rapidement. Contrairement aux listes Python, les arrays NumPy ont des **types homogènes** : tous les éléments doivent être du même type.

- **Notion de type dans NumPy :**
  Chaque array a un type défini (`dtype`), qui peut être spécifié lors de sa création.  
  Les types les plus courants sont :
  - `int` (entiers)
  - `float` (nombres décimaux)
  - `bool` (valeurs booléennes : True/False)
  - `str` (chaînes de caractères)

>[!NOTE] 
>Avantages des Arrays avec types homogènes :
>Consommation mémoire optimisée.
>
>Calculs plus rapides grâce à l'utilisation de types adaptés.

---

### **2. Créer un Array avec un Type**
#### **Array de type entier (`int`) :**
```python
import numpy as np

numbers = np.array([1, 2, 3, 4], dtype=int)
print("Numbers :", numbers)
print("Type:", numbers.dtype)
```

#### **Array de type float :**
```python
# Créer un array avec des floats
numbersf = np.array([1, 2, 3, 4], dtype=float)
print("Numbers:", numbersf)
print("Type:", numbersf.dtype)
```

#### **Array de type booléen :**
```python
# Créer un array booléen
valuesb = np.array([True, False, True], dtype=bool)
print("Values:", valuesb)
print("Type:", valuesb.dtype)
```

Remarque vous pouvez faire la somme des valeurs True, Numpy les comptera comme +1 dans la somme.

```python
print(np.sum(valuesb)) # affiche 2 
```

---

### **3. Conversion de type (casting)**
NumPy permet de convertir facilement les types d'un array existant avec la méthode `.astype`.

#### **Exemple :**
```python
# Créer un array d'entiers
num = np.array([1, 2, 3, 4], dtype=int)

# Convertir en float
num = num.astype(float)
print("Num converti en float :", num)
print("Type:", num.dtype)

```

#### **Attention :**
Lors de la conversion, certaines valeurs peuvent être modifiées ou perdues :
```python
# Conversion float vers int (perte des décimales)
numbersf = np.array([1.7, 2.3, 3.9])
numbersInt = numbersf.astype(int)
print("Numbers:", numbersf)
print("Type:", numbersInt)
```

---

### **4. Attributs et Propriétés**
#### **Attributs importants :**
```python
numbers = np.array([1, 2, 3, 4], dtype=float)

# Nombre de dimensions
print("Dimensions :", numbers.ndim)

# Forme
print("Forme :", numbers.shape)

# Taille
print("Nombre d'éléments :", numbers.size)

# Type des éléments
print("Type des éléments :", numbers.dtype)
```

---

### **5. Opérations et Calculs avec des Types**
Les types influencent les calculs dans NumPy :
#### **Exemple avec des floats et des entiers :**
```python
numbersInt = np.array([1, 2, 3])
numbersFloat = np.array([1.5, 2.5, 3.5])

# Addition
result = numbersInt + numbersFloat
print("Résultat (int + float) :", result)
print("Type du résultat :", result.dtype)
```

---

### **6. Exercices pratiques**

#### **Exercice 1 : Créer des arrays avec des types spécifiques**

Pour certains exercices utilisez `np.arange`

1. Créez un array contenant les nombres entiers de 1 à 10 avec le type `int`.
2. Créez un array contenant les nombres décimaux de 1.0 à 10.0 avec le type `float`.
3. Créez un array contenant uniquement des valeurs `True` et `False`.

```python
#  Correction
## 1
a = np.array( range(1, 11) , dtype=int )
# identique mais avec arange
a = np.arange(1, 11, dtype=int )

## 2
b = np.arange(1, 11, dtype=float )

## 3
c = np.array( [True, False, True ], dtype=bool)
d = np.zeros(10, dtype=bool) # tableau de False
```

#### **Exercice 2 : Conversion de type**
1. Créez un array avec des nombres décimaux (floats). Convertissez-le en type `int`.
2. Créez un array de type booléen et convertissez-le en type `int`.

```python
# Ex1
e = np.array([1.1, 2.2, 3.3, 4.4], dtype=float)
e = e.astype(int)
# Ex2
f = np.array( [True, False, True ], dtype=bool)
f = f.astype(int)
print(f)

# négation et changement de type
(~np.array([True, False])).astype(int)
```

#### **Exercice 3 : Manipulation des types dans les calculs**
1. Additionnez un array d'entiers et un array de floats. Vérifiez le type du résultat.
2. Multipliez un array booléen par un entier. Observez le résultat.

```python
# 1
g = a + b 
g.dtype
# 2
h = 2*c
```

### **Exercice 4 : Manipulation des types booleans**


Vous utiliserez un tableau np.zeros qui crée un tableau de zéro(s), pensez à le caster pour transformer les zéros en False
```python
N = 10
lamps = np.zeros(N, dtype=bool)
```

>[!NOTE]
>Vous avez une série de lampes alignées, représentées par un array de booléens.  
>Une lampe **allumée** est représentée par `True`.
>  
>Une lampe **éteinte** est représentée par `False`.

- Remarque négation opérateur `~` :
```python
vb = np.array([True, False, True])  # Tableau booléen
inverted = ~vb  # Inverse les valeurs (True <-> False)
print(inverted)  # Résultat : [False  True False]
```

Votre tâche est de manipuler cet array en appliquant différentes opérations logiques pour changer l'état des lampes.

1. **Initialisez un tableau de 10 lampes** (booléens) où toutes les lampes sont éteintes.  
   ```python
   lampes = np.zeros(10, dtype=bool)
   ```

2. **Allumez les lampes aux indices pairs.**  
Allumez les lampes d'indices 0, 2, 4, 6, 8.

1. **Inversez l'état des lampes.**  
Une lampe allumée doit être éteinte, et une lampe éteinte doit être allumée.

1. **Comptez le nombre de lampes allumées.**

2. **Allumez toutes les lampes aux indices multiples de 3.**

3. **Éteignez toutes les lampes allumées qui sont à des indices impairs.**

---

### **Code de départ :**
```python
import numpy as np

# Étape 1 : Initialiser les lampes
lamps = np.zeros(10, dtype=bool)
print("État initial des lampes :", lamps)

# Étape 2 : Allumer les lampes aux indices pairs
# À compléter...

# Étape 3 : Inverser l'état des lampes
# À compléter...

# Étape 4 : Compter les lampes allumées
# À compléter...

# Étape 5 : Allumer les indices multiples de 3
# À compléter...

# Étape 6 : Éteindre les indices impairs
# À compléter...

# Affichez le résultat final
```

### **Exercice 5** Température

Exercice température

Nous avons relevé des températures au mois de Janvier. Répondez aux questions suivantes :

1. Donnez toutes les températures qui sont supérieures à 0.
2. Comparez les températures supérieures et inférieures à 0.
3. Donnez le pourcentage des températures positives sur le mois.
4. Créez un tableau days pour les jours du mois et donnez les jours pour lesquels la température était supérieure à 0.
5. Donnez toutes les températures supérieures à 0 à partir du dixième jour du mois.
6. Remplacez maintenant les températures négatives par la moyenne des températures positives.
```python
january = np.array([-2,  5, -5,  6, -2,  0,  6,  2,  8,  0,  6, -1,  3,  3,  7,  0, -5,
        7,  4,  7,  8, -1,  5, -2,  3, -3, -2,  7,  8,  4,  2])
```
