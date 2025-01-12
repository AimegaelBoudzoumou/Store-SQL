# Modèle Logique de Données

## Principe de fonctionnement du MLD

Le MLD (Modèle Logique de Données) est une couche intermédiaire entre le modèle conceptuel de données [(MCD)](https://github.com/AimegaelBoudzoumou/Store-SQL/blob/main/1_Mod%C3%A9lisation/1_MCD.md) et la base de données.

Les entités et attributs du MCD deviennent respectivement des tables et des champs dans le MLD.

Les associations ayant la cardinalité max N,N se transforment en tables.

Lorsqu'une association reliant deux éléments A et B, possède la cardinalité max 1,N (soit 1 pour A et N pour B) :

l'élément A reçoit la clé primaire de l'élément B. Cette clé primaire se transforme en clé étrangère dans A.
