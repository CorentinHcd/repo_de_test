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

Modifié ? Bien, allons-voir ce qu'il se passe quand on tape `git diff src/app/app.component.html`.
Et oui, cette commande permet de voir ce que vous avez modifié dans le fichier concerné, pratique non ?
En l'occurrence, 'Here are some links to help you start:' est en rouge car vous l'avez supprimé, on le remarque notamment avec le moins rouge et vous avez mis à la place votre texte qui est caractérisé par un + en vert.

De même, tapez `git status` :

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

Cette commande permet de supprimer un fichier d'un état de staged ( autrement dit un commit et donc modifier l'historique Git ), en quelque sorte, si vous ajoutez un dossier sur git mais que vous ne souhaitez pour l'instant qu'un seul fichier parmi les deux se trouvant dans le dit dossier, vous n'avez qu'à reset le fichier avec cette commande : `git reset [chemin_vers_le_dossier]/[nom_dossier]/[nom_fichier]`

De même, si vous souhaitez modifier un commit ( il manque un fichier par exemple ), utilisez la commande `git reset --soft HEAD^` (^ pour revenir d'un commit en arrière, ^^ deux commits, etc.). La commande `git reset --hard` est plus dangereuse c'est pourquoi je n'en parlerai pas ici.

> Mais quel rapport avec notre problème ?

Et bien le rapport, c'est que l'on va pouvoir enlever le fichier de l'état de staging grâce au git reset ! 
En effet, vous pouvez voir sur Git Bash si vous faîtes `git_status` une petite ligne au dessus de votre fichier : `use "git reset HEAD <file>..." to unstage`. Et oui Jamy, ils ont raison, le fait de reset notre fichier va l'enlever du dit état, et nous allons pouvoir le corriger pour que nous n'ayons pas à faire un autre commit pour le corriger par dessus.

> Mais attends, imagine j'avais push le tout sur mon répertoire distant ??

Toujours pas de panique, il aurait suffit de faire un `git revert`.

Je m'explique, git revert qu'est-ce que c'est ?
C'est un commit pour corriger un commit.

![commit](https://media.giphy.com/media/ANbD1CCdA3iI8/giphy.gif)

Mais encore ? Disons que vous avez commit une erreur, mais que vous voulez que les autres la voient pour pas qu'ils la reproduisent, et bien cette commande tombe à point, l'historique de Git est conservé et vous pouvez expliquer ce qui ne va pas dans votre commit et comment éviter cela la prochaine fois.

On en était où déjà nous ? Ah oui le git reset, retournons-y.

Tapez `git reset src/app/app.component.ts`, ouf, le fichier revient bien en rouge et dans l'état avant le commit et c'est parti pour le corriger, changez 'Meilleur titre' par 'Ohla on reset sa bêtise et on corrige'. On a l'air bon, ajoutez juste ce fichier ( car rappelez vous, nous souhaitons faire deux commits différents ) avec la commande `git add src/app/app.component.ts`.

Créez votre commit et n'oubliez pas ce que je vous ai dit plus haut sur les commits puis pushez avec cette commande `git push`.

ALEEEEEERTE !!!

- [x] Créer un commit
- [X] Push mon commit
- [ ] Set upstream

Et bien là encore, nous nous retrouvons bloqués ( promis c'est la dernière fois ).
Il s'avère que nous n'avons absolument pas spécifié à Git de se souvenir qu'un `git push` de notre branche hello_world envoie les changements à la branche hello_world sur le dépôt distant. Après l'avoir spécifié, il sera possible de juste écrire `git push`.

tapez `git push --set-upstream origin hello_world`. Ouf le push se passe bien, enfin finit les problèmes.

![success](https://media.giphy.com/media/XreQmk7ETCak0/giphy.gif)

Allons voir du côté des logs !

Tapez `git log` et regardez ce que vous obtenez.
Vous pouvez apercevoir le numéro du commit, l'auteur, la date et le message du commit juste en dessous, en gros, la liste des commits.

Si vous êtes plus tâtillon et souhaitez afficher les différents commits sur une seule ligne, il vous suffit de taper `git log --oneline --graph --decorate`.
Vous pouvez aussi :
  - Filtrer par auteur
    - `git log --author="nomAuteur"`
  - Filtrer par fichier
    - `git log -- [nomFichier]`
  - Filtrer par message
    - `git log --grep="nomDuMessageQueVousCherchez"`

Bon, plus qu'un commit et on est bon je crois !

Ouplà, attention DANGER !!!

![danger](https://media.giphy.com/media/3ohc11UljvpPKWeNva/giphy.gif)

Ohlà d'accord, bon bah juste attention alors...

Il s'avère que nous nous sommes trompés et que ce travail à faire n'est que plus tard et n'est pas prioritaire et c'est là que `git checkout` intervient. Cette commande permet beaucoup de choses, listons en 3 :
  - Supprimer les modifications d'un fichier :
    - `git checkout chemin/vers/le/fichier`
  - Changer de branche : Vous vous rappelez de ma petite astuce de tout à l'heure ? Bon pas grave, au lieu de créer une branche avec         `git branch` puis d'utiliser `git checkout` pour aller sur cette branche, l'utilisation de la commande `git checkout -b                 [nomBranche]` s'occupe de faire le tout en 1, un peu comme un liquide vaisselle.
  - Détachement du HEAD :
    - Si vous souhaitez voir votre projet dans un état précédent, vous pouvez le faire via cette commande : `git checkout HEAD^` (^           revient d'un commit, ^^ de deux, etc).

> Je suis perdu entre git checkout, git reset et git revert !!

![lost](https://media.giphy.com/media/3o7aCTPPm4OHfRLSH6/giphy.gif)

Pas de problème, c'est assez dur à assimiler mais avec la pratique aucun souci, je vais quand même faire un rappel.

``git checkout``: Expliqué juste au dessus, servira essentiellement à la **création de branche** et à la **suppression des modifications d'un fichier**.

``git reset``: Sert à **supprimer un fichier d'un état de staged** mais aussi de **de revenir d'un ou plusieurs commits en arrière**.

``git revert``: Plus souple que le git reset, il permet de **garder un historique des modifications**. Il va **supprimer les modifications d'un commit dans un nouveau commit**.
  
Allez, on tape `git checkout src/app/app.component.html`.
Si l'on tape `git status`, rien ne devrait apparaître et tant mieux.
Nos modifications ont bien été faîtes et supposons qu'elles ont été vérifiées, il va être maintenant temps de la merger. Mais pas trop vite, en temps normal, la branche master (origin) bouge énormement et de nombreux commits l'impactent, il est donc important de récupérer ce qu'il y a sur la master pour se mettre à jour et éviter tout conflit.

Au lieu d'un `git pull` qui s'occupe de faire un `git fetch + git merge`, ce qui peut engendrer des conflits, il est préférable de faire un `git fetch` puis un `git rebase`. `git fetch` s'occupe de récupérer les références et objets du dépôt distant et le merge s'occupe de fusionner le tout. `git rebase` quand à lui s'occupe d'appliquer les commits sur le dessus de la branche avec laquelle on souhaite travailler.

![rebase](https://github.com/CorentinHcd/repo_de_test/blob/branche_maj_app_component/screenshots/rebase.png)

[Volé sans scrupule](https://wodric.com/commandes-git-2/)

> Une petite explication ?

Il s'avère que dans ce cas précis le git pull n'est pas un problème, mais si j’ai effectué des modifications sur la même branche, il va alors faire un commit de merge, ce qui n’a pas vraiment de sens car on veut uniquement mettre à jour notre branche et surtout pas enrichir notre projet avec une nouvelle fonctionnalité, il ne serait pas très judicieux de laisser un commit dans l’historique pour des raisons techniques… Pour contourner le problème il faut utiliser le rebase pour réécrire l’historique.

Attention toutefois avec le rebase, son principe est de mettre à plat notre branche et, par conséquent, perdre les précédents commits de merge... Pour contourner ce problème :
`git fetch + git rebase origin/[nomBranche] --preserve-merges`. Le rebase gardera alors vos commits de merge et ajoutera bien les fonctionnalités à votre branche.

`Git merge` quand à lui, s'occupera de fusionner vos modifications avec la branche principale, sauf qu'il peut y avoir des conflits...
Si le nombre de conflits est trop important il est toujours possible d'attendre quelqu'un pour vous aider en exécutant la commande `git merge --abort`. Cela remettra le dépôt à l'état avant ce maudit merge.

> Comment résoudre un conflit ?

Et bien, il suffit de sélectionner les parties qui ont un intérêt et supprimer celles qui n'en ont plus, les lignes qui posent problème sont entourées par <<<<< ou =====. 

![merge_conflict](https://github.com/CorentinHcd/repo_de_test/blob/branche_maj_app_component/screenshots/merge_conflit.png)

Lorsque tout est résolu, on doit ajouter le fichier que l'on a modifié avec la commande `git add` puis le commiter en tout bien tout honneur.

Pfiou, on en a vu des choses jusqu'ici vous vous en rappelez ?

Un petit résumé de tout ça ferait pas de mal :

  - `git clone` : Permet de cloner un répertoire distant sur en local.
  - `git add` : Permet d'ajouter un fichier pour pouvoir l'associer au prochain commit.
  - `git commit` : Permet d'identifier les fonctionnalités que vous avez développés.
  - `git push` : Permet de pousser son travail sur le répertoire distant.
  - `git rebase` : Permet d'être à jour avec la branche avec laquelle on souhaite travailler et permet d'éviter les conflits.
  - `git reset` : Permet de supprimer un fichier d'un état de staged mais aussi de revenir d'un ou plusieurs commits en arrière.
  - `git revert` : Permet de supprimer les modifications d'un commit dans un autre commit.
  - `git checkout` : Permet de créer/changer de branche, de supprimer les modifications d'un fichier mais aussi de voir son projet dans      un état précédent.
  - `git pull` : Permet de récupérer les données sur le répertoire distant et de les merger avec la branche avec laquelle on souhaite        travailler.
  - `git fetch` : Permet de récupérer les données sur le répertoire distant sans les merger.
  - `git merge` : Permet de fusionner les modifications.
  
Ce tutoriel n'est encore qu'une ébauche et vise à être amélioré, toutes les remarques seront prises en compte et appréciées.
