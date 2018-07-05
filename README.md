# Formation Github

## Bienvenue dans le Github de formation.
Généré à partir d'angular-cli, ce projet somme toute basique est ici pour
comprendre les mécaniques et rouages de Github tout en voyant directement son fonctionnement
à travers des cas pratiques ( loin de moi l'idée de concurrencer tout autre tutoriel précédemment proposé comme [celui ci](https://www.miximum.fr/blog/enfin-comprendre-git/ ), je souhaite juste mettre en place les commandes expliquées ).
Le but ici n'est pas de faire de vous des experts mais des utilisateurs qui posséderont les bases de ce gestionnaire de versions décentralisé pour ne pas avoir à se cacher lorsqu'il y a un problème.

![When git blame points to me](https://tclhost.com/AIszOw3.gif)

Avant de commencer, qu'est-ce que Github.

![Github Schema](http://borntocode.fr/wp-content/uploads/2016/01/git-centralized-vs-distributed.png)
[Source](http://borntocode.fr/git-tutoriel-et-configuration-sur-le-gestionnaire-de-versions/)

Ouhlà, ça fait beaucoup d'un coup tout ça ! Voyons plus en détail :

Aujourd'hui, les deux **gestionnaires de versions les plus utilisés** sont **SVN** (Subversion) et **Git** (GitHub), jusqu'ici tout va bien.

**GitHub est un gestionnaire de versions**, c'est à dire qu'il permet de gérer/stocker un ensemble de fichiers tout en conversant un historique des modifications de ces derniers. De même, il est **décentralisé**, c'est-à-dire qu'il n'impose pas forcément de dépôt de référence et que chaque développeur ou développeuse travaille avec son propre dépôt en local qu'il synchronise avec ceux des autres ( si les besoins du projet s'en font ressentir, il est tout à fait possible d'ajouter un dépôt de référence ).

**SVN est un gestionnaire de versions centralisé**, qui lui, cette fois, est caractérisé par un **dépôt géré par un serveur**. Chaque utilisateur travaille sur une copie et synchronise son avancée/ses développements avec le dépôt central.

> Pourquoi je choisirai SVN à Github et inversement alors ?

Très bonne question, tout dépend de votre projet et des besoins de ce dernier. Pour un peu plus vous orienter, je vais vous donner les avantages et désavantages de chacun afin que vous soyiez à même de choisir quel gestionnaire de versions utiliser.

**SVN :**
  - Avantages :
    - **Facile d'utilisation :** On ne peut pas dire le contraire, avec l'éditeur TortoiseSVN, utiliser Subversion est devenu un jeu             d'enfant.
  - Inconvénients :
    - **Gestion des branches lourde :** SVN ne gère pas aussi bien les branches que Git. Pour créer une branche il faut copier tout le           projet avec la commande `svn copy`.
    - **Être connecté à Internet :** il est obligatoire d'avoir un accès internet pour envoyer son travail sur le dépôt distant, ce qui         est plutôt embarrassant si l'on souhaite travailler dans le train par exemple.

**Git :**
  - Avantages :
    - **Gestion des branches :** Il est possible de travailler sur plusieurs fonctionnalités du projet sans se marcher sur les pieds.
        On parle plus de diverger de la ligne principale de développement et continuer à travailler sans s'en préoccuper.
    - **Fusion des fichiers :** Il est possible de fusionner les modifications d'un fichier qui a été modifié par plusieurs personnes en         même temps. Git émettera un conflit en vous montrant ce qui a changé et vous n'aurez qu'à choisir ce que vous gardez.
    - **Mise à jour rapide :** Lorsque vous mettez à jour, les données sont empaquetées, compressées et les mises à jours fusionnées.
    - **Travailler sans Internet :** Petit exemple, vous vous retrouvez tout au fond de la Meuse et d'un coup vous prends l'idée                 d'avancer un travail, soit ( Nous prônons tout de même le droit à la déconnexion hein ). Pas d'internet ? Pas de problème, vous         pouvez commit votre travail et travailler sur une nouvelle fonctionnalité sans avoir à attendre de pusher, ce qui est réellement         pratique.
  - Inconvénients :
    - **Complexe :** En effet, il faut savoir que Git est bien plus complexe que SVN. Doté d'une pléthore de fonctionnalités, ce dernier         peut parfois être déroutant notamment avec la commande `git checkout` qui permet de changer de branche, de supprimer les                 modifications d'un fichier ou encore de voir votre projet dans un état précédent. Mais ne vous inquiétez pas, nous verrons tout         ça juste après.
    - **Les retours à la ligne :** Ils doivent tous être du même type (\n par exemple). On y pense pas forcément certes, mais si votre           petit copain à côté possède un éditeur qui fait des retours à la ligne de type \r\n, les conflits de merge vont pleuvoir et ça           deviendra vite ingérable.
    - **Les fichiers binaires :** Contrairement aux autres fichiers, les fichiers binaires ne sont pas de grands copains avec Git. À             chaque modification, git ne stocke que ce qui a changé depuis la dernière version. Dans le cas des fichiers binaires, il est             donc obligé de stocker la version complète du fichier à chaque modification, ce qui conduit rapidement à une augmentation               importante de la taille du dépôt.

> QUAND EST-CE QU'ON PASSE À LA PRATIQUE ?

Justement, j'y viens, pas besoin de crier nonmé

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

Puisque la sécurité est au coeur des préoccupations, il est fortement recommandé de générer une clé SSH histoire de se connecter de manière sécurisée ( mais aussi parce que s'identifier à chaque commit c'est légèrement lourd ). Ici, nous n'en auront pas besoin mais suivez tout de même [ce tuto](https://gitlab.com/help/ssh/README#generating-a-new-ssh-key-pair) si vous êtes curieux !

Bien, nous voilà fin prêts pour commencer à jouer avec GitHub. Mettez vous dans le dossier 'Documents' de votre arborescence de fichiers.

Récupérez le projet à l'aide de cette commande :

`git clone https://github.com/CorentinHcd/repo_de_test.git` Cela va vous créer un dossier nommé 'repo_de_test' ( original comme nom je vous l'accorde ) avec lequel nous allons interagir. Si vous souhaitez changer le nom de ce projet, vous n'avez qu'à spécifier le nom du répertoire dans lequel vous souhaitez le mettre : `git clone https://github.com/CorentinHcd/repo_de_test.git GithubRepo` ira dans le dossier GithubRepo.

Vous vous rappelez des branches ? Et bien nous y revoilà, appréhendons les :

![branch](https://github.com/CorentinHcd/repo_de_test/blob/master/screenshots/git_branch.PNG)

Tout d'abord, vérifions la liste des branches avec `git branch`. On s'aperçoit que l'on possède la '**master**' ( qui, dans tous les projets, représente le livrable, ce que l'on va rendre au client ) et la branche '**branche_maj_app_component**'. Cette branche est une copie de la branche master au moment du git branch et sert à développer une fonctionnalité indépendamment de la branche master. En d'autres termes, nous ne sommes pas obligés de travailler directement sur le produit livrable, nous travaillons sur une branche à part qui nous permet de ne pas impacter directement la master.

Petite astuce gratuite : Pour créer une branche et directement aller dessus, il vous suffit de lancer la commande `git checkout -b [nom_branche]` au lieu d'avoir à faire `git branch [nom_branche]` puis `git checkout [nom_branche]`.

Et bien à votre tour, créez une branche que vous appelez hello_world. Allez dans le projet et modifiez le fichier C:\Users\nomUtilisateur\Documents\nomDuRepo\src\app\app.component.ts en remplacant 'MAJ du titre' par 'Meilleur titre'.

Retournez sur Git Bash et tapez `git status`. Normalement, vous devriez vous retrouver avec ce résultat :

![status](https://github.com/CorentinHcd/repo_de_test/blob/branche_maj_app_component/screenshots/git_status.PNG)

> Mais ça représente quoi exactement ?

Et bien `git status` permet de connaître l'**état de votre dépôt**. En plus clair, savoir si des fichiers ont été modifiés, créés ou supprimés.

On va faire une autre manipulation, modifiez le fichier app.component.html en remplaçant 'Here are some links to help you start:' par ce que vous souhaitez écrire, faîtes vous plaisir.

Modifié ? Bien, allons-voir ce qu'il se passe quand on tape `git status`.

![status_2](https://github.com/CorentinHcd/repo_de_test/blob/branche_maj_app_component/screenshots/status_2.PNG)

Nous voilà avec deux fichiers modifiés et en rouge en plus, il doit nous manquer un truc non ?

Et bien on va jouer un peu avec, comme les fichiers sont connus de Git, ils se retrouvent dans l'état : `Changes not staged for commit`. 
Si ils n'étaient pas connus ( par exemple lorsque vous créez un fichier ), ils se retrouveraient dans l'état : `Untracked files`.

Maintenant, tapez `git add src/app/app.component.ts`. Cette commande va ajouter le fichier dans l'état : `Changes to be committed`.
Un exemple intéressant ici, disons que votre premier travail consiste à mettre à jour le titre puis votre second travail à mettre à jour le texte dans le HTML. Problème, vous avez fait tout le travail en même temps car c'était rapide et puis bon ça tuera personne hein. Effectivement et heureusement, cela ne tuera personne, mais on ne s'y retrouvera plus vraiment dans l'historique des modifications, c'est pourquoi il faut faire deux commits différents. Et c'est là que notre petite manipulation aide.

Tapez `git commit -m "MAJ titre"`.

**Explication :**
  ![statut_sequence](https://github.com/CorentinHcd/repo_de_test/blob/branche_maj_app_component/screenshots/git_status_sequence.png)

Vous comprenez mieux ?
C'est à dire que nous avons mis notre fichier dans notre répertoire local et que nous sommes dans le bon état pour pouvoir 'push' sur notre répertoire distant ( si nous en possédons un bien sûr ).

  - Astuces : 
    - Votre commit vous identifiant déjà grâce à la configuration de Git au préalable pas besoin de trigramme.
    - Votre commit doit posséder le numéro du usecase qu'il a résolu ( si il a un numéro), le cas échant, toujours expliquer ce que           corrige le commit.

Mais tiens donc, que se passe t-il ? vous avez fait une erreur !!!!

![erreur](https://media.giphy.com/media/bEVKYB487Lqxy/giphy.gif)

Cela arrive et ce n'est pas si grave. Mais ici, il s'avère que vous avez mal lu et que le message à mettre dans `app.component.ts` n'était pas 'Meilleur titre' mais 'Ohla on reset sa bêtise et on corrige', quelle coïncidence !

Bon, pas grave, parce qu'il y a une commande magique pour ça, c'est le `git reset`.

Cette commande permet de supprimer un fichier d'un état de staged, en quelque sorte, si vous ajoutez un dossier sur git mais que vous ne souhaitez pour l'instant qu'un seul fichier parmi les deux se trouvant dans le dit dossier, vous n'avez qu'à reset le fichier avec cette commande : `git reset [chemin_vers_le_dossier]/[nom_dossier]/[nom_fichier]`

> Mais quel rapport avec notre problème ?

Et bien le rapport, c'est que l'on va pouvoir enlever le fichier de l'état de staging grâce au git reset ! 
En effet, vous pouvez voir sur Git Bash si vous faîtes `git_status` une petite ligne au dessus de votre fichier : `use "git reset HEAD <file>..." to unstage`. Et oui Jamy, ils ont raison, le fait de reset notre fichier va l'enlever du dit état, et nous allons pouvoir le corriger pour que nous n'ayons pas à faire un autre commit pour le corriger par dessus.

> Mais attends, imagine j'avais push le tout sur mon répertoire distant ??

