
<div>
  <h1 align="center" position="relative">
    <a  href="https://github.com/armandwadji/Deploy-symfony-project.git" target='_blank'>DEPLOY SYMFONY PROJECT TO O2SWITCH 🖲
    </a> 
  </h1> 
</div> 

## Connecter vous à votre hébergeur puis créer un nom de domaine ou sous domaine :
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## rendez vous dans le repertoire créer, lors de la mise en place de votre sous domaine créer précédement:
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

## initialiser un fichier git avec la commande suivante :
```
git init
```

## Ajouter un remote correspondant au repository (Github ou Gitlab) distant de votre projet à installer, avec la commande suivante:
```
git remote add origin https://github.com/XXXXXXXXXXX
```

## installer le code source de votre projet dans le repertoire courant où vous vous trouvez : 
```
git remote pull origin main
```
## Maintenant installer les dépendances de votre projet mais en mode production avec la commande :
```
composer install --no-dev --optimize-autoloader
```

## une fois les dépendances insatller, créer un fichier d'environnement de production avec la commande :
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


