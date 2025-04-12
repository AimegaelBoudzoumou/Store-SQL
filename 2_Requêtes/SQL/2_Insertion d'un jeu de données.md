# Insertion d'un jeu de données

Ce jeu de données peut être utilisé pour tester les code SQL pour l'extraction, la mise à jour et la suppression des données, dans ce document.

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

INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (2, 'iStorage', TO_CHAR(SYSDATE));
INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (3, 'Belkin', TO_CHAR(SYSDATE));
INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (4, 'Epson', TO_CHAR(SYSDATE));
INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (5, 'Philips', TO_CHAR(SYSDATE));
INSERT INTO marques(code_marque, nom_marque, date_creation_marque) VALUES (6, 'Samsung', TO_CHAR(SYSDATE));

SELECT * FROM marques;

/*##############################################################################################################
gammes (nom_gamme, date_creation_gamme, #nom_marque) 
###############################################################################################################*/

INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (20, 'DiskAshur', TO_CHAR(SYSDATE), 2);
INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (30, 'Accessoires GSM & SmartPhone', TO_CHAR(SYSDATE), 3);
INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (40, 'Scanners Professionnels', TO_CHAR(SYSDATE), 4);
INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (50, 'Lcd / TV', TO_CHAR(SYSDATE), 5);
INSERT INTO gammes (code_gamme, nom_gamme, date_creation_gamme, code_marque) VALUES (60, 'Galaxy Tab A', TO_CHAR(SYSDATE), 6);

SELECT * FROM gammes;

/*##############################################################################################################
categories (nom_categorie, date_creation_categorie)
###############################################################################################################*/

INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (200, 'Disque interne SSD', TO_CHAR(SYSDATE));
INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (300, 'Protection écran téléphone portable', TO_CHAR(SYSDATE));
INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (400, 'Scanner de production', TO_CHAR(SYSDATE));
INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (500, 'Moniteur 27'' - 30''', TO_CHAR(SYSDATE));
INSERT INTO categories (code_categorie, nom_categorie, date_creation_categorie) VALUES (600, 'Tablette tactile', TO_CHAR(SYSDATE));

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
INSERT INTO employes(matricule_employe, nom_employe, prenom_employe) VALUES (134867, 'Charles', 'Elise');
INSERT INTO employes(matricule_employe, nom_employe, prenom_employe) VALUES (165898, 'Makaya', 'Ngékou');
INSERT INTO employes(matricule_employe, nom_employe, prenom_employe) VALUES (134098, 'Biloundi', 'Rigobert');
INSERT INTO employes(matricule_employe, nom_employe, prenom_employe) VALUES (178698, 'Igenta', 'Carlos');

SELECT * FROM employes;

/*##############################################################################################################
produits (reference_fabricant, reference_interne, date_creation_produit, date_derniere_commande, visibilite_web, titre, designation, description_produit, quantite_globale, filtre_gamme, filtre_categorie, #nom_phase, #nom_type, #nom_categorie, #nom_gamme)
###############################################################################################################*/

-- titre sera de la forme « Fabricant_Marque - Gamme Référence_fabricant »

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'IS-DAP3-256-SSD-1000-F', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 200, 20);

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'OVA160HQ', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 300, 30);

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'B11B261401', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 400, 40);

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), '273V7QDSB/00', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 500, 50);

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'SM-X210NZAAEUB', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 600, 60);

SELECT * FROM produits;

/*##############################################################################################################
bundles (numero, date_creation_bundle) ###############################################################################################################*/

INSERT INTO bundles (numero, date_creation_bundle) VALUES (floor(dbms_random.value(500000, 599999)), TO_CHAR(SYSDATE));
INSERT INTO bundles (numero, date_creation_bundle) VALUES (floor(dbms_random.value(500000, 599999)), TO_CHAR(SYSDATE));
INSERT INTO bundles (numero, date_creation_bundle) VALUES (floor(dbms_random.value(500000, 599999)), TO_CHAR(SYSDATE));
INSERT INTO bundles (numero, date_creation_bundle) VALUES (floor(dbms_random.value(500000, 599999)), TO_CHAR(SYSDATE));

SELECT * FROM bundles;

```

<!--
/*##############################################################################################################
bundle_produits (reference_fabricant, numero)
###############################################################################################################*/

-- Ecrire une procédure PL/SQL pour créer un 'bundle_produits'
-->
