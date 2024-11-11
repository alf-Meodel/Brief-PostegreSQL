<a href="/README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
  </a>

![border](../assets/line/border_r.png)

# Sécuriser la Base de données

![border](../assets/line/line_teal_point_r.png)

# Sommaire

- [Les Extensions](#les-extensions)
- [Fonction pour hacher les mots de passe](#fonction-pour-hacher-les-mots-de-passe)
- [Création du Trigger pour hacher le mot de passe](#création-du-trigger-pour-hacher-le-mot-de-passe)
- [Fonction pour mettre à jour automatiquement le champ updated_at](#fonction-pour-mettre-à-jour-automatiquement-le-champ-updated_at)
- [Attribution des privilèges au rôle manager](#attribution-des-privilèges-au-rôle-manager)

![border](../assets/line/border_b.png)

![border](../assets/line/line_pink_point_l.png)

# Les Extensions

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
