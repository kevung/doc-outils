# Git

Ces commandes se lancent dans le dossier du dépot Git dans :

- un terminal (Linux/Mac)
- Git Bash

Les fichiers au sein d'un dépot sont :

- soit *non suivis* (*untracked*): Git ne se préocupe pas de suivre leur
  évolution dans le temps.

- soit *suivis mais non validés* (*unstaged*): Git indiquera si ces
  fichiers ont été modifiés par rapport à la dernière version archivée.

- soit *suivis et validés* (*staged*): ce sont les fichier suivis par
  Git dont on veut que leur modification soit sauvegardée pour la
  prochaine version archivée du dépot.

Git n'enregistre que les modifications effectuées sur les fichiers (et
non le fichier entier)

## Configuration initiale

L'éditeur par défaut de Git est Vim, qui peut être déroutant au premier
abord. Pour que Git utilise à la place Notepad`, taper la commande:

- `git config --global core.editor "Notepad"`.

Lorsque l'on est plusieurs à travailler sur un dépot, il est bon de
savoir qui a écrit quoi. Renseigner donc son identité une fois pour
toute à Git:

- `git config --global user.name "Franklin Latortue"`

- `git config --global user.email "franklin.latortue@coolraoul.net"`

Les retours à la ligne ne sont pas traités de la même manière sous Unix
(LF=Line Feed) et sous Windows (CRLF=Carriage+Line Feed). Etant donné
que des scripts conçus originellement pour Unix sont dans le dépot, le
retour à la ligne Unix fait référence.

Si vous travaillez sous Windows, la commande suivante convertira
automatiquement les retours à la ligne lors des commits:

- `git config --global core.autocrlf true`

Si vous travaillez sous Unix, la commande suivante corrigera lorsque
nécessaire les retours à la ligne CRLF qui se seraient glissés:

- `git config --global core.autocrlf input`

[source](https://stackoverflow.com/questions/5834014/lf-will-be-replaced-by-crlf-in-git-what-is-that-and-is-it-important)

## Workflow typique

### Faire au tout début une fois seulement:

- cloner un dépot existant:
  `git clone https://github.com/floraweissgerber/fonctionnel.git`

- ou initialiser un nouveau dépot dans un dossier:
  `git init`

### Habituellement

- afficher l'état du dépot (faire souvent):
  `git status`

