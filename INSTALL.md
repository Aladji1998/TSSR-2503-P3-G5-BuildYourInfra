Pour la mise en place de mon projet il me faut mettre en place ces éléments suivants 

## 1- Création des machines 

- Utilisation de virtualbox pour la création et configuration des VM 

1 VM serveur Windows 2022 Graphique 

1 Vm client Windows 10 

Réseau: 172.16.50.5/24 

Ip Adresse: 172.16.50.7

Masque: 255.255.255.0

Passerelle 172.16.50.8

DNS: 172.16.50.7 


 ## Configuration Reseau VM 

 - Configurer le Réseau des machines Windows Serveur et Client en réseau interne 

<img width="639" alt="Capture reseau vm" src="https://github.com/user-attachments/assets/76dd1af5-b3bb-4ad2-977e-52fc1466e84d" />


## Installation et configuration Serveur Active Directory 

- Configuration Ip 

<img width="250" alt="Capture conf ip" src="https://github.com/user-attachments/assets/f5580114-f3bf-438f-8201-5995c1b5cc61" />


- installation AD-DS, DNS et DHCP 


ouvrir gestionnaire serveur ensuite clic droit sur gérer puis sur ajouter des roles et fonctionnalités une fenètre va s'ouvrir



<img width="425" alt="Capture ad ro" src="https://github.com/user-attachments/assets/f8a6b6d7-b199-4b19-b865-c2b0bf974e2b" />





<img width="421" alt="Capture a" src="https://github.com/user-attachments/assets/234370a7-593d-4bb9-80b9-dad03c199b19" />



continuer à cliquer sur suivant jusqu'a selectionner des roles et serveurs, installer et configurervd'abord AD-DS ensuite DNS et enfin DHCP 


Apres ces installation et configuration de ces derniers on obtient ceci 



<img width="510" alt="Capture insta" src="https://github.com/user-attachments/assets/9b05cb27-9fc9-4f97-95fa-97ec9171af58" />



- Promouvoir le serveur en tant que contrôleur de domaine


Après l’installation du rôle AD-DS :


Retourne dans le Gestionnaire de serveur


Une alerte jaune apparaît : "Promouvoir ce serveur en contrôleur de domaine"


Assistant de déploiement :


Ajouter une nouvelle forêt


Nom du domaine : WILDER.local 


Définis ensuite un mot de passe pour le mode restauration


Suivre les étapes et laisser le serveur redémarrer



<img width="395" alt="Capture co" src="https://github.com/user-attachments/assets/c270152d-1f62-49b8-9578-c6d33494a765" />


- Finalisation de la configuration DNS et DHCP

Le serveur sera dans le domaine WILDER.local

DNS sera configuré automatiquement

Pour DHCP :

Ouvrir la console DHCP

Créer une nouvelle étendue: Adresse de debut 172.16.50.100 - Adresse de fin 172.16.50.200

Ajouter les options de base : passerelle 172.16.50.8, DNS 172.16.50.7, domaine (WILDER.local)

Activer l'étendue



<img width="522" alt="Capturedhc" src="https://github.com/user-attachments/assets/bef99b4e-4c65-4864-9d85-00092d06a08c" />




- Création des Utilisateurs 


Aller dans outils => utilisateur et ordinateur Active Directory cliquer droit sur le domaine => nouveau => utilisateur 



<img width="401" alt="Capture nv" src="https://github.com/user-attachments/assets/1ef050e6-6616-44a6-8279-eb5cf186d051" />







<img width="248" alt="Capture creation utii" src="https://github.com/user-attachments/assets/35abf7b1-1579-401a-a40f-95b940085d3e" />





<img width="377" alt="Capture cre utilis" src="https://github.com/user-attachments/assets/17f0a7a2-d412-45fd-92d3-833270e0e837" />



- Creation des O.U 


Aller dans outils=> utilisateur et ordinateur Active Directory=> clique droit sur lr domaine => nouveau=> unité d'organisation=> nommer l'O.U 





<img width="278" alt="Capture Creation O U" src="https://github.com/user-attachments/assets/05ca07df-b03b-4fd8-a61b-cc0aeaa952ff" />



- Création des groupes correspondants

Aller dans outils=> utilisateur et ordinateur Active Directory=> clique droit sur lr domaine => nouveau=> créer un Groupe



<img width="425" alt="Capture group 1" src="https://github.com/user-attachments/assets/0a8a87ac-21dd-4087-85b3-5556d8304eb5" />








<img width="484" alt="Capture grp" src="https://github.com/user-attachments/assets/fd5723e1-3fdf-4d55-bdae-dfa3c40e2adc" />





b- Création des GPO 

Aller dans la barre des recherches=> gestions des stratégie de groupe=> 


<img width="543" alt="Capture GPO" src="https://github.com/user-attachments/assets/506c0bfd-82b5-4669-8fe4-a05f8ea2eb3d" />


Ensuite clique droit sur le domaine=> ensuite créer un un objet GPO dans ce Domaine 


<img width="258" alt="Capture nv gp" src="https://github.com/user-attachments/assets/3bc77598-1f29-46b7-b547-139e336c028f" />


Nommer le GPO 


<img width="212" alt="Capture nex" src="https://github.com/user-attachments/assets/a07cf88a-e844-4248-bec8-17ba421e0a62" />


Faire la meme chose pour le reste des GPO 

