# **Automates cellulaires et modèle SIR \- GA2\-7 \- Cazals Mathias \- Leiner Lucas**

## **Présentation du projet**

Dans ce projet, nous avons étudié la propagation d'un virus au sein d'une population en utilisant des automates cellulaires. 

Pour cela, nous avons simulé la diffusion du virus dans une grille de pixels pour mieux comprendre les mécanismes de propagation. Notre approche s'est portée sur un rapprochement entre notre résultat et le modèle mathématique "SIR" utilisé pour décrire la propagation d'une maladie au sein d'une population en la classant en trois états : Sain, Infecté, et Rétabli. 

Pour réaliser cette comparaison nous avons donc créer deux codes différents, un pour générer les automates cellulaires et un autre pour adapter en python le modèle SIR. Dans les deux cas, nous obtenons un graphique composé de plusieurs courbes décrivant l'évolution de l'état de la population. Ainsi cela offre des perspectives d'analyse de notre simulation et de sa précision par rapport à un modèle mathématique fiable.

## **Représentation visuelle**

### <span style='font-size:large'>Représentation des automates cellulaires</span>

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

### <span style='font-size:large'>Représentation graphique</span>

Ainsi, que ce soit dans le cas de la représentation de la diffusion du virus par automate cellulaire ou par le modèle SIR, nous avons deux graphiques différents. Nous avons pour cela employé la bibliothèque matplotlib pour étudier sous forme graphique l'évolution de l'état des personnes de la population et en fonction des paramètres définis comme le taux de propagation ou l'indicateur de rétablissement.

La courbe bleue représente l'évolution du nombre de personnes saines au fur et à mesure du temps.

La courbe orange indique elle l'évolution du nombre de personnes infectées.

Enfin, la courbe verte représente elle l'évolution du nombre de personnes rétablies, donc après avoir été infectées.

Ces courbes peuvent énormément varier en fonction du paramétrage qu'on fait  mais restent tout de même la plupart du temps proportionnelles entre elles.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/3.png"   width="371px"  height="287px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/4.png"   width="383.5px"  height="284.496px"  style="object-fit:cover"/>


## **Théorie, présentation du modèle S.I.R.**

Le modèle SIR est une méthode mathématique utilisée en épidémiologie pour simuler la propagation des maladies infectieuses au sein d'une population.

Ce modèle définit une représentation d'une population N pouvant être classée en 3 catégories, sain \(S\), infecté \(I\), rétabli \(R\). Les personnes saines peuvent devenir infectées, et les personnes infectées peuvent devenir rétablies.

Ces changements d'états sont définis par deux paramètres : β  qui implique la probabilité de passer de l'état sain à infecté d'une personne qui est entrée en contact avec une autre déjà infectée et λ qui représente la probabilité de passer de l'état infecté à rétabli en moyenne.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/5.png"   width="457px"  height="110px"  style="object-fit:cover"/>

Pour formuler mathématiquement les dynamiques de ce modèle, il faut utiliser des formules d'équations différentielles. En l’occurrence, nous nous intéressons ici à trois formules que l'on va représenter par trois courbes dans le but d'avoir une représentation des différents états au fil du temps.

<u>Variation du nombre de personnes saines au fil du temps</u> :

$
\frac{dS}{dt} = - \beta \frac{SI}{N}
$

<u>Variation du nombre de personnes infectés</u> :

$\frac{dI}{dt} = \beta \frac{SI}{N} - \lambda I$

<u>Variation du nombre de personnes rétablies </u>:

$\frac{dR}{dt} = \lambda I$

Avec :

S : Pour le nombre de personnes saines.

I : Pour le nombre de personnes infectées.

R : Pour le nombre de personnes rétablies.

N : Pour la population totale $(S+I+R)$.

β : Le taux de transmission.

λ : Le taux de rétablissement.

Il est donc possible de représenter les trois équations précédentes en trois courbes selon les valeurs définies des paramètres β et λ.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/6.png"   width="473px"  height="317px"  style="object-fit:cover"/>

Le modèle SIR peut également être représenté de manière plus complexe, en effet le premier paramètre que l'on pourrait ajouter serait le taux de mortalité μ qui définit la probabilité pour une personne infectée de mourir.

