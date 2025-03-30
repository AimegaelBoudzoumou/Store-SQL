# Insertion d'un jeu de données

Ce jeu de données sera utilisés dans la suite de ce document (pour l'extraction, la mise à jour et la suppression des données)

```sql
/***** DELETING ALL DATAS *****/

DELETE FROM produits;
DELETE FROM phases;
DELETE FROM types_de_produit;
DELETE FROM categories;
--DELETE FROM bundles_produits;
DELETE FROM bundles;
DELETE FROM employes;
DELETE FROM gammes;
DELETE FROM marques;

/***** DELETING ALL DATAS *****/


/*##############################################################################################################
marques (nom_marque, date_creation_marque, #matricule_employe_etre_acheteur, #matricule_employe_etre_chef_de_produit) 
###############################################################################################################*/

INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (23, 'iStorage', TO_CHAR(SYSDATE));
INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (24, 'Belkin', TO_CHAR(SYSDATE));
INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (25, 'Epson', TO_CHAR(SYSDATE));
INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (26, 'Philips', TO_CHAR(SYSDATE));
INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (27, 'Samsung', TO_CHAR(SYSDATE));

SELECT * FROM marques;

/*##############################################################################################################
gammes (nom_gamme, date_creation_gamme, #nom_marque) 
###############################################################################################################*/

INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (90, 'DiskAshur', TO_CHAR(SYSDATE), 23);
INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (130, 'Accessoires GSM & SmartPhone', TO_CHAR(SYSDATE), 24);
INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (200, 'Scanners Professionnels', TO_CHAR(SYSDATE), 25);
INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (300, 'Lcd / TV', TO_CHAR(SYSDATE), 26);
INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (400, 'Galaxy Tab A', TO_CHAR(SYSDATE), 27);

SELECT * FROM gammes;

/*##############################################################################################################
categories (nom_categorie, date_creation_categorie)
###############################################################################################################*/

INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (900, 'Disque interne SSD', TO_CHAR(SYSDATE));
INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (1300, 'Protection écran téléphone portable', TO_CHAR(SYSDATE));
INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (2000, 'Scanner de production', TO_CHAR(SYSDATE));
INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (3000, 'Moniteur 27'' - 30''', TO_CHAR(SYSDATE));
INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (4000, 'Tablette tactile', TO_CHAR(SYSDATE));

SELECT * FROM categories;

/*##############################################################################################################
phases (nom_phase, signification)
###############################################################################################################*/

INSERT INTO phases (code_phase, nom_phase, signification) VALUES (43, 'A statuer', NULL);
INSERT INTO phases (code_phase, nom_phase, signification) VALUES (44, 'En ligne', NULL);
INSERT INTO phases (code_phase, nom_phase, signification) VALUES (45, 'Suspendu', NULL);
INSERT INTO phases (code_phase, nom_phase, signification) VALUES (46, 'Refusé', NULL);
INSERT INTO phases (code_phase, nom_phase, signification) VALUES (47, 'Rejeté', NULL);

SELECT * FROM phases;

/*##############################################################################################################
types_de_produit (nom_type)
###############################################################################################################*/

INSERT INTO types_de_produit(code_types_de_produit, nom_type) VALUES (80, 'Physique');
INSERT INTO types_de_produit(code_types_de_produit, nom_type) VALUES (81, 'Licence');
INSERT INTO types_de_produit(code_types_de_produit, nom_type) VALUES (82, 'Service');

SELECT * FROM types_de_produit;

/*##############################################################################################################
employes (matricule_employe, nom_employe, prenom_employe, full_name_employe)
###############################################################################################################*/

INSERT INTO employes(matricule_employe, nom_employe, prenom_employe) VALUES (139898, 'Camara', 'Moussa');
INSERT INTO employes(matricule_employe, nom_employe, prenom_employe) VALUES (134867, 'Charles', 'ELise');
INSERT INTO employes(matricule_employe, nom_employe, prenom_employe) VALUES (165898, 'Makaya', 'Ngoné');
INSERT INTO employes(matricule_employe, nom_employe, prenom_employe) VALUES (134098, 'Biloundi', 'Rigobert');
INSERT INTO employes(matricule_employe, nom_employe, prenom_employe) VALUES (178698, 'Igenta', 'Carlos');

SELECT * FROM employes;

/*##############################################################################################################
produits (reference_fabricant, reference_interne, date_creation_produit, date_derniere_commande, visibilite_web, titre, designation, description_produit, quantite_globale, filtre_gamme, filtre_categorie, #nom_phase, #nom_type, #nom_categorie, #nom_gamme)
###############################################################################################################*/

-- titre sera de la forme « Fabricant_Marque - Gamme Référence_fabricant »

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'IS-DAP3-256-SSD-1000-F', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 900, 90);

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'OVA160HQ', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 1300, 130);

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'B11B261401', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 2000, 200);

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), '273V7QDSB/00', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 3000, 300);

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'SM-X210NZAAEUB', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 4000, 400);

SELECT * FROM produits;

/*##############################################################################################################
bundles (numero, date_creation_bundle) ###############################################################################################################*/

INSERT INTO bundles (numero, date_creation_bundle) VALUES (floor(dbms_random.value(500000, 599999)), TO_CHAR(SYSDATE));
INSERT INTO bundles (numero, date_creation_bundle) VALUES (floor(dbms_random.value(500000, 599999)), TO_CHAR(SYSDATE));
INSERT INTO bundles (numero, date_creation_bundle) VALUES (floor(dbms_random.value(500000, 599999)), TO_CHAR(SYSDATE));
INSERT INTO bundles (numero, date_creation_bundle) VALUES (floor(dbms_random.value(500000, 599999)), TO_CHAR(SYSDATE));

SELECT * FROM bundles;

/*##############################################################################################################
bundle_produits (reference_fabricant, numero)
###############################################################################################################*/

-- Ecrire une procédure PL/SQL pour créer un 'bundle_produits'
```
