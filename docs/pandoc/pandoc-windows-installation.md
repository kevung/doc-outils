# Installation de Pandoc sous Windows

Ce guide a été testé sous Windows 8.

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


