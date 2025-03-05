# Mise_A_Jour_De_Descriptif_Produit.md

Dupliquer : 

New réf :                             Réf à dupliquer :

7511896                             7486963

7511939                             7356805

7509364                             7356619

7507336                             7342724    

7509868                             7342725   


Attention : s'assurer que le fabricant, la gamme et la catégorie de chaque couple correspondent.

Exemple : 7511896 et 7486963 doivent avoir le même fabricant, la même gamme et la même catégorie avant de charger les données de 7486963 sur 7511896.

Possibilité 1 : créer une procédure PL/SQL qui reçoit deux réfs en arguments. Le code recopie la description (contenu HTML/CSS) du la deuxième dans la première

Possibilité 2 : créer une procédure qui reçoit une liste de couple de réfs …

Ecrire une procédure PL/SQL qui reçoit des couples de réfs internes.
Pour chaque couple, le code récupère le contenu marketing de la première réf et le copie sur la deuxième réf.
Note : il est également possible de transmettre en argument au code PL/SQL un fichier (ex. Excel), avec deux colonnes de réfs internes : la première colonne contient la réf source et la seconde contenant la réf cible.

Autre piste d'idée : 
Solution fonctionnelle :
L’acheteur nous fournit un fichier Excel contenant deux colonnes. Une pour la « New réf » et une autre pour la « réf à dupliquer ».
Ecrire une procédure PL/SQL qui parcourt le fichier Excel, et copie les données (visuels, fiche produit (contenu marketing)) de « New réf » vers « réf à dupliquer ».
