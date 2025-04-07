# Extraction de données - SELECT

<!-- Pour chaque situation, je présente le __besoin fonctionnel__, suivi de la __requête SQL__ y relatif. -->

## 1. Afficher tous les produits
```sql
SELECT *
FROM produits;
```
## 1.bis. Affichage du produit dont la référence interne est 7874539
```sql
--SELECT *
--FROM produits;
--WHERE reference_interne=7874539;
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


## 6. Pour un employé donné, afficher la ou les marques dont il est 'acheteur'
<!--
Astuce : pensez à utiliser la table "Gamme" dans notre requête SQL; et à une éventuelle double jointure entre :

Employe et Gamme (sur Employe.matricule = Gamme.matricule)

Gamme et Marque (sur Gamme.nom_marque = Marque.nom_marque)
-->

## 7. Afficher les produits dont une employé donné est 'chef de produit'

## 8. Sélectionner la catégorie pour une reference interne donnée

## 9. Rechercher les produits non visibles sur le web et dont la désignation est à NULL
<!--
```sql
DROP TABLE gproduits;

CREATE TABLE gproduits (
    reference_interne int,
    visibilite_web int,
    designation varchar2(50)
);

INSERT INTO produits VALUES (74554245, 0, NULL);
INSERT INTO produits VALUES (72151245, 0, NULL);
INSERT INTO produits VALUES (74551254, 0, 'Clé USB');
INSERT INTO produits VALUES (70124558, 0, 'Clavier filaire');
INSERT INTO produits VALUES (74124545, 0, NULL);
INSERT INTO produits VALUES (74002159, 0, NULL);
INSERT INTO produits VALUES (75989459, 1, 'Etui téléphone');
INSERT INTO produits VALUES (74501285, 0, 'Sac PC 17"');

SELECT reference_interne
FROM gproduits
WHERE visibilite_web = 0
AND designation IS NULL;
```
-->
## 10. 

## 11. Récupérer plusieurs titres
<!--
```sql
DROP TABLE gproduits;

CREATE TABLE gproduits (
    reference_interne int,
    visibilite_web int,
    designation varchar2(50)
);

INSERT INTO gproduits VALUES (74554245, 0, NULL);
INSERT INTO gproduits VALUES (72151245, 0, NULL);
INSERT INTO gproduits VALUES (74551254, 0, 'Clé USB');
INSERT INTO gproduits VALUES (70124558, 0, 'Clavier filaire');
INSERT INTO gproduits VALUES (74124545, 0, NULL);
INSERT INTO gproduits VALUES (74002159, 0, NULL);
INSERT INTO gproduits VALUES (75989459, 1, 'Etui téléphone');
INSERT INTO gproduits VALUES (74501285, 0, 'Sac PC 17"');

