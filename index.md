---
titre: Docker
description: Présentation de Docker
---
## Introduction
- Les cas d'utilisation fournis sont illimités et le besoin a toujours été là. Docker est là pour vous offrir un moyen efficace et rapide de transférer des applications sur des systèmes et des machines. Il est léger et léger, vous permettant de contenir rapidement des applications et de les exécuter dans leurs propres environnements sécurisés.
- je souhaite vous présenter de manière approfondie Docker : l'un des projets open source les plus passionnants et les plus puissants à avoir vu le jour ces dernières années. Docker peut vous aider tellement qu'il est injuste d'essayer de résumer ses capacités en une phrase.

## Qu'est-ce que Docker ?
- Docker est un produit développé par la société du même nom. Initialement développé par un ingénieur français, Solomon Hykes, le produit a été dévoilé en mars 2013. Depuis cette date, Docker est devenu LE soft à la mode ! Nous allons voir à quoi il sert et comment vous pouvez vous en servir au quotidien.
- Docker est un logiciel libre permettant facilement de lancer des applications dans des conteneurs logiciels.
- Docker est un outil qui peut empaqueter une application et ses dépendances dans un conteneur isolé, qui pourra être exécuté sur n'importe quel serveur. Il ne s'agit pas de virtualisation, mais de conteneurisation, une forme plus légère qui s'appuie sur certaines parties de la machine hôte pour son fonctionnement. Cette approche permet d'accroître la flexibilité et la portabilité d’exécution d'une application, laquelle va pouvoir tourner de façon fiable et prédictible sur une grande variété de machines hôtes, que ce soit sur la machine locale, un cloud privé ou public, une machine nue, etc...
- Techniquement, Docker étend le format de conteneur Linux standard, LXC, avec une API de haut niveau fournissant une solution pratique de virtualisation qui exécute les processus de façon isolée. Pour arriver à ses fins, Docker utilise entre autre LXC, groups et le noyau Linux lui-même. Contrairement aux machines virtuelles traditionnelles, un conteneur Docker n'inclut pas de système d'exploitation, mais s'appuie au contraire sur les fonctionnalités du système d’exploitation fournies par la machine hôte.
- Que ce soit à partir de votre machine de développement à un serveur distant pour la production, ou tout l'empaquetage pour l'utilisation ailleurs, c'est toujours un défi quand il s'agit de porter votre pile d'application avec ses dépendances et de l'exécuter sans avoir des bogues. En fait, le défi est immense et les solutions n'ont jusqu'à présent pas vraiment réussi pour les masses. En un mot, docker en tant que projet vous offre l'ensemble complet d'outils de haut niveau pour transporter tout ce qui forme une application à travers les systèmes et les machines - virtuels ou physiques - et apporte avec lui de nombreux avantages. Docker réalise son encapsulation robuste des applications (et donc des processus et des ressources) via des conteneurs Linux (par exemple des espaces de noms et d'autres fonctionnalités du noyau). Ses capacités supplémentaires proviennent des composants et pièces internes d'un projet, qui extraient toute la complexité du travail avec les outils / API Linux de bas niveau utilisés pour la gestion des systèmes et des applications en ce qui concerne la sécurisation des processus.

### Docker, isoler un environnement ? Comme une VM ?

- Docker et les containers Linux ne se comportent pas de la même manière qu'une VM. Une machine virtuelle isole tout un système (son OS), et dispose de ses propres ressources.
- Dans le cas de  Docker, le kernel va partager les ressources du système hôte et interagir avec le(s) container(s). Techniquement, Docker n'est pas une VM, pas le moins du monde, mais en terme d'utilisation, Docker peut-être apparenté à une VM.
- Lancer un environnement, et isoler les composants de ce container avec les composants de mon hôte, voilà ce que Docker sait faire! Il le fait d'ailleurs très bien, et reste une alternative bien plus performante que les VMs (à utilisation équivalente).

### Principaux composants de Docker ?

Le projet Docker (ouvert par dotCloud en mars 2013) se compose de plusieurs parties principales (applications) et éléments (utilisés par ces parties) qui sont tous construits en se basant sur les fonctionnalités, bibliothèques et frameworks déjà existants proposés par le noyau Linux et d’élements externes (par exemple LXC, device-mapper, aufs, etc.).
-Principaux composants de Docker :
1.Daemon : utilisé pour gérer les conteneurs docker (LXC) sur l'hôte qu'il exécute
2.Image index : un référentiel (public ou privé) pour les images docker
3.CLI : utilisé pour commander et communiquer avec le démon docker 
4.Containers : répertoires contenant toute votre application.
5.Images : image de conteneurs ou du système d’exploitation de base (par exemple Ubuntu) .
6.Dockerfiles : scripts automatisant le processus de création des images.
-Les composants docker :
Les éléments suivants sont utilisés par les applications formant le projet docker.
-Containers :
Toute la procédure de portage des applications utilisant docker repose uniquement sur l'exécution des conteneurs. Les conteneurs Docker sont essentiellement des répertoires qui peuvent être empaquetés (par exemple archivés par tar) comme tous les autres, puis partagés et exécutés sur différentes machines et plates-formes (hôtes). La seule dépendance est d'avoir les hôtes à l'écoute pour exécuter les conteneurs (c'est-à-dire que le docker est installé). Le confinement est ici obtenu via Linux Containers (LXC).

