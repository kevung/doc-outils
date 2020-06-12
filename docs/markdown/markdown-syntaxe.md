# Syntaxe

## Pour créer une liste

Avoir 4 espaces pour passer d'un niveau à un autre :

```
- mon premier niveau
xxxx-mon deuxième niveau
```

## Pour insérer un lien

- vers un fichier
    ```
    ![texte du lien](./chemin/vers/mon/fichier.md)
    ```

- vers une section précise du fichier

    ```
    ![texte du lien](./chemin/vers/mon/fichier.md#la-section)
    ```
!!! note
    La résolution du lien se fait de manière relative par rapport au
    fichier dans lequel on écrit.

## Pour insérer une image

```
![texte à propos de mon image](./chemin/vers/mon/image.png)
```

## Pour créer un tag associé à une section

```
# <a name="montag"> </a>Nom de ma section
```

on s'y réfère ensuite par

```
[texte du lien](#montag)
```
