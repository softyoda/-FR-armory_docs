# Physics

Armory est conçu pour fonctionner avec n'importe quel moteur physique. Un [code glue](https://en.wikipedia.org/wiki/Glue_code) est généré en interne, celui-ci relie le moteur physique à la simulation. Cela vous permet de choisir le moteur physique le plus approprié en fonction des besoins du projet et rend Armory à l'épreuve du temps.

Si aucun rigidy body n'est détecté dans la scène, Armory n'active pas le module physique, pour économiser de l'espace et des performances. Pour forcer le module de physique, passez `Armory Project - Physics` de  `Auto` a `Enabled`.

Par défaut, Armory est configuré pour utiliser une version complète[Bullet physics] (https://github.com/armory3d/haxebullet). Si un moteur plus léger est suffisant,[Oimo physics](https://github.com/armory3d/oimo_module) est fourni. Avec Oimo, les formes de mailles triangulaires sont approximées à l'aide de coques convexes.

Pour choisir un moteur physique actif, définissez la propriété `Armory Project - Physics Engine`.
