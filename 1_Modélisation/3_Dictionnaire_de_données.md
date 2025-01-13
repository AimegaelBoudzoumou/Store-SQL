# Dictionnaire de données

Le __dictionnaire de données__ apporte des informations détaillées sur les champs des tables.

Il est question pour chaque champ de table, d'expliquer les éléments suivants:

identifiant, signification, type, longueur, nature, calcul (règle de calcul), Règle

## Exemple de l'entité/table : produits

Rappel du MLD d'un produit :

produits (reference_interne, reference_fabricant, date_creation, date_derniere_commande, visibilite_web, titre, designation, description_produit, quantite_globale, filtre_gamme, filtre_categorie, #type_produit, #nom_categorie, #nom_gamme, #matricule_employe, #nom_phase)

__Champ 1 : reference_interne__

- code : reference_interne (clé primaire de la table)
- signification : identifiant unique d'un produit, propre à notre système
- type : nombre
- longueur : 7 à 8 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur générée par le système

__Champ 2 : reference_fabricant__

- code : reference_fabricant
- signification : identifiant unique d'un produit, connu de tous (constructeur du produit, fournisseurs)
- type : chaîne de caractères
- longueur : non connu au préalable
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur générée par le constructeur du produit

__Champ 3 :date_creation__

- code : date_creation
- signification : date de création d'un produit
- type : date
- longueur : dépend du format standard du SGBD utilisé
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur générée par le SGBD (Système de Gestion de Bases de Données)

__Champ 4 : date_derniere_commande__

- code : date_derniere_commande
- signification : date la plus récente à laquelle une commande a été passée. Sera utile pour la procédure PL/SQL (qui sera exécutée chaque 6 mois) ayant pour but de "désactiver" les produits n'ayant pas fait l'objet d'une vente sur les deux mois précédents.
- type : date
- longueur : dépend du format standard du SGBD utilisé
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun 
- Règle : valeur initialement à NULL (lors de la création d'un produit). Ensuite mise à jour via un "Trigger" qui écoute la table des "ventes".

__Champ 5 : visibilite_web :__

- code : visibilite_web
- signification : indique si un produit est visible ou non visible sur le web (e-commerce)
- type : chaîne de caractère soit "oui" soit "non"
- longueur : 3 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : par défaut à "oui"

__Champ 6 : titre :__

- code : titre
- signification : titre d'un produit
- type : chaîne de caractère
- longueur : environ 50 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : aucune

__Champ 7 : designation :__

- code : designation
- signification : designation d'un produit
- type : chaîne de caractère
- longueur : environ 253 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : aucune

 __Champ 8 : description_produit :__

- code : description_produit
- signification : description marketin du produit
- type : chaîne de caractère
- longueur : environ 1000 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : aucune

 __Champ 9 : quantite_globale :__

- code : quantite_globale
- signification : quatité de produit
- type : nombre
- longueur : dépend des fournisseurs
- nature : E (pour élémentaire)
- calcul (règle de calcul) : Somme des quantités disponibles chez nos fournisseurs
- Règle : aucune

__Champ 10 : filtre_gamme :__

- code : filtre_gamme
- signification : la mise en place d'un filtre permet de restreindre les activités sur un produit
- type : nombre soit 1 (présence de filtre), soit 0 (absence de filtre)
- longueur : un caractère
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : par défaut à 0

__Champ 11 : filtre_categorie :__

- code : filtre_categorie
- signification : la mise en place d'un filtre permet de restreindre les activités sur un produit
- type : nombre soit 1 (présence de filtre), soit 0 (absence de filtre)
- longueur : un caractère
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : par défaut à 0

__Champ 12 : #type_produit :__

- code : #type_produit
- signification : type d'un produit (physique, logiciel, licence, "service et garantie")
- type : chaîne de caractères
- longueur : environ 30 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : clé étrangère dans la table "produits" et clé primaire de la table "type_de_produit"

__Champ 13 : #nom_categorie :__

- code : #nom_categorie
- signification : nom de la catégorie à laquelle appartient le produit
- type : chaîne de caractères
- longueur : environ 30 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : clé étrangère dans la table "produits" et clé primaire de la table "categories"

__Champ 14 : #nom_categorie :__

- code : #nom_gamme
- signification : nom de la gamme à laquelle appartient le produit
- type : chaîne de caractères
- longueur : environ 30 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : clé étrangère dans la table "produits" et clé primaire de la table "gamme"

__Champ 15 : #matricule_employe :__

- code : #matricule_employe
- signification : matricule du chef de produit
- type : chaîne de caractères
- longueur : environ 8 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : clé étrangère dans la table "produits" et clé primaire de la table "employes"

__Champ 16 : #nom_phase :__

- code : #nom_phase
- signification : désigne la phase du produit
- type : chaîne de caractères
- longueur : environ 30 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : par défaut à "vert" (ce qui signifie "en ligne")



