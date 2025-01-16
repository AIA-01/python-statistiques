# TP Loi Normale

### **Exercice : Illustration du Théorème Central Limite avec Python**

Une entreprise souhaite analyser la moyenne des scores obtenus lors de lancers de dés pour différents groupes de joueurs. L'objectif est de comparer la variabilité des moyennes des scores entre des groupes de petite taille (5 joueurs) et des groupes plus grands (30 joueurs).

1. Générer une **population** représentant les scores des lancers de dés (1 à 6) pour 100 000 lancers.
2. Prélever des échantillons de deux tailles différentes :
   - Petits groupes : taille 5.
   - Grands groupes : taille 30.
3. Calculer les **moyennes** pour chaque groupe sur un total de 1 000 échantillons.
4. Visualiser les distributions des moyennes des échantillons.

---

### **Étapes à réaliser**

1. **Générer la population :**
   - Simulez une population de 100 000 lancers de dés en utilisant une distribution uniforme entre 1 et 6.
   - Utilisez `numpy.random.randint` pour créer cette population.

2. **Fonction de calcul des moyennes des échantillons :**
   - Implémentez une fonction `sample_means` qui :
     - Prend comme arguments : la population, la taille des échantillons, et le nombre d'échantillons à prélever.
     - Retourne une liste contenant les moyennes de chaque échantillon.

3. **Calculer les moyennes :**
   - Utilisez la fonction `sample_means` pour :
     - Calculer 1 000 moyennes pour des échantillons de taille 5.
     - Calculer 1 000 moyennes pour des échantillons de taille 30.

4. **Visualiser les résultats :**
   - Affichez deux histogrammes :
     - Un pour les moyennes des petits échantillons.
     - Un pour les moyennes des grands échantillons.
   - Utilisez `matplotlib` ou `seaborn` pour tracer les histogrammes.

---

### **Critères de validation**
1. Les distributions des moyennes pour $n=5$ et $n=30$ doivent être affichées sur des histogrammes distincts.
2. Vous devez observer que :
   - Les moyennes des petits échantillons ont une variabilité plus élevée (distribution plus large).
   - Les moyennes des grands échantillons sont concentrées autour de la moyenne réelle (distribution plus étroite).

---

### **Indications**
- La fonction `np.random.choice` peut être utile pour prélever des échantillons dans la population.
- La visualisation peut être améliorée avec `seaborn.histplot` pour une densité plus lisse.
- N’oubliez pas d’ajouter des titres, labels et légendes pour rendre vos graphiques lisibles.
- Utilisez ce code pour subdivier l'espace pour créer deux histogramme côte à côte `plt.subplot(1, 2, 1)` `plt.subplot(1, 2, 2)`
