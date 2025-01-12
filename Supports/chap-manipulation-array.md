## **Cours : Manipulation et gestion des tableaux avec NumPy**

- Sauvegarder et charger des tableaux NumPy.
- Comprendre les manipulations avancées comme la transposition.
- Apprendre à gérer des fichiers `.npy` et `.npz`.

---

### **1. Sauvegarder et charger des tableaux (Saving and Loading Arrays)**

#### **Introduction :**
NumPy permet de sauvegarder des tableaux sous forme de fichiers `.npy` ou `.npz` pour les réutiliser ultérieurement. 

**Ces formats sont optimisés pour la performance.**

#### **Exemple : Sauvegarder un tableau**
```python
import numpy as np

# Créer un tableau
data = np.array([1, 2, 3, 4, 5])

# Sauvegarder dans un fichier .npy
np.save('data.npy', data)
print("Tableau sauvegardé dans 'data.npy'")
```

#### **Exemple : Charger un tableau**
```python
# Charger le tableau depuis le fichier .npy
loaded_data = np.load('data.npy')
print("Tableau chargé :", loaded_data)
```
--- 

### **2. Charger des fichiers .npy (Loading .npy Files)**

#### **Introduction :**
Les fichiers `.npy` contiennent un seul tableau, tandis que `.npz` permet de sauvegarder plusieurs tableaux.

#### **Exemple : Sauvegarder et charger plusieurs tableaux**
```python
# Sauvegarder plusieurs tableaux dans un fichier .npz
a = np.array([1, 2, 3])
b = np.array([[4, 5, 6], [7, 8, 9]])
np.savez('multiple_arrays.npz', a=a, b=b)

# Charger le fichier .npz
loaded = np.load('multiple_arrays.npz')
print("a 1 :", loaded['a'])
print("b 2 :", loaded['b'])
```

---

### **3. Obtenir de l'aide (Getting Help)**

#### **Introduction :**
NumPy offre une documentation intégrée accessible via des commandes Python.

#### **Exemple : Utiliser `help` et `?`**
```python
# Obtenir de l'aide sur une fonction NumPy
help(np.save)

# Ou utiliser le point d'interrogation
np.save?
```

### **4. Mettre à jour et sauvegarder (Update and Save)**

#### **Introduction :**
Modifier un tableau chargé, puis le sauvegarder.

#### **Exemple :**
```python
# Charger un tableau existant
data = np.load('data.npy')

# Modifier le tableau
data += 10

# Sauvegarder les modifications
np.save('updated_data.npy', data)
print("Tableau mis à jour et sauvegardé :", data)
```
---

### **5. Acrobaties avec les tableaux (Array Acrobatics)**

#### **Introduction :**
Les manipulations comme la transposition et la modification des dimensions sont cruciales.

#### **Exemple : Transposition**
```python
# Créer un tableau 2D
A = np.array([[1, 2, 3], [4, 5, 6]])

# Transposer le tableau
transposed = np.transpose(A)
print("Tableau transposé :", transposed)
```

#### **Exercice :**
Considérez la grille 6x6.
1. Divisez-la en blocs 2x2.
2. Appliquez une transformation (par ex. +10).
3. Puis reconstruisez la grille.

```python
# Créer une grille 6x6
grid = np.array([[1, 2, 3, 4, 5, 6],
                 [7, 8, 9, 10, 11, 12],
                 [13, 14, 15, 16, 17, 18],
                 [19, 20, 21, 22, 23, 24],
                 [25, 26, 27, 28, 29, 30],
                 [31, 32, 33, 34, 35, 36]])
```