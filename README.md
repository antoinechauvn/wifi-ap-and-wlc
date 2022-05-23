# wifi-ap-and-wlc

## Types de déploiements
* Point d’accès lourds (Autonomous APs)
* Contrôleur (WLC) et points d’accès légers (Lightweight APs)
* Solution basée nuage (Cloud)

* Plan de gestion
Le plan de contrôle fait référence à toutes les fonctions et processus qui déterminent le chemin à utiliser pour envoyer le paquet ou la trame.
Le routage est effectué dans le plan de contrôle.

* Plan données
Le plan de données fait référence à toutes les fonctions et processus qui transfèrent les paquets/trames d'une interface à une autre en fonction de la logique du plan de contrôle.
La commutation est effectuée dans le plan de données.

## Architecture autonome
Un point d’accès autonome est un périphérique totalement indépendant qui “ponte” et étend des VLANs de l’infrastructure filaire avec différents SSID sur le réseau sans fil.
Une ou plusieurs interfaces Ethernet peuvent créent un pont de couche 2 (L2) avec une ou plusieurs interfaces radio.
* Chaque point d’accès autonome se gère individuellement en SSH ou en interface Web. Il pourrait être géré par une plateforme comme Cisco Prime Infrastructure ou comme DNA Center (voir plus bas).

![image](https://user-images.githubusercontent.com/83721477/169789006-6d33ab34-557d-4634-bf3c-3675fd42127e.png)

## Architecture Cloud
Dans ce type d’architecture de déploiement basé Cloud, le contrôleur se situe dans le nuage. Ce type de déploiement se distingue en deux parties :

des périphériques physiques comme des points d’accès, des commutateurs L2/L3, des pare-feu que l’on déploie tels quel sur l’infrastructure existante
un abonnement qui permet de configurer, contrôler, gérer et surveiller l’ensemble des périphériques à partir d’une interface Web et/ou d’un API HTTP REST situé dans le nuage (selon ses caractéristiques précises)

![image](https://user-images.githubusercontent.com/83721477/169791692-6b6a25ca-7cdf-48a4-a26e-e0ea51834c63.png)


Les points d‘accès légers, sans système d'exploitation complet propre, suppriment le routage, DNS, serveur DHCP et de nombreuses autres fonctions de chargement et ne conserve que la partie accès sans fil

un point d‘accès lourd qui dispose de ports WAN et LAN peut prendre en charge des fonctions de sécurité telles que le serveur DHCP, DNS, clonage d'adresses MAC, accès VPN et pare-feu. En tant que dispositif de réseau pouvant fonctionner de manière indépendante, le point d‘accès lourd peut implémenter la numérotation (dialing), le routage et certaines fonctions supplémentaires. Généralement, les points d‘accès lourds sont utilisés comme des points d'accès autonomes qui peuvent fonctionner en l'absence de tout dispositif de contrôle.

