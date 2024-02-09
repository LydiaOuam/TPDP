# Rapport TP Deep Learning
## Le problème des clients de la banque

### Chargement et inspection et nettoyages des données
On a 14 colonnes et 10k lignes de data.
On a supprimé les colonnes suivantes : RowNumber, CustomerId, Surname
Explication de quelques colonnes : 
CreditScore : c'est le pointage de crédit.
Balance : L'argent qui se trouve dans le compte bancaire.
Tenure : L'ancienneté du client.
### Encodage des caractéristiques catégorielles en numérique
On a besoin de transformer les valeurs en type chaine de caractere en type entier
Gender => F = 1, M = 0
Geography => France = 0, Spain = 1, Germany = 2

### Division les données en ensembles d'entraînement et de test.
### Utilisation de StandardScaler pour mettre à l'échelle vos données.(Standarisation)

### Préparation du modèle et entrainement


- Utilisation le séquentiel de keras.models pour initialiser votre modèle ANN en le définissant comme une séquence de couches.
- Ajoutez la couche d'entrée et la première couche cachée en utilisant la méthode add() .
- Ajoutez une deuxième couche cachée composée de 6 unités.
- Ajoutez la couche de sortie avec une unité binaire. N'oubliez pas, cette fois, l'activation sigmoïde fonction doit être utilisée.



Ajustez votre modèle et appliquez la validation croisée avec une taille de lot de 10. On a Répété 50 ou 100 fois (époque = 50 ou 100) mais les résultats restent les memes.

Faites des prédictions.

 Évaluer le modèle à l'aide de la matrice de confusion et du rapport de classification.
 
 Prédire si le client avec les informations suivantes quittera la banque ou non :
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
