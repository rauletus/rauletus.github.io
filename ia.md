---
layout: page
title: Supervision
permalink: /ia/
---

UN RESEAU FERROVIAIRE MINIATURE POUR LA SIMULATION

Un nouveau type de détecteur ?

Présentation
------------

La détection de position du matériel repose actuellement sur de multiples solutions techniques.

La technologie peut nous permettre d'enrichir le catalogue des solutions.

## Supervision

Principe : utiliser l'intelligence artificielle

Le contrôle d'un scénario et du respect des règles peut être réalisé en observant le déroulement du jeu avec une caméra positionnée pour avoir une vue d'ensemble.
Un programme d'intelligence artificielle basé sur un réseau de neurones de type "Object Detector" (Yolo ou RetinaNet) a appris à reconnaitre les locos et les wagons présents à chaque photo avec leur position dans l'image. Un traitement relie la position des éléments sur la photo et la position physique des bâtiments.
Elle peut être positionnée en surplomb, de face ou dans l'axe des voies (ou bien en vue du dessus et en utilisant des marques sur les toitures des wagons si cela peut faciliter la reconnaissance mais cela n'est pas esthétique).

Fonctionnement :
* Caméra : une webcam capture des photos à intervalle régulier (toutes les 5 secondes)
* Normalisation image
* Inférence "Object Detector" : liste des objets détectés
* Détermination de la position des objets sur le réseau modèle (bounding boxes)
* Génération de la log horodatée des positions
* Fusion avec la log horodatée des commandes DCC capturées par JMRI
* Mise en cohérence avec l’historique *
* Calcul des trajets et manoeuvres réalisés
* Calcul du respect des contraintes
* Calcul du score
* Affichage dans JMRI (qui affiche l’horloge, gère le script aller/retour)

(*) entre deux photos, certains objets peuvent temporairement disparaitre en fonction de la reconnaissance par l’IA : il est nécessaire de considérer plusieurs cycles pour compenser.

Pour l'apprentissage du réseau de neurones, il est plus simple que la caméra soit positionnée de face pour éviter d'avoir des perspectives en 3D, dans la mesure ou le jeu de données (images d'entrainement) contient une reconnaissance en 2D vue de face avec des _bounding boxes_ étiquettées rectangulaires en 2D.

Remarque : notons que le cablage du réseau peut rester simple et le plan des voies pourrait même évoluer sans impacter le fonctionnement général. Dans une certaine mesure, cela permet de changer la structure du réseau sans impact sur la supervision et le placement de capteurs.
