# But du Projet-Docker
Ce projet consiste à dévellopper une infrastructure Dockercompose contenant un client, serveur et un parefeu de type docker. Le conteneur de type pare-feu va pouvoir lancer une image et des règles SHELL. L'implémentation des règles va se faire avec les règles postroutung en employant les iptables.

# Installation de Docker
Nous allons utilisé une machine debian sur laquelle on installera Docker. Une mise à jour est nécéssaire pour préparer la machine avec la commande : **apt-get update**
Puis on commence l'installation par les dépendances : **sudo apt-get install  curl apt-transport-https ca-certificates software-properties-common**
- Puis On ajoute la clé GPG avec la commande suivante: **curl -fsSL https://download.docker.com/linux/debian/gpg |  sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg**
Ensuite on installe et on vérifie que le docker fonction correctement:
![image](https://user-images.githubusercontent.com/66318278/170119519-50452215-9275-4aca-955d-0cb29ef3b3fa.png)
- On installe un Docker compose : 
![image](https://user-images.githubusercontent.com/66318278/170121369-5e51a985-e377-41c8-91ff-f7d6d9969651.png)
# Architecture des fichiers : 
On disposera d'un repository contenant l'architecture suivante :
- docker-compose.yml
- dossier client : client.py (il va renvoyer une requete au serveur pour récupérer les informations de la page web ) - Dockerfile 
- dossier server : server.py (reçoit l'information du client et lancera le serveur web) - Dockerfile- index.html
- dossier parefeur : clean.sh (initialise toutes les configurations iptables) - Dockerfile- firewall.sh 
# Composition des fichiers :
  - Docker-compose.yml 
 ![image](https://user-images.githubusercontent.com/66318278/170126786-f854dd1e-61e6-4b7b-af82-feb03075b403.png)
- Client.py
![image](https://user-images.githubusercontent.com/66318278/170127296-75800181-ad6b-4425-840b-329a0f24dadf.png)
- Dockerfile (client)

![image](https://user-images.githubusercontent.com/66318278/170127423-8ea9171d-fba2-4083-9919-555e31d4aba9.png)
- Server.py

![image](https://user-images.githubusercontent.com/66318278/170127893-224eba97-c9f2-494b-9931-ac7bf641c3d9.png)
- Dockerfile (server)

![image](https://user-images.githubusercontent.com/66318278/170127970-8809099a-85cf-4b64-94f4-d05ba1611bcf.png)
- Index.html

![image](https://user-images.githubusercontent.com/66318278/170128275-cb3035f6-f0d7-458e-a62e-b75114b15d84.png)
- Firewall.sh qui permettra d'initier les règles iprouting et iptables:

![image](https://user-images.githubusercontent.com/66318278/170128982-39cb1b70-a13c-401a-aff4-cce68a05da98.png)
- Dockerfile (firewall) contenant :
 ![image](https://user-images.githubusercontent.com/66318278/170129261-5302c41a-e0f8-4a93-8366-5d8baae3788a.png)
 # Mise en place de l'infrastructure et construction du dockercompose 
 J'ai éxécuté la commande docker-compose build pour construire mon docker-compose, mais j'ai une erreur qui s'affiche en m'indiquant que le compose n'est pas reconnue et le service ssh ne marche pas.
 # Pour lancer le docker-compose dans le cas où il a été fonctionnel, on lance la commande docker_compose up qui va permettre de lancer les 3 containers : Serveur, Client et Firewall
 Le serveur pourra donc lancer la page index.html pour le client.
 
