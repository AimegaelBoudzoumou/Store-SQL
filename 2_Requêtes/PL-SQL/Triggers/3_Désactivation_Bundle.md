Désactiver un Bundle : 

Ecrire un Trigger qui écoute le champ "Phase" d'un produit. Si ce champ passe à "rouge", alors le code PL/SQl recherche dans la table "produits_bundles", les "numeros" de Bundles associés au fameux produit.

Tous les Bundles concernés sont mis en phase drapeau rouge.

```sql
select numero from produits_bundle where reference_interne = 'xxxxxxx';
```
