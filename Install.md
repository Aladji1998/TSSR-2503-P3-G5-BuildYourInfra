
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
