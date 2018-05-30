# Traits

Armory utilise un système de trait (caractéristiques) pour insérer la logique dans les objets Blender et les rendre interactifs. Les traits peuvent être attachés à des objets de scène ou à des scènes elles-mêmes. Pour inspecter les traits placés dans la scène, passez à la vue `Groups`" dans l'`Outliner`.

![](/essentiels/img/traits_groups.png)

Il existe plusieurs types de traits de caractère :
- `Haxe Script` - écriture du script à partir de zéro dans Haxe.
- `Bundled Script`  - manipulant des choses communes comme les contrôleurs de caractères, fournis avec Armory.
- `Logic Nodes`  - assembler la logique visuellement.
- `Canvas`" - travailler avec l'interface utilisateur.

Pour les scripts, il est possible de passer des paramètres ou de définir les propriétés du script directement depuis Blender.

![](/essentiels/img/traits_panel.png)

## Trait events

Trait exposes events - ce qui permet d'être informé de son cycle de vie.

`Trait.notifyOnAdd()` - le trait est ajouté à un objet.
`Trait.notifyOnInit()` - l'objet auquel ce trait appartient est ajouté à la scène.
`Trait.notifyOnRemove()` - l'objet auquel appartient ce trait est retiré de la scène.
`Trait.notifyOnUpdate()` - mettre à jour la logique ici.
`Trait.notifyOnRender()` - mise à jour du rendu ici

Comme la scène est construite de manière asynchrone, l'événement `onInit` peut être appelé à un moment où tous les objets de la scène ne sont pas encore présents. Si la construction des traits dépend d'autres objets de scène, utilisez `Scene.active.notifyOnInit()` événement qui est appelé dès que la scène est entièrement construite.