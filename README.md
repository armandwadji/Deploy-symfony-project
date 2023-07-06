
<div>
  <h1 align="center" position="relative">
    <a  href="https://github.com/armandwadji/Deploy-symfony-project.git" target='_blank'>DEPLOY SYMFONY PROJECT TO O2SWITCH 🖲
    </a> 
  </h1> 
</div> 

## Connecter vous à votre hébergeur puis créer un nom de domaine :

<img alt="create domaine name" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/554a916c-bd26-4865-8d89-ae9241ad02de">


## rendez vous dans le repertoire créer, lors de la mise en place de votre sous domaine via le terminal du serveur:
Ce dossier a le même nom que le nom de domaine.

<div style="display: flex; flex-direction: row;">
  <img alt="search terminal" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/77d214c4-d461-46b3-ba58-f496d817243d">
  <img alt="terminal in the project" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/0b5ec3f3-825f-4402-be8d-fdd75fcf423e">
</div>

## initialiser un fichier git dans ce dossier avec la commande suivante :
```
git init
```

## Ajouter un remote correspondant au repository `(Github ou Gitlab)` distant de votre projet à installer, avec la commande suivante:
```
git remote add origin https://github.com/XXXXXXXXXXX
```
`Explication`: cette commande demande à Git, de nous ajouter une ancre que l'on appelera `origin` et qui pointera vers le lien `https://` suivant. 
Ce lien correpond au lien de notre dépôt distant.

## installer le code source de votre projet dans le repertoire courant où vous vous trouvez : 
Saisissez la commande suivante : 
```
git pull origin main
```
Si vous allez dans votre gestionnaire de fichier vous verez apparaitre l'arborescence de votre projet symfony.

<img alt="skeleton project" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/1ae6367b-a4da-4ad6-8d0f-84457f69c8f9">

`Attention :` avant de poursuivre le process, veuillez à l'aide de votre terminale, vous mettre sur la branche que vous voulez déployé.
Dans notre cas, nous voulons deployé la branche `main` (anciennement aussi nommé `master` en fonction de votre hebergeur de code)

## Maintenant installer les dépendances de votre projet mais en mode production avec la commande :
```
composer install --no-dev --optimize-autoloader
```
Un dossier `vendor` contenant toute les dépendances de notre projet à été créer.

<img alt="vendor folder" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/b436b819-d535-48e6-9d2c-25f14dc9bdcc">

## une fois les dépendances installées, créer un fichier d'environnement de production avec la commande :
```
composer dump-env prod
```
cette commande créer un fichier .env.local.php à partir des informations présentent dans votre fichier .env
<img alt=".env.local.php folder" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/37c6c6b2-bfb6-4f3a-b874-219d263b13c4">

## Editer le fichier .env.local.php créer en y insérant tous les éléments nécéssaire au bon fonctionnement de votre parojet:
## Exemple: connection base de donnée, ...
pour cela vous devez vous rendre dans l'option `Base de données MYSQL` pour créer une base de donnée et y attribuer un utilisateur.
Veuillez à bien conserver les informations tels que `nom de la base de donnée`, `nom de l'utilisateur`, `mot de passe de l'utilisateur`. Elles vous seront utiles pour la suite.

<div style="display: flex; flex-direction: row;">
  <img width="500px" height='400px' alt="create database" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/7eb2a267-0a9c-4136-b4ea-a15ceac27c4a">
  <img width="500px" height='400px' alt="create user database" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/c048f247-7191-4deb-bc98-e27a994576e8">
</div>

une fois la base de donnée et l'utilsateur crées, il vous suffit d'édité le fichier `.env.local.php` pour y inscrire les information de connection de votre projet à cette base.
Vous pouvez utilisé des éditeurs tels que `vim` ou `nano`. Dans notre cas nous utiliserons `nano`.

<img alt="connexion database" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/46b93725-4c95-4e58-a397-144492ee8758">

##Aller dans les paramètres de votre nom de domaine:
Dans votre document root `(File system location)`, vous devez rajouter un `/public` car c'est dans ce dossier que le serveur va aller chercher le fichier index.php qui permet de démarrer la racine du projet.

<img alt="create domaine name" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/6b5ab494-a49d-42a8-8707-f781107dcfe9">


## Tapez la commande suivant pour la gestion des réécritures des différentes routes définit dans votre projet :
Si vous éssayez de vous rendre sur un endpoint autre que la racine du projet `/`, vous vous rendez compte que vous avez une erreur. Pour remédier à cela, il faut installer le bundle `apache-pack` de symfony pour qu'il se charge de réecrire tous nos endpoints.

```
composer require symfony/apache-pack
```

## Mettez en place un checker pour mettre en place des outils d'exigences de productins différentes de celle présente en mode dévéloppement dans la console `symfony CLI`:
```
composer require symfony/requirements-checker
```

## Il est conseiller de supprimer le cache du projet avant de le lancer avec la commande suivante :
```
APP_ENV=prod APP_DEBUG=0 php bin/console cache:clear
```

## Pour plus d'informations, reférez vous à la [documentation officiel de symfony][symfony]

## Enfin connecter vous à votre projet en saisiant votre nom de domaine dans le navigateur de votre choix :

<p align="right">Back to top :
  <a href="#top">
    ☝
  </a>
</p>

<h1 align="center">Bon Code 🖥 💻 📱</h1>

[symfony]: https://symfony.com/doc/current/deployment.html#symfony-deployment-basics