- ajouter un fichier non suivi `toto.md` au dépot:
  `git add toto.md`.

  Maintenant, toute modification appliquée à `toto.md` sera détectée par
  Git. (modifier `toto.md` et taper `git status` pour s'en convaincre)

- modifier `toto.md` dans Word/Notepad/Neovim/éditeur préféré

- valider les modifications de `toto.md` pour la prochaine archive:
  `git add toto.md`

- archiver la nouvelle version de `toto.md`:
  `git commit`

  L'éditeur par défaut s'ouvre. Indiquer un résumé court (1 ligne) des
  modifications effectuées sur `toto.md` et fermer.

  Si l'éditeur par défaut est toujours Vim (voir plus haut pour changer
		l'éditeur), on reste calme. Appuiyer sur `i` pour passer en mode
  insertion (`-- INSERT --` apparait en bas). Taper un message qui
  récapitule les modifications effectuées sur `toto.md`. Appuiyer sur
  `Esc` (Echap) pour passer en mode Normal. Taper `:wq` pour sauvegarder
  et sortir.

- afficher l'historique des versions:
  `git log` (assez détaillé)
  `git log --oneline` (plus concis)

  Chaque version est identifiée avec un hash du type `7b9a61442eec8ad384099b957f3804802d552a3c`.

- revenir à une version donnée (identifiée par exemple par `7b9a61442eec8ad384099b957f3804802d552a3c`)
  `git checkout 7b9a61442eec8ad384099b957f3804802d552a3c` 

  (les premiers caractères suffisent généralement).
  Git indique que le dépot est en `detached HEAD`, c'est à dire sur une
  version particulière et non sur la dernière version (`master` par
  défaut)

- revenir à la dernière version du dépot (donnée par défaut par la branche `master`):
  `git checkout master`

  Si vous aviez effectué des modifications sur des fichiers d'une
  version archivée, Git ne peut écraser vos changements. Vous pouvez
  soit les archiver (`git add`, puis `git commit`), soit les abandonner
  (`git checkout .`). Par contrer, pour retrouver vos changements, il
  vous faut créer un nouvelle branche.

- pour récupeŕer des changements distants:
  `git pull`
  `git pull origin master`

  Parfois, lorsque des nouvelles modifications ont été effectuées sur le
  dépot distant sur les mêmes fichiers que ceux que vous avex modifiés
  récemment, Git ne sait pas quelles modifications choisir et vous
  demande de régler le conflit. Il faut ouvrir les fichiers en question
  et choisir ce qu'il faut garder. Les passages en conflit sont indiqués
  par

   ```
    >>>>>>>>>>>>>>>>>>>HEAD
    Blablabla
    ===================
    BaratinBaratin
    <<<<<<<<<<<<<<<<<< fefwfwefwef3r3532334 
    ```

    Le passage entre `>>>>>>HEAD` et `=========` correspond à vos
    modifications. Le passage entre `<<<<<<<<<<<fefwfwefwef3r3532334`
    correspond aux modifications sur le dépot distant (identifiées par le
    commit `fefwfwefwef3r3532334`).

    Une fois les passages en conflit corrigés, les valider (`git add`) et
    les archiver (`git commit`). Un message automatique sera normalement
    proposé pour le commit, indiquant qu'il s'agit de la fusion de deux
    branches (celle distante, et la vôtre celle locale).

    Des outils pour résoudre les conflits sont conseillés car plus commodes, comme Meld, Kdiff3.
    Pour les utiliser, il faut configurer Git (voir la section
	[Astuces](#astuces) ) et taper la commande :
    `git mergetool`

- pour partager des nouveaux changements:
  `git push origin master`

## Astuces

### Les alias

Les commandes Git étant fréquemment utilisées, il est conseillé de se
créer des raccourcis/alias. Par exemple:

`git config --global alias.st status` 
`git config --global alias.co checkout` 
`git config --global alias.ci commit` 
`git config --global alias.br branch` 

permet d'utiliser respectivement `git st`, `git co`, `git ci`, `git br`
au lieu de `git status`, `git checkout`, `git commit`, `git branch`.

### Résolution des conflits

Il est conseillé d'utiliser un logiciel de comparaison de fichiers lors
de la résolution de conflits, comme l'excellent `Meld`.

Sous Windows, on peut indiquer à Git de l'utiliser avec les commandes:

```
git config --global merge.tool "meld"
git config --global mergetool.merge.path "C:\Program Files (x86)\Meld\Meld.exe"
```

### Cacher les fichiers que l'on ne souhaite pas suivre

Les fichiers que l'on ne souhaite pas suivre peuvent mis dans un fichier
`.gitignore` placé à la racine du dépot Git. Par exemple, le fichier
`.gitignore` suivant:

```
*.log
*.aux
*.bbl
```

rend les fichiers terminant par `.log`, `.aux`, `.bbl` invisibles à Git.
Utile par exemple pour ne pas être embêté par les fichiers temporaires
lors de la compilation de fichiers Latex. Faire attention aux règles
générales `*.monextension` car il est possible d'oublier de versionner
des fichiers importants. Pour versionner un fichier `toto.log` étant
visé par les règles du `.gitignore`, les ajouter avec la commande:
`git add -f toto.log`.

## Eliminer la demande d'identifiants avec l'échange de clés SSH

Lorsque l'adresse d'un dépot distant est donné avec le protocole HTTP
(quand on clone par exemple), Git demande l'identifiant et le mot de
passe associé au dépot pour s'y connecter, et ce pour chaque `git pull`
ou `git push`. C'est rapidement imcommodant.

Utiliser l'adresse du dépot avec SSH (souvent proposé sur les
plateformes Github, Gitlab, ...) et échanger sa clé SSH publique avec le
serveur distant. (`ssh-copy-id -i ~/.ssh/id_rsa.pub user@server` ou
directement dans les paramètres du compte si c'est une plateforme).

## Mémo des commandes les plus utiles ou courantes

Elles sont des déclinaisons de `git checkout`, `git diff`, `git branch`,
`git log`, `git commit`... Cette section sert juste de référence. Pas
besoin de les apprendre ;)

| Commande Git | Action |
| :------------: | ------- |
| `git status` | affiche l'état du dépot |
| `git add fichier.txt` | suivre le fichier `fichier.txt` |
| `git add fichier.txt` | valide les modifications de `fichier.txt` |
| `git add -p fichier.txt` | comme `git add` mais en mode interactif.  permet de diviser les modifications à valider quand on a fait trop de modifications |
| `git add -u` | valide tous les fichiers ayant été modifiés |
| `git commit` | archive les modifications effectuées dans le dépot |
| `git commit -m 'mon message de commit'`| comme `git commit` mais permet de mettre le message de commit dirrectement | 
| `git checkout .` | annule les modifications effectués dans le dépot et remets les fichiers dans l'état de la dernière archive |
| `git checkout ew34fj3` | mets le dépot Git dans l'état du commit `ew34fj3` |
| `git checkout ew34fj3 toto.txt` | restitue `toto.txt` dans l'état du commit `ew34fj3` en laissant le reste intact (`HEAD` n'est pas modifié) |
| `git pull origin master` | récupère les modifications de la branche `master` du dépot distant `origin` (celle par défaut) |
| `git pull` | idem |
| `git push depot_distant branche_distante` | pousse les modifications sur la branche `branche_distante` du `depot_distant` |
| `git push -u depot_distant branche_distante` | comme `git push depot_distant branche_distante` et considère pour l'avenir que c'est le choix par défaut. Permet d'utiliser `git push` seulement. |
| `git push depot_distant :branche_distante` | supprime `branche_distante` sur le dépot distant `depot_distant` |
| `git branch` | indique la branche courante |
| `git branch -v` | affiche toutes les branches (meme les distantes) |
| `git branch branche_franklin` | crée une branche `branche_franklin` |
| `git checkout branche_franklin` | bascule le dépot Git sur la branche `branche_franklin` |
| `git checkout -b branche_franklin` | crée et bascule sur la branche `brbranche_franklin` |
| `git clean -n` | affiche les fichiers non suivis qui serraient supprimés (utile pour supprimer plein de fichiers temporaires) |
| `git clean -f` | supprime tous les fichiers non suivis (dangereux!!) |
| `git diff` | affiche les modifications des fichiers ayant été modifiés (mais pas encore validés, i.e *unstaged*) |
| `git diff --cached` | comme `git diff` mais en prenant en compte les fichiers validés (*staged*) |
| `git diff --name-only` | affiche uniquement le nom des fichiers ayant été modifiés |
| `git diff efwefw ij3453` | montre différences de fichiers entre les commits `efwefw` et `ij3453` |
| `git log` | affiche l'historique des commits |
| `git log --oneline` | comme `git log` mais n'affiche que la première ligne de chaque commit |
| `git log --oneline --graph` | comme `git log --oneline` mais affiche l'évolution des différentes branches |
| `git log --all` | comme `git log` mais affiche tous les commits, aussi les commits éventuellement plus récents que `HEAD` (utile quand `HEAD` n'est pas sur le commit le plus récent) |
| `git log regfrge..ffwefw` | liste tous les commits entre `regfrge` et `ffwefw` |
| `git ls-files` | liste tous les fichiers suivis par Git |
| `git mv toto.txt titi.txt` | renomme le fichier `toto.txt` en `titi.txt` tout en l'indiquant à Git | 
| `git bisect` | permet de retrouver un commit par recherche dichotomique (puissant!) |
| `git blame fichier.txt` | permet de savoir pour chaque ligne de `fichier.txt` qui a effectué les dernières modifications |
| `git reflog` | historique des opérations sur `HEAD`. Utile pour récupérer des modifications en cas de pépins |
| `git cherry-pick 12ed3r2r` | applique les modifications apportées par le commit `12ed3r2r` à la branche courante |
| `git merge branche_franklin` | fusionne les commits de la branche `branche_franklin` dans la branche courante |
| `git mergetool` | lance le logiciel de comparateur de fichiers pour résoudre les conflicts |
| `git remote add nom_depot_distant url_ou_ssh_depot_distant` | ajoute l'adresse d'un dépot distant `url_ou_ssh_depot_distant` sous le nom `nom_depot_distant`. Pour ensuite faire `git push nom_depot_distant` |
| `git remote set-url depot_distant nouvelle_url` | change l'adresse du `depot_distant` à `nouvelle_url` |
| `git remote show depot_distant` | affiche les infos du `depot_distant` (ses branches, etc...) |
| `git rm toto.txt` | supprime le fichier `toto.txt` tout en l'indiquant à Git |
| `git show egf4456:toto.txt` | affiche la version de `toto.txt` du commit `egf4456` |
| `git stash` | met en mémoire temporairement les modifications effectuées. Utile pour changer de branche/commit en urgence |
| `git stash pop` | réapplique les modifications mises en mémoire temporairement |
| `git stash list` | liste des mises en mémoire temporaires |

## Pour aller plus loin

- `git rebase`

- `.gitattributes`, notamment pour faire des diffs de binaires (pour les affreux qui utilisent Word)

- git merge --theirs, --ours

- `git-crypt` pour pouvoir gérer des documents sensibles dans un dépot Git

- `git sub-tree` (`git submodule`) pour gérer un dépot secondaire dans un dépot principal

