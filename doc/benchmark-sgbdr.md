 <a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)

# BENCHMARK Postgres VS les autres SGBDR

## ![border](../assets/line/line_pink_point_l.png)

## Sommaire

- [Introduction](#introduction)
- [Premier comparatif basé sur MySQL](#premier-comparatif-basé-sur-mysql)
- [Comparatif entre les principaux SGBDR](#comparatif-entre-les-principaux-sgbdr)
- [Avantages de PostgreSQL](#avantages-de-postgresql)
- [Cas d'usages optimaux](#best-practices)

## Introduction

Pour le projet "AuBonDeal", le choix du SGBDR doit être guidé par des critères tels que la sécurité, la performance, la gestion des transactions et la flexibilité des données. Le tableau ci-dessus compare PostgreSQL et MySQL selon ces critères clés, en tenant compte des exigences d'une plateforme de commerce en ligne.

![border](../assets/line/line_teal_point_r.png)

## Premier comparatif basé sur MySQL

| Critères                                  | PostgreSQL | MySQL                  |
| ----------------------------------------- | ---------- | ---------------------- |
| **Conformité aux standards ACID**         | ✅         | ✅ (InnoDB uniquement) |
| **Gestion avancée des transactions**      | ✅         | ❌                     |
| **Flexibilité des types de données**      | ✅         | ❌                     |
| **Support des extensions**                | ✅         | ❌                     |
| **Indexation avancée (GIN/GIST)**         | ✅         | ❌                     |
| **Gestion fine des rôles et permissions** | ✅         | ❌                     |
| **Performance sur requêtes complexes**    | ✅         | ❌                     |
| **Support pour JSON et JSONB**            | ✅         | ✅                     |
| **Communauté open-source active**         | ✅         | ✅                     |
| **Options de sécurité**                   | ✅         | ❌                     |

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_teal_point_r.png)

# Comparatif entre les principaux SGBDR

![border](../assets/line/line_teal_point_r.png)

---

| Critères                     | MySQL                                     | PostgreSQL                                              | Oracle                                                      | SQL Server                                                                |
| ---------------------------- | ----------------------------------------- | ------------------------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------- |
| **Utilisation**              | Idéal pour les petites applications       | Adapté aux applications de niveau professionnel         | Principalement pour des applications critiques d’entreprise | Optimisé pour les environnements Windows et les applications d'entreprise |
| **Conformité SQL**           | Permissive, parfois laxiste               | Rigoureuse                                              | Strictement conforme, normes SQL ANSI élevées               | Conforme aux normes SQL ANSI avec des options propriétaires               |
| **Gestion des données JSON** | Basique, JSON pris en charge              | Avancée, avec le type JSONB pour stockage et indexation | JSON pris en charge dans les versions récentes              | JSON pris en charge avec stockage en colonnes                             |
| **Performances**             | Rapide en lecture                         | Optimal pour les requêtes complexes                     | Excellente pour des applications OLTP de grande envergure   | Très performant dans les environnements Windows                           |
| **Indexation**               | Index B-Tree principalement               | GIN, GiST, BRIN, et B-Tree pour des recherches avancées | Nombreux types d’index (bitmap, partitionnés) mais coûteux  | Index avancés, notamment pour la recherche en texte intégral              |
| **Extensibilité**            | Limitée en extensions et personnalisation | Très extensible avec de nombreuses extensions           | Hautement extensible, mais généralement coûteux             | Possède des options extensibles via des modules payants                   |
| **Coût**                     | Gratuit pour la version communautaire     | Gratuit et open-source                                  | Très onéreux, surtout pour les grandes entreprises          | Version gratuite limitée, versions complètes onéreuses                    |
| **Support / Mises à jour**   | Actif avec des mises à jour fréquentes    | Actif avec des mises à jour régulières                  | Support solide mais coûteux, mises à jour fréquentes        | Actif, avec mises à jour régulières, mais coûteux                         |
| **Scalabilité**              | Scalabilité verticale principalement      | Scalabilité horizontale et verticale                    | Scalabilité avancée, mais coûteuse (Oracle RAC)             | Bonne scalabilité verticale, limitée horizontalement                      |

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_l.png)

## Avantages de PostgreSQL

![border](../assets/line/line_teal_point_r.png)

- Dans la même base de donnée fait du r**elationnel et du non relationnel** ( docs... )

- **Conformité SQL** : PostgreSQL suit strictement les normes SQL en garantissant la fiabilité des applications complexes par une structure solide.

- **Transactions et ACID** : PostgreSQL applique les principes **ACID** pour des opérations de haute intégrité :

  - **Atomicité** : Une transaction est "tout ou rien" ; <span style="color: #ab638c">si une partie échoue, tout est annulé.</span>
  - **Cohérence** : <span style="color: #ab638c">La base reste organisée et valide avant et après chaque transaction.</span>
  - **Isolation** : <span style="color: #ab638c">Les transactions simultanées n’interfèrent pas entre elles</span>, garantissant des résultats précis.
  - **Durabilité** : <span style="color: #ab638c">Une fois validées, les données sont sauvegardées en permanence, même en cas de panne.</span>

- **Gestion avancée des données** : PostgreSQL prend en charge **JSONB** (format structuré pour des données complexes comme des objets JSON) et **PostGIS** (extension géospatiale, idéale pour les applications de cartographie).

- **Performance** : Excellente pour traiter de grandes quantités de données et des requêtes complexes, bien adapté aux écritures et lectures intensives.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/line_pink_point_l.png)

## Best Practices

![border](../assets/line/line_teal_point_r.png)

- **Applications analytiques** : Idéal pour des analyses et rapports détaillés sur de grands volumes de données.
- **Banques et Finances** : Gère des transactions sûres et précises, parfait pour des opérations bancaires complexes.

- **Systèmes de gestion de données** : Excellente gestion de données variées comme des cartes géographiques ou des documents structurés (JSON).

- **Applications critiques** : Idéal pour des services **où la disponibilité et la sécurité sont essentielles**, comme les **services de santé et de sécurité.**

---

![border](../assets/line/line_pink_point_l.png)

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="Back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)
