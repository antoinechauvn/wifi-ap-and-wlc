# wifi-ap-and-wlc

## Types de déploiements
* Point d’accès lourds (Autonomous APs)
* Contrôleur (WLC) et points d’accès légers (Lightweight APs)
* Solution basée nuage (Cloud)

### Plan de gestion
Le plan de contrôle fait référence à toutes les fonctions et processus qui déterminent le chemin à utiliser pour envoyer le paquet ou la trame.
Le routage est effectué dans le plan de contrôle.

### Plan données
Le plan de données fait référence à toutes les fonctions et processus qui transfèrent les paquets/trames d'une interface à une autre en fonction de la logique du plan de contrôle.
La commutation est effectuée dans le plan de données.
En tant que , le point d‘accès lourd peut implémenter la numérotation (dialing), le routage et certaines fonctions supplémentaires. Généralement, les points d‘accès lourds sont utilisés comme des points d'accès autonomes qui peuvent fonctionner en l'absence de tout dispositif de contrôle.

## Protocoles IEEE 802.11
WLAN du standard IEEE 802.11:
* “Accès au réseau” du modèle TCP/IP
* “Physique” (L1) et “Liaison de données” (L2) du modèle OSI.

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

#### BSS
Ensemble de services de base (Basic Service Set)
* Un groupe de stations communiquant entre elles par l’intermédiaire d’un point d’accès (Access Point, AP)
* Communiquant dans la zone de service de base (BSA, “Basic Service Area”), un espace défini par les caractéristiques de propagation des ondes radio.

![image](https://user-images.githubusercontent.com/83721477/169845255-9a757379-f562-4877-9a98-bd15d05f5cda.png)

#### BSA
Une zone de service de base (BSA) est la zone physique de couverture fournie par un point d'accès dans un BSS

![image](https://user-images.githubusercontent.com/83721477/169846061-a210e44e-a9b3-4361-b0db-c57c8e8c5b68.png)

#### Extended Service Set
* Minimum 2 bornes d’accès, voir des dizaines ou centaines.
* Les clients peuvent effectuer du roaming en passant d’une borne vers une autre sans couper la communication réseau.

![image](https://user-images.githubusercontent.com/83721477/169848565-84833aaa-ede2-4e86-8266-e696086f4459.png)

### Borne lourde / Standalone

![image](https://user-images.githubusercontent.com/83721477/169830437-8930c152-a591-4f61-b091-9796e590e3f2.png)

**Dispositif de réseau pouvant fonctionner de manière indépendante**

* Les premières bornes d’accès étaient en mode lourd/standalone
* Gère la commutation
* Au sein de leur système d’exploitation se trouvait toute la configuration (comme un IOS pour un switch ou routeur)
* dispose de ports WAN et LAN
* peut prendre en charge des fonctions de sécurité telles que le serveur DHCP, DNS, clonage d'adresses MAC, accès VPN et pare-feu.
* Connexion en console ou telnet/ssh/http à la borne pour lui configurer différents paramètres comme le SSID, le canal à utiliser, la puissance.

### Borne légère / Lightweight

![image](https://user-images.githubusercontent.com/83721477/169832050-dd4e2305-2091-49e5-95b1-9d1905c191ad.png)

* l’émission/réception du trafic radio
* la gestion des accès (MAC)
* le chiffrement du trafic
* Pas de routage, DNS, serveur DHCP et de nombreuses autres fonctions de chargement et ne conserve que la partie accès sans fil
* reçoit/envoi des trames vers un boitier intelligent, le WLC (Wireless LAN Controller).
*Note: les points d’accès légers se gèrent uniquement avec un contrôleur (WLC)*

#### Fonctionnement
* La borne démarre électriquement
* Son interface filaire va envoyer une requête DHCP pour récupérer une adresse IP
* Une fois reçue, elle va contacter son WLC
* Le WLC va lui envoyer sa configuration minimal avec tous les paramètres au bon fonctionnement (SSID, puissance, canal…)
* Une fois configurée, la borne envoi tout le trafic des clients WiFi au contrôleur qui se chargera de les envoyer vers les bonnes destinations

### WLC (Wireless LAN Controllers)
* Contrôler des points d’accès (AP)
* Vue unifiée du réseau sans-fil.
* Embarquent des fonctions avancées du réseau.
* Détection des interférences et l’ajustement des fréquences utilisées
* Optimiser la couverture radio sur des espaces physiques très larges.

#### Un contrôleur WLAN (WLC) peut se gérer de différentes manières :
* Un accès graphique (GUI) en HTTP ou en HTTPS
* Un accès en ligne de commande (CLI) en Telnet, en SSH, ou en console physique
* Un accès à travers un port de service dédié

## Multi-BSS
* Un seul point d’accès (AP) pour gérer plusieurs réseaux, “multi-SSID”, “multi-BSS” ou “APs virtuels”.
* 1 “station de base” physique simule un ensemble de “stations de base” avec différentes configurations
* L’espace physique est le même et il est partagé entre les réseaux logiques.

![image](https://user-images.githubusercontent.com/83721477/169848474-4b95e77f-ccf8-400e-b2d6-3d6faec2d1c4.png)

*Note: Multiplier les SSIDs n’augmente pas la capacité du réseau.*

### Système de distribution (DS)
Le système de distribution établit la connexion entre le réseau filaire Ethernet et le réseau sans fil sur un plan logique, agissant de la sorte comme un pont vers le réseau Wi-Fi.
![image](https://user-images.githubusercontent.com/83721477/170251884-092cb8f4-13b8-40cf-a9f7-21c2f7a99f5d.png)
