# Traitement de désignations en masse

_Outils : Python, Pandas, Jupyter, Googletrans_

## Contexte

Un client souhaite améliorer des désignations pour plusieurs produits. Le client fournit un fichier Excel contenant les références concernées.

Les désignations à intégrer se trouvent sur le site de notre fournisseur de contenu.

## Objectif

- Récuperer des désignations sur le site du fournisseur de contenu. 
- Générer un nouveau fichier, afin d'intégration en masse.

## Les étapes à appliquer

1. Connexion aux données
2. Création d'un DataFrame par fabricant
3. Importation des désignation du site du fournisseur de contenu. Création d'un DataFrame par fabricant
4. Extraction des désignations
5. Fusionner les DataFrame des différents fabricants
6. Traduire toutes désignations
7. Exporter le DataFrame sous forme de fichier Excel

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Implémentation

### 1. Connexion aux données

Connexion aux données. Importer dans Pandas le fichier du client - contenant les produits dont il souhaite améliorer les désignations.


```python

```


### 2. Créer un DataFrame pour chaque fabricant

Répérer les différentes fabricants concernées. pour chaque fabricants : créer un DataFrame contenant les réfs associées (et ayant ces deux colonnes : référence fabricant, designation). 

__Note :__ Nommer le DataFrame sous la nomenclature suivante : df2_nom_fabricant. Bien gérer le set_index


```python

```


### 3. Importer les désignations du fournisseur de contenu

Pour chaque fabricant : se rendre sur le site du fournisseur de contenu, puis exporter le fichier contenant les produits de la marque en question. 

Ensuite importer ce fichier dans Pandas.

__Note__: 
Pour des raisons d'optimisation de la mémoire, n'importer dans Pandas que les colonnes du fichier qui sont utiles, à savoir : la "référence fabricant" et la "désignation". 

__Note :__ Nommer le DataFrame sous la nomenclature suivante : export_nom_fabricant. Bien gérer le set_index

```python

```


### 4. Extraire les désignations

Extraire les désignations : pour chaque DataFrame créé à l'étape 2 (df2_nom_fabricant), extraire la désignation associées (provenant du fournisseur de contenu).

Exploiter ceci :

```python

df2_nom_fabricant = df2_nom_fabricant.set_index(ref_fab)

liste_ref_desirees_nom_fabricant = df2_nom_fabricant.index

df_final_ref_desirees_nom_fabricant = export_nom_fabricant.loc[liste_ref_desirees_nom_fabricant]

```

```python

```


### 5. Fusionner les DataFrame

Fusionner/Concatener tous les df_final_ref_desirees_nom_fabricant.

```python

```


### 6. Traduire toutes désignations

Traduire toutes désignations de df_final_ref_desirees_nom_fabricant de l'anglais vers le français. Ajouter une colonne à df_final_ref_desirees_nom_fabricant et utiliser l'API _Googletrans_ pour faire la traduction.

```python

```


### 7. Exporter le DataFrame sous forme de fichier Excel.

```python

```
