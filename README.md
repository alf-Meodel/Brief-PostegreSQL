# Brief-PostegreSQL

![Brief_main_title](assets/img/Brief_title_last.png)

![border](assets/design/border/cadre_white_b.png)

# Sommaire

- [Diagrammes](#diagrammes)
- [Objectif et Consignes](#objectif-et-consignes)

# Navigation

- [Règles de gestion](/Brief-PostegreSQL/doc/regles-gestion.md)

![border](assets/design/line/pink_point_line_r.png)

<!-- <details> -->

<!-- <summary><strong style="font-size: 1.5em; font-weight: bold">Consignes  :</strong></summary> -->

# Diagrammes

![border](assets/design/line/pink_point_line_l.png)

### MCD - Modèle Conceptuel de Données

- Le MCD est le premier niveau de conception d'une base de données. Il vise à représenter les données de manière conceptuelle, sans se préoccuper de la structure informatique finale. Ce modèle permet de visualiser les entités principales et les relations entre elles.

---

### Cardinalités Explication

![border](assets/design/line/pink_point_line_l.png)

## Relation utilisateur/commande

- **Users 0,n > is ordered by :**

  Cette cardinalité signifie qu'un utilisateur peut passer zéro ou plusieurs commandes

- **Orders 1,1 > is ordered by :**

  Chaque commande est associée à un seul utilisateur, et il est obligatoire pour une commande d'avoir un utilisateur.

## Relation commande/produit

- **1,n Orders > belong(appartenir) :**

  Cela signifie qu'une commande (Orders) doit contenir au moins un produit et peut en contenir plusieurs.
  **Cela reflète le fait qu'une commande ne peut pas exister sans produits** (au moins un produit est requis), et elle peut contenir de nombreux produits.

- **Cardinalité 0,n partant de Products vers belong :**

  Cette cardinalité signifie qu'un produit (Products) peut être inclus dans aucune, une, ou plusieurs commandes (Orders).
  **Un produit peut ne pas encore être commandé (d'où le 0), mais il peut aussi faire partie de plusieurs commandes.**

---

![Brief_main_title](assets/img/first_mcd.png)

![border](assets/design/line/pink_point_line_l.png)

### MLD - Modèle Logique de Données

- Le MLD est une représentation du MCD adaptée aux contraintes des bases de données relationnelles. Ce modèle prend en compte la structure des tables, les clés primaires, les clés étrangères et les relations entre les tables.

![Brief_main_title](assets/img/first_mld.png)

![border](assets/design/line/pink_point_line_l.png)

<a href="#sommaire">
  <img src="assets/design/button/back_to_top.png" alt="Home page" style="width: 150px; height: auto;">
</a>

# Objectif et Consignes

![border](assets/design/line/pink_point_line_l.png)

## Date de Livraison

Modalités pédagogiques
Travail individuel à rendre pour le **Mardi 12 Novembre 2024 9h00**

## Modalités d'évaluation

Revue de code sur GitHub : Les contributions seront analysées directement dans le dépôt pour évaluer la structure, l’optimisation et la conformité.

## Livrables

- Repo Github
- Un fichier SQL format PostgreSQL
- Des règles de gestion
- Un dictionnaire de données
- Une définition de l'acronyme MERISE dans la documentation

#### Bonus :

- Un RBAC

## Critères de performance

- Exactitude : **La transposition des modèles MCD et MLD en une base de données PostgreSQL** doit être fidèle et correcte.
- Sécurité : Une **gestion efficace des rôles et permissions** dans la base de données.
- Documentation : **Clarté et complétude de la documentation fournie**, permettant à un tiers de comprendre facilement la structure et les choix effectués.

<!-- </details> -->

<!-- <details> -->
<!-- <summary><strong style="font-size: 1.5em; font-weight: bold">Mission  :</strong></summary> -->

## Contexte du projet

Vous allez contribuer à la création de "AuBonDeal", une plateforme de commerce en ligne 🚀. Cette initiative vise à proposer une solution performante pour la gestion des transactions commerciales, la mise en relation des vendeurs et acheteurs, et la gestion des produits.

## Votre Mission Consiste à :

### Analyse des Modèles de Données :

Examiner et comprendre le Modèle Conceptuel de Données (MCD) et le Modèle Logique de - Données (MLD) fournis.
Identifier les entités, attributs et relations clés afin de préparer une implémentation cohérente.
​

### Création de la Base de Données :

Traduire le MCD et le MLD en une base de données relationnelle fonctionnelle, à l’aide du langage SQL. Définir les tables, les clés primaires et étrangères, et les contraintes d’intégrité.

### Gestion des Opérations CRUD :

- Veiller à ce que la base de données permette des opérations CRUD efficaces et sécurisées.

- Porter une attention spéciale à la performance et à la sécurité (par exemple, la gestion des rôles et des permissions).
  ​

### Exportation et Sauvegarde de la Base de Données :

Réaliser l’exportation et la sauvegarde de la base de données en utilisant les commandes SQL appropriées.
Mettre en place une politique de rétention des sauvegardes, incluant la mise en place d’un script pour la sauvegarde journalière.
Documenter la politique de rétention des sauvegardes en expliquant la fréquence des sauvegardes, la durée de conservation, et les procédures de restauration. Cette documentation doit également préciser les menaces que la politique de rétention permet de contrer.

<!-- </details> -->

<a href="#sommaire">
  <img src="assets/design/button/back_to_top.png" alt="Home page" style="width: 150px; height: auto;">
</a>

![border](assets/design/line/pink_point_line_r.png)

![border](assets/design/border/cadre_white_b.png)
