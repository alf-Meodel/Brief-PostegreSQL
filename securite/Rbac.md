<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
  </a>

![border](../assets/line/border_r.png)

# Role-Based Access Control

![border](../assets/line/line_teal_point_r.png)

# Sommaire

- [Introduction](#introduction)
- [RBAC](#rbac)

![border](../assets/line/border_b.png)

# Introduction

![border](../assets/line/line_pink_point_l.png)

- Ce modèle de contrôle d'accès basé sur les rôles (RBAC) définit les permissions accordées aux visiteurs et utilisateurs enregistrés de l'application.

- Il établit des règles claires pour l'accès et la gestion des informations personnelles, des commandes et des produits :

```
Les visiteurs peuvent consulter le catalogue et créer un compte, tandis que les utilisateurs enregistrés disposent de droits supplémentaires, tels que la gestion de leurs commandes et l'accès aux informations de livraison.
```

- Ce système permet de protéger les données sensibles tout en offrant une expérience utilisateur fluide et sécurisée

# RBAC

![border](../assets/line/line_pink_point_l.png)

| Rôle        | Permission                          | Description                              |
| ----------- | ----------------------------------- | ---------------------------------------- |
| Visiteur    | Se connecter                        | Accès à l'interface sans compte          |
|             | Créer un compte                     | Enregistrement d'un nouveau compte       |
|             | Voir les produits                   | Accès au catalogue de produits           |
| Utilisateur | Se connecter                        | Accès avec un compte                     |
|             | Voir ses propres informations       | Visualiser les informations personnelles |
|             | Modifier ses propres informations   | Modifier ses informations personnelles   |
|             | Créer une commande                  | Passer une commande                      |
|             | Voir ses propres commandes          | Accéder à l'historique de ses commandes  |
|             | Modifier ses propres commandes      | Modifier une commande avant validation   |
|             | Confirmer une commande              | Confirmer une commande pour livraison    |
|             | Commander un produit (si stock > 0) | Ajouter un produit au panier             |
|             | Voir les informations de livraison  | Accéder aux informations de livraison    |

![border](../assets/line/line_pink_point_l.png)

<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
  </a>
<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)