### Les conteneurs docker ?
Les conteneurs Docker ont plusieurs caractéristiques principales. Ils permettent :
    -La portabilité d’applications
    -L’isolation de processus
    -Prévention de modification venant de l’extérieur
    -La gestion de l’utilisation des ressources
En plus, ils nécessitent beaucoup moins de ressources que les machines virtuelles traditionnelles utilisées pour le déploiement d’applications isolés. Ils ne permettent pas :
    -Le mélange avec d’autre processus
    -L’éxecution sur des systems d’exploitations différents
    -La vulnérabilité aux attaques et l’utilisation abusives des ressources du système hôte.
Étant basé et dépendant de LXC, d'un point de vue technique, ces conteneurs sont comme un répertoire (vide et formaté). Cela permet la portabilité et la construction progressive des conteneurs.
Chaque conteneur est superposé comme un oignon et chaque action prise dans un conteneur consiste à placer un autre bloc (qui se traduit en fait par un simple changement dans le système de fichiers) en plus du précédent. Et divers outils et configurations font que cette configuration fonctionne de manière harmonieuse (par exemple, système de fichiers union).
La disposition des conteneurs suivant cette architecture permet de démarrer et de créer facilement de nouveaux conteneurs et images. Ces conteneurs et images sont ainsi maintenus en étant légers (grâce à la manière graduelle et stratifiée sur lesquelles se base leurs créations). Puisque tout est basé sur le système de fichiers, prendre des images et effectuer des roll-backs dans le temps est moins couteux (c'est-à-dire très facile / pas lourd sur les ressources), tout comme les systèmes de contrôle de version.
Chaque conteneur docker commence à partir d’une image docker qui constitue la base pour les autres applications et couches à venir.

### Docker Images ?

Les images Docker constituent la base des conteneurs dockers à partir desquels tout commence à se former. Ils sont très similaires aux images de disque du système d'exploitation par défaut qui sont utilisées pour exécuter des applications sur des serveurs ou des ordinateurs de bureau.
Ces images (par exemple, la base Ubuntu) permettent une portabilité transparente sur tous les systèmes. Ils constituent une base solide, cohérente et fiable avec tout ce qui est nécessaire pour exécuter les applications. Lorsque tout est autonome et que le risque de mises à jour ou de modifications au niveau du système est éliminé, le conteneur devient immunisé contre les expositions externes qui pourraient le mettre hors service - empêchant ainsi les soucis de dépendances.
Au fur et à mesure que d'autres couches (outils, applications, etc.) sont ajoutées sur la base, de nouvelles images peuvent être formées en validant ces changements. Lorsqu'un nouveau conteneur est créé à partir d'une image enregistrée (c'est-à-dire validée), les choses continuent là où elles se sont arrêtées. Et le système de fichiers union réunit toutes les couches en une seule entité lorsque vous travaillez avec un conteneur.
Ces images de base peuvent être explicitement indiquées lorsque vous travaillez avec la CLI docker pour créer directement un nouveau conteneur ou elles peuvent être spécifiées dans un Dockerfile pour la création automatique d'images.

### Docker Images ?

Dockerfiles sont des scripts contenant une série successive d'instructions, de directions et de commandes qui doivent être exécutées pour former une nouvelle image docker. Chaque commande exécutée se traduit par une nouvelle couche de l'oignon, formant le produit final. Ils remplacent essentiellement le processus de tout faire manuellement et à plusieurs reprises. Quand un Dockerfiles a fini d'être exécuté, vous finissez par avoir une image formée, que vous utilisez ensuite pour commencer (c'est-à-dire créer) un nouveau conteneur.

### Installation de Docker ?

