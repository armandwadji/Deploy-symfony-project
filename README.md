
<div>
  <h1 align="center" position="relative">
    <a  href="https://github.com/armandwadji/Deploy-symfony-project.git" target='_blank'>DEPLOY SYMFONY PROJECT TO O2SWITCH 🖲
    </a> 
  </h1> 
</div> 

## Connecter vous à votre hébergeur puis créer un nom de domaine :
Attention: dans votre document root `(File system location)`, vous devez rajouter un `/public` car c'est dans ce dossier que le serveur va aller chercher le fichier index.php qui permet de démarrer la racine du projet.

<img alt="create domaine name" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/20a4339e-53e2-4414-8299-5f12285cc6b9">

## rendez vous dans le repertoire créer, lors de la mise en place de votre sous domaine via le terminal du serveur:
Ce dossier a le même nom que le nom de domaine.

<div style="display: flex; flex-direction: row;">
  <img alt="create domaine name" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/b60df397-1fdf-4bed-9ceb-a39ef3ed9b2d">
  <img alt="create domaine name" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/7e850d8f-dd2c-43c1-8b1f-d3e58609a355">
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
<img alt="create domaine name" src="https://github.com/armandwadji/Deploy-symfony-project/assets/90448006/35fae6fc-c9ff-4559-bcd2-82da625a1c6d">

`Attention :` avant de poursuivre le process, veuillez vous mettre sur la branche que vous voulez déployé.
Dans notre cas, nous voulons deployé la branche `main` (nommé aussi master en fonction de votre hebergeur de code)

## Maintenant installer les dépendances de votre projet mais en mode production avec la commande :
```
composer install --no-dev --optimize-autoloader
```
Un dossier `vendor` contenant toute les dépendances de notre projet à été créer.

## une fois les dépendances installées, créer un fichier d'environnement de production avec la commande :
```
composer dump-env prod
```

## Editer le fichier .env.local.php créer en y insérant tous les éléments nécéssaire au bon fonctionnement de votre parojet:
## Exemple: connection base de donnée, ...
```
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

## Tapez la commande suivant pour la gestion des réécritures des différentes routes définit dans votre projet :
```
composer require symfony/apache-pack
```

## Mettez en place un checker pour l'envoie des log d'erreurs :
```
composer require symfony/requirements-checker
```

## Il est conseiller de supprimer le cache du projet avant de le lancer avec la commande suivante :
```
APP_ENV=prod APP_DEBUG=0 php bin/console cache:clear
```

## Enfin connecter vous à votre projet :

<p align="right">Back to top :
  <a href="#top">
    ☝
  </a>
</p>

<h1 align="center">Bon Code 🖥 💻 📱</h1>


