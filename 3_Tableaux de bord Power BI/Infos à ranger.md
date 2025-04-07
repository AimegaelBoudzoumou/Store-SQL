Différentes approches de collecte de données.

1- Export du fichier Excel (depuis l'interface de notre logiciel) contenant tous les produits de la base de données. Ensuite traiter ce fichier sous Power BI.

2- Ecrire les requêtes SQL permettant de réaliser les KPIs sur les produits du site e-commerce. 

Reporting

Mettre ici le tableaux des KPIs pour :

- analyste descriptive
- analyse de tendance

Liste des 20 fabricants/marques ayant enregistrés le plus/moins de ventes sur ces périodes 

Le mois, le trimestre, le semestre, l’année

Reporting  

Pour un fabricant donné : les catégories ayant enregistrés le plus/moins de ventes sur ces périodes : Le mois, le trimestre, le semestre, l’année

Reporting  

Pour un fabricant donné : les gammes ayant enregistrés le plus/moins de ventes sur ces périodes : Le mois, le trimestre, le semestre, l’année

Reporting  

Parmi toutes les marques (fabricants) d’un acheteur : lesquels enregistrent les meilleurs/pires ventes

Reporting  

Etablir des stats sur chacune de ces périodes : le mois dernier, les 3 trois derniers mois, les 6 derniers mois, les 12 derniers mois

Groupe 1 : 
- nombre de produits crées 
- nombre de produits crées par marque
- nombre de produits crées par marque et gamme
- nombre de produits crées par catégorie

Note : 
- exploiter les fonctions : MIN, MAX, SUM, AVG, YEAR, SUBSTRING, CTE, RANK, DENSE_RANK (cf. vidéo ci-dessous vers 28min10
- possiblilité de les classer par : ordre alphabétique, les plus créés, les moins créés, etc.
- afficher les résultats avec __over__ pour afficher chaque sous-total (ex. voir cette vidéo, vers 18min48 : https://www.youtube.com/watch?v=QYd-RtK58VQ&list=PLUaB-1hjhk8FE_XZ87vPPSfHqb6OcM0cF&index=20)

Reporting : 

1/ Requêtes de Reporting mensuel :

- nombre et liste des produits créés sur le dernier mois

- nombre de produits créés par fabricants/marque, par gamme, par catégorie, par type

- Classement des produits qui ont été le plus créés (par fabricant, par gamme, par catégorie, par type) et le moins créés (par fabricant, par gamme, par catégorie, par type)

2/ Requêtes de Reporting trimestiel : 

reproduire les stats ci-dessus, mais cette fois ci sur les 3 derniers mois

3/ Requêtes de Reporting semestriel : 

reproduire les stats ci-dessus, mais cette fois ci sur les 6 derniers mois

4/ Requêtes de Reporting semestriel : 

reproduire les stats ci-dessus, mais cette fois ci sur les 12 derniers mois

5/ Requêtes de Reporting pour chaque semaine du dernier mois : 

reproduire les stats ci-dessus, mais cette fois ci par semaine sur le dernier mois. Cela permet par exemple de savoir au quel de quel semaine il y a eu le plus de ventes/création de produits.

Il pourrait être intéressant de faire un rapport pour les 4 semaines, pour chaque mois dans l'année (le tout ensemble)

Autres indicateurs : 
- nombre total de produits créés dans le mois
- moyenne des produits créés par jours, par semaine
- Total des produits par marque

- Recherches : comment choisir le bon visuel (barre, histogramme, etc.)


Exemple de réalisations : 

__Window Functions__

![image](https://github.com/user-attachments/assets/aa1df12f-4763-49f1-95a1-ef7c1371e1cc)

__DENSE_RANK__

![image](https://github.com/user-attachments/assets/f8626dc9-8eb4-4635-8948-eb84265e6f21)

### Les 10 produits les plus performants
- de façon générale
- par marque/fabricant
- par gamme
- par catégorie
- par marque/fabricant et catégorie
- par type

### Le nombre de produits créés
- de façon générale
- par marque/fabricant
- par gamme
- pa catégorie
- par marque/fabricant et catégorie
- par type

![image](https://github.com/user-attachments/assets/26f43553-7760-4245-8c91-40ecdffc44e3)



Aujourd'hui.

Hier.

Les 7 derniers jours.

Les 28 derniers jours (par défaut).

Les 30 derniers jours.

Les 90 derniers jours.

Les 12 derniers mois.

La dernière année civile.

Cette année depuis le 1ᵉʳ janvier.

Comparer deux périodes entre elles

#### Situation des créas en fonction de la période dans le mois (1ère ou 2ième quizaine du mois) : 

![image](https://github.com/user-attachments/assets/09d3c217-99bc-4a51-8fa9-a1ea8130a009)

![image](https://github.com/user-attachments/assets/b0e2e087-61e2-4898-ab75-f31b8d2301bc)

<!--
#### Important : rapport sur les redescente automatique de contenu C|Net (Descritption, Visuel, Spécs) quand ce contenu est pourtant dispo.
Par marque, catégorie, gamme, etc. (à définir) : comparer les données (pop-up C|Net) côté C|Net et celles côté TMS. Si les données C|Net sont présentes et différentes de celles côté TMS, cela signifie que la redescente ne se fait pas automatiquement. Alors il faut récuperer les réfs (ref_interne, fabricant, catégorie, gamme, etc) concernées et investiguer. l'investigation débute par une regroupement des produits selon les critères : marque, catégorie, gamme
-->

