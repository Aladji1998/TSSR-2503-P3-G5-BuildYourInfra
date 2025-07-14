Pour la mise en place de mon projet j'ai mis en place ces éléments suivants 

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




























## 6- FreePBX 

VM à créer - FreePBX

Configuration :
- Nom : IPBX01
- Type : FreePBX
- Réseau : @IP fixe => 192.168.1.179 

Tâches :
- Création de lignes VoIP pour les utilisateurs déjà créer
- Validation de communication téléphonique VoIP entre 2 clients VoIP sur serveur et client Windows


a- Configuration et mise en place du VM
Configration du réseau 

<img width="447" alt="Capture config réseau" src="https://github.com/user-attachments/assets/4a46e264-6348-483e-920a-37bc2c8ca02a" />


b- Fin installation IPBX01 

<img width="419" alt="Capture interface" src="https://github.com/user-attachments/assets/edf12538-fd05-4b83-8821-4dbe95a9a5cf" />


c-  Connexion via site avec adresse ip qui affiche l'interface du site 


<img width="524" alt="Capture site" src="https://github.com/user-attachments/assets/fd361511-db6e-42af-9a64-6b13adbb93fc" />



- configuration du site 


<img width="589" alt="Capture intface 1" src="https://github.com/user-attachments/assets/575a077a-7d12-4dec-bfcb-ce87558d31a3" />





<img width="477" alt="Capture intface 2" src="https://github.com/user-attachments/assets/7f1a9dd8-ec77-4b53-953a-949661c3c0cb" />





<img width="501" alt="Capture intface 3" src="https://github.com/user-attachments/assets/9edb3c49-b3c8-49f8-81d6-47e2963fc2b7" />





<img width="673" alt="Captureconfig firewal" src="https://github.com/user-attachments/assets/c8f1922f-6634-40cd-b45d-89e8637b9977" />




<img width="668" alt="Capture config freepbx" src="https://github.com/user-attachments/assets/49fb808c-95b7-452b-a39c-4bf34c9f5d3c" />




<img width="666" alt="Capture inface" src="https://github.com/user-attachments/assets/bc2a30e6-894e-4cfc-b63d-664c01feae08" />




d- Création des lignes VOIP 

- Ajout des postes


<img width="652" alt="Capture ajout poste" src="https://github.com/user-attachments/assets/c9ae9158-0681-4378-b51c-1249402c64bf" />





- ajout client 


<img width="603" alt="Capture poste 1" src="https://github.com/user-attachments/assets/7409d34b-ba0f-4c38-939d-19d9e1c8b5e2" />




<img width="599" alt="Capture client" src="https://github.com/user-attachments/assets/bd069584-8380-443a-9cf0-b239fcc6a200" />



e- Configuration de 3CXPhone 

Pour mon projet je vais utiliser le logiciel 3CXPhone pour pouvoir passer les appel entre les clients 



<img width="139" alt="Capture call" src="https://github.com/user-attachments/assets/72d919ea-702a-4599-b1a4-815a91634741" />



- config client 1 sur 3CXPhone



<img width="305" alt="Capture 3cx" src="https://github.com/user-attachments/assets/c7d556a1-8d53-4d4c-a760-ea1affc6bbd7" />




- Config client 2



<img width="234" alt="Capture client 2" src="https://github.com/user-attachments/assets/ac0ae811-db39-45da-bb35-3888e0da95af" />




- Test de connexion des appels

<img width="152" alt="Capture connexion client" src="https://github.com/user-attachments/assets/c66b12cd-7f77-4cd6-9cbc-98222de02720" />












 <img width="431" alt="Capture essaye appel" src="https://github.com/user-attachments/assets/3e3d5d7c-a6da-4ed5-bb6b-a259994bec53" />


pour faire les test j'ai aussi utiliser un autre logiciel pour faire les test Zoiper5




<img width="382" alt="Capture client 3" src="https://github.com/user-attachments/assets/3b3371dc-224a-40ce-a2ab-884e48242f7c" />






<img width="382" alt="Capture cli 3" src="https://github.com/user-attachments/assets/fd9a8d4d-49c1-4a90-b533-c63c889268e9" />




<img width="397" alt="Capture conf cli 3" src="https://github.com/user-attachments/assets/72d9f450-ae0a-426e-93b7-40c8109cfc51" />







- appel du client 3 avec les autres clients 


<img width="496" alt="Capture client  appel" src="https://github.com/user-attachments/assets/171cb112-b128-43c1-8238-b3850b04f6ad" />

