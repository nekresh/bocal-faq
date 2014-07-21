---
layout: post
title:  "Fonctionnement du dump (blinux)"
date:   2014-07-18 18:00:00
categories: update
author: nekresh
---

Le dump de Février 2014 utilise un ensemble d'outils nommés `blinux-*` pour se maintenir à jour.

## blinux-release

La commande `blinux-release` permet d'obtenir des informations sur le dump.

    blinux-release -r # release du dump
    blinux-release -v # version du dump
    blinux-release -m # mode du dump (std ou exam)
    
    blinux-release -sr xxxx # change la release du dump pour xxxx
    blinux-release -sv xxxx # change la version du dump pour xxxx
    blinux-release -sm xxxx # change le mode du dumpe pour xxxx

Attention, la modification de la release, la version ou le mode requiert un accès root.
N'ayant pas testé de modifier la release ou le mode d'un dump, effectuez ces modifications à vos propres risques.

## blinux-update

Le service `blinux-update` se charge de vérifier régulièrement la présence de nouvelle version pour le dump ainsi que le maintenir à jour.
Cette vérification ainsi que la mise à jour se base sur le site [http://pkg.bocal.org/blinux](http://pkg.bocal.org/blinux).

L'arborescence est assez simple:

* [http://pkg.bocal.org/blinux/$RELEASE](http://pkg.bocal.org/blinux/$RELEASE) contient les informations pour une release donnée
* [http://pkg.bocal.org/blinux/$RELEASE/current_version_$MODE](http://pkg.bocal.org/blinux/$RELEASE/current_version_$MODE) contient la dernière version pour le mode d'un release donnée
* [http://pkg.bocal.org/blinux/$RELEASE/repo_add_$MODE_$VERSION](http://pkg.bocal.org/blinux/$RELEASE/repo_add_$MODE_$VERSION) ainsi que [http://pkg.bocal.org/blinux/$RELEASE/repo_del_$MODE_$VERSION](http://pkg.bocal.org/blinux/$RELEASE/repo_del_$MODE_$VERSION) contiennent la liste des dépots OpenSuSe à ajouter/supprimer sur le dump
* [http://pkg.bocal.org/blinux/$RELEASE/pkg_add_$MODE_$VERSION](http://pkg.bocal.org/blinux/$RELEASE/pkg_add_$MODE_$VERSION) ainsi que [http://pkg.bocal.org/blinux/$RELEASE/pkg_del_$MODE_$VERSION](http://pkg.bocal.org/blinux/$RELEASE/pkg_del_$MODE_$VERSION) contiennent la liste des paquets RPM à installer/supprimer du dump
