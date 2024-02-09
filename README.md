# Rapport TP Deep Learning
# Le problème des clients de la banque

 Chargement et inspection et nettoyages des données
On a 14 colonnes et 10k lignes de data.
On a supprimé les colonnes suivantes : RowNumber, CustomerId, Surname
Explication de quelques colonnes : 
CreditScore : c'est le pointage de crédit.
Balance : L'argent qui se trouve dans le compte bancaire.
Tenure : L'ancienneté du client.
On a besoin de transformer les valeurs en type chaine de caractere en type entier (Encodage des caractéristiques catégorielles en numérique)
Gender => F = 1, M = 0
Geography => France = 0, Spain = 1, Germany = 2

- Division les données en ensembles d'entraînement et de test.
- Utilisation de StandardScaler pour mettre à l'échelle vos données.(Standarisation)


- Utilisation le séquentiel de keras.models pour initialiser votre modèle ANN en le définissant comme une séquence de couches.

3. 



 Divisez vos données en ensembles d'entraînement et de test. 

Ajoutez la couche d'entrée et la première couche cachée en utilisant la méthode add() .



classifier.add(Dense(units = 6, kernel_initializer = 'uniform', activation = 'relu', input_dim = 11))





Utilisez Dense() pour créer une couche Dense qui est la couche de réseau neuronal profondément connectée habituelle. Il s’agit de la couche la plus courante et la plus fréquemment utilisée.


La méthode Dense prend les arguments suivants :
unités : dimensionnalité de l'espace de sortie.
activation : Fonction d'activation à utiliser. o Dans cette activité, utilisez :
relu : fonction d'activation du redresseur pour les couches cachées. ▪ fonction
sigmoïde pour la couche de sortie utilisable lorsque la sortie est binaire.



kernel_initializer : Initialiseur pour la matrice de poids du noyau.



De plus, ajoutez l'argument input_dim : dimension de la couche d'entrée, à transmettre pour la première couche cachée.


Ajoutez une deuxième couche cachée composée de 6 unités.
Ajoutez la couche de sortie avec une unité binaire. N'oubliez pas, cette fois, l'activation sigmoïde fonction doit être utilisée.



Avant de former le modèle ANN, vous devez configurer le processus d'apprentissage, qui est effectué via la méthode de compilation .


classifier.compile (optimizer = 'adam', loss = 'binary_crossentropy', metrics=['accuracy'])





compile() reçoit trois arguments : un optimiseur (utilisez 'adam'), une fonction de perte (utilisez 'binary_crossentropy') et une liste de métriques (utilisez la 'précision').
Cela signifie que votre processus de validation sera effectué à l'aide de l'optimiseur Adam qui utilise la descente de gradient stochastique pour optimiser les hyperparamètres du réseau, principalement les pondérations des caractéristiques. L' erreur est calculée en utilisant l'entropie croisée bianaire  fonction et les mesures d'évaluation utilisées dans le score de précision.


Ajustez votre modèle et appliquez la validation croisée avec une taille de lot de 10. Répétez 50 ou 100 fois (époque = 50 ou 100).


classifier.fit (X_train, y_train, batch_size = 10, époques = 50)




 Faites des prédictions.
 Évaluer le modèle à l'aide de la matrice de confusion et du rapport de classification.
 Prédire si le client avec les informations suivantes quittera la banque ou non : Géographie : France • Pointage de crédit : 600 • Sexe : Homme • Âge : 40 • Ancienneté : 3 • Solde : 60000 • Nombre de produits : 2 • Possède un crédit carte : Oui • Est membre actif : Oui • Salaire estimé : 50000
Vous pouvez utiliser des modèles Keras séquentiels dans le cadre de votre flux de travail Scikit•Learn via le wrappers trouvés dans la bibliothèque keras. Suivez les instructions données dans le notebook Python pour comprendre comment utiliser KerasClassifier à partir de keras.wrappers.scikit_learn.
