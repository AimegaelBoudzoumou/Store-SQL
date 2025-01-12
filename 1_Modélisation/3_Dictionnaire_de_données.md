# Dictionnaire de données

Le __dictionnaire de données__ apporte des informations détaillées sur les champs des tables.

Il est question pour chaque champ de table, d'expliquer les éléments suivants:

identifiant, signification, type, longueur, nature, calcul (règle de calcul), Règle

## Exemple de l'entité/table : produits

Rappel du MLD d'un produit :

produits (reference_interne, reference_fabricant, date_creation, date_derniere_commande, visibilite_web, titre, designation, description_produit, quantite_globale, filtre_gamme, filtre_categorie, #type_produit, #nom_categorie, #nom_gamme, #matricule_employe, #nom_phase)


__Champ 1 : reference_interne__

- code : reference_interne
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
- type : 
- longueur : 
- nature : 
- calcul (règle de calcul) : 
- Règle : 


__Champ ... :__

- code : 
- signification : 
- type : 
- longueur : 
- nature : 
- calcul (règle de calcul) : 
- Règle : 

