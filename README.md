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

un point d‘accès lourd qui dispose de ports WAN et LAN peut prendre en charge des fonctions de sécurité telles que le serveur DHCP, DNS, clonage d'adresses MAC, accès VPN et pare-feu. En tant que dispositif de réseau pouvant fonctionner de manière indépendante, le point d‘accès lourd peut implémenter la numérotation (dialing), le routage et certaines fonctions supplémentaires. Généralement, les points d‘accès lourds sont utilisés comme des points d'accès autonomes qui peuvent fonctionner en l'absence de tout dispositif de contrôle.

## Protocoles IEEE 802.11
La technologie WLAN du standard IEEE 802.11 couvre la couche “Accès au réseau” du modèle TCP/IP ou les couches “Physique” (L1) et “Liaison de données” (L2) du modèle OSI.

![image](https://user-images.githubusercontent.com/83721477/169827947-d9fad851-be74-4b3c-a20e-b8a91bf4f666.png)

![image](https://user-images.githubusercontent.com/83721477/169828091-2705a45e-77c0-44b1-bd93-c9dd872533ca.png)

## Les différents modes d’architecture
Dans un réseau sans fil, il existe 2 types d’architecture que l’on peut mettre en place:

* MODE `AD-HOC`
* MODE `INFRASTRUCTURE`

### Mode AD-HOC
![image](https://user-images.githubusercontent.com/83721477/169828890-8db62f2c-0a03-486c-a3a9-7b3631972b22.png)
* Pas d'intervention d'une borne d’accès.
* Communication point à point (P2P).

#### Avantage
* Tous les équipements sans fil peuvent fonctionner en mode ad-hoc.

Ce mode s’appelle IBSS (Independent Basic Service Set)

### Mode INFRASTRUCTURE
![image](https://user-images.githubusercontent.com/83721477/169829637-387f01b6-768f-493b-aaac-460cd91ed8cc.png)

* Fonctionne par l’intermédiaire d’au moins 1 borne d’accès.
* Les clients sans fil, ordinateurs portables, smartphones… s’associent à la borne d’accès puis envoient leur données à la borne qui se charge de les transmettre aux bonnes destinations.

Il existe 2 sous-mode
* mode `BSS` (Basic Service Set)
* mode `ESS` (Extended Service Set)

#### Basic Service Set
* 1 borne d'accès

#### Extended Service Set
* Minimum 2 bornes d’accès, voir des dizaines ou centaines.
* Les clients peuvent effectuer du roaming en passant d’une borne vers une autre sans couper la communication réseau.

### Borne lourde / Standalone
![image](https://user-images.githubusercontent.com/83721477/169830437-8930c152-a591-4f61-b091-9796e590e3f2.png)

* Les premières bornes d’accès étaient en mode lourd/standalone
* Au sein de leur système d’exploitation se trouvait toute la configuration (comme un IOS pour un switch ou routeur)
* Les trames utilisateurs étaient commutées par la borne vers les bonnes destination.
* Connexion en console ou telnet/ssh/http à la borne pour lui configurer différents paramètres comme le SSID (le nom de la pizzeria), le canal à utiliser, la puissance.

### Borne légère / Lightweight
![image](https://user-images.githubusercontent.com/83721477/169832050-dd4e2305-2091-49e5-95b1-9d1905c191ad.png)
* sans système d'exploitation complet
* suppriment le routage, DNS, serveur DHCP et de nombreuses autres fonctions de chargement et ne conserve que la partie accès sans fil
* reçoit/envoi des trames vers un boitier intelligent, le WLC – Wireless LAN Controller.

WLC: Ce boitier va contrôler à distance toutes les bornes d’accès et c’est sur ce boitier que l’administrateur va se connecter. Toute la configuration se trouve dedans et c’est le WLC qui va commuter/router les trames vers les bonnes destinations et non plus les bornes !

#### Fonctionnement
* La borne démarre électriquement
* Son interface filaire va envoyer une requête DHCP pour récupérer une adresse IP
* Une fois reçue, elle va contacter son WLC
* Le WLC va lui envoyer sa configuration minimal avec tous les paramètres au bon fonctionnement (SSID, puissance, canal…)
* Une fois configurée, la borne envoi tout le trafic des clients WiFi au contrôleur qui se chargera de les envoyer vers les bonnes destinations

