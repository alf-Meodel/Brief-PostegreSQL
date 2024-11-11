 <a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)

# Mise en place de la base de données

![border](../assets/line/line_pink_point_r.png)

# Sommaire

- [Premier pas](#premier-pas)

![border](../assets/line/border_b.png)

![border](../assets/line/line_pink_point_l.png)

# Premier pas :

![border](../assets/line/line_teal_point_r.png)

### Avec pgcli

- Ouvrez votre terminal (Invite de commandes ou PowerShell) et connectez-vous en tant que super utilisateur PostgreSQL, généralement postgres :

```
pgcli -U postgres
```

### Avec psql

- Ouvrez l’Invite de commandes (ou PowerShell) et connectez-vous avec psql :

```
psql -U postgres
```

### Créer la base de données "aubondeal"

```
CREATE DATABASE aubondeal;
```

_Si la commande réussit, vous verrez un message de confirmation indiquant CREATE DATABASE_

### Vérifier la création de la base de données

- Pour vérifier que la base de données aubondeal a été créée, vous pouvez lister les bases de données avec la commande suivante :

```
\l
```

- Cela affichera toutes les bases de données existantes, avec aubondeal.

```
+------------+----------+----------+--------------------+--------------------+-----------------------+
| Name       | Owner    | Encoding | Collate            | Ctype              | Access privileges     |
|------------+----------+----------+--------------------+--------------------+-----------------------|
| aubondeal  | postgres | UTF8     | French_France.1252 | French_France.1252 | <null>                |
| helloworld | postgres | UTF8     | French_France.1252 | French_France.1252 | <null>                |

```

### Se connecter à la base de données aubondeal

- Pour commencer à utiliser la base de données nouvellement créée, connectez-vous à celle-ci en utilisant la commande suivante :

```
\c aubondeal
```

- Si la connexion est réussie, vous verrez un message de confirmation indiquant ceci

```
postgres@(none):postgres> \c aubondeal
You are now connected to database "aubondeal" as user "postgres"
```

![border](../assets/line/line_teal_point_l.png)

<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>
<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_r.png)
