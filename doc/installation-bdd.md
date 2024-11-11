 <a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)

# Installation de la base de données

![border](../assets/line/line_pink_point_r.png)

# Sommaire

- [Prérequis](#prérequis)
- [Installation du projet](#installation-du-projet)
- [Notes/Précisions sur le code sql](#quelques-précisions-sur-le-code-sql)

  - [Primary Key Foreign Key](#primary-key-foreign-key)
  - [Cas de la table Belong](#cas-de-la-table-belong)

- [Sécurisation avancée](#sécurisation-avancée)
  - [Pgcrypto](#pgcrypto)
  - [uuid-ossp](#uuid-ossp)
  - [Fonction pour hacher les mots de passe](#fonction-pour-hacher-les-mots-de-passe)
  - [Création du Trigger pour hacher le mot de passe](#création-du-trigger-pour-hacher-le-mot-de-passe)
  - [Fonction pour mettre à jour automatiquement le champ updated_at](#uuid-ossp)

# Documents

- [Base de donnée .sql](../BDD/init_aubondeal.sql)

![border](../assets/line/border_b.png)

![border](../assets/line/line_pink_point_l.png)

# Prérequis

![border](../assets/line/line_teal_point_r.png)

## PostgreSQL installé :

Assurez-vous que PostgreSQL est installé et accessible.

## Permissions :

Avoir un accès avec un utilisateur ayant le droit de créer des bases de données (comme le superutilisateur postgres).

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_l.png)

# Installation du projet

![border](../assets/line/line_teal_point_r.png)

## Créer le fichier SQL :

[script.sql](../BDD/init_aubondeal.sql)

Copiez le script SQL fourni ci-dessus dans un éditeur de texte.
Enregistrez-le sous un nom comme init_aubondeal.sql.

## Ouvrir le terminal ou l’invite de commandes :

Sur Windows, utilisez PowerShell ou Invite de commandes.
Sur Linux ou macOS, ouvrez un terminal.

## Se connecter à PostgreSQL avec le superutilisateur :

Dans le terminal, connectez-vous à PostgreSQL en utilisant le superutilisateur postgres pour exécuter le script avec les permissions nécessaires. Utilisez psql pour cela.

```
psql -U postgres
```

Entrez le mot de passe de postgres si nécessaire.

## Importer le fichier SQL :

Exécutez la commande suivante pour importer et exécuter le fichier init_aubondeal.sql :

```
\i /chemin/vers/le/fichier/init_aubondeal.sql
```

Remplacez /chemin/vers/le/fichier/init_aubondeal.sql par le chemin réel vers votre fichier SQL.

## Exemple pour Windows :

```
\i 'C:/Users/franc/Desktop/test/init_aubondeal.sql'
```

## Vérifier la création de la base de données et des tables :

Après l'exécution du fichier, vous pouvez vérifier que la base de données, les tables et les utilisateurs ont été créés correctement.
Pour lister les bases de données :

```
\l
```

Pour voir les tables dans la base de données aubondeal :

```
\c aubondeal
\dt
```

## Tester la connexion avec l’utilisateur aubondeal_api :

Déconnectez-vous de psql en tapant \q.
Testez la connexion avec l'utilisateur aubondeal_api :

```
psql -U aubondeal_api -d aubondeal -h localhost
```

Entrez le mot de passe de aubondeal_api tel que défini dans le script.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_l.png)

# Quelques précisions sur le code sql

![border](../assets/line/line_teal_point_r.png)

## Primary Key Foreign Key

Dans la base de données, les clés primaires et clés étrangères permettent de lier les tables entre elles, établissant des relations.

- Clé primaire :

  Un champ ou une combinaison de champs qui identifie de manière unique chaque enregistrement dans une table.

- Clé étrangère :

  Un champ dans une table qui fait référence à une clé primaire d'une autre table, établissant ainsi une relation entre les deux tables.

# Cas de la table Belong

```
CREATE TABLE Belong (
    product_uuid UUID NOT NULL,
    order_number INTEGER NOT NULL,
    PRIMARY KEY (product_uuid, order_number),
    FOREIGN KEY (product_uuid) REFERENCES Products(product_uuid) ON UPDATE CASCADE,
    FOREIGN KEY (order_number) REFERENCES Orders(order_number) ON UPDATE CASCADE
);
```

- **product_uuid et order_number** sont les clés de la table Belong.

- **PRIMARY KEY** (product_uuid, order_number) :

Ici, la clé primaire est composée des deux champs product_uuid et order_number. Cela signifie qu'une combinaison unique de ces deux valeurs identifie chaque ligne dans cette table.

- **FOREIGN KEY** :

Les clés étrangères lient cette table avec les tables Products et Orders, ce qui signifie que chaque product_uuid doit exister dans Products et chaque order_number dans Orders.

- **ON UPDATE CASCADE** :

Si la valeur de la clé primaire référencée change dans la table Products ou Orders, elle est automatiquement mise à jour dans Belong.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_l.png)

# Sécurisation avancée :

![border](../assets/line/line_teal_point_r.png)

```
CREATE EXTENSION IF NOT EXISTS "pgcrypto";
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
```

## Pgcrypto

Cette extension est utilisée pour ajouter des fonctionnalités cryptographiques dans PostgreSQL, comme le hachage des mots de passe de manière sécurisée. Elle fournit des fonctions pour chiffrer et hacher des données, ce qui est essentiel pour la sécurité des informations sensibles (par exemple, les mots de passe).

## uuid ossp

Cette extension permet de générer des identifiants uniques (UUID) dans la base de données. Les UUID sont des identifiants uniques qui ne se répètent pas et sont souvent utilisés pour les clés primaires, garantissant ainsi l'unicité des enregistrements.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

## Fonction pour hacher les mots de passe

```
CREATE OR REPLACE FUNCTION hash_password() RETURNS TRIGGER AS $$
BEGIN
    NEW.user_password := crypt(NEW.user_password, gen_salt('bf'));
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;
```

- Cette fonction hash_password est utilisée pour hacher les mots de passe avant de les stocker.

- crypt(NEW.user_password, gen_salt('bf')) : La fonction crypt prend le mot de passe brut et applique un hachage sécurisé en utilisant le sel (salt) généré par gen_salt('bf'). Ici, 'bf' indique l'utilisation de l'algorithme bcrypt, qui est sécurisé pour stocker des mots de passe.

- TRIGGER : Cette fonction sera exécutée automatiquement avant chaque insertion ou mise à jour dans la table Users pour hacher le mot de passe.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

## Création du Trigger pour hacher le mot de passe

```
CREATE TRIGGER hash_user_password
BEFORE INSERT OR UPDATE OF user_password ON Users
FOR EACH ROW
EXECUTE FUNCTION hash_password();
```

- Ce trigger (déclencheur) exécute la fonction hash_password avant chaque insertion ou mise à jour du champ user_password dans la table Users.

- Cela garantit que chaque mot de passe est haché avant d'être stocké, améliorant ainsi la sécurité des mots de passe.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

## Fonction pour mettre à jour automatiquement le champ updated_at

```
CREATE OR REPLACE FUNCTION set_updated_at() RETURNS TRIGGER AS $$
BEGIN
    NEW.updated_at := NOW();
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;
```

- Cette fonction set_updated_at est utilisée pour mettre à jour automatiquement le champ updated_at à la date et heure actuelles (NOW()) lors d'une modification dans la table Products.

- Cela permet de savoir quand chaque produit a été modifié pour la dernière fois, ce qui est utile pour le suivi et l'audit des données.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

## Trigger pour mettre à jour le champ updated_at

```
CREATE OR REPLACE FUNCTION set_updated_at() RETURNS TRIGGER AS $$
BEGIN
    NEW.updated_at := NOW();
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;
```

- Ce trigger exécute la fonction set_updated_at avant chaque mise à jour sur la table Products.
- Il remplit automatiquement le champ updated_at avec la date et l'heure actuelles, permettant un suivi précis des modifications sur les produits.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

## Attribution des privilèges au rôle manager

- GRANT SELECT, INSERT, UPDATE ON TABLE Users, Orders, Products, Belong TO manager;
- REVOKE UPDATE ON TABLE Users, Orders, Products, Belong FROM PUBLIC;
- GRANT CONNECT ON DATABASE aubondeal TO manager;
- GRANT USAGE ON SCHEMA public TO manager;

![border](../assets/line/line_teal_point_l.png)

<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>
<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_r.png)
