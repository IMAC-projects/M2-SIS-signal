# Filtre

> Un filtre est un système. Le filtrage correspond à sélectionner certaines fréquences du signal.

## Sommaire
 
[**Introduction**](#Introduction)

[**Définitions**](#Définitions)

[**Filtre passe-haut**](#Filtre-passe-haut)

[**Filtre passe-bas**](#Filtre-passe-bas)

[**Filtre passe-bande**](#Filtre-passe-bande)

[**Filtre coupe-bande**](#Filtre-coupe-bande)

[**Filtrage analogique**](#Filtrage-analogique)
 - [**Dirac**](#Dirac)
 - [**Réponse impulsionnelle**](#Réponse-impulsionnelle)
 - [**Causalité**](#Causalité)
 - [**Gain et phase**](#Gain-et-phase)
 - [**Fonction de transfert**](#Fonction-de-transfert)

[**Filtrage numérique**](#Filtrage-numérique)
 - [**Transformée en Z**](#Transformée-en-Z)
 - [**Causalité**](#Causalité)


## Introduction

On parle de filtrage de signal lorsqu'on atténue (la suppression est difficile) ou favorise dans un signal des fréquences par rapport à d'autres.

En général, on recense 4 types de filtres :
-   Le filtre passe-haut qui laisse passer les fréquences hautes
-  Le filtre passe-bas qui laisse passer les fréquences basses
-   Le filtre passe-bande qui laisse passer une bande de fréquence
-   Le filtre coupe-bande qui supprime une bande de fréquence

<img src="http://www.siloged.fr/cours/html/ssi_filtrage/lib/gabarit.png"  
alt="schéma filtres" style="text-align:center;"/>


De nombreux systèmes physiques peuvent être schématisés du point de vue de la théorie du signal par le lien entre le signal d’entrée $e$ et le signal de sortie $s$.

<img src="https://i.ibb.co/BzfTXmW/Capture-d-cran-2020-10-26-221553.png"  
alt="schéma filtres" style="text-align:center;"/>

Cette correspondance entre l’entrée et la sortie est notée $s = H(e)$.

## Définitions 

### **<font color=red>Amplification</font>**
L'amplification d'un signal consiste à augmenter une ou certaine de ses grandeurs électriques :
-   le courant : amplification de courant
-   la tension : amplification de tension
-   la puissance : amplification de puissance

L'amplification de puissance étant à la fois une amplification de courant et de tension.

Une opération d'amplification est donc une opération de multiplication par une constante supérieure à 1.

### **<font color=red>Saturation</font>**

Les structures de traitement des signaux analogiques sont réalisées avec des amplificateurs. Ces derniers ne peuvent restituer, au maximum que la tension maximum qui les alimente.
Si théoriquement ils doivent restituer plus, la tension de sortie ne dépassera pas cette tension d'alimentation. On dit qu'ils saturent.

### **<font color=red>Octave</font>**
Une octave est un rapport de deux entre deux fréquences.
Par exemple un LA2 de fréquence 440Hz est une octave en dessous d'un LA3 de 880Hz.
Pour changer de son à l'octave, on double par exemple la longueur d'une flûte

### **<font color=red>Décade</font>**
Une décade est un rapport de 10 entre deux fréquences. Généralement, pour des grandeurs évoluant par décade, on utilise une échelle logarithmique (logarithme décimal) de sorte que les phénomènes soient plus visibles.

### **<font color=red>Gain</font>**

Plutôt que de parler de coefficient d'amplification, on préfère parler de gain.
Le gain désigne la capacité d'une structure à augmenter ou diminuer la puissance ou l'amplitude d'un signal. Si le gain est positif, la structure amplifie le signal, si le gain est négatif, la structure atténue le signal.

L'unité du gain est le décibel noté $dB$.

### **<font color=red>Fréquence de coupure</font>**

La fréquence de coupure spécifie une fréquence particulière à laquelle le signal est atténué de $-3dB$ (ou subit une atténuation de $\frac{1}{\sqrt{2}}$ par rapport à l'amplitude maximale.
Selon la position de cette fréquence par rapport à la courbe de fréquence on parle de fréquence de coupure basse ou de fréquence de coupure haute.

### **<font color=red>Bande passante</font>**

C'est la différence entre la fréquence de coupure haute et la fréquence de coupure basse. Les deux fréquences sont prises pour une atténuation par rapport au maximum de $\frac{1}{\sqrt{2}}$.

## Filtre passe-haut

Un filtre passe-haut laisse passer les fréquences hautes et atténue les fréquences basses.

## Filtre passe-bas

Un filtre passe-bas laisse passer les fréquences entre 0Hz et la fréquence de coupure $f_c$. Au-delà de $f_c$, les fréquences sont atténuées.

**Exemple du filtre passe-bas :**

$$s_{[0,1]^2 \to \mathbb{R}} \sim\hat{s} * \Pi_{[-Bc,Bc]}$$

$TF^-1(\hat{s} * \Pi_{[-Bc,Bc]^2})$ est le signal filtré passe-bas.

**<font color="red">Remarque</font> :**  Quel est le coût de la convolution discrète ? $\to$ à priori, $N^2$

En fait, pour calculer la convolution, on peut utiliser la **FFT**.

$$s \ast h = FFT^{-1}(FFT(s) .FFT(h))$$

On fait passer une convolution sur le signal pour sélectionner un contenu fréquentiel.

## Filtre passe-bande

Un filtre passe-bande est un filtre ne laissant passer qu’une bande ou intervalle de fréquences compris entre une fréquence de coupure basse et une fréquence de coupure haute du filtre. Il cumule le fonctionnement du filtre passe-bas et du filtre passe-haut.

## Filtre coupe-bande

Un filtre coupe-bande aussi appelé filtre réjecteur de bande est un filtre empêchant le passage d'un intervalle de fréquences. Il est composé d'un filtre passe-haut et d'un filtre passe-bas dont les fréquences de coupure sont souvent proches mais différentes, la fréquence de coupure du filtre passe-bas est systématiquement inférieure à la fréquence de coupure du filtre passe-haut.
