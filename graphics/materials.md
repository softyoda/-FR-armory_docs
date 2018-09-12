# Materials

<img src="./graphics/img/materials.jpg">


Les matériaux sont construits avec des[nodes de cycles](https://docs.blender.org/manual/en/dev/render/cycles/nodes/index.html).

## Displacement

Trouvez la propriété `Armory Render Path - Renderer - Displacement` :
- `Off` - Aucun déplacement effectué.
- `Vertex` - Les sommets sont déplacés.
- `Tessellation` - Le maillage est d'abord "tessellé" pour plus de détails, puis déplacé.

Avec `Tessellation` sélectionné, le niveau de tessellation peut être défini à l'aide des propriétés `Mesh` et `Shadow`.

Note : Les sommets sont déplacés dans le sens des normales. Utilisez un ombrage lisse (`Space - Shade Smooth`) pour les mailles avec déplacement pour éviter les erreures.

Lorsque vous utilisez une heightmap, vous pouvez placer un node `Armory PBR` et connecter la heightmap au node `Height`. Assurez-vous de connecter également le `Displacement`.

<img src="./graphics/img/displace.png">

Examples:
- https://github.com/armory3d/armory_examples/tree/master/material_displace
- https://github.com/armory3d/armory_examples/tree/master/material_tessellation

## Blending


Pour activer le mélange additif pour un matériau spécifique, réglez `Armory Render Path - Blending` sur `On` et cochez la propriété `Blending` dans `Material - Armory Props`.

Exemples :
- https://github.com/armory3d/armory_examples/blob/master/particles/particle_info.blend

## Paramètres des matériaux

Les nodes `RGB`, `Value` et `Image Texture` peuvent être contrôlés au moment de l'exécution à l'aide de nodes script ou logiques. Pour exposer le node matériel, activez la propriété `Parameter` dans `Node Editor - Properties - Armory Material Node`.

Exemples :
- https://github.com/armory3d/armory_examples/tree/master/material_params
