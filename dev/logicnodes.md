# Logic Nodes

## Création de nodes personnalisés

### Créer une librairie

Nous allons créer une nouvelle librairie pour stocker les sources des nodes logiques personnalisés et les garder portables sans modification des sources du moteur.

Localisez votre fichier .blend et créez un nouveau dossier `Libraries` à côté. Naviguez jusqu'au dossier  `Libraries`  et créez-y un nouveau dossier `mynodes`.


### Python

Commencez par créer la définition de node logique pour Blender. Créez un fichier nommé `blender.py' dans le dossier `Libraries/mynodes'. Armory récupère automatiquement ce fichier une fois que la bibliothèque est chargée. Définir un node simple avec une seule prise d'entrée/sortie.

```py
from bpy.types import Node
from arm.logicnode.arm_nodes import *
import arm.nodes_logic

class TestNode(Node, ArmLogicTreeNode):
    '''Test node'''
    bl_idname = 'LNTestNode'
    bl_label = 'Test'
    bl_icon = 'GAME'

    def init(self, context):
        self.inputs.new('ArmNodeSocketAction', 'In')
        self.outputs.new('ArmNodeSocketAction', 'Out')

def register():
    # Add custom nodes
    add_node(TestNode, category='Action')
    # Register newly added nodes
    arm.nodes_logic.register_nodes()
```

Redémarrer Blender et charger à nouveau le projet, le nouveau node logique est disponible.

![](/dev/img/logicnodes/1.png)

### Haxe

Avant que le projet puisse être exécuté, nous avons besoin d'implémenter la logique de node réelle dans Haxe. Lorsque le node est exécuté, nous lui permettons d'afficher un 'Hello, World!' !

```hx
package armory.logicnode;

class TestNode extends LogicNode {

	public function new(tree:LogicTree) {
		super(tree);
	}

	override function run() {
		// Logic for this node
		trace("Hello, World!");

		// Execute next action linked to this node
		super.run();
	}
}
```


### Aller plus loin

- Exemple de projet:
https://github.com/armory3d/armory_examples/tree/master/dev_logicnode

Lors de l'implémentation de nouveaux nodes logiques, il est facile de parcourir les sources des nodes existants comme référence.

- Définitions Python des nodes d'Armory : https://github.com/armory3d/armory/tree/master/blender/arm/logicnode

- Equivalents Haxe : https://github.com/armory3d/armory/tree/master/Sources/armory/logicnode
