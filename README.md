# PROJET DE CLOUD COMPUTING

### Objectifs
Ce TP a pour objectif la réalisation d’une architecture web basée sur le cloud computing. Pour ce faire, nous avons opté pour Amazon Aws qui est le leader dans le domaine. 
A la fin de ce TP, chaque étudiant devra être capable de :
1.	Réaliser l’architecture suivante sur Amazon Aws: 
2.	Créer une machine virtuelle et y accéder avec un client SSH
3.	Créer une base de données et y accéder avec le client Workbench
4.	Créer une application Laravel et déployer cette application sur un serveur d’application nginx 

### Description
Amazon Web Services (AWS) est une plateforme évolutive complète de Cloud computing proposée par Amazon.com. Il est le fournisseur de cloud le plus sollicité dans le monde entier. Cette première partie du TP consistera à créer un compte sur amazon aws.

### Partie 1 : Création d’un compte sur Amazon AWS
1.	Ouvrer le lien https://aws.amazon.com sur votre navigateur.
2.	Cliquez sur Créer un compte AWS gratuit
3.	Suivez ensuite les étapes de création de votre compte, en indiquant que vous voulez créer un compte gratuitement

### Partie 2 : Service EC2

- EC2 (Elastic Compute Cloud) est un service de AWS qui vous permet de crée une machine virtuelle sur le Cloud d'Amazon. 
- Un compte AWS fournit plusieurs Régions afin que vous puissiez lancer des instances Amazon EC2 dans des emplacements qui satisfont vos exigences. Par exemple, vous pouvez souhaiter lancer des instances en Europe afin d'être plus proche de vos clients européens ou pour satisfaire à des exigences légales.

#### Création d’une machine virtuelle
1.	Connectez-vous à votre compte créé précédemment pour accéder à votre comsole.
2.	Cliquez sur services, puis sur EC2
 
-	Sur le menu de gauche, vous avez la possibilité d’afficher la liste de vos machines virtuelles. Cliquez sur 

-	Sur la nouvelle interface, choisissez les caractéristiques suivantes pour la création de votre machine virtuelle.
o	Le nom TP1 Cloud Computing
o	Une image 64 bits (x86) Ubuntu Server 22.04 LTS (HVM), SSD Volume Type
o	Une instance de type t2.micro (1 vCPU, 1GiB RAM)
o	Ne mettez aucune paire de clé. Le service EC2 se chargera de le faire. Une fois téléchargé, copiez-le en lieu sûr, car elle est générée une seule fois. Cette clé sera utilisée par le client SSH pour accéder à la machine virtuelle.
o	Laissez les paramètres réseau par défaut
o	Au niveau du stockage, augmentez à 10GiB pour un volume SSD à usage général (gp2)
o	Cliquez ensuite sur lancer l’image 

#### Questions : 
-	Quel sont les différent état la machine virtuelle que vous avez créée ?
-	Quelles sont les adresse IP publique et privée de votre machine virtuelle ?

### Partie 3 : Connexion à une VM

Sur la VM précédente, cliquez sur connexion. Dans la nouvelle interface, vous avez tous les méthodes de connexion à la machine virtuelle.
 
#### Connexion par EC2 Instance Connect
-	Cliquez sur l’onglet EC2 Instance Connect.
-	Resigné ensuite le nom d’utilisateur associé utilisé lors de la création de la machine virtuelle. Par défaut, le nom qui s’affiche est le bon. 
-	Cliquez ensuite sur Se connecter. Vous allez alors voir l’interface suivante vous permettant de contrôler votre VM.
 

#### Connexion par un client SSH
-	Cliquez sur l’onglet client SSH
-	Vous avez alors la procédure pour vous connecter à votre VM, soit en utilisant un client spécialisé, soit en passant directement par la console (terminal) du système d’exploitation
Console de l’OS :
Entrer la commande suivante dans le terminal : ssh -i "Clé Instance.pem" nom-utilisateur@adresse-intance. 
o	« Clé Instance.pem » est la clé que vous avez télécharger lors de la création. Vous devez renseigner le chemin complet.
o	nom-utilisateur est le nom d’utilisateur renseigné toujours lors du processus de création de la VM
o	adresse-intance est l’adresse ip publique ou le nom de domaine de votre VM.

#### Client SSH spécialisé : PuTTY
PuTTY est un client SSH Open source, développé à l'origine par Simon Tatham pour la plateforme Windows. Nous allons l’utiliser dans cadre de ce TP
o	Allez sur le site https://www.putty.org et télécharge PuTTY
o	Installer le logiciel et lancer le
 
o	Au niveau de nom d’haute, renseigner l’adresse IP publique ou le nom de domaine de votre machine virtuelle.
o	Vérifié que vous êtes sur le port 22
o	Cliquez ensuite sur SSH, puis sur Auth et télécharger la clé que vous avez téléchargé lors de la création de votre VM. Cette clé sera utilisée par le client SSH pour vous connecter
o	Cliquez ensuite sur Open et renseigner les informations comme nom d’utilisateur mot de passe en cas de besoin.

### Installation de notre première application Web
Nous allons maintenant installer et configurer notre application laravel.
*	Ouvre l’invite de commande et tapez les commandes suivantes :
    * $ cd /usr/share/nginx/html
*	Nous allons maintenant installer les dépendances de php par les commandes suivantes
    * $ sudo apt install php-mbstring php-xml php-bcmath
*	Nous allons maintenant installer composer qui va nous aider à créer un projet laravel
    * $ php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    * $ COMPOSER=CHAINE COMPOSER (Chaine de caractère affiché par la commande précédente)
    * $ sudo apt-get install curl php-cli php-mbstring git unzip
    * $ sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
    * $ composer –version (Pour vérifier que tout s’est bien passé)
* Nous pouvons à présent installer laravel. Nous allons l’appeler simplement tp1
    * $ composer create-project --prefer-dist laravel/laravel tp1
    * $ cd tp1
    * $ sudo chown -R www-data.www-data storage
    * $ sudo chown -R www-data.www-data bootstrap/cache




