# Traitement de désignations en masse

_Outils : Python, Pandas, Jupyter, Googletrans_

## Contexte

Un client souhaite améliorer des désignations pour plusieurs produits. Le client fournit un fichier Excel contenant les références concernées.

Les désignations à intégrer se trouvent sur le site de notre fournisseur de contenu.

## Objectif

- Récuperer des désignations sur le site du fournisseur de contenu. 
- Générer un nouveau fichier, afin d'intégration en masse.

## Les étapes à appliquer

__Etape 1 :__ connexion aux données. Importer dans Pandas le fichier du client - contenant les produits dont il souhaite améliorer les désignations.

__Etape 2 :__ répérer les différentes fabricants concernées. pour chaque fabricants : créer une DataFrame contenant les réfs associées (et ayant ces deux colonnes : référence fabricant, designation). 

Note : Nommer le DataFrame sous la nomenclature suivante : df2_nom_fabricant. Bien gérer le set_index

__Etape 3 :__ pour chaque fabricant : se rendre sur le site du fournisseur de contenu, puis exporter le fichier contenant les produits de la marque en question. 

Ensuite importer ce fichier dans Pandas.

__Note__: 
Pour des raisons d'optimisation de la mémoire, n'importer dans Pandas que les colonnes du fichier qui sont utiles, à savoir : la "référence fabricant" et la "désignation". 

Note : Nommer le DataFrame sous la nomenclature suivante : export_nom_fabricant. Bien gérer le set_index

__Etape 4 :__ extraire les désignations : pour chaque DataFrame créé à l'étape 2 (df2_nom_fabricant), extraire la désignation associées (provenant du fournisseur de contenu).

Exploiter ceci :

```python

df2_nom_fabricant = df2_nom_fabricant.set_index(ref_fab)

liste_ref_desirees_nom_fabricant = df2_nom_fabricant.index

df_final_ref_desirees_nom_fabricant = export_nom_fabricant.loc[liste_ref_desirees_nom_fabricant]

```

__Etape 5 :__ Fusionner/Concatener tous les df_final_ref_desirees_nom_fabricant.

__Etape 6 :__ Traduire toutes désignations de df_final_ref_desirees_nom_fabricant en anglais. Ajouter une colonne à df_final_ref_desirees_nom_fabricant et utiliser l'API _Googletrans_ pour faire la traduction.

__Etape 7 :__  Exporter le DataFrame sous forme de fichier Excel.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Implémentation : 

### Etape 1


```python

```

### Etape 2


```python

```


### Etape 3

```python

```

### Etape 4

```python

```

### Etape 5

```python

```

### Etape 6

```python

```

### Etape 7

```python

```
