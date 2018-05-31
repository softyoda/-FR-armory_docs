# Substance Painter

Cette page décrit comment utiliser Armory avec[Substance Painter](https://www.allegorithmic.com/products/substance-painter) pour **Peindre des textures en 3D**.

*Notez que ce sujet ne concerne que les spécificités de d'Armory et qu'il est nécessaire d'avoir des connaissances générales sur Substance Painter.*

Importez votre géométrie préparée pour la peinture de texture dans Substance Painter. Pour ce tutoriel, nous utiliserons le[Modèle Vela].(https://share.allegorithmic.com/libraries/1633).

![](./tooling/img/subst/0.jpg)

Once the model is painted, we want to import resulting textures back into Armory. Click **File - Export Textures...**

Choose a destination for file export and select **PBR MetalRough** config (or a compatible roughness-metallic model like Sketchfab). Hit **Export**.


Une fois le modèle peint, nous voulons importer les textures résultantes dans Armory. Cliquez sur **File - Export Textures...**

Choisissez une destination pour l'exportation de fichier et sélectionnez **PBR MetalRough** config (ou un modèle compatible roughness-metallic comme Sketchfab). puis cliquez sur **Export**.





![](./tooling/img/subst/1.jpg)

Localiser les textures exportées dans la destination spécifiée.

![](./tooling/img/subst/2.jpg)

Dans Blender, sélectionnez le modèle peint et entrez dans l'éditeur **material editor**. Choisissez **Add - Group - Armory PBR** et connectez-le à la **Material Output**. Déposer les textures exportées de Substance Painter dans le matériel et les connecter aux prises appropriées (base color, occlusion, normal, roughness, metallic..).

Avec les matériaux et l'éclairage et en jouant la scène, vous serez en mesure d'obtenir un résultat similaire à celui de Substance Painter.

![](./tooling/img/subst/3.jpg)
