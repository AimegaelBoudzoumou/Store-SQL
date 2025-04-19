## 20. Récupérer les titres actuellement en place, pour une liste de réf donnée

## 21. Récupérer la marque d’un produit. Penser à la jointure multique (entre produit, gamme, marque)

## 22. Pour plusieurs réfs : rechercher celle dont le contenu marketing vaut NULL
<!--
Parmi plusieurs réf traitées, j’ai oublié d’intégrer du contenu pour une réf. sauf que je ne sais plus laquelle.
Solution fonctionnelle : 
Sur une liste de refs, sélectionner celle dont le contenu_marketing (description_produit) est à NULL
Select ref_interne from g_produits where ref_interne IN (XXXXX, …) and description_produit IS NULL ;
-->

## 23. J’ai une liste de réf fabricant dont je veux récupérer les réfs internes correspondantes

## 24. Dans une liste de réf, déterminer celles(s) qui n’est pas en ligne

# Bundle

## 25. Pour une liste de Bundle donnée : récupérer les produits constituant chaque Bundle (faire un group by numéro de Bundle)

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
<!--
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
-->

## 38. Sauvegarder des désignations actuelles pour certaines réfs - à faire une fois en fin de journée

<!--
```sql
SELECT reference_fabricant, description_produit
FROM produits
WHERE reference_interne IN (XXXXXXX, XXXXXXX, XXXXXXX, XXXXXXX, XXXXXXX, XXXXXXX);
```
-->

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