Ce paramètre est généralement très minime dans une représentation du modèle SIR  car il est souvent peu important dans une épidémie.

Cependant il n'est pas négligeable et peu avoir un impact sur les autres états.

On peut notamment le voir par la courbe de la population totale qui baisse au fil du temps.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/7.png"   width="428px"  height="307px"  style="object-fit:cover"/>

## **Notre modèle de propagation de virus en automates cellulaires**

### Initialisation

Nous avons utilisés la bibliothèque pygame qui nous permet d'afficher la simulation en temps réel dans une fenêtre à part.

Nous démarrons d'ailleurs notre code par quelques déclarations de variables, ainsi qu'une initialisation de notre fenêtre.

Ensuite nous déclarons quelques éléments importants comme notre infecté initial et nos variables de contamination et de décontamination qui vont totalement affecter le déroulé de la simulation, ainsi qu'une matrice que l'on appellera grille qui représente notre fenêtre de simulation et stock l'état de chaque cellule \(0 = sain, 1 = infecté, 2 =  immunisé\).

### Propagation et changements d'état

Ensuite notre fonction 'virusPropagation' s'occupe de parcourir chaque cellules de notre grille et d'en modifier ou non l'état.

Ainsi une cellule infectée aura une chance prédéfinie de contaminer chaque cellule autour d'elle, la contamination étant déterminé en comparant notre variable 'PropagationProb' avec un chiffre aléatoire, le tout en vérifiant si la cellule concernée est bien saine et dans les limites de notre fenêtre de simulation.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/8.png"   width="359.492px"  height="78.4961px"  style="object-fit:cover"/>

Une cellule infectée peut aussi devenir immunisée après un certain temps passé infecté. Pour vérifier si une cellule à passé assez de temps infectée, nous avons une "copie" de notre grille qui elle ne comporte pas les états de nos cellules mais leur temps passé malade. Nous pouvons ainsi vérifier si leur temps de maladie est dépassé, dans ce cas  la cellule devient immunisé, ou sinon on incrémente son compteur.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/9.png"   width="360px"  height="95px"  style="object-fit:cover"/>

Tous les nouveaux états de nos cellules sont stockés dans une grille à part entière dont les valeurs sont affectées à la grille principale en fin de fonction afin de pouvoir enchainer des tours de contamination.

### Fin de programme

Ainsi notre fonction qui gère la propagation tourne dans une boucle 'while running' qui se stop quand le virus disparaît. Dans cette boucle une partie du code nous permet d'enregistrer le compte de chaque état à chaque frame de la simulation afin d'afficher nos résultats sur un plot à la fermeture du programme.

![](https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/10.png)

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/10.5.png"   width="346px"  height="244px"  style="object-fit:cover"/>

Nous avons aussi dans cette boucle une boucle qui parcourt le tableau et qui affiche les couleurs en fonction de l'état de la cellule.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/11.png"   width="514px"  height="182px"  style="object-fit:cover"/>

````
import pygame
import random
import matplotlib.pyplot as plt

running = True

## Parameters
# Displaying
frameDelay = 1
WindowSize = 500
PixelSize = 5
GridSize = WindowSize // PixelSize

# Pygame window initialisation
pygame.init()
window = pygame.display.set_mode((WindowSize, WindowSize))
pygame.display.set_caption("Virus Propagation")

# Colors
White = (255, 255, 255)
Green = (0, 255, 0)
Grey = (125, 125, 125)
Red = (255, 0, 0)

# Grid definition
grid = [[0 for i in range(GridSize)] for i in range(GridSize)]
contaminedTime = [[0 for i in range(GridSize)] for i in range(GridSize)]

