# Transformée de Fourier

> La transformée de Fourier est une opération qui transforme une fonction intégrable sur $\mathbb{R}$ en une autre fonction.

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

**<font color=red>Attention</font>** : On a bien $\int_{\mathbb{R}} f(x)\overline{f}(x)dx = \int_{\mathbb{R}} |f(x)|^2dx \leq 0$ et nul ssi $f = 0$

Quelques propriétés sur ce produit scalaire : 
* **Symétrie hermitienne** : $<f,g> = \overline{<g,f>}$

* **Linéarité à gauche** : $<f+ \lambda h, g> \ = \ <f,g> + \lambda <h,g>$

* **Semi-linéarité à droite** : $<f,g + \lambda h> \ = \ <f,g> + \overline{\lambda} <f,h>$

  >Remarque : on appelle une telle application une forme **sesquilinéaire hermitienne** (à droite)

$$ \\ $$

**<font color=red>Définition</font>** : 

Soit $f \in L^1(\mathbb{R})$ et $\omega \in \mathbb{R}$
La transformée de Fourier de $f$ est définie par :

$$ TF(f)(t) = \hat{f}(t) = \int_{\mathbb{R}} f(t) e^{-2i\pi\omega t}dt $$

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

$$
|< f,e_{\omega}>| \leq \int_{\mathbb{R}}^{} | f(t) e^{-2i\pi \omega t} | \ dx =  \int_{\mathbb{R}}^{}  | f(t) | \ dt \le + \infty
$$
donc $\forall \omega \ | \hat{f}(\omega) | \leq \int_{\mathbb{R}}^{} | f(t) | \ dt$ avec $\omega$ la fréquence en $Hz$

## Propriétés de la TF

* **<font color=red>Linéarité </font>**

Soit $a,b \in \mathbb{R}$  et  $f,g \in L^1(\mathbb{R})$

$$
TF(af+bg) = \widehat{af+bg} = a\hat{f}+b\hat{g} 
$$


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

  $$
  \widehat{D_a(f)} = \frac{1}{|a|} \hat{f}(\frac{\omega}{a})
  $$
  
  
  **Démonstration** : 
  
  ​	Pour $a \geq 0$ :

