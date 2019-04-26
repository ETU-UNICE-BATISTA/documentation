# Interface S. Batterie / S. Microcontrôleur : Alimentation

## Description

Cette interface permet d'alimenter le système "microcontrôleur" et le
sous-système "IHM" à partir de sources de tensions régulées fournies par
le système "gestion batterie".



## Description du bus

Ce bus contient les signaux suivants :

| Identifiant      | Désignation     | Description          |
| :---             | :---:           | :---                 |
|                  | 0V / GND        | Masse/tension de référence pour le système. |
|                  | +5Vcc           | Tension stabilisée à +5Vcc. |

__Nota :__ Il sera peut-être nécessaire d'ajouter une ligne +3,3Vcc en remplacement ou en supplément de la ligne +5Vcc.



## Considérations dynamiques

Les systèmes alimentés au travers de cette interface s'efforceront de limiter
leur consommation de courant.

La consommation pic devra se limiter à moins de 500mA (estimation).



## Interface matérielle

**TODO** : ADU
