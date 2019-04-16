# Compte-rendu de réunion groupe microcontrôleur

## Introduction

### Généralités

|--- |--- |
| Date | Vendredi 12 Avril 2019 |
| Réunion organisée par : | BLM |
| Type de réunion : | Extraordinaire |
| Animateur : | GOM |
| Secrétaire : | BLM |
| Maître du temps : | JMO |

### Participants

| Trigramme | Nom | 
|--- |--- |
| BLM | Maxime B. |
| GOM | Mathias G. |
| JMO | Jacques M. |

Excusés :

| Trigramme | Nom | Raison |
|--- |--- |--- |
| BAA | Alan B. | Travail. |
| MIK | Kévin M. | Travail. |


### Ordre du jour

| Sujet | Temps imparti | Présentateur |
|--- |--- |--- |
| Fixer le périmètre du système | 30min | |
| Fixer les interfaces du système | 1h | |
| Définir un layout normalisé pour le PCB | 15min | |
| Fixer les outils de production (design PCB, dev,...) | 15min | |


## Minutes

### Sujet 1 : Fixer le périmètre du système

#### Recencement des exigences applicables au système

| Libellé | Description |
|--- |--- |
| Gestion de la charge : Orientation du panneau solaire en site : Réglage | Un système comportant trois leds (trop bas, OK, trop haut) permettra d'assurer le bon réglage de l'axe vertical.|
| Interface du chargeur : Affichage des mesures | Le chargeur doit afficher l'ensemble des mesures qu'il collecte. |
| Mesures collectées : Courant de la batterie | Le chargeur doit mesurer le courant de charge/décharge de la batterie. |
| Mesures collectées : Courant de la charge | Le chargeur doit mesurer le courant consommé par la charge. |
| Mesures collectées : Pourcentage de charge de la batterie | Le chargeur doit mesurer le pourcentage de charge de la batterie. |
| Mesures collectées : Température ambiante | Le chargeur doit mesurer la température ambiante. |
| Mesures collectées : Température de la batterie | Le chargeur doit mesurer la température de la batterie. |
| Mesures collectées : Tension de la batterie | Le chargeur doit mesurer la tension de la batterie. |
| Transmission des mesures : Intervalle d'émission | Les mesures devront être transmises à intervalle régulier ou lors d'une variation importante de l'une des grandeurs. |
| Transmission des mesures : Paramètres | Les paramètres de transmission (puissance, ....) devront être adaptés à la configuration géographique du lieu pour assurer une consommation minimale. |


#### Définition du périmètre

Le système microcontrôleur prend en charge :
+ L'intégration d'un microcontrôleur et de ses périphériques élémentaires (quartz) ;
+ L'interface opérateur :
  + L'intégration d'un écran ;
  + L'intégration de boutons nécessaires à l'interaction avec l'opérateur.
+ L'intégration des signaux de pilotage du panneau solaire.

Le système microcontrôleur ne prend **PAS** en charge :
+ La communication radio ;
+ La gestion de batterie et l'alimentation ;
+ La régulation des tensions d'alimentation ;
+ L'alimentation en puissance du système d'orientation du panneau solaire ;
+ L'adaptation des tensions en provenance des senseurs


### Sujet 2 : Fixer les interfaces du système

__Objectif :__ Figer les différentes interfaces matérielles nécessaires pour échanger des informations avec les autres systèmes pour permettre le démarrage des études de qualification des composants.


#### Interface Système Radiocomm :

+ **Alimentation :** Signal de pilotage TTL permettant de couper l'alimentation du système "radiocommunication" lors de la mise en veille du système.
+ **Données :** Bus I2C permettant l'échange de données entre le système radiocomm et le système microcontrôleur. Le système microcontrôleur est le maître.
+ **Interruption :** Signal fourni par le système radiocommunication en cas de réception d'un message.


#### Interface interne "opérateur"

Interface avec l'écran et les boutons
+ **Données :** Bus I2C pour piloter l'écran ;
+ **Entrées TTL :** 3 à 5 GPIO en provenance des boutons.


#### Interface Système "panneau solaire"

Interface avec le système pilotant en position le panneau solaire.

Hypothèses :
+ Le pilotage de la position du panneau solaire se fait en I2C (contrôleur de moteur pas-à-pas ou autre microcontrôleur) ;
+ L'information de tension en sortie du panneau solaire et de position angulaire du moteur pas à pas est accessible via le bus I2C ;
+ L'affichage du positionnement se fait sur l'écran du système "microcontrôleur" ;
+ L'alimentation du système "panneau solaire" ne passe pas par la carte microcontrôleur ;

Interfaces à prévoir :
+ **Bus I2C :** Le système microcontrôleur est le maître.
+ **GPIO :** Prévoir en spare à minima une entrée ADC sur le microcontrôleur (mesure tension panneau), si possible 2 sorties TTL pour un éventuel pilotage "manuel".


#### Interface Système "batterie"

Hypothèses :
+ Le sous-système "batterie" prend en charge la fourniture des tensions d'alimentation stabilisées pour l'ensemble du système de gestion de la charge ("système embarqué") ;
+ Le système "batterie" fournit :
  + Le courant de la batterie ;
  + Le courant consommé par la charge ;
  + La température ambiante ;
  + La température de la batterie ;
  + La tension batterie ;
+ Les données sont accessibles soit via un bus I2C, soit via des tensions dans la gamme tolérable par le microcontrôleur.

Interfaces à prévoir :
+ **Bus I2C :** Le système microcontrôleur est le maître.
+ **GPIO :** Prévoir en spare à minima :
  + 5 x Entrées ADC sur le microcontrôleur.


#### Synthèse

Les directions sont données ici par rapport au microcontrôleur.

| - | Digital<BR>inputs (interrupts) | Digital<BR>outputs | Analog<BR>inputs | Bus I2C<BR>(**M**aster ou **S**lave) |
|:--				|:--:	|:--:	|:--:|:--:|
| Système Batterie		| -	| -	| 5	| 1xS |
| Système Panneau Solaire	| -	| 2	| 1	| 1xS |
| Système Radiocommunication	| 1	| 1	| -	| 1xS |
| Interface opérateur		| 3-5	| -	| -	| 1xS |
| **TOTAL :**			| **4-6** | **3** | **6** | **1 x M** |



### Sujet 3 : Définir un layout normalisé pour le PCB

Ajourné faute d'informations sur les autres sous-systèmes.



### Sujet 4 : Fixer les outils de production

+ Hardware :
  + Schematics / Design PCB : KiCAD
+ Software :
  + Environnement de développement : Linux
  + Compilation via Makefile
  + Utilisation de paquets standard si possible
  + Versionning : Git
+ Gestion :
  + Intégration continue : Travis CI (compilation régulière)
  + Gestion des tâches et actions : Kanban + issues sur Github.
  + Documentation :
    + Doc de conception : projet "documentation" sur Github.
    + Doc de developpement : Doxygen dans le code.



## Actions

| Identifiant Github | Désignation | Détails |
| ---|--- |--- |
| [documentation#1](https://github.com/itii-p17-projet-elec/documentation/issues/1) | Validation interfaces | Valider les interfaces avec les autres groupes. |
| | Bilan E/S | Dresser le bilan des entrées et sorties du système microcontrôleur. |
| | Identifier composants | Veille techno sur les µC et écrans utilisables (en particulier trouver des écrans I2C avec alim en 3,3V). |

