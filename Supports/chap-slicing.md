### **Cours : Le slicing en Python**

Le **slicing** (ou découpage) est une technique puissante en Python qui permet de travailler facilement avec des **sous-parties** de séquences, comme les listes, les chaînes de caractères, ou les tuples.

---

### **1. Syntaxe du slicing**

La syntaxe générale pour le slicing est :  
```python
sequence[start:stop:step]
```

#### **Les paramètres :**
1. **`start`** : L'indice où commence le slicing (inclus).
   - Par défaut : 0.
2. **`stop`** : L'indice où le slicing s'arrête (exclu).
   - Par défaut : la fin de la séquence.
3. **`step`** : Le pas, c'est-à-dire combien d'éléments sauter à chaque itération.
   - Par défaut : 1.

---

### **2. Exemples de base**
#### Exemple avec une liste :
```python
# Liste de base
my_list = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Slicing basique
print(my_list[2:7])  # [2, 3, 4, 5, 6]

# Slicing avec un pas
print(my_list[1:8:2])  # [1, 3, 5, 7]

# Slicing sans `start` ni `stop`
print(my_list[::2])  # [0, 2, 4, 6, 8]
```

#### Exemple avec une chaîne de caractères :
```python
# Chaîne de base
my_string = "Python slicing"

# Extraire "Python"
print(my_string[:6])  # 'Python'

# Extraire "slicing"
print(my_string[7:])  # 'slicing'

# Extraire avec un pas
print(my_string[::2])  # 'Pto lcn'
```

---

### **3. Indices négatifs**

Python permet d'utiliser des indices **négatifs** pour compter à partir de la fin de la séquence.  
- `-1` correspond au dernier élément.
- `-2` correspond à l'avant-dernier, etc.

#### Exemples :
```python
my_list = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Accéder aux 3 derniers éléments
print(my_list[-3:])  # [7, 8, 9]

# Accéder à tous les éléments sauf les 3 derniers
print(my_list[:-3])  # [0, 1, 2, 3, 4, 5, 6]

# Renverser une liste ou une chaîne
print(my_list[::-1])  # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]

# Chaîne de caractères inversée
my_string = "Python slicing"
print(my_string[::-1])  # 'gnicils nohtyP'
```

---

### **4. Cas particuliers**

- **Omettre `start` ou `stop`** :
  - `[:stop]` : Découpe depuis le début jusqu'à `stop`.
  - `[start:]` : Découpe depuis `start` jusqu'à la fin.
  - `[:]` : Une copie complète de la séquence.

#### Exemple :
```python
my_list = [0, 1, 2, 3, 4, 5]
print(my_list[:3])  # [0, 1, 2]
print(my_list[3:])  # [3, 4, 5]
print(my_list[:])   # [0, 1, 2, 3, 4, 5] (copie de la liste)
```

- **Slicing avec un pas négatif** :
  Permet de parcourir une séquence dans le sens inverse.

#### Exemple :
```python
my_list = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(my_list[7:2:-1])  # [7, 6, 5, 4, 3]
```

---

### **5. Applications courantes du slicing**

1. **Extraire une partie d'une séquence** :
   - Par exemple, sélectionner les trois premiers ou derniers éléments.

2. **Inverser une séquence** :
   - Utiliser `[::-1]` pour inverser rapidement une liste ou une chaîne.

3. **Copier une séquence** :
   - `[:]` est une méthode rapide pour créer une copie d'une liste.

4. **Extraire un sous-ensemble périodique** :
   - Utiliser `step` pour sélectionner un élément sur deux, trois, etc.

---

### **6. Erreurs fréquentes**
1. **Indices hors limites** :
   - Python gère automatiquement les indices hors limites dans le slicing, ce qui évite les erreurs.
   - Exemple :
     ```python
     my_list = [0, 1, 2, 3, 4]
     print(my_list[10:15])  # []
     ```
2. **Modifier une séquence immuable** :
   - Les chaînes et les tuples ne peuvent pas être modifiés directement. Le slicing peut être utilisé pour créer une nouvelle séquence, mais pas pour modifier l'original.

