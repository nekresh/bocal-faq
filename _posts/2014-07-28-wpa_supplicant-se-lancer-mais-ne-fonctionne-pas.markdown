---
layout: post
title:  "wpa_supplicant se lance mais ne fonctionne pas"
categories: wifi
author: nekresh
root: true
---

Dans certains cas, `wpa_supplicant` se lance bien mais ne fonctionne pas.
La commande `ps aux | grep wpa_supplicant | grep -v grep` retourne :

    /usr/sbin/wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf -u -f /var/log/wpa_supplicant.log

L'utilisation de `wpa_gui` montre que `wpa_supplicant` effectue bien les scans mais qu'aucun réseau wifi n'est jamais trouvé.

Le nom de l'interface réseau wifi à utiliser se trouve en utilisant la commande `iwconfig`. Il s'agit de la seule interface ayant des capacités wifi.
Dans les exemples suivant, nous utilisons `wlo1`. Il suffira de substituer `wlo1` avec le nom de votre interface dans les lignes suivantes.

En root, il est possible de vérifier que `wpa_supplicant` et la carte wifi fonctionnent bien :

    # arrêter le service wpa_supplicant
    service wpa_supplicant stop
    
    # lancer wpa_supplicant
    # il doit rester actif pour faire fonctionner la carte wifi
    wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf -u -f /var/log/wpa_supplicant.log -iwlo1
    
    # wpa_gui devrait pouvoir scanner et se connecter à un réseau wifi
    # une fois connecté, forcer une demande d'IP au DHCP dans un autre shell
    dhclient wlo1
    
Si l'utilisation de `wpa_supplicant` de cette manière fonctionne, la modification est assez simple.
Il faut modifier le fichier `/etc/systemd/system/multi-user.target.wants/wpa_supplicant.service` et ajouter `-iwlo1` à la fin de la ligne `ExecStart`.