Au début, docker était uniquement disponible sur Ubuntu. De nos jours, il est possible de déployer docker sur les systèmes basés sur RHEL (par exemple CentOS) et d'autres aussi bien.
Je vais passer au processus d’installation sur un système Linux Ubuntu.
Installation Instructions for Ubuntu
Le moyen le plus simple d'obtenir docker, autre que l'utilisation d’une version pré compilé de l’image d’application, est d'utiliser un Ubuntu VPS 64 bits.
Mise à jour des paquets et dépôt :
sudo apt-get update
sudo apt-get -y upgrade
Vérification du support de l’aufs:
sudo apt-get install linux-image-extra-`uname -r`
Ajout du dépôt docker au sources Apt:
echo "deb https://apt.dockerproject.org/repo ubuntu-trusty main" | sudo tee /etc/apt/sources.list.d/docker.list
Mise à jour des dépôt en prenant en compte les derniers ajouts :
sudo apt-get update
Pour finir, télechargement et installation de docker :
sudo apt-get install docker-engine
Le pare-feu par défaut d'Ubuntu (UFW: Uncomplicated Firewall) refuse tout le trafic de transfert par défaut, ce qui est nécessaire pour le docker. Activer le transfert avec UFW: Mise à jour de la configuration UFW avec l’éditeur de texte nano.
sudo nano /etc/default/ufw
Descendez et trouvez la ligne commençant par DEFAULTFORWARDPOLICY. Remplacer:
DEFAULT_FORWARD_POLICY="DROP"
Par
DEFAULT_FORWARD_POLICY="ACCEPT"
Appuyez CTRL+X et valider avec Y pour sauvegarder et fermer. Pour finir, redémarrez UFW:
sudo ufw reload
Une fois docker installé, son utilisation intuitive le rend très facile à utiliser. À ce stade, le processus docker doit être exécuté en arrière-plan. Sinon, utilisez la commande suivante pour exécuter le démon docker. Pour démarer le processus daemon:
sudo docker -d
Syntaxe: L'utilisation de docker (via CLI) consiste à lui passer une chaîne d'options et de commandes suivies d'arguments. Il faut quand même se rappeler que docker a besoin de privilèges sudo afin de travailler.
sudo docker [option] [command] [arguments]

### Commençons par voir toutes les commandes disponibles du docker ?

Demander à docker une liste de toutes les commandes disponibles :
sudo docker
Toutes les commandes disponibles actuellement:
attach Attach to a running container
build Build a container from a Dockerfile
commit Create a new image from a container's changes
cp Copy files/folders from the containers filesystem to the host path
diff Inspect changes on a container's filesystem
events Get real time events from the server
export Stream the contents of a container as a tar archive
history Show the history of an image
images List images
import Create a new filesystem image from the contents
info Display system-wide information
insert Insert a file in an image
inspect Return low-level information on a container
kill Kill a running container
load Load an image from a tar archive
login Register or Login to the docker registry server
logs Fetch the logs of a container
port Lookup the public-facing port which is NAT-ed to PRIVATE_PORT
ps List containers
pull Pull an image or a repository from the docker server
push Push an image or a repository to the docker server
restart Restart a running container
rm Remove one or more containers
rmi Remove one or more images
run Run a command in a new container
save Save an image to a tar archive
search Search for an image in the docker index
start Start a stopped container
stop Stop a running container
tag Tag an image into a repository
top Lookup the running processes of a container
version Show the docker version information
wait Block until a container stops, then print its exit code

### Commençons par voir toutes les commandes disponibles du docker ?

Pour les informations système conçernant docker :
sudo docker info
Pour la version de docker :
sudo docker version
Travailler avec les images : Comme nous l'avons longuement évoqué, la clé pour commencer à travailler avec n'importe quel conteneur docker est d'utiliser des images. Il y a beaucoup d'images librement disponibles partagées à travers l'index d'image docker et la CLI permet un accès simple pour interroger le référentiel d'images et pour en télécharger de nouvelles. Lorsque vous êtes prêt, vous pouvez également partager votre image. Voir la section sur "partager" plus bas pour plus de détails.

### Travailler avec les images ?

Recherche d’une image docker :
sudo docker search ubuntu
Cela vous donnera une très longue liste de toutes les images disponibles correspondant à la requête : Ubuntu.
Téléchargement (récupération) une image. Soit lorsque vous construisez / créez un conteneur ou, avant de le faire, vous devez avoir une image présente sur la machine hôte où les conteneurs existeront. Afin de télécharger des images (peut-être après "recherche"), vous pouvez exécuter pull pour en obtenir un.
 Utilisation: sudo docker pull [nom]
sudo docker pull ubuntu

