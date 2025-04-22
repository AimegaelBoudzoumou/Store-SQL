# Comparaison de fichiers

But : vérifier que des titres précédemment chargés, sont bien conformes à la demande du client (ici la marque/fabricant).

A faire : pour une liste de réfs : faire une extraction des titres visibles actuellement et les comparer à ce que le client avait demandé l'intégration.
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

### Create new_DataFrame, Iterate df_fichier_de_base and Search data corresponding inside df_exports_au22_04_2025, and copy them in new_DataFrame

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

new_DataFrame
#len(refs_problematiques)
#refs_problematiques
#df_fichier_de_base
```

```python

```

```python

```

```python

```

```python

```
