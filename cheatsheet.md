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

# Build CFG for a given language

# Reduce a CFG 

# Algorithm for:

## CFG is finite

## CFG is empty

## A word belongs to L(G)

### CYK

### Brute force

# Normal Forms

## Chomsky

## Greibach

# LL(k) Grammars

# CFG to NPDA

For any context-free grammar in Greibach Normal Form we can build an equivalent nondeterministic pushdown automaton. This establishes that an npda is at least as powerful as a cfg.
It will always produce a PDA with **three states**

1. Start state $q_0$ will serve as initialization. 

    \begin{equation}
        (q_0,\lambda,z) \rightarrow \{(q_1,S_z)\}
    \end{equation}    

2. State $q_1$ will contain the actual grammar computation.

    \begin{figure}[!h]
        \centering
        \includegraphics[width=50mm]{./captures/CFG_NPDA_1.png}
    \end{figure}

3. Transition $q_1$ to $q_f$ to accept the string
    
    \begin{equation}
        delta(q_1,\lambda,z) \rightarrow \{(q_f,z)\} 
    \end{equation}

# NPDA to CFG
 
1. Las transiciones del tipo $\delta (q_i,a,A) = (q_j,\lambda)$ se transforman en reglas gramaticas del tipo: 

    \begin{figure}[!h]
        \centering
        \includegraphics[width=50mm]{./captures/NPDA_CFG_1.png}
    \end{figure}

2. Las transiciones del tipo $\delta (q_i,a,A)=(q_j,BC)$ resultan en una multitud de reglas. Una para cada par de estados $q_x,q_y$ en el NPDA, muchas *unreachable* pero las utiles definen la gramatica:

    \begin{figure}[!h]
        \centering
        \includegraphics[width=50mm]{./captures/NPDA_CFG_2.png}
    \end{figure}

    