# Reference

## Activateurs

### On Init

Active les node\(s\) qui y sont connectés sur la première image du jeu.

![](/assets/On-Init.JPG)


### On Timer

Active les node\(s\) auquel est connecté après un compte à rebours à partir du début du jeu, de façon répétée lorsque la case est cochée.

![](/assets/On-Timer.JPG)


### On Mouse

Active les node\(s\) qui y sont connectés lorsque le bouton de la souris est démarré, maintenu enfoncé ou relâché, selon les réglages.

![](/assets/On-Mouse.JPG)


### On Keyboard

Active les node\(s\) qui y sont connectés lorsque le bouton de la souris est démarré, maintenu enfoncé ou relâché, selon les réglages.

![](/assets/On-Keyboard.JPG)


### On Update

Active les node\(s\) qui y sont connectés à chaque image.

![](/assets/On-Update.JPG)


### On Volume Trigger

L'entrée objet inférieure est utilisée comme volume, l'entrée objet supérieure comme entrée objet pour l'objet qui entre, quitte ou chevauche avec lui. 


Enter-mode: Active les nœuds connectés sur le cadre, l'objet entre dans le volume, sur tous les autres cadres, il ne le fait pas.

Leave-mode: Active les nœuds connectés sur le cadre, l'objet quitte le volume, sur tous les autres cadres, il ne le fait pas.

Overlap-mode: Active les nœuds connectés sur le cadre, l'objet chevauche le volume, mais sur tous les autres cadres, il ne le fait pas.

![](/assets/on-volume-trigger.JPG)


## Logique

### Alternate

Alterne entre ses sorties activées pour passer par son entrée lorsqu'elle est réactivée.  

![](/assets/Alternate.JPG)


### Gate

Les nœuds logiques permettent de faire des instructions "if". Lorsqu'elle est activée, elle compare si ses deux entrées sont égales, plus grandes égales, moins égales ou non égales, quel que soit le type de variable, et passe par son entrée rouge si l'état de l'ensemble est le cas.

"And" et "Or" ne sont utilisés que pour les bools, et passent par l'entrée lorsque les deux bools sont vrais (And) ou au moins un (Or).

![](/assets/Gate.JPG)


### Not

Inverse le booléen branché, donc si son entrée est "true" il sort "false".

![](/assets/Not.JPG)


### Sleep

Active le node connecté avec sa sortie après la valeur flottante en secondes après qu'il a été activé lui-même.

![](/assets/sleep.JPG)


### Branch

Lorsqu'il est activé, il active sa sortie "True" ou "False", en fonction de l'état du booléen branché.

![](/assets/Branch.JPG)


### Is True/False

Passe par son activation uniquement si le booléen branché est "True"/"False", selon le node.!

[](/assets/Is-true_false.JPG)


### Merge

Le bouton "Nouveau" crée de nouvelles entrées, le bouton "X" efface la plus basse. S'il reçoit à l'activation de l'une de ses entrées, il activera sa sortie.

![](/assets/Merge.JPG)


## États

### Mouse

Sortie d'un bool si le bouton de réglage est en cours de démarrage, maintenu enfoncé, relâché, déplacé \(true\) ou non \(false\).

![](/assets/Mouse.JPG)


### Mouse Cords

Affiche l'emplacement X,Y de la souris à l'écran et son mouvement en tant que vecteur, et un entier si la molette de défilement a été déplacée vers le haut \(1\) ou vers le bas \(-1\) a la frame actuelle.

![](/assets/Mouse-Cords.JPG)


### Keyboard

Sortie d'un bool si le bouton de réglage est actuellement démarré, maintenu enfoncé, relâché, \(true\) ou non \(false\).

![](/assets/Keyboard.JPG)


### Get Transform


Affiche la transformation courante de l'objet défini. Une Transformation d'objets se compose de Vecteurs pour sa position globale, sa rotation et son échelle.

![](/assets/get-transform.JPG)


### Get Location

Sortie de l'emplacement global actuel de l'objet défini en tant que vecteur.

![](/assets/get-location.JPG)


### Get Rotation

Affiche la rotation actuelle de l'objet défini en tant que vecteur.

![](/assets/get-rotation.JPG)


### Get Scale

Sortie de l'échelle actuelle de l'objet défini en tant que vecteur.

