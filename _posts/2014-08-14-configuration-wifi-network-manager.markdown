---
layout: post
title:  "Configuration du Wifi avec NetworkManager"
categories: wifi
author: nekresh
---

L'utilisation de `NetworkManager` sur une autre distribution que le dump peut poser des problèmes de connexion.

Par défaut, l'utilisation d'un réseau `WPA2-Enterprise` demande la présence d'un certificat valide. Si le certificat n'est pas valide, la connexion échouera.
Le certificat n'étant pas valide sur `iit-wifi`, il faut désactiver ce test.

Pour cela, il faudra modifier le fichier `/etc/NetworkManager/system-connections/iit-wifi` et supprimer la ligne `system-ca-certs=true`.

[Source](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1104476)
