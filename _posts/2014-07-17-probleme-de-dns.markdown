---
layout: post
title:  "Problème de DNS"
categories: dns
root:   true
author: nekresh
---

Lors de problème réseau ou de connexion à un autre réseau wifi, il se peut que la configuration DNS soit écrasée.

Afin de corriger ce problème, en root, il faut modifier le fichier `/etc/resolv.conf` et modifier les lignes suivantes :

    nameserver 10.42.6.6
    search epitech.eu

N'oubliez pas de supprimer toute autre entrée nameserver dans le fichier `resolv.conf`.
