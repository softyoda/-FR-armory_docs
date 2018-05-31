# Render Path

*Cette page est en cours d'élaboration - la plupart des travaux manuels décrits ici doivent être automatisés.*

Armory est alimenté par un système de chemin de rendu scriptable. Cela nous permet de gérer à la fois les rendus avancés et différés et de les étendre facilement avec des passes supplémentaires tout en introduisant le moins de frais possible et en réutilisant les ressources existantes. Le moteur est également préparé pour l'ajout de nouveaux types de rendus.

Le chemin de rendu est construit lorsque le jeu lui-même est compilé. Lorsqu'un laissez-passer spécifique est désactivé, il n'y a plus rien à faire pour économiser les ressources.


## Extension du compositor

Si possible, effectuez un post-traitement supplémentaire directement dans le compositeur. De cette façon, tout est conservé en un seul passage. Voir[LUT-based-color-grading](https://github.com/armory3d/armory/commit/42b0aaadeda67b2eabde0344ebbb100f18bd8e0d). Il est possible d'accéder à aux pre-tonemaped color, depth, normals,....

## Ajout d'une passe de post-traitement

Pour les effets qui ne rentrent pas dans une seul passe.

- Dans [make_renderpath.py](https://github.com/armory3d/armory/blob/master/blender/arm/make_renderpath.py) - inclure des fichiers de shader supplémentaires (`assets.add_shader_pass()`) et ajouter des définitions (`assets.add_khafile_def()`)

- Dans [RenderPathCreator.hx](https://github.com/armory3d/armory/blob/master/Sources/armory/renderpath/RenderPathCreator.hx) - chargez les shaders (`path.loadShader()`), créer des cibles de rendu (`path.createRenderTarget()`) et [ajouter des nouvelles commandes](https://github.com/armory3d/armory/blob/master/Sources/armory/renderpath/RenderPathCreator.hx#L891)

```hx
#if rp_custom_pass
{
	// Draw into helper 'buf' render target
	path.setTarget("buf"); 
	// Bind current screen color
	path.bindTarget("tex");
	
	// Draw full-screen quad(actually triangle) using custom shader
	// file_name/shader_name/context_name
	path.drawShader("shader_datas/custom_pass/custom_pass");
	
	// NOTE: this step is temporary till the interface for adding custom passes improves
	// Copy results of custom_pass back to the "tex" render target,
	// which will then get picked up be compositor pass
	path.setTarget("tex");
	path.bindTarget("buf", "tex");
	path.drawShader("shader_datas/copy_pass/copy_pass");
}
#end
```

## Custom geometry pass

Voir l'exemple du [material_shaders](https://github.com/armory3d/armory_examples/tree/master/material_shaders).

- Créer un nouveau [material definition](https://github.com/armory3d/armory_examples/blob/master/material_shaders/Bundled/MyMaterial/MyMaterial.arm) in `blend_root/Bundled/your_material`
- Dans Blender, sélectionnez le matériau et réglez `Properties - Material - Armory Props - Custom Material` a `your_material`
- Créez `your_material.vert.glsl` et `your_material.frag.glsl` shaders (.geom, .tesc, .tese are optional) dans `blend_root/Shaders`

### Au-delà

Minimal vertex shader:

```glsl
#version 450
in vec3 pos;
in vec3 nor;
uniform mat4 WVP;
void main() {
	gl_Position = WVP * vec4(pos, 1.0);
}
```

Minimal fragment shader:

```glsl
#version 450
out vec4 fragColor;
void main() {
	fragColor = vec4(1.0);
}
```

### Différé

Pour le rendu différé, nous avons besoin d'encoder la sortie du fragment shader dans la mise en mémoire tampon.

Minimal vertex shader:

```glsl
#version 450
in vec3 pos;
in vec3 nor;
out vec3 wnormal;
uniform mat3 N;
uniform mat4 WVP;
void main() {
	wnormal = normalize(N * nor);
	gl_Position = WVP * vec4(pos, 1.0);
}
```

Minimal fragment shader:

```glsl
#version 450
#include "std/gbuffer.glsl"
in vec3 wnormal;
out vec4[2] fragColor;
void main() {
	// Pack normal into 2 components
	vec3 n = normalize(wnormal);
	n /= (abs(n.x) + abs(n.y) + abs(n.z));
	n.xy = n.z >= 0.0 ? n.xy : octahedronWrap(n.xy);
	// Define material values
	vec3 basecol = vec3(1.0);
	float roughness = 0.0;
	float metallic = 0.0;
	float occlusion = 1.0;
	// Store in gbuffer
	fragColor[0] = vec4(n.xy, packFloat(metallic, roughness), 1.0 - gl_FragCoord.z);
	fragColor[1] = vec4(basecol.rgb, occlusion);
}
```

## Ecriture d'un chemin de rendu personnalisé

Créer un nouveau `blend_root/Sources/arm/renderpath/RenderPathCreator.hx`. Ceci fera en sorte qArmory écrase le chemin de rendu interne avec le vôtre.

```hx
package arm.renderpath;

class RenderPathCreator {

	public static function get():RenderPath {
		var path = new iron.RenderPath();
		path.commands = function() {
			path.setTarget(""); // Draw to framebuffer
			path.clearTarget(0xffffffff, 1.0); // Clear color & depth
			path.drawMeshes("mesh"); // Draw all visible meshes
		};
		return path;
	}
}
```

Il est également possible de remplacer/manipuler le chemin de rendu au moment de l'exécution en utilisant la commande `iron.RenderPath.setActive(path)`.
