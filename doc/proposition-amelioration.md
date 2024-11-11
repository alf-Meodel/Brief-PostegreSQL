 <a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)

# Propositions d'amélioration

![border](../assets/line/line_pink_point_r.png)

Sans remettre en cause la qualité indéniable de la conception de votre site e-commerce, voici une série de suggestions visant à optimiser la gestion et la sécurité de votre base de données.

### Correction de la Colonne "deliver_atO"

La colonne "deliver_atO" contient une coquille ("O" à la fin) et pourrait être renommée en "delivery_date" pour indiquer plus clairement la date de livraison.

### Table des Utilisateurs

Séparation du Nom et Prénom
Actuellement, le site regroupe nom et prénom des utilisateurs dans un champ unique appelé "username". Il serait plus clair de séparer ces informations pour une gestion facilitée des utilisateurs.

### Unicité des Pseudonymes

Pour éviter les doublons de pseudonymes, il serait utile de définir une contrainte d'unicité dans la colonne "user_pseudo", afin que chaque utilisateur ait un pseudo unique.

### Ajout d'une Colonne Email

Inclure une colonne "user_email" permettrait de recueillir les adresses email des utilisateurs, facilitant ainsi l'envoi de notifications de commande et de promotions commerciales.

### Renommage de la Colonne "created_at"

Dans plusieurs tables, la colonne "created_at" existe pour enregistrer la date de création de chaque entrée. Afin d'éviter toute confusion, il serait préférable de la renommer spécifiquement, comme par exemple "account_creation_date" dans la table des utilisateurs.

### Table des Commandes
Renommage de la Colonne "created_at"
Pour plus de clarté, renommer la colonne "created_at" dans cette table en "order_date" faciliterait l’identification de la date de commande.

### Table des Produits
Renommage de la Colonne "created_at"
Afin d'éviter les ambiguïtés, il serait pertinent de renommer "created_at" par "product_added_date" pour indiquer clairement la date d'ajout du produit.

![border](../assets/line/line_teal_point_l.png)

<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>
<a href="#règles-de-gestion">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_r.png)
