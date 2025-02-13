# Store-SQL

Une de mes expériences professionnelles m'a permi d'assurer le support des produits vendus sur un site e-commerce.

A travers ce document, je présente les réponses que j'ai pu apporter aux bésoins métiers rencontrés lors de ladite expérience professionelle.

Ce document comprend deux parties : __Modélisation de données relationnelles__ et __Ecriture des requêtes__ (SQL et PL/SQL).

## 1. Modélisation : 
MCD : Modèle Conceptuel de Données

MLD : Modèle Logique de Données

Dictionnaire de données

## 2. Requêtes SQL et PL/SQL

__Note__ : les requêtes SQL et PL/SQL ont été excutées dans un environnement __Oracle Live SQL__.

### PL/SQL

Les requêtes PL/SQL se trouvent dans le répertoire __2_Requêtes/PL-SQL__

### SQL

Les requêtes se trouvent dans le répertoire __2_Requêtes/SQL__

Ces requêtes SQL sont regroupées par type :

Création de tables - CREATE

Insertion de données dans les tables - INSERT INTO

Extraction de données - SELECT

Mise à jour de données - UPDATE

Suppression de données - DELETE

## 3. Tableaux de bord Power BI

J'ai jugé pertinent d'afficher dans un répertoire unique, les travaux relatifs au reporting.

Ce répertoire contient : 
- le tableaux des KPIs
- les requêtes SQL permettant de réaliser les KPIs sur les produits du site e-commerce
- le rapports et tableaux réalisés sous Power BI

Les trois éléments ci-dessus se trouvent dans le répertoire __3_Tableaux de bord - Power BI__

<!--
**Brouillon : A supprimer plus tard**

Procedure qui permet d'affecter un produit à un bundle. La procédure reçoit deux infos : le numéro de bundle et la réf_interne du produit.

On a un numéro de bundle : on aimerait savoir les produits (référence interne) associés à ce bundle. Penser à une jointure entre bundle_produits et produits, sur la ref_fabricant

On a une référence interne : on aimerait savoir quelles sont les bundles contenant la référence interne en question.

```sql

select numero from bundle_produits

where exists (

              select reference_interne
              
              from produits p
              
              join bundle_produits b
              
              on p.reference_fabricant = b.reference_fabricant
)
```
__Notion de filtre :__ 

Ajouter un attribut/champ 'filtre' dans les tables marque, gamme, categorie.

Ajouter un attrinbut/champ filtre dansles tables : "marque", "catégories" et "catégories". Ecrire les requêtes associées à la mise en place des filtres.

La mise en place d'un filtre sur une marque se repercute sur les gammes associés à la marque; et donc sur les produits associés aux gammes en question.

La mise en place d'un filtre sur une gamme se repercute sur les produits faisant partie de cette gamme.

La mise en place d'un filtre sur une catégorie se répercute sur les produits faisant partie de cette catégorie.

Avant de retirer un filtre_gamme sur un produit : vérifier que sa gamme n'est pas filtrée (attribut 'filtre' de la gamme en question).

Avant de retirer un filtre_categorie sur un produit : vérifier que sa catégorie n'est pas filtrée (attribut 'filtre' de la catégorie en question).

------------------------------------------------------------------------------------------------------------------------------------------------------------------

Récupérer le titre de chaque produit et l'intégrer en début de la déscription produit de la réf concernée.

------------------------------------------------------------------------------------------------------------------------------------------------------------------


Mettre en place une fonction qui vérifie qu'une référence_interne est unique (n'existe pas en doublon) dans la base de données.

Phase : vert (en ligne), gris (à statuer) par défaut, orange (pas de stock), rouge (suspendu)

Les types de produits

L'affectation de produit à un acheteur ou à un chef de produit, se fait par "marque". Modifier le MCD

Typage : 

P : produit physique

W : extension de garantie

L : Licence d'accès à des logiciels

Service (I : interne, E : externe, S : mise en relation entre le client et le prestataire)

C : crédit (ligne comptable)

-->

<!--
Pour plusieurs réfs : récupérer le "contenu marketing" (texte brute) et l'entourer dans la balise HTML de type paragraphe.

Allez plus loin : 

Séparer le "texte brute" en plusieurs parties (taille à définir). Encadrer chaque partie dans une balise HTML de type paragraphe.
-->

<!--
J'ai une liste de Bundle : 
pour chaque Bundle : je veux savoir la situation (Phase, Visible sur le Web) de chaque constituant le Bundle.
-->

<!-- GRANT
https://www.techbrothersit.com/2018/11/grant-permission-to-individual-fields.html
-->
