# README : DockerCompose Node.js IIA Laval

## Technologies
  - **Docker** : version 20.10.16 (disponible sur MacOS 10.15 ou plus, Windows 10 21H2 ou plus, Linux)
  - **Nginx** : latest
  - **PhpMyAdmin** : latest
  - **MySql** : latest

## Architecture Docker
L'architecture Docker est construite de la manière suivante :
  - Un Network dans lequel on trouve plusieurs conteneurs :
      - Un conteneur Nginx (reverse proxy) par lequel tout passe.
      - Un conteneur contenant l'application
      - Un conteneur pour un gestion de la BDD avec PhpMyAdmin
      - Un conteneur MySQL pour la BDD

Tous les accès aux données et à la gestion de la base de données ainsi qu'à l'application passent par le conteneur Nginx. Les ports ne sont donc pas mappés dans le docker-compose pour des raisons de sécurité.

Un fichier ```.env``` doit être créé. Il contient les informations de la BDD (nom, credentials).

![schéma docker](https://user-images.githubusercontent.com/88578151/175386608-601fc360-59ef-427c-a63f-57acd115c612.png)

## Installation
Pour l'installation de cette configuration (ou orchestration) de Docker, il faut :

  - Avoir téléchargé et installé Docker (https://docs.docker.com/get-docker/)
  - Récupérer le fichier ```docker-compose.yml```
  - Le placer dans un répertoire (faire au plus simple, un dossier sur le bureau ira très bien)
  - Dans ce même répertoire, créer un fichier ```.env``` dans lequel il faut écrire :
  ```
  DB_NAME=appnodejsdb
  DB_USER=admin
  DB_PASSWORD=securiteavanttout
  ```
  - Ouvrir un terminal de commande et exécuter la commande suivante : ```docker compose up -d``` (***-d*** n'est pas obligatoire, il permet de détacher le processus de build dans le terminal)

## Utilisation
| URL | Destination |
| :---------------: | :---------------: |
| localhost ou localhost/ | Affichage brut des données de la Base de Données |
| localhost/admin ou localhost/admin/ | Accès à PhpMyAdmin |
