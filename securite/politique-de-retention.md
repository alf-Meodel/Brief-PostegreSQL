<a href="/README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
  </a>

![border](../assets/line/border_r.png)

# Politique de Rétention des Sauvegardes

![border](../assets/line/line_teal_point_r.png)

# Sommaire

- [Objectif](#objectif)
- [Risques Couverts](#risques-couverts)
- [Fréquence des Sauvegardes](#fréquence-des-sauvegardes)
- [Durée de Conservation](#durée-de-conservation)
- [Règle de Sauvegarde 3 2 1](#règle-de-sauvegarde-3-2-1)
- [Automatisation des Sauvegardes](#automatisation-des-sauvegardes)

![border](../assets/line/line_pink_point_l.png)

## Objectif

La politique de rétention des sauvegardes PostgreSQL a pour vocation de garantir la sécurité, l’intégrité, et la disponibilité des données critiques de l’organisation. Elle est conçue pour répondre aux exigences de restauration rapide en cas d’incident, tout en minimisant les risques associés aux pertes de données.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="back to top" style="width: 150px; height: auto;">
</a>

## Risques Couverts

La politique de rétention vise à protéger contre les événements suivants :

- **Perte accidentelle de données** : Prévention contre la suppression involontaire de données critiques.
- **Cyberattaques** : Protection renforcée contre les ransomwares, malwares, et autres menaces de sécurité.
- **Défaillance matérielle** : Maintien des sauvegardes en cas de panne du matériel serveur.
- **Catastrophes naturelles et sinistres** : Réplication et stockage distant pour garantir une récupération en cas de sinistre majeur.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="back to top" style="width: 150px; height: auto;">
</a>

## Fréquence des Sauvegardes

- **Sauvegarde quotidienne complète** : Une copie complète des données critiques est réalisée chaque jour à 2h du matin. Ce créneau nocturne a été sélectionné afin de minimiser l'impact sur les opérations en production, assurant ainsi la continuité des services pendant les heures de travail.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="back to top" style="width: 150px; height: auto;">
</a>

## Durée de Conservation

- **Rétention des sauvegardes journalières** : Les sauvegardes sont conservées pendant 7 jours, offrant une disponibilité pour la semaine écoulée. Cette période garantit une récupération rapide en cas de besoin.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="back to top" style="width: 150px; height: auto;">
</a>

## Règle de Sauvegarde 3 2 1

Pour maximiser la sécurité et la disponibilité des données, la politique de rétention suit le principe de sauvegarde 3-2-1 :

- **3 copies des données** : Une copie de production et deux copies de sauvegarde afin de prévenir toute perte totale.
- **2 types de stockage distincts** : Les sauvegardes sont réparties sur différents supports (par exemple, un disque dur et un stockage en cloud) pour atténuer les risques de défaillance matérielle ou de sinistre.
- **1 copie hors site** : Une copie est conservée dans un emplacement distant (cloud sécurisé ou centre de données séparé) pour protéger les données en cas de catastrophe locale.

Cette approche renforce la résilience et permet une restauration efficace des données, même en cas d'incidents majeurs.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="back to top" style="width: 150px; height: auto;">
</a>

## Automatisation des Sauvegardes

Les sauvegardes sont automatisées via une tâche cron, déclenchant un script de sauvegarde quotidien à 2h du matin. Cette configuration garantit des sauvegardes régulières et fiables, réduisant ainsi le risque d'erreurs humaines.

<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="back to top" style="width: 150px; height: auto;">
</a>

## Sécurité et Stockage des Sauvegardes

- **Chiffrement des sauvegardes** : Toutes les sauvegardes sont chiffrées afin d'empêcher tout accès non autorisé.
- **Stockage externe et distant** : Une copie des sauvegardes est transférée vers un stockage sécurisé externe pour atténuer les risques liés aux sinistres locaux.
- **Contrôle d'accès** : L'accès aux fichiers de sauvegarde est strictement restreint aux utilisateurs autorisés.

En adoptant cette politique de rétention, l’organisation assure une gestion sécurisée et optimale des données critiques, renforçant ainsi la continuité opérationnelle et la sécurité des informations sensibles.

![border](../assets/line/line_pink_point_l.png)

<a href="../README.md">
  <img src="../assets/button/home_page.png" alt="Home page" style="width: 150px; height: auto;">
</a>
<a href="#sommaire">
  <img src="../assets/button/back_to_top.png" alt="back to top" style="width: 150px; height: auto;">
</a>

![border](../assets/line/border_r.png)
