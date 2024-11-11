 <a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)

# MCD et MLD

![border](../assets/line/line_pink_point_l.png)

# Sommaire

- [Merise Définition](#merise-définition)
- [Modèle Conceptuel de Données](#modèle-conceptuel-de-données)
  - [Entités & Relations](#entités)
  - [Modèle Logique de Données](#modèle-logique-de-données)
  - [Tables & Relations](#tables)
  - [Cardinalités](#cardinalités)

# Diagrammes

- [Diagrammes](../doc/diagrammes.md)

![border](../assets/line/border_b.png)

# Merise Définition

![border](../assets/line/line_pink_point_r.png)

Merise est une méthode française d'analyse et de conception des systèmes d'information, développée à la fin des années 1970. Le nom "Merise" n'est pas un acronyme, mais certains ont proposé des interprétations telles que

- "Méthode d'Étude et de Réalisation Informatique pour les Systèmes d'Entreprise"

- Cependant, ces interprétations ne sont pas officielles. Le nom "Merise" a été choisi en référence au merisier,

- « qui ne peut porter de beaux fruits que si on lui greffe une branche de cerisier : ainsi en va-t-il des méthodes informatiques bien conçues, qui ne produisent de bons résultats que si la greffe sur l'organisation réussit »

<a href="#diagrammes">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_teal_point_l.png)

## Modèle Conceptuel de Données

![border](../assets/line/line_teal_point_r.png)

- Le MCD est le premier niveau de conception d'une base de données. Il vise à représenter les données de manière conceptuelle, sans se préoccuper de la structure informatique finale. Ce modèle permet de visualiser les entités principales et les relations entre elles.

<a href="#diagrammes">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_teal_point_l.png)

# Entités

![border](../assets/line/line_teal_point_r.png)

### Users :

Cette entité représente les utilisateurs. Elle possède les attributs

- user_pseudo,
- username,
- user_password,
- created_at.

---

### Products :

Elle représente les produits avec les attributs

- product_name,
- product_description,
- product_price,
- product_quantity,
- created_at,
- updated_at.

---

### Orders :

Elle représente les commandes avec les attributs

- order_total_cost_ht,
- order_total_quantity,
- created_at,
- deliver_at,
- une clé étrangère user_UUID **pour lier une commande à un utilisateur.**

![border](../assets/line/line_teal_point_l.png)

# Relations :

![border](../assets/line/line_teal_point_r.png)

### is ordered by :

La relation entre Users et Orders est de type 1,n, signifiant qu'un utilisateur peut passer plusieurs commandes, mais une commande est liée à un seul utilisateur.

### belong :

La relation entre Orders et Products est de type n,n, ce qui signifie qu'une commande peut contenir plusieurs produits et qu'un produit peut être présent dans plusieurs commandes.

<a href="#diagrammes">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_teal_point_l.png)

## Modèle Logique de Données

![border](../assets/line/line_teal_point_r.png)

- Le MLD est une représentation du MCD adaptée aux contraintes des bases de données relationnelles. Ce modèle prend en compte la structure des tables, les clés primaires, les clés étrangères et les relations entre les tables.

![border](../assets/line/line_teal_point_l.png)

# Tables

![border](../assets/line/line_teal_point_r.png)

### Users :

La table contient user_UUID comme clé primaire,
et les colonnes

- user_pseudo,
- username,
- user_password,
- created_at.

---

### Products :

La table contient product_UUID comme clé primaire et des colonnes pour

- product_name,
- product_description,
- product_price,
- product_quantity,
- created_at,
- updated_at

---

### Orders :

La table contient order_number comme clé primaire et les colonnes

- order_total_cost_ht,
- order_total_quantity,
- created_at,
- deliver_at,
- une clé étrangère user_UUID **qui fait référence à la table Users.**

<a href="#diagrammes">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_teal_point_l.png)

# Relations :

![border](../assets/line/line_teal_point_r.png)

is ordered by : La relation est représentée par une clé étrangère user_UUID dans la table Orders, pour indiquer que chaque commande est passée par un utilisateur.
belong : La relation entre Orders et Products est gérée par une table d'association belong, avec deux clés étrangères product_UUID et order_number, qui relient les produits aux commandes dans une relation de type n,n.

<a href="#diagrammes">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_teal_point_r.png)

# Cardinalités

![border](../assets/line/line_teal_point_l.png)

## Relation Utilisateur / Commande ↔ is ordered by

- #### Cardinalité Users (0,n) → is ordered by :

  Un utilisateur peut passer zéro ou plusieurs commandes. Autrement dit, un utilisateur a la possibilité d’entrer dans un magasin et de ne rien acheter, mais il peut aussi passer plusieurs commandes s'il le souhaite.

- #### Cardinalité Orders (1,1) → is ordered by :

  Une commande doit être passée par un seul utilisateur. Cela signifie que chaque commande a un utilisateur unique associé, tout comme un ticket de caisse appartient à un seul client et ne peut pas être partagé entre plusieurs clients.

## Relation Commande / Produit ↔ belong

- #### Cardinalité Orders (1,n) → belong :

  Une commande doit contenir au moins un produit et peut en contenir plusieurs. En d’autres termes, une commande ne peut pas être vide ; elle doit comporter au moins un produit, mais peut également en inclure plusieurs.

- #### Cardinalité Products (0,n) → belong :

  Un produit peut ne faire partie d'aucune commande, ou être présent dans plusieurs commandes. Par exemple, un produit en stock peut ne pas avoir encore été commandé, mais il peut aussi être inclus dans plusieurs commandes si plusieurs clients l'achètent.

![border](../assets/line/line_pink_point_l.png)

<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a><a href="#diagrammes">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)
