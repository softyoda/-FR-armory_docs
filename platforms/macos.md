# Déploiement sur macOS

## Krom

Créer un nouveau preset dans `Armory Exporter' et sélectionner la cible `MacOS (Krom)`.
Appuyez sur " Publier ".
C'est ça ! Appuyez sur `Triangle - Open Folder` pour visualiser les fichiers exportés.

## Natif (C+++)

Créez un nouveau preset dans *Properties - Render - Armory Exporter* et sélectionnez MacOS target. Cliquez sur *Publish* pour exporter les fichiers de projet XCode.

Pour continuer, installez[XCode].(https://developer.apple.com/xcode/). Une fois installé, ouvrez le projet situé à *blend_file_location/build_projectname/osx-build/projectname.xcodeproj*.

![](/platforms/img/macos/1.jpg)

Ensuite, vous pouvez tester, débugger  et profiler votre projet dans XCode.

![](/platforms/img/macos/2.jpg)

Lorsque vous êtes prêt à exporter le binaire final, appuyez sur Menu - Produit - Archive.
