# WebAssembly

![](/code/img/wasm/0.jpg)


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

// Inclure la fonction principale, Armory l'appelle quand le trait est instancié.
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


## Programmez Armory en Rust


Comme dans l'exemple précédent, la rotation d'un cube en `Rust`.

```rust
extern {
  fn notify_on_update(f: extern fn() -> ()) -> ();
  fn get_object(name: *const i8) -> i32;
  fn set_transform(object: i32, x: f32, y: f32, z: f32, rx: f32, ry: f32, rz: f32, sx: f32, sy: f32, sz: f32) -> ();
}

#[no_mangle]
pub extern "C" fn update() -> () {
  unsafe {
    let name = std::ffi::CString::new("Cube").unwrap();
    let object = get_object(name.as_ptr());
    static mut rot: f32 = 0.1;
    rot += 0.01;
    set_transform(object, 0.0, 0.0, 0.0, 0.0, 0.0, rot, 1.0, 1.0, 1.0);
  }
}

#[no_mangle]
pub extern "C" fn main() -> i32 {
  unsafe {
    notify_on_update(update);
  }
  return 0;
}
```

Vous pouvez compiler cette source de `Rust` dans `Wasm` en direct sur [webassembly.studio](https://webassembly.studio/?f=qi0imd4j9t).


- Example sur [GitHub](https://github.com/armory3d/armory_examples/tree/master/web_assembly/rust_trait)


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
