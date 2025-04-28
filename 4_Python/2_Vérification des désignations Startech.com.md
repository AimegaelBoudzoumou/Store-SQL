# Vérification des désignations Startech.com

```python
## 1. Importer la librairie Pandas
import pandas as pd

## 2. Importer le fichier contenant les désignations que l'on souhaite charger

# ce tableau va être utilisé pour spécifier les colonnes à extraire du fichier de base
columns1 = ["REF interne", "Désignation"]

# création du dataframe df_StarTech_fichier_de_base
df_StarTech_designation_à_charger = pd.read_excel("Demande Intégration en masse - StarTech - 25 Mar 2025 - Copie.xlsx",
usecols = columns1)

# fixer comme index : REF interne
df_StarTech_designation_à_charger = df_StarTech_designation_à_charger.set_index("REF interne")

# appel du dataframe df_StarTech_fichier_de_base
df_StarTech_designation_à_charger

## 3. Importer le fichier affichant la situation de la BDD
# Export depuis TMS
df_Export_ProductsList_StarTech = pd.read_excel("ProductsList_StarTech.xlsx", usecols = ["[FR.REPORTING.PRODUCTSLIST.INTERNAL_REF]", "Designation"])

df_Export_ProductsList_StarTech = df_Export_ProductsList_StarTech.set_index("[FR.REPORTING.PRODUCTSLIST.INTERNAL_REF]")

df_Export_ProductsList_StarTech

liste_des_refs_à_integrer = df_StarTech_designation_à_charger.index
liste_des_refs_à_integrer

## 4. Création du fichier afin de comparaison
df_pour_comparaison = df_Export_ProductsList_StarTech.loc[liste_des_refs_à_integrer]
df_pour_comparaison

## 5. Comparaison
df_StarTech_designation_à_charger

### Faire en sorte que les colonnes des deux dataframe à comparer, aient les mêmes appelations
df_StarTech_designation_à_charger.rename(columns={"Désignation": "Designation"}, inplace = True)

df_StarTech_designation_à_charger

"""
### Supprimer les éventuelles espaces autour des textes
# df["Last_Name"] = df["Last_Name"].str.strip("123._/")
#df_StarTech_designation_à_charger["Designation"] = df_StarTech_designation_à_charger["Designation"].str.strip()
#df_pour_comparaison["Designation"] = df_pour_comparaison["Designation"].str.strip()
"""

### Comparaison des deux dataframe
diff = df_StarTech_designation_à_charger.compare(df_pour_comparaison)
diff


```
