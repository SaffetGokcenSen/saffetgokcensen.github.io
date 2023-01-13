---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: The Sequential Backdoor Conditions
---

## Introduction

In this article, it will be explained in detail that sequential backdoor conditions are sufficient for the identification of a plan which is defined to be a collection of sequential or concurrent interventions in <a href="#Pearl">[1]</a>. Some thoughts about the sequential backdoor conditions will be stated.

## The Sequential Backdoor Conditions

Before starting to prove the sufficiency of sequential backdoor conditions for the identification of a plan, some definitions should be made. There is a directed acyclic graph (DAG) $G$ which presents the knowledge or assumptions about the problem in hand. There are four disjoint sets of variables as $X$, $Z$, $U$ and $Y$. They make up the nodes in the DAG $G$. $X$ represents the set of control variables. $Z$ is the set of observed variables or covariates. $U$ is the set of unobserved variables or latent variables. $Y$ is the outcome variable. There is such an order in the control variables that $X_{j}$ is a nondescendant of $X_{k}$ if $j < k$. The outcome $Y$ is a descendant of $X_{n}$ which is the last control variable. $N_{k}$ denotes the set of covariates which are nondescendants of any element in the set $\left \lbrace X_{k}, X_{k+1}, ... , X_{n} \right \rbrace$. The plan whose identification condition is to be analyzed is an ordered set of interventions on the control variables $X_{1}, ... , X_{n}$. The plan is represented by $\left \lbrace do\left(x_{1}\right), ..., do\left(x_{n}\right) \right \rbrace$.

The sequential backdoor conditions are stated in the following theorem given on the page 123 of <a href="#Pearl">[1]</a>:

The probability $p\left(y|do\left(x_{1}\right), ..., do\left(x_{n}\right)\right)$ is identifiable if, for every $1 \leq k \leq n$, there exists a set $Z_{k}$ of covariates satisfying the following (sequential backdoor) conditions:
\begin{equation}
    Z_{k} \subseteq N_{k}
    \label{firstCond}
\end{equation}
(i.e., $Z_{k}$ consists of nondescendants of $\left\lbrace X_{k}, X_{k+1},..., X_{n} \right \rbrace$) and
\begin{equation}
    Y \text{ d-sep } X_{k}|X_{1},..., X_{k-1}, Z_{1}, Z_{2},...,Z_{k} \text{ in } G_{\underline{X}\_{k}, \overline{X}\_{k+1},...,\overline{X}_{n}}
    \label{secondCond}
\end{equation}

When these conditions are satisfied, the effect of the plan is given by
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=\sum_{z_{1},...,z_{n}}p\left(y|z_{1},...,z_{n}, x_{1},...x_{n}\right) \times \prod_{k=1}^{n}p\left(z_{k}|z_{1},...,z_{k-1},x_{1},...,x_{k-1}\right)
\end{equation}

Let this theorem be proven. The proof follows the one given in <a href="#Pearl">[1]</a>. There will be a little more explanation compared to the original. 

The first equality to be used in the proof is as follows:
\begin{equation}
    p\left(z_{k}|z_{1},...,z_{k-1},x_{1},...,x_{k-1},do\left(x_{k}\right),do\left(x_{k+1}\right),...,do\left(x_{n}\right)\right)=p\left(z_{k}|z_{1},...,z_{k-1},x_{1},...,x_{k-1}\right)
    \label{assistRel1}
\end{equation}
This equality is about removing interventions. According to the third rule of do-calculus, the following condition must be satisfied for the removal to be possible:
\begin{equation}
    \left (Z_{k} \text{ d-sep } \left \lbrace X_{k}, ...,X_{n}\right \rbrace \big | Z_{1}, ..., Z_{k-1}, X_{1}, ..., X_{k-1} \right ) \text{ in } G_{\overline{\left \lbrace X_{k}, ...,X_{n}\right \rbrace \left(Z_{1}, ..., Z_{k-1}, X_{1}, ..., X_{k-1}\right)}}
    \label{removal}
