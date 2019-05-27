---
title: "Grammar Cheatsheet"
author: [ ]
date: "2019"
header-includes: |
    \usepackage{physics}
    \usepackage{amsmath}
    \usepackage{mathtools}
    \mathtoolsset{showonlyrefs}
subtitle: "TLP"
titlepage: "true"
toc: "true"
toc-own-page: "true"
lof : "true"
lof-own-page: "true"
lot: "true"
lot-own-page: "true"
listings-no-page-break: "true"
...

# Build GCL for a given language

# Reduce a CFG 

Dada una gramática  $G = (N, T, S, P)$:

- Un símbolo útil $\in N \cup T$ es aquel:
    - $X \in N \cup T$ accesible si: $S \Rightarrow^* \alpha X \beta$
    - $X \in N$ co-accesible si: $X \Rightarrow^* \omega , \omega \in T^*$

- El orden importa, primero calcular co-accesibles y luego accesibles.

## Algoritmo para calcular símbolos co-accesibles

Símbolos co-accesibles:
$S_{co} = \{A \in N \mid A \rightarrow \alpha, \alpha \in T^* \}$
  
$S_{co_i+1} = S_[co_i] \{ A \in N \mid A \rightarrow \alpha \in P, \alpha \in (S_[co_i]\cup T)^* \}$

**STOP WHEN**: $S_{co_i} = S_{co_i+1}$

## Algoritmo para calcular símbolos accesibles

Se construye un grafo: 

- Los nodos son símbolos(dependencias)
- $X\rightarrow Y$  si  $X\rightarrow \alpha Y \beta \in P$

X es accesible si $\exists$ un camino de S hasta X.

# Algorithm for:

## GCL is finite

## GCL is empty

## A word belongs to L(G)

### CYK

### Brute force

# Normal Forms

## Chomsky

## Greibach

# LL(k) Grammars

# CFG to NPDA

# NPDA to CFG


