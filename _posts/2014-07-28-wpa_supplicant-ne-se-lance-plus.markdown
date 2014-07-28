---
layout: post
title: "wpa_supplicant ne se lance pas"
author: nekresh
caregories: wifi
root: true
---

Il se peut, pour plusieurs raisons, que `wpa_supplicant` ne se lance pas au démarrage.
Cette commande ne retournera donc rien.

    ps aux | grep wpa_supplicant | grep -v grep

`wpa_supplicant` étant en charge de la connexion wifi, le dump ne sera plus en mesure de se connecter au wifi.
`wpa_gui` ne pourra pas non plus corriger ce problème, celui-ci ayant besoin que `wpa_supplicant` fonctionne pour modifier sa configuration.

En root, il faudra éditer le fichier `/etc/wpa_supplicant/wpa_supplicant.conf`.
Il est aussi possible de réutiliser la sauvegarde de la configuration, située dans `/etc/wpa_supplicant/wpa_supplicant.conf.backup`.