![](/assets/get-scale.JPG)


### Get Object

Recherche un objet avec le nom de l'ensemble dans la scène et l'édite.

![](/assets/get-object.JPG)


### Get Visible

Sortie d'une valeur booléenne en fonction du réglage de visibilité actuelle des objets dans l'Outliner. Faux si invisible, Vrai si visible, même si l'Objet n'est pas sur la caméra en ce moment.

![](/assets/get-visible.JPG)


### Get Child

Recherche l'objet avec le nom de l'ensemble qui est actuellement un enfant de l'objet et l'affiche.

![](/assets/get-child.JPG)


### Get Children

Sortie de tous les enfants actuels de l'objet défini en tant qu'array d'objets.

![](/assets/get-children.JPG)


### Get Parent

Sortie du parent courant le plus proche de l'objet défini.

![](/assets/get-parent.JPG)


### Get Group

Recherche un groupe d'objets avec le nom de l'ensemble et l'édite sous forme d'array d'objets.

![](/assets/get-group.JPG)


### Group

Affiche tous les objets du groupe défini sous forme de tableau.

![](/assets/group.JPG) 


### Get Distance

Affiche la distance actuelle entre les deux objets (float).

![](/assets/get-distance.JPG)


### Get Trait

Recherche un caractère avec le nom de l'ensemble qui est appliqué sur l'objet défini et l'édite.

![](/assets/get-trait.JPG)


### Active Camera

Sortie de la caméra active dans votre jeu en tant qu'objet.

![](/assets/active-camera.JPG)


### Active Scene

Sortie de la scène actuellement active dans votre jeu.

![](/assets/active-scene.JPG)


### Volume Trigger

L'entrée objet inférieure est utilisée comme Volume, l'entrée objet supérieure comme entrée objet pour l'objet qui entre, quitte ou chevauche avec lui

Enter-mode: Sortie vrai sur la frame l'objet entre dans le volume, sur toutes les autres frames il sort faux.

Leave-mode: Sortie vrai sur la frame l'objet quitte le volume, sur toutes les autres frames il sort faux.

Overlap-mode: Sortie vrai sur la frame l'objet chevauche le volume, sur toutes les autres frames il sort faux.


![](/assets/Volume-trigger.JPG)


## Valeurs et variables

### Global Object

Donne accès à un objet global, qui peut être utilisé pour partager des informations entre différents Traits.

![](/assets/global-object.JPG)


### Get Property

Peut être utilisé pour recevoir les propriétés d'autres objets, qui ont été définis avec le noeud "[Set Property](/logic-nodes/set-property.md)". Le nom des propriétés et l'objet doivent correspondre aux entrées de ce node.

![](/assets/Get-property.JPG)


### Integer

Enregistre une valeur entière. Ce sont des nombres entiers.

![](/assets/Integer.JPG)


### Float

Enregistre une valeur flottante. Une variable flottante est un nombre avec un nombre limité de décimales. Si votre nombre a plus de 3 décimales, la valeur affichée sera arrondie, mais lorsque vous cliquez dessus, vous pouvez toujours voir le nombre entier, qui sera également utilisé dans le jeu.

![](/assets/float.JPG)


### Boolean

Enregistre une valeur booléenne. Une valeur booléenne n'a que deux états : Vrai et Faux.

![](/assets/boolean.JPG)


## Actions

### Set Variable

Lorsqu'il est activé, il met à jour la première variable branchée à la valeur de la seconde. Convertit automatiquement certains types de variables.

![](/assets/set-variable.JPG)


### Translate Object

Déplace l'objet défini à chaque fois qu'il est activé par le vecteur donné.

![](/assets/translate-object.JPG)

### Set Property

Lorsqu'il est activé, définit ou met à jour une Propriété de l'objet donné nommé d'après son entrée de chaîne de caractères à la Valeur de son entrée de Variable générale \(la verte\). Vous n'avez pas à vous soucier du type variable, vous pouvez tout brancher à part les activations. 

Ce nœud peut être utilisé pour partager des Variables entre différents Traits. Si le trait\(s\) avec lequel vous voulez accéder à la variable se trouve sur différents objets, utilisez le noeud "[Global Object](/logic-nodes/global-object.md)" pour stocker les données. Chaque trait de caractère peut accéder à celui-ci.

![](/assets/set-property.JPG)
