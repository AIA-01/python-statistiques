### Introduction à NumPy : les Masks

Un **mask** dans NumPy est un tableau de booléens généré en appliquant une condition logique sur un tableau. Chaque élément du mask indique si l'élément correspondant dans le tableau d'origine satisfait (True) ou non (False) la condition.

#### Exemple simple

```python
import numpy as np

# Créer un tableau NumPy
data = np.array([10, 20, 30, 40, 50])

# Générer un mask : True pour les éléments > 25
mask = data > 25
print("Mask :", mask)  # [False False  True  True  True]

# Utiliser le mask pour filtrer les données
filtered_data = data[mask]
print("Filtered Data :", filtered_data)  # [30 40 50]
```

---

### Fonctionnalités principales des masks dans NumPy

1. **Filtrage des éléments d'un tableau**

Un mask permet de sélectionner uniquement les éléments qui remplissent une condition. 

```python
# Sélectionner les valeurs inférieures ou égales à 30
filtered_data = data[data <= 30]
print(filtered_data)  # [10 20 30]
```

2. **Modification conditionnelle des données**

Vous pouvez modifier uniquement les éléments qui remplissent une condition, sans affecter les autres.

```python
# Modifier les valeurs > 25 pour qu'elles valent 0
data[mask] = 0
print(data)  # [10 20  0  0  0]
```

3. **Combinaison de conditions**

Les conditions peuvent être combinées à l'aide des opérateurs logiques :

- `&` : "ET" logique.
- `|` : "OU" logique.
- `~` : "NON" logique (inversion).

Voici un exemple d'utilisation avec une combinaison de conditions :

```python
data = np.array([10, 20, 30, 40, 50])
mask = (data > 10) & (data < 40)  # Entre 10 et 40 (exclus)
print(data[mask])  # [20 30]
```

4. **Comptage des éléments correspondant à une condition**

Vous pouvez compter combien d'éléments remplissent une condition en utilisant `np.sum(mask)`.

```python
count = np.sum(mask)
print("Count :", count)  # 2
```

5. **Opérations inverses**

L'opérateur `~` permet d'inverser un mask. Par exemple, si un mask sélectionne certains éléments, son inverse sélectionnera les autres.

```python
inverse_mask = ~mask
print(data[inverse_mask])  # [10 40 50]
```

---

### Avantages des masks dans NumPy

- **Efficacité** : Manipuler les données directement à l'aide de masks est beaucoup plus rapide que d'utiliser des boucles explicites.
- **Expressivité** : Les conditions logiques sont faciles à écrire et lisibles, ce qui rend le code plus intuitif.
- **Flexibilité** : Les masks permettent de réaliser des opérations complexes en combinant plusieurs conditions dynamiquement.

---

### Exemple complet d'utilisation des masks

```python
import numpy as np

# Créer un tableau d'exemple
data = np.array([15, 22, 8, 19, 35, 50])

# Mask : valeurs entre 10 et 30 (inclus)
mask = (data >= 10) & (data <= 30)

print("Original Data :", data)
print("Mask :", mask)  # [ True  True False  True False False]

# Appliquer le mask pour filtrer
filtered_data = data[mask]
print("Filtered Data :", filtered_data)  # [15 22 19]

# Modifier les valeurs correspondant au mask
data[mask] = -1
print("Modified Data :", data)  # [-1 -1  8 -1 35 50]
```
