Activité : charger les désignations venant de C|Net

Etape 1 :
Sara me communique un lien web contenant les produits concernés :
iStorage diskAshur 2
Faire du web scraping pour extraire : les réfs internes et réfs fabricants de la page ci-dessus ; et les stocker dans un fichier fichier_A

Etape 2 : récupérer les désignations sur C|Net

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
