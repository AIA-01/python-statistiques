### Introduction à Pandas

Pandas est une bibliothèque open-source en Python, largement utilisée pour la manipulation et l'analyse de données. Elle offre des structures de données flexibles et puissantes, principalement **Series** (tableaux 1D) et **DataFrame** (tableaux 2D), qui permettent de travailler facilement avec des données tabulaires ou étiquetées.

---

### Points clés :

1. **Importation de la bibliothèque :**
   ```python
   import pandas as pd
   ```

2. **Création d'une `Series` (1D) :**
   ```python
   data = [10, 20, 30]
   series = pd.Series(data, index=['a', 'b', 'c'])
   print(series)
   ```
   **Résultat :**
   ```
   a    10
   b    20
   c    30
   dtype: int64
   ```

3. **Création d'un `DataFrame` (2D) :**
   ```python
   data = {
       'Name': ['Alice', 'Bob', 'Charlie'],
       'Age': [25, 30, 35],
       'Score': [85, 90, 95]
   }
   df = pd.DataFrame(data)
   print(df)
   ```
   **Résultat :**
   ```
       Name  Age  Score
   0   Alice   25     85
   1     Bob   30     90
   2  Charlie   35     95
   ```

4. **Chargement de données depuis un fichier CSV :**
   ```python
   df = pd.read_csv('file.csv')
   print(df.head())  # Affiche les 5 premières lignes
   ```

5. **Opérations courantes :**
   - **Afficher les colonnes :**
     ```python
     print(df.columns)
     ```
   - **Accéder à une colonne :**
     ```python
     print(df['Name'])
     ```
   - **Filtrer les lignes :**
     ```python
     filtered = df[df['Age'] > 30]
     print(filtered)
     ```
   - **Statistiques descriptives :**
     ```python
     print(df.describe())
     ```

6. **Manipulations courantes :**
   - **Ajouter une colonne :**
     ```python
     df['Grade'] = ['A', 'B', 'A']
     ```
   - **Supprimer une colonne :**
     ```python
     df.drop('Grade', axis=1, inplace=True)
     ```
   - **Groupement :**
     ```python
     grouped = df.groupby('Grade')

     print(grouped.mean(numeric_only=True))

     # Sur une valeur spécifique de colonne double crochets == DataFrame
     grouped[['Score']].mean()
     ```