# First infected définition in the middle of the grid
initialInfected = (GridSize // 2, GridSize // 2)
grid[initialInfected[0]][initialInfected[1]] = 1

# Probability
PropagationProb = 0.5
contaminationTime = 14
deathProbability = 0.001


#Propagation
def virusPropagation():
    global grid
    nextGrid = [[0 for i in range(GridSize)] for i in range(GridSize)]
    for x in range(GridSize):
        for y in range(GridSize):
            #Infected cells treatment
            if grid[x][y] == 1:
                if contaminedTime[x][y] >= contaminationTime:
                    if random.random() < deathProbability:
                        nextGrid[x][y] = 3
                    else:
                        nextGrid[x][y] = 2
                else:
                    nextGrid[x][y] = 1
                    contaminedTime[x][y] += 1
                for diffX in range(-1, 2):
                    for diffY in range(-1, 2):
                        if 0 <= x + diffX < GridSize and 0 <= y + diffY < GridSize:
                            if grid[x + diffX][y + diffY] == 0:
                                if random.random() < PropagationProb:
                                    nextGrid[x + diffX][y + diffY] = 1
            if grid[x][y] == 2:
                nextGrid[x][y] = 2
            if grid[x][y] == 3:
                nextGrid[x][y] = 3
    grid = nextGrid


def endVerification():
    infectedCount = 0
    for x in range(GridSize):
        for y in range(GridSize):
            if grid[x][y] == 1:
                infectedCount += 1
    if infectedCount == 0:
        return False


sainCountTotal = []
infectedCountTotal = []
imunisedCountTotal = []
while running:
    for event in pygame.event.get():
        endVerification()
        run = endVerification()
        if event.type == pygame.QUIT or run == False:
            running = False

    virusPropagation()

    sainCount = 0
    infectedCount = 0
    imunisedCount = 0

    for x in range(GridSize):
        for y in range(GridSize):
            if grid[x][y] == 0:
                sainCount += 1
            if grid[x][y] == 1:
                infectedCount += 1
            if grid[x][y] == 2:
                imunisedCount += 1
    sainCountTotal.append(sainCount)
    infectedCountTotal.append(infectedCount)
    imunisedCountTotal.append(imunisedCount)

    # Display
    window.fill(White)
    for x in range(GridSize):
        for y in range(GridSize):
            if grid[x][y] == 1:
                color = Green
            elif grid[x][y] == 2:
                color = Grey
            elif grid[x][y] == 3:
                color = Red
            else:
                color = White
            pygame.draw.rect(
                window, color,
                (x * PixelSize, y * PixelSize, PixelSize, PixelSize))

    pygame.display.flip()
    pygame.time.delay(frameDelay)

# Display the results
print("Stats :")
print(sainCountTotal)
print(infectedCountTotal)
print(imunisedCountTotal)
x = range(0, len(sainCountTotal))
plt.plot(x, sainCountTotal, label='Sain')
plt.plot(x, infectedCountTotal, label='Infecté')
plt.plot(x, imunisedCountTotal, label='Immunisé')
plt.xlabel('Temps')
plt.ylabel('Population')
plt.title('Simulation de propagation de virus')
plt.legend()
plt.show()

pygame.quit()

````

## <span style='font-size:x-large'>**Notre reproduction du modèle SIR**</span> 

Ce code est donc une adaptation du modèle mathématique SIR, le but est donc de reproduire les différentes courbes qui représentent l'évolution des états de la population.

### <span style='font-size:large'>Initialisation</span>

Ainsi dans ce code, on va dans un premier temps initialiser les paramètres du modèle SIR en prenant en compte la population totale\(N\), le nombre initial d'individus infectés, le taux de transmission\(β\), le taux de rétablissement\(λ\) et de mortalité\(μ\).

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/12.png"   width="280px"  height="217px"  style="object-fit:cover"/>

### <span style='font-size:large'>Simulation du modèle SIR</span>

Pour la simulation du SIR, on va donc définir un nombre de jours pour la durée d'expérience. En effet, contrairement aux automates cellulaires qui s'arrêtent quand la grille est pleine, on doit ici définir une limite qui va constituer notre nombre d'itérations.

On applique donc les équations qui constituent les variations des états de la population et les listes de données sont actualisées à chaque boucle.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/13.png"   width="796px"  height="150px"  style="object-fit:cover"/>

### <span style='font-size:large'>Affichage du résultat graphique</span>

Enfin, on peut visualiser les courbes et afficher les résultats de la simulation par rapport aux paramètres qu'on a défini.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/14.png"   width="369px"  height="172px"  style="object-fit:cover"/>

````
import matplotlib.pyplot as plt

# SIR parameters
totalPopulation = 10000  # N
initialInfectious = 1
propagationRate = 0.3  # β
recoveryRate = 0.05  # λ
mortalityRate = 0.001  # μ


# Lists for each condition
sain = [totalPopulation - initialInfectious]
infectious = [initialInfectious]
recovered = [0]
dead = [0]
actualPopulation = [totalPopulation]

# SIR simulation
for i in range(1, 100):
    sainVariation = -propagationRate * sain[-1] * infectious[-1] / totalPopulation
    infectiousVariation = propagationRate * sain[-1] * infectious[-1] / totalPopulation - recoveryRate * infectious[-1] - mortalityRate * infectious[-1]
    recoveryVariation = recoveryRate * infectious[-1]

    sain.append(sain[-1] + sainVariation)
    infectious.append(infectious[-1] + infectiousVariation)
    recovered.append(recovered[-1] + recoveryVariation)

    actualPopulation.append(sain[-1] + infectious[-1] + recovered[-1] - dead[-1])

# Display the results
days = range(100)
plt.plot(days, sain, label='Sains')
plt.plot(days, infectious, label='Infectés')
plt.plot(days, recovered, label='Rétablis')
plt.plot(days, actualPopulation, label='Population totale')
plt.xlabel('Jours')
plt.ylabel('Population')
plt.title('Simulation du modèle SIR ')
plt.legend()
plt.show()

````

## <span style='font-size:x-large'>**Analyse et interprétation des résultats**</span> 

### <span style='font-size:large'>Analyse de modélisation du SIR</span>

La reproduction du modèle SIR en python nous permet donc de comprendre et analyser les mécanismes fondamentaux de la propagation virale au sein d'une population.

En effet, en étudiant les courbes on peut s'intéresser à l'impact de chaque paramètre.

Par exemple on peut s'intéresser au taux de transmission \(β\), on défini des paramètres constants N = 10 000, nombre d'infecté initial = 1, λ = 0.1, μ = 0.001 .

On va réaliser trois graphiques en changeant uniquement le paramètre β  avec β  = 0.3, β  = 0.5, β  = 0.8.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/15.png"   width="382px"  height="299px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/16.png"   width="384.5px"  height="296.484px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/17.png"   width="391.496px"  height="297.492px"  style="object-fit:cover"/>

On voit donc que le paramètre β qui défini le taux de transmission du virus a une importance cruciale sur le graphique. Tout d'abord il influence naturellement l'ampleur de la transmission du virus, ce qui est logique. Cependant, on remarque également un impact plus global notamment dans la rapidité de variation des courbes.

On peut également s'intéresser au deuxième paramètre central du modèle SIR qui est le taux de rétablissement λ.

On va à nouveau réaliser trois graphiques en modifiant uniquement ce paramètre pour observer son impact avec λ = 0.1, λ = 0.2, λ = 0.3 et en gardant N = 10 000, nombre d'infecté initial = 1, β  = 0.5, μ = 0.001.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/18.png"   width="378px"  height="292px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/19.png"   width="371px"  height="292px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/20.png"   width="380.492px"  height="289.492px"  style="object-fit:cover"/>

On remarque que ce paramètre a lui aussi un impact majeur sur l'évolution des courbes dans le graphique. En effet, plus on l'augmente moins le pic de personnes infectées est élevé, ce qui implique donc que moins de personnes seront touchées par le virus puisque la maladie a une durée de propagation plus courte. En d'autres termes, une augmentation du taux de guérison \(λ\) contribue fortement à une diminution de l'intensité de l'épidémie, ce qui réduit donc la proportion de la population totale qui est infectée. 

Cela souligne l'importance du taux de guérison dans la gestion et la modération de la propagation d'un virus au sein d'une population qui peut être par exemple amélioré avec des vaccins ou des confinements.

### <span style='font-size:large'>Comparaison du modèle d'automates cellulaires et du modèle SIR</span>

Les deux codes que nous avons réalisés proposent donc tous les deux une simulation de propagation d'un virus au sein d'une population. Pourtant on peut y observer des différences dans la réalisation notamment car l'un est implémenté avec des automates cellulaires et l'autre un modèle mathématique.

En effet bien que le résultat soit plus ou moins similaire, il y a une différence dans la réalisation puisque l'un est basé sur des formules mathématiques et l'autre sur des boucles et des probabilités. Ainsi même si on remarque que les deux ont deux paramètres principaux pour déterminer le taux de propagation et le taux de rétablissements, ils ne sont pas pour autant similaires car pas utilisés de la même manière. Cela signifie qu'à  valeur égale, le résultat sur l'affichage graphique sera différent d'autant plus que le paramètre λ est calculé en nombre de jours dans le modèle avec automates cellulaires et dans le modèle du SIR il correspond à un coefficient.

Ainsi, bien que les deux codes soient différents, on retrouve un résultat graphique globalement similaire. La seule différence notable entre les deux graphiques se situe dans le fait que les courbes qui résultent des automates cellulaires ne sont pas aussi "constantes" que sur l'autre modèle. En effet, si on regarde la courbe orange représentant la proportion de la population infectée, dans le premier graphique la courbe augmente de manière presque linéaire avant d'atteindre son pic tandis que l'autre a une montée plus exponentielle et cela dans la plupart des cas.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/21.png"   width="364px"  height="278px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/22.png"   width="361.469px"  height="271.5px"  style="object-fit:cover"/>

Ce phénomène s'explique par le fait qu'il existe une fonction exponentielle définie par le modèle SIR. En effet, lorsqu'on s'intéresse à cette courbe des personnes infectées en orange représenté par l'équation $\frac{dI}{dt} = \beta \frac{SI}{N} - \lambda I$.

On considère que N ≈ S car il n'y a qu'un seul infecté au départ, on a donc $\frac{SI}{N}$≈I.

Notre équation différentielle devient donc :  $\frac{dI}{dt} =$ βI−λI qui peut se factoriser en  $\frac{dI}{dt} =$ \(β−λ\)I.

On a donc maintenant une équation différentielle linéaire du premier ordre de la forme I\(t\) = I0 e\(β−λ\)t 

Ainsi on peut expliquer pourquoi la courbe de croissance des personnes infectées semble suivre une tendance exponentielle en fonction du temps avant d'atteindre son pic.


## <span style='font-size:x-large'>**Problèmes et incohérences**</span> 

Notre modèle de simulation de propagation de virus se base sur des automates cellulaires, et de ce fait nous n'avons pas pu obtenir des résultats semblables sur la courbe de la propagation avec le modèle SIR.

Cela s'explique par le nombre limité de contacts entre une cellule et ses voisins.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/23.png"   width="312px"  height="214px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/24.png"   width="320px"  height="216px"  style="object-fit:cover"/>

Nous ne pouvons pas non plus obtenir une maladie avec des cellules qui ne sont jamais infectées sans obtenir une propagation ridiculement trop lente.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/25.png"   width="252.496px"  height="271.488px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/26.png"   width="392.484px"  height="270.496px"  style="object-fit:cover"/>

Ainsi en baissant beaucoup le taux de propagation ainsi que la durée de la maladie, nous obtenons des cellules qui ne tombent pas malades et restent saines tout le long de la simulation, mais comme on peut le voir sur le graphique la  propagation se fait très lentement, ce qui ne correspond pas à la plupart des maladies. Mais une maladie contaminant 100% de la population n'a pas beaucoup plus de sens.

<img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/27.png"   width="248.496px"  height="267.488px"  style="object-fit:cover"/><img src="https://raw.githubusercontent.com/LucasLeiner/imagesRenduMaths/main/28.png"   width="381.484px"  height="263.496px"  style="object-fit:cover"/>


## <span style='font-size:x-large'>**Sources**</span> 

[https://deptinfo\-ensip.univ\-poitiers.fr/ENS/doku/doku.php/tp:python:epidemie](https://deptinfo-ensip.univ-poitiers.fr/ENS/doku/doku.php/tp:python:epidemie) 

[https://interstices.info/modeliser\-la\-propagation\-dune\-epidemie/](https://interstices.info/modeliser-la-propagation-dune-epidemie/) 

[https://images.math.cnrs.fr/Modelisation\-d\-une\-epidemie\-partie\-1.html](https://images.math.cnrs.fr/Modelisation-d-une-epidemie-partie-1.html) 

[https://nextjournal.com/essicolo/le\-modèle\-sir](https://nextjournal.com/essicolo/le-mod%C3%A8le-sir) 