\end{equation}
$\left \lbrace X_{k}, ...,X_{n}\right \rbrace \left(Z_{1}, ..., Z_{k-1}, X_{1}, ..., X_{k-1}\right)$ represents the elements of $\left \lbrace X_{k}, ...,X_{n}\right \rbrace$ which are not ancestors of any nodes in $\left \lbrace Z_{1}, ..., Z_{k-1}, X_{1}, ..., X_{k-1}\right \rbrace$. According to the condition given in the equation (\ref{firstCond}), $Z_{k}$ consists of nodes which are at the same level with or above any node in $\left\lbrace X_{k},..., X_{n} \right \rbrace$ in the DAG $G$. Therefore, $\left \lbrace X_{k}, ...,X_{n}\right \rbrace$ cannot be ancestors of any of $\left \lbrace Z_{1}, ..., Z_{k-1}\right \rbrace$. Due to the order in the control variables, $\left\lbrace X_{k},..., X_{n} \right \rbrace$ cannot be ancestors of any node in $\left \lbrace X_{1}, ..., X_{k-1}\right \rbrace$. Hence, no node in $\left \lbrace X_{k}, ...,X_{n}\right \rbrace$ can be an ancestor of any node in $\left \lbrace Z_{1}, ..., Z_{k-1}, X_{1}, ..., X_{k-1}\right \rbrace$. Then:
\begin{equation}
    \left \lbrace X_{k}, ...,X_{n}\right \rbrace \left(Z_{1}, ..., Z_{k-1}, X_{1}, ..., X_{k-1}\right)=\left \lbrace X_{k}, ...,X_{n}\right \rbrace
\end{equation}
The condition in the equation (\ref{removal}) can now be updated as follows:
\begin{equation}
    \left (Z_{k} \text{ d-sep } \left \lbrace X_{k}, ...,X_{n}\right \rbrace \big | Z_{1}, ..., Z_{k-1}, X_{1}, ..., X_{k-1} \right ) \text{ in } G_{\overline{\left \lbrace X_{k}, ...,X_{n}\right \rbrace }}
\end{equation}
Due to the first sequential backdoor condition in the equation (\ref{firstCond}), $Z_{k}$ consists of nondescendants of $\left\lbrace X_{k}, ..., X_{n} \right \rbrace$. This means that no arrow can exit from any element in $\left\lbrace X_{k}, ..., X_{n} \right \rbrace$ and enter $Z_{k}$. No path can exist from $Z_{k}$ to $\left\lbrace X_{k}, ..., X_{n} \right \rbrace$ in $G_{\overline{\left \lbrace X_{k}, ...,X_{n}\right \rbrace }}$. Therefore, $Z_{k}$ and $\left\lbrace X_{k}, ..., X_{n} \right \rbrace$ are d-separated in $G_{\overline{\left \lbrace X_{k}, ...,X_{n}\right \rbrace }}$. The equality in the equation (\ref{assistRel1}) has been shown to be valid.

The second equality to be used in the proof is as follows:
\begin{equation}
    p\left(y|z_{1}, ... , z_{k}, x_{1}, ... , x_{k-1}, do\left(x_{k}\right), do\left(x_{k+1}\right), ... , do\left(x_{n}\right)\right)=p\left(y|z_{1}, ... , z_{k}, x_{1}, ... , x_{k-1}, x_{k}, do\left(x_{k+1}\right), ... , do\left(x_{n}\right)\right)
    \label{assistRel2}
\end{equation}
So, this is related with replacing the intervention on the control variable $X_{k}$ with observing $X_{k}$. For this removal to be possible, the following condition must be satisfied:
\begin{equation}
    \left (Y \text{ d-sep } X_{k} \big | Z_{1}, ..., Z_{k}, X_{1}, ...,X_{k-1}, X_{k+1}, ..., X_{n} \right ) \text{ in } G_{\underline{X}\_{k},\overline{X}\_{k+1},...,\overline{X}_{n}}
    \label{proofEq2}
\end{equation}

This condition resembles the second sequential backdoor condition in the equation (\ref{secondCond}). For the sake of ease, let the second sequential backdoor condition be rewritten:
\begin{equation}
    \left ( Y \text{ d-sep } X_{k}|X_{1},..., X_{k-1}, Z_{1}, Z_{2},...,Z_{k} \right ) \text{ in } G_{\underline{X}\_{k}, \overline{X}\_{k+1},...,\overline{X}_{n}}
\end{equation}

The second sequential backdoor condition contains additional conditioning var\-i\-ables $X_{k+1},...,X_{n}$. Does the second sequential backdoor condition imply the condition in the equation (\ref{proofEq2})? The additional conditioning variables do not have any incoming arrows as implied by the DAG for which they are defined. Therefore, the existence or nonexistence of the additional conditioning variables do not matter. That's the mean, the second sequential backdoor condition implies the condition in the equation (\ref{proofEq2}). Hence, the equality in the equation (\ref{assistRel2}) is valid.

