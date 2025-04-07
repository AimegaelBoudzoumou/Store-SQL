# Mise à jour de données - UPDATE

## 1. Présentation du besoin métier

Tester une requête de type update où on met à jour plusieurs champs. Ex :

Update table g_produits

Set idMan = ‘1263’, iRange = ‘27454’

Where id in (val1, val2, val3, val4,…) ;

Requêtes SQL

## 2. Mise à jour / Changement de la catégorie pour plusieurs réfs :

Mise à jour / Changement de la catégorie pour plusieurs réfs :

Requêtes SQL

## 3. Présentation du besoin métier

Texte bref (moins de 4 phrases)

Requêtes SQL

## 4. Modifier le fabricant et la gamme pour plusieurs références

Hello Gp,

Merci de mettre les ref sous la marque et logo Philips .

STG

## Requêtes SQL

## 5. Fermer (mettre la phase à "rouge") les produits d'une marque donnée
soit PL/SQL
soit SQL : utiliser un CTE ou une "Temporary Table"

## 6. Fermer (mettre la phase à "rouge") les produits d'une gamme donnée

## 7. Fermer (mettre la phase à "rouge") les produits d'une catégorie et d'une marque données

## 8. Rendre visible sur le web, plusieurs réfs en même temps

## 9. Rendre "visible sur le web" toutes les réfs internes créées la veille

# 10. 
Update ou PL/SQL
Synchroniser plusieurs réfs internes (attribut « Phase » de chaque réf) : 
La méthode manuelle : 
TMS -> Aller sur chaque réf et cliquer sur 
  
Attends le message vert de confirmation

# 11.
Situation : un acheteur J.G. décide de quitter l’entreprise. Le directeur des achats S.S.  souhaite transférer les produits jusqu’alors sous la responsabilité de J.G. vers d’autres acheteurs.
L’affectation des réfs à un acheteur se fait par « marque et gamme » ou simplement par Gamme (car cette dernière contient l’information sur la marque)
Note : voici quelques tables de la BDD : utilisateurs (exemple : acheteurs), produits, gammes, categories
L’affectation d’un employeur en tant qu’acheteur pour une marque-gamme donnée, se fait soit par ajout dans la table être_acheteur (dans le cas où on souhaite garder en mémoire la liste des anciens acheteurs), 
soit par modification de l’employé dans la table être_acheteur.
Rappel de la structure d’un enregistrement dans la table être_acheteur : 
employé – marque – gamme – date

# 12.
Ecrire une procédure PL/SQL qui supprime le contenu_marketing pour plusieurs réfs
Ou simplement du code SQL :
Update g_produits
Set description_produits = NULL
Where ref_inerne IN (…) ;

## 13. Gammes de toutes ces réfs à passer en « iMac (M4) »

7512751

7512752

7512753

7512754

7512755

## 14. Ecrire une requête (ou même une procédure PL/SQl) qui permet de modifier la gamme pour une liste de référence

# Modifier Fabricant et Gamme

## 15. Peux-tu reclasser les réfs suivantes en fabricant : Blackview / gamme : Produits Blackview
30017842
30040186
30056307
30064315
30064400

## 16. Mise à jour de contenu marketing

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


# Intéressant ...
Il faudrait suprrimer la mention "jusqu’à" sur les désignaitons de plusieurs réfs

<!--
## 17. Mettre du contenu dans une balise HTML <p>...</p>

Pour toutes les réf qui ont les données "Description Existante" identiques à "Description CNET"; et dont le contenu textuel n'est pas entouré de la balise HTML <p>...</p> : 

écrire un code SQL qui : 
- soit récupérer le contenu, l'entourer dans la balise <p>...</p>, puis le charger
- soit écrire : <p> de texte et </p> en fin de texte
Je penche pour la première option.
-->

## 17. Mettre à jour les désignations de plusieurs produits, à partir de la désignation d'un produit donné :
```sql
UPDATE produits
SET designation = (SELECT designation FROM produit WHERE reference_interne = 7512536)
WHERE refererence_interne IN (XXXXXXX, XXXXXXX, XXXXXXX, XXXXXXX);
```



