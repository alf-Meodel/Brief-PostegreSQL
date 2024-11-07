<a href="/README.md">
  <img src="/assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
  </a>

![border](/assets/line/green_point_line_l.png)

<!-- ![border](../assets/line/pink_point_line_l.png) -->

# Dictionnaire de Données

![border](/assets/line/green_point_line_l.png)

# Sommaire

- [Définition](#définition)
- [Le Dictionnaire de données](#le-dictionnaire-de-données)
  - [Table Users](#table-users)
  - [Table Products](#table-users)
  - [Table Orders](#table-users)
  - [Table belong (Table d’association entre Orders et Products)](#table-users)

![border](/assets/line/pink_point_line_l.png)

## Définition

Un dictionnaire de données est un document essentiel dans la conception et la gestion de bases de données, car il décrit les structures de données d'une manière standardisée et compréhensible. Voici ses principales utilités :

## Documentation et Communication

Le dictionnaire de données liste et explique chaque table, colonne, type de donnée, et relation dans la base de données.
Il sert de référence pour les développeurs, analystes, et autres parties prenantes, facilitant la compréhension de la structure des données sans devoir analyser directement le code ou les tables SQL.

## Standardisation et Cohérence

En précisant les noms des colonnes, types de données, et contraintes, le dictionnaire aide à maintenir des conventions de nommage et des standards de données.
Il garantit une utilisation uniforme des termes et types, réduisant le risque d’erreurs dues à des incohérences.

## Support au Développement et à la Maintenance

Le dictionnaire de données sert de guide pour le développement de requêtes SQL, les ajouts ou modifications de tables, et la maintenance de la base de données.
En cas de changement, les développeurs peuvent consulter le dictionnaire pour comprendre l’impact potentiel sur d’autres parties du système.

## Aide à l’Intégrité des Données

En définissant les clés primaires, clés étrangères, et les relations, le dictionnaire joue un rôle clé dans l’assurance de l’intégrité référentielle.
Il spécifie également les contraintes sur les données (ex., pas de valeurs nulles, formats de données), ce qui garantit la qualité des données stockées.

## Support aux Testeurs et Analystes

Les équipes de test et d’analyse peuvent s’appuyer sur le dictionnaire de données pour comprendre les structures qu’elles doivent vérifier ou analyser, ce qui aide à établir des plans de test efficaces et à interpréter les résultats.

![border](/assets/line/pink_point_line_l.png)

# Le Dictionnaire de données

![border](/assets/line/pink_point_line_l.png)

## Table Users

| Nom de la colonne | Type de donnée | Description                                         |
| ----------------- | -------------- | --------------------------------------------------- |
| user_UUID         | UUID           | Identifiant unique de l’utilisateur (clé primaire)  |
| user_pseudo       | VARCHAR(50)    | Pseudonyme de l’utilisateur                         |
| username          | VARCHAR(50)    | Nom complet de l’utilisateur                        |
| user_password     | VARCHAR(255)   | Mot de passe de l’utilisateur, sécurisé par hachage |
| created_at        | TIMESTAMP      | Date et heure de création de l’utilisateur          |

## Table Products

| Nom de la colonne   | Type de donnée | Description                                         |
| ------------------- | -------------- | --------------------------------------------------- |
| product_UUID        | UUID           | Identifiant unique du produit (clé primaire)        |
| product_name        | VARCHAR(100)   | Nom du produit                                      |
| product_description | TEXT           | Description détaillée du produit                    |
| product_price       | DECIMAL(10, 2) | Prix unitaire du produit                            |
| product_quantity    | INTEGER        | Quantité de produit disponible                      |
| created_at          | TIMESTAMP      | Date et heure de création du produit                |
| updated_at          | TIMESTAMP      | Date et heure de la dernière mise à jour du produit |

## Table Orders

| Nom de la colonne    | Type de donnée | Description                                                                                 |
| -------------------- | -------------- | ------------------------------------------------------------------------------------------- |
| order_number         | UUID           | Identifiant unique de la commande (clé primaire)                                            |
| order_total_cost_ht  | DECIMAL(10, 2) | Coût total hors taxes de la commande                                                        |
| order_total_quantity | INTEGER        | Quantité totale de produits dans la commande                                                |
| created_at           | TIMESTAMP      | Date et heure de création de la commande                                                    |
| deliver_at           | DATE           | Date de livraison prévue de la commande                                                     |
| user_UUID            | UUID           | Identifiant de l’utilisateur ayant passé la commande (clé étrangère vers `Users.user_UUID`) |

## Table belong (Table d’association entre Orders et Products)

| Nom de la colonne | Type de donnée | Description                                                           |
| ----------------- | -------------- | --------------------------------------------------------------------- |
| order_number      | UUID           | Identifiant de la commande (clé étrangère vers `Orders.order_number`) |
| product_UUID      | UUID           | Identifiant du produit (clé étrangère vers `Products.product_UUID`)   |

![border](/assets/line/pink_point_line_l.png)

<a href="../README.md">
  <img src="/assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>
<a href="#dictionnaire-de-données">
  <img src="/assets/button/back_to_top.png" alt="summary" style="width: 150px; height: auto;">
</a>

![border](/assets/line/pink_point_line_l.png)
