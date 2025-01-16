### **Étude de Deux Ensembles de Données : Poids des Chats et des Chiens**

Dans cette étude, vous allez explorer l’utilisation du **z-score** pour comparer les poids de deux groupes d'animaux : les chats et les chiens. Vous utiliserez des ensembles de données générés aléatoirement pour ces animaux, et appliquerez les notions statistiques pour effectuer une analyse comparative.

---

#### **Objectifs :**

1. Calculer les **moyennes** et les **écarts-types** pour les deux groupes d'animaux.
2. Calculer les **z-scores** des poids des chats et des chiens dans l’échantillon.
3. Comparer le poids d’un chat et d’un chien spécifiques par rapport à la moyenne de leur groupe respectif à l’aide du **z-score**.

---

### **Données Exemple**

Vous disposez de deux ensembles de données :

- **Poids des Chats** : Moyenne = 4.0 kg, Écart-type = 0.5 kg
- **Poids des Chiens** : Moyenne = 12.0 kg, Écart-type = 1.5 kg

Les poids ont été générés suivant une loi normale, avec une troncature entre certaines valeurs. Les deux ensembles sont ajustés pour ne contenir que des poids compris entre certaines valeurs :

- **Poids des Chats** : Troncature entre 2.0 kg et 6.0 kg
- **Poids des Chiens** : Troncature entre 8.0 kg et 16.0 kg

Générez ces données à l'aide des fonctions suivantes

```python
import numpy as np
import matplotlib.pyplot as plt

# Fixer la graine pour la reproductibilité
np.random.seed(42)

# cats
cats_weights = np.random.normal(loc=4.0, scale=0.5, size=5000) 

# dogs
dogs_weights = np.random.normal(loc=12.0, scale=1.5, size=5000) 
```

---

### **Questions :**

#### 1. Calcul des Statistiques

- a. **Calculez / vérifiez  la moyenne et l'écart-type** des poids des chats.
- b. **Calculez / vérifiez la moyenne et l'écart-type** des poids des chiens.

#### 2. Calcul des Z-scores

- a. **Calculez le z-score** pour chaque poids dans l’ensemble des chats. Utilisez la formule :  
  $z = \frac{x - \mu}{\sigma}$
  où $x$ est un poids donné, $\mu$ est la moyenne et $\sigma$ est l'écart-type des chats.
  
- b. **Calculez le z-score** pour chaque poids dans l’ensemble des chiens en utilisant la même formule.

#### 3. Comparaison entre un Chat et un Chien

- a. Vous avez un chat pesant **4.2 kg** et un chien pesant **14.2 kg**. **Calculez leurs z-scores respectifs** en utilisant les statistiques des chats et des chiens calculées précédemment.

- b. **Interprétez les résultats** : Quel animal est le plus éloigné de la moyenne de son groupe ? Expliquez pourquoi.

#### 4. Ajout de Nouvelles Données

- a. Vous ajoutez un nouveau chat pesant **5.0 kg** et un chien pesant **16.0 kg** à vos ensembles de données.  
  **Calculez les z-scores** pour ces deux nouveaux animaux en utilisant les statistiques précédemment calculées.

- b. **Analysez les résultats** : Qui, parmi le chat de 5.0 kg et le chien de 16.0 kg, est le plus éloigné de la moyenne de son groupe ?

---

### **Contexte Pratique**

Les résultats obtenus peuvent être utilisés pour détecter des animaux qui ont des poids particulièrement **élevés** ou **bas** par rapport à la moyenne de leur groupe. 

