---
layout: post
title:  "Passer root sur le dump"
categories: dump root
author: nekresh
---

Afin de pouvoir effectuer les actions nécessaires au bon fonctionnement du dump des étudiants, il peut être nécessaire de devoir passer root sur la machine.

## Ouverture d'un shell root

* Lors du démarrage de la machine, sélectionner la ligne du dump OpenSuSe et appuyez sur la touche d'édition `e`.
* Aller sur la ligne commençant par `linux` et ajout `init=/bin/bash` à la fin de la ligne.
* Continuer le démarrage de la machine en appuyant sur `F10`.
* Un shell root est maintenant à votre disposition.
* Effectuer les modifications voulues.
* Executez la commande `sync` pour forcer le système a écrire sur le disque.
* Arrêter la machine en appuyant longtemps sur le bouton `power`. Il est nécessaire de forcer l'extinction, le support de l'ACPI n'étant pas chargé par le système.

## Obtention des droits root permanent

La méthode suivante ne permet que d'obtenir temporairement les droits root.
La séquence de démarrage étant coupée par le shell, l'interface graphique ainsi que bon nombre de services ne sont pas lancés.
Il peut être nécessaire d'obtenir des droits root tout en lançant la machine normalement.

En utilisant la méthode précédente, il faudra modifier le fichier `/etc/sudoers`:

* Commenter les lignes `Defaults targetpw` et `ALL  ALL=(ALL) ALL`.
* Ajouter une ligne `MY_LOGIN ALL=(ALL) ALL` en indiquant le login de l'étudiant au lieu de `MY_LOGIN`.

Une fois la machine redémarrée normalement, il sera possible de passer root avec les commandes `su` ainsi que `sudo`.

Il faudra bien veiller à restaurer la précédente configuration avant de rendre la machine à l'étudiant, afin qu'il ne puisse pas profiter de ces droits supplémentaires.
