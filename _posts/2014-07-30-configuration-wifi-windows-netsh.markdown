---
layout: post
title:  "Configuration du wifi sous Windows avec netsh"
categories: wifi
author: nekresh
---

Il se peut que l'interface graphique de configuration du wifi sous Windows ne fonctionne pas.

Il est cependant possible d'utiliser le binaire `netsh` pour manipuler la configuration de la couche wifi sans avoir besoin de l'interface graphique.
`netsh` permet de configurer la couche wifi gràce à sa section `wlan`.

Pour configurer la connexion pour `iit-wifi`, il suffira d'incorporer le fichier [Wi-Fi-iit-wifi.xml]({{ "/assets/Wi-Fi-iit-wifi.xml" | preprend: site.baseurl | prepend: site.url }}) dans le système avec la commande :

    netsh wlan add profile filename="Wi-Fi-iit-wifi.xml" user=current
    
La configuration pour `iit-wifi` est maintenant faite et disponible depuis l'interface standard de connexion de Windows.
    
Le fichier `Wi-Fi-iit-wifi.xml` est obtenu en lançant la commande suivante :

    netsh wlan export profile iit-wifi
    
Le fichier exporté ne contient pas les identifiants, si ceux-ci sont sauvegardés.
