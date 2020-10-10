# Transformée de Fourier

> La transformée de Fourier est une opération qui transforme une fonction intégrable sur $\mathbb{R}$ en une autre fonction.

## Sommaire

[**Signaux continus en 1D**](#Signaux-continus-en-1D)

[**Propriétés de la TF**](#Propriétés-de-la-TF)

[**Convolution**](#Convolution)

[**Inverse de la TF**](#Inverse-de-la-TF)

[**TF et dérivation**](#TF-et-dérivation)

[**Égalité de Parseval**](#Égalité-de-Parseval)



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
$$ \begin{align}
\hat{f}(\omega) =& <f, e_\omega> \\
=& \int_{\mathbb{R}} f(t) \overline{e^{2i\pi\omega t}}dt \\
=& \int_{\mathbb{R}} f(t) e^{-2i\pi\omega t}dt
\end{align} $$

> *Pourquoi retrouve-t-on le signe $-$ devant $2i\pi \omega t$ ?* 
> La transformée de Fourier utilise le produit scalaire $<f,e_\omega>$, dans lequel on utilise le **conjugué**.

**<font color=red>Remarque</font>** : $L^1(\mathbb{R})$ contient des fonctions discontinues mais on a une condition d'intégrabilité.

$TF(f)(\omega)$ est bien définie car $$ | < f,e_{\omega} > | \leq \int_{\mathbb{R}}^{} | f(x) e^{-2i\pi \omega x} | \ dx =  \int_{\mathbb{R}}^{}  | f(x) | \ dx \le + \infty $$

donc $\forall \omega \ | \hat{f}(\omega) | \leq \int_{\mathbb{R}}^{} | f(x) | \ dx$ avec $\omega$ la fréquence en $Hz$

## Propriétés de la TF

* **<font color=red>Linéarité </font>**

  Soit $a,b \in \mathbb{R}$  et  $f,g \in L^1(\mathbb{R})$
  $$ TF(af+bg) = \widehat{af+bg} = a\hat{f}+b\hat{g} $$

* **Démonstration** :
  $$ \begin{align}
  TF(af+bg) =& <af+bg, e_\omega> \\
  & {\small\text{(par linéarité du produit scalaire hermitien)}} \\
  =& a<f, e_\omega> + b<g, e_\omega> \\
  =& a\hat{f}+b\hat{g} \quad \\
  \end{align} $$

* **<font color=red>Théorème du retard (translation temporelle) </font>** 

  Soit $t_0 \in \mathbb{R}$ et $f : \mathbb{R} \to \mathbb{C}$. On définit la translation de $f$ par $t_0$ :  $\tau_a(f)(t) \mapsto f(t-t_0)$
  $$ \widehat{\tau_a(f)}(\omega) = e^{-2i\pi \omega t_0} \hat{f}(\omega) $$

**Démonstration** : 
$$ \begin{align}
\widehat{\tau_a(f)}(\omega) =& \int_{\mathbb{R}} \tau_a(f)e^{-2i\pi\omega t}dt \\
&{\small \text{On pose} \ t' = t-t_0 \ \text{(changement de variable)}} \\
=& \int_{\mathbb{R}} f(t')e^{-2i\pi\omega (t'+a)} \ dt' \\
=& e^{-2i\pi\omega t_0} \int_{\mathbb{R}} f(t')e^{-2i\pi\omega t'} dt' \\
=& e^{-2i\pi\omega t_0} \hat{f}(\omega)
\end{align} $$

- **<font color=red>Modulation ou Translation fréquencielle </font>**

  Soit $\omega_0 \in \mathbb{R}$ et $f:\mathbb{R} \to \mathbb{C}$ On pose la notation suivante : $f_{w_0}(t) \mapsto e^{2i \pi \omega_0 t}f(t)$ 

$$ \widehat{f_{\omega_0}}(\omega) = \tau_{\omega_0}(\hat{f})(\omega) = \hat{f}(\omega-\omega_0) $$

**Démonstration** : 
$$ \begin{align}
\widehat{f_{\omega_0}} =& \int_{\mathbb{R}} f(t) e^{2i\pi\omega_0 t} e^{-2i\pi \omega t}dt \\
=& \int_{\mathbb{R}} f(t) e^{2i\pi (\omega-\omega_0) t} dt \\
=& \hat{f}(\omega-\omega_0)
\end{align} $$

* **<font color=red>Dilatation du temps (changement d'échelle)</font>** 

  Soit $a \in \mathbb{R}$ et $f : \mathbb{R} \to \mathbb{C}$. On définit la dilatation de $f$ par $a$ :  $D_a(f)(t) \mapsto f(at)$
  $$ \widehat{D_a(f)} = \frac{1}{|a|} \hat{f}(\frac{\omega}{a}) $$

**Démonstration** : 

Pour $a \geq 0$ :
$$ \begin{align}
\widehat{D_a(f)} =& \int_{\mathbb{R}} f(at) e^{-2i\pi \omega t}dt \\
&{\small \text{On pose} \ t' = at \ \text{(changement de variable)}} \\
=& \int_{\mathbb{R}} f(t') e^{-2i\pi \omega \frac{t'}{a}} \frac{dt'}{a} \\
=& \frac{1}{a} \int_{\mathbb{R}} f(t') e^{-2i\pi \frac{\omega}{a}t'} dt' \\
=& \frac{1}{a} \hat{f}(\frac{\omega}{a})
\end{align} $$

Pour $a<0$ :
$$ \begin{align}
\widehat{D_a(f)} =& \int_{\mathbb{R}} f(at) e^{-2i\pi \omega t}dt \\
&{\small \text{On pose} \ t' = at \ \text{(changement de variable)}} \\
& ⚠{\small \text{: ici le changement de variable inverse les bornes }} \\
=& \int_{+\infty}^{-\infty} f(t') e^{-2i\pi \omega \frac{t'}{a}} \frac{dt'}{a} \\
=& \frac{1}{a}\int_{+\infty}^{-\infty} f(t') e^{-2i\pi \frac{\omega}{a}t'} dt' \\
& {\small \text{par inversion des bornes }} \\
=& -\frac{1}{a} \int_{\mathbb{R}} f(t') e^{-2i\pi \frac{\omega}{a}t'} dt' \\
=& -\frac{1}{a} \hat{f}(\frac{\omega}{a})
\end{align} $$


- **<font color=red> Passage au conjugué</font>** 
Soit $f : \mathbb{R} \to \mathbb{C}$
$$ \widehat{\overline{f}(\omega)} = \overline{\hat{f}(-\omega)} $$
**Démonstration** : 
$$ \begin{align}
\widehat{\overline{f}(\omega)} =& \int_{\mathbb{R}} \overline{f(t)} e^{-2i\pi \omega t}dt \\
=& \int_{\mathbb{R}} \overline{f(t)} \overline{e^{2i\pi \omega t}}dt \\
& {\small \text{par la propriété du conjugué : } \overline{z_1}.\overline{z_2} =  \overline{z_1.z_2}} \\
=& \overline{\int_{\mathbb{R}} f(t) e^{2i\pi \omega t}dt} \\
=& \overline{\int_{\mathbb{R}} f(t) e^{-2i\pi (-\omega) t}dt} \\
=& \overline{\hat{f}(-\omega)}
\end{align} $$

Si on se donne $\widehat{{f}(\omega)}$ pour $\omega \geq 0$, alors on connaît partout $\widehat{{f}(\omega)}$. La moitié de l'information suffit.

- **<font color=red>La gaussienne (issue de la loi normale)</font>** 
$$ g_{\sigma} = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{x^2}{2\sigma^2}} $$

**Calcul de la TF**
- **<font color=red>Rappel intégration par partie</font>** 

$\int_{a}^{b} F'G \ dt =  \int_{a}^{b}  FG' \ dt = F(b)G(b) - F(a)G(a)$

## Convolution

On définit la **convolution h*g** tel que :

$$ (h*g)(t) = \int_{\mathbb{R}}^{} h(t-u)g(u) du $$

**Exemple : signal porte**

![signal porte](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Rectangular_function.svg/1200px-Rectangular_function.svg.png)

Dans le cas du signal porte, $\int_{}^{}h \ du = 1$
$$ (h*g)(t) = \int_{\mathbb{R}}^{}h(u-t)g(u) \ du $$
Remarque : h(u) est paire, i.e $h(u) = h(-u)$

**<font color=red>Propriétés de la convolution</font> :** 
- Symétrie : $h*s = s*h$
- $\int_{\mathbb{R}}^{}| f*g(t)| \ dt \leq \int_{\mathbb{R}}^{}| f| \ dt \ \int_{\mathbb{R}}^{}|g| \ dt$
- Soit $f,g \in L^2(\mathbb{R})$, on a : $$ \widehat{f*g}(\omega) = \hat{f}(\omega)\hat{g}(\omega) $$

## Inverse de la TF

On peut inverser la TF.  $$ (TF)^{-1}(\hat{f})(t) = \int_{\mathbb{R}}^{} \hat{f}(t)e^{2i\pi \omega t}\ dt $$

**<font color=red>Propriété</font> :** 
$$ \widehat{fg} = \hat{f} * \hat{g} $$ car  :

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
-\int_{\mathbb{R}}^{}(e^{-2i \pi \omega t)'}f(t) \ dt
\\ &= (2i \pi \omega)\int_{\mathbb{R}}^{} e^{-2i \pi \omega t} f(t) \ dt
\end{align} 
$$

Si le signal est p fois différenciable, $$ \widehat{f^{(p)}}(\omega) = (2i \pi \omega)^p \hat{f}(\omega) $$

Si  $\widehat{f^{(p)}}(\omega)$ est d'énergie finie, $L^2(\mathbb{R})$ : $$ \widehat{f^{(p)}}(\omega) \in L^2 => (2i \pi \omega)^p \hat{f}(\omega) \in L^2 $$

## Égalité de Parseval

La TF préserve l'énergie des signaux. Isométrie de $L^2(\mathbb{R})$

Cela signifie, pour $f : \mathbb{R} \to \mathbb{R}$

$$ \int_{\mathbb{R}}^{}|f(t)|^2  \ dt = \int_{\mathbb{R}}^{} | \hat{f}(\omega)|^2  \ d\omega $$

> L'énergie  totale s'obtient en sommant les contributions des différents harmoniques