GPO demandé 


<img width="172" alt="Capture CRE GPO" src="https://github.com/user-attachments/assets/2ab7dd76-6683-47b5-916c-fdbdb1688dfa" />




GPO politique de mot de passe=> apprés installation nous allons le configurer pour obtenir (complexité, longueur)  clic droit dessus => modifier=> configuration ordinateur=>clic sur stratégie=> paramétres Windows=> paramétres securité=> stratégie de compte=> stratégie de mot de passe 







<img width="314" alt="Capture 2 par secu" src="https://github.com/user-attachments/assets/9a2684fd-f9d7-40a9-949b-c4e9f51071b2" />










<img width="316" alt="Capturess" src="https://github.com/user-attachments/assets/68e36a71-133e-46b9-8fdc-26ead85c6357" />




<img width="288" alt="Capture 8carac" src="https://github.com/user-attachments/assets/35e121ec-9665-47f1-a0f1-c331141acf3f" />






















## 3- intégration du client au serveur

 
  Configurer le VM en réseau interne avant son installation 


  <img width="645" alt="Capture res cli" src="https://github.com/user-attachments/assets/23390c18-4a3a-4dc2-992c-c7aa84da2106" />


Sur cette machine je ne vais pas configurer l'adresse ip je vais plutot désactiver les pare-feux parceque la machine a dèja une adresse ip fourni par le DHCP 

ping du serveur vers le client= ici le serveur ne reconnait pas la machine client 


<img width="549" alt="Capture ping Serv ver client" src="https://github.com/user-attachments/assets/a3eb6b2b-a6e6-4c68-83e0-92b400b330bf" />




Je dois donc Desactiver les pare-feux pour avoir une connectivité entre les 2 machines faire le ping du serveur vers la machine client 



<img width="475" alt="Capture desac" src="https://github.com/user-attachments/assets/13e5015c-4735-4b79-9427-d47fbad8ae73" />



Aprées avoir désactiver les pare-feux la connectivité va marcher 



<img width="300" alt="Capture ping cli" src="https://github.com/user-attachments/assets/04d7c17d-7086-4c4e-9206-de5d33cedb02" />









ping du client vers le serveur=> ici la machine du client reconnait le serveur 



<img width="530" alt="Capture PING serv" src="https://github.com/user-attachments/assets/af8d0310-4b5b-4218-a512-114fd7ffabd2" />



- Mettre le client au domaine 


verifier le beau d'adresse 

<img width="484" alt="Capture DHCP" src="https://github.com/user-attachments/assets/72b2f371-944a-464e-97e4-ba76383a7948" />













Modification du nom de l'ordinateur au domaine 


<img width="375" alt="Capture 1 1" src="https://github.com/user-attachments/assets/2ee45b74-c096-47ae-8441-2cd53c677592" />







integration du client dans le domaine 


<img width="439" alt="Capture recup cli srv" src="https://github.com/user-attachments/assets/3218d495-e5e3-4dd5-b32f-d46f4eca4217" />


connexion machines nouveau utilisateurs




<img width="546" alt="Capture cl" src="https://github.com/user-attachments/assets/5f8c7dec-721b-4e00-8788-6860b3ed961c" />


Tester si les connexion marche entre un utilisateur  le client WIN et le SERVEUR 


<img width="509" alt="Capture ping new util" src="https://github.com/user-attachments/assets/b068d0c0-8261-4a39-b12f-aad023e31d4e" />



## - 5 Mise en place des pare-feu 

Configuration :
- Nom : FW01
- Type : pfsense
- Réseau : 3 interfaces WAN, LAN, DMZ
	- WAN : @IP dans la plage réseau de la box Internet
		- Gateway : @IP interne de la box internet
	- LAN : 10.0.0.254/24
	- DMZ : 172.16.0.254/24

  1- Configuration des résaux du VM


<img width="546" alt="Capture reseaux vm" src="https://github.com/user-attachments/assets/0466f1cf-aa0f-4080-8574-f71995a0c573" />


 
Interface aprés installation 


<img width="379" alt="Capture install pfsence" src="https://github.com/user-attachments/assets/6a0c7d0b-00fd-49af-81b0-03d717c74f3c" />


3- Modification des réseaux LAN et DMZ 
LAN

<img width="372" alt="Capture config LAN" src="https://github.com/user-attachments/assets/6aea5a27-6c36-47e5-ad98-1a6761ec81ec" />


DMZ 

<img width="379" alt="Capture config DMZ" src="https://github.com/user-attachments/assets/0807c633-8c41-4929-b52f-aab431ef3e20" />


4-Config final interface

<img width="395" alt="Capture interface 2" src="https://github.com/user-attachments/assets/b554366b-e18d-404b-99dd-40058ca507c7" />



5- Tester la connexion des réseaux 

Ping lan et DMZ 

<img width="497" alt="Capture ping Reseau LAN DMZ" src="https://github.com/user-attachments/assets/3eb43f76-3382-407e-96cc-8c501c7cfd86" />


6- Configuration plateforme pfsense 


<img width="506" alt="Capture config pfsense 1" src="https://github.com/user-attachments/assets/9ab3e398-589b-4c13-996b-a5ebb7c23fb0" />




<img width="523" alt="Capture config pfsense 2" src="https://github.com/user-attachments/assets/03dc8e6e-8a85-4290-8a89-ada318462b49" />








