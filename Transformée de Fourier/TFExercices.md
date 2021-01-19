## Calculs de transformées de fourrier

Soit $\alpha \in \mathbb{R}^*$

## 1. $\mathbb{r}_\alpha(t) = \Pi(\frac{t}{\alpha})$ :

En sachant que  $\widehat{\Pi}(\omega)=  sinc(\pi\omega)$

et d'après la formule de dilatation du temps  $\widehat{D_a(f)} = \frac{1}{|a|} \hat{f}(\frac{\omega}{a})$ 

On obtient facilement :
$$
\widehat{\mathbb{r}_\alpha}(\omega) =|\alpha| sinc(\pi\omega \alpha)
$$
On obtient alors un **sinus cardinal**. C'est une fonction paire et réelle.



## 2. $x(t) = \frac{sin(\alpha t)}{t}$ :

---

>  Calcul intermédiaire pour l'exemple mais à ne pas refaire nécessaire mais à ne pas refaire.
>  $$
>  \begin{align}
>  \widehat{sinc}(\pi t) &= \int_\mathbb{R} sinc(\pi t) e^{-2i\pi\omega t} dt \\
>  &= \int_\mathbb{R} sinc(\pi t)  (cos(2\pi\omega t) - i.Sin(cos(2\pi\omega t)) dt \\
>  & \text{en remarquant que le produit de deux sinus est impaire} \\
>  &= \int_\mathbb{R} sinc(\pi t)cos(2\pi\omega t) dt \\
>  &= \int_\mathbb{R} \frac{1}{\pi t}sin(\pi t)cos(2\pi\omega t) dt \\
>  & \text{en utiliant l'identitée : } sin(a)cos(b) = \frac{1}{2}(sin(a+b)+sin(a-b)) \\
>  &= \int_\mathbb{R} \frac{1}{2\pi t} [sin(\pi t(1+2\omega)) + sin(\pi t(1-2\omega))] dt \\
>  &=  \frac{1}{2\pi} [ \int_\mathbb{R}\frac{sin(\pi t(1+2\omega))}{t} dt + \int_\mathbb{R}\frac{sin(\pi t(1-2\omega))}{t} ] \\
>  &= \frac{1}{2\pi} [ \int_\mathbb{R}(1+2\omega)\frac{sin(\pi t(1+2\omega))}{t(1+2\omega)} dt + \int_\mathbb{R}(1-2\omega)\frac{sin(\pi t(1-2\omega))}{t(1-2\omega)}dt ] \\
>  & \text{avec le changement de variable  générique : } \int_\mathbb{R} f(ax)dx = \frac{1}{|a|}dy \\
>  &= \frac{1}{2\pi} [ \int_\mathbb{R}\frac{1+2\omega}{|1+2\omega|} \frac{sin(t)}{t}dt + \int_\mathbb{R}\frac{1-2\omega}{|1-2\omega|} \frac{sin(t)}{t}dt ] \\
>  &= \frac{1}{2\pi} (sign(1+2\omega) + sign(1-2\omega)) \int_\mathbb{R}\frac{sin(t)}{t} dt \\
>  & \text{or on sait que} : \int_\mathbb{R}\frac{sin(t)}{t} = \pi \\
>  &= \frac{1\pi}{2\pi} (sign(1+2\omega) + sign(1-2\omega))  \\
>  &= \frac{1}{2} (sign(1+2\omega) + sign(1-2\omega)) \\
>  &= \Pi_{[-\frac{1}{2}, \frac{1}{2}]}(\omega) = \Pi(\omega) \\
>  \end{align}
>  $$
>
>  ---
>
>  ou alors : en sachant que $\widehat{\Pi}(\omega) = sinc(\pi\omega)$  et $\widehat{\widehat f}(t) = f(-t)$
>
>  On à : 
>  $$
>  \begin{align}
>  \widehat{sinc}(\pi t) &= \widehat{\widehat \Pi}(t) \\
>  &= \Pi(-t) \\
>  &= \Pi(t) \\
>  \end{align}
>  $$


$$
\begin{align}
x(t) &= \frac{sin(\alpha t)}{t} \\
&= \alpha\frac{sin(\alpha t)}{\alpha t} \\
&= \alpha.sinc(\alpha t) \\
& \text{en posant : } \alpha = \pi\beta \\
&= \pi\beta.sinc(\pi\beta t) \\
\end{align}
$$

Alors :
$$
\begin{align}
\widehat{x}(t) &= \pi\beta.TF(sinc(\pi\beta t)) \\
& \text{ par dilatation du temps on obtient} \\
&= \pi\beta.\frac{1}{|\beta|} \widehat{sinc(\pi t)}(\frac{\omega}{\beta})) \\
&= \pi.\Pi(\frac{\omega}{\beta}) \\
& \text{ en retournant à } \beta = \frac{\alpha}{\pi}\\
&= \pi.\Pi(\frac{\pi\omega}{\alpha}) \\ 
&= \pi.\Pi_{[-\alpha/2\pi, \alpha/2\pi]}
\end{align}
$$
Vérification WolframAlpha et desmos

![image-20210104164014481](D:\IMAC\IMAC3\S5\révisions signal\sin(at)t.png)


## 3.   $y(t) = \left(\frac{sin(\alpha \beta t)}{\alpha \beta t} \right)^2$

$$
\begin{align}
y(t)  &= \left(\frac{sin(\alpha \beta t)}{\alpha \beta t} \right)^2 \\
&= sinc(\alpha\beta t)^2 \\
& \text{en posant : } \alpha = \pi\gamma \\
&= sinc(\gamma\beta\pi t)^2 \\
\end{align}
$$

$$
\begin{align}
TF(sinc(\gamma\beta\pi t)) &= \frac{1}{|\gamma\beta|} \widehat{sinc(\pi t)}(\frac{\omega}{\gamma\beta})) \\
& \text{ par dilatation du temps} \\
&= \frac{1}{|\gamma\beta|} \Pi(\frac{\omega}{\gamma\beta})\\
& \text{ en retournant à } \gamma = \frac{\alpha}{\pi}\\
&= \frac{\pi}{|\alpha\beta|} \Pi(\frac{\pi\omega}{\alpha\beta})\\
\end{align}
$$

Or: 
$$
\begin{align}
\widehat{y}(t) &= sinc(\gamma\beta\pi t)^2 \\
& \text{ en utilisant la propriété de la convolution :} TF(f.g) = \widehat{f}*\widehat{g} \\
&= \frac{\pi}{|\alpha\beta|^2} \Pi(\frac{\pi\omega}{\alpha\beta}) * \Pi(\frac{\pi\omega}{\alpha\beta}) \\
& \text{ en sachant que : } \Pi(t)*\Pi(t)= \Lambda_{[-1, 1]}(t) \\
& \Lambda_{[-1, 1]}(t) \text{ est la fonction triangulaire de -1 à de 1 et de maximum en 0 = 1} \\
& \frac{\pi}{|\alpha\beta|^2} \Lambda_{[-1, 1]}(\frac{\pi\omega}{\alpha\beta})
\end{align}
$$
