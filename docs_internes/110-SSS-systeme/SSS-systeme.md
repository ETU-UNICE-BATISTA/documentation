# Spécifications Système


## Généralités

Ce document recense les exigences applicables au projet "Chargeur Solaire".


## Liste des exigences

| Traçabilité amont | Libellé |        Description |
|:---              |:---                                                                           |:---        |
| CDC001v1.1       | Accumulateurs : Capacité                                                      | La capacité des accus doit être comprise entre 2000 et 4000 mAh. |
| CDC001v1.1       | Accumulateurs : Gestion : Décharge excessive                                  | Le chargeur doit déconnecter la charge en cas de décharge excessive. |
| CDC001v1.1       | Accumulateurs : Nature                                                        | Le chargeur doit permettre la charge de trois à six éléments NiMh ou d'un ou deux éléments Li-Ion ou Li-Po. |
| CDC001v1.1       | Accumulateurs : Protection                                                    | La séquence et le circuit de charge doivent assurer la sécurité et une longévité maximale des accus. |
| CDC001v1.1       | Gestion de la charge : Orientation du panneau solaire en azimuth              | Le support du panneau sera motorisé sur l'axe horizontal permettant ainsi d'orienter le panneau pour obtenir un rendement maximal. |
| CDC001v1.1       | Gestion de la charge : Orientation du panneau solaire en site                 | L'orientation verticale du panneau solaire doit être manuelle. |
| CDC001v1.1       | Gestion de la charge : Orientation du panneau solaire en site : Réglage       | Un système comportant trois leds (trop bas, OK, trop haut) permettra d'assurer le bon réglage de l'axe vertical. |
| CDC001v1.1       | Interface du chargeur : Affichage des mesures                                 | Le chargeur doit afficher l'ensemble des mesures qu'il collecte. |
| CDC001v1.1       | Mesures : Exploitation : Plate-formes                                         | Les mesures transmises par le chargeur devront être affichées sur PC/tablette/téléphone. |
| CDC001v1.1       | Mesures collectées : Courant de la batterie                                   | Le chargeur doit mesurer le courant de charge/décharge de la batterie. |
| CDC001v1.1       | Mesures collectées : Courant de la charge                                     | Le chargeur doit mesurer le courant consommé par la charge. |
| CDC001v1.1       | Mesures collectées : Pourcentage de charge de la batterie                     | Le chargeur doit mesurer le pourcentage de charge de la batterie. |
| CDC001v1.1       | Mesures collectées : Puissance du signal radio reçu                           | Pour chaque transmission en provenance du chargeur, on enregistrera la puissance du signal radio reçu dans la base de données. |
| CDC001v1.1       | Mesures collectées : Stockage                                                 | Les mesures transmises par le chargeur devront être enregistrées dans une base de données. |
| CDC001v1.1       | Mesures collectées : Température ambiante                                     | Le chargeur doit mesurer la température ambiante. |
| CDC001v1.1       | Mesures collectées : Température de la batterie                               | Le chargeur doit mesurer la température de la batterie. |
| CDC001v1.1       | Mesures collectées : Tension de la batterie                                   | Le chargeur doit mesurer la tension de la batterie. |
| CDC001v1.1       | Transmission des mesures : Couche physique                                    | Le chargeur devra transmettre au travers d'un réseau sans fil les mesures qu'il a effectuées. |
| CDC001v1.1       | Transmission des mesures : Intervalle d'émission                              | Les mesures devront être transmises à intervalle régulier ou lors d'une variation importante de l'une des grandeurs. |
| CDC001v1.1       | Transmission des mesures : Paramètres                                         | Les paramètres de transmission (puissance, ....) devront être adaptés à la configuration géographique du lieu pour assurer une consommation minimale. |
| CDC001v1.1       | Transmission des mesures : Portée                                             | Le chargeur devra transmettre ses données avec une portée de plusieurs kilomètres. |
