# Effets

Cette page fournit une vue d'ensemble des effets d'écran graphique que Armory peut fournir et améliorer visuellement vos projets et créer une immersion.

La liste complète des différents effets qu'il est possible d'utiliser dans l'Armurerie comprend \(triés par ordre alphabétique\) :

* [Anti-aliasing](/graphics/antialiasing.md) _\[Separate Article\]_
* [Auto Exposure](#auto-exposure) 
* [Bloom](#bloom)
* [Film Grain](#film-grain)
* [Fish-Eye](#fish-eye) _\[En cours de rédaction......\]_
* [Global Illumination](/graphics/global_illumination.md) _\[Separate Article\]_
* [Lens Flares](#lens-flares) \[_En cours de rédaction......_\]
* [Lens Textures](#lens-textures)
* [Letterboxing](#letterboxing)
* [LUT Colorgrading](#lut-colorgrading)
* [Motion Blur](#motion-blur)
* [Screen-Space Raytraced Shadows](#ssrs)
* [Screen-Space Reflections](#ssr)
* [Tonemapping](#tonemapping)
* [Vignette](#vignette)
* [Volumetric Fog](#volumetric-fog) _\[En cours de rédaction......\]_
* [Volumetric Light](#volumetric-light)

_Veuillez noter que certains de ces effets ont leurs propres articles pour plus de documentation.._

---

## Auto Exposure {#auto-exposure}

L'auto exposition ou l'adaptation oculaire est un effet où l'exposition d'une scène est automatiquement ajustée en fonction de la luminance d'une image. Cet effet imite la capacité oculaire de l'œil à s'adapter aux différents niveaux d'obscurité et de lumière.

|  |
| :--- |
| _**To do: .....Insert an illustratory gif here...**_ |

##### Properties:

Auto Exposure Strength - _Règle l'intensité de l'exposition automatique. Il n'est pas recommandé de régler cette valeur à 1 ou plus, car les surfaces blanches pleines deviennent complètement sombres. \[Défaut: 0.7\]_

**Comment faire:**

Basculer la propriété booléenne située à: **Armory Render Path** &gt; **Auto Exposure**.

## Bloom {#bloom}

Le Bloom Glow est un effet d'écran qui reproduit les artefacts qui se produisent dans les caméras du monde réel, et aide à donner l'illusion d'une lumière vive vue à travers une caméra. En raison des limitations des ensembles d'affichage typiques ne supportant pas l'HDR\(High Dynamic Range (Haute dynamique de couleur et de contraste\), la possibilité de rendre des objets exceptionnellement lumineux n'est pas disponible et donc serré à une couleur blanche ordinaire sur SDR \(Standard Dynamic Range\). Malgré cela, les moteurs de jeu peuvent encore prendre en compte les HDR en termes d'effets, où les valeurs HDR sont mises à disposition des shaders, le bloom étant l'une d'entre elles.

Avec les paramètres par défaut, Armory Engine ajoute du bloom pour les éléments dont la luminosité est supérieure à ce qu'un ensemble d'affichage SDR est capable de rendre \(Une valeur de 1 étant égale à blanc\).  
![](/graphics/img/se/Bloom_Image.jpg)

_Bloom used in a scene. Note the glow surrounding the bright areas._

##### Propriétés:

Threshold - _Définit le seuil de délimitation pour l'application de l'effet de bloom. Des valeurs plus basses appliquent l'effet de bloom  aux éléments moins brillants. \[Défaut: 1\]_

Strength - _Règle la force de l'effet de bloom. \[Défaut: 3.5\]_

Radius - _Règle la taille du bloom. Des valeurs plus élevées augmentent la taille de la lueur. \[Défaut: 3\]_

**Comment faire:**

Changer la propriété booléenne située à l'emplacement suivant : **Armory Render Path** &gt; **Bloom**.

| Blend example |
| :--- |
| [https://github.com/armory3d/armory\_examples/tree/master/render\_bloom](https://github.com/armory3d/armory_examples/tree/master/render_bloom) |

## Grain {#film-grain}

Le grain ou granularité du film est un effet d'écran généralement observé dans les films et la photographie en raison de la présence de petites particules pendant le traitement du film. Dans Armory, l'effet est simulé par un shader qui ajoute du bruit à chaque image.

| Sans grain | Avec grain |
| :--- | :--- |
| ![](/graphics/img/se/Without_Grain.gif) | ![](/graphics/img/se/With_Grain.gif) |

_Comparaison d'une scène avec et sans grain. _

##### Propriété:

Strength - _Règle la force du grain du film dans la scène. \[Défaut: 2\]_

**Comment faire:**

Basculer la propriété booléenne située sur : **Armory Render Props** &gt; **Film Grain**.

## Fish Eye {#fish-eye}

En cours de rédaction......

## Lens Flares {#lens-flares}

En cours de rédaction......

## Lens Textures {#lens-textures}

En cours de rédaction......

## Letterboxing {#letterboxing}

La Letterboxing est un effet dans lequel un format d'écran large est transféré vers un format vidéo de largeur standard. Comme son nom l'indique, le cadre est compressé dans un cadre plus large en forme de boîte aux lettres. Dans le jeu, il est souvent utilisé pendant les coupes et les dialogues.

| Sans letterboxing | Avec letterboxing |
| :--- | :--- |
| ![](/graphics/img/se/No_Letterbox.jpg) | ![](/graphics/img/se/Letterbox.jpg) |

##### propriété:

Size - La taille en relation avec la dimention du letterboxing._. \[Défaut: 0.1\]_

| Blend Example |
| :--- |
| Going to be done... |

## LUT Colorgrading {#lut-colorgrading}

L'étalonnage 3D basé sur LUT est un effet dans lequel un utilisateur a fourni un fichier LUT. \(dans armory juste un fichier .jpg\) ajuste les couleurs de l'écran. Souvent utilisé pour créer des scènes d'ambiance.![](/graphics/img/se/Render Result - Noir.png)

_Une scène montrant un exemple d'un fichier Noir et blanc LUT._

**Comment faire:**

Dans votre dossier de projet, créez un dossier appelé "Bundled" et dans ce dossier, fournissez une un fichier LUT de 512x512 appelée "luttexture.jpg".

Dans Armory Render Props &gt; LUT Texture, write "luttexture.jpg".

**Comment faire vos propre fichiers LUT \(Procédure recommandé\):**

Tout d'abord, prenez une capture d'écran de votre scène que vous n'avez pas encore colorée, et ouvrez-la dans votre éditeur d'images préféré \(Photoshop, Affinity Photo, Gimp, etc.\)

Dans le coin, mettez un fichier LUT neutre \(inclus dans l'exemple de mélange ci-dessous\) à côté et commencez à ajouter des ajustements.

Supprimez votre capture d'écran, de sorte que seul le 512x512 soit visible avec votre LUT et vos ajustements de couleur.

Enregistrez-le sous le nom "luttexture.jpg" en utilisant les réglages que vous avez effectués.

| Blend Example |
| :--- |
| [https://github.com/armory3d/armory\_examples/tree/master/render\_lut\_colorgrading](https://github.com/armory3d/armory_examples/tree/master/render_lut_colorgrading) |

## Motion Blur {#motion-blur}

En cours de rédaction......

## Screen-Space Raytraced Shadows {#ssrs}

En cours de rédaction......

## Screen-Space Reflections {#ssr}

Screen-Space Reflections est une technique où les objets de l'espace sont réfléchis sur un support brillant comme le métal ou l'eau. La limitation de ce shader est que seuls les objets visibles à l'intérieur du cadre sont réfléchis.

**Propriété:**

Ray Step - _Description prochainement (en construction)..._

Ray Step Minimum - _Description prochainement (en construction)..._

Search Distance - _Description prochainement (en construction)..._

Falloff - _Description prochainement (en construction)..._

Jitter - _Description prochainement (en construction)..._

**Comment faire:**

Activer la propriété booléenne située à l'emplacement suivant : **Armory Render Path** &gt; **SSR**.

## Tonemapping {#tonemapping}

Le Tonemapping est une technique utilisée dans le traitement de l'image et les graphiques utilisés pour mapper un ensemble de couleurs à un autre afin de simuler les apparences des images HDR à un ensemble d'affichage SDR. Armory est livré avec 4 algorithmes de tonemapping :

* Filmic - L'option Défaut d'Armory. 
* Filmic 2 - Option Défaut dans Unreal Engine. Utilise la courbe ACES\(Academy Color Encoding System\).
* Reinhard - Un opérateur de tonemapping très couramment utilisé.
* Uncharted - Une implémentation de tonemapping développée pour le jeu Uncharted 2.

| Aucun | Filmic | Filmic2 | Reinhard | Uncharted |
| :--- | :--- | :--- | :--- | :--- |
| ![](/graphics/img/se/T_None.jpg) | ![](/graphics/img/se/T_Filmic.jpg) | ![](/graphics/img/se/T_Filmic2.jpg) | ![](/graphics/img/se/T_Reinhard.jpg) | ![](/graphics/img/se/T_Uncharted.jpg) |

_Une comparaison de la façon dont les différents opérateurs de tonemapping affectent la luminosité et les couleurs d'un cadre.._

**Comment faire:**

Sélectionnez l'option de tonemapping située à l'adresse: **Armory Render Props** &gt; **Tonemapping**.

## Vignette {#vignette}

La vignette est un effet d'écran où la luminosité est réduite à la périphérie d'un cadre. C'est souvent un effet involontaire qui se produit dans la photographie et l'optique en raison des limitations de l'objectif. Dans le jeu, il est souvent utilisé pour créer plus de focus sur les points centraux de l'écran.

|  |
| :--- |
| _**To do: .....Insert an illustratory jpg's here...**_ |

**Comment faire:**

Activer la propriété booléenne située à l'emplacement suivant : **Armory Render Props** &gt; **Vignette**.

## Volumetric Fog {#volumetric-fog}

En cours de rédaction......

## Lumière Volumétrique {#volumetric-light}

La lumière volumétrique (souvent appelée rayons divins) est un effet qui permet à l'utilisateur de créer des faisceaux de lumière émanant d'une source de lumière. Dans le monde réel, cet effet est connu sous le nom de rayons crépusculaires et est présent lorsque la lumière forte traverse un milieu tel que le brouillard, le gaz, la poussière, etc.

| Sans lumière volumétrique | Avec lumière volumétrique |
| :--- | :--- |
| ![](/graphics/img/se/No_Volumetric_Lights.jpg) | ![](/graphics/img/se/Volumetric_Lights.jpg) |

_Une scène avec et sans lumière volumétrique allumée. Les faisceaux lumineux qui traversent les fenêtres sont visibles à droite. Notez également que la lumière volumétrique affecte l'éclairage global._

**Comment faire:**

Activer la propriété booléenne située à l'emplacement suivant : **Armory Render Path** &gt; **Volumetric Light**.

Ajoutez un projecteur pointant vers l'endroit où vous voulez que la lumière volumétrique soit.

