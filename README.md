# Rapport TP Deep Learning
## Le problème des clients de la banque

### Chargement et inspection et nettoyages des données
- On a 14 colonnes et 10k lignes de data.
- On a supprimé les colonnes suivantes : RowNumber, CustomerId, Surname
- Explication de quelques colonnes : 
- CreditScore : c'est le pointage de crédit.
- Balance : L'argent qui se trouve dans le compte bancaire.
- Tenure : L'ancienneté du client.
### Encodage des caractéristiques catégorielles en numérique
On a besoin de transformer les valeurs en type chaine de caractere en type entier
- Gender => F = 1, M = 0
- Geography => France = 0, Spain = 1, Germany = 2

### Division des données en ensembles d'entraînement et de test.
``` python
from sklearn.model_selection import train_test_split

# splitting data
X_train, X_test, y_train, y_test = train_test_split(
                new_data.drop('Exited', axis=1),
                new_data['Exited'],
                test_size=0.2,
                random_state=42)
```
### Utilisation de StandardScaler pour mettre à l'échelle vos données.(Standarisation)
``` python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_train = scaler.fit_transform(X_train)
X_test = scaler.fit_transform(X_test)
```

### Préparation du modèle et entrainement


- Utilisation le séquentiel de keras.models pour initialiser le modèle ANN en le définissant comme une séquence de couches.
- Ajout de la couche d'entrée et la première couche cachée en utilisant la méthode add().
- Ajout une deuxième couche cachée composée de 6 unités.
- Ajout de la couche de sortie avec une unité binaire. L'activation sigmoïde fonction doit être utilisée.
- Ajustement du modèle et application de la validation croisée avec une taille de lot de 10. On a Répété 50 et 100 fois (époque = 50 ou 100) mais les résultats restent les memes.

### Les prédictions.
On a fait des prédictions sur les X_test qu'on a pas mis dans l'entrainement du modèle. Puis comme les résultat de la prédictions sont des réels entre 0 et 1, donc on a arrondit les résultats pour avoir 0 et 1. Enfin on a comparé les résultats obtenu du modèle avec les y_test qu'on mis de coté à partir du dataset.

La matrice de confusion :
![matrice](https://github.com/LydiaOuam/TPDP/assets/84903904/767f64b3-0d53-4028-8b26-868ad5127a45)

#### Explication de la matrice de confusion  : 
- Il y a 1564 échantillons qui ont été correctement classés comme négatifs (classe négative).
- Il y a 128 échantillons qui ont été correctement classés comme positifs (classe positive).
- Il y a 43 échantillons qui ont été incorrectement classés comme positifs alors qu'ils sont réellement négatifs (FP).
- Il y a 265 échantillons qui ont été incorrectement classés comme négatifs alors qu'ils sont réellement positifs (FN).
Notre modele n'est pas très fort pour la prediction des valeurs correctements négatifs. D'ailleur c'est ce qu'on voit dans le rapport de classification.

- Rapport de classification : 
![rapportClassif](https://github.com/LydiaOuam/TPDP/assets/84903904/4af53b5a-0054-4552-8979-61e15ab5db16)


 
 ### Prédiction pour un exemple donné : 
 - Géographie : France
 - Pointage de crédit : 600
 - Sexe : Homme
 - Âge : 40
 - Ancienneté : 3
 - Solde : 60000
 - Nombre de produits : 2
 - Possède un crédit carte : Oui
 - Est membre actif : Oui
 - Salaire estimé : 50000
   
 __Résultat__ : Le client ne quittera pas la banque
