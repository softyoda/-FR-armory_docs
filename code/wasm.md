# WebAssembly

![](/code/img/wasm/0.jpg)

Note : Cette fonctionnalité nécessite armory 0.4/git. Utilisez[Armory Updater](http://armory3d.org/manual/#/dev/gitversion) pour l'obtenir maintenant.

## Intro

[WebAssembly](http://webassembly.org/) (`Wasm`) est un format d'instruction binaire pour une machine virtuelle basée sur une pile, conçue comme une cible portable pour la compilation de langages tels que `C`/`C++`/`Rust`.

Armory peut être programmé avec `Wasm` pour une exécution de code de haute performance. L'inclusion des modules WebAssembly est supportée sur les plates-formes `HTML5` et `Desktop (Windows, Linux, macOS)`en utilisant[Krom](https://github.com/Kode/Krom).

## Programmez Armory en C

Dans l'exemple suivant, nous implémentons un trait (un morceau de logique attaché à un objet) dans `C`. Ce trait fait tourner un cube placé dans la scène :

```c
#define WASM_EXPORT __attribute__((visibility("default")))

// Declare Armory API used in this module
// github.com/armory3d/armory/blob/master/Sources/armory/trait/internal/wasm_api.h
void notify_on_update(void* f);
int get_object(const char* name);
void set_transform(int object, float x, float y, float z,
	float rx, float ry, float rz, float sx, float sy, float sz);

WASM_EXPORT
void update() {
	static float rot = 0.0f;
	rot += 0.01f;
	set_transform(get_object("Cube"), 0, 0, 0, 0, 0, rot, 1, 1, 1); // Set cube rotation
}

WASM_EXPORT
int main() {
	notify_on_update(update); // Register callback
	return 0;
}
```
Vous pouvez compiler cette source `C' dans `Wasm' en direct sur[webassembly.studio](https://webassembly.studio/?f=kl1f79ll4x). Placez le fichier `.wasm' résultant dans le dossier `blend_location/Bundled`.

Sélectionnez le cube et naviguez jusqu'à `Properties - Object - Armory Traits`. Créez un nouveau trait `Wasm` et remplissez la propriété `Module`. Appuyez sur Play(`F5`) et regardez le cube tourner !



<a href="./code/img/wasm/1.jpg">![](./code/img/wasm/1.jpg)</a>


- Example sur [GitHub](https://github.com/armory3d/armory_examples/tree/master/web_assembly/c_trait)


## Appel Wasm depuis Haxe.

Pour encore plus de flexibilité, le " wasm " peut être appelé directement à partir d'un trait écrit en " Haxe ". Commencez par une simple fonction "C" :

```c
#define WASM_EXPORT __attribute__((visibility("default")))

WASM_EXPORT
float test() {
	return 0.01f;
}
```
Vous pouvez compiler cette source `C' dans `Wasm' en direct sur[webassembly.studio](https://webassembly.studio/?f=gkkao6y44ga). Placez le fichier `.wasm' résultant dans le dossier `blend_location/Bundled`.

Pour appeler `test()`depuis Haxe :

```haxe
package arm;
import iron.data.*

class MyTrait extends iron.Trait {
	public function new() {
		super();
		notifyOnInit(init);
	}

	function init() {
		Data.getBlob("main.wasm", function(b:kha.Blob) { // Load wasm blob
			var wasm = Wasm.instance(b); // Create wasm module
			var rot = 0.0;
			notifyOnUpdate(function() {
				rot += wasm.exports.test(); // Call function from wasm module!
				object.transform.setRotation(0, 0, rot);
			});
		});
	}
}

```

- Example sur [GitHub](https://github.com/armory3d/armory_examples/tree/master/web_assembly/call_wasm)
