# Extraction de données - SELECT

Pour chaque situation, je présente le __besoin fonctionnel__, suivi de la __requête SQL__ y relatif.

## 1. Vérifier qu'une référence existe en base de données

```sql
SELECT 7506950
FROM gproduits;
```

## 2. Référence fabricant vers référence interne

Pour un besoins divers, je souhaite récupérer la liste de __référence interne__ à partir de __références fabricants__.

### Requêtes SQL
```sql
```

## 3. Rechercher des produits en fonction d'un nom de marque

Rechercher les produits de marques « Génériques » et voir si on peut leur affecter la bonne marque (le bon fabricant)

## Requêtes SQL


## 3. Rechercher les produits de marque "Générique"
Rechercher les produits de marque "Générique"; afin de voir si on peut leur affecter la bonne marque.

Texte bref (moins de 4 phrases)

## Requêtes SQL

## 4. Rechercher les produits d'une marque quelconque
Soit la marque "Articona". Rechercher les produits de cette marque

Soit jointure, soit requêtes imbriquée : à définir

Soit jointure : Cf. question 6 ci-dessous

## 5. Afficher le nom d'une marque d'une référence interne

Soit la marque "Articona". Rechercher les produits de cette marque

## 6. Pour un employé donné, afficher la ou les marques dont il est "acheteur".
Astuce : pensez à utiliser la table "Gamme" dans notre requête SQL; et à une éventuelle double jointure entre :

Employe et Gamme (sur Employe.matricule = Gamme.matricule)

Gamme et Marque (sur Gamme.nom_marque = Marque.nom_marque)

## 7. Afficher les produits dont une employé donnée est responsable (chef de produit)

## 8. Sélectionner la catégorie pour une refs de produits donnée

## 9. Retrouver les réfs internes à partir d’une liste de réf fabricant

## 10. Recherches des produits non visibles sur le web et dont la désignation est à NULL
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

SELECT reference_interne
FROM gproduits
WHERE visibilite_web = 0
AND designation IS NULL;
```

## 11. Récupérer plusieurs titres
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

12. Rechercher l’acheteur d’une marque et d’une gamme donnée