SELECT designation
FROM gproduits
WHERE reference_interne IN (74551254, 74124545, 75989459, 74501285);
```
Ou bien avec PL/SQL : 
Sauvegarder les titres pour plusieurs produits (réfs)
Piste : script Linux/Unix qui crée un « fichier fic1 », lance un script PL/SQL (recevant en argument le « fichier fic1 » ou tout simplement utilisant en son sein le « fichier fic1 »)
-->

## 12. Rechercher l’acheteur d’une marque et d’une gamme donnée

## 13. Sélectionner des produits (uniquement les réfs internes) de marque « Apple » et de catégories « iPhone 16 »
<!--
# Gamme
-->

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

## 19 Bis. Supprimer certains filtres pour une liste de réfs données - pensez à PL/SQL

## 20. Récupérer les titres actuellement en place, pour une liste de réf donnée

## 21. Récupérer la marque d’un produit. Penser à la jointure multique (entre produit, gamme, marque)

## 22. Besoin métier / situation : parmi plusieurs réf traitées, j’ai oublié d’intégrer du contenu pour un réf. sauf que je ne sais plus laquelle.
<!--
Solution fonctionnelle : 
Sur une liste de refs, sélectionner celle dont le contenu_marketing (description_produit) est à NULL
Select ref_interne from g_produits where ref_interne IN (XXXXX, …) and description_produit IS NULL ;
-->

## 23. J’ai une liste de réf fabricant dont je veux récupérer les réfs internes correspondantes

## 24. Dans une liste de réf, déterminer celles(s) qui n’est pas en ligne

# Bundle

## 25. Pour une liste de Bundle donnée : récupérer les produits constituant chaque Bundle (faire un regroupe by numéro de Bundle)

## 26. Pour une liste de réfs donnée : déterminer cettes faisant partie d'un quelconque

## 27. Quelles sont les réfs Canon qui sont existantes chez nous

## 28. Rechercher les produits de telle gamme ayant l'expression "jusqu'à" dans leur désignation et corriger le cas échéant

## 29. Afficher le full_name de l’acheteur d’une marque donnée

## 30. Vérifier qu’il n’existe pas de référence_interne en doublon.
<!--
Pensez à ROW_NUM pour supprimer les doublons (Cf. tutorial de Data Cleaning de Data Analyst BootCamp ».

Select reference_interne from … where row_num > 2 ;

Ensuite

Changer les référence_interne en question.

Ce besoin métier n'aurait du sens que si la réference_fabricant était clé primaire de la table "produits". La référence interne étant générée automatiquement, il aurait été important de vérifier régulièrement que la référence n'est pas présente plus d'une fois dans la base de données.
-->

## 31. Afficher les produits dont certains critères sont incorrects. Ex : absence d’images, désignation ayant plus de n mots non français.

## 35. Ecrire un script SQL qui, pour chaque réf : recherche le chef de produit et l'acheteur. Et regroupe les résultats par chef de produit.
<!-- On a une liste de produits n'ayant pas de visuel (sur le site e-commerce). Nous souhaitons demandez au Chef de produit et Acheteur de nous fournir des visuels.-->

## 36. Qui (Chef de produit, achéteur) gère telle marque ?

## 37. Un produit contient l’erreur de clavier : R.-U. au lieu de Français. Rechercher dans la base s’il existe des produits ayant la même erreur.

```sql
Select référence_interne, designation
From produits
Where gamme = 'Workstation Z' and categorie = 'Station de travail fixe' and designation LIKE '%R.-U. %'
-- OU
Select reference_interne, designation
From produits
Where exists (
Select * from produits where gamme = 'Workstation Z' and categorie = 'Station de travail fixe' and designation LIKE '%R.-U. %'
)
```

## 38. Sauvegarder des désignations actuelles pour certaines réfs - à faire une fois en fin de journée
```sql
SELECT reference_fabricant, description_produit
FROM produits
WHERE reference_interne IN (XXXXXXX, XXXXXXX, XXXXXXX, XXXXXXX, XXXXXXX, XXXXXXX);
```
<!--
Note : 
- copier/coller le résultat dans un fichier Excel ou CSV.
- sous Python : faire une concaténation des fichiers sauvegardées sur le mois
- exporter le fichier unique
- écrire une fonction Python qui parcourir plusieurs fichiers et qui, sur la base d'une réf interne, recherche l'ancienne désignation correcpondante.
-->

<!--
## Un peu complexe ...

PL/SQL
Historique : 
Après un chargement en masse, je me rends qu’il y a des désignations qui n’ont pas été mises à jour. Dans mes nouvelles désignations souhaitées, le premier mot devrait être « Canon ». Mais il y a des réfs dont le premier mot n’est pas « Canon ».

Besoin métier :
On a une liste de références. On aimerait savoir quelle désignation ne commence pas par « Canon ». 

Solution fonctionnelle : 
Pour chaque réf, on récupère la désignation. Si le premier mot de la désignation n’est pas Canon, on récupère la réf.
2978365	Canon CLI-571Y XL - 11 ml - haut rendement - jaune - original - réservoir d'encre - pour PIXMA TS5051, TS5053, TS5055, TS6050, TS6051, TS6052, TS8051, TS8052, TS9050, TS9055
2978366	Canon PGI-570PGBK XL - 22 ml - haut rendement - noir - original - réservoir d'encre - pour PIXMA MG5751, MG5752, MG5753, MG6851, MG6852, MG6853, MG7750, MG7751, MG7752, MG7753
2978367	Canon CLI-571M XL - 11 ml - haut rendement - magenta - original - réservoir d'encre - pour PIXMA TS5051, TS5053, TS5055, TS6050, TS6051, TS6052, TS8051, TS8052, TS9050, TS9055
7023430	Canon PFI-1000 PC - 80 ml - photo cyan - original - réservoir d'encre - pour imagePROGRAF PRO-1000
7023455	Canon PFI-1000 R - 80 ml - red - original - réservoir d'encre - pour imagePROGRAF PRO-1000
7023463	Canon PFI-1000 CO - 80 ml - optimisateur de couleurs - original - réservoir d'encre - pour imagePROGRAF PRO-1000
7023469	Canon PFI-1000 PBK - 80 ml - photo noir - original - réservoir d'encre - pour imagePROGRAF PRO-1000
-->

<!--
```sql
SELECT reference_interne, designation
FROM g_produits
WHERE description_produit IS NULL
AND system_id IS NOT NULL; -- system_id n'a pas été implémentée dans ma conception
```
-->

<!--
```sql
SELECT reference_interne, designation
FROM g_produits
WHERE system_id IS NOT NULL -- system_id n'a pas été implémentée dans ma conception
AND categorie = 'PC Portable';
```
-->

<!--
## 35. répérer les réfs (produtis) n'ayant pas de Spécs une semaine après leur visibilité dans TMS (différente de la date de création d'un produit)
-->


