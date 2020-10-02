# Transformée de Fourier

> La transformée de Fourier est une opération qui transforme une fonction intégrable sur $ \mathbb{R} $ en une autre fonction.


## Sommaire

[**Signaux continus en 1D**](#Signaux-continus-en-1D)

[**Propriétés de la TF**](#Propriétés-de-la-TF)

## Signaux continus en 1D

Deux espaces :  
* $ L^1(\mathbb{R}) = \left\{  f: \mathbb{R} -> \mathbb{R}; \ \int_{\mathbb{R}}^{} | f(x) | \ dx < + \infty \right\} $
* $ L^2(\mathbb{R}, \mathbb{C}) = \left\{  f: \mathbb{R} -> \mathbb{C}; \ \int_{\mathbb{R}}^{} | f(x) |^2 \ dx < + \infty \right\} $

$ L^2 $ correspond à **l'énergie finie**

On défini sur l'espace des signaux d'énergie finie $L^2$ le **<font color=red>Produit scalaire hermitien </font>** suivant : 
$$
<f,g> = \int_{\mathbb{R}} f(x)\overline{g(x)} dx
$$
Où $\overline{a}$ le complexe conjugué de a $\in \mathbb{C}$.

$ \left\{  \begin{array}{ll} a = a_{1} + ia_{2} \\ 
\overline{a} = a_1 - ia_2 \end{array} \right. $

**<font color=red>Attention</font>** : On a bien $ \int_{\mathbb{R}} f(x)\overline{f}(x)dx = \int_{\mathbb{R}} f(x)|^2dx \leq 0 $ et nul ssi $f = 0$

Quelques propriétés sur ce produit scalaire : 
* symétrie hermitienne: $ <f,g> = \overline{<g,f>} $

* linéarité à gauche: $ <f+ \lambda h, g> \ = \ <f,g> + \lambda <h,g> $

* semi-linéarité à droite: $ <f,g + \lambda h> \ = \ <f,g> + \overline{\lambda} <f,h> $

  > remarque : on appelle une telle application une forme **sesquilinéaire hermitienne** (à droite)

$$ \\ $$

**<font color=red>Définition</font>** : 

Soit $ f \in L^1(\mathbb{R}) $. et $\omega \in \mathbb{R}$
La transformée de Fourier de $f$ est définie par :
$$
TF(f)(\omega) = \hat{f}(\omega) = \int_{\mathbb{R}} f(t) e^{-2i\pi\omega t}dt
$$
Ici, on passe du domaine **temporel** au domaine **fréquentiel**.

En posant  la notation $e_\omega = e^{2i\pi\omega t}$, On retrouve alors la forme suivant exprimée avec le produit scalaire précédemment défini:
$$
\begin{align}
\hat{f}(\omega) =& <f, e_\omega> \\
=& \int_{\mathbb{R}} f(t) \overline{e^{2i\pi\omega t}}dt \\
=& \int_{\mathbb{R}} f(t) e^{-2i\pi\omega t}dt
\end{align}
$$

> *Pourquoi retrouve-t-on le signe $ - $ devant $ 2i\pi \omega t$ ?* 
> La transformée de Fourier utilise le produit scalaire $ <f,e_\omega> $, dans lequel on utilise le **conjugué**.

**<font color=red>Remarque</font>** : $ L^1(\mathbb{R}) $ contient des fonctions discontinues mais on a une condition d'intégrabilité.

$ TF(f)(\omega) $ est bien définie car $$ | < f,e_{\omega} > | \leq \int_{\mathbb{R}}^{} | f(x) e^{-2i\pi \omega x} | \ dx =  \int_{\mathbb{R}}^{}  | f(x) | \ dx \le + \infty $$

donc $ \forall \omega \ | \hat{f}(\omega) | \leq \int_{\mathbb{R}}^{} | f(x) | \ dx $ avec $\omega$ la fréquence en $Hz$

## Propriétés de la TF

* **<font color=red>Linéarité </font>**

  Soit $a,b \in \mathbb{R}$  et  $f,g \in L^1(\mathbb{R}) $
  $$
  TF(af+bg) = \widehat{af+bg} = a\hat{f}+b\hat{g}
  $$

* **démonstration** :
  $$
  \begin{align}
  TF(af+bg) =& <af+bg, e_\omega> \\
  & {\small\text{(par linéarité du produit scalaire hermitien)}} \\
  =& a<f, e_\omega> + b<g, e_\omega> \\
  =& a\hat{f}+b\hat{g} \quad \\
  \end{align}
  $$

  

* **<font color=red>Théorème du retard (Translation temporelle) </font>** 

  Soit $ t_0 \in \mathbb{R} $ et $ f : \mathbb{R} \to \mathbb{C} $. On définit la translation de $f$ par $t_0$ :  $ \tau_a(f)(t) \mapsto f(t-t_0) $
  $$
  \widehat{\tau_a(f)}(\omega) = e^{-2i\pi \omega t_0} \hat{f}(\omega)
  $$

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

  Soit $\omega_0 \in \mathbb{R} $ et $f:\mathbb{R} \to \mathbb{C}$ On pose la notation suivante : $ f_{w_0}(t) \mapsto e^{2i \pi \omega_0 t}f(t)$ 

$$
\widehat{f_{\omega_0}}(\omega) = \tau_{\omega_0}(\hat{f})(\omega) = \hat{f}(\omega-\omega_0)
$$

**Démonstration** : 
$$
\begin{align}
\widehat{f_{\omega_0}} =& \int_{\mathbb{R}} f(t) e^{2i\pi\omega_0 t} e^{-2i\pi \omega t}dt \\
=& \int_{\mathbb{R}} f(t) e^{2i\pi (\omega-\omega_0) t} dt \\
=& \hat{f}(\omega-\omega_0)
\end{align}
$$



* **<font color=red>Dilatation du temps (changement d'echelle)</font>** 

  Soit $ a \in \mathbb{R} $ et $ f : \mathbb{R} \to \mathbb{C} $. On définit la dilatation de $f$ par $a$ :  $ D_a(f)(t) \mapsto f(at) $
  $$
  \widehat{D_a(f)} = \frac{1}{|a|} \hat{f}(\frac{\omega}{a})
  $$

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


- **<font color=red> Passage au conjugué</font>** 

Soit $ f : \mathbb{R} \to \mathbb{C} $
$$
\widehat{\overline{f}(\omega)} = \overline{\hat{f}(-\omega)}
$$
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
