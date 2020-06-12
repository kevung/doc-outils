# Guide d'installation de Mkdocs pour Windows

Teste sur Windows 8.1 Pro

## Mise en place (a faire que la premiere fois)

1. Installer Python: (si non deja present. J'ai teste avec v3.8.2 mais doit fonctionner avec v2....)
    - https://www.python.org/downloads/windows/
    - python-3.8.2-amd64.exe
    - cocher Add Python 3.8 to PATH
    - Install Now

2. Installer Mkdocs:
    - Windows-R > "powershell"
    - `pip install mkdocs`
    - `mkdocs --version`

Dans la suite, on suppose que le depot Git de la documentation API fonctionnelle se trouve au chemin suivant (adapter sinon):
C:\Users\test0\Documents\fonctionnel

- Creer le dossier C:\Users\test0\Documents\fonctionnel-web

- Faire les liens symboliques pour Mkdocs:
Avec un technicien de la DSI : 
  - Menu Demarrer Windows > taper "invite de commande" > Click droit "invite de commande" > "run as administrator" (le technicien met le mot de passe)
  En fonction des techniciens, certains vous laisseront taper la commande et d'autres pas. Préparer donc la commande (après vérification des chemins) dans un document texte afin qu'ils puissent facilement faire un copier-coller
  - Commande 1 (pour un fichier) :
  mklink C:\Users\test0\Documents\fonctionnel-web\mkdocs.yml C:\Users\test0\Documents\fonctionnel\mkdocs\mkdocs.yml
  - Commande 2 (pour un dossier)
 mklink /D C:\Users\test0\Documents\fonctionnel-web\docs C:\Users\test0\Documents\fonctionnel`
  
## Installation de plugins Mkdocs

Des plugins supplémentaires peuvent être utilisés avec Mkdocs. Notamment
le plugin [mkdocs-exclude](https://pypi.org/project/mkdocs-exclude/) permet d'ignorer des fichier dans le dossier `./docs`.

```
pip install mkdocs-exclude
```

## Visualiser/éditer la doc web Mkdocs avec Mkdocs

- Lancer le serveur Web integre a Mkdocs
  - Windows-R > "powershell"
  - `cd C:\Users\test0\Documents\fonctionnel-web`
  - `mkdocs serve` (ou `python -m mkdocs serve`)
  - le serveur web integre a Mkdocs se lance, et reste ouvert tant que la fenetre powershell n'est pas fermee
  - http://localhost:8000

La modification des fichier sources Markdown dans 
C:\Users\test0\Documents\fonctionnel
est repercutee en temps reelle sur la version web.

:)

## Produire la doc web finale

- `mkdocs build`
ou bien
- `mkdocs build --clean`

Il en résulte un dossier `site` standalone qui peut se lire avec un
serveur Web (apache, lighttpd, nginx). Python possède un petit serveur
embarqué bien pratique. Dans le dossier `site`, taper

```
python -m http.server 9000
```

Le site est alors accessible à l'adresse `http://localhost:9000/`.

## Utiliser la doc sans serveur web

Mettre dans le fichier dans `mkdocs.yml`:
```
use_directory_urls: false
```
afin que les liens pointent vraiment vers des fichiers.


[source](https://www.mkdocs.org/user-guide/configuration/#use_directory_urls)
