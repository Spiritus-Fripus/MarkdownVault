# Schéma Conceptuel Merise

## Entités

### Client

- Identifiant (PK)
- Nom
- Prénom
- Adresse

### Commande

- Numéro de commande (PK)
- Date de commande
- Montant total

### Produit

- Code produit (PK)
- Nom du produit
- Prix unitaire

## Relations

### Relation "Passer"

- Client (1, N) <------> (0, N) Commande <------> (1, N) Produit
  - Quantité commandée

Dans cet exemple :

- Les entités sont représentées par des sections, et les attributs sont énumérés avec leur type.
- Les relations entre les entités sont représentées sous la section "Relations".

![Méthode merise](//Markdown%20Vault/Introduction%20Web/Ressources/Synoptique_Methode_Merise_2.jpg)

# Utilité de Merise

## Objectif

Merise est une méthodologie de conception qui vise à organiser et structurer les systèmes d'information.

## Principaux éléments

### Modèle Conceptuel des Données (MCD)

- Représentation des entités et de leurs relations.
- Permet de définir la structure conceptuelle de la base de données.

### Modèle Organisationnel des Données (MOD)

- Définit la structure organisationnelle des données.
- Introduit des notions telles que les vues et les traitements.

### Modèle Physique des Données (MPD)

- Détaille la manière dont les données sont stockées physiquement.
- Définit les tables, les index, etc.

## Avantages

- Clarifie la structure des données.
- Facilite la communication entre les différents acteurs d'un projet.
- Guide le processus de conception depuis le concept jusqu'à l'implémentation.

## Outils Associés

- Utilisation d'outils de modélisation comme Merise Designer pour créer des schémas détaillés.
