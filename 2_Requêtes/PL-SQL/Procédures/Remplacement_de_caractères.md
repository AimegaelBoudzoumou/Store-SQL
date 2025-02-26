On a une liste de produits. Dans la désignation de chaque produit, on souhaite remplacer la virgule (,)par un tiret (-).

### SQL
```sql
SELECT REPLACE('Hello tout le monde', 'Hello', 'Bonjour');
INTO...
```

The same thing with Python ! Just for joke

```python
txt = "Nvidia GeForce - RTX4060, Carte graphique, vitesse processeur 2475 MHz, mémoire 8 Go GDDR6, 2 x HDMI, 2 x DisplayPort, PCI Express 4.0, Profil bas"

txt2 = txt.replace(",", " -")

print(txt)

print(txt2)
```
