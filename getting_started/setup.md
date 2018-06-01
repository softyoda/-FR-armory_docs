# Installation

Armory est livrée avec tout ce dont vous avez besoin. **Blender 2.79** est utilisé avec **Armory player** intégré. Les versions 2.8** de Blender 2.8** sont actuellement expérimentales. Les sources d'Armory sont disponibles sur [GitHub](https://github.com/armory3d/).

- Décompressez  **Armory_version.zip** à l'endroit de votre choix. *(Sous Windows, préférez un chemin court comme 'C:\Dev' ou décompressez avec [7-zip](http://www.7-zip.org) pour éviter de longues erreurs de parcours et accélérer l'extraction.)*
- Exécutez Blender situé dans le SDK dézipper. *(Sous Windows, il se peut que vous ayez besoin de l'activer pour la première fois en cliquant sur **Plus d'information** - **Passer ** (More info - Run anyway**.)*

<img src="./getting_started/img/winrun.png" width="50%">

- Pour vérifier que tout fonctionne correctement, enregistrez votre fichier .blend, passez au moteur `Cycles Render` ou `Eevee` (en utilisant un menu déroulant situé dans l'en-tête info) et appuyez sur le bouton **Play in Viewport** (P), situé dans l'en-tête de la vue 3D.

<iframe width="560" height="315" src="https://www.youtube.com/embed/1Ey1MAIRPm4?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

- Continuer vers le  [Playground tutorial](./getting_started/playground.md) pour en savoir plus. Si vous avez du mal à mettre les choses en place, faites en nous part sur le [forum](http://armory3d.org/community.html) ou sur le [discord](https://discord.gg/tpMbh2C)!


## Utilisation d'Armory comme add-on

Si vous n'avez pas besoin du lecteur intégré, Armory peut être utilisé comme add-on uniquement dans l'installation standard de Blender. Le lecteur se lancera alors dans une fenêtre séparée.

- [Téléchargez](http://armory3d.org/download.html) et décompressez le SDK approprié pour votre plate-forme.
- Dans Blender, sélectionnez  **File** - **User Preferences...** et naviguer jusqu'à l'onglet **Add-ons**.
- Cliquez sur **Install from File...**
- Séléctionnez **armory.py** dans *my_unpacked_sdk/Armory/armsdk/armory/blender/addon* (sur MacOS l'emplacement est *my_unpacked_sdk/Armory/Blender.app/armsdk/armory/blender/addon*)
- **Activez** l'add-on et **définir l'emplacement du SDK** sur **my_unpacked_sdk/Armory/armsdk*
- Appuyez sur **Save User Settings** en bas et redémarrer Blender. C'est tout !
