# Brief-PostegreSQL

![Brief_main_title](assets/img/Brief_title_last.png)

![border](assets/border/cadre_white_b.png)

![border](assets/line/pink_point_line_r.png)

# Sommaire

- [Cardinalités](#cardinalités)
- [Objectif et Consignes](#objectif-et-consignes)

# Navigation

- [Diagrammes MCD MLD](./doc/diagrammes.md)
- [Règles de gestion](doc/regles-gestion.md)

![border](assets/line/pink_point_line_r.png)

# Merise Définition

Merise est une méthode française d'analyse et de conception des systèmes d'information, développée à la fin des années 1970. Le nom "Merise" n'est pas un acronyme, mais certains ont proposé des interprétations telles que

- "Méthode d'Étude et de Réalisation Informatique pour les Systèmes d'Entreprise"

- Cependant, ces interprétations ne sont pas officielles. Le nom "Merise" a été choisi en référence au merisier,

- « qui ne peut porter de beaux fruits que si on lui greffe une branche de cerisier : ainsi en va-t-il des méthodes informatiques bien conçues, qui ne produisent de bons résultats que si la greffe sur l'organisation réussit »

![border](assets/line/pink_point_line_r.png)

# Cardinalités

![border](assets/line/green_point_line_l.png)

### Relation Utilisateur / Commande ↔ is ordered by

- #### Cardinalité Users (0,n) → is ordered by :

  Un utilisateur peut passer zéro ou plusieurs commandes. Autrement dit, un utilisateur a la possibilité d’entrer dans un magasin et de ne rien acheter, mais il peut aussi passer plusieurs commandes s'il le souhaite.

- #### Cardinalité Orders (1,1) → is ordered by :

  Une commande doit être passée par un seul utilisateur. Cela signifie que chaque commande a un utilisateur unique associé, tout comme un ticket de caisse appartient à un seul client et ne peut pas être partagé entre plusieurs clients.

### Relation Commande / Produit ↔ belong

- #### Cardinalité Orders (1,n) → belong :

  Une commande doit contenir au moins un produit et peut en contenir plusieurs. En d’autres termes, une commande ne peut pas être vide ; elle doit comporter au moins un produit, mais peut également en inclure plusieurs.

- #### Cardinalité Products (0,n) → belong :

  Un produit peut ne faire partie d'aucune commande, ou être présent dans plusieurs commandes. Par exemple, un produit en stock peut ne pas avoir encore été commandé, mais il peut aussi être inclus dans plusieurs commandes si plusieurs clients l'achètent.

![border](assets/line/green_point_line_l.png)

   <a href="#sommaire">
  <img src="assets/button/back_to_top.png" alt="Home page" style="width: 150px; height: auto;">
  </a>

![border](assets/line/pink_point_line_r.png)

# Objectif et Consignes

![border](assets/line/green_point_line_l.png)

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

---

<a href="#sommaire">
  <img src="assets/button/back_to_top.png" alt="Home page" style="width: 150px; height: auto;">
</a>

![border](assets/line/green_point_line_l.png)

## Votre Mission Consiste à :

![border](assets/line/green_point_line_l.png)

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

![border](assets/line/green_point_line_l.png)

<a href="#sommaire">
  <img src="assets/button/back_to_top.png" alt="Home page" style="width: 150px; height: auto;">
</a>

![border](assets/line/pink_point_line_l.png)
