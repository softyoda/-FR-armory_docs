# Vertex Colors

Cette page décrit comment rendre les couleurs de vertex associées aux données de maillage.

Commencez par le cube par défaut, entrez en mode **Vertex Paint** et peignez l'un des bords en rouge.

![](/graphics/img/vcols/0.jpg)

Pour inclure les couleurs de vertex dans le matériel, créez et connectez le noeud **Attribute** à la prise **Color**. Seul l'ensemble des couleurs d'un seul vertex par maillage est actuellement supporté.

![](/graphics/img/vcols/1.jpg)

Vous pouvez également utiliser le nœud Armory PBR pour connecter **Attribute** à la prise **Base Color**.

![](/graphics/img/vcols/2.jpg)

Appuyez sur **Play in Viewport**  pour vérifier le résultats.

![](/graphics/img/vcols/3.jpg)

Si vous avez des difficultés à afficher les couleurs des vertex dans des scènes plus complexes, l'invalidation du cache de maillage peut aider au cas où Armory n'a pas réussi à enregistrer les changements. Cochez **Properties - Object data - Armory Props - Invalidate Cache**.