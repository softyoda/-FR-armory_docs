# Utilisation de Git version

## Armory Updater

Naviguez jusqu'à `File - User Preferences... - Add-ons - Armory`. Avant le clonage, vous devrez peut-être installer Git d'abord - cliquez sur le bouton `Install Git` pour ouvrir la page de téléchargement. Lors de l'installation sur Windows, sélectionnez l'option `Use Git from the Windows Command Prompt`.

Ensuite, sélectionnez `Update SDK' et inspectez la ligne de commande pour plus de détails - le processus ne devrait prendre que quelques secondes. Une fois terminé, redémarrez Blender pour que les changements prennent effet. Si quelque chose ne va pas, utilisez le bouton `Restore SDK` pour annuler les changements.



![](/dev/img/gitversion/updater.png)

## Clone manuel

- Installer [Git](https://git-scm.com/download/win).
- Choisissez un emplacement pour cloner le sdk et ouvrez un terminal/une ligne de commande ici.

```
git clone --recursive https://github.com/armory3d/armsdk
cd armsdk
git submodule foreach --recursive git pull origin master
```

- Dans Blender, naviguez jusqu'à `File - User Preferences... - Add-ons - Armory`. Uncheck `Bundled SDK` et indiquez le chemin d'accès au dossier `armsdk` nouvellement cloné.

#### Mettre à jour

```
cd armsdk
git submodule foreach --recursive git pull origin master
git pull origin master
```

---

### Pour ller plus loin:

- Vous pouvez reconstruire Krom : https://github.com/Kode/Krom
- Vous pouvez reconstruire Blender lui-même avec Krom intégré : https://github.com/armory3d/krom_blender
