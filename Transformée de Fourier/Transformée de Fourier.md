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

**<font color=red>Produit hermitien </font>** sur l'espace des signaux d'énergie finie : $$ <f,g> \ = \int_{\mathbb{R}}^{} f(x)\ \overline{g(x)} \ dx $$
avec $\overline{a}$ le complexe conjugué de a et a $\in \mathbb{C}$.

$ \left\{  \begin{array}{ll} a = a_{1} + ia_{2} \\ 
\overline{a} = a_1 - ia_2 \end{array} \right. $

**<font color=red>Attention</font>** : On a bien $$ \int_{\mathbb{R}}^{} f(x)\overline{f}(x) \ dx = \int_{\mathbb{R}}^{} |f(x)|^2 \ dx \leq 0 \ \\ \text{et nul ssi} \ f = 0$$

Quelques propriétés sur les scalaires : 
* $ <f,g> = \overline{<g,f>} $
* $ <f+ \lambda h, g> \ = \ <f,g> + \lambda <h,g> $
* $ <f,g + \lambda h> \ = \ <f,g> + \overline{\lambda} <f,h> $

$$ \\ $$

**<font color=red>Définition</font>** : Soit $ f \in L^1(\mathbb{R}) $. La transformée de Fourier de $f$ est définie par :

$$ TF(f)(\omega) = \hat{f}(\omega) = \int_{\mathbb{R}}^{} f(t) e^{-2i\pi \omega t} \ dt \\ 
avec \ \omega \in \mathbb{R} $$


Ici, on passe du domaine **temporel** au domaine **fréquentiel**.



*Pourquoi retrouve-t-on le signe $ - $ devant $ 2i\pi \omega t$ ?* 
La transformée de Fourier utilise le produit scalaire $ <f,e_\omega> $, dans lequel on utilise le **conjugué**.

**<font color=red>Remarque</font>** : $ L^1(\mathbb{R}) $ contient des fonctions discontinues mais on a une condition d'intégrabilité.

$ TF(f)(\omega) $ est bien définie car $$ | < f,e_{\omega} > | \leq \int_{\mathbb{R}}^{} | f(x) e^{-2i\pi \omega x} | \ dx =  \int_{\mathbb{R}}^{}  | f(x) | \ dx \le + \infty $$

donc $ \forall \omega \ | \hat{f}(\omega) | \leq \int_{\mathbb{R}}^{} | f(x) | \ dx $ avec $\omega$ la fréquence en $Hz$

## Propriétés de la TF

* **<font color=red>Linéarité </font>** : $$ TF(af + bg) = aTF(f) + bTF(g) 
\\ avec \ a,b \in \mathbb{R} \ et \ f,g \in L^1(\mathbb{R}) $$



* **<font color=red>Translation </font>** : Soit $ a \in \mathbb{R} $ et $ f : \mathbb{R} \to \mathbb{C} $. On définit la translation de $f$ par $a$ : 
$$ \tau_a(f)(x) \to f(x-a) $$

**Démonstration** : 

$$ \hat{\tau_a(f)} = \int_{\mathbb{R}}^{} \tau_a(f)e^{-2i\pi \omega x} \ dx
\\ = \int_{\mathbb{R}}^{} f(x-a)e^{-2i\pi \omega x} \ dx
\\ \text{On pose} \ u = x-a \ \text{(changement de variable)}
\\ = \int_{\mathbb{R}}^{} f(u)e^{-2i\pi \omega (u+a)} \ d(u+a)
\\ = e^{-2i\pi \omega a} \int_{\mathbb{R}}^{} f(u)e^{-2i\pi \omega u} \ du
\\ = e^{-2i\pi \omega a} \hat{f}(\omega) $$

Soit $\omega_0 \in \mathbb{R} $ alors $ x \to e^{2i \pi \omega_0 x} f(x) = f_{w_0} $

$$ TF(f_{w_0}) = \int_{\mathbb{R}}^{} f(x) e^{2i\pi \omega_0 x} e^{-2i\pi \omega x} \ dx
\\ \int_{\mathbb{R}}^{} f(x) e^{2i\pi (\omega - \omega_0) x} \ dx $$

On a donc $$ \hat{f_{w_0}} = \tau_{w_0}(\hat{f}) $$ qui est la **translation**


* **<font color=red>Dilatation du temps </font>**  : $ D_a(f)(x) = f(ax) $ avec $ a > 0 $
Quelle est la TF $(Da(f))$ ? 

$$ \int_{\mathbb{R}}^{} f(ax) e^{-2i\pi \omega x} \ dx
\\ \text{On pose} \ u = ax
\\ = \int_{\mathbb{R}}^{} f(u) e^{-2i\pi \omega \frac{u}{a}} \ \frac{du}{a}
\\ = \frac{1}{a}\hat{f}(\frac{\omega}{a}) $$

Si $a < 0$ 
$$ TF(D_a(f)) = \frac{1}{| a |} \hat{f}(\frac{\omega}{a}) $$
