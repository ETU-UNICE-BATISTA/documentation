## Description

Ce signal permet de faire rentrer/sortir d'hibernation le système Radiocomm. Il pourra éventuellement être utilisé pour piloter l'alimentation du système Radiocomm si ce dernier le permet.

## Interface matérielle

TODO : Via bus d'interconnexion.


## Description du signal

Le signal est de type logique **(tension à définir ultérieurement en fonction des disponibilités)**.

+ Un état haut du signal indique au système Radiocommunication qu'il doit s'apprêter à dialoguer avec le système Microcontrôleur.
+ Un état bas du signal indique au système Radiocommunication qu'il peut passer en mode faible consommation.



## Considérations dynamiques

Le système microcontrôleur pourra attendre durant un certain délai entre le passage du signal à l'état haut et la tentative de communication avec le système Radiocommunication.
