# Vérification des désignations Startech.com

## 1. Importer la librairie Pandas
```python
import pandas as pd
```

## 2. Importer le fichier contenant les désignations que l'on souhaite charger
```pyton
# ce tableau va être utilisé pour spécifier les colonnes à extraire du fichier de base
columns1 = ["REF interne", "Désignation"]

# création du dataframe df_StarTech_fichier_de_base
df_StarTech_designation_à_charger = pd.read_excel("Demande Intégration en masse - StarTech - 25 Mar 2025 - Copie.xlsx",
usecols = columns1)
```

### Fixer comme index : REF interne
```python
df_StarTech_designation_à_charger = df_StarTech_designation_à_charger.set_index("REF interne")
```

### Appel du dataframe df_StarTech_fichier_de_base
```python
df_StarTech_designation_à_charger
```

## 3. Importer le fichier affichant la situation de la BDD
```python
# Export depuis TMS
df_Export_ProductsList_StarTech = pd.read_excel("ProductsList_StarTech.xlsx", usecols = ["[FR.REPORTING.PRODUCTSLIST.INTERNAL_REF]", "Designation"])

df_Export_ProductsList_StarTech = df_Export_ProductsList_StarTech.set_index("[FR.REPORTING.PRODUCTSLIST.INTERNAL_REF]")

df_Export_ProductsList_StarTech
```

```python
liste_des_refs_à_integrer = df_StarTech_designation_à_charger.index
liste_des_refs_à_integrer
```

## 4. Création du fichier afin de comparaison
```python
df_pour_comparaison = df_Export_ProductsList_StarTech.loc[liste_des_refs_à_integrer]
df_pour_comparaison
```

## 5. Comparaison
```python
df_StarTech_designation_à_charger
```

### Faire en sorte que les colonnes des deux dataframe à comparer, aient les mêmes appelations
```python
df_StarTech_designation_à_charger.rename(columns={"Désignation": "Designation"}, inplace = True)

df_StarTech_designation_à_charger
```

## Comparaison des deux dataframe
```python
diff = df_StarTech_designation_à_charger.compare(df_pour_comparaison)
diff
```
