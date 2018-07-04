# Formation Github

## Bienvenue dans le Github de formation.
Généré à partir d'angular-cli, ce projet somme toute basique est ici pour
comprendre les mécaniques et rouages de Github tout en voyant directement son fonctionnement
à travers des cas pratiques ( loin de moi l'idée de concurrencer le wiki ou tout autre tutoriel précédemment proposé comme [celui ci](https://www.miximum.fr/blog/enfin-comprendre-git/ ), je souhaite juste mettre en place les commandes expliquées ).
Le but ici n'est pas de faire de vous des experts mais des utilisateurs qui posséderont les bases de ce gestionnaire de versions décentralisé pour ne pas avoir à se cacher lorsqu'il y a un problème.

![When git blame points to me](https://tclhost.com/AIszOw3.gif)

Avant de commencer, qu'est-ce que Github.

![Github Schema](http://borntocode.fr/wp-content/uploads/2016/01/git-centralized-vs-distributed.png)
[Source](http://borntocode.fr/git-tutoriel-et-configuration-sur-le-gestionnaire-de-versions/)

Ouhlà, ça fait beaucoup d'un coup tout ça ! Voyons plus en détail :

Aujourd'hui, les deux **gestionnaires de versions les plus utilisés** sont **SVN** (Subversion) et **Git** (GitHub), jusqu'ici tout va bien.

**GitHub est un gestionnaire de versions**, c'est à dire qu'il permet de gérer/stocker un ensemble de fichier tout en conversant un historique des modifications de ces derniers. De même, il est **décentralisé**, c'est-à-dire qu'il n'impose pas forcément de dépôt de référence et que chaque développeur ou développeuse travaille avec son propre dépôt en local qu'il synchronise avec ceux des autres ( si les besoins du projet s'en font ressentir, il est tout à fait possible d'ajouter un dépôt de référence ).

**SVN est un gestionnaire de versions centralisé**, qui lui, cette fois, est caractérisé par un **dépôt géré par un serveur**. Chaque utilisateur travaille sur une copie et synchronise son avancée/ses développements avec le dépôt central.

> Pourquoi je choisirai SVN à Github et inversement alors ?

Très bonne question, tout dépend de votre projet et des besoins de ce dernier. **EXPLIQUER**

> Quand est-ce qu'on passe à la pratique ?

Justement, j'y viens ! 

![C'est parti](https://media.giphy.com/media/13Qd06UWpuicJW/giphy.gif)

# Configuration de votre GitHub

**Si vous n'avez pas installé Git pour Windows, je vous suggère de le faire ! [Voici le lien de téléchargement](https://gitforwindows.org/)**

Après avoir installé Git, lancez-le (Git Bash) et commençons notre belle aventure.
Pour commencer par le commencement, il est important de **configurer Git**.

`git config --global user.name "Jean-Pierre Foucault"`. C'est ici que l'on définit son nom d'utilisateur pour les commits à venir.

`git config --global user.email jpfoucault@kiveutgagnerdelargentenmousse.com`. Ici, l'adresse email associée à votre compte.

Pour vérifier que tout est en ordre, tapez `git config --list` et faîtes attention à bien retrouver les éléments que vous avez enregistrés à l'aide des deux dernières commandes.

Une bonne chose de faîte, mais nous avons de la route devant nous. 

![Forrest Gump](https://media.giphy.com/media/D6uUoxFgRL1GU/giphy.gif)

Puisque la sécurité est au coeur des préoccupations, nous allons générer une clé SSH histoire de se connecter de manière sécurisée.
Et comme je suis feignant, je vous laisse suivre [un très bon tuto](https://gitlab.com/help/ssh/README#generating-a-new-ssh-key-pair) !


