# Global Illumination

Cette page présente un guide de démarrage rapide pour vous permettre de configurer facilement le **Global Illumination** dans vos projets d'Armory.

Armory dispose d'une technique d'illumination globale entièrement dynamique basée sur une combinaison du voxel cone-tracing et du screen-space ray-tracing. Tout d'abord, la scène est voxélisée et transformée en une texture 3D. Ces données sont ensuite utilisées pour obtenir un éclairage grossier de la scène. Ensuite, le traçage de l'espace-écran est effectué pour les détails.

- Téléchargez la [scène](https://github.com/armory3d/armory_examples/tree/master/voxelgi_teapots) (troll non inclus !).

<iframe width="560" height="315" src="https://www.youtube.com/embed/8KavBpfLLtY?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## Exigences

- Une carte graphique avec **OpenGL 4.5** (pour la voxélisation).
- Fonctionne sur **Windows** et **Linux**.
- Pour Blender 2.79, lancez le projet dans  **stand-alone window** (F5).

## Démarrage rapide

Pour activer l'éclairage global de votre scène en utilisant les paramètres par défaut, réglez `Armory Render Path - Preset` sur `Max (Render)`. Lisez ce qui suit pour en savoir plus sur la configuration.

## Voxel AO

Définissez `Armory Render Path - Global Illumination` sur `Voxel AO`.

La façon la moins chère d'utiliser les voxels, utilisable pour **l'occlusion ambiante et les ombres**. Fonctionne plus rapidement et consomme moins de mémoire par rapport à `Voxel GI`.

- Contrôler la qualité à l'aide de la propriété `Cones`.
- Contrôler l'intensité à l'aide de la propriété `Occlusion`.
- Changez les paramètres de traçage en utilisant les propriétés `Step, Range, Offset`.

<img src="./graphics/img/gi/ao.jpg" width="50%">

## Voxel GI

Définissez `Armory Render Path - Global Illumination` sur `Voxel GI`.

Voxel GI permet **l'éclairage diffus et spéculaire**. Il s'agit toujours d'une fonction lourde de performance qui ne devrait être activée que sur le matériel haut de gamme.

- Contrôlez la qualité à l'aide de la propriété `Cones`.
- Contrôlez l'intensité à l'aide des propriétés `Diffuse, Specular, Occlusion`.
- Changez les paramètres de traçage en utilisant les propriétés `Step, Range, Offset`.
- Changez la contribution de l'environement map aux lumières indirectes à l'aide de la propriété `Env Map`.

<img src="./graphics/img/gi/game.jpg" width="50%">

## Voxel Volume Setup

Localisez la propriété `Armory Render Path - Global Illumination`. Lorsqu'il est réglé sur `Voxel AO` ou `Voxel GI`, **le volume de voxelisation** peut être configuré. 

- Réglez `Dimensions' pour contrôler la taille du volume. Les objets placés hors de ce volume ne contribueront pas à l'éclairage global. Par défaut, les dimensions sont réglées à 16 - ce qui signifie qu'un volume de 16x16x16x16 unités de mélangeur est voxélisé. Ceci couvre conventionnellement la grille 3D par défaut montrée dans la vue 3D Viewport.
- Définissez `Résolution' pour spécifier la quantité de voxels utilisés pour le volume. Pour la performance, gardez ce chiffre à 128 ou moins.
- Réduisez le multiplicateur `Resolution Z` pour conserver la mémoire si votre scène est principalement plate sur l'axe Z (comme un échiquier). Avec `Resolution Z' réglé à 0.5, les dimensions 16x16x8 seront voxélisées.
- Activer la propriété `Revoxelize` pour mettre à jour le volume de voxel à chaque image. Dans le cas de scènes statiques, vous pouvez désactiver cette fonction - les objets en mouvement recevront toujours un éclairage indirect, mais ne l'affecteront pas.
- Avec `Revoxelize' coché, activez `Dynamic Camera` pour voxeliser la scène autour de la caméra. Au fur et à mesure que la caméra se déplace, le volume de voxélisation se déplace également, ce qui permet de couvrir des scènes infiniment grandes. Avec `Dynamic Camera` désactivé, le volume à l'origine de la scène (0,0,0,0) est voxélisé.

## Screen-space ray-tracing

#### Ray-traced AO

Définissez `Armory Render Path - SSGI` sur `RTAO`.

**L'occlusion ambiante** sera tracée.

- Contrôler la qualité à l'aide des propriétés `Rays, Step, Max Steps`.
- Contrôler l'intensité à l'aide de la propriété `Strength`.

#### Ray-traced GI

Définissez `Armory Render Path - SSGI` sur `RTGI`.

**L'éclairage diffus indirect** sera tracé.

- Contrôler la qualité à l'aide des propriétés `Rays, Step, Max Steps`.
- Contrôler l'intensité à l'aide de la propriété `Strength`.

#### Ray-traced Shadows

Les **ombres de contact** à petite échelle seront tracées.

Activez `Armory Render Path - SSRS`.

Augmenter la valeur `Step` dans le cas d'artefacts.

#### Ray-traced Reflections

Les **réflexions locales** seront tracées.

Activez `Armory Render Path - SSR`.

Augmenter la valeur `Step` dans le cas d'artefacts.

## Limites

Il y a encore de graves limitations à résoudre.

Des scintillements et des fuites peuvent se produire.
Pas encore de volumes multiples de voxel pour traiter de grandes distances.
Voxel GI est un GPU lourd.

## Baked lighting

Avec Blender, nous avons un moteur de traçage entièrement intégré à portée de main. Pour les scènes statiques, vous pouvez pré-calculer l'éclairage en lightmaps à l'aide de l'outil intégré  `Armory Bake`.

- Localisez le panneau `Properties - Render - Armory Bake`.
- Ajouter des objets à bake ou cliquer sur `Triangle - Add All`.
- Appuyez sur `Bake` pour générer des lightmaps pour tous les objets listés.
- Une fois terminé, cliquez sur `Apply pour restaurer les matériaux et empaqueter les lightmaps.
- Optionnellement, réglez `Armory Render Path - Preset` sur `Lightmap`.
- Lancer(F5) ! Armory prendra les materials baker.


<iframe width="560" height="315" src="https://www.youtube.com/embed/RM2gkM95Kuk?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## Light probes

Depuis la 2.8, blender supporte les Light probes. Grâce à cela, vous pouvez vous attendre à ce qu'Armory implémente cela en utilisant la même interface utilisateur.


Obtenir le [.blend](https://github.com/armory3d/archviz_templates/tree/master/baked) de ce tutoriel.