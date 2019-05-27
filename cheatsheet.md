---
title: "Grammar Cheatsheet"
author: [ ]
date: "2019"
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

# Reduce a GCL 

Dada una gramática  $G = (N, T, S, P)$:

- Un símbolo útil $\in N \cup T$ es aquel:
    - $X \in N \cup T$ accesible si: $S \Rightarrow^* \alpha X \beta$
    - $X \in N$ co-accesible si: $X \Rightarrow^* \omega , \omega \in T^*$

 Algorithm for:

## GCL is finite

## GCL is empty

## A word belongs to L(G)

### CYK

### Brute force

# Normal Forms

## Chomsky

## Greibach

# LL(k) Grammars

# GCL to APDN

# APDN to GCL
