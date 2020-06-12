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
    [texte du lien](./chemin/vers/mon/fichier.md)
    ```

- vers une section précise du fichier

    ```
    [texte du lien](./chemin/vers/mon/fichier.md#la-section)
    ```
!!! note
    La résolution du lien se fait de manière relative par rapport au
    fichier dans lequel on écrit.

- vers une page web

    ```
    [texte du lien](urldelapage.web)

## Pour insérer une image

```
![légende de l'image](./chemin/vers/mon/image.png)

```

Grâce à l'extension [img2fig](https://pypi.org/project/mkdocs-img2fig-plugin/), le texte entre crochet correspond à la légende de l'image.

## Pour insérer un tableau 

Les tableaux se crées en ajoutant des | entre les éléments. 
Les | des bords sont optionnels.
Pour qu'un tableau soit reconnu, il faut que toutes les lignes aient la même taille et qu'il y ait au moins trois tiret dans chaque case de la 2ème ligne. 


```

|   |   |   |   |   |
|---|---|---|---|---|
|   |   |   |   |   |
|   |   |   |   |   |
|   |   |   |   |   |

```


## <a name="sec_tag"> </a>  Pour créer un tag associé à un élément

La syntaxe des tags est la suivante :

```
<a name="montag"> </a>

```
on s'y réfère ensuite par

```
[texte du lien](#montag)
```
Si le tag n'est pas le même fichier que le référence, il est nécessaire d'introduire le lien du fichier dans lequel se trouve le tag. 

```
[texte du lien](./chemin/vers/mon/fichier#montag)
```

Les tags peuvent se placer n'importe où dans le document. 
Lorsque l'on s'y réfère, on crée un lien hypertexte. 
Lors qu'on clique sur ce lien hypertexte, la page contenant le tag est affiché, avec la position de la page en haut de la page. 
Il est donc nécessaire de mettre le tag au dessus de l'élément auquel on veut faire référence. 
Ainsi pour faire référence à une image, la syntaxe proposée est la suivante : 
```
<a name="img_montag"> </a>
![texte à propos de mon image](./chemin/vers/mon/image.png)
```
Pour une section par contre le tag doit être entre les # et le nom de la section.

```

# <a name="sec_montag"> </a> Nom de ma section
```


