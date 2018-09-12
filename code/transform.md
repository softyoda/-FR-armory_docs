# Transform

Transform décrit l'emplacement, la rotation, l'échelle et les dimensions de l'objet. Pour accéder à la transformation en trait de Haxe :

```haxe
var transform = object.transform;
```

Pour accéder aux propriétés de transformation avec les coordonées de l'objet :

```haxe
var m = transform.local; // Matrix
var l = transform.loc;   // Location
var r = transform.rot;   // Rotation
var s = transform.scale; // Scale
```

Pour accéder aux propriétés de transformation avec les coordonées de la scène :

```haxe
var m = transform.world;                     // Matrix
var l = transform.world.getLoc();            // Location
var r = new Quat().fromMat(transform.world); // Rotation
var s = transform.world.getScale();          // Scale
```

Pour manipuler las transformations :

```haxe
transform.translate(1, 2, 3); // x, y, z
transform.rotate(Vec4.zAxis(), 1.2); // Axis, angle in radians
```

Alternativement, modifiez directement les propriétés de transformation. Pour appliquer les modifications, appelez `buildMatrix()`:

```haxe
transform.loc.set(0, 5, 0);
transform.scale.x = 2.0;
transform.buildMatrix();
```

Pour régler l'emplacement, la rotation et l'échelle à l'aide d'une matrice :

```haxe
var m = Mat4.identity();
transform.setMatrix(m);
```

Pour récupérer le vecteur global de la vue :

```haxe
var look = transform.look();
```

Example:
- https://github.com/armory3d/armory_examples/tree/master/script_transform
