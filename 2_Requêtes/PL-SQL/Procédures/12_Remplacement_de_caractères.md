Depuis un certains moment, la nomenclature des désignations impose d'utiliser des tirets (-) à la place des virgules (,).

On a une liste de produits dont on souhaiterait améliorer les désignations. 

Dans la désignation de chaque produit, on souhaite remplacer la virgule (,) par un tiret (-).

### SQL
```sql
update table_name
set designation = replace(designation, ',', ' -')
-- where ref_interne in (...)
```

<!--
### Python
The same thing with Python/Pandas : 

Partant d'un fichier CSV avec plusieurs colonnes dont une colonne pour la réf_interne, et une autre contenant la désignation, supprimer toutes les autres colonnes.

importer Pandas

lire le fichier CSV et le récupérer dans un dataframe

supprimer les colonnes non pertinentes

éventuallement mettre la réf_interne en index

parcourir chaque élément

pour chaque élément : remplacer la virgule par le tiret

exporter le dataframe

```python
txt = "Nvidia GeForce - RTX4060, Carte graphique, vitesse processeur 2475 MHz, mémoire 8 Go GDDR6, 2 x HDMI, 2 x DisplayPort, PCI Express 4.0, Profil bas"

txt2 = txt.replace(",", " -")

print(txt)

print(txt2)
```
-->
