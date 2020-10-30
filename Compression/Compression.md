# Compression

La **compression de données** est l'opération consistant à **transformer** une donnée A en une autres B pouvant **restituer** les mêmes informations, ou des informations *"proches"*, en utilisant un algorithme de *décompression*.

C'est une opération dite de **codage** qui change la représentation des données visant à en **diminuer** la taille (de stockage) de celles-ci au prix d'un travail de compression (et de décompression pour la restitution des données).

## Sommaire

- [**Types de compression**](#Types de compression)
- [**Taux de compression**](#Taux de compression)
- [**Entropie de Shannon**](#Entropie de Shannon)
- [**Codage de Huffman**](#Codage de Huffman)

## Types de compression

 Il existe deux types de compression de données:

- La **sans perte** restituant après décompression un signal (données) strictement identique à l'original avant compression. 
  On peux exploiter par exemple la redondance des données ou des a priori sur la source de données.
  (**Codage RLE,** **codage de Huffman**, **codage LZW** ...)

- A l'inverse, la **avec perte** restituant un signal différent mais relativement *"proche"* du signal d'origine mais permet une compression plus importante. 
  On considère généralement la différence entre les deux signaux comme négligeable (non perceptibles) et étant une perte acceptable dans certains cas pour que la source de données reste compréhensible/perceptible.
   On peux par exemple exploiter la perception humaine pour définir l'information négligeable (comme les hautes fréquences d'une image par exemple).

  (**sous échantillonnage**, **Codage par DTC**, **codage par ondelettes** ...)



## Taux de compression

Le taux de compression que l'on peut noté $\tau$ est relié au rapport entre la taille $b$ du fichier compressé $B$ et la taille $a$ du fichier original $A$. Le taux de compression est généralement exprimé en pourcentage et est défini par :
$$
\tau = 1 - (b/a)
$$
**Exemple :** $a$ = 550 Mo,  $b$=250 Mo , $\tau = 1 - (250/550) = 54\%$

L'algorithme utilisé cherche généralement à obtenir un taux de compression inférieur à 1.

## Entropie de Shannon

L'**entropie de Shannon**, crée par Claude Shannon, est une fonction mathématique qui permet de quantifié la quantité d'information contenue par une source d'information. Cette source peut être un texte écrit dans une langue donnée, un signal électrique ou encore un fichier informatique quelconque.

Autrement dit, l'entropie de Shannon indique la **quantité d'information nécessaire** pour que l'on puisse déterminer sans ambiguïté ce que l'on perçois d'une source de données. 
En particulier, plus la source est redondante, moins elle contient d'information. Par exemple, si une source envoie toujours le même symbole, par exemple la lettre 'a', alors son entropie est *nulle*, c'est-à-dire minimale, car l'on peut identifié sans aucune connaissances et sans ambiguïté le prochains symbole émis par la source. En l'absence de contraintes particulières, l'entropie est maximale pour une source dont tous les symboles sont équiprobables.

### Définition

Pour une source, qui est une variable aléatoire discrète $X$ comportant $N$ symboles distincts, chaque symbole $x_i$ ayant une probabilité $P_i$ d'apparaître. Les symboles représentent les réalisations possibles de la variable aléatoire $X$.
L'**entropie** $H$ de la source $X$ est définie comme :
$$
H_b(X) = -\mathbb{E}[log_b(P(X))] = -\sum_{i=1}^N P_i.log_b(P_i)
$$
Où $\mathbb{E}$ désigne l'espérance mathématique, et $log_b$ le logarithme en base *b*. 
On utilise en général un logarithme à base 2 car l'entropie s'exprime alors en nombre de bits par symbole. Dans ce cas, on peut interpréter $H(X)$ comme le nombre de questions à réponse binaire que l'on doit poser en moyenne à la source, ou la quantité d'information en bits que la source doit fournir au récepteur pour que ce dernier puisse déterminer sans ambiguïté la valeur de $X$.

$$
H(X) = H_2(X) = -\sum_{i=1}^N P_i.log_2(P_i)
$$

### Interprétation

Dans le cas où l'on dispose d'un nombre $N$ de symboles de la forme $N= 2^n$ avec $n$ entier, et où les $N$ symboles sont équiprobables, il suffit de $n$ questions, en procédant par dichotomie, pour déterminer le symbole envoyé par la source. Dans ce cas, la quantité d'information contenue par le symbole est exactement $n = log_2(N)$.
$$
\begin{align}
H(X) =& -\sum_{i=1}^N P_i.log_2(P_i) \\
	 =& -\sum_{i=1}^N \frac{1}{N}.log_2(\frac{1}{N}) \\
	 =& -\frac{1}{N} \sum_{i=1}^N log_2(\frac{1}{N}) \\
	 =& -\frac{1}{N} * N.log_2(\frac{1}{2^n}) \\
	 =&\quad log_2(2^n) = n\\
\end{align}
$$
De manière plus générale, il est naturel de conserver cette formule dans le cas où $N$ n'est pas une puissance de 2. Par exemple, si les symboles sont les lettres de l'alphabet et que l'on les considères toutes équiprobables, alors l'information contenue par un symbole est $log_2(26) \approx 4.7$ .
Cette valeur est une valeurs intermédiaire entre 4 bits (permettant de coder 16 symboles) et 5 bits (qui permet d'en coder 32).

### Exemple

Considérons une urne contenant des boules de 4 couleurs différentes: rouge, bleue, jaune et vert, toutes équiprobables.
On tire une boule au hasard et il s'agit d'en identifier la couleur. Comme aucun tirage n'est privilégié, l'entropie est ici maximale égale à  $log_2(4)=2$. 
Si on convient que les couleurs sont codées respectivement $00$, $01$, $10$, $11$, l'information contenue dans le tirage correspond effectivement à 2 bits.

Mais si une certaine couleur est plus représentée que les autres, alors l'entropie est légèrement réduite. Supposons par exemple que l'urne contienne 4 boules rouges, 2 bleues, 1 jaune et 1 verte. 

On peux calculer l'entropie de la manière suivante:
$$
\begin{align}
H(X) =& -\sum_{i=1}^N P_i.log_2(P_i) \\
	 =& -\left( \frac{4}{8}.log_2(\frac{4}{8}) + \frac{2}{8}.log_2(\frac{2}{8}) + \frac{1}{8}.log_2(\frac{2}{8}) + \frac{2}{8}.log_2(\frac{1}{8})\right) \\
	 =& -\left( \frac{log_2(\frac{1}{2})}{2} + \frac{log_2(\frac{1}{4})}{4} + \frac{log_2(\frac{1}{8})}{8} + \frac{log_2(\frac{1}{8})}{8}\right) \\
	 =& \quad \frac{log_2(2)}{2} + \frac{log_2(4)}{4} + \frac{log_2(8)}{8} + \frac{log_2(8)}{8} \\
	 =& \quad \frac{1}{2} + \frac{2}{4} + \frac{3}{8} + \frac{3}{8} \\
	 =& \quad \frac{7}{4} = 1.75
\end{align}
$$
Si les couleurs sont codées respectivement $0$ pour le rouge, $10$ pour le bleu, $110$ pour le jaune et $111$ pour le vert, alors l'information sur la couleur tirée occupe 1 bit une fois sur deux, 2 bits une fois sur quatre et 3 bits une fois sur quatre, soit en moyenne 7/4 bits, correspondant à l'entropie calculée.

## Codage de Huffman

Le **codage de Huffman** est un algorithme de compression de données **sans perte**. Il consiste à utiliser un code à longueur variable pour représenter un symbole d'une source de données en ayant une connaissance préalable (ou une estimation) des probabilités d'apparition des symboles de cette source. Un code court étant associé aux symboles les plus fréquents.

Un code de Huffman est optimal au sens de la plus courte longueur pour un codage par symbole, et une distribution de probabilité connue. Des méthodes plus complexes réalisant une modélisation probabiliste de la source permettent d'obtenir de meilleurs ratios de compression.

### Principe

> TODO: arbre, code préfixe (contre exemple code pas préfixe avec plusieurs interprétations possibles)

### Inégalité de Kraft

### Limitations du codage de Huffman

> TODO : définir longueur moyenne, bornes par entropie 

## Codage RLE

> TODO

## Cas du JPEG

> TODO

### Transformation : espace de couleurs

### Sous-échantillonnage de la chrominance

### Passage en fréquence : Transformation en cosinus discrètes

### Quantification

### Encodage - codage RLE et codage de Huffman