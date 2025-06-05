## Création des machines 

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













 
