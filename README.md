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
Etablir des stats sur chacune de ces périodes : le mois dernier, les 3 trois derniers mois, les 6 derniers mois, les 12 derniers mois

Groupe 1 : 
- nombre de produits crées 
- nombre de produits crées par marque
- nombre de produits crées par marque et gamme
- nombre de produits crées par catégorie

Note : 
- exploiter les fonctions : MIN, MAX, SUM, AVG, YEAR, SUBSTRING, CTE, RANK, DENSE_RANK (cf. vidéo ci-dessous vers 28min10
- possiblilité de les classer par : ordre alphabétique, les plus créés, les moins créés, etc.
- afficher les résultats avec __over__ pour afficher chaque sous-total (ex. voir cette vidéo, vers 18min48 : https://www.youtube.com/watch?v=QYd-RtK58VQ&list=PLUaB-1hjhk8FE_XZ87vPPSfHqb6OcM0cF&index=20)

![image](https://github.com/user-attachments/assets/aa1df12f-4763-49f1-95a1-ef7c1371e1cc)

DENSE_RANK : 

![image](https://github.com/user-attachments/assets/f8626dc9-8eb4-4635-8948-eb84265e6f21)

