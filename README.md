# Plan de cours

## Python Statistiques 

<img src="./images/stat.png" width="200" />

1. 🐍  Numpy 
   1. Array [array](./Supports/chap-array-maths.md)
   2. 🏅 Array manipulation [Array](./Supports/chap-manipulation-array.md)
   3. Mask [mask](./Supports/chap-numpy-mask.md)

2. Pandas
   1. Pandas starter [pandas starter](./Supports/chap-pandas-starter.md)
   2. Pandas introduction [pandas intro](./Supports/chap-pandas-introduction.md)
   3. Pandas Pivot [pandas pivot](./Supports/chap-pandas-pivot.md)
3. Matplotlib [matplotlib](./Supports/chap-graphique.md)
   1. Complément [matplotlib complement](./Supports/chap-graphique-complements.md)

4. Statistiques descriptives
   1. z-score [z-score](./Supports/chap-zscore.md)
      1. TP z-score (Poids des Chats et des Chiens) [z-score tp](./Supports/tp-z-score.md)
   2. Loi Normale et TCL [loi normale](./Supports/chap-loi-normale-introduction.md)
   
5. Complément en Python
   1. slicing [slicing](./Supports/chap-slicing.md)
---

## QCM


## Complément de cours

   
## Juyter 

- [jupyter](https://jupyter.org/)

## 🐳 Docker avec Jupyter 

```python
docker run -it --rm -p 10000:8888 -v "${PWD}/work":/home/jovyan/work quay.io/jupyter/datascience-notebook:2024-04-29
```
