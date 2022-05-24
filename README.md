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
![image](https://user-images.githubusercontent.com/66318278/170124358-69e3a40c-992d-497d-b02b-3811754092b9.png)
![image](https://user-images.githubusercontent.com/66318278/170124463-010eac9c-d9d4-4897-bb76-b9cf59b975b3.png)
![image](https://user-images.githubusercontent.com/66318278/170124506-86bbc0b9-c32a-4a78-9e31-ae3580692910.png)

