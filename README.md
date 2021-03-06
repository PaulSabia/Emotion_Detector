# Emotion_Detector

## Objectif :

Ce projet consiste à créer un détecteur d'émotions sur une image ou directement depuis une webcam. Le but étant de pouvoir détecter jusqu'à 7 émotions :

* Colère
* Dégoût
* Peur
* Joie
* Neutre
* Triste
* Surpris

## Les données :

Pour ce projet, nous avons utilisé un jeu de donnée disponible dans le dossier [dataset](./dataset) du repository. Il est composé de presque 36 000 images, déjà divisé en données de train, de test et par émotions.


## Formation et entrainement du modèle :

L'entrainement du modèle a été réalisé sur `Google Colab`, service de Google permettant d'avoir accès gratuitement à un GPU sur machine virtuelle, augmentant ainsi nos temps de traitement.

Pour ce modèle, nous nous sommes tournés vers un réseau neuronal convolutif (CNN), efficace pour la classificaion d'images : 

![](Images/CNN.PNG)

Notre modèle est composé d'une alternance de couches `Conv2D`, `BatchNormalization`, `Conv2D`, `BatchNormalization`, `MaxPooling2D`, `Dropout` puis de couches `Dense`.

* `Conv2D`, `MaxPooling2D` extraient les caractéristiques.
* `BatchNormalization` normalise les entrées
* `Dropout` abandonne de façon aléatoire certain noeuds du CNN afin d'éviter le sur-apprentissage
* `Dense` pour la classification.

Le notebook est disponible [ici](./classification_model.ipynb)

## Résultat

Au final, le modèle présente un précision de **68,8 %**. Voici la matrice de confusion : 

![](Images/confusion_matrix.PNG)

* 0 : Colère
* 1 : Dégoût
* 2 : Peur
* 3 : Joie
* 4 : Triste
* 5 : Surprise
* 6 : Neutre

Le modèle détecte plutôt bien les émotions neutre, joie, tristesse, colère et surprise mais semble plus en difficulté sur le dégoût et la peur.

## Application

Pour tester la detection avec une camera le fichier est disponible [ici](Test_Model.ipynb)

![](Images/test_images.PNG)


