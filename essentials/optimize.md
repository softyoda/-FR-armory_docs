# Optimisation

Armory est conçu pour éliminer automatiquement les fonctions inutilisées des projets exportés afin d'éviter la surcharge d'espace et de performance. Cette page traite des options permettant d'affiner ce processus.

## Temps de build

Pour garder les temps de build bas :
- Activer `Khamake Threads` dans les préférences d'armory
- Activer `Armory Project - Cache Shaders`
- Activer `Armory Project - Cache Compiler`

`Khamake Threads` activera la compilation multi-threaded shader/asset. Les `Cache Shaders/Compiler` permettront à Armory de réutiliser les données de la compilation précédente.

En fonction du CPU, les constructions répétées de scènes comme le [first_person](https://github.com/armory3d/armory_templates/tree/master/first_person) template devrait tenir en une seconde.

## Optimiser pour la taille

- Activer `Armory Project - DCE`
- Activer `Armory Project - Minimize Data`
- Activer `Armory Project - Asset Compression`
- Désactiver `Armory Project - Compiler Inline`

Inspectez `Armory Render Path` pour vous assurer que les fonctions qui ne sont pas utilisées sont désactivées. Les particules, le skinning, les ombres, les décalques, la translucidité ou certaines fonctions de post-traitement réduiront encore la taille.

Utilisez `Armory Exporter - Publish` pour exporter le projet. Ceci permettra d'effectuer des DCE (élimination du code mort).

Pour les cibles Krom/HTML5, utilisez un outil comme [jscompress.com](https://jscompress.com/) pour minimiser davantage les fichiers `krom.js`/`kha.js`. La scène par défaut contenant un seul cube devrait tenir dans 349KB/88KB(zip) en utilisant un chemin raccourcis.

Armory supporte plusieurs moteurs physiques - voir [oimo_module](https://github.com/armory3d/oimo_module).

## Optimiser les performances

- Activer `Armory Project - Minimize Data`
- Activer `Armory Project - Compiler Inline`
- Activer `Armory Project - Optimize Meshes`
- Activer `Armory Project - Batch Meshes` (experimental)
- Activer `Armory Project - Batch Materials` (experimental)

Les performances générales du moteur dépendront principalement du chemin de rendu. Le panneau `Armory Render Path` vous permet de créer plusieurs chemins de rendu, chacun ciblant une plate-forme ou une configuration différente. Selon que le jeu est géré par CPU ou GPU, des fonctions telles que le skinning ou les particules peuvent être configurées pour être calculer sur le CPU ou le GPU.
