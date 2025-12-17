======= CLASSE "Beehive" =======
(Abeilles, Nectar, AbeillesMax, NectarMax)

Abeilles -> Nombre d'habitants de la ruche. ne peut pas dépasser AbeillesMax
Nectar -> Stock de nectar dans la ruche.
AbeillesMax -> Nombre maximum d'abeilles pouvant cohabiter.
NectarMax -> Seuil de nectar. Si Nectar >= NectarMax, alors remet nectar à zéro et Reine::Reproduction = 1
 
==============================

-=-=-=-= CLASSE "Entity" =-=-=-=-
(Position, Fenetre)

Position -> Position de l'entité dans la fenêtre.
Fenetre -> Définit dans quelle fenêtre se situe l'entité, donc dans quelle fenêtre l'afficher. BEEHIVE = 1, OUTSIDE = 2

======= CLASSE "Bee" =======
(Vie)

Vie -> Chaque abeille a de la vie, donc ce paramètre peut être initié sur la classe parent (Ex. : 6 PV, si l'abeille devient Guerrière alors, 6*2 = 12 PV. Si l'abeille devient Reine, alors 6 = 1 = 1 PV) 

------- Worker (sous-classe de "Bee") -------
(Vie, Etat, Energie, Butinage, VitesseDeplacement)

Vie -> Durée de vie, en fonction des passages à l'extérieur (Ex. : 6 PV = 6 pollinisations)
Etat -> MORT = 0, DANS_RUCHE = 1, TRAVAILLE = 2
Energie -> Quantité de pollen récupérable avant de retourner à la ruche (Ex. : 10 NR = 10 nectars)
Butinage -> Vitesse de pollinisation d'une fleur (Ex. : 2 BT = 2 secondes par fleur)
VitesseDeplacement -> Vitesse de déplacement entre deux fleurs (Ex. 5 SP = 500ms entre deux fleurs)

Lieux : Ruche, Exterieur

------- Warrior (sous-classe de "Bee") -------
(Vie*2, Etat, Force, FrequenceAttaque)

Vie -> Ses points de vie. Baisse si attaquée par un Nuisible, se régénère si Etat = SOIN.
Etat -> MORT = 0, REPOS = 1, DEFENSE = 2, SOIN = 3
Force -> Dégats envers les Nuisibles par l'abeille (Ex. : 2 STR = -2 PV au Nuisible à chaque attaque)
FrequenceAttaque -> Fréquence d'attaque. (Ex. : 5 SP = 500ms entre deux attaques)

Lieu : Ruche

------- Queen (sous-classe de "Bee") -------
(Vie = 1, Reproduction, FrequenceReproduction)

Vie -> Sert juste à savoir si elle est en vie ou non (1 = en vie, 0 = morte). Ne sert pas dans la simulation, car elle n'est pas sensé mourir
Reproduction -> Permet de savoir si la reine est en train de créer une abeille. Si Reproduction = 1 alors elle crée une abeille
FrequenceReproduction -> Vitesse de création d'une Abeille (Ex. 10 SP = 10 secondes pour créer une abeille)

Lieu : Ruche

================================


======= CLASSE "Intruder" =======
(Vie, Force, FrequenceAttaque)

Vie -> Ses points de vie. Baisse si attaquée par une Abeille Guerrière
Force -> Dégats envers les Abeilles (Ex. : 2 STR = -2 PV à l'Abeille à chaque attaque)
FrequenceAttaque -> Fréquence d'attaque. (Ex. : 9 SP = 900ms entre deux attaques)

Lieu : Ruche

=================================


======= CLASSE "Flower" =======
(Pollen, Utilisable)

Pollen -> Quantité de pollen dans la fleur pouvant être récoltée par une Ouvrière (Ex. : 2 P = 2 Pollen donné à l'Abeille)
Utilisable -> Si elle est utilisable, Utilisable = 1. Si elle a été utilisé par une abeille, alors Utilisable = 0, et se régénère au bout d'une minute.

==============================

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
