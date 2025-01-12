# Modèle Logique de Données

## Principe de fonctionnement du MLD

Le MLD (Modèle Logique de Données) est une couche intermédiaire entre le modèle conceptuel de données et la base de données.

Les entités et attributs du MCD [(MCD)](https://github.com/AimegaelBoudzoumou/Store-SQL/blob/main/1_Mod%C3%A9lisation/1_MCD.md) deviennent respectivement des tables et des champs dans le MLD.

Les associations ayant la cardinalité max N,N se transforment en tables.

Lorsqu'une association reliant deux éléments A et B, possède la cardinalité max 1,N (soit 1 pour A et N pour B) :

l'élément A reçoit la clé primaire de l'élément B. Cette clé primaire se transforme en clé étrangère dans A.

## MLD


produits (__reference_interne__, reference_fabricant, date_creation, date_derniere_commande, visibilite_web, titre, designation, description_produit, quantite_globale, filtre_gamme, filtre_categorie, #type_produit, #nom_categorie, #nom_gamme, #matricule_employe, #nom_phase) 

type_de_produit (__type_produit__) 

employes (__matricule_employe__, nom_employe, prenom_employe, full_name_employe) 

bundles (__numero__, date_creation_bundle, #nom_phase) 

gamme (__nom_gamme__, date_creation_gamme, #nom_marque) 

phases (__nom_phase__, signification) 

marques (__nom_marque__, date_creation_marque) 

categories (__nom_categorie__, date_creation_categorie) 

acheteurs (__matricule_employe__, __nom_gamme__, __date__) 

bundle_produits (__numero__, __reference_interne__) 
