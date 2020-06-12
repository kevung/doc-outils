Cette partie a du sens si la rédaction des fichiers sources est
réalisée dans un dossier différent de celui où la doc est construite.

Dans la suite, on suppose que le depot Git de la documentation se trouve au chemin suivant (adapter sinon):
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
   
