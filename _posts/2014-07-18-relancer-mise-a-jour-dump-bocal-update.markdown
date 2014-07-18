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
