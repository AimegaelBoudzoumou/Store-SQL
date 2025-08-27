# Mise à jour de données - UPDATE

## 1. Mettre à jour plusieurs champs en même temps
<!--
Tester une requête de type update où on met à jour plusieurs champs. Ex :

Update table g_produits

Set idMan = ‘1263’, iRange = ‘27454’

Where id in (val1, val2, val3, val4,…) ;
-->

## 2. Mise à jour / Changement de la catégorie pour plusieurs réfs :

## 3. Modifier le fabricant et la gamme pour plusieurs références
<!--
Hello Gp,

Merci de mettre les ref sous la marque et logo Philips .

STG
-->

## 4. Fermer (mettre la phase à "Suspendu") les produits d'une marque donnée
<!-- soit PL/SQL
soit SQL : utiliser un CTE ou une "Temporary Table"
-->

## 5. Fermer (mettre la phase à "rouge") les produits d'une gamme donnée

## 6. Fermer (mettre la phase à "rouge") les produits d'une catégorie et d'une marque données

## 7. Rendre visible sur le web, plusieurs réfs en même temps

## 8. Rendre "visible sur le web" toutes les réfs internes créées la veille

## 9. Synchroniser plusieurs réfs internes (attribut « Phase » de chaque réf)
<!-- Update ou PL/SQL
Synchroniser plusieurs réfs internes (attribut « Phase » de chaque réf) : 
La méthode manuelle : 
TMS : Aller sur chaque réf et cliquer sur 
  
Attends le message vert de confirmation
-->

## 10. Aaffecter des produits à un acheteur
<!--
Situation : un acheteur J.G. décide de quitter l’entreprise. Le directeur des achats S.S.  souhaite transférer les produits jusqu’alors sous la responsabilité de J.G. vers d’autres acheteurs.
L’affectation des réfs à un acheteur se fait par « marque et gamme » ou simplement par Gamme (car cette dernière contient l’information sur la marque)
Note : voici quelques tables de la BDD : utilisateurs (exemple : acheteurs), produits, gammes, categories
L’affectation d’un employeur en tant qu’acheteur pour une marque-gamme donnée, se fait soit par ajout dans la table être_acheteur (dans le cas où on souhaite garder en mémoire la liste des anciens acheteurs), 
soit par modification de l’employé dans la table être_acheteur.
Rappel de la structure d’un enregistrement dans la table être_acheteur : 
employé – marque – gamme – date
-->

## 11. Supprimer le contenu_marketing pour plusieurs réfs
<!--
Ecrire une procédure PL/SQL qui supprime le contenu_marketing pour plusieurs réfs
Ou simplement du code SQL :
Update g_produits
Set description_produits = NULL
Where ref_inerne IN (…) ;
-->
## 12. Modifier la gamme en « iMac (M4) », pour plusieurs produits

<!--
7512751

7512752

7512753

7512754

7512755
-->

## 13. Ecrire une requête (ou même une procédure PL/SQL) qui permet de modifier la gamme pour une liste de référence

## 14. Reclasser les réfs suivantes en fabricant : Blackview / gamme : Produits Blackview
<!-- 
30017842
30040186
30056307
30064315
30064400
-->

## 15. Mise à jour de contenu marketing
<!--
Recopier / Dupliquer le contenu marketing (descriptif produit) d’une réf, sur plusieurs autres réfs.
Ou avec SQL (à tester)
```sql
UPDATE produits
SET descriptif_produit = (
                          SELECT descriptif_produit
                          FROM produits
                          WHERE reference_interne = XXXXXX
                          )
WHERE reference_interne = XXXXXXX
```

Il est aussi possible d'utiliser PL/SQL : voir fichier...
-->

<!--
# Intéressant ...
Il faudrait suprrimer la mention "jusqu’à" sur les désignaitons de plusieurs réfs
-->

<!--
## 17. Mettre du contenu dans une balise HTML <p>...</p>

Pour toutes les réf qui ont les données "Description Existante" identiques à "Description CNET"; et dont le contenu textuel n'est pas entouré de la balise HTML <p>...</p> : 

écrire un code SQL qui : 
- soit récupérer le contenu, l'entourer dans la balise <p>...</p>, puis le charger
- soit écrire : <p> de texte et </p> en fin de texte
Je penche pour la première option.
-->

## 16. Mettre à jour les désignations de plusieurs produits, à partir de la désignation d'un produit donné :
```sql
UPDATE produits
SET designation = (SELECT designation FROM produits WHERE reference_interne = 7512536)
WHERE refererence_interne IN (XXXXXXX, XXXXXXX, XXXXXXX, XXXXXXX);
```

## 17. Mettre un filtre_gamme sur une liste de réfs données

```sql
UPDATE produits
SET FILTRE_GAMME = 1
WHERE REFERENCE_INTERNE IN (7951201, 7457826);
```

## 18. Supprimer filtre_gamme sur une liste de réfs données

## 19. Pour un ensemble de désignations remplacer une mention par une autre
<!--
Bonjour,

Il faut changer la designation sur toutes les references.

Tout ce qui contient "Azure Active Directory Premium" doit être remplacé par "Entra ID".

Le P1/P2 reste.

Merci

Code SQl :

drop table t1;

create table t1 (
    id_product int,
    designation varchar2(100)
);

insert into t1 values (10, 'Azure Active Directory Premium P1|CFQ7TTC0LFLS:0002-P1M-Monthly-COM');
insert into t1 values (20, 'Azure Active Directory Premium P1|CFQ7TTC0LFLS:0002-P1M-Monthly-COM');

select * from t1;

update t1
set designation = replace(designation, 'Azure Active Directory Premium', 'Entra ID')
where id_product in (10);

-- Autre

update t1
set designation = replace(designation, 'Azure Active Directory Premium', 'Entra ID')
where id_product in (
    select id_product from g_produits where ref_fab = 'CFQ7TTC0LFLS'
);

-- UPDATE table SET nom_colonne = REPLACE(nom_colonne, 'ancien texte', 'texte de remplacement')

select * from t1;

-->

### 20. Double Update

Soit la réf 7523922 : merci de modifier 

Gamme :	Windows Server ROK - Standard
Catégorie :	OS Serveur




