# Déploiement sous Windows

## Krom

- Créer un nouveau preset dans `Armory Exporter' et sélectionner la cible `Windows (Krom)`.
- Appuyez sur `Publish`.
- C'est ça ! Appuyez sur `Triangle - Ouvrir dossier` pour visualiser les fichiers exportés.

## Natif (C+++)

Créez un nouveau preset dans *Properties - Render - Armory Exporter* et sélectionnez la cible Windows. Cliquez sur *Publish* pour exporter les fichiers de projet Visual Studio.

Pour ce faire, installez[Visual Studio](https://www.visualstudio.com/vs/community/). Assurez-vous d'installer des composants pour compiler le code C+++. Une fois installé, ouvrez le projet situé à *blend_file_location/build_project_name/windows-build/project_name.sln*.

![](/platforms/img/windows/1.jpg)

Ensuite, vous pouvez tester, déboguer et profiler votre projet dans Visual Studio. Lorsque vous êtes prêt à exporter le binaire final, passez en mode Release et construisez le projet.

![](/platforms/img/windows/2.jpg)

Une fois le processus de compilation terminé, copiez le binaire résultant à partir du dossier *Release* (dans ce cas *untitled.exe*) - -)

![](/platforms/img/windows/3.jpg)

- dans le dossier *blend_file_location/build_projectname/windows* qui contient également des ressources de jeu.

![](/platforms/img/windows/4.jpg)

Vous pouvez maintenant empaqueter et distribuer ce dossier !

## UWP (Universal Windows Platform)

TBD
