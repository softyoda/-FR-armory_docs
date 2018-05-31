# Particules supportées

Les systèmes de particules sont actuellement au stade expérimental et seront encore améliorés.

## Mise en place

La simulation CPU est efficace pour les mesh high-poly, tandis que le GPU est efficace pour simuler des hordes mesh low poly ou pour accéder aux `Particle Info`. Le rendu lui-même se fait toujours en utilisant l'instanciation GPU.

Pour activer la simulation de particules GPU :
- Cochez `Properties - Particle System - Armory Props - GPU Simulation`.
- Sélectionnez *Dupli Object* (objet émis) et réglez `Properties - Materials - Armory Props - Particle` sur `GPU`.
- Cette configuration sera éventuellement automatisée.

Pour activer la simulation de particules CPU :
- Sélectionnez *Dupli Object* (objet émis) et réglez `Properties - Materials - Armory Props - Particle` sur `CPU`.
- Cette configuration sera éventuellement automatisée.

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
