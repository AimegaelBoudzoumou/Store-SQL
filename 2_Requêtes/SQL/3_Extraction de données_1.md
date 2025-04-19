# Extraction de données - SELECT

<!-- Pour chaque situation, je présente le __besoin fonctionnel__, suivi de la __requête SQL__ y relatif. -->

## 1. Afficher tous les produits
```sql
SELECT *
FROM produits;
```
## 1.bis. Affichage du produit dont la référence interne est 7874539
```sql
SELECT *
FROM produits;
WHERE reference_interne=7874539;
```

## 2. Compter le nombre de produits
```sql
SELECT COUNT(*)
FROM produits;
```

## 3. Référence fabricant vers référence interne
Récupérer la liste de __références internes__ à partir de __références fabricants__.
```sql
SELECT reference_fabricant, reference_interne
FROM produits
WHERE reference_fabricant IN ('OVA160HQ', 'B11B261401', '273V7QDSB/00', 'SM-X210NZAAEUB');
```

## 4. Rechercher les produits de marque 'Belkin'

Approche 1 : sous-requêtes impliquant 3 tables : produits, gammes et marques
```sql
/*
INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'IS-DAP3-256-SSD-1000-I', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 200, 20);

INSERT INTO produits (reference_interne, reference_fabricant, date_creation_produit, visibilite_web, quantite_globale, filtre_gamme, filtre_categorie, code_phase, code_types_de_produit, code_categorie, code_gamme) 
    VALUES (floor(dbms_random.value(7000000, 7999999)), 'IS-DAP3-256-SSD-1000-H', TO_CHAR(SYSDATE), 'non', floor(dbms_random.value(0, 500)), '0', '0', 43, 80, 200, 20);
*/

SELECT *
FROM produits
WHERE code_gamme = (
    SELECT g.code_gamme 
    FROM gammes g
    JOIN marques m on m.code_marque = g.code_marque
    WHERE m.nom_marque = 'iStorage'
);
```

Approche 2 : utiliser un CTE
```sql
with search_belkin as (
    SELECT g.code_gamme 
    FROM gammes g
    JOIN marques m on m.code_marque = g.code_marque
    WHERE m.nom_marque = 'Belkin'
)
SELECT *
FROM produits
WHERE code_gamme = (SELECT * FROM search_belkin);
```

<!-- 4-Bis. Pour une liste de "références internes" données, je souhaite récupérer la marque

Soit jointure, soit requêtes imbriquée : à définir

Soit jointure : Cf. question 6 ci-dessous -->

## 5. Afficher le nom d'une marque à partir d'une référence interne
```sql
WITH nom_marque_by_ref_interne as (
    SELECT m.code_marque
    FROM marques m JOIN gammes g ON m.code_marque = g.code_marque
    JOIN produits p ON p.code_gamme = g.code_gamme
    WHERE reference_interne = 7465831
)
   
SELECT nom_marque
FROM marques
WHERE code_marque = (SELECT code_marque FROM nom_marque_by_ref_interne);
```


## 6. A partir du full_name d'un employe donné, afficher la ou les marques dont il est 'acheteur'
```sql
-- Définir l'employée 'Elise Charles' (matricule '134867') comme acheteur des marques iStorage (code_marque : 2) et Belkin (code_marque : 3).

UPDATE marques
SET MATRICULE_EMPLOYE_ETRE_ACHETEUR = '134867'
WHERE CODE_MARQUE IN (2, 3);

-- Définir l'employée 'Ngékou Makaya' (matricule '165898') comme acheteur de la marque Philips (code_marque : 5).
UPDATE marques
SET MATRICULE_EMPLOYE_ETRE_ACHETEUR = '165898'
WHERE CODE_MARQUE = 5;

-- Afficher la ou les marques ayant pour acheteur : 'Elise Charles'
SELECT nom_marque
FROM marques
WHERE matricule_employe_etre_acheteur = (
    SELECT matricule_employe
    FROM employes
    WHERE full_name_employe = 'Elise Charles'
);
```


## 7. Affecter chef de produits

```sql

-- Affecter 'Rigobert Biloundi' comme chef_de_produit pour les marques 'iStorage' et 'Epson'

UPDATE marques
SET MATRICULE_EMPLOYE_ETRE_CHEF_DE_PRODUIT = 
    (
    	SELECT matricule_employe
		FROM employes
		WHERE full_name_employe = 'Rigobert Biloundi'
	)
WHERE code_marque IN (
    SELECT code_marque
    FROM marques
    WHERE nom_marque IN ('iStorage', 'Epson')
);

-- Affecter 'Carlos Igenta' comme chef_de_produit pour les marques 'Belkin' et 'Philips'

UPDATE marques
SET MATRICULE_EMPLOYE_ETRE_CHEF_DE_PRODUIT = 
    (
    	SELECT matricule_employe
		FROM employes
		WHERE full_name_employe = 'Rigobert Biloundi'
	)
WHERE code_marque IN (
    SELECT code_marque
    FROM marques
    WHERE nom_marque IN ('Belkin', 'Philips')
);

```

## 7.bis Afficher les produits dont un employé donné est 'chef de produit'

