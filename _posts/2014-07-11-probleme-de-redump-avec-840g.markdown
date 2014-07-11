---
layout: post
title:  "Probleme de redump avec un 840g"
date:   2014-07-11 14:14:00
categories: redump 840g
---

Lors du redump d'un ordinateur HP 840g, il se peut que l'ecran de boot se bloque avec pour message :

    Getting cached packet
    My IP is xxx.xxx.xxx.xxx

Il s'agit d'une mauvaise configuration d'usine de la machine. Celle-ci essaie de demarrer en utilisant l'UEFI au lieu du BIOS pour demarrer en reseau.
Pour corriger le probleme et effectuer un redump, il suffit de configurer la machine en mode legacy :

- Au demarrage, appuyer sur `F10` pour rentrer dans le BIOS
- Aller dans le menu `Advanced` puis `Boot options`
- Changer l'option `Boot Mode` a `Legacy`