Let the causal effect of the sequential interventions on the control variables $X_{1},...,X_{n}$ be calculated. This causal effect is represented by the quantity
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right).
\end{equation}
Using the total probability law, the sought causal effect can be expanded as follows:
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)= \sum_{z_{1}} p\left(y, z_{1}|do\left(x_{1}\right),...,do\left(x_{n}\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=\sum_{z_{1}} \frac{p\left(y, z_{1}|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)}{p\left(z_{1}|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)}p\left(z_{1}|do\left(x_{1}\right),...,do\left(x_{n}\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=\sum_{z_{1}}p\left(y| z_{1},do\left(x_{1}\right),...,do\left(x_{n}\right)\right)p\left(z_{1}|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)
    \label{expansion1}
\end{equation}
Using the equality in (\ref{assistRel1}) with $k=1$ implies the following:
\begin{equation}
    p\left(z_{1}|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=p\left(z_{1}\right)
\end{equation}
Using the equality in (\ref{assistRel2}) with $k=1$ implies the following:
\begin{equation}
    p\left(y| z_{1}, do\left(x_{1}\right), ...,do\left(x_{n}\right)\right)=p\left(y|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right)
\end{equation}
Putting these results into the expansion in the equation (\ref{expansion1}) yields the following:
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=\sum_{z_{1}}p\left(y|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right)p\left(z_{1}\right)
\end{equation}
Let the second covariate $Z_{2}$ be included in the causal effect calculation as follows:
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=\sum_{z_{1}}p\left(y|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right)p\left(z_{1}\right)
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=\sum_{z_{1}} \left (\sum_{z_{2}}p\left(y,z_{2}|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right)\right ) p\left(z_{1}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=\sum_{z_{1}} \sum_{z_{2}}p\left(y,z_{2}|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right) p\left(z_{1}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} \frac{p\left(y,z_{2}|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right)}{p\left(z_{2}|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right)}p\left(z_{2}|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right) p\left(z_{1}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} p\left(y|z_{1}, z_{2},x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right)p\left(z_{2}|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right) p\left(z_{1}\right)
    \label{expansion2}
\end{equation}
Using the equality in (\ref{assistRel1}) with $k=2$ implies the following:
\begin{equation}
    p\left(z_{2}|z_{1}, x_{1}, do\left(x_{2}\right),...,do\left(x_{n}\right)\right)=p\left(z_{2}|z_{1},x_{1}\right)
\end{equation}
Using the equality in (\ref{assistRel2}) with $k=2$ implies the following:
\begin{equation}
    p\left(y|z_{1},z_{2},x_{1},do\left(x_{2}\right),...,do\left(x_{n}\right)\right)=p\left(y|z_{1}, z_{2},x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)
\end{equation}
Putting these results into the expansion in the equation (\ref{expansion2}) yields the following:
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} p\left(y|z_{1}, z_{2},x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)p\left(z_{2}|z_{1},x_{1}\right) p\left(z_{1}\right)
\end{equation}
Let the third covariate $Z_{3}$ be included in the causal effect calculation as in the following:
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} p\left(y|z_{1}, z_{2},x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)p\left(z_{2}|z_{1},x_{1}\right) p\left(z_{1}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} \left (\sum_{z_{3}} p\left(y,z_{3}|z_{1}, z_{2},x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)\right )p\left(z_{2}|z_{1},x_{1}\right) p\left(z_{1}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} \sum_{z_{3}} p\left(y,z_{3}|z_{1}, z_{2},x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)p\left(z_{2}|z_{1},x_{1}\right) p\left(z_{1}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} \sum_{z_{3}} \frac{p\left(y,z_{3}|z_{1}, z_{2},x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)}{p\left(z_{3}|z_{1}, z_{2},x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)}p\left(z_{3}|z_{1}, z_{2},x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)p\left(z_{2}|z_{1},x_{1}\right) p\left(z_{1}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} \sum_{z_{3}} p\left(y|z_{1}, z_{2},z_{3}, x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)p\left(z_{3}|z_{1}, z_{2},x_{1}, x_{2}, do\left(x_{3}\right), ...,do\left(x_{n}\right)\right)p\left(z_{2}|z_{1},x_{1}\right) p\left(z_{1}\right)
    \label{expansion3}
\end{equation}
Using the equality in (\ref{assistRel1}) with $k=3$ implies the following:
\begin{equation}
    p\left(z_{3}|z_{1}, z_{2}, x_{1}, x_{2}, do\left(x_{3}\right),...,do\left(x_{n}\right)\right)=p\left(z_{3}|z_{1}, z_{2},x_{1}, x_{2}\right)
\end{equation}
Using the equality in (\ref{assistRel2}) with $k=3$ implies the following:
\begin{equation}
    p\left(y|z_{1},z_{2},z_{3},x_{1},x_{2},do\left(x_{3}\right),...,do\left(x_{n}\right)\right)=p\left(y|z_{1},z_{2},z_{3},x_{1},x_{2},x_{3}, do\left(x_{4}\right),...,do\left(x_{n}\right)\right)
\end{equation}
Putting these results into the expansion in the equation (\ref{expansion3}) yields the following:
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} \sum_{z_{3}} p\left(y|z_{1},z_{2},z_{3},x_{1},x_{2},x_{3}, do\left(x_{4}\right),...,do\left(x_{n}\right)\right)p\left(z_{3}|z_{1}, z_{2},x_{1}, x_{2}\right)p\left(z_{2}|z_{1},x_{1}\right) p\left(z_{1}\right)
\end{equation}
Continuing with this procedure by including the rest of the covariates which are $Z_{4},...,Z_{n}$ in the causal effect calculation, the following expression is obtained:
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} \sum_{z_{3}} ... \sum_{z_{n}} p\left(y|z_{1},...,z_{n},x_{1},...,x_{n}\right)\times 
    p\left(z_{n}|z_{1}, z_{2},...,z_{n-1},x_{1}, x_{2},...,x_{n-1}\right)\times ... \times p\left(z_{3}|z_{1}, z_{2},x_{1}, x_{2}\right)\times p\left(z_{2}|z_{1},x_{1}\right) \times p\left(z_{1}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x_{1}\right),...,do\left(x_{n}\right)\right)=
    \sum_{z_{1}} \sum_{z_{2}} \sum_{z_{3}} ... \sum_{z_{n}} p\left(y|z_{1},...,z_{n},x_{1},...,x_{n}\right)\prod_{i=1}^{n}p\left(z_{i}|z_{1},...,z_{i-1},x_{1},...,x_{i-1}\right)
    \label{theResult}
\end{equation}
So, when the sequential backdoor conditions are satisfied, the causal effect of the plan is identifiable and given by the expression in the equation (\ref{theResult}).

## Some Thoughts On The Sequential Back\-door Conditions

The interventions are made in an ordered fashion in time. The first sequential backdoor condition which is 
\begin{equation}
    Z_{k} \subseteq N_{k}
\end{equation}
means that the $k^{th}$ intervention $X_{k}$ and later interventions are made after the observations $Z_{1}, ..., Z_{k-1}$. The second backdoor condition which is 
\begin{equation}
    Y \text{ d-sep } X_{k}|X_{1},..., X_{k-1}, Z_{1}, Z_{2},...,Z_{k} \text{ in } G_{\underline{X}\_{k}, \overline{X}\_{k+1},...,\overline{X}_{n}}
\end{equation}

means that there are no backdoors from $Y$ to $X_{k}$ and the causal effect of $X_{k}$ on $Y$ is not spoilt by spurious associations between $X_{k}$ and $Y$. One may ask the question if there is a need for such a condition since the interventions are ordered in time. One may think that in $G\_{\underline{X}\_{k}, \overline{X}\_{k+1},...,\overline{X}\_{n}}$, exits from $X_{k}$ and entries to $X_{k+1}, ..., X_{n}$ are cut off; hence, there can be no backdoor paths from $X_{k}$ to $Y$. However, there are also the unobserved variables. There can still be backdoor paths through them. So, the condition is needed.

## Conclusion

The sequential backdoor conditions have been shown to be sufficient for the identification of a plan, i.e. determining the causal effect of a plan on an output variable. Some thoughts on the sequential backdoor conditions have been stated.

## References

<span id="Pearl"> [1] Judea Pearl, *Causality: Models, Reasoning and Inference*, Cambridge University Press, 2009.</span>
