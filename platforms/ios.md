# Déploiement sur iOS

Avant d'exécuter sur un appareil mobile, assurez-vous que le projet est optimisé pour fonctionner sans problème sur le matériel cible. Il est recommandé de sélectionner *Mobile* prédéfini dans *Properties - Render - Armory Render Path*. De plus, il peut être nécessaire de simplifier **les matériaux, les textures et la géométrie**. Pour utiliser la résolution inférieure à la résolution maximale disponible, définissez la propriété *Armory Render Path - Resolution*.

## Natif (C+++)

Créez un nouveau preset dans *Properties - Render - Armory Exporter* et sélectionnez iOS target. Cliquez sur *Publier* pour générer des fichiers de projet iOS.

Pour procéder, installez et exécutez *XCode* à partir de MacOS App Store. Lancez XCode en ouvrant le projet généré situé à *blend_file_location/build_projectname/ios-build/projectname.xcodeproj*. Connectez votre appareil iOS et appuyez sur *Run*.

![](/platforms/img/ios/2.jpg)

Une fois compilé, le projet sera lancé sur votre appareil !
