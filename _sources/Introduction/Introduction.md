
# Introduction

> Introduction au cours de représentation et filtrage numérique 1D/2D du M2 Informatique - Sciences de l'image effectué à l'Université Gustave Eiffel. La retranscription est effectuée majoritairement par [Enguerrand De Smet](https://github.com/dsmtE) et [Laurine Lafontaine](https://github.com/LafLaurine).

## Sommaire

[**Introduction au signal**](#Introduction-au-signal)

[**Décomposition signal dans une base**](#Décomposition-signal-dans-une-base)

[**Projection orthogonale**](#Projection-orthogonale)

## Introduction au signal

Un signal est une représentation physique d'une information qui se propage le long d'un support entre l'émission et la réception. On se demande à chaque fois quelle est la nature de l'information transportée (audio, sonore, visuelle).
Toute information est susceptible d'être codée en émission et décodée en réception. 

Pour étudier un signal et apporter les traitements nécessaires, on peut se baser sur sa représentation graphique et mathématique.

## Décomposition signal dans une base

**<font color=red>Échantillonnage </font>** : signal analogique vers numérique

**<font color=red>Interpolation </font>** : signal numérique vers analogique

Décomposition en signaux élémentaire : 
* dans un espace Euclidien ($\mathbb{R}$)
* $\forall$ vecteur $f$. $f = (f_1, ..., f_n) = \sum_{i=1}^{n} (f_{i}\times e_{i})$
* une image peut donc s'écrire :

$$ 
I = \sum_{i,j}^{} I(i,j)e_{ij}
\\ avec \ e_{i,j}(k,l) = 1 \ \text{si} \ k = i \ et \ l = j
\\ 0 \ sinon 
$$

**<font color=red>Approximation linéaire </font>** : </br> 
Chercher des coefficients $\lambda_i$ tq 

$$ 
f \approx \sum_{i=1}^{p} \lambda_i \nu_i 
\\ avec \ (\nu_1, ..., \nu_p) \ des \ vecteurs \ d'intérêt 
$$

On considère un cas particulier : la famille $(\nu_1, ..., \nu_p)$ est **orthonormée**.

**Rappel** :

* $\lVert \nu_{i} \rVert = 1 \to$ normée
* $<v_i, v_j> = 0 \ si \ i \neq j \to$ orthogonalité
* $\lVert f \rVert = \sqrt{<f,f>}$
* $\lVert f + g \rVert \leq  \lVert f \rVert +  \lVert g \rVert$

**Remarque** :

Sur $\mathbb{R}^n$, le produit scalaire (canonique) : $<x,y> = \sum_{i=1}^{n} x_i y_i$

$$ 
f = \sum_{i=1}^{p} <f, \nu_i> \nu_i + \ reste 
$$

## Projection orthogonale

On considère $<f,g> = \sum_{i=1}^{n}f_i g_i$, produit scalaire sur $\mathbb{R}^n$

**<font color=red>Propriétés </font>** : 
* $<f + \lambda g, h> = <f,h> + \lambda <g,h>, \lambda \in \mathbb{R}$
* $<f,f> \geqslant 0$
* $<f,f> = 0 \Leftrightarrow f = 0$
* $<f,g> = <g,f>$

Sur les signaux continus :

$$ 
f,g : [0,1]^2 \to \mathbb{R} 
\\ <f,g> = \int_{\mathbb{}}^{}\int_{\mathbb{[0,1]^2}}^{} f(x) g(x) \ dx 
$$

Sur les signaux discrets :

$$ 
f,g \in \mathbb{R}^n
\\ <f,g> = \frac{1}{N} \sum_{i=1}^{N}f_i g_i 
$$

On peut résumer un signal en coefficients associé à une fonction d'évaluation. On utilise pour cela la décomposition de Fourier et on garde les coefficients significatifs. Pour un signal discontinu, on aura besoin de plus de coefficients.

L'effet de bord est appelé **phénomène de Gibbs**.
