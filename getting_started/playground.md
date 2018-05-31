# Tutoriel "Playground"

<iframe width="560" height="315" src="https://www.youtube.com/embed/H5ylSfTfNg8?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Ce tutoriel vous guide à travers les bases d'Armory. Nous créerons une scène ressemblant à un terrain de jeu et présentant les caractéristiques essentielles étape par étape. Allons-y !

- Téléchargez le fichier [.blend](https://github.com/armory3d/armory_tutorials/releases) pour ce tutoriel.

### Hello World

Reprendre là où nous avons laissé le tutoriel [Installation](./getting_started/setup.md). Ouvrez Blender, enregistrez le projet et sélectionnez le moteur `Cycles Render` ou `Eevee` dans l'en-tête. Appuyez sur `Armory Player - Run (F5)` pour jouer dans la fenêtre.

Vous pouvez sélectionner une runtime dans le panneau " Armory Player " :
- Sélectionnez `Krom` pour jouer rapidement la scène.
- Sélectionnez " Navigateur " pour le déploiement HTML5.
- Sélectionnez `C++` pour le déploiement natif (compilateur C++ requis). 


Vous pouvez également sélectionner le mode caméra dans le panneau " Armory Player " :
- Sélectionnez `Scene' pour démarrer le jeu à partir du point de la caméra de scène active.
- Sélectionnez `Viewport' pour démarrer le jeu à partir de la vue viewport. Ceci est utile pour une prévisualisation rapide de la scène car il vous permet également de contrôler l'appareil photo. Essayez-le !
- Appuyez sur `Shift + F` dans la vue 3D pour naviguer autour de la scène.

De plus, vous pouvez modifier les `Dimensions - Résolution` pour la taille de la fenêtre. Pour exécuter en plein écran, sélectionnez  `Armory Project - Window Mode - Fullscreen`.

<a href="./getting_started/img/playground/1.jpg">![](./getting_started/img/playground/1.jpg)</a>

### Objets

Nous allons commencer par quelques notions de base de Blender sur la manipulation des objets de la scène :

- Dans la vue 3D, cliquez sur " Espace " et tapez " Ajouter un plan " pour créer un objet plan (ou faites " Ajouter - Mesh - Plan " à partir de l'en-tête de la vue 3D).
- Appuyez sur `S' pour mettre à l'échelle le plan, `R` pour tourner, ou `G` pour saisir et déplacer.
- Sélectionner les objets avec le clic droit.
- Effacer des objets en appuyant sur " X ".


### Modifiers

Blender a une variété de modificateurs qui appliquent des effets procéduraux sur l'objet actif. Sélectionnez Cube, naviguez jusqu'à l'onglet `Modifiers` et ajoutez le modificateur `Bevel` pour que les bords du cube aient l'air polis.

<a href="./getting_started/img/playground/1b.jpg">![](./getting_started/img/playground/1b.jpg)</a>

### Materials

Sélectionnez Cube et passez à l'éditeur de nodes. Allez dans `Shader Nodes' et activez `Use Nodes'. Vous pouvez maintenant ajuster la couleur et la rugosité(roughness) du matériau en utilisant le nodes par défaut `Diffuser BSDF`.

<a href="./getting_started/img/playground/2.jpg">![](./getting_started/img/playground/2.jpg)</a>

Ensuite, revenez à `3D View` et sélectionnez Plane. Nous voulons lui donner une texture. Appuyez sur `Tab` pour entrer en mode édition, appuyez sur `Space` et tapez `Unwrap` pour créer des coordonnées UV pour le plan.

Dans l'onglet Material, créez un nouveau material. Passez à Node Editor comme nous l'avons fait auparavant. Sélectionnez le nodes `Diffuse BSDF` et appuyez sur `X` pour le supprimer. Dans l'en-tête, appuyez sur `Add - Group - Armory PBR` et placez-le. Connecter la prise `Surface` au nodes `Material Output`. Pour de meilleurs résultats, préférez utiliser le nodes `Armory PBR` lorsque vous travaillez avec des matériaux dans Armory.

![](./getting_started/img/playground/grid_base.png)
![](./getting_started/img/playground/grid_rough.png)

Sauvegardez les images ci-dessus et glissez-déposez simplement les fichiers dans le node editor sur Blender. Connectez les nodes `Image Texture` aux sockets `Base Color` et `Roughness`.

<a href="./getting_started/img/playground/3.jpg">![](./getting_started/img/playground/3.jpg)</a>

A la suite de ces étapes, une scène de base se dessine déjà. Appuyez sur `F5` pour jouer la scène dans Armory !

<a href="./getting_started/img/playground/5.jpg">![](./getting_started/img/playground/5.jpg)</a>

### Animation

Créons une animation qui fait tourner le cube. Localisez la `Timeline` et allez à la frame 1. Sélectionnez Cube et appuyez sur `I - Rotation` pour insérer les images-clés pour la rotation. Ensuite, allez à la frame 60 dans la timeline. Lorsque le Cube est sélectionné, appuyez sur `R` pour le faire pivoter a la position désirée et appuyez à nouveau sur `I - Rotation`.


<a href="./getting_started/img/playground/6.jpg">![](./getting_started/img/playground/6.jpg)</a>

### Lumières

Sélectionnez l'objet lampe dans la hiérarchie et passez à l'onglet `Data`. Vous pouvez définir le type de lampe et ajuster la couleur et la puissance de la lampe.

<a href="./getting_started/img/playground/9.jpg">![](./getting_started/img/playground/9.jpg)</a>

### Environnement

Les "World nodes" sont utilisés pour configurer l'environnement. Passez à `Node Editor - World Nodes` pour accéder aux nodes (icone rond bleu). Dans ce tutoriel, nous utilisons le noeud `Sky Texture` pour rendre le ciel procédural. Si nous devions ajouter une texture d'environment, nous utiliserions le noeud `Environment Texture` avec le fichier `.hdr`.

<a href="./getting_started/img/playground/10.jpg">![](./getting_started/img/playground/10.jpg)</a>

### Physique

Avec l'objet sélectionné, naviguez jusqu'à l'onglet `Physics` et appuyez sur le bouton `Rigid Body`. Définir la forme désirée représentant l'objet dans le panneau `Rigid Body Collision`.

Dans le panneau `Rigid Body`, définissez la masse et le type de l'objet :
- Sélectionnez `Active` pour les objets qui sont librement affectés par la physique.
- Sélectionnez `Passive` pour les objets qui sont animés sur la timeline.

<a href="./getting_started/img/playground/11.jpg">![](./getting_started/img/playground/11.jpg)</a>

### Importation d'asset

Avec Blender, il est possible d'importer facilement des formats de fichiers communs.
- Sélectionnez `File - Import` pour importer des formats de fichiers.
- Sélectionnez `File - Append` pour importer des objets à partir d'autres fichiers.blend.
- Sélectionnez `File - Link` pour lier les objets d'autres fichiers .blend.

In this tutorial, we are using an animated `.fbx` model from [mixamo](http://mixamo.com), imported using the `File - Import` option.

<a href="./getting_started/img/playground/8.jpg">![](./getting_started/img/playground/8.jpg)</a>

### Logic Nodes

Les nodes logiques fournissent un moyen visuel de créer des scènes interactives. Lorsque vous construisez votre projet, les nodes créés sont automatiquement compilés en scripts.

Le système se compose de 5 catégories essentielles :
- `Events` - node où l'exécution commence, déclenchée par l'événement désiré.
- `Actions` - s'active une fois qu'un événement est déclenché.
- `Logic` - noeuds utilisés pour contrôler le flux d'exécution, en utilisant des branchement, des boucles, et des portes logiques...
- `Variables` - nodes utilisés pour stocker des données dans une arborescence logique.
- `Values` - nodes utilisés pour récupérer des données à partir d'autres objets.


Nous allons animer le cylindre de manière procédurale en utilisant des noeuds logiques. Passez à la zone `Node Editor` et sélectionnez `Logic` nodes. Appuyez sur `New` pour créer une nouvelle arborescence de nodes.

Vous pouvez parcourir tous les nodess disponibles via l'élément de menu `Add`, ou simplement appuyer sur " Maj + A " pour lancer la recherche.

- Rechercher le nodes `On Update` et le placer. Il s'agit d'un nodes d'action qui est appelé chaque trame.
- Connectez-le au nodes `Set Location`.
- Ajouter un nodes `Vector` et le connecter au nodes `Set Location`. Chaque image, l'emplacement du cylindre sera réglé sur ce vecteur.
- Pour l'emplacement `X`, ajoutez le nodes `Math` et réglez-le sur `Sine`.
- Ajouter le nodes `Time` pour piloter le nodes sinusoïdal.
- Ajouter un autre nodes `Math`, en mettant à l'échelle la sortie sinusoïdale.
- Nous garderons les emplacements `Y` et `Z` inchangés.

Chaque nodes doit être attaché à un objet. Sélectionnez Cylindre et créez un nouveau trait dans `Properties - Object - Armory Traits`. Définissez le type sur `Nodes` et entrez notrs nodes nouvellement créé en tant qua `Tree`.

<a href="./getting_started/img/playground/12.jpg">![](./getting_started/img/playground/12.jpg)</a>

### Haxe Scripts

Nous pouvons programmer les caractéristiques de l'objet directement en utilisant le langage de programmation `Haxe`. Créons un trait qui donne naissance à une case après avoir appuyé sur une touche.

Créez un objet vide dans la scène (`Shift+A - Add - Empty Plain Axes`). L'emplacement de cet objet servira de point de spawn. Créez un nouveau trait dans `Properties - Object - Armory Traits'. Définissez le type sur `Haxe' et appuyez sur le bouton `New Script`.

Appuyez sur `Edit Script` pour ouvrir le fichier script dans Kode Studio. Kode Studio est un éditeur de code dédié qui inclut la complétion de code et le support du débogage.


```haxe
package arm;

import iron.object.Object;
import iron.system.Input;
import iron.Scene;
import armory.trait.physics.RigidBody;

class SpawnBox extends iron.Trait {
	public function new() {
		super();
		// We want to get notified every frame
		notifyOnUpdate(update);
	}

	function update() {
		// f key was pressed
		if (Input.getKeyboard().started("f")) {
			// Spawn Box object
			Scene.active.spawnObject("Box", null, boxSpawned);
		}
	}

	// Box just got spawned
	function boxSpawned(o:Object) {
		// Translate cube to the location of empty object
		var traitOwner = object;
		o.transform.loc.setFrom(traitOwner.transform.loc);
		// Box object has a rigid body trait
		// Notify physics system to take new location into effect!
		o.getTrait(RigidBody).syncTransform();
	}
}
```

<a href="./getting_started/img/playground/13.jpg">![](./getting_started/img/playground/13.jpg)</a>

### Scripts groupés

Armory est livré avec un ensemble de scripts pré-créés. Semblable au script régulier, les scripts groupés peuvent être attachés à un objet en tant que trait de caractère. Dans ce tutoriel, nous utiliserons le trait `PhysicsDrag`. Lorsque ce trait est attaché à un objet physique, il nous permet de faire glisser cet objet à l'aide de la souris.

<a href="./getting_started/img/playground/14.jpg">![](./getting_started/img/playground/14.jpg)</a>

### UI Canvas

UI signifie interface utilisateur.

Pour construire l'interface de jeu, un outil ArmorUI dédié est utilisé.

Outre les objets, la scène elle-même peut aussi contenir des caractéristiques. Cela correspond bien aux caractéristiques de l'UI. Allez à l'onglet `Scene' et ajoutez une nouvelle caractéristique dans le panneau `Armory Traits`. Définissez le type de caractéristique sur `UI' et appuyez sur le bouton `New Canvas`. Ensuite, appuyez sur le bouton `Edit Canvas` pour lancer ArmorUI.

Dans `ArmorUI`, appuyez sur le bouton `Text` pour générer un objet texte. Ajustez le texte dans le panneau `Properties`  et cliquez sur `Save`. Si vous lancez le jeu maintenant, l'interface s'affichera.

<a href="./getting_started/img/playground/15.jpg">![](./getting_started/img/playground/15.jpg)</a>

### Chemin de rendu

Armory est alimenté par un système de rendu programmable. Naviguez jusqu'au panneau `Render - Armory Render Path` pour accéder aux paramètres. Plusieurs préréglages sont disponibles pour une configuration simple.

Plusieurs chemins de rendu peuvent être créés. Lors de l'exportation du projet, vous pouvez utiliser le chemin de rendu qui convient le mieux au matériel.

Si vous utilisez un GPU moderne (OpenGL 4.5+), sélectionnez `Max (Game)` pour activer des effets plus avancés comme l'occlusion ambiante à base de voxel. Notez que le Voxel AO doit fonctionner dans une fenêtre autonome - il suffit d'appuyer sur `F5` pour lancer.

<a href="">![](./getting_started/img/playground/16.png)</a>

### Exporter

Lorsque vous êtes prêt à publier votre projet, allez dans `Properties - Render - Armory Exporter`

Vous pouvez créer plusieurs presets d'exportation, chacun spécifiant une plate-forme cible, une API graphique, un chemin de rendu et une scène de démarrage. Sélectionnez la plate-forme souhaitée et cliquez sur le bouton `Publish`. Une fois terminé, cliquez sur `Triangle - Open Folder` pour visualiser les fichiers exportés.


<a href="">![](./getting_started/img/playground/17.png)</a>

- Continuez vers le [Tutoriel avec les chars](./getting_started/tanks.md)
