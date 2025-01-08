# Bundle - Fonction de création d'un Bundle

Une Bundle est une association de plusieurs produits. 

Exemple : lorsqu'un produit doit être vendu avec une garantie, on créé un Bunlde associant le _fameux produit_ et la _garantie en question._

Solution fonctionnelle : 

Pour créer un bundle, l'utilisateur saisie uniquement les références internes des produits qui constitueront le futur Bundle.

- Générer le numéro du Bundle : le numéro de Bundle est généré en incrémentant (ajout de 1) le dernier Bundle présent en BDD. Dans la pratique : un premier numéro de Bundle est enregistré en BDD. C'est à partir de ce numéro que l'incrémentation ci-dessus se fait.
- Association du numéro de Bundle et des références internes de produits

Code PL/SQL (Algo) : 
1. selectionner le numéro du dernier Bundle en BDD
2. increnter ce numéro de 1; afin d'obtenir le numéro du Bundle en cours de création
3. parcourir la liste des références internes (passées en argument à la Fonction PL/SQL)
4. pour chaque références internes, enregistrer dans Bundle_Produits, une ligne qui comprend le _numéro de Bundle_ et la _référence interne_ en cours de traitement
5. retourner le numéro de Bundle

```sql
CREATE OR REPLACE FUNCTION create_bundle(...liste_des_refs...) return number
IS
  numero_dernier_bundle_en_bdd bundle.numero%TYPE;
  numero_bundle_en_cours bundle.numero%TYPE;
BEGIN
  -- 1. et 2.
  select numero_dernier_bundle_en_bdd from bundles order by date desc limit 1;
  numero_bundle_en_cours := numero_dernier_bundle_en_bdd + 1;
  -- OR
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

## Autres besoins métiers à propos de Bundle : 
- Afficher les produits (références internes et titres) constituant un Bundle donné.
- Pour plusieurs Bundle : afficher les produits (références internes et titres) constituant ces Bundles.
