# Comparaison de fichiers

Après une intégration en masse de titres, il est intéressant de vérifier que l'intégration a réussi.

L'objectif de ce script est de comparer le contenu de deux fichiers Excel : 

celui (reçu du chef de produit ou du client : fabricant) contenant les données que l'on vient d'intégrer,

et 

celui contenant la situation réelle en Base de données, à un moment donné.

__But :__ vérifier que des titres précédemment chargés, sont bien conformes à la demande du client (ici la marque/fabricant).

__A faire :__ pour une liste de réfs : faire une extraction des titres visibles actuellement et les comparer à ce que le client avait demandé l'intégration.
charger les deux fichiers dans Jupyter et les comparer.

```python
import pandas as pd
```

### Connecting to Datas

```python
df_fichier_de_base = pd.read_excel("mes_fichiers/fichier_de_base.xlsx")
df_fichier_de_base
```

```python
df_exports_au_22_04_2025 = pd.read_excel("mes_fichiers/Export_22_04_2025.xlsx", usecols = 'A,I')
df_exports_au_22_04_2025
```

### Set the new indexes

```python
df_fichier_de_base = df_fichier_de_base.set_index("Inmac REF")
df_fichier_de_base
```

```python
df_exports_au_22_04_2025 = df_exports_au_22_04_2025.set_index("idproduct")
df_exports_au_22_04_2025
```

### Build a new DataFrame for comparison and fichier_de_base

```python
new_DataFrame = pd.DataFrame(columns=["Inmac REF", "Titre"])

refs_problematiques = []

for x in df_fichier_de_base.index:
    if x in df_exports_au_22_04_2025.index:
        title = df_exports_au_22_04_2025.loc[x, "ttPDPDescription"]
        new_line = [x, title]
        lenght = len(new_DataFrame)
        new_DataFrame.loc[lenght] = new_line
    #else:
        # sauvegardes les réfs problématiques : présentes dans df_fichier_de_base, mais pas dans df_exports_au_22_04_2025
        #refs_problematiques.append(x)
        
        # supprimer une à une les réfs en question, ie le supprimer de df_fichier_de_base (ou les supprimer en une seule fois)
        #df_fichier_de_base.drop(x,  axis=0, inplace=True) 

# plus tard : comparer df_fichier_de_base et new_DataFrame

```

```python
new_DataFrame
```

```python
len(refs_problematiques)
```

```python
refs_problematiques
```

```python
df_fichier_de_base
```

### Comparison of new_DataFrame and fichier_de_base

```python

```

```python

```

```python

```

```python

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


