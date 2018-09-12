# Déploiement sous Windows

## Krom (V8)

- Créer un nouveau preset dans `Properties - Render - Armory Exporter` et sélectionner la cible `Windows (Krom)`.
- Appuyez sur `Publish`.
- Ça y est ! Appuyez sur `Triangle - Ouvrir dossier` pour visualiser les fichiers exportés.

<iframe width="560" height="315" src="https://www.youtube.com/embed/GVw3B5e4Rjs?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


## Natif (C+++)

Créez un nouveau preset dans `Properties - Render - Armory Exporter` et sélectionnez la cible de `Windows (C++)` . Cliquez sur `Publish` pour exporter les fichiers de projet Visual Studio.

Pour ce faire, installez[Visual Studio](https://www.visualstudio.com/vs/community/). Assurez-vous d'installer des composants pour compiler le code C+++. Une fois installé, ouvrez le projet situé à *blend_file_location/build_project_name/windows-build/project_name.sln*.

![](/platforms/img/windows/1.jpg)

Ensuite, vous pouvez tester, déboguer et profiler votre projet dans Visual Studio. Lorsque vous êtes prêt à exporter le binaire final, passez en mode Release et construisez le projet.

![](/platforms/img/windows/2.jpg)

Une fois le processus de compilation terminé, copiez le binaire résultant à partir du dossier *Release* (dans ce cas *untitled.exe*) - -)

![](/platforms/img/windows/3.jpg)

- dans le dossier *blend_file_location/build_projectname/windows* qui contient également des ressources de jeu.

![](/platforms/img/windows/4.jpg)

Vous pouvez maintenant empaqueter et distribuer ce dossier !

## HashLink (C)

Créez un nouveau preset dans `Properties - Render - Armory Exporter` et sélectionnez `Windows (HashLink)`. Cliquez sur `Publish` pour exporter les fichiers de projet Visual Studio. Après, ouvrez le projet exporté et compilez.

## Windows App (UWP)

Créez un nouveau preset dans `Properties - Render - Armory Exporter` et sélectionnez la cible `Windows App`. Cliquez sur `Publish` pour exporter les fichiers de projet Visual Studio. Après, ouvrez le projet exporté et compilez.

