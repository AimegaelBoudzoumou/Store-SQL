# Extraction d'informations de plusieurs pages web avec Python (Requests, BeautifulSoup, Pandas)

## Contexte
Certaines pages produits ne sont plus consultées depuis un certaines temps.

Parmi ces pages l'équipe web souhaite savoir lesquels conserver dans le site internet.

Pour ce faire, l'équipe web transmet à chaque chefs de produits, un fichier Excel/CSV contenant des informations (dont les liens URLs) sur les produits concernés. Ceci, afin que chacun se prononce sur les produits à conserver dans le site internet.

## Mon objectif
Avoir un fichier Excel/CSV contenant certains éléments (titres, désignation, description produit).
Ensuite : parcourir ce fichier visuellement et décider des éléments à améliorer.

## Les étapes
- Collecter les fichiers
- Nettoyer les fichiers
- Faire du web scraping et construire un nouveau fichier contenant les éléments pertinents : titre, désignation, description produit, URL

---------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Collecter les fichiers
Je reçois les fichiers Excel/CSV dans ma boîte email

## Nettoyer les fichiers 
Le but du nettoyage est de supprimer les lignes et colonnes non pertinentes, afin de n'avoir qu'une seule colonne d'URL dans le fichier Excel/CSV.

## Faire du web scraping
Pour chaque URL dans le fichier Excel/CSV, extraire les informations (titre, désignation, description produit) de la page web concernée.
Construuire un nouveau fichier Excel/CSV et l'exporter.
