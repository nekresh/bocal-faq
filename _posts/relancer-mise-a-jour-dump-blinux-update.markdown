---
layout: post
title:  "Relancer les mises à jour sur le dump (blinux-update)"
date:   2014-07-18 14:00:00
categories: update
author: nekresh
root:   true
---

Juste après un redump, celui-ci doit se mettre à jour. Pour celà, le système utilise le service `blinux-update`.
Il se peut que le service n'effectue pas les mises à jour, celui-ci ne vérifiant pas correctement le code de retour de la commande `zypper`.

Afin de pouvoir relancer l'installation des commandes, il faudra, en root, modifier la version locale du dump et redémarrer.

Ainsi, pour la release `amaretto_apericube`, il suffit de forcer une ancienne version, 0.7 par exemple.

    blinux-release -sv 0.7

En utilisant le fonctionnement simple du dump [blinux]({% port_url "fonctionnement-dump-blinux" %}), le script suivant, exécuté en root, permet de forcer l'installation/désinstallation pour la release en cours :

    # couper le service blinux-update durant notre manipulation
    service blinux-update stop
    
    # récupération des informations essentielles
    release=`blinux-release -r`
    mode=`blinux-release -m`
    version=`wget -qO - http://pkg.bocal.org/blinux/$release/current_version_$mode`
    
    # suppression des paquets inutiles
    for package in `wget -qO - http://pkg.bocal.org/blinux/$release/pkg_del_$mode_$version`; do
      zypper -n remove --force-resolution $package
    done
    
    # installation des nouveaux paquets
    for package in `wget -qO - http://pkg.bocal.org/blinux/$release/pkg_add_$mode_$version`; do
      zypper -n install --force-resolution $package
    done
    
    # redémarrer le service blinux-update
    service blinux-update start
