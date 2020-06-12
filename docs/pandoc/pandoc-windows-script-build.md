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
