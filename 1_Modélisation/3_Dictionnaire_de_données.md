# Dictionnaire de données

Le __dictionnaire de données__ apporte des informations détaillées sur les champs des tables.

Il est question pour chaque champ de table, d'expliquer les éléments suivants:

identifiant, signification, type, longueur, nature, calcul (règle de calcul), Règle

## Exemple de l'entité/table : produits

Rappel du MLD d'un produit :

produits (reference_interne, reference_fabricant, date_creation, date_derniere_commande, visibilite_web, titre, designation, description_produit, quantite_globale, filtre_gamme, filtre_categorie, #type_produit, #nom_categorie, #nom_gamme, #matricule_employe, #nom_phase)

__Champ 1 : reference_fabricant__

- code : reference_fabricant (clé primaire de la table)
- signification : identifiant unique d'un produit, connu de tous (constructeur du produit, fournisseurs)
- type : chaîne de caractères
- longueur : non connu au préalable
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur fournie par le constructeur du produit

__Champ 2 : reference_interne__

- code : reference_interne
- signification : identifiant unique d'un produit, propre à notre système
- type : nombre
- longueur : 7 à 8 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur générée de façon aléatoire par le SGBD (système de gestion de bases de données)
  
__Champ 3 : date_creation__

- code : date_creation
- signification : date de création d'un produit
- type : date
- longueur : dépend du format standard du SGBD utilisé
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur générée automatiquement par le SGBD (Système de Gestion de Bases de Données)

__Champ 4 : date_derniere_commande__

- code : date_derniere_commande
- signification : date la plus récente à laquelle une commande a été passée sur un produit. Sera utile par la Procédure PL/SQL (qui sera exécutée chaque 6 mois) ayant pour but de "désactiver" les produits n'ayant pas fait l'objet d'une vente sur les deux mois précédents.
- type : date
- longueur : dépend du format standard du SGBD utilisé
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun 
- Règle : valeur initialement à NULL (lors de la création d'un produit). Ensuite mise à jour via un "Trigger" qui écoute la table des "ventes".

__Champ 5 : visibilite_web__

- code : visibilite_web
- signification : indique si un produit est visible ou non sur le web (e-commerce)
- type : chaîne de caractère type 'CHAR' ou 'VARCHAR', soit "1" (pour visible sur le web), soit "0" (pour non visible sur le web)
- longueur : 1 caractère
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur initialement (lors de la création d'un produit) à "0" (pour 'non visble' sur web)

__Champ 6 : titre__

- code : titre
- signification : titre d'un produit
- type : chaîne de caractère
- longueur : environ 50 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur générée par le système (SGBD), selon le format : "Nom du constructeur/Fabricant/Marque - Nom Gamme Référence_Fabricant". Le nom de la marque est déterminée grâce au nom de la gamme

__Champ 7 : designation__

- code : designation
- signification : designation d'un produit
- type : chaîne de caractère
- longueur : environ 253 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur initialement à NULL (lors de la création d'un produit)

 __Champ 8 : description_produit__

- code : description_produit
- signification : description marketin du produit
- type : chaîne de caractère
- longueur : environ 1000 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur initialement à NULL (lors de la création d'un produit)

 __Champ 9 : quantite_globale__

- code : quantite_globale
- signification : quatité de produit
- type : nombre
- longueur : dépend des quantités disponibles chez les fournisseurs
- nature : E (pour élémentaire)
- calcul (règle de calcul) : Somme des quantités disponibles chez nos fournisseurs
- Règle : en réalité : dépend des quantités disponibles chez les fournisseurs. Pour cette conception : valeur numérique générée aléatoirement

__Champ 10 : filtre_gamme__

- code : filtre_gamme
- signification : la mise en place d'un filtre permet de restreindre les activités sur un produit
- type : chaîne de caractère type 'CHAR' ou 'VARCHAR', soit "1" (pour présence d'un filtre gamme), soit "0" (pour absence d'un filtre gamme)
- longueur : un caractère
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : par défaut à "0"

__Champ 11 : filtre_categorie__

- code : filtre_categorie
- signification : la mise en place d'un filtre permet de restreindre les activités sur un produit
- type : chaîne de caractère type 'CHAR' ou 'VARCHAR', soit "1" (pour présence d'un filtre categorie), soit "0" (pour absence d'un filtre categorie)
- longueur : un caractère
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : par défaut à "0"

__Champ 16 : #nom_phase__

- code : #nom_phase
- signification : désigne la phase du produit
- type : chaîne de caractères
- longueur : environ 30 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : par défaut à "gris" ("en attente"), clé étrangère dans la table "produits" et clé primaire de la table "phase"

__Champ 12 : #type_type__

- code : #type_produit
- signification : type d'un produit (physique, logiciel, licence, "service et garantie", etc.)
- type : chaîne de caractères
- longueur : environ 30 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur renseigné manuellement à la création d'un produit. Clé étrangère dans la table "produits" et clé primaire de la table "types_de_produit"

__Champ 13 : #nom_categorie__

- code : #nom_categorie
- signification : nom de la catégorie à laquelle appartient le produit
- type : chaîne de caractères
- longueur : environ 30 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur renseigné manuellement à la création d'un produit.. Clé étrangère dans la table "produits" et clé primaire de la table "categories"

__Champ 14 : #nom_gamme__

- code : #nom_gamme
- signification : nom de la gamme à laquelle appartient le produit
- type : chaîne de caractères
- longueur : environ 30 caractères
- nature : E (pour élémentaire)
- calcul (règle de calcul) : aucun
- Règle : valeur renseigné manuellement à la création d'un produit. Clé étrangère dans la table "produits" et clé primaire de la table "gammes"
