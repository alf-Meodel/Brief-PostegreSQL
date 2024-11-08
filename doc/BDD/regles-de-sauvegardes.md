# Documentation : Sauvegardes Automatiques de Base de Données avec Cron

Cette documentation explique comment configurer une tâche cron pour effectuer des sauvegardes automatiques de votre base de données en utilisant pg_dump. Ce guide est destiné aux utilisateurs de PostgreSQL, mais peut être adapté pour d’autres bases de données.

## Commande Cron pour pg_dump

La commande suivante permet de créer des sauvegardes automatiques de votre base de données en utilisant pg_dump dans une tâche cron.

```
* * * * * pg_dump -h localhost -p 5432 -U (ton_nom_d'utilisateur) -F c (nom_de_ta_bdd) > (ton_chemin_d'accès)
```

## Explication de la Commande

- `* * * * *` : Définit l’intervalle de temps pour exécuter la commande.
- pg_dump : Utilitaire PostgreSQL pour réaliser une sauvegarde de la base de données.
  - `-h localhost` : Définit l’hôte de la base de données (localhost pour la machine locale).
  - `-p 5432` : Spécifie le port PostgreSQL (par défaut : 5432).
  - `-U (ton_nom_d'utilisateur)` : Nom d’utilisateur pour se connecter à la base de données.
  - `-F c `: Format de sortie c (format de sauvegarde personnalisé de PostgreSQL).
  - `(nom_de_ta_bdd)` : Nom de la base de données à sauvegarder.
  - `>` : Redirection de la sortie vers un fichier.
  - `(ton_chemin_d'accès)` : Chemin où enregistrer le fichier de sauvegarde (par ex., /backups/backup.sql).

## Exemple de Commande

Si vous souhaitez sauvegarder une base de données nommée my_database avec l'utilisateur db_user et stocker le fichier dans /backups/my_database_backup.sql, la commande sera :

```
* * * * * pg_dump -h localhost -p 5432 -U db_user -F c my_database > /backups/my_database_backup.sql

```

## Explication des Étoiles dans Cron

Les cinq étoiles dans la syntaxe cron déterminent la fréquence d’exécution de la commande. Voici la signification de chaque position :

| Position | Symbole | Description                | Exemple                 |
| -------- | ------- | -------------------------- | ----------------------- |
| 1ère     | `*`     | Minutes (0 - 59)           | `0` pour 0 min          |
| 2e       | `*`     | Heures (0 - 23)            | `2` pour 2h du matin    |
| 3e       | `*`     | Jour du mois (1 - 31)      | `15` pour le 15 du mois |
| 4e       | `*`     | Mois (1 - 12)              | `6` pour juin           |
| 5e       | `*`     | Jour de la semaine (0 - 7) | `1` pour lundi          |
