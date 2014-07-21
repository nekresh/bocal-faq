---
layout: post
title:  "Relancer les mises à jour sur le dump (bocal-update)"
date:   2014-07-18 14:00:00
categories: update
author: nekresh
root:   true
---

Juste après un redump, celui-ci doit se mettre à jour en utilisant la commande `bocal-update`.
Cette commande ayant un gros problème de design interne, il se peut quelle n'effectue pas les mises à jour.

Afin de pouvoir relancer l'installation des commandes, il faudra, en root, supprimer le fichier `/etc/dump_release` et redémarrer la machine.
L'absence de ce fichier relancera les mises à jour sur la machine.

Il arrive que le dump ne relance pas les mises à jour tout seul.
Le script suivant permet de forcer les mises à jour :

    # arrêter le service bocal-update pour ne pas avoir de conflit
    service bocal-update stop
    
    # récupérer la dernière version du dump
    version=`wget -qO - http://repo.epitech.eu/opensuse/std/dump_release`
    
    # suppression des paquets
    for package in `wget -qO - http://repo.epitech.eu/opensuse/std/pkg_del_$version`
    do
      zypper -n remove --force-resolution $package
    done
    
    # installation des paquets
    for package in `wget -qO - http://repo.epitech.eu/opensuse/std/pkg_add_$version`
    do
      zypper -n install --force-resolution $package
    done
    
    # relancer le service
    service bocal-update start
