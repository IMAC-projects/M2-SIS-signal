# Transformée de Fourier

> La transformée de Fourier est une opération qui transforme une fonction intégrable sur $\mathbb{R}$ en une autre fonction.

## Sommaire

[**Signaux continus en 1D**](#Signaux-continus-en-1D)

[**Propriétés de la TF**](#Propriétés-de-la-TF)

[**Convolution**](#Convolution)

[**Inverse de la TF**](#Inverse-de-la-TF)

[**TF et dérivation**](#TF-et-dérivation)

[**Égalité de Parseval**](#Égalité-de-Parseval)

[**Transformation de Fourier en 2D**](#Transformation-de-Fourier-en-2D)

[**Calcul de la TF du signal porte**](#Calcul-de-la-TF-du-signal-porte)

[**Introduction aux distributions : masse de Dirac**](#Introduction-aux-distributions-:-masse-de-Dirac)

[**Dirac et convolution**](#Dirac-et-convolution)

[**Échantillonnage et théorème de Shannon**](#Échantillonnage-et-théorème-de-Shannon)

[**Formule sommatoire de Poisson**](#Formule-sommatoire-de-Poisson)

[**Peigne de Dirac**](#Peigne-de-Dirac)

## Signaux continus en 1D

Deux espaces : 

* $L^1(\mathbb{R}) = \left\{  f: \mathbb{R} -> \mathbb{R}; \ \int_{\mathbb{R}}^{} | f(x) | \ dx < + \infty \right\}$
* $L^2(\mathbb{R}, \mathbb{C}) = \left\{  f: \mathbb{R} -> \mathbb{C}; \ \int_{\mathbb{R}}^{} | f(x) |^2 \ dx < + \infty \right\}$

$L^2$ correspond à **l'énergie finie**

On défini sur l'espace des signaux d'énergie finie $L^2$ le **<font color=red>produit scalaire hermitien </font>** suivant :

$$ <f,g> = \int_{\mathbb{R}} f(x)\overline{g(x)} dx $$

Où $\overline{a}$ le complexe conjugué de a $\in \mathbb{C}$.

$\left\{  \begin{array}{ll} a = a_{1} + ia_{2} \\ 
\overline{a} = a_1 - ia_2 \end{array} \right.$

**<font color=red>Attention</font>** : On a bien $\int_{\mathbb{R}} f(x)\overline{f}(x)dx = \int_{\mathbb{R}} f(x)|^2dx \leq 0$ et nul ssi $f = 0$

Quelques propriétés sur ce produit scalaire : 
* **Symétrie hermitienne** : $<f,g> = \overline{<g,f>}$

* **Linéarité à gauche** : $<f+ \lambda h, g> \ = \ <f,g> + \lambda <h,g>$

* **Semi-linéarité à droite** : $<f,g + \lambda h> \ = \ <f,g> + \overline{\lambda} <f,h>$

  >Remarque : on appelle une telle application une forme **sesquilinéaire hermitienne** (à droite)

$$ \\ $$

**<font color=red>Définition</font>** : 

Soit $f \in L^1(\mathbb{R})$. et $\omega \in \mathbb{R}$
La transformée de Fourier de $f$ est définie par :

$$ TF(f)(\omega) = \hat{f}(\omega) = \int_{\mathbb{R}} f(t) e^{-2i\pi\omega t}dt $$

Ici, on passe du domaine **temporel** au domaine **fréquentiel**.

En posant  la notation $e_\omega = e^{2i\pi\omega t}$, on retrouve alors la forme suivante exprimée avec le produit scalaire précédemment défini :

$$ 
\begin{align}
\hat{f}(\omega) =& <f, e_\omega> \\
=& \int_{\mathbb{R}} f(t) \overline{e^{2i\pi\omega t}}dt \\
=& \int_{\mathbb{R}} f(t) e^{-2i\pi\omega t}dt
\end{align} 
$$

> *Pourquoi retrouve-t-on le signe $-$ devant $2i\pi \omega t$ ?* 
> La transformée de Fourier utilise le produit scalaire $<f,e_\omega>$, dans lequel on utilise le **conjugué**.

**<font color=red>Remarque</font>** : $L^1(\mathbb{R})$ contient des fonctions discontinues mais on a une condition d'intégrabilité.

$TF(f)(\omega)$ est bien définie car 

$$ | < f,e_{\omega} > | \leq \int_{\mathbb{R}}^{} | f(x) e^{-2i\pi \omega x} | \ dx =  \int_{\mathbb{R}}^{}  | f(x) | \ dx \le + \infty $$

donc $\forall \omega \ | \hat{f}(\omega) | \leq \int_{\mathbb{R}}^{} | f(x) | \ dx$ avec $\omega$ la fréquence en $Hz$

## Propriétés de la TF

* **<font color=red>Linéarité </font>**

  Soit $a,b \in \mathbb{R}$  et  $f,g \in L^1(\mathbb{R})$

  $$ TF(af+bg) = \widehat{af+bg} = a\hat{f}+b\hat{g} $$

* **Démonstration** :

  $$ 
  \begin{align}
  TF(af+bg) =& <af+bg, e_\omega> \\
  & {\small\text{(par linéarité du produit scalaire hermitien)}} \\
  =& a<f, e_\omega> + b<g, e_\omega> \\
  =& a\hat{f}+b\hat{g} \quad \\
  \end{align} 
  $$

* **<font color=red>Théorème du retard (translation temporelle) </font>** 

  Soit $t_0 \in \mathbb{R}$ et $f : \mathbb{R} \to \mathbb{C}$. On définit la translation de $f$ par $t_0$ :  $\tau_a(f)(t) \mapsto f(t-t_0)$

  $$ \widehat{\tau_a(f)}(\omega) = e^{-2i\pi \omega t_0} \hat{f}(\omega) $$

**Démonstration** : 

$$ 
\begin{align}
\widehat{\tau_a(f)}(\omega) =& \int_{\mathbb{R}} \tau_a(f)e^{-2i\pi\omega t}dt \\
&{\small \text{On pose} \ t' = t-t_0 \ \text{(changement de variable)}} \\
=& \int_{\mathbb{R}} f(t')e^{-2i\pi\omega (t'+a)} \ dt' \\
=& e^{-2i\pi\omega t_0} \int_{\mathbb{R}} f(t')e^{-2i\pi\omega t'} dt' \\
=& e^{-2i\pi\omega t_0} \hat{f}(\omega)
\end{align} 
$$

- **<font color=red>Modulation ou Translation fréquencielle </font>**

  Soit $\omega_0 \in \mathbb{R}$ et $f:\mathbb{R} \to \mathbb{C}$ On pose la notation suivante : $f_{w_0}(t) \mapsto e^{2i \pi \omega_0 t}f(t)$ 

$$ \widehat{f_{\omega_0}}(\omega) = \tau_{\omega_0}(\hat{f})(\omega) = \hat{f}(\omega-\omega_0) $$

**Démonstration** :

$$ 
\begin{align}
\widehat{f_{\omega_0}} =& \int_{\mathbb{R}} f(t) e^{2i\pi\omega_0 t} e^{-2i\pi \omega t}dt \\
=& \int_{\mathbb{R}} f(t) e^{2i\pi (\omega-\omega_0) t} dt \\
=& \hat{f}(\omega-\omega_0)
\end{align} 
$$

* **<font color=red>Dilatation du temps (changement d'échelle)</font>** 

  Soit $a \in \mathbb{R}$ et $f : \mathbb{R} \to \mathbb{C}$. On définit la dilatation de $f$ par $a$ :  $D_a(f)(t) \mapsto f(at)$

  $$ \widehat{D_a(f)} = \frac{1}{|a|} \hat{f}(\frac{\omega}{a}) $$

**Démonstration** : 

Pour $a \geq 0$ :

$$ 
\begin{align}
\widehat{D_a(f)} =& \int_{\mathbb{R}} f(at) e^{-2i\pi \omega t}dt \\
&{\small \text{On pose} \ t' = at \ \text{(changement de variable)}} \\
=& \int_{\mathbb{R}} f(t') e^{-2i\pi \omega \frac{t'}{a}} \frac{dt'}{a} \\
=& \frac{1}{a} \int_{\mathbb{R}} f(t') e^{-2i\pi \frac{\omega}{a}t'} dt' \\
=& \frac{1}{a} \hat{f}(\frac{\omega}{a})
\end{align}
$$

Pour $a<0$ :

$$ 
\begin{align}
\widehat{D_a(f)} =& \int_{\mathbb{R}} f(at) e^{-2i\pi \omega t}dt \\
&{\small \text{On pose} \ t' = at \ \text{(changement de variable)}} \\
& ⚠{\small \text{: ici le changement de variable inverse les bornes }} \\
=& \int_{+\infty}^{-\infty} f(t') e^{-2i\pi \omega \frac{t'}{a}} \frac{dt'}{a} \\
=& \frac{1}{a}\int_{+\infty}^{-\infty} f(t') e^{-2i\pi \frac{\omega}{a}t'} dt' \\
& {\small \text{par inversion des bornes }} \\
=& -\frac{1}{a} \int_{\mathbb{R}} f(t') e^{-2i\pi \frac{\omega}{a}t'} dt' \\
=& -\frac{1}{a} \hat{f}(\frac{\omega}{a})
\end{align}
$$


- **<font color=red> Passage au conjugué</font>** 

Soit $f : \mathbb{R} \to \mathbb{C}$

$$ \widehat{\overline{f}(\omega)} = \overline{\hat{f}(-\omega)} $$

**Démonstration** : 

$$ 
\begin{align}
\widehat{\overline{f}(\omega)} =& \int_{\mathbb{R}} \overline{f(t)} e^{-2i\pi \omega t}dt \\
=& \int_{\mathbb{R}} \overline{f(t)} \overline{e^{2i\pi \omega t}}dt \\
& {\small \text{par la propriété du conjugué : } \overline{z_1}.\overline{z_2} =  \overline{z_1.z_2}} \\
=& \overline{\int_{\mathbb{R}} f(t) e^{2i\pi \omega t}dt} \\
=& \overline{\int_{\mathbb{R}} f(t) e^{-2i\pi (-\omega) t}dt} \\
=& \overline{\hat{f}(-\omega)}
\end{align}
$$

Si on se donne $\widehat{{f}(\omega)}$ pour $\omega \geq 0$, alors on connaît partout $\widehat{{f}(\omega)}$. La moitié de l'information suffit.

- **<font color=red>La gaussienne (issue de la loi normale)</font>** 

$$ g_{\sigma} = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{x^2}{2\sigma^2}} $$

**Calcul de la TF**
- **<font color=red>Rappel intégration par partie</font>** 

$\int_{a}^{b} F'G \ dt =  \int_{a}^{b}  FG' \ dt = F(b)G(b) - F(a)G(a)$

## Convolution

On définit la **convolution h $\ast$ g** tel que :

$$ (h \ast g)(t) = \int_{\mathbb{R}}^{} h(t-u)g(u) du $$

**Exemple : signal porte**

![signal porte](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Rectangular_function.svg/1200px-Rectangular_function.svg.png)

Dans le cas du signal porte, $\int_{}^{}h \ du = 1$

$$ (h \ast g)(t) = \int_{\mathbb{R}}^{}h(u-t)g(u) \ du $$

Remarque : h(u) est paire, i.e $h(u) = h(-u)$

**<font color=red>Propriétés de la convolution</font> :** 

- Symétrie : $h \ast s = s \ast h$
- $\int_{\mathbb{R}}^{}| f \ast g(t)| \ dt \leq \int_{\mathbb{R}}^{}| f| \ dt \ \int_{\mathbb{R}}^{}|g| \ dt$
- Soit $f,g \in L^2(\mathbb{R})$, on a : 

$$ \widehat{f \ast g}(\omega) = \hat{f}(\omega)\hat{g}(\omega) $$

## Inverse de la TF

On peut inverser la TF.  

$$ (TF)^{-1}(\hat{f})(t) = \int_{\mathbb{R}}^{} \hat{f}(t)e^{2i\pi \omega t}\ dt $$

**<font color=red>Propriété</font> :** 

$\widehat{fg} = \hat{f} * \hat{g}$ car :

- $TF^{-1} TF(fg) = fg$
- $TF^{-1}(f)(\omega) = TF(f)(-\omega)$

## TF et dérivation

Soit $f: \mathbb{R} \to \mathbb{R}$ signal différenciable p fois tq $\forall i f^{(i)} \in L^1(\mathbb{R})$

$$ \widehat{f^{(p)}}(\omega) = (2i\pi \omega)^p\hat{f}(\omega) $$

**Démo :**

Pour p = 1 :

$TF(f') = \int_{\mathbb{R}}^{}e^{-2i \pi \omega t} f'(t) \ dt$

IPP :

$$ 
\begin{align}
=& -\int_{\mathbb{R}}^{}(e^{-2i \pi \omega t)'}f(t) \ dt
=& (2i \pi \omega)\int_{\mathbb{R}}^{} e^{-2i \pi \omega t} f(t) \ dt
\end{align} 
$$

Si le signal est p fois différenciable, $ \widehat{f^{(p)}}(\omega) = (2i \pi \omega)^p \hat{f}(\omega) $

Si  $\widehat{f^{(p)}}(\omega)$ est d'énergie finie, $L^2(\mathbb{R})$ : 

$$ \widehat{f^{(p)}}(\omega) \in L^2 => (2i \pi \omega)^p \hat{f}(\omega) \in L^2 $$

## Égalité de Parseval

La TF préserve l'énergie des signaux. Isométrie de $L^2(\mathbb{R})$

Cela signifie, pour $f : \mathbb{R} \to \mathbb{R}$

$$ \int_{\mathbb{R}}^{}|f(t)|^2  \ dt = \int_{\mathbb{R}}^{} | \hat{f}(\omega)|^2  \ d\omega $$

> L'énergie  totale s'obtient en sommant les contributions des différents harmoniques

## Transformation de Fourier en 2D

On considère $\{f : \mathbb{R}^2 \to \mathbb{C};  \int_{\mathbb{R}^2}^{}|f(x,y)|^2 dxdy < +\infty \}$

On définit la TF :

$$TF(f)(\omega_1 \omega_2) = \int_{\mathbb{R}^2}^{}f(x_1,x_2) e^{-2i \pi(\omega_1 x_1 + \omega_2 x_2)}dx_1 dx_2$$

En dimension n :

$$TF(f)(\omega_1...\omega_n) = \int_{\mathbb{R}^n}^{}f(x_1,...,x_n) e^{-2i \pi(\omega_1 x_1 + ... + \omega_n x_n)}dx_1...dx_n$$

La plupart des propriétés déjà vues en 1D restent vraies en nD.

$$TF(f(ax_1,ax_2)) = \frac{1}{|a|^2}\hat{f}(\frac{w_1}{a},\frac{w_2}{a})$$

$$TF(\delta x_1 f) = (2i\pi \omega_1)TF(f)$$

$\delta x_1$ signifie que l'on dérive par rapport à la $1^{ère}$ variable. On peut aussi l'écrire $\frac{\delta}{\delta x_1}f$

**<font color=red>Remarque</font> :** 

Considérons le signal $f(x_1,x_2) = h(x_1)g(x_2)$

$$TF(f) = \int_{\mathbb{R}^2}^{}e^{-2i \pi \omega_1 x_1}h(x_1)e^{-2 i \pi \omega_2 x_2}g(x_2)dx_1 dx_2$$

$$TF(f)(\omega_1 \omega_2) = TF(h)(\omega_1)TF(g)(\omega_2)$$

En général, le signal n'est pas séparable.

## Calcul de la TF du signal porte

Soit $s(t)$, le signal porte suivant : $s(t) = [-\frac{T}{2},\frac{T}{2}]$ en 1D.
![signal porte](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Rectangular_function.svg/1200px-Rectangular_function.svg.png)


$$ 
\begin{align}
&= TF(s) =\int_{\mathbb{R}}^{}s(t)e^{-2 i \pi \omega t} dt
&= TF(s) = \int_{-\frac{T}{2}^{\frac{T}{2}}e^{-2 i \pi \omega t} dt
&= TF(s) = [\frac{e^{-2 i \pi \omega t}}{-2i \pi \omega}]^{\frac{T}{2}}_{-\frac{T}{2}}]
&= \frac{e^{i \pi \omega T }- e^{-i \pi \omega T}}{2i \pi \omega}
&= \frac{sin(\pi \omega T)}{\pi \omega}
\end{align}
$$

On obtient alors le **sinus cardinal**

## Introduction aux distributions : masse de Dirac

**Rappels sur Dirac :**

Soient un espace mesurable $(X,{\mathcal {A}}$ et $a\in X)$. On appelle **mesure de Dirac** au point  $a$, et l'on note  $\delta _{a}$, la mesure sur  $(X,{\mathcal {A}})$  définie par :

$$\forall A\in {\mathcal {A}},\ \delta _{a}(A)=1_{A}(a) = \left\{  \begin{array}{ll} 1 \ si \ a \in A \\ 
0 \ si \ a \notin A \end{array} \right.$

où $1_{A}$ désigne la fonction indicatrice de  $A$

$\delta _{a}(X)=1$ donc cette mesure est une probabilité sur $(X,{\mathcal {A}})$


Par abus de langage, on dit que la « fonction » δ de Dirac est nulle partout sauf en 0, où sa valeur infinie correspond à une « masse » de 1.

**<font color=red>Masse de Dirac</font> :** notation mathématique, définition de fonctions généralisées.

$f \to f(x)$ évaluation en x, linéaire.

Si $f$ est continue, alors :

$$f(x) = \lim_{n\to\infty} \int_{-\frac{1}{2n}}^{\frac{1}{2n}}f(y)dy$$
$$f(x) = \lim_{\delta\to0} (g_\delta \ast f)(x)$$

On appelle **Dirac en x**, la fonction généralisée $\delta_x$ et vérifie : 

$$<\delta_x, f>_{L^2} = f(x) \ \ \forall f \text{est une fonction continue}$$

$$\int_{\mathbb{R}}^{}f(u)\delta_x(u)du = f(x)$$

La **distribution de Dirac**, aussi appelée par abus de langage **fonction  δ  de Dirac**, peut être informellement considérée comme une fonction qui prend une « valeur » infinie en 0, et la valeur zéro partout ailleurs, et dont l'intégrale sur $\mathbb{R}$ est égale à 1.

On dit qu'un signal correspondant à une distribution de Dirac a un spectre blanc. C’est-à-dire que chaque fréquence est présente avec une intensité identique. Cette propriété permet d'analyser la réponse fréquentielle d'un système sans avoir à balayer toutes les fréquences.

**<font color=red>Propriétés</font> :**

- IPP : soit $f \ \mathbb{C}^\infty, f = 0 \ quand \ |x|>>1$
$$
\begin{align}
\int_{\mathbb{R}}^{}f(t)(1_{[0,+\infty[}(t))dt = \int_{\mathbb{R}}^{}f'(t)(1(t))dt 
&= -\int_{\mathbb{R}}^{}f(t)dt 
&= (f(+\infty) - f(0))
&= f(0)
\end{align}
$$

Une autre façon de définir la masse de Dirac, c'est de dire : 
$$\delta_0 = (1_{[0, +\infty[})$$

qui est une **limite de fonction**

- Pour $f$ continue, $f(t) \delta_0(t) = f(0) \delta_0(t)$
Avec $g$ continue

$$ 
\begin{align}
<f(t) \delta_0(t), g(t)>_{L^2} = <\delta_0(t), f(t)g(t)>
&= f(0)g(0)
&= <f(0)\delta_0,g>
\end{align}
$$

**Calcul de la TF de $\delta_0$**

$$TF(\delta_0) = \int_{\mathbb{R}}^{} \delta_0(t)e^{-2i \pi \omega t} dt$$

$$TF(\delta_0) = 1$$

$$TF(\delta_\tau) = e^{-2i\pi\omega\tau}$$

## Dirac et convolution

L'« **impulsion de Dirac** »  δ  est l'élément neutre de la convolution

$$(\delta \ast f)(x)\!:=\delta \left(f(x-\cdot )\right)=f(x-0)\quad (x\in \mathbb {R} ^{n})$$

d'où :  $\delta \ast f=f$

$$TF(\delta_0 \ast f) = TF(\delta_0)TF(f) = 1TF(f)$$

Dirac d'ordre supérieur : $<\delta_0^{(1)},f> = f'(0)$

**<font color=red>Égalité entre deux distributions</font> :**

Soient $\eta_1, \eta_2$, deux fonctions généralisées.

$\eta_1 = \eta_2 = <h_1,f> = <h_2,f>$ 
$\forall f \in \mathbb{C}^\infty(\mathbb{R}, \mathbb{C}) \ tq \ f(x) = 0 \ si \ |x| >> 1$

## Échantillonnage et théorème de Shannon

**<font color=red>Motivation</font> :** étant donné un signal analogique $s: \mathbb{R} \to \mathbb{R}$. On échantillonne le signal en **$(nTe)_{n\in\mathbb{Z}}$**

$Te$: temps d'échantillonnage

Étant donné $(s(nTe))_{n\in\mathbb{Z}}$, peut-on avoir accès à $s(t)$ ? $\to$ non en toute généralité. Si $Te << 1$, on aura une bonne approximation. Que se passe-t-il quand $Te$ augmente ?

**<font color=red>Théorème de Shannon</font> :** 

Soit $s:\mathbb{R} \to \mathbb{C}$ à bande passante $\hat{s}(\omega) = 0$ si $\omega \notin [-\omega_c,\omega_c]$ alors si $Te < \frac{1}{2\omega_c}$, on peut reconstruire $s$ par la formule d'interpolation.

$$ s(t) = \sum_{n\in\mathbb{Z}}^{}s(nTe)\frac{sin(\frac{\pi(t-nTe)}{Te})}{\pi(\frac{t-nTe}{Te})}$$

On retient donc que sous des hypothèses de bande passante, on peut reconstruire exactement le signal échantillonné suffisamment rapidement. Ce théorème établit les conditions qui permettent l'échantillonnage d'un signal de largeur spectrale et d'amplitude limitées.

La fréquence d'échantillonnage $Fe$ doit respecter la règle suivante : $Fe > 2f_0$ sachant que $f_0=\nu_0 Fe$

{$f$ à bande passante} $\subset$ signaux très régulier

$$TF(s^{(n)}) = (2i\pi\omega)^nTF(s)$$

$TF(s)$ est le support dans $[-\omega_c,\omega_c]$

## Formule sommatoire de Poisson

La **formule sommatoire de Poisson** (parfois appelée **resommation de Poisson**) est une identité entre deux sommes infinie : sa première construite avec une fonction $f$, la seconde avec sa transformée de Fourier  $\hat{f}$

Soient  $a$ un réel strictement positif et  $\omega_0  = \frac{2\pi}{a}$.

Si  $f$ est une fonction continue de $\mathbb{R}$ dans $\mathbb{C}$ et intégrable telle que 

$$\exists C>0\quad \exists \alpha >1\quad \forall x\in \mathbb {R} \quad |f(x)|\leq {\frac {C}{\left(1+|x|\right)^{\alpha }}}$$ 

et 
$$\sum _{m=-\infty }^{\infty }|{\hat {f}}(m\omega _{0})|<\infty$$

alors

$$\sum _{n=-\infty }^{\infty }f(t+na)={\frac {1}{a}}\sum _{m=-\infty }^{\infty }{\hat {f}}(m\omega _{0}){\rm {e}}^{{\rm {i}}m\omega _{0}t}.$$

## Peigne de Dirac

La distribution du peigne de Dirac est une somme de distributions espacées de 

$$\sum_{k=-\infty}^{\infty}\delta_{k T}(t) = \sum_{k=-\infty}^{\infty}\delta(t-kT)$$

Cette distribution périodique est particulièrement utile dans les problèmes d'échantillonnage, remplacement d'une fonction continue par une suite de valeurs de la fonction séparées par un pas de temps $T$. Elle est $T$-périodique et tempérée, comme dérivée d'une fonction constante par morceaux ; on peut donc la développer en série de Fourier.

![Peigne de Dirac](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0c/DiracComb.png/1200px-DiracComb.png)
