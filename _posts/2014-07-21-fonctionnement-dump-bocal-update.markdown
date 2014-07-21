---
layout: post
title:  "Fonctionnement du dump (bocal-update)"
date:   2014-07-21 10:20:00
categories: update
author: nekresh
---

Le dump d'Octobre 2013 utilise le service `bocal-update` pour se maintenir à jour.
Celui-ci se charge de vérifier régulièrement si une mise à jour est présente et se charge de l'appliquer.
La vérification des mises à jour se base sur le site [http://repo.epitech.eu/opensuse/](http://repo.epitech.eu/opensuse/).

L'arborescence est assez simple :
* [http://repo.epitech.eu/opensuse/$MODE](http://repo.epitech.eu/opensuse/$MODE) contient les informations pour le mode donné (soit `std` soit `exam`).
* [http://repo.epitech.eu/opensuse/$MODE/dump_release](http://repo.epitech.eu/opensuse/$MODE/dump_release) contient la dernière version pour un mode donné.
* [http://repo.epitech.eu/opensuse/$MODE/repo_add_$VERSION](http://repo.epitech.eu/opensuse/$MODE/repo_add_$VERSION) ainsi que [http://repo.epitech.eu/opensuse/$MODE/repo_del_$VERSION](http://repo.epitech.eu/opensuse/$MODE/repo_del_$VERSION) contiennent la liste des dépôts à ajouter/supprimer du dump.
* [http://repo.epitech.eu/opensuse/$MODE/pkg_add_$VERSION](http://repo.epitech.eu/opensuse/$MODE/pkg_add_$VERSION) ainsi que [http://repo.epitech.eu/opensuse/$MODE/pkg_del_$VERSION](http://repo.epitech.eu/opensuse/$MODE/pkg_del_$VERSION) contiennent la liste des paquets RPM à ajouter/supprimer du dump.

Il n'y a pas de cumul de version, il n'est pas nécessaire d'installer les version intermédiaires. Chaque fichier contient la totalité des informations nécessaires pour passer le dump de la version initiale à cette version.
