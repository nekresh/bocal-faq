---
layout: post
title: "Réparation du système de paquet lorsqu'il est cassé"
author: nekresh
root: true
---

Les mises à jour du dump s'effectuant en background, il se peut que celles-ci s'exécutent lorsque la machine d'un étudiant s'éteint violemment, pour cause d'un crash, d'une batterie vide ou simplement d'une action de l'étudiant.

Dans certains cas, le système peut être en train de mettre à jour des paquets critiques.
Il se peut que le système d'installation des paquets `zypper` soit touché.
Un des messages suivant peut s'afficher si vous lancer la commande `zypper` à la main :

* `libzypp.so.1036 not found`
* `libzypp.so.1036 can't be loaded`

Toute variante de la library ainsi que de la version indique le même problème.

Heureusement, le programme `zypper` n'est pas le gestionnaire de paquet principal sur OpenSuse.
Il vous sera possible d'utiliser `yast2` afin de réinstaller le paquet `zypper`.
Une fois le paquet `zypper` réinstallé avec `yast2`, celui-ci devrait être fonctionnel.
Il ne vous reste plus qu'à forcer la mise à jour du dump, afin de vous assurer que ce problème ne surviendra plus.
La documentation pour [bocal-update]({% post_url 2014-07-18-relancer-mise-a-jour-dump-bocal-update %}) ainsi que [blinux-update]({% post_url 2014-07-22-relancer-mise-a-jour-dump-blinux-update %}) est disponible.
    
