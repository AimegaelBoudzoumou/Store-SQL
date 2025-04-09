# Traitement de désignations en masse

Un client souhaite améliorer des désignations pour plusieurs produits. Le client fournit un fichier Excel contenant les références concernées.

__But :__

- Récuperer des désignations sur le site du fournisseur de contenu. 
- Générer un nouveau fichier, afin d'intégration en masse.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

Etape 1 : importer dans Pandas le fichier du client - contenant les produits à traiter (dont il faut traiter les désignations).

Etape 2 : répérer les marques/fabricants concernées

Etape 3 : pour chaque marque/fabricant : se rendre sur le site du fournisseur de contenu, puis exporter le fichier contenant les produits de la marque en question.

Etape 4 : importer les fichiers ci-dessus dans Pandas et les fusionner (concatener).

Etape 5 : Rechercher les désignations, puis exporter un nouveau fichier Excel contenan les produits (références) et les bonnes désignations associées.
