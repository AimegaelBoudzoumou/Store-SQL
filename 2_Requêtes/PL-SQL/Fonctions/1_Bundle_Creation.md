# Bundle - Fonction de création d'un Bundle

## 1. Définition d'un Bundle 
Une Bundle est une association de plusieurs produits. 

Exemple : lorsqu'un produit doit être vendu avec une garantie, on créé un Bunlde associant le _fameux produit_ et la _garantie en question._

## 2. Solution fonctionnelle - Algorithme

Pour créer un bundle, l'utilisateur saisie (passe en argument à la fonction) uniquement les références internes des produits qui constitueront le futur Bundle.

- Générer le numéro du Bundle : le numéro de Bundle est généré en incrémentant (ajout de 1) le dernier Bundle présent en BDD. Dans la pratique : un premier numéro de Bundle est enregistré en BDD. C'est à partir de ce numéro que l'incrémentation ci-dessus se fait.
- Appeler la fonction en lui passant en argument les références internes de produit. Associer le numéro de Bundle et des références internes de produit

1. selectionner le numéro du dernier Bundle en BDD. Dans la pratique : un premier numéro de Bundle est enregistré manuellement en BDD. C'est à partir de ce numéro que l'incrémentation suivante va se faire.
2. increnter ce numéro de 1; afin de générer le numéro du Bundle en cours de création.
3. parcourir la liste des références internes (passées en argument à la fonction PL/SQL).
4. pour chaque références internes, enregistrer dans __Bundle_Produits__, une ligne qui comprend le _numéro de Bundle_ et la _référence interne_ en cours de traitement.
5. retourner le numéro de Bundle.

## 3. Solution technique

```sql
CREATE OR REPLACE FUNCTION create_bundle(...liste_des_refs...) return number
IS
  numero_dernier_bundle_en_bdd bundle.numero%TYPE;
  numero_bundle_en_cours bundle.numero%TYPE;
  -- Traiter la liste_des_refs
BEGIN
  -- 1. et 2.
  select numero_dernier_bundle_en_bdd from bundles order by date_bundle desc limit 1;
  numero_bundle_en_cours := numero_dernier_bundle_en_bdd + 1;
  -- OU : écrire les deux lignes ci-dessous, sur une seule ligne : 
  -- select (numero_dernier_bundle_en_bdd + 1) into numero_bundle_en_cours from bundles order by date desc limit 1;
  
  -- 3. et 4.
  FOR ref_interne IN liste_des_refs
  LOOP
    INSERT INTO bundles_produits VALUES (numero_bundle_en_cours, ref_interne);
  END LOOP
  -- 5. retourner le numéro de Bundle
  return numero_bundle_en_cours
END;
/
```

## 4. Pour exécuter la fonction _create_bundle_: 

```sql
-- select package_name.function_name (15000)
-- from dual;
```

### Autres besoins métiers à propos de Bundle : 
- Afficher les produits (références internes) constituant un Bundle donné.
- Afficher les produits (références internes et titres) constituant un Bundle donné.
- Pour une liste de Bundles : afficher les produits (références internes et titres) constituant chaque Bundle.
- Retirer un produit d'un Bundle. Attention : vérifier que le nombre de produit restant est supérieur ou égal à deux.
- Remplacer un produit dans un Bundle. Attention : vérifier que le nombre de produit restant est supérieur ou égal à deux. Vérifier aussi que la nature du produit qu'on remplace est cohérente. Par exemple : remplacer un produit __PC Portable__ par un produit __iPhone__ n'est pas cohérent. Pour cette cohérence, on se base sur la gamme des deux produits (celui qu'on remplacer et le remplaçant).
