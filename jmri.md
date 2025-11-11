---
layout: single
title: "MODELISME FERROVIAIRE ET SIMULATION"
permalink: /jmri/
excerpt: "JMRI : Java Model Railroad Interface"
header:
    overlay_image: /assets/images/headerimage.jpeg
    image_description: "G1000"
    caption: "Photo Rauletus"
toc: false
toc_label: "Technologies"
toc_sticky: true
author_profile: false
read_time: true
sidebar:
    nav: "mainleft"
---

## Logiciel de pilotage de réseau ferroviaire

J'utilise le logiciel open source **JMRI (Java Model Railroad Interface)**.

Globalement, JMRI permet la gestion complète d'un réseau de trains miniatures depuis la programmation des décodeurs DCC jusqu'au pilotage des itinéraires, en passant par les cantons, les signaux, les aiguillages, etc.

J'utilise JMRI avec la configuration suivante :
* ordinateur standard (PC ou Mac) :
    * connecté à la carte Arduino Mega 2560 avec un cable USB (5V et données)
    * connecté au réseau local Wifi
* logiciel JMRI DecoderPro ou PanelPro
* pour la commande mobile de type "walk-around" en Wifi :
    * serveur JMRI WiThrottle
    * application mobile open source Engine Driver pour Android
    * application mobile WiThrottleLite pour iOS 

Des capteurs tels que des ILS ou des détecteurs de présence par consommation de courant peuvent être reliés à une carte Arduino (j'utilise des détecteurs 5556 de [Stock87](https://www.stock87.fr)). Cette carte Arduino peut être la même que celle qui supporte le programme DCC-EX EX-CommandStation car cette centrale de commande intègre la capacité de gérer des capteurs (sensors).
Pour des réseaux qui le nécessitent, la librairie arduinoCMRI permet de réaliser un noeud C/MRI SMINI avec une carte Arduino dédiée.
Reliée au PC avec un cable USB, JMRI peut ainsi réagir à des changements d'état de boutons et détecteurs et peut comme de nombreux logiciels de cette catégorie actionner par exemple des LED, des signaux lumineux et des moteurs d'aiguillage.
