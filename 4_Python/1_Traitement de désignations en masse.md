# Traitement de désignations en masse

_Outils : Python, Pandas, Jupyter, Googletrans_

## Contexte

Un client souhaite améliorer des désignations pour plusieurs produits. Le client fournit un fichier Excel contenant les références concernées.

Les désignations à intégrer se trouvent sur le site de notre fournisseur de contenu.

## Objectif

- Récuperer des désignations sur le site du fournisseur de contenu. 
- Générer un nouveau fichier, afin d'intégration en masse.

## Les étapes à appliquer

Etape 1 : importer dans Pandas le fichier du client - contenant les produits dont il souhaite améliorer les désignations.

Etape 2 : répérer les marques/fabricants concernées

Etape 3 : pour chaque marque/fabricant : se rendre sur le site du fournisseur de contenu, puis exporter le fichier contenant les produits de la marque en question.
<!-- __Note :__ le fichier export étant lourd, le choix a été fait de traiter les marques par groupe de 2. -->

Etape 4 : importer les fichiers ci-dessus dans Pandas et les fusionner (concatener).

Etape 5 : Rechercher les désignations, puis exporter un nouveau fichier Excel contenan les produits (références) et les bonnes désignations associées.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Etape 1
Importer dans Pandas le fichier du client - contenant les produits dont il souhaite améliorer les désignations.

```python

```

### Etape 2
Répérer les marques/fabricants concernées

```python

```

### Etape 3
Pour chaque marque/fabricant : se rendre sur le site du fournisseur de contenu, puis exporter le fichier contenant les produits de la marque en question.
<!-- __Note :__ le fichier export étant lourd, le choix a été fait de traiter les marques par groupe de 2. Et surtout : de n'importer que les colonnes utiles. 
Pensez à convertir les données exportées car en anglais.
-->

```python

```

### Etape 4
Importer les fichiers ci-dessus dans Pandas et les fusionner (concatener).

```python

```

### Etape 5
Rechercher les désignations, puis exporter un nouveau fichier Excel contenan les produits (références) et les bonnes désignations associées.

```python

```
