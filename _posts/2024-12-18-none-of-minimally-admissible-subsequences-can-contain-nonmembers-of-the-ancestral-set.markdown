---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: None Of Minimally Admissible Subsequences Can Contain Nonmembers Of The Ancestral Set 
---
## Introduction 
In this article, an important fact related with the proof of a theorem is 
proven. The theorem is about the existence of an admissible sequence within the 
context of the sequential backdoor criterion. The theorem states the 
following: 

*If there exists an admissible sequence $Z_{1}^{\*}, \ldots , Z_{n}^{\*}$, 
then for every minimally admissible subsequence $Z_{1}, \ldots , Z_{k-1}$ of 
covariates, there is an admissible set $Z_{k}$.*

The important fact related with this theorem is as follows:

*The covariates in the minimally admissible sequence $Z_{1}, \ldots , Z\_{k-1}, 
Z\_{k}$ cannot contain a nonmember of $A\_{k}$ where $A\_{k}$ is the ancestral 
set of $\left(X\_{k}, Y\right)$ in $G\_{k}$ which is $G\_{\underline{X}\_{k}, 
\overline{X}\_{k+1}, \ldots , \overline{X}\_{n}}$.*

This important fact was already proven in the article 
<a href="#theArticle">[1]</a>. However, in my opinion, this proof is not clear 
enough and redundantly long without explanations. That's why I want to elaborate 
on it. 

## The Proof 
If $Z_{1}, \ldots , Z_{k-1}, Z_{k}$ is a minimally admissible sequence then 
$Z_{k} \subseteq N_{k}$ and 
\begin{equation} 
\left(Y \perp \\!\\!\\! \perp X_{k} | X_{1}, \ldots , X_{k-1}, Z_{1}, \ldots , 
Z_{k-1}, Z_{k}\right ) \text{ in } G_{k} 
\label{admissibility2}
\end{equation} 
where 
\begin{equation} 
G_{k} = G\_{\underline{X}\_{k}, \overline{X}\_{k+1}, \ldots , \overline{X}\_{n}}
\end{equation} 
and $N_{k}$ is the set of covariates which are nondescendants of $X_{k}$. The 
minimality constraint requires the covariates $Z_{1}, \ldots , Z_{k-1}, Z_{k}$ 
to be minimal. The fact that the covariates in the minimally admissible 
sequence $Z_{1}, \ldots , Z\_{k-1}, Z\_{k}$ cannot contain a nonmember of 
$A\_{k}$ in $G_{k}$ is to be proven using contradiction. As a contradiction, it is assumed 
that $Z_{i}$ $\left(1 \leq i \leq k\right)$  contains nonmembers of $A_{k}$. Let the nonmembers of $A_{k}$ be 
removed from $Z_{i}$. Removing the nonmembers of $A_{k}$ from $Z_{i}$ must not 
break the conditional independence in the equation \eqref{admissibility2}. The 
reason is the second equation \eqref{lemma12} of the lemma 1 in 
<a href="#theArticle">[1]</a>. Lemma 1 is given as follows: 

*For any DAG $G$ and any two disjoint subsets of nodes $X$ and $Y$, let the 
ancestor-set of $\left(X,Y\right)$, denoted $A\left(X,Y\right)$, be the set of 
nodes which have a descendant in either $X$ or $Y$. The following two 
separation conditions hold for any sets of nodes $W$ and $Z$: 
\begin{equation} 
\left(Y \perp \\!\\!\\! \perp X | Z, W \cap A\left(X,Y\right)\right)_{G} 
\text{ whenever } \left(Y \perp \\!\\!\\! \perp X|Z\right)_{G} 
\label{lemma11}
\end{equation}
\begin{equation}
\left(Y \perp \\!\\!\\! \perp X|W\cap A\left(X,Y\right) \right)_{G} 
\text{ whenever } \left(Y \perp \\!\\!\\! \perp X|W\right)_{G} 
\label{lemma12}
\end{equation}*

The second equation \eqref{lemma12} of this lemma states that removing nonmembers of the ancestors from 
the conditioning set does not harm conditional independence. The proof of this 
lemma is elaborated on in <a href="#lemma1">[2]</a>. Let the form of $Z_{i}$ 
with nonmembers of $A_{k}$ removed be denoted by $Z_{i}^{\prime}$. Then, the 
following conditional dependence is known to hold due to \eqref{lemma12}: 
\begin{equation} 
\left(Y \perp \\!\\!\\! \perp X_{k} | X_{1}, \ldots , X_{k-1}, Z_{1}, \ldots , 
Z_{i}^{\prime}, \ldots , Z_{k-1}, Z_{k}\right ) \text{ in } G_{k} 
\label{admissibility3}
\end{equation} 
In the equation \eqref{admissibility3}, $Z_{i}$ in the conditioning set can be 
seen to have been replaced with $Z_{i}^{\prime}$ which is smaller than $Z_{i}$. 
Then, $Z_{i}$ is not minimal. This is a contradiction. This contradiction has 
been caused by the assumption that $Z_{i}$ contains nonmembers of $A_{k}$. So, 
it has been proven by contradiction that $Z_{i}$ $\left(1\leq i \leq k\right)$ does not contain nonmembers of 
$A_{k}$. 

## Conclusion 
The proof of the fact that none of minimally admissible subsequences can 
contain nonmembers of the ancestral set has been elaborated on.

## References 

<span id="theArticle"> [1] Judea Pearl and James Robins. Probabilistic evaluation of sequential plans from causal models with hidden variables. In Proceedings of the Eleventh Conference on Uncertainty in Artificial Intelligence, pages 444-453, 1995.</span> 

<span id="lemma1"> [2] [https://saffetgokcensen.github.io/blog/2024/08/29/conditioning-on-ancestors-does-not-harm-d-separability](https://saffetgokcensen.github.io/blog/2024/08/29/conditioning-on-ancestors-does-not-harm-d-separability)</span>
