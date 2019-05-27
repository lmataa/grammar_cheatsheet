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

Dada una gramática  $G = (N, T, S, P)$:

- Un símbolo útil $\in N \cup T$ es aquel:
    - $X \in N \cup T$ accesible si: $S \Rightarrow^* \alpha X \beta$
    - $X \in N$ co-accesible si: $X \Rightarrow^* \omega , \omega \in T^*$

- El orden importa, primero calcular co-accesibles y luego accesibles.

**Algoritmo para calcular símbolos co-accesibles**

Símbolos co-accesibles:
$S_{co} = \{A \in N \mid A \rightarrow \alpha, \alpha \in T^* \}$
  
$S_{co_i+1} = S_[co_i] \{ A \in N \mid A \rightarrow \alpha \in P, \alpha \in (S_[co_i]\cup T)^* \}$

*STOP WHEN*: $S_{co_i} = S_{co_i+1}$

**Algoritmo para calcular símbolos accesibles**

Se construye un grafo: 

- Los nodos son símbolos(dependencias)
- $X\rightarrow Y$  si  $X\rightarrow \alpha Y \beta \in P$

X es accesible si $\exists$ un camino de S hasta X.

<<<<<<< HEAD
# CFG is finite
=======
# Algorithm for:

Given a CFG ...

## CFG is finite
>>>>>>> refs/remotes/origin/master

1. Reduce the grammar.
2. Transform into CNF.
3. Look for loops in the dependency graph.

# CFG is empty

1. Calculate co-accesible symbols.
2. If  $S \in S_c \rightarrow L(G) \neq \emptyset$ else $L(G) = \emptyset$

# A word belongs to L(G)

# CYK

# Brute force

# Chomsky

La CNF es una gramatica del tipo:

1. $A \rightarrow BC$, donde $A,B,$ y $C$, son no-terminales o
2. $A \rightarrow a$ donde $A$ es un no-terminal y $a$ es una terminal
3. Cabe notar que un CNF no tiene simbolos inutiles (se debe reducir antes) ni tampoco tiene producciones $\epsilon$

Los pasos para transformar una CFG a una CNF son:

a. Conseguir que todos los cuerpos de tamano 2 o mas consistan solo de no-terminales.
b. Romper los cuerpos de tamano 3 o superior en cuerpos pequenos para cumplir la condicion anterior.

ejemplo:

\begin{figure}[!h]
    \centering
    \includegraphics[width=100mm]{./captures/CFG_CNF_1.png}
    \label{fig:label}
\end{figure}

\begin{figure}[!h]
    \centering
    \includegraphics[width=100mm]{./captures/CFG_CNF_2.png}
    \label{fig:label}
\end{figure}

\newpage

# Greibach

$S \rightarrow \lambda$ S don't appears in the right member of the same rule.

$A \rightarrow a \alpha, A \in N, a \in T, \alpha \in N^*$ 

1. $G \rightarrow G \prime \mid G \prime is in CNF$
2. $G \prime \rightarrow G \prime \prime in GNF$

- 2.1 Order the non terminals (ex: S<A<B):
    
    $A_1 \leftrightarrow S$
      
    $A_2 \leftrightarrow A$
      
    $A_2 \leftrightarrow B$

- 2.2 Every rule must be in the form of:

    $A_i \rightarrow A_j \alpha, j>i$

- 2.3 In the case that a rule is not in that form:

    ex: $A_2 \rightarrow A_1 A_3$

    Replace $A_1$ with its right members.

    ex: $A_1 \rightarrow A_2 A_3 \mid A_2 A_2$

    Replacing: $A_2 \rightarrow A_2 A_3 A_3 \mid A_2 A_2 A_3$ (Recursivity to the left)


# PDA

**Deterministic PDA**

$PDA = (Q, \Sigma, \Gamma, \delta, q_0, Z_0, F)$ is deterministic if:

1. $\mid \delta(q,a,A)\mid \leq 1, \forall q \in Q, a \in \Sigma, A \in \Gamma$

2. $\delta(q, \lambda, A) \neq \emptyset, \delta(q,a,A)=\emptyset \forall A \in \Sigma$

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

    