```sql

-- Cas de 'Rigobert Biloundi' -- utilisation de requêtes imbriquées dans le CTE

WITH cte_search_code_marque_by_full_name_employe AS (
    SELECT code_marque
    FROM marques
    WHERE MATRICULE_EMPLOYE_ETRE_CHEF_DE_PRODUIT = (
        SELECT matricule_employe
        FROM employes
        WHERE full_name_employe = 'Rigobert Biloundi'
    )  
)

SELECT * 
FROM produits 
WHERE code_gamme IN (
    SELECT code_gamme 
    FROM gammes 
    WHERE code_marque IN (SELECT * FROM cte_search_code_marque_by_full_name_employe)
);

-- Cas de 'Carlos Igenta' -- utilisation de jointure dans le CTE

WITH cte_search_code_marque_by_full_name_employe AS (
    SELECT code_marque
    FROM marques m JOIN employes e
    ON m.MATRICULE_EMPLOYE_ETRE_CHEF_DE_PRODUIT = e.matricule_employe
    WHERE m.MATRICULE_EMPLOYE_ETRE_CHEF_DE_PRODUIT = (
        SELECT matricule_employe
        FROM employes
        WHERE full_name_employe = 'Carlos Igenta'
    )  
)

SELECT * 
FROM produits 
WHERE code_gamme IN (
    SELECT code_gamme 
    FROM gammes 
    WHERE code_marque IN (SELECT * FROM cte_search_code_marque_by_full_name_employe)
);
```

## 8. Sélectionner la catégorie pour une reference interne donnée
```sql
-- Avec une jointure
SELECT nom_categorie
FROM categories c JOIN produits p
    ON p.code_categorie = c.code_categorie
WHERE reference_interne = 7699835;

-- Avec une sous-requête
SELECT nom_categorie 
FROM categories
WHERE code_categorie = (
    SELECT code_categorie FROM produits
    WHERE reference_interne = 7699835
    );
```

## 9. Rechercher les produits non visibles sur le web et dont la désignation est à NULL
```sql
SELECT reference_interne, visibilite_web, designation 
FROM produits
WHERE visibilite_web = 'non'
AND designation IS NULL;
```

## 11. Afficher les produits ayant un filtre sur la gamme

```sql
SELECT reference_interne
FROM produits
WHERE filtre_gamme = 1;
```

## 11. Récupérer les titres pour plusieurs produits
```sql
SELECT REFERENCE_INTERNE, TITRE
FROM produits
WHERE REFERENCE_INTERNE IN (7003595, 7193359);
```

## 12. Rechercher l’acheteur d’une marque donnée
```sql
-- Définir l'employée 'Elise Charles' (matricule '134867')
-- comme acheteur des marques iStorage (code_marque : 2) et Belkin (code_marque : 3).

UPDATE marques
SET MATRICULE_EMPLOYE_ETRE_ACHETEUR = '134867'
WHERE CODE_MARQUE IN (2, 3);

-- Définir l'employée 'Ngékou Makaya' (matricule '165898')
-- comme acheteur de la marque Philips (code_marque : 5).

UPDATE marques
SET MATRICULE_EMPLOYE_ETRE_ACHETEUR = '165898'
WHERE CODE_MARQUE = 5;

-- Rechercher l’acheteur d’une marque (Philips par exemple)
SELECT * 
FROM employes
WHERE MATRICULE_EMPLOYE = (
    SELECT MATRICULE_EMPLOYE_ETRE_ACHETEUR 
    FROM marques
    WHERE nom_marque = 'Philips'
    );
```

## 13. Sélectionner des produits (uniquement les réfs internes) de marque « Apple » et de gamme « iPhone 16 »

-->
```sql
/*
Ajouter des produits de marques Apple (Gammes => Catégorie)

Gamme : Mac Studio => Catégorie : PC de bureau

Gamme :	MacBook Air => Catégorie : PC Portable

Gamme :	iPhone 16 => Catégorie : Smartphone

*/
--
 
```

## 13.bis Sélectionner des produits (uniquement les réfs internes) de marque « Apple » et de categorie « PC Portable »


## 14. J’ai une liste de réfs et une gamme. Je veux savoir quelles réfs a pour gamme, la gamme en question
<!--
Select ref_interne, gamme 
from g_produits
where ref_interne IN (7513027, 7513028, 7513029, 7513030, …, 7513039)
having gamme = ‘…’ ;
-->

## 15. Récupérer la gamme pour plusieurs réfs
<!--
J’ai une liste de réf dont la gamme. Je veux savoir quelle est la gamme chaque produit de la liste

Select ref_interne, gamme 
from g_produits
where ref_interne IN (7513027, 7513028, 7513029, 7513030, …, 7513039)

Filtre
-->

## 16. Lister les filtres actifs sur une réf donnée (ou des réfs données) (penser à GROUP BY)

## 17. Supprimer les filtres sur une ou une plusieurs réfs / Supprimer les filtres pour une liste de réfs données

## 18. Mettre en place un fiche (catégorie, gamme) sur un produit

## 19. Afficher les filtres présents sur un produit
<!--
Afficher les gammes filtrées
Afficher les produits filtrés
Afficher les fabricants filtrés
Afficher les catégories filtrées
-->




