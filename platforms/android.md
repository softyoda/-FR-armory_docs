# Déploiement sur Android

Avant d'exécuter sur un appareil mobile, assurez-vous que le projet est optimisé pour fonctionner sans problème sur l'appareil cible. Il est recommandé de sélectionner *Mobile* prédéfini dans *Properties - Render - Armory Render Path*. De plus, il peut être nécessaire de simplifier **les matériaux, les textures et la géométrie**. Pour utiliser la résolution inférieure à la résolution maximale disponible, définissez la propriété *Armory Render Path - Resolution*.

## Natif (C+++)

Créez un nouveau preset dans *Properties - Render - Armory Exporter* et sélectionnez la cible Android. Appuyez sur *Publish* pour générer des fichiers de projet android.

Pour ce faire, installez et exécutez[Android Studio](https://developer.android.com/studio/index.html). Sélectionnez *Ouvrir un projet Android Studio existant*. Le projet est situé à *blend_file_location/build_projectname/android-native-build/projectname*.

![](/platforms/img/android/2.jpg)

Une fois le projet chargé, assurez-vous d'installer *NDK* en ouvrant *SDK Manager - SDK Tools* depuis Android Studio.

![](/platforms/img/android/3.jpg)

Android Studio peut vous demander d'installer des outils supplémentaires. Continuez jusqu'à ce que vous résolvez toutes les dépendances. Pour accélérer le processus de construction, sélectionnez'armv7' target dans l'onglet Build Variants. Connectez votre appareil** et appuyez sur *Run*. Le processus de compilation peut prendre jusqu'à plusieurs minutes lors de la compilation pour la première fois.

Note : Si vous rencontrez des erreurs de compilation, assurez-vous que la variante de compilation'armv7' est sélectionnée.

![](/platforms/img/android/4.jpg)

Une fois compilé, le projet sera lancé sur votre appareil !

## Krom

TBD