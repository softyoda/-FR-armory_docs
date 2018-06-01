# Tanks Game

<iframe width="560" height="315" src="https://www.youtube.com/embed/5b97eR5_fQI?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Construisons un mini-jeu ! Il sera composé de 2 joueurs manipulant un tank et se battant l'un contre l'autre. Nous construisons un petit terrain de jeu avec des obstacles et deux modèles de tanks. Chaque objet a un corps rigide. Certains obstacles sont animés sur la timeline pour rendre le jeu plus dynamique. La configuration de l'éclairage est basée sur tutoriel [Playground](./getting_started/playground.md).

![](./getting_started/img/tanks/1.jpg)

Le tank rouge agit en tant que joueur 1. Nous autorisons les contrôles du clavier et de la manette de jeu, mais nous codons en dur les touches réelles utilisées par souci de simplicité. Dans une arborescence **Player1Controls**, la touche gauche du clavier ou de la manette de jeu est réglée pour envoyer un événement nommé **'turn_left'**. Plus tard, nous utilisons cet événement pour faire tourner le tank contrôlé par le joueur.

![](./getting_started/img/tanks/2.jpg)

Faites ceci pour toutes les touches - gauche, droite, avant, avant et arrière.

![](./getting_started/img/tanks/3.jpg)

Le tank bleu agit en tant que joueur 2. Nous définissons les mêmes contrôles, mais nous mappons les clés sur WSAD et la deuxième manette de jeu connectée à la place.

Dans un **TankTree**, nous écoutons les événements et effectuons des actions pour contrôler réellement le tank. La raison pour laquelle cet arbre de nodes est séparé est que nous l'attachons aux deux tank, ce qui empêche les arbres de nodes dupliqués.

Le node On Event** est configuré pour écouter l'événement **'turn_left'**. Pour le joueur 1, cet événement est déclenché lorsqu'on appuie sur la touche gauche. Pour le joueur 2, cela se fait en appuyant sur la touche A. Le node **On Event** est connecté au node **Rotate Object**, la valeur **Vector Z** étant réglée sur une petite valeur positive contrôlant la vitesse de rotation. En jouant le jeu maintenant, appuyer sur la touche gauche fait tourner le tank ! 

![](./getting_started/img/tanks/4.jpg)

Nous faisons la même chose pour l'événement **'turn_right'**, mais la valeur **Vector Z** est réglée sur une valeur négative pour tourner dans le sens inverse.

En ce qui concerne l'événement handling **'forward'**. Pour déterminer la direction dans laquelle le tank doit se déplacer, **Vector from Transform** node est utilisé avec le type réglé sur **Look**. Ce vecteur est ensuite réduit à l'aide du node **Vector Math** pour ralentir la vitesse du tank. Le vecteur résultant est transmis dans le node **Translate Object**.

![](./getting_started/img/tanks/5.jpg)

Comme précédemment, nous faisons la même chose pour l'événement **'backward'** avec le vecteur translate inversé.

Maintenant que les tanks sont entièrement contrôlables, nous leur faisons tirer des balles. Pour garder la scène dégagée, l'objet bullet est placé dans la deuxième layer de la scène avec **Render disabled**.. Ceci garantit que l'objet sera exporté mais non visible en tant que tel.

![](./getting_started/img/tanks/6.jpg)

En sélectionnant le tank rouge, un objet vide est ajouté en tant qu'enfant - l'emplacement de cet objet définit où tirer les balles. Un nouvel arbre logique est ajouté à cet objet vide. La touche M (ou gamepad) émet un événement **'fire'**. Nous faisons la même chose pour le tank bleu.

![](./getting_started/img/tanks/7.jpg)

Nous attachons un autre arbre logique - gérer la réponse à l'événement **'fire'**. Nous créons un nouvel objet - notre modèle de balle du layer 2, et plaçons son emplacement au propriétaire de l'arbre logique - dans ce cas le point de spawn de la balle - défini comme un objet vide placé comme un enfant de tank.

![](./getting_started/img/tanks/8.jpg)

En jouant la scène maintenant, nous découvrons que les balles tombent du canon jusqu'au sol. Il nous faut de la poudre à canon !

![](./getting_started/img/tanks/a.jpg)

Appliquer le **node Impulse** corrige ce problème. Comme pour faire avancer le tank, nous acquérons le vecteur avant et nous le mettons à l'échelle.

![](./getting_started/img/tanks/9.jpg)

Même si Armory élimine les objets de l'écran, il est important de réduire au minimum l'utilisation des ressources. Nous enlevons chaque balle après 2 secondes de vie. Pour ce faire, le node **Array(Object)** est placé et toutes les balles tirées sont stockées dans ce tableau en utilisant le node **Array Add**. Nous attendons 2 secondes avec le node **Sleep** et appelons le node **Remove Object**. Le node  **Array Shift** de tableau alimente le premier élément du tableau de la balle dans le node **Remove Object**, et supprime également cet élément du tableau lui-même.

![](./getting_started/img/tanks/10.jpg)

C'est tout - n'hésitez pas à expérimenter davantage ! Téléchargez le .blend complet pour ce tutoriel :

- https://github.com/armory3d/armory_tutorials/tree/master/tanks
