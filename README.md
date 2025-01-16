# Store-SQL

Une de mes expériences professionnelles m'a permi d'assurer le support des produits vendus sur un site e-commerce.

A travers ce document, je présente les réponses que j'ai pu apporter aux bésoins métiers rencontrés lors de ladite expérience professionelle.

Ce document comprend deux parties : __Modélisation de données relationnelles__ et __Ecriture des requêtes__ (SQL et PL/SQL).

## 1. Modélisation : 
MCD : Modèle Conceptuel de Données

MLD : Modèle Logique de Données

Dictionnaire de données

## 2. Ecriture des requêtes SQL et PL/SQL

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

### Reporting

J'ai jugé pertinent d'afficher dans un répertoire unique, les requêtes SQL relatives au reporting.

Ces requêtes se trouvent dans le répertoire __2_Requêtes/Reporting__

**Brouillon : A supprimer plus tard**

Reporting : 

1/ Requêtes de Reporting mensuel :

- nombre et liste des produits créés sur le dernier mois

- nombre de produits créés par fabricants/marque, par gamme, par catégorie, par type

- Classement des produits qui ont été le plus créés (par fabricant, par gamme, par catégorie, par type) et le moins créés (par fabricant, par gamme, par catégorie, par type)

2/ Requêtes de Reporting trimestiel : 

reproduire les stats ci-dessus, mais cette fois ci sur les 3 derniers mois

3/ Requêtes de Reporting semestriel : 

reproduire les stats ci-dessus, mais cette fois ci sur les 6 derniers mois

4/ Requêtes de Reporting semestriel : 

reproduire les stats ci-dessus, mais cette fois ci sur les 12 derniers mois

5/ Requêtes de Reporting semestriel : 

reproduire les stats ci-dessus, mais cette fois ci par semaine sur le dernier mois. Cela permet par exemple de savoir au quel de quel semaine il y a eu le plus de ventes/création de produits.

- Recherches : comment choisir le bon visuel (barre, histogramme, etc.)


Exemple de réalisations : 

__Window Functions__

![image](https://github.com/user-attachments/assets/aa1df12f-4763-49f1-95a1-ef7c1371e1cc)

__DENSE_RANK__

![image](https://github.com/user-attachments/assets/f8626dc9-8eb4-4635-8948-eb84265e6f21)

Phase : vert (en ligne), gris (à statuer) par défaut, orange (pas de stock), rouge (suspendu)

Les types de produits

L'affectation de produit à un acheteur ou à un chef de produit, se fait par "marque". Modifier le MCD

Typage : 

P : produit physique

W : extension de garantie

L : Licence d'accès à des logiciels

Service (I : interne, E : externe, S : mise en relation entre le client et le prestataire)

C : crédit (ligne comptable)
