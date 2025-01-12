### 1. **Installation de l'environnement**

#### a. **Via Anaconda**
- Anaconda installe Python, Jupyter, NumPy, et d'autres bibliothèques scientifiques par défaut.
  1. Téléchargez [Anaconda](https://www.anaconda.com/products/distribution) pour leur système d'exploitation.
  2. Une fois installé, lancez "Anaconda Navigator" pour ouvrir un Jupyter Notebook directement.
  
#### b. **Via pip et environnement virtuel**
- *C'est une approche plus légère et personnalisable
- **Instructions :**
  1. Installez Python à partir de [python.org](https://www.python.org/).
  2. Créez un environnement virtuel :
     ```bash
     python -m venv env
     ```
  3. Activez l'environnement :
     - **Windows** : `env\Scripts\activate`
     - **Mac/Linux** : `source env/bin/activate`
  4. Installez Jupyter et NumPy :
     ```bash
     pip install notebook numpy
     ```
  5. Lancez Jupyter Notebook :
     ```bash
     jupyter notebook
     ```

---

### 3. **Astuce pour simplifier l'installation**
Si problèmes d'installation utilisez Google Colab :
- **Pourquoi ?** Google Colab est une plateforme en ligne où Jupyter Notebook peut être utilisé sans installation locale.
- **Instructions :**
  1. Connectez-vous à [Google Colab](https://colab.research.google.com/).
  2. Commencez un nouveau notebook.
  3. NumPy est préinstallé sur Colab, donc ils peuvent directement commencer à coder !

---

### 4. **Vérification de l'installation**
Testez le code suivant 
```python
import numpy as np

# Test NumPy
a = np.array([1, 2, 3])
print("NumPy array:", a)
```