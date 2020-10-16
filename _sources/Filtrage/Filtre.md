# Filtre

> Un filtre est un système. Le filtrage correspond à sélectionner certaines fréquences du signal.

## Sommaire

[**Introduction**](#Introduction)

On fait passer une convolution sur le signal pour sélectionner un contenu fréquentiel.

**Exemple du filtre passe-bas :**

$$s_{[0,1]^2 \to \mathbb{R}} \sim\hat{s} * \Pi_{[-Bc,Bc]}$$

$TF^-1(\hat{s} * \Pi_{[-Bc,Bc]^2})$ est le signal filtré passe-bas.

**<font color="red">Remarque</font> :**  Quel est le coût de la convolution discrète ? $\to$ à priori, $N^2$

En fait, pour calculer la convolution, on peut utiliser la **FFT**.

$$s \ast h = FFT^{-1}(FFT(s) .FFT(h))$$

