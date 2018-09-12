# Déploiement en HTML5

## Navigateur

Créez un nouveau preset dans *Properties - Render - Armory Exporter* et sélectionnez HTML5 target. Cliquez sur *Publish* pour exporter les fichiers HTML5.

Les fichiers résultants seront situés à *blend_file_location/build_projectname/html5*.

* Notez que vous devez copier ces fichiers sur un serveur web ou démarrer un serveur local. Sinon, vous obtiendrez une erreur d'origine croisée lors de l'ouverture de index.html directement pour des raisons de sécurité des navigateurs web. Lors de la lecture d'un projet HTML5 à partir de Blender, Armory démarre automatiquement un serveur local. Avec Python installé, vous pouvez démarrer le serveur local à partir du terminal en utilisant `python -m SimpleHTTPServer` dans le répertoire build_projectname/html5 et ensuite naviguer jusqu'à http://localhost:8000 dans votre navigateur web.*.

![](/platforms/img/html5/1.png)


## Embed

Intégrer des projets Armory dans des pages Web existantes est très simple. Une fois le projet publié, inspectez le fichier `index.html` exporté. Notez les éléments `<canvas>' et `<script>'.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
    <title>Armory</title>
</head>
<body style="margin: 0; padding: 0;">
    <p align="center"><canvas align="center" style="outline: none;" id='khanvas' width='1280' height='720'></canvas></p>
    <script src='kha.js'></script>
</body>
</html>
```