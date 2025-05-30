# Comparaison de fichiers

_Outils : Python, Pandas, Jupyter_

## Contexte

Après une intégration en masse de titres, il est intéressant de vérifier que l'intégration a réussi.

## Objectif

L'objectif de ce script est de comparer le contenu de deux fichiers Excel : 

celui (reçu du chef de produit ou du client : fabricant) contenant les données que l'on vient d'intégrer,

et 

celui contenant la situation réelle en Base de données, à un moment donné.
<!--
__But :__ vérifier que des titres précédemment chargés, sont bien conformes à la demande du client (ici la marque/fabricant).

__A faire :__ pour une liste de réfs : faire une extraction des titres visibles actuellement et les comparer à ce que le client avait demandé l'intégration.
charger les deux fichiers dans Jupyter et les comparer.
-->

## Les étapes à appliquer

1. Connexion aux données et Définition d'index
   
3. Construire un nouveau DataFrame
   
5. Comparaison des deux DataFrame
   
7. Répertorier les réfs dont l'intégration du titre a potentiellement réussi

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Implémentation

### 1. Connexion aux données

Importation de la librairie Pandas
```python
import pandas as pd
```

Importation du fichier "fichier_de_base.xlsx" contenant les titres dont on a demandé l'intégration
```python
df_fichier_de_base = pd.read_excel("mes_fichiers/fichier_de_base.xlsx")
df_fichier_de_base
```

Importation du fichier "Export_22_04_2025.xlsx", uniquement les colonnes A et I, contenant respectivement les références internes de produits et les titres.
```python
df_exports_au_22_04_2025 = pd.read_excel("mes_fichiers/Export_22_04_2025.xlsx", usecols = 'A,I')
df_exports_au_22_04_2025 # contient les titres après l'action d'intégration
```

### Définir un index

Fixer la colonne "Inmac REF" comme index du dataframe
```python
df_fichier_de_base = df_fichier_de_base.set_index("Inmac REF")
df_fichier_de_base
```

Fixer la colonne "idproduct" comme index du dataframe
```python
df_exports_au_22_04_2025 = df_exports_au_22_04_2025.set_index("idproduct")
df_exports_au_22_04_2025
```

### 2. Construire un nouveau DataFrame, afin de comparaison avec le DataFrame fichier_de_base


```python
new_DataFrame = pd.DataFrame(columns=["Inmac REF", "Titre"])

refs_problematiques = []

for x in df_fichier_de_base.index:
    if x in df_exports_au_22_04_2025.index:
        title = df_exports_au_22_04_2025.loc[x, "ttPDPDescription"]
        new_line = [x, title]
        lenght = len(new_DataFrame)
        new_DataFrame.loc[lenght] = new_line
    else:
        # sauvegarder les réfs problématiques : présentes dans df_fichier_de_base, mais pas dans df_exports_au_22_04_2025
        refs_problematiques.append(x)
        
        # supprimer une à une les réfs en question, ie le supprimer de df_fichier_de_base (ou les supprimer en une seule fois)
        df_fichier_de_base.drop(x,  axis=0, inplace=True) # afin que df_fichier_de_base soit de même dimension que new_DataFrame

new_DataFrame
```


### Modification de l'index pour new_DataFrame

```python
new_DataFrame = new_DataFrame.set_index("Inmac REF")
new_DataFrame
```

### 3. Comparaison des deux DataFrame

```python
diff = df_fichier_de_base.compare(new_DataFrame)
diff
```

```python
# Exporter le résultat de la comparaison dans un fichier Excel
diff.to_excel("mes_fichiers/Comparaison_de_fichiers/diff.xlsx")
```

### 4. Répertorier les réfs dont l'intégration du titre a potentiellement réussi

```python
# créer une liste nommée "ref_reussie"
ref_reussie = []

# itérer df_fichier_de_base
for x in df_fichier_de_base.index :
   # si une réf présente dans df_fichier_de_base, n'est pas dans diff alors la stocker dans ref_reussie
    if x not in diff.index:
        ref_reussie.append(x)

# Afficher le contenu de ref_reussie
ref_reussie

# Convertir la liste ref_reussie en DataFrame
df_ref_reussie = pd.DataFrame(ref_reussie, columns=["Refs internes"])
df_ref_reussie
```

<!--
Divers 1 :
df_fichier_de_base.loc[7317066,:] # 7317066 n'est pas dans l'export d'Olivier

#df_exports_au_22_04_2025.loc[7317066,:]

df_fichier_de_base.loc[7531255,:]

Divers 2 :

import pandas as pd

# df = pd.read_excel(r"C:/Users/aimegael.boudzoumou/Documents/export.xlsx", sheet_name="Feuil", header=0, usecols='A:C', nrows=5, skiprows=None, na_values=['NA','-','N/A'])

df = pd.read_excel("mes_fichiers/Export.xlsx", sheet_name="Feuil1", header=0, index_col="RefFabricant")

df
-->


