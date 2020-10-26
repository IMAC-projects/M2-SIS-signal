# Compression

> La compression de données consiste à ne conserver que les données pertinentes afin de réduire la taille de stockage.

## Sommaire

[**Introduction**](#Introduction)

[**Échantillonnage**](#Échantillonnage)

[**Quantification**](#Quantification)

## Introduction

Lorsque l’on transporte une image ou un son, il faut passer du format analogique (réel) au format numérique (virtuel). Il faut donc un  conditionnement et un codage. Puis il faut transporter ces informations par un « tunnel », autrement appelé « canal de transmission ».

<img src="http://www.fortisfio.com/wp-content/uploads/2013/02/codage-arrow.png"  
alt="schéma filtres" style="text-align:center;"/>


Types de compression :
- Sans pertes : le signal original peut être récupéré du signal compressé. On exploite uniquement la redondance des données ou utilise une transformation réversible 
- Avec pertes : le signal original ne peut être récupéré du signal compressé. On exploite la redondance des données et la perception humaine

Transmission analogique : le procédé reproduit la forme même du signal que l'on veut transmettre. 
Transmission numérique : on traduit le signal en une suite de bits

## Échantillonnage

Théorème de Shannon

## Quantification

On cherche à convertir un signal échantillonné (dont l'amplitude peut prendre une infinité de valeur) en une séquence de caractères discrets, issus d'un alphabet fini de $N$ caractères.

