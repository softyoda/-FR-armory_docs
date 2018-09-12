# Krom

[Krom](https://github.com/Kode/Krom) est la runtime par défaut utilisée pour jouer aux jeux Armory. Il est conçu pour des temps de compilation et des performances rapides, alimenté par le moteur[Chakra] (https://github.com/Microsoft/ChakraCore) ou[V8] (https://developers.google.com/v8/). Par rapport à l'environnement précompilé (Armory peut également cibler directement C/C++), Krom présente plusieurs avantages.

Lorsque vous clonez Armory à partir de git, il n'est pas nécessaire de construire quoi que ce soit. Le moteur est compilé à côté du jeu en `JS` instantanément quand vous appuyez sur le bouton `Play`. Vous pouvez passer à la dernière version d'Armory en utilisant l'[updater intégré](https://armory3d.org/manual/#/dev/gitversion) à tout moment. Vous pouvez bricoler les sources du moteur et chaque modification est instantanément en direct pendant que vous jouez. Apprenez et expérimentez librement.

Krom expose les capacités matérielles natives et fonctionne sur n'importe quelle API graphique. Il s'agit d'un exécutable unique, qui pèse environ 7.9MB/2.8MB(zip) sous Windows/Chakra. Krom peut fonctionner de manière autonome ou intégrée dans des programmes existants. En dehors de JS, WebAssembly peut être utilisé pour inclure du code C/C++.

Une sécurité est assurée lors de la construction, et une traçabilité de paquet est lancée pour les erreurs d'exécution. En plus de cela, un débogueur est disponible. Une fois prêt à publier, Krom peut se déployer sous Windows, Linux et macOS à partir d'une seule plate-forme en quelques secondes. Les jeux déployés peuvent être mis à jour simplement en patchant le fichier `krom.js'. Krom offre également des capacités d'exécution de scripts.

<iframe width="560" height="315" src="https://www.youtube.com/embed/GVw3B5e4Rjs?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