$$
\begin{align}
\widehat{D_a(f)} =& \int_{\mathbb{R}} f(at) e^{-2i\pi \omega t}dt \\
&{\small \text{On pose} \ t' = at \ \text{(changement de variable)}} \\
=& \int_{\mathbb{R}} f(t') e^{-2i\pi \omega \frac{t'}{a}} \frac{dt'}{a} \\
=& \frac{1}{a} \int_{\mathbb{R}} f(t') e^{-2i\pi \frac{\omega}{a}t'} dt' \\
=& \frac{1}{a} \hat{f}(\frac{\omega}{a})
\end{align}
$$

​		Pour $a<0$ :

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

$$
\widehat{\overline{f}}(\omega) = \overline{\hat{f}(-\omega)}
$$

​	**Démonstration** : 
$$
\begin{align}
\widehat{\overline{f}}(\omega) =& \int_{\mathbb{R}} \overline{f(t)} e^{-2i\pi \omega t}dt \\
=& \int_{\mathbb{R}} \overline{f(t)} \overline{e^{2i\pi \omega t}}dt \\
& {\small \text{par la propriété du conjugué : } \overline{z_1}.\overline{z_2} =  \overline{z_1.z_2}} \\
=& \int_{\mathbb{R}} \overline{f(t) e^{2i\pi \omega t}dt} \\
& {\small \text{par la propriété du conjugué : } \overline{z_1}+\overline{z_2} =  \overline{z_1+z_2}} \\
=& \overline{\int_{\mathbb{R}} f(t) e^{2i\pi \omega t}dt} \\
=& \overline{\int_{\mathbb{R}} f(t) e^{-2i\pi (-\omega) t}dt} \\
=& \overline{\hat{f}(-\omega)}
\end{align}
$$

​	Si on se donne $\widehat{{f}(\omega)}$ pour $\omega \geq 0$, alors on connaît partout $\widehat{{f}(\omega)}$. La moitié de l'information suffit.

- **<font color=red> Dérivation temporelle</font>** 

  Soit $f : \mathbb{R} \to \mathbb{R}$​ différentiable

$$
\widehat{f'}(\omega) = 2i\pi\omega \widehat{f}(\omega)
$$

​	**Démonstration** : 



> **<font color=red>Rappel intégration par partie</font>** 
>
> $\int_{a}^{b} F'.G\ dt = [F.G]_{a}^{b} - \int_{a}^{b} F.G'\ dt $

Fixons $M_1$ et $M_2$ deux réels positifs.


$$
\begin{align}
\widehat{f'}(\omega) = \lim\limits_{M_1 \to -\infty \\ M_2 \to +\infty} & \int_{M_1}^{M_2} f'(t) e^{-2i\pi \omega t}dt \\
& {\small \text{par intégration par parties }}\\
=& \lim\limits_{M_1 \to -\infty \\ M_2 \to +\infty} \quad [f.e^{-2i\pi \omega t}]_{M_1}^{M_2} - \int_{M_1}^{M_2} f(t) (-2i\pi \omega).e^{-2i\pi \omega t}dt \\
=& \lim\limits_{M_1 \to -\infty \\ M_2 \to +\infty} \quad f(M_2).e^{-2i\pi\omega M_2} - f(M_1).e^{-2i\pi \omega M_1} + 2i\pi \omega\int_{M_1}^{M_2} f(t).e^{-2i\pi \omega t}dt \\
& {\small \text{comme f est supposée integrable, }} \\
& {\small \text{les deux premiers termes tendent vers 0 quand } M_1 \text{ et } M_2 \text{ tendent respectivement vers
} -\infty \text{ et } +\infty}\\
=& \lim\limits_{M_1 \to -\infty \\ M_2 \to +\infty} \quad 2i\pi\omega \int_{M_1}^{M_2} f(t).e^{-2i\pi \omega t}dt \\
=& 2i\pi\omega \int_\mathbb{R} f(t).e^{-2i\pi \omega t}dt \\
=& 2i\pi\omega .\widehat{f}(\omega) \\
\end{align}
$$


par <font color=red>généralisation</font> si $f$ est différentiable $p$ fois tq $\forall i \in \mathbb{Z} : f^{(i)} \in L^2$ alors :


$$
\widehat{f^{(p)}}(\omega) = (2i\pi\omega)^p .\widehat{f}(\omega)
$$

De plus, si  $\widehat{f^{(p)}}(\omega)$ est d'énergie finie, $L^2(\mathbb{R})$ alors :  $ \widehat{f^{(p)}}(\omega) \in L^2(\mathbb{R}) => (2i \pi \omega)^p \hat{f}(\omega) \in L^2(\mathbb{R}) $

- **<font color=red>Dérivation fréquentielle</font>** 

  Soit $f : \mathbb{R} \to \mathbb{R}$ , si $f$ et $tf$ sont intégrables  dans $\mathbb{R}$  c.a.d: $f,\;t \to tf(t) \in L^1(\mathbb{R})$

  Alors la transformée de Fourier $\widehat{f}$ est dérivable (c’est à dire $\widehat{f} \in C^1$) et on a :

$$
\frac{d}{d\omega}\widehat{f}(\omega) = -2i\pi.\widehat{tf(t)}(\omega)
$$

​	**Démonstration** : 

​	Posons $g(t, \omega) = e^{−2i\pi\omega t}f(t)$, et calculons : $\frac{d}{d\omega} g(t, ω) = -2i\pi t.e^{−2i\pi\omega t}f(t)$

​	Cette dérivée est continue $\forall t $ et de plus  $\frac{dg}{d\omega}$   est une fonction intégrable (car $tf(t) ∈ L^1(\mathbb{R})$). 

 	Les hypothèses du théorème de la dérivation sous le signe de l’intégrale sont donc vérifiées, et nous avons :
$$
\begin{align}
\frac{d}{d\omega}\widehat{f}(\omega) =& \frac{d}{d\omega} \int_\mathbb{R} f(t)e^{-2i\pi \omega t}\ dt \\
&= \small {\text{dérivation sous le signe intégrale}} \\
=& \int_\mathbb{R} \frac{d}{d\omega}(f(t)e^{-2i\pi \omega t})dt \\
=& -2i\pi \int_\mathbb{R} t.e^{−2i\pi\omega t}f(t)dt \\
=& -2i\pi.\widehat{tf(t)}(\omega)
\end{align}
$$


- **<font color=red>La gaussienne (issue de la loi normale)</font>** 

Soit $g_\sigma$ la gaussienne d'écart type $\sigma \in  \mathbb{R}^+$ 
$$
g_{\sigma}(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{x^2}{2\sigma^2}}
$$

> TODO : calcul de $ \widehat{g_{\sigma}}$

## Convolution

Soit $h,g \in L^2(\mathbb{R})$

On définit la **convolution h $\ast$ g** tel que :


$$
(h \ast g)(t) = \int_\mathbb{R} h(t-u)g(u) du
$$


**Signal porte**

On défini le signal porte $\Pi_{[a,b]}$ part la formule suivante :

$$
\Pi_{[a,b]}(t) = \left\{
\begin{array}{ll}
1 & \text{si } t \in [a, b] \\ 
0 & \text{sinon}
\end{array}
\right.
$$


> Par convention si a et b ne sont pas précisés alors  $\Pi(x) = \Pi_{[-\frac{1}{2}, \frac{1}{2}]}(x)$

![signal porte](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Rectangular_function.svg/1200px-Rectangular_function.svg.png)

On a les propriétés suivantes : 

- $\int_\mathbb{R} \Pi(t)dt = 1$
- Parité : $\Pi(t) = \Pi(-t)$

### Propriétés  

- Commutativité : $h \ast s = s \ast h$

- Bilinéarité :  $(af+bg)*h = a.f*h+ b.g*h$

- Impulsion unitaire comme élément neutre :  $\mathbb{1}(t) = \left\{
  \begin{array}{ll}
  1 & \text{si } t = 0 \\ 
  0 & \text{sinon}
  \end{array}
  \right.$
  
- $\int_{\mathbb{R}}^{}| f \ast g(t)| \ dt \leq \int_{\mathbb{R}}^{}| f| \ dt \ \int_{\mathbb{R}}^{}|g| \ dt$

- La convolution d'un signal $f$ par le signal porte s'obtient en faisant glisser $f$ sur l'intervalle $[a,b]$. On obtient alors un élargissement de $f$.

  ![](./produit_convolution.png)


**<font color=red>Transformée de Fourier d’un produit de convolution</font>**:

Soit $f,g \in L^2(\mathbb{R})$, on a :

$$
\widehat{f \ast g}(\omega) = \hat{f}(\omega)\hat{g}(\omega)
$$


**Démonstration** : 

$$
\begin{align}
\widehat{f \ast g}(\omega) =& \int_{\mathbb{R}\times\mathbb{R}} f(u)g(t-u)du\;e^{-2i\pi \omega t}dt \\
=& \int_{\mathbb{R}}\int_{\mathbb{R}} f(u)g(t-u) e^{-2i\pi\omega t}du\;dt \\
&{\small \text{On pose} \ t' = t-u \ \text{(changement de variable)}} \\
=& \int_{\mathbb{R}}\int_{\mathbb{R}} f(u)g(t') e^{-2i\pi\omega (t'+u)}du\;dt' \\
&{\small \text{par le théorème de Fubini on obtient :}} \\
=& \int_{\mathbb{R}}f(u) e^{-2i\pi\omega u}du\;\int_{\mathbb{R}} g(t') e^{-2i\pi\omega t'}dt' \\
=& \hat{f}(\omega)\hat{g}(\omega)
\end{align}
$$


## Inverse de la TF

Soit $f \in L^1(\mathbb{R})$, On définit la transformation de Fourier inverse $TF^{-1}$ par la relation :

$$
(TF)^{-1}(f)(t) = \int_\mathbb{R} f(t)e^{2i\pi \omega t}\ dt
$$
**<font color=red>Propriétés</font> :** 

- Symétrie : $TF^{-1}(f)(t) = TF(f)(-t)$

- $\widehat{fg} = \hat{f} * \hat{g}$

- $TF^{-1} TF(fg) = fg$

## Égalité de Parseval

La TF préserve l'énergie des signaux. Isométrie de $L^2(\mathbb{R})$

Cela signifie, pour $f : \mathbb{R} \to \mathbb{R}$

$$
\int_{\mathbb{R}}^{}|f(t)|^2  \ dt = \int_{\mathbb{R}}^{} | \hat{f}(t)|^2  \ dt
$$


> L'énergie totale s'obtient en sommant les contributions des différents harmoniques

## Transformation de Fourier en 2D

On considère $L^2(\mathbb{R}^2,\mathbb{C}) = \{f : \mathbb{R}^2 \to \mathbb{C};  \int_{\mathbb{R}\times\mathbb{R}}|f(x,y)|^2 dxdy < +\infty \}$

On définit la TF :

$$
\widehat{f}(\omega_1, \omega_2) = \int_{\mathbb{R}\times\mathbb{R}} f(x_1,x_2) e^{-2i \pi(\omega_1 x_1 + \omega_2 x_2)}dx_1 dx_2
$$
généralisation en dimension n :

Soit $x = (x_1, \dots, x_n)$et $ \omega = (\omega_1, \dots, \omega_n)$

$$
\widehat{f}(\omega_1,\dots,\omega_n) = \int_{\mathbb{R}^n}f(x_1,\dots,x_n) e^{-2i\pi<\omega, x>}dx_1\dots dx_n
$$

La plupart des propriétés déjà vues en $1D$ restent vraies en $nD$ cependant il y a quelques exceptions: 

- $$TF(f(ax_1,ax_2)) = \frac{1}{|a|^2}\hat{f}(\frac{w_1}{a},\frac{w_2}{a})$$

- $$TF( \frac{\delta f}{\delta_{x_1}}) = (2i\pi\omega_1)\widehat{f}(\omega_1,\omega_2)$$

> $\frac{\delta}{\delta x_1}f$ indique une dérivée partielle.  Cela signifie que l'on dérive la fonction par rapport à la $1^{ère}$ variable uniquement en considèrent la seconde (ici $x_2$) comme constante.

**<font color=red>Remarque</font> :** 

Considérons le signal séparable suivant $f(x_1,x_2) = h(x_1)g(x_2)$

$$
\begin{align}
\widehat{f}(\omega_1,\omega_2) =& \int_{\mathbb{R}\times\mathbb{R}}e^{-2i\pi\omega_1 x_1}h(x_1)\;e^{-2i\pi\omega_2 x_2}g(x_2)dx_1 dx_2 \\
&{\small \text{par le théorème de Fubini}} \\
=& \int_\mathbb{R}e^{-2i\pi\omega_1 x_1}h(x_1)dx_1\;\int_\mathbb{R}e^{-2i\pi\omega_2 x_2}g(x_2)dx_2 \\
=& \widehat{h}(\omega_1).\widehat{g}(\omega_2)
\end{align}
$$
<font color=red>⚠ </font>: En général, le signal n'est pas séparable.

## Calcul de la TF du signal porte

Soit $s(t) = \Pi_{[-\frac{T}{2}, \frac{T}{2}]}(t)$ avec $T \in \mathbb{R}^+$

$$
\begin{align}
\widehat{s}(t) =& \int_\mathbb{R}s(t)e^{-2i\pi\omega t}dt  \\
=& \int_{-\frac{T}{2}}^{\frac{T}{2}}e^{-2i\pi\omega t} dt \\ \\
& \text{Rappel : } \ F(e^{u}) = \frac{e^u}{u}\\ \\
=& [\frac{e^{- 2 i\pi \omega t}}{- 2 i \pi \omega}]^{\frac{T}{2}}_{-\frac{T}{2}} \\
=& \frac{e^{i\pi \omega T} - e^{-i \pi \omega T}}{-2 i \pi \omega}\\ \\
& \text{on retrouve} \ A = \frac{e^{i\pi \omega T} - e^{-i \pi \omega T}}{2i}. \ \text{Selon la formule d'Euler, on a donc} \ A = sin(\pi \omega T) \\ \\
=& \frac{sin(\pi \omega T)}{\pi\omega} = T.sinc(\pi\omega T)
\end{align}
$$

On obtient alors un **sinus cardinal**.

> On peut également s'apercevoir que $s(t) = \Pi_{[-\frac{T}{2}, \frac{T}{2}]}(t) = \Pi_{[-\frac{1}{2}, \frac{1}{2}]}(T.t) = D_{1/T}(\Pi)$
> Alors d'après la formule $\widehat{D_a(f)} = \frac{1}{|a|} \hat{f}(\frac{\omega}{a})$ 
>
> et sachant que  $\widehat{\Pi}(\omega)=  sinc(\pi\omega)$
>
> On obtient facilement : $\widehat{s}(\omega) = T.sinc(\pi\omega T) = \frac{sin(\pi \omega T)}{\pi\omega}$

## Introduction aux distributions : masse de Dirac

**Rappels sur Dirac :**

Soient un espace mesurable $(X,{\mathcal {A}}$ et $a\in X)$. On appelle **mesure de Dirac** au point  $a$, et l'on note  $\delta _{a}$, la mesure sur  $(X,{\mathcal {A}})$  définie par :

$$\forall A\in {\mathcal {A}},\ \delta _{a}(A)=1_{A}(a) = \left\{  \begin{array}{ll} 1 \ si \ a \in A \\ 
0 \ si \ a \notin A \end{array} \right.$$

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
=& -\int_{\mathbb{R}}^{}f(t)dt 
=& (f(+\infty) - f(0))
=& f(0)
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

L'échantillonnage consiste à prélever à intervalle de temps régulier des échantillons du signal. Le signal devient alors périodique avec la $T_e$ la période d'échantillonnage. 

$$T_e = \frac{1}{fe}$$

**<font color=red>Motivation</font> :** étant donné un signal analogique $s: \mathbb{R} \to \mathbb{R}$. On échantillonne le signal en **$(nTe)_{n\in\mathbb{Z}}$**

Étant donné $(s(nTe))_{n\in\mathbb{Z}}$, peut-on avoir accès à $s(t)$ ? $\to$ non en toute généralité. Si $Te << 1$, on aura une bonne approximation. Que se passe-t-il quand $Te$ augmente ?

**<font color=red>Théorème de Shannon</font> :** 

Soit $s:\mathbb{R} \to \mathbb{C}$ à bande passante $\hat{s}(\omega) = 0$ si $\omega \notin [-\omega_c,\omega_c]$ alors si $Te < \frac{1}{2\omega_c}$, on peut reconstruire $s$ par la formule d'interpolation.

$$ f(t) = \sum_{n\in\mathbb{Z}}^{}Te.f(nTe)\frac{sin(\frac{\pi(t-nTe)}{Te})}{\pi(\frac{t-nTe}{Te})}$$

Si on pose $\phi_{Te} \ \text{le sinus cardinal} : \phi_{Te}=\frac{\frac{sin(\pi T)}{Te}}{\frac{\pi t}{Te}}$

On peut donc écrire : 

$$ f = \sum_{n\in\mathbb{Z}}^{}Te.f(nTe)\delta_{nTe} \ast \phi_{Te}$$

**Problème :** le sinus cardinal décroît lentement vers 0. Pour reconstruire f(t), on a besoin de beaucoup d'échantillons pour une bonne précision.

**<font color=red>Hypothèse sur f :</font>**

$supp(\hat{f}) \subset [-B,B]$  et $[-B, B] \subset [-\frac{1}{2Te},\frac{1}{2Te}]$

On multiplie par une porte :

$$\hat{f}(\omega)= \hat{f_d}(\omega) . \Pi_{[-\frac{1}{2Te},\frac{1}{2Te}]}$$

On applique $TF^{-1}$ avec $\phi_{Te}(t) = \frac{sin(\frac{\pi t}{Te})}{\frac{\pi t}{Te}}$

On a donc :

$\hat{f} = \hat{f_d}.h$

$$
\begin{align}
f = f_d \ast TF^{-1}(h)
&= \sum_{n\in\mathbb{Z}}^{} f(nTe)_{\delta_{nTe}} * TF^{-1}(h)
\end{align}
$$

et $TF^{-1}(h)$ décroit vite car h est régulier.

On retient donc que sous des hypothèses de bande passante, on peut reconstruire exactement le signal échantillonné suffisamment rapidement. Ce théorème établit les conditions qui permettent l'échantillonnage d'un signal de largeur spectrale et d'amplitude limitées.

La période d'échantillonnage $Te$ doit respecter la règle suivante : $Te > 2f_{max}$. Si cette contrainte n'est pas respectée, alors on a un **repliement spectral** car le signal analogique et l'échantillonnage se superposent.

{$f$ à bande passante} $\subset$ signaux très régulier

$$TF(s^{(n)}) = (2i\pi\omega)^nTF(s)$$

$TF(s)$ est le support dans $[-\omega_c,\omega_c]$

### Shannon en 2D

Si $\hat{f}$ a un support dans $[-\frac{1}{2Te},\frac{1}{2Te}]^2$

alors :

$$ f(x) = \sum_{n_1, n_2\in\mathbb{Z^2}}^{}f(n_1Te,n_2Te)\phi_T(x-(n_1T,n_2T))$$

avec $\phi_T : \mathbb{R^2} \to \mathbb{R}$

$$x \to \frac{\frac{sin(\pi x_1)}{T}}{\frac{\pi x_1}{T}} . \frac{\frac{sin(\pi x_2)}{T}}{\frac{\pi x_2}{T}}$$

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

## Transformée de Fourier discrète 

On se donne un signal de longueur $N$ $(s_n)_{n=0,...,N-1}$

$\hat{s}(k)=\sum _{n=0}^{N-1}s(n)e ^{-2\mathrm {i} \pi k{\frac {n}{N}}}\qquad {\text{pour}}\qquad 0\leqslant k<N$

Soit $\omega = e^{\frac{-2i\pi}{N}}$ 	alors on a :

$$\hat{s}_k = \sum_{n=0}^{N-1}s_n(\omega^k)^n$$

Soit s un signal périodique donc 

$$ s = \hat{s}_ne^{\frac{2i \pi nt}{T}}$$

sachant que $A_{k,n} = (\omega^k)^n$, on a :

$$ s = \hat{s}_ne^{2i \pi n\frac{t}{T}}$$ 

où T est la période du signal

**<font color="red">Inverse de la TFD</font> :**

Soit une image f de taille M × N. La transformée de Fourier discrète inverse permet de calculer l’image originale à partir d’une transformée de Fourier : 

$$f(m,n) = \frac{1}{MN}\sum^{M−1}_{u=0}\sum^{N−1}_{v=0}F(u,v)e^{+j 2\pi(\frac{um}{M} + \frac{vn}{N})}$$

où $F(u,v)$ représente la TFD de l'image f. 

$$F(u,v) = \frac{1}{MN}\sum^{M−1}_{u=0}\sum^{N−1}_{v=0}f(m,n)e^{−j 2\pi(\frac{um}{M} + \frac{vn}{N})}$$

Le produit de convolution de deux images est équivalent à la multiplication de leurs TFD.

### TFD en 2D :

$$\hat{X}_{k_1,k_2} = \sum_{n_1,n_2}^{N-1}X_{n_1,n_2}e^{\frac{-2i\pi k_1 n_1}{N_1}} e^{\frac{-2i\pi k_2 n_2}{N_2}}$$


## Fast Fourier Transform

> On introduit l'algorithme de la FFT pour calculer la TFD car sa complexité varie en $O(nlog(n))$ contrairement à l'algorithme naïf en $O(n^2)$

L'algorithme de la FFT est un algorithme qui permet d'effectuer la TF de manière plus optimale.

Lorsqu’on désire calculer la transformée de Fourier d’une fonction $x(t)$  à l’aide d’un ordinateur, ce dernier ne travaille que sur des valeurs discrètes, on est amené à :
-   discrétiser la fonction temporelle,
-   tronquer la fonction temporelle,
-   discrétiser la fonction fréquentielle

$$
\begin{align}
X_k = \sum_{n=0}^{N-1}x_ne^{\frac{-2i \pi nk}{N}}
&= \sum_{m=0}^{N/2-1}x_{2m}e^{\frac{-2i \pi (2mk)}{2N}} +  \sum_{m=0}^{N/2-1}x_{2m+1}e^{\frac{-2i \pi ((2m+1)k)}{M}}
&= \sum_{m=0}^{M-1}x_{2m}e^{\frac{-2i \pi (mk)}{M}} +  \sum_{m=0}^{M-1}x_{2m+1}e^{\frac{-2i \pi (mk)}{M}}
\end{align}
$$

La FFT est donc une décomposition par alternance de signal de $N = 2^m$ points dans le domaine temporel en $N$ signaux de 1 point.

$$f_j = \sum^{n-1}_{k=0}x_ke^{\frac{-2\pi i}{n}jk}$$

**<font color="red">Rappel sur la double somme </font> :**

$$ (\sum_{n}^{}x[n]) (\sum_{k}^{}x[k]) = \sum_{n,k}^{}(x[n].x[k])$$

Pour étudier la FFT à temps discret, on n'analyse pas ce qu'il y a au-delà de $\frac{1}{2}$, on étudie le signal sur l'intervalle $[0;\frac{N}{2}]$

**Un exemple de la technique du zéro padding** : 

$\vec{Y} = \begin{pmatrix} Y[0] \\ Y[N+M-1] \end{pmatrix}$

Calculez $Y[k]$ en faisant intervenir la TF $X(\nu)$

Soit $\tilde{N} = N+M$

$Y[k] = Y(\frac{k}{\tilde{N}})$

$$
\begin{align}
Y(\nu) = \sum^{\tilde{N}-1}_{n=0} y[n]e^{-i2\pi n \nu}
&= \sum^{N-1}_{n=0} y[n]e^{-i2\pi n \nu} + \sum^{N+M-1}_{n=N} y[n]e^{-i2\pi n \nu}
&= X(\nu)
\end{align}
$$

$Y[k] = X(\frac{k}{N+M})$

On a $\frac{1}{N+M} < \frac{1}{N}$

donc le pas d'échantillonnage de la fonction $X(\nu)$ est plus fin. On mets autant de 0 que le nombre d'échantillon.



## Short Time Fourier Transform

> Les transformées de Fourier n'indiquent pas clairement comment le contenu en fréquence d'un signal change dans le temps. Cette information est cachée dans la phase. Pour voir comment le contenu en fréquence d'un signal change au fil du temps, nous pouvons découper le signal en blocs et calculer le spectre de chaque bloc.
>

Elle peut être utilisée pour isoler différentes sources dans un signal. Elle est aussi utilisée pour calculer le changement de phase et de fréquence d'un signal non-stationnaire en fonction du temps.

Le carré de son module donne le **spectrogramme**.
$$
STFT\left\{x[n]\right\} = X(m, \omega) = \sum^{\infty}_{n = -\infty}x[n]w(n-m)e^{(-i \omega n)}
$$
où $w$ est la fenêtre. Lorsque la fonction de fenêtrage est une **fonction gaussienne**, la transformée de Fourier à court terme est également appelée **transformée de Gabor**.

La STFT d'un signal $x(n)$ est une fonction de deux variables : le temps et la fréquence. La longueur du bloc est déterminée par le support de la fonction de fenêtre $w(n)$.

La STFT d'un signal est **inversible**.
On peut choisir la **longueur du bloc**. Plus le bloc est **long**, plus la **résolution de fréquence sera élevée** (parce que le lobe principal de la fonction de fenêtre sera étroit). Plus le bloc est **court**, plus **la résolution temporelle sera élevée** parce que la moyenne des échantillons est moins élevée pour chaque valeur de la STFT.

