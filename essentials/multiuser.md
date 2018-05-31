# Flux de travail multi-utilisateurs

Cette page traite des outils pour aider plusieurs personnes à travailler sur le même projet.

## Proxy lié
Le projet peut être divisé en plusieurs fichiers `.blend` individuels. Ces fichiers `.blend` sont ensuite combinés dans le fichier principal à l'aide de la fonctionnalité de liaison Blenders. Voir[exemple](https://github.com/armory3d/armory_examples/tree/master/linked_proxy).

## Outils proxy
Une fois que les objets sont liés dans le fichier principal, localisez les outils d'aide dans `Properties - Object - Armory Proxy`. Dans ce panneau, vous pouvez transformer la hiérarchie complète des objets liés en proxies en utilisant l'opérateur `Make Proxy`. Vous pouvez également gérer les propriétés à synchroniser avec l'objet lié original. Les propriétés vérifiées sont automatiquement synchronisées au `.blend` charger. Vous pouvez également déclencher la synchronisation manuellement en appuyant sur `ctrl + shift + o -> enter`.

## Édition de données liées
Blender est livré avec un add-on pratique qui vous permet de sauter directement dans le fichier source `.blend` de l'objet lié sélectionné. Activez l'extension `Edit Linked Library` pour déverrouiller cette fonctionnalité. Une vidéo expliquant comment utiliser l'add-on peut être trouvée[ici](https://vimeo.com/41440647).

## Racine du projet
Si vous conservez les fichiers `.blend' dans des sous-dossiers, il est nécessaire de définir le dossier racine du projet. Définissez `Properties - Render - Armory Project - Root` à l'emplacement du fichier principal `.blend`. Avec la racine du projet correctement configuré `.blend` fichiers dans les sous-dossiers seront en mesure de trouver les caractéristiques haxe, et il est également possible de `Play` les fichiers `.blend` eux mêmes.