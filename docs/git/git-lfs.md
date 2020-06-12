# Git LFS

## Installation

Télécharger la version adéquate (linux, windows) dans la section "assets" en bas de la page.

https://github.com/git-lfs/git-lfs/releases/tag/v2.11.0

## Initialisation

Pour activer git-lfs sur votre système, taper dans un terminal (`git
bash` sous Windows)

```
git lfs install
```

Pour activer git-lfs dans un nouveau dépot git vierge, taper dans le
dépot

```
git lfs install
```

## Suivre des fichiers avec Git-lfs

Si les fichiers n'ont jamais été suivi par Git.
Pour suivre par Git Lfs toutes les images `png` par exemple:
```
git lfs track "*.png"
```
Ne pas oublier de commiter ensuite `.gitattributes`.

Si les fichiers int déjà été suivi par Git, ils faut d'abord indiquer
à Git d'arrêter de les suivre. Par exemple, pour toutes les images
`png` du dossier courant:
```
git rm --cached *.png
```

## En savoir plus

- [site officiel](https://git-lfs.github.com/)
- [tutoriel Atlassian](https://www.atlassian.com/git/tutorials/git-lfs): très didactique, clair

