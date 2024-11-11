 <a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)

# Mise en place de la base de données

![border](../assets/line/line_pink_point_r.png)

# Sommaire

- [Premier pas](#premier-pas)

# Documents

- [Base de donnée .sql](#premier-pas)

![border](../assets/line/border_b.png)

![border](../assets/line/line_pink_point_l.png)

# Premier pas :

![border](../assets/line/line_teal_point_r.png)

Tutoriel : Comment importer et exécuter le script SQL pour créer la base de données aubondeal
Prérequis
PostgreSQL installé : Assurez-vous que PostgreSQL est installé et accessible.
Permissions : Avoir un accès avec un utilisateur ayant le droit de créer des bases de données (comme le superutilisateur postgres).
Étapes
Créer le fichier SQL :

Copiez le script SQL fourni ci-dessus dans un éditeur de texte.
Enregistrez-le sous un nom comme init_aubondeal.sql.
Ouvrir le terminal ou l’invite de commandes :

Sur Windows, utilisez PowerShell ou Invite de commandes.
Sur Linux ou macOS, ouvrez un terminal.
Se connecter à PostgreSQL avec le superutilisateur :

Dans le terminal, connectez-vous à PostgreSQL en utilisant le superutilisateur postgres pour exécuter le script avec les permissions nécessaires. Utilisez psql pour cela.
bash
Copier le code
psql -U postgres
Entrez le mot de passe de postgres si nécessaire.
Importer le fichier SQL :

Exécutez la commande suivante pour importer et exécuter le fichier init_aubondeal.sql :
sql
Copier le code
\i /chemin/vers/le/fichier/init_aubondeal.sql
Remplacez /chemin/vers/le/fichier/init_aubondeal.sql par le chemin réel vers votre fichier SQL.
Exemple pour Windows :

sql
Copier le code
\i C:\Users\votre_nom\Documents\init_aubondeal.sql
Vérifier la création de la base de données et des tables :

Après l'exécution du fichier, vous pouvez vérifier que la base de données, les tables et les utilisateurs ont été créés correctement.
Pour lister les bases de données :
sql
Copier le code
\l
Pour voir les tables dans la base de données aubondeal :
sql
Copier le code
\c aubondeal
\dt
Tester la connexion avec l’utilisateur aubondeal_api :

Déconnectez-vous de psql en tapant \q.
Testez la connexion avec l'utilisateur aubondeal_api :
bash
Copier le code
psql -U aubondeal_api -d aubondeal -h localhost
Entrez le mot de passe de aubondeal_api tel que défini dans le script.
Résumé des Commandes pour Importer le Script SQL
Ouvrir psql avec le superutilisateur :

bash
Copier le code
psql -U postgres
Importer le script SQL :

sql
Copier le code
\i /chemin/vers/le/fichier/init_aubondeal.sql
Vérifier la création de la base de données et des tables :

sql
Copier le code
\l -- Lister les bases de données
\c aubondeal -- Se connecter à la base de données aubondeal
\dt -- Lister les tables
Tester la connexion avec aubondeal_api :

bash
Copier le code
psql -U aubondeal_api -d aubondeal -h localhost

![border](../assets/line/line_teal_point_l.png)

<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>
<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_r.png)
