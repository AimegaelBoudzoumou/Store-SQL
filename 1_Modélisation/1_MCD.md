# Modèle Conceptuel de Données

Le MCD (Modèle Conceptuel de Données) est une représentation graphique des éléments (entités) qui seront amenés à interagir au sein d'un applicatif.

Ce [tutoriel](https://www.ibm.com/fr-fr/topics/data-modeling) de IBM contient des informations détaillées sur la modélisation des données relationnelles.

Outil utilisé : logiciel AnalyseSI en environnement Windows.

__Note importante :__ 
- dans l'idéal, la clé primaire de certaines tables (marques, gamme, catégories, phases, type_de_produits) devrait être de type numérique (Integer) et non chaîne de caractères (Varchar). Dans la suite (section Requêtes), j'attribuerai un code (de type numérique) aux tables ci-haut citées.
- dans la suite de ce document, j'ai également modifié la table 'produits' pour faire de l'attribut 'reference_interne' la clé primaire.

![image](https://github.com/user-attachments/assets/68b36bde-e7e0-48f1-8239-3a451e505845)

__Modifications à apporter au MCD ci-dessus :__ : 

- Ajouter la possibilité de filtrer une marque.
Techniquement : ajouter un champ "presence_filtre" dans l'entité "marque/fabricant".
Cet attribut vaut 0 pour _absence de filtre_ et 1 pour _présence de filtre_.
- Dans l'entité "produits" : retirer les attributs "filtre_gamme" et "filtre_categorie"; et les remplacer par "nom_gamme" et "nom_categorie" respectivement.
- Dans les entités "gamme" et "categorie" : ajouter un attribut "presence_filtre" .
Cet attribut vaut 0 pour _absence de filtre_ et 1 pour _présence de filtre_.
- Ajouter une entité "Fournisseur", associée à l'entité "Produits"
