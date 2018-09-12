# Particules supportées

Les systèmes de particules sont actuellement au stade expérimental et seront encore améliorés.

## Mise en place

- Par défaut, Armory utilise la simulation de particules par le GPU.
- L'accès au node matériel `Particle Info` nécessite une simulation GPU.
- Pour utiliser la simulation CPU, définissez `Properties - Armory Render Path - Particles` sur `CPU`.
- Le rendu est toujours effectué en utilisant l'instanciation GPU.

## Fonctionnalités

- Type (Emitter, Hair)
- Seed
- Emission - Number
- Emission - Start
- Emission - End
- Emission - Lifetime
- Emission - Random
- Emission - Emit From (Verts, Volume)
- Velocity - Emitter Object
- Velocity - Random
- Physics (No, Newtonian)
- Physics - Newtonian - Size
- Physics - Newtonian - Mass
- Render (Object)
- Render - Dupli Object
- Render - Size
- Field Weights - Gravity
- Particle Info material node - GPU particles
