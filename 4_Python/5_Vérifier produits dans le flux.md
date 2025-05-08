Vérifier produits dans le flux

__Note :__ le terme "refs" signifie "référence fabricant" (ou produit).

Lors de la création de produits, il peut être judicieux de vérifier que les produit (pour une marque donnée) 
est disponible chez les fournisseurs, avant de tenter de les créer.

Se connecter au progiciel : pour une marque données, exporter (fichier Excel) les produits présents dans le flux.
Depuis Pandas/Jupyter : importer les deux fichiers : 
le fichier export ci-dessus (soit Excel_Export), et fichier contenant les réfs qu'on souhaite créer (Excel_Creation).

Rechercher dans Excel_Export, les réfs présentes dans Excel_Creation. 
On obtient les réfs à créer. Les autres sont considérées comme n'étant pas dans le flux.
