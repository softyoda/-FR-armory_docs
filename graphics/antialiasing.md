# Anti-aliasing (AA)

L'aliasing a un grand impact sur la qualité de l'image. Pour le combattre, Armory est pré-équipée de plusieurs solutions. Chacun d'eux a un rapport qualité/performance variable.

- [No AA](#no-aa)
- [MSAA](#msaa)
- [FXAA](#fxaa)
- [Subpixel Morphological AA](#subpixel-morphological-aa)
- [Temporal AA](#taa)
- [Super sampling](#super-sampling)

![](/graphique/img/img/aaa/noaaa_taa.jpg)

#### No AA

AA peut être complètement désactivé. Actuellement, Forward Low render path n'a pas d'AA activé par défaut.

![](/graphique/img/img/aaa/noaa.jpg)

### MSAA

MSAA peut être utilisé pour le chemin de rendu Forward Low, ou n'importe quel chemin personnalisé qui rend directement au framebuffer. MSAA peut être activé en réglant **Render** - **Armory Build** - **Samples per Pixel**. Entrer une valeur de 1 (désactivé) à 16 (qualité maximale).

### FXAA
La technique la plus rapide, au prix d'un brouillage de certains éléments.
![](/graphique/img/img/aaa/fxaa.jpg)

### Subpixel Morphological AA
Utilisé en voie différée.
![](/graphics/img/aa/smaa.jpg)

### Temporal AA
Utilisé en voie haute différée. Pour les scènes dynamiques, une mémoire tampon de vitesse est nécessaire pour la repojection.
![](/graphique/img/img/aaa/taa_smaa.jpg)

#### Super sampling
Méthode très coûteuse produisant de très bons résultats.
![](/graphiques/img/img/aaa/taa_smaa_smaa_2x.jpg)

