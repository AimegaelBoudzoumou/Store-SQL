# Store-SQL

Ce projet concerne la gestion des produits vendus sur un site e-commerce. A travers ce document, je présente les réponses informatiques susceptibles de répondre aux bésoins métiers émanant des acheteurs, chefs de produits, commerciaux.

Contenu:

## Modélisation : 
MCD : Modèle Conceptuel de Données. MLD : Modèle Logique de Données. Dictionnaire de données. 

## Requêtes
SQL : création de tables, insertion de données dans les tables, extraction de données, mise à jour de données, suppression de données.

PL/SQL : Trigger, Fonctions, Procédures. 

## Tableaux de bord Power BI
Le tableaux des KPIs. Les requêtes SQL permettant de réaliser les KPIs sur les produits du site e-commerce. 

Les rapports et tableaux de bord réalisés sous Power BI.

## Python : Web Scraping
Projet d'extration des certaines informations (titres, désignation, description produit, référénces internes, références fabricants) de plusieurs pages web. 

Python, Requests, BeautifulSoup, Pandas.

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

<!-- Process : Gestion des réfs mises en ligne :

Créer un trigger qui écoute le champ phase des produits "qui ne sont pas en ligne". 

Si le produit est mis en ligne (passage à la phase "verte"), alors : la réf est enregistrée dans une table "suivi_ref_mises_en_phase_verte".

Ces réfs nouvellement mise en ligne sont alors visibles dans une "page dans TMS". Un clic sur un produit nous conduit vers la page TMS du produit en question, afin de voir ce qu'il faut améliorer : titre, visuel, CM, désignation, Spécs

Une fois la réf traitée : il faut le signifier dans la "page dans TMS". Ceci afin que le produit soit retirée de la liste.

-->

<!-- Besoin métier 
Parcourir une liste de réf
Pour chaque désignaion, retirer un mot donnée
-->

<!--
Pour plusieurs réfs, je souhaite qu'on intègre :
 
1/2
Spécification(s) Principale(s) Cnet
Spécification(s) Etendue(s) Cnet
Image(s) Cnet

2/2 Pour les mêmes réfs : 
Est-il possible d'intégrer à la place du "titre", les données C|Net suivante ?
Spécification(s) Principale(s) Cnet -> Description du produit :
-->

<!-- GRANT
https://www.techbrothersit.com/2018/11/grant-permission-to-individual-fields.html
-->

<!--
Grâce au web scraping : rechercher les pages web contenant le texte "Description produit non disponible pour le moment et nous en sommes désolés.".

En utilisant SQL : Remplacer le texte "Description produit non disponible pour le moment et nous en sommes désolés." par le titre du produit.

Il sera question de renseigner manuellement chaque URL, ce qui peut être chronophage. Refléchir à comment automatiser
-->