outes les images de votre système, y compris celles que vous avez créées en vous (voir ci-dessous pour plus de détails), peuvent être listées en utilisant "images". Ceci fournit une liste complète de tous ceux disponibles.
Liste des images :
sudo docker images
Ex :
REPOSITORY TAG IMAGE ID CREATED VIRTUAL SIZE
my_img latest 72461793453e 36 seconds ago 130 MB
ubuntu 14.04 8dcd1e456a96 8 months ago 130 MB
ubuntu latest 8dcd9e456a96 8 months ago 130 MB
ubuntu precise 8dcd9e456a96 8 months ago 130 MB
ubuntu 14.10 b453fe79269d 8 months ago 215.3 MB
ubuntu quantal b453fe79269d 8 months ago 215.3 MB

### Commit les changements concernant une image ?

Lorsque vous travaillez avec un conteneur et continuez à effectuer des actions (par exemple, télécharger et installer un logiciel, configurer des fichiers, etc.), pour qu'il conserve son état, vous devez effectuer un "commit". Le commit permet de s'assurer que tout reprend d'où ils sont partis la prochaine fois que vous en utilisez un (c'est-à-dire une image).
Utilisation: sudo docker commit [ID] [nom]
sudo docker commit 8dcd9e456a96 my_img
Partage d’images (PUSH) : Bien que ce fasse un peu moment que vous avez créé votre propre conteneur que vous aimeriez partager avec le reste du monde, vous pouvez utiliser push pour que votre image soit listée dans l'index où tout le monde peut le télécharger et l’utiliser. Rappelez-vous de “commit” après vos changements.
utilisation: sudo docker push [username/image name] 
sudo docker push my_username/my_first_image

### Travailler avec les Conteneurs ?

Lorsque vous "exécutez" un processus en utilisant une image, en retour, vous aurez un conteneur. Lorsque le processus n'est pas en cours d'exécution, ce conteneur sera un conteneur non-exécutant. Néanmoins, ils resteront tous sur votre système jusqu'à ce que vous les supprimiez via la commande rm.
Lister tous les conteneurs :
sudo docker ps
Pour avoir une liste complète de tout les processus, use:
sudo docker ps -l 
Création d’un nouveau conteneur :Il n'est actuellement pas possible de créer un conteneur sans exécuter quoi que ce soit (c'est-à-dire des commandes). Pour créer un nouveau conteneur, vous devez utiliser une image de base et spécifier une commande à exécuter.
sudo docker run my_image echo "test"
Utilisation: sudo docker run [image] [command]
sudo docker run my_image echo "test"
 Pour nommer un conteneur au lieu d’avoir un long ID
Usage: sudo docker run -name [name] [img] [com]
sudo docker run -name my_cnt my_image echo "test"
Exécution d’un conteneur :Lorsque vous créez un conteneur et qu'il s'arrête (soit en raison de la fin de son processus, soit en l'arrêtant explicitement), vous pouvez utiliser "run" pour que le conteneur fonctionne à nouveau avec la même commande que celle utilisée pour le créer.
 Utilisation: sudo docker run [ID]
sudo docker run c629b7d70666
Arrêter un conteneur :
 utilisation: sudo docker stop [ID]
sudo docker stop c629b7d70666
Sauvegarder (commit) un conteneur : Si vous souhaitez enregistrer la progression et les modifications effectuées avec un conteneur, vous pouvez utiliser "commit" comme expliqué ci-dessus pour l'enregistrer en tant qu'image. Cette commande transforme votre conteneur en une image. Rappelez-vous qu'avec docker, les commits sont bon marché. N'hésitez pas à les utiliser pour créer des images pour enregistrer votre progression avec un conteneur ou pour revenir en arrière lorsque vous avez besoin (par exemple, comme des images à temps).
Suppression d’un conteneur :En utilisant l'identifiant d'un conteneur, vous pouvez en supprimer avec rm.
Utilisation: sudo docker rm [ID]
sudo docker rm c629b7d70666

### Les avantages

Dans l’ensemble, en tant que développeur, l’utilisation de conteneurs peut me faciliter la vie.
Cela facilite le partage d’un même environnement entre devs.
Les dépendances seront les mêmes peu importe l’environnement. (Je suis sûr d’avoir la même version des outils que mes collègues) ?
Docker est cross-plateforme : les différences d’OS entre dev ne sont plus un soucis
Je travaille sur un environnement cloisonné.
Je dispose de solutions sur étagère grâce aux images open source à disposition.
Je peux faire des POCs rapides grâce aux images Docker sans polluer ma machine.
C’est plus rapide à démarrer/arrêter qu’une VM.
Cela accélère considérablement la boucle de feedback et la livraison en production.

### Conclusion

Grâce à Docker, multipliez les environnements sur votre machine, sans limiter les performances de votre ordinateur. Les ressources sont partagées avec la machine hôte ! Chaque environnement peut être configuré simplement grâce à son Dockerfile, présent à sa racine.
