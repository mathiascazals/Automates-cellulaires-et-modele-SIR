<span style='font-size:xx-large'>**Automates cellulaires et modèle SIR \- GA2\-7 \- Cazals Mathias \- Leiner Lucas**</span>

<span style='font-size:x-large'>**Présentation du projet**</span>

Dans ce projet, nous avons étudié la propagation d'un virus au sein d'une population en utilisant des automates cellulaires. 

Pour cela, nous avons simulé la diffusion du virus dans une grille de pixels pour mieux comprendre les mécanismes de propagation. Notre approche s'est portée sur un rapprochement entre notre résultat et le modèle mathématique "SIR" utilisé pour décrire la propagation d'une maladie au sein d'une population en la classant en trois états : Sain, Infecté, et Rétabli. 

Pour réaliser cette comparaison nous avons donc créer deux codes différents, un pour générer les automates cellulaires et un autre pour adapter en python le modèle SIR. Dans les deux cas, nous obtenons un graphique composé de plusieurs courbes décrivant l'évolution de l'état de la population. Ainsi cela offre des perspectives d'analyse de notre simulation et de sa précision par rapport à un modèle mathématique fiable.

<span style='font-size:x-large'>**Représentation visuelle**</span>  

<span style='font-size:large'>Représentation des automates cellulaires</span>

Pour ce projet, nous avons choisis les automates cellulaires pour leur côté visuel et leur capacité à simuler des phénomènes réels de manière pertinente. Cette approche nous permet d'étudier la dynamique de la propagation d'une maladie tout en la rendant applicable à des situations concrètes. 

Pour cela, nous avons utilisé la bibliothèque pygame de python pour réaliser une grille qui représente une population avec des pixels de couleurs variées en fonction de l'état des personnes, chaque personne étant symbolisée par un pixel. 

Initialement, nous avions hésité avec une autre option de représentation visuelle. En effet, avant de choisir une grille avec des pixels pour représenter une population, nous avions sélectionné des déplacements de points avec des vecteurs de mouvements dans une grille. Dans cette interprétation, un point est égal à une personne et ces derniers changent de couleur en fonction de l'état de la personne qu'ils représentent.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/1.png"   width="535.969px"  height="326.375px"  style="object-fit:cover"/>

Ce schéma est une bonne option car elle est lisible, compréhensible et facilement interprétable mais est assez limitée. En effet, le nombre de points que l'on étudie dans cette grille peut difficilement dépasser les 200 personnes et ainsi si l'on souhaite ajouter des paramètres plus précis que les simples états sains, infectés et rétablis comme le taux de mortalité, les naissances, les vaccins,... , l'analyse de cette représentation devient plus compliquée et trop aléatoire.

De plus, la méthode de calcul entre les deux modèles pour la propagation du virus est assez différente puisque avec les points, la probabilité que ces derniers se contaminent est calculé quand deux éléments rentrent en contact au fil de leurs mouvements. A l'inverse dans l'autre modèle, les pixels sont en contact constant, ce qui implique que chaque personne peut potentiellement contaminer 8 personnes autour d'elle en permanence. Les valeurs pour les paramètres que nous utilisons dans le code serons donc différentes.

Il était donc plus judicieux selon nous de prendre la deuxième option qui offre plus de possibilités et d'analyses graphiques au vu de l'échelle plus importante.

En effet, sur cette grille il y a 10 000 pixels soit une représentation 50 fois plus importante que sur l'autre grille. 

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/2.png"   width="291px"  height="309px"  style="object-fit:cover"/>

Dans ce modèle, chaque pixel représente une personne et peut être dans l'un des quatre états distingués par une couleur : blanc l'état sain, vert pour l'état infecté, gris pour l'état rétabli et rouge pour mort. Au départ, à la manière d'un virus, une seule personne est infectée et se trouve au centre de la grille. Au fur et à mesure que les images de la grille se rafraîchissent, de nouvelles personnes en contact avec l'infectée peuvent être contaminées à leur tour, prenant la couleur verte. Ensuite, après avoir été malade, une personne passe à l'état de rétablissement, symbolisé par la couleur grise et peut décéder donc devenir rouge en fonction des paramètres définis défini.

<span style='font-size:large'>Représentation graphique</span>

Ainsi, que ce soit dans le cas de la représentation de la diffusion du virus par automate cellulaire ou par le modèle SIR, nous avons deux graphiques différents. Nous avons pour cela employé la bibliothèque matplotlib pour étudier sous forme graphique l'évolution de l'état des personnes de la population et en fonction des paramètres définis comme le taux de propagation ou l'indicateur de rétablissement.

La courbe bleue représente l'évolution du nombre de personnes saines au fur et à mesure du temps.

La courbe orange indique elle l'évolution du nombre de personnes infectées.

Enfin, la courbe verte représente elle l'évolution du nombre de personnes rétablies, donc après avoir été infectées.

Ces courbes peuvent énormément varier en fonction du paramétrage qu'on fait  mais restent tout de même la plupart du temps proportionnelles entre elles.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/3.png"   width="371px"  height="287px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/4.png"   width="383.5px"  height="284.496px"  style="object-fit:cover"/>


