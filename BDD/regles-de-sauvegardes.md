<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
  </a>

![border](../assets/line/border_r.png)

# Documentation : Règles de sauvegarde

# Sommaire

- [Sauvegardes Automatiques avec Cron](#sauvegardes-automatiques-de-base-de-données-avec-cron)
  - [Presentation](#presentation)
  - [Mise en place ](#mise-en-place)
  - [Planifier la sauvegarde avec cron ](#planifier-la-sauvegarde-avec-cron)
  - [Plusieurs cas de sauvegardes ](#plusieurs-cas-de-sauvegardes)
  - [Explication des Étoiles dans Cron](#explication-des-étoiles-dans-cron)
  - [Vérifier les sauvegardes](#vérifier-les-sauvegardes)
  - [Tester le script](#tester-le-script)
  - [Supprimer les sauvegardes automatiques](#supprimer-les-sauvegardes-automatiques)
  - [Vérification de la suppression ](#vérification-de-la-suppression)
- [Pg_Dump !! ](#pg_dump)
  - [Pourquoi l'utiliser](#pourquoi-utiliser-pg_dump)
  - [Sauvegardes automatiques avec pg_dump ](#sauvegardes-automatiques-avec-pg_dump)

![border](../assets/line/border_b.png)

## Sauvegardes Automatiques de Base de Données avec Cron

![border](../assets/line/line_teal_point_l.png)

## Presentation

Cette documentation explique comment configurer une tâche cron pour effectuer des sauvegardes automatiques de votre base de données en utilisant pg_dump. Ce guide est destiné aux utilisateurs de PostgreSQL, mais peut être adapté pour d’autres bases de données.

![border](../assets/line/line_pink_point_l.png)

# Mise en place

![border](../assets/line/line_pink_point_r.png)

## Préparer un répertoire pour les sauvegardes

- Nous allons créer un répertoire dédié aux sauvegardes pour une meilleure organisation.

```
mkdir -p ~/backups
```

## Créer un script de sauvegarde

- Créez un script qui effectuera la sauvegarde. **Ce script copiera le fichier init_aubondeal.sql** dans le dossier de sauvegarde **avec une date dans le nom pour les versions successives.**

- Ouvrez un éditeur pour créer le script de sauvegarde, **par exemple backup_script.sh** :

```
nano ~/backup_script.sh
```

## Dans le fichier, ajoutez les lignes suivantes :

```
#!/bin/bash
# Répertoire de sauvegarde
BACKUP_DIR=~/backups
# Nom du fichier SQL original
FILE_TO_BACKUP=~/chemin/vers/init_aubondeal.sql
# Nom de la sauvegarde avec la date
BACKUP_NAME="init_aubondeal_$(date +%Y%m%d%H%M%S).sql"
# Copier le fichier dans le répertoire de sauvegarde
cp "$FILE_TO_BACKUP" "$BACKUP_DIR/$BACKUP_NAME"

```

- Sauvegardez le fichier, puis fermez l'éditeur.
- En suite nous allons rendre le script exécutable :

```
chmod +x ~/backup_script.sh
```

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="sommaire" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_l.png)

# Planifier la sauvegarde avec cron

![border](../assets/line/line_pink_point_r.png)

Ouvrez le planificateur de tâches cron en éditant la crontab :

```
crontab -e
```

- ce qui (comme c'est la première fois que je l'utilise) nous emmene vers la selection suivante afin de chosir notre editeur de texte préféré ( nano)

```
crontab -e

no crontab for meodel - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <---- easiest
  2. /usr/bin/vim.tiny
  3. /usr/bin/code
  4. /bin/ed

Choose 1-4 [1]: 1
```

- ensuite tout en bas après la myriade de commentaires nous pouvons link notre **backup_script.sh** fraichement créé afin de définir une durée de sauvegarde

## Plusieurs cas de sauvegardes

- ajoutez la ligne suivante pour exécuter le script tous les jours à 2h du matin :

```
0 2 \* \* \* ~/backup_script.sh
```

## Explication des Étoiles dans Cron

- Les options cron sont organisées comme suit :

```
* * * * * command
│ │ │ │ │
│ │ │ │ └── Jour de la semaine (0-7, où 0 et 7 = dimanche)
│ │ │ └──── Mois (1-12)
│ │ └────── Jour du mois (1-31)
│ └──────── Heure (0-23)
└────────── Minute (0-59)
```

- Sauvegardez et fermez crontab.

Les cinq étoiles dans la syntaxe cron déterminent la fréquence d’exécution de la commande. Voici la signification de chaque position :

| Position | Symbole | Description                | Exemple                 |
| -------- | ------- | -------------------------- | ----------------------- |
| 1ère     | `*`     | Minutes (0 - 59)           | `0` pour 0 min          |
| 2e       | `*`     | Heures (0 - 23)            | `2` pour 2h du matin    |
| 3e       | `*`     | Jour du mois (1 - 31)      | `15` pour le 15 du mois |
| 4e       | `*`     | Mois (1 - 12)              | `6` pour juin           |
| 5e       | `*`     | Jour de la semaine (0 - 7) | `1` pour lundi          |

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="sommaire" style="width: 150px; height: auto;">
</a>

## Vérifier les sauvegardes

Les sauvegardes seront enregistrées dans le dossier ~/backups avec un nom de fichier unique comprenant la date et l’heure de la sauvegarde.

## Tester le script

- Pour vérifier que tout fonctionne correctement, exécutez le script manuellement une fois :

```
~/backup_script.sh
```

### Youpi ca marche

![cron youpi](../assets/img/backups_op.png)

## Supprimer les sauvegardes automatiques

- Ouvrez crontab pour modifier les tâches planifiées :

```
crontab -e
```

- Trouvez la ligne correspondant à votre tâche de sauvegarde

- Supprimez cette ligne ou ajoutez un # au début pour la commenter (ce qui désactivera la tâche sans la supprimer).

- Enregistrez et quittez :

## Vérification de la suppression

- Vous pouvez vérifier que la tâche a bien été supprimée en listant vos tâches cron :

```
crontab -l
```

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="sommaire" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_l.png)

# PG_dump
![border](../assets/line/line_pink_point_r.png)

## Pourquoi utiliser pg_dump

- Bases de données dynamiques : Contrairement aux fichiers, une base de données est constamment mise à jour (insertion de données, suppression, modifications). pg_dump s'assure de capturer une image complète et cohérente de la base de données à un moment donné.

- Format de sauvegarde approprié : pg_dump crée un fichier de sauvegarde dans un format que vous pouvez restaurer avec PostgreSQL, incluant toutes les tables, les schémas et les données, ce qui est difficile à faire avec une simple copie de fichier.

- Automatisation avec cron : Utiliser pg_dump dans un script automatisé avec cron permet de créer des sauvegardes régulières et mises à jour de la base de données sans intervention manuelle. Cela garantit que vous disposez toujours d'une sauvegarde récente de l'état de votre base de données.

## Résumé du comparatif CRON PG_DUMP

#### cron seul :

Utilisé pour programmer l’exécution de tâches à intervalles réguliers.

#### pg_dump + cron :

Idéal pour les bases de données, car pg_dump crée une exportation complète de la base de données au moment de l’exécution, que vous pouvez programmer avec cron.

---

---

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="sommaire" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_l.png)

# Premiers pas avec PG_Dump

![border](../assets/line/line_pink_point_r.png)

## Installer pg_dump

- pg_dump fait partie du package PostgreSQL. Si PostgreSQL n'est pas déjà installé sur votre système, vous pouvez l'installer de cette manière :

```
sudo apt update
sudo apt install postgresql
```

## Vérifier l'installation de pg_dump

```
pg_dump --version
```

- ce qui affiche notr version de pg_dump comme ceci :

```
pg_dump (PostgreSQL) 16.4 (Ubuntu 16.4-0ubuntu0.24.04.2)
```

## Créer un script pour sauvegarder la base de données

- Maintenant, nous allons créer un script qui utilisera pg_dump pour sauvegarder la base de données **init_aubondeal.sql.**

- pour faire original nosu allons crréer un fichier
  de script **(backup_pg.sh)** oui comme pour cron mais avec **pg à la fin ^^** :

```
nano ~/backup_pg.sh
```

- Ajoutez le code suivant dans le script, en adaptant les informations de connexion (utilisateur, nom de base de données) :

```
#!/bin/bash
# Variables pour le script
TIMESTAMP=$(date +%Y%m%d%H%M%S)  # Horodatage pour les noms de fichiers uniques
BACKUP_DIR=~/backups             # Dossier de sauvegarde
DB_NAME=init_aubondeal            # Nom de la base de données
DB_USER=postgres                  # Nom d'utilisateur de PostgreSQL

# Exécuter pg_dump pour sauvegarder la base de données dans le répertoire de sauvegarde
pg_dump -U $DB_USER -d $DB_NAME -F c -f "$BACKUP_DIR/${DB_NAME}_$TIMESTAMP.sql"

# Vérification de la réussite
if [ $? -eq 0 ]; then
    echo "Sauvegarde de la base de données réussie : ${BACKUP_DIR}/${DB_NAME}_$TIMESTAMP.sql"
else
    echo "Échec de la sauvegarde de la base de données."
fi
```

- **TIMESTAMP** : Ajoute l'horodatage au nom de la sauvegarde pour des versions uniques.
- **BACKUP_DIR** : Répertoire où les sauvegardes seront stockées.
- **DB_NAME** : Nom de la base de données à sauvegarder (ici init_aubondeal).
- **DB_USER** : Nom d’utilisateur PostgreSQL (vous pouvez le remplacer par le vôtre).

#### Enregistrez et fermez le fichier, puis rendez le script exécutable :

```
chmod +x ~/backup_pg.sh
```

# Tester le script manuellement

- Avant de l’automatiser avec cron, testons le script pour vérifier qu'il fonctionne en écrivant :

```
~/backup_pg.sh
```

- Mais cela ne focntionne pas

```
Password:
pg_dump: error: la connexion au serveur sur le socket « /var/run/postgresql/.s.PGSQL.5432 » a échoué : FATAL:  password authentication failed for user "postgres"
Échec de la sauvegarde de la base de données.
```

## Option 1 : Utiliser le fichier .pgpass pour stocker le mot de passe

- PostgreSQL permet de stocker le mot de passe dans un fichier caché nommé .pgpass dans votre répertoire personnel. Voici comment configurer ce fichier pour que pg_dump puisse accéder à la base de données sans demander le mot de passe à chaque fois :

## Créez le fichier .pgpass dans votre répertoire personnel :

```
nano ~/.pgpass
```

- Ajoutez la ligne suivante, en remplaçant hostname, port, database, username, et password par les informations de connexion correctes :

```
hostname:port:database:username:password
```

- Pour une connexion locale avec PostgreSQL (par défaut, localhost et le port 5432), voici ce que vous pouvez mettre :

```
localhost:5432:init_aubondeal:postgres:VotreMotDePasse
```

- Enregistrez et fermez le fichier, puis modifiez les permissions pour que seul votre utilisateur puisse le lire :

```
chmod 600 ~/.pgpass
```

- Avec cette configuration, pg_dump utilisera automatiquement le mot de passe dans .pgpass, ce qui devrait résoudre le problème d'authentification.

- mais ... cela ne focntionne pas

```
❯ ~/backup_pg.sh
pg_dump: error: la connexion au serveur sur le socket « /var/run/postgresql/.s.PGSQL.5432 » a échoué : FATAL:  database "init_aubondeal" does not exist
Échec de la sauvegarde de la base de données.
```

- nous allons donc vérifier si la base de donnée **init_aubondeal** existe

```
sudo -u postgres psql
\l
```

- mais nosu découvrons que la base s'appelle aubondeal

- Nous allons donc devoir mettre à jour le script de sauvegarde

- en ouvrant notre script **backup_pg.sh** pour corriger le nom de la base de données :

dsdsds
dsdsqff

dsdsds
dsdsqff

dsdsds
dsdsqff

dsdsds
dsdsqff

![border](../assets/line/line_pink_point_l.png)

<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>
<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="sommaire" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)

```

```
