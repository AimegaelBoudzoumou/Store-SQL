# Modèle Logique de Données

Présentation du MLD

# Modèle créé le : Sat Jan 11 16:23:30 CET 2025 
produits (reference_interne, reference_fabricant, date_creation, date_derniere_commande, visibilite_web, titre, designation, description_produit, quantite_globale, filtre_gamme, filtre_categorie, #matricule, #nom_gamme, #nom_produit, #nom_phase, #nom_categorie) 
categories (nom_categorie, date_creation_categorie) 
employes (matricule, nom_employe, prenom_employe, full_name) 
bundle (numero_bundle, date_creation_bundle, #nom_phase) 
phase (nom_phase, signification) 
type_de_produits (nom_produit) 
marque (nom_marque, date_creation_marque) 
gamme (nom_gamme, date_creation_gamme, #nom_marque) 
acheteur (matricule, nom_marque, nom_gamme) 
appartenir_bundle (reference_interne, numero_bundle) 
