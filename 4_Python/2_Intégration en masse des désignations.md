# Charger en masse des désignations venant de notre provider de contenu

## Contexte
Cette avtivité consiste à intégrer des désignations (à récupérer auprès de notre fournisseur de contenu) sur plusieurs produits.

## Mon objectif
Sur la base d'un lien web que me fournit le chef de produits, je dois, pour chaque produit visibles sur le lien web, récupérer puis charger la désignation correspondante provenant de notre fournisseur de contenu. 

## Les étapes appliquées

__1-__ Le chef de produits me communique un lien web contenant les produits concernés.
<!--[iStorage diskAshur 2](https://www.inmac-wstore.com/recherche/istorage-diskashur-2.htm?txtrecherche=istorage-diskashur-2)-->

Faire du web scraping sur le lien web reçu, pour extraire les __références internes__ et les __références fabricants__ des produits visibles sur le lien web en question. Stocker les données dans un fichier Excel ou CSV.

_Aperçu du fichier*_

__2-__ Aller sur le site web de notre provider de contenu, et récupérer toutes les désignations de la marque/fabricant iStorage; sous forme de fichier Excel.

_Aperçu du fichier*_

__3-__ Grâce à Python, "croiser" les deux fichiers ci-dessus, pour se retrouver avec un DataFrame contenant uniquement 3 informations/colonnes : les __références internes__, les __références fabricants__, et les __descriptions__.

__4-__ Les désignations étant en anglais : utiliser l’API de Google nommée Googletrans, pour traduire ces désignations de l’anglais vers le français.
Récupérer le résultat dans un nouveau DataFrame. Exporter ce dernier sous forme de CSV ou Excel, qui sera nommé : 
iStorage_integration_designations_en_masse_date_du_jour.

__5-__ Faire une intégration en masse de plusieurs désignations, via SQL.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 1. Faire du web sraping sur le lien web reçu du che de produits
<!--[iStorage diskAshur 2](https://www.inmac-wstore.com/recherche/istorage-diskashur-2.htm?txtrecherche=istorage-diskashur-2)-->

_Aperçu du lien web*_

```python
```

_Aperçu du fichier obtenu après avoir appliqué le web scraping*_

## 2- Récupérer toutes les désignations de la marque/fabricant iStorage, sur le site web de notre provider de contenu.

_Aperçu du fichier*_

## 3. A partir des deux fichiers ci-dessus, créer un DataFrame contenant uniquement 3 colonnes : références internes, références fabricants, descriptions.

```python
```

_Aperçu du DataFrame*_

## 4. Utiliser l’API de traduction de Google (Googletrans), pour traduire les désignations de l’anglais vers le français.
Créer un nouveau DataFrame contenant en plus, une colonne des désignations en français.

```python
```

_Aperçu du DataFrame avec les désignations traduites*_

Exporter ce DataFrame (fichier iStorage_integration_designations_en_masse_date_du_jour).

```python
# Exporter le DataFrame au format CSV.

```

_Aperçu du fichier CSV iStorage_integration_designations_en_masse_date_du_jour*_

## 5. Intégrer les nouvelles désignations en masse, via SQL

```sql

```

* : les aperçus de fichiers sont disponibles sur demande. Merci de votre compréhension.

<!--
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
Etape 1 :
Un chef de produit me communique un lien web contenant les produits concernés :
[iStorage diskAshur 2](https://www.inmac-wstore.com/recherche/istorage-diskashur-2.htm?txtrecherche=istorage-diskashur-2)

Faire du web scraping pour extraire : les réfs internes et réfs fabricants de la page ci-dessus ; et les stocker dans un fichier fichier_A

Etape 2 : récupérer les désignations chez notre provider de contenu

2.1.
Aller sur le site de C|Net et faire : 
Product Catalog -> Catalog availability ->Ecrire « iStorage » dans le champ « Manufacturer Name » sur la droite -> cliquer sur « Search »

2.2.
Une fois le résultat affiché à l’écran, cliquer sur « Download Search Results » en bas à droite

Sur la nouvelle page, cliquer sur « Download generated text file ». 

2.3.
Ce fichier est au format .txt
Pour le transformer au format Excel : Copier/coller son contenu dans un fichier Excel, qui sera nommé fichier_B

Aperçu du fichier Excel fichier_B :

Note : 
Description = Désignation (chez Inmac)
Mfg_PN         = Référence fabricant (chez Inmac)

Etape 3 :
Grâce à Python, croiser les deux fichier fichier_A et fichier_B, pour se retrouver avec un DataFrame contenant uniquement :
Réfs interne, réfs fabricant, Description

Etape 4 :
Utiliser l’API de Google nommée Googletrans, pour traduire les désignations de l’anglais vers le français.
Récupérer le résultat dans un nouveau DataFrame. Exporter ce dernier sous forme de CSV ou Excel, qui sera nommé : 
iStorage_integration_designations_en_masse_date_du_jour.

Vidéo ressources pour Googletrans : 
Google Translate API for Python - Step-by-Step guide - YouTube

Etape 5 :
Faire une intégration en masse de plusieurs désignations


-->
