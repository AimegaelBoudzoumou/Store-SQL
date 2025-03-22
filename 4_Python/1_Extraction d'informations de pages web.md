# Extraction d'informations de plusieurs pages web avec Python (Requests, BeautifulSoup, Pandas)

## Contexte

<!--
Dans le cadre de la mise en conformité du site e-commerce avec les normes d’accessibilité (WCAG 2.2 niveau AA / RGAA), l'équipe web doit procéder à un tri des pages existantes.
-->

Certaines pages produits étant obsolètes, ou n'ayant pas été consultées depuis un certains temps, l'équipe web doit procéder à un tri des pages web, pour savoir lesquels conserver dans le site e-commerce.

Pour ce faire, l'équipe web transmet à chaque chef de produits, un fichier Excel/CSV contenant des informations (dont les liens URLs) sur les produits concernés paar le tri. Ceci, afin que chacun se prononce sur les produits à conserver dans le site internet.

## Mon objectif
Avoir un fichier Excel/CSV contenant certains éléments (titres, désignation, description produit).
Ensuite : parcourir ce fichier visuellement et décider des éléments à améliorer.

## Les étapes appliquées sur chaque fichier Excel/CSV
- Collecter le fichier
- Nettoyer le fichier
- Faire du web scraping et construire un nouveau fichier contenant les éléments pertinents : titre, désignation, description produit, URL

---------------------------------------------------------------------------------------------------------------------------------------------------------------------
## 1. Collecter le fichier
Je reçois le fichier Excel/CSV dans ma boîte email.

_Aperçu d'un fichier collecté :_

## 2. Nettoyer le fichier 
Le but du nettoyage est de supprimer les lignes et colonnes non pertinentes, afin de n'avoir qu'une seule colonne (contenant l'URL) dans le fichier Excel/CSV.

_Aperçu d'un fichier après nettoyage :_

## 3. Faire du web scraping
Pour chaque URL dans le fichier Excel/CSV, extraire les informations (titre, désignation, description produit) de la page web concernée.
Construire un nouveau fichier Excel/CSV et l'exporter.

_Aperçu d'un fichier obtenu après le web scraping :_

C'est le fichier ci-dessus que je parcours visuellement pour savoir quelles informations (titre, désignation, description produit) à améliorer sur chaque produit.
