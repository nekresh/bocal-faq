---
layout: post
title:  "Récupération des projets rendus avec blih"
categories: blih
author: nekresh
---

Les projets rendus à travers `blih` ou `rendu` peuvent simplement être récupéré par un étudiant.

La commande `blih` peut lister les dépôts avec `blih repository list`.
Il est ensuite possible de cloner ce dépôt avec la commande `git clone $USER@git.epitech.eu:/$USER/depot`.

Un simple script permet de récupérer les anciens rendus :

    for repo in `blih repository list`; do
        git clone $USER@git.epitech.eu:/$USER/$repo;
    done

Ce script récupère tous les dépôts présents sur `blih` dans le répertoire courant. Cette procédure peut donc prendre un certain temps.
