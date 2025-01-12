## **Introduction aux Statistiques avec NumPy**

### **1. Résumer les données : Summarizing Data**

#### **📚 Introduction :**
Pour analyser des données, il est courant de calculer des statistiques descriptives comme la somme, la moyenne ou la médiane. NumPy facilite ces calculs grâce à des fonctions intégrées.

#### **Exemple : Calculer la somme et la moyenne**
```python
import numpy as np

# Exemple de données de ventes
sales = np.array([200, 300, 250, 400, 350])

# Somme totale des ventes
total_sales = np.sum(sales)
print("Total des ventes :", total_sales)

# Moyenne des ventes
average_sales = np.mean(sales)
print("Moyenne des ventes :", average_sales)

# Médiane des ventes
median_sales = np.median(sales)
print("Médiane des ventes :", median_sales)
```

---

### **2. Totaux des ventes : Sales Totals**

#### **📚 Introduction :**
Additionner les totaux dans des tableaux multidimensionnels permet d'analyser les performances globales.

#### **Exemple :**
```python
# Tableau des ventes par mois pour 3 régions
sales = np.array([[200, 300, 250],  # Région 1
                  [400, 350, 300],  # Région 2
                  [450, 500, 550]]) # Région 3

# Totaux des ventes pour chaque région (somme sur les colonnes)
# axis=1 signifie que nous additionnons les éléments sur l'axe horizontal (par ligne)
totals_per_region = np.sum(sales, axis=1)
print("Totaux par région (somme par ligne) :", totals_per_region)

# Totaux des ventes par mois (somme sur les lignes)
# axis=0 signifie que nous additionnons les éléments sur l'axe vertical (par colonne)
totals_per_month = np.sum(sales, axis=0)
print("Totaux par mois (somme par colonne) :", totals_per_month)
```

---

### **3. Représenter la moyenne : Plotting Averages**

#### **📚 Introduction :**
Visualiser les moyennes permet de mieux comprendre les données.

#### **📊 Exemple avec Matplotlib :**
```python
import matplotlib.pyplot as plt

# Moyenne des ventes par mois
average_per_month = np.mean(sales, axis=0)

# Tracer les moyennes
plt.bar(["Janvier", "Février", "Mars"], average_per_month, color="skyblue")
plt.title("Moyenne des ventes par mois")
plt.ylabel("Ventes moyennes")
plt.show()
```

---

### **4. Ventes cumulées : Cumulative Sales**

#### **📚 Introduction :**
Les ventes cumulées montrent la progression au fil du temps.

#### **Exemple :**
```python
# Cumul des ventes d'une région
cumulative_sales = np.cumsum(sales[0])
print("Ventes cumulées :", cumulative_sales)

# Tracer les ventes cumulées
plt.plot(cumulative_sales, marker='o', color="green")
plt.title("Ventes cumulées")
plt.ylabel("Ventes")
plt.xlabel("Temps")
plt.show()
```

---

### **5. Opérations vectorisées : Vectorized Operations**

#### **Introduction :**

>[!IMPORTANT]
>Les opérations vectorisées permettent de manipuler des données sans utiliser de boucles explicites, ce qui rend le code plus rapide et concis.

#### **Exemple : Ajouter 10% de taxe**
```python
# Ajouter 10% de taxe aux ventes
sales_with_tax = sales * 1.10
print("Ventes avec taxe :", sales_with_tax)
```

---

### **6. Calculs de taxes : Tax Calculations**

#### **Exemple : Calcul d'une taxe variable**
```python
import numpy as np

# Tableau des ventes par mois pour 3 régions
sales = np.array([[200, 300, 250],  
                  [400, 350, 300],  
                  [450, 500, 550]])  

# Définir les taux de taxes pour chaque région
tax_rates = np.array([0.08, 0.10, 0.12])  # Taux de taxe : 8% pour région 1, 10% pour région 2, 12% pour région 3

# Appliquer les taux de taxes à chaque région
# Étendre (broadcasting) tax_rates pour qu'il s'applique correctement à chaque ligne du tableau `sales`.
#           - `[:, None]` transforme tax_rates de forme (3,) à (3, 1) pour une compatibilité avec `sales`.
# Étape 3 : Multiplier les ventes par les taux ajustés (ex. région 1 : 200 * 1.08, 300 * 1.08, etc.).
sales_after_taxes = sales * (1 + tax_rates[:, None])

# Afficher les ventes après application des taxes
print("Ventes après taxes :", sales_after_taxes)
```

---

### **7. Projection des ventes : Projecting Sales**

#### **Exemple :**
Projeter une augmentation de 5% pour chaque mois.
```python
growth_factor = 1.05
projected_sales = sales * growth_factor
print("Ventes projetées :", projected_sales)
```

---

### **8. Broadcasting**

#### **Introduction :**
Le **broadcasting** est une technique utilisée par NumPy pour effectuer des calculs entre arrays de tailles différentes.

#### **Exemple : Broadcasting Across Columns**
Ajouter une prime fixe de 50 pour chaque région.
```python
bonus = 50
sales_with_bonus = sales + bonus
print("Ventes avec bonus :", sales_with_bonus)
```

#### **Exemple : Broadcasting Across Rows**
Ajouter un bonus spécifique pour chaque mois.
```python
monthly_bonus = np.array([10, 20, 30])
sales_with_monthly_bonus = sales + monthly_bonus
print("Ventes avec bonus mensuel :", sales_with_monthly_bonus)
```

- Question : Ajouter les bonus pour chaque région 

```python
sales + monthly_bonus[:, None]
```

---

### **Exercices :**

Pour les exercices suivants, utilisez la méthode `plot` de `matplotlib.pyplot` : 

```python
import matplotlib.pyplot as plt

# ... définissez data

plt.plot(data, marker='o')
plt.title("Ventes cumulées")
plt.xlabel("Mois")
plt.ylabel("Ventes cumulées")
plt.show()
```

1. **Résumé des données :**
   - Créez un array de ventes aléatoires pour 12 mois et calculez la somme, la moyenne et la médiane. 📊
   - Affichez un graphique des ventes cumulées.

Remarques : utilisez la méthode `np.random.randint` pour générer des valeurs aléatoires.

2. **Calculs de taxes :**
   - Appliquez des taux de taxes différents pour chaque mois et calculez les totaux après taxes. 💸

Remarques : utilisez la méthode `np.random.uniform(low, high, size)` qui génère un tableau de nombres aléatoires suivant une distribution uniforme.

3. **Broadcasting :**
   - Ajoutez un bonus fixe pour chaque région et chaque mois.
   - Multipliez les ventes par un facteur qui augmente chaque mois (ex. 1.05, 1.10, 1.15, ...). 🚀

Remarques : pour ajouter un facteur qui augmente, utilisez la méthode `np.linspace` pour créer un tableau de facteurs de croissance.
