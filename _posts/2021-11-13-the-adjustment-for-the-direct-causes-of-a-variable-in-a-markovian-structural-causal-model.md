---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: The Adjustment For The Direct Causes Of A Variable In A Markovian Structural Causal Model
---
## Introduction
There is a Markovian structural causal model. A variable in the model is intervened on. The effect of this intervention to another variable of the model is to be calculated in terms of the probabilities related with the direct causes or parents of the intervened variable. The theorem 3.2.2 (adjustment for direct causes) which is given on the $73^{rd}$ page of [1] is proven in a more detailed way.
## Intervention
Let $X\_{1}, \dotso , X\_{n}$ be the variables of the Markovian structural causal model. $X\_{i}$ is the $i^{th}$ variable. $x\_{i}$ denotes the value of the variable. The parents or direct causes of $X\_{i}$ are represented by $PA\_{i}$. $pa\_{i}$ stands for the value taken by $PA\_{i}$. The joint distribution expressed by this Markovian structural causal model can be written in terms of the decomposition formula as follows:
\begin{equation}
    p\left(x\_{1} , \dotso , x\_{n}\right)=\prod\_{i=1}^{n} p\left(x\_{i}|pa\_{i}\right)
\end{equation}
The $i^{th}$ variable is intervened on to make sure that its value is $x\_{i}^{\prime}$. It means that in the directed acyclic graph of the model, the edges between $X\_{i}$ and $PA\_{i}$ are pruned. Then, the decomposition formula is updated as follows:
\begin{equation}
    p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \prod\_{j \neq i} p\left(x\_{j}|pa\_{j}\right) & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases}
\end{equation}
$p\left(x\_{i}^{\prime}|pa\_{i}\right)$ does not exist in the decomposition formula. The reason is that the variable $X\_{i}$ is no longer under the influence of its parents. Let the decomposition be multiplied and divided by $p\left(x\_{i}^{\prime}|pa\_{i}\right)$:
\begin{equation}
    p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \prod\_{j \neq i} p\left(x\_{j}|pa\_{j}\right)\frac{p\left(x\_{i}^{\prime}|pa\_{i}\right)}{p\left(x\_{i}^{\prime}|pa\_{i}\right)} & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases} \Rightarrow
\end{equation}
\begin{equation}
    p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \frac{\prod\_{j=1}^{n} p\left(x\_{j}|pa\_{j}\right)}{p\left(x\_{i}^{\prime}|pa\_{i}\right)} & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases} \Rightarrow
\end{equation}
\begin{equation}
    p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \frac{p\left(x\_{1} , \dotso , x\_{n}\right)}{p\left(x\_{i}^{\prime}|pa\_{i}\right)} & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases}
\end{equation}
Another form of the last equation can be obtained by expanding $p\left(x\_{i}^{\prime}|pa\_{i}\right)$:
\begin{equation}
    p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \frac{p\left(x\_{1} , \dotso , x\_{n}\right)}{p\left(x\_{i}^{\prime}|pa\_{i}\right)} & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases} \Rightarrow
\end{equation}
\begin{equation}
    p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \frac{p\left(x\_{1} , \dotso , x\_{n}\right)}{\frac{p\left(x\_{i}^{\prime}, pa\_{i}\right)}{p\left(pa\_{i}\right)}} & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases} \Rightarrow
\end{equation}
\begin{equation}
    p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \frac{p\left(x\_{1} , \dotso , x\_{n}\right)}{p\left(x\_{i}^{\prime},pa\_{i}\right)}p\left(pa\_{i}\right) & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases} \Rightarrow
\end{equation}
\begin{equation}
    p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        p\left(x\_{1} , \dotso , x\_{n}|x\_{i}^{\prime}, pa\_{i}\right)p\left(pa\_{i}\right) & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases}
\end{equation}
Using this form, the intervention's effect on a set of variables $Y$ is to be obtained. $Y$ is a set of variables which is disjoint from $X\_{i} \cup PA\_{i}$. As indicated in [1], the calculation is made by summing $p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)$ over all model variables except $X\_{i} \cup Y$. Now, let this calculation be carried out:
\begin{equation}
    \sum \dotso \sum p\left(x\_{1}, \dotso , x\_{n} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \sum \dotso \sum p\left(x\_{1} , \dotso , x\_{n}|x\_{i}^{\prime}, pa\_{i}\right)p\left(pa\_{i}\right) & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases} \Rightarrow
\end{equation}
\begin{equation}
    p\left(y, x\_{i} | do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \sum\_{pa\_{i}} p\left(y,x\_{i},pa\_{i}|x\_{i}^{\prime}, pa\_{i}\right)p\left(pa\_{i}\right) & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases} \Rightarrow
\end{equation}
\begin{equation}
    p\left(y| do\left(X\_{i}=x\_{i}^{\prime}\right)\right)=\begin{cases}
        \sum\_{pa\_{i}} p\left(y|x\_{i}^{\prime}, pa\_{i}\right)p\left(pa\_{i}\right) & \text{if } x\_{i}=x\_{i}^{\prime} \newline
        0 & \text{if } x\_{i}\neq x\_{i}^{\prime}
    \end{cases}
\end{equation}
The last formula is called the adjustment for direct causes of $X\_{i}$.
## Conclusion
In a Markovian structural causal model, the adjustment formula for the direct causes or parents of a variable has been derived.
## References
[1] Judea Pearl, *Causality: Models, Reasoning and Inference*, Cambridge University Press, 2009.
