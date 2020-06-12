# TUTO PANDOC (teste sur Windaube 8)

Pandoc est un outil de conversion de document texte.  Il permet en
l'occurence de convertir les fichiers Markdown en documents docx,
html...  Ce tuto explique comment lancer le script `./pandoc/build.sh`
qui génère automatiquement le document docx final.

## Installation

- Installer Pandoc
  - https://pandoc.org/installing.html
- ajouter pandoc au PATH
  - ouvrir l'explorateur de fichiers a PC > Onglet `propriétes systèmes`
    > `Paramètres systèmes avancés` > `Variables d'environnement`
  - dans la partie `Variables systèmes` > sélectionner `Path` > `Editer`
  - ajouter dans `valeur` à la fin `;C:\Program Files\Pandoc\` (il y a
    un `;` pour séparer les différents chemins)
Ces deux étapes doivent être 

- Installer `Git for windows` (fournit Bash et des outils utiles. Déjà
  utilisé pour Git.)
  - https://gitforwindows.org/

- Installer Zip (outil pour zipper en ligne de commande, du projet GnuWin)
  - https://sourceforge.net/projects/gnuwin32/files/zip/3.0/zip-3.0-setup.exe/download
  - installer zip-3.0-setup.exe
- ajouter Zip au PATH
  - ouvrir l'explorateur de fichiers a PC > Onglet `propriétes systèmes`
    > `Paramètres systèmes avancés` > `Variables d'environnement`
  - dans la partie `Variables systèmes` > sélectionner `Path` > `Editer`
  - ajouter dans `valeur` à la fin `;C:\Program Files (x86)\GnuWin32\bin\` (il y a
    un `;` pour séparer les différents chemins)

## Utilisation simple

- ouvrir le dossier `./pandoc`
- double-cliquer sur `build.sh` (`build` si Windows ne montre pas
  l'extension)

Si Windows ne sait pas quel programme utiliser:

- click-droit > Ouvrir avec > Git for Windows

sinon utiliser Git bash (voir section suivante)

## Utilisation plus complète

Le lancement du script `build.sh` dans un terminal permet d'afficher les
Warnings lors de la conversion par Pandoc.  Ces derniers sont utiles
pour comprendre ce qui se passe lorsque la conversion se passe mal.  Par
ailleurs, il est possible d'utiliser `build.sh` avec en paramètre un
format pour générer un document non nécessairement au format docx.

- ouvrir le dossier `./pandoc`
- click-droit > `Git Bash ici`
- `./build.sh`

Si on veut générer une page html :
- `./build.sh html`

Si on veut générer un pdf (Latex) :
- `./build.sh pdf`
