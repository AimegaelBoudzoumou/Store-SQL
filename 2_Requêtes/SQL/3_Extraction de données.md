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

## 3. Présentation du besoin métier

Texte bref (moins de 4 phrases)

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




