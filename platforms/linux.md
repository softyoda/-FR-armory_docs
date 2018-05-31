# Déploiement sous Linux

## Krom

- Créer un nouveau preset dans `Armory Exporter' et sélectionner la cible `Linux (Krom)`.
- Appuyez sur " Publier ".
- C'est ça ! Appuyez sur `Triangle - Ouvrir dossier` pour visualiser les fichiers exportés.

## Natif (C+++)

Pour que la compilation C+++ réussisse, il se peut que vous ayez besoin d'installer des paquets supplémentaires - lisez plus à[Kha/Wiki].(https://github.com/Kode/Kha/wiki/Linux).

Créez un nouveau preset dans *Properties - Render - Armory Exporter* et sélectionnez Linux target. Cliquez sur *Publier* pour exporter les fichiers de compilation.

Ensuite, vous pouvez compiler le projet en utilisant le fichier makefile généré dans *blend_file_location/build_projectname/linux-build/Release* ou en utilisant le projet[Code::Blocks](http://codeblocks.org) situé à *blend_file_location/build_projectname/linux-build*.

Pour que les ressources se chargent correctement, vous devrez copier l'exécutable dans le dossier contenant toutes les ressources du jeu.

Pour ce faire, il suffit de copier l'exécutable de *blend_file_location/build_projectname/linux-build/Release* dans *blend_file_location/build_projectname/linux*.

![](/platforms/img/linux/1.png)

Vous pouvez maintenant exécuter et empaqueter votre jeu !