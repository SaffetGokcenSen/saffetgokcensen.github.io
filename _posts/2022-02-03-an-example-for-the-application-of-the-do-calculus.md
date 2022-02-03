---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: An Example For The Application Of The Do-calculus
---
## Introduction
The computation of a causal effect by means of the do-calculus is elaborated on. The causal effect computation to be elaborated on is the fifth task on page 88 of [1].
## The Causal Effect Computation
There is a simple causal model whose directed acyclic graph (DAG) is given in the Figure 1.
<figure>
   <img src="/assets/orig_dag.png" style="max-width: 400px;">
   <figcaption>Figure 1. The DAG of the causal model.</figcaption>
</figure>
As can be seen from the DAG $G$, there are four variables in the model: $U$, $X$, $Y$ and $Z$. $U$ is unobserved. The causal effect to be computed is $p\left(x,y|do\left(z\right)\right)$. This conditional joint probability can be written as follows using the Bayes rule:
\begin{equation}
    p\left(x,y|do\left(z\right)\right)=p\left(x|y,do\left(z\right)\right)p\left(y|do\left(z\right)\right)
\end{equation}
Let $p\left(x|y,do\left(z\right)\right)$ be attempted for computation. Can the intervention $do \left(z\right)$ be replaced with the observation $Z=z$?
\begin{equation}
    p\left(x|y,do\left(z\right)\right) \stackrel{?}{=} p\left(x|y,z\right)
\end{equation}
It must be examined if $\left(X \perp \perp Z | Y\right)$ in $G\_{\underline{Z}}$. $G\_{\underline{Z}}$ is a modified version of the original DAG $G$. The arrows going out of $Z$ are removed from $G$ to obtain $G\_{\underline{Z}}$. $G\_{\underline{Z}}$ is shown in the Figure 2.
<figure>
   <img src="/assets/dag_Z_underline.png" style="max-width: 400px;">
   <figcaption>Figure 2. The graph $G_{\underline{Z}}$.</figcaption>
</figure>
As can easily be detected from $G\_{\underline{Z}}$, $X$ and $Z$ are conditionally d-connected given $Y$ through the path $X \rightarrow Z$. Therefore, the intervention on $Z$ cannot be replaced with the observation of $Z$:
\begin{equation}
    p\left(x|y,do\left(z\right)\right) \neq p\left(x|y,z\right)
\end{equation}

Can the intervention on $Z$ be removed?
\begin{equation}
    p\left(x|y,do\left(z\right)\right) \stackrel{?}{=} p\left(x|y\right)
\end{equation}
It must be scrutinized if $\left(X \perp \perp Z | Y\right)$ in $G\_{\overline{Z\left(Y\right)}}$. $G\_{\overline{Z\left(Y\right)}}$ is a modified version of $G$. The arrows going into $Z$ variable(s) which are not ancestor(s) of $Y$ are removed to get $G\_{\overline{Z\left(Y\right)}}$. $Z$ is an ancestor of $Y$. Hence, $G\_{\overline{Z\left(Y\right)}}$ is the same as $G$. $X$ and $Z$ are conditionally d-connected given $Y$ in $G$ through either the path $X \rightarrow Z$ or the path $X \leftarrow U \rightarrow Y \leftarrow Z$. So, the intervention on $Z$ cannot be removed:
\begin{equation}
    p\left(x|y,do\left(z\right)\right) \neq p\left(x|y\right)
\end{equation}

A way into a solution may be obtained by replacing the observation of $Y$ with the intervention on $Y$. Can the observation of $Y$ be replaced with the intervention on $Y$?
\begin{equation}
    p\left(x|y,do\left(z\right)\right) \stackrel{?}{=} p\left(x|do\left(y\right),do\left(z\right)\right)
\end{equation}
It must be studied if $X \perp \perp Y$ in $G\_{\overline{Z}\underline{Y}}$. $G\_{\overline{Z}\underline{Y}}$ can be obtained from $G$ by removing the arrows entering $Z$ and the arrows going out of $Y$. $G\_{\overline{Z}\underline{Y}}$ is displayed in the Figure 3.
<figure>
   <img src="/assets/dag_Z_overline_Y_underline.png" style="max-width: 400px;">
   <figcaption>Figure 3. The graph $G_{\overline{Z}\underline{Y}}$ or the graph $G_{\overline{Z}}$.</figcaption>
</figure>
The graph $G\_{\overline{Z}\underline{Y}}$ implies that $X$ and $Y$ are d-connected through the path $X \leftarrow U \rightarrow Y$. This means that the observation of $Y$ cannot be replaced by the intervention on $Y$:
\begin{equation}
    p\left(x|y,do\left(z\right)\right) \neq p\left(x|do\left(y\right),do\left(z\right)\right)
\end{equation}

All of the three attempts to initiate a solution by means of the do-calculus rules have not been successful, which means that $p\left(x|y,do\left(z\right)\right)$ cannot be computed for G shown in the Figure 1. Then, the conditional joint probability $p\left(x,y|do\left(z\right)\right)$ must be decomposed as follows:
\begin{equation}
    p\left(x,y|do\left(z\right)\right)=p\left(y|x,do\left(z\right)\right)p\left(x|do\left(z\right)\right)
    \label{solvable\_decomposition}
\end{equation}
Let $p\left(y|x,do\left(z\right)\right)$ be attempted for computation. Can the intervention on $Z$ be replaced by the observation of $Z$?
\begin{equation}
    p\left(y|x,do\left(z\right)\right) \stackrel{?}{=} p\left(y|x,z\right)
\end{equation}
Is $\left(Y \perp \perp Z | X \right)$ in $G\_{\underline{Z}}$? Yes. From $G\_{\underline{Z}}$ shown in the Figure 2, it can be detected that $Y$ is conditionally d-separated from Z given $X$ since the path $Z \leftarrow X \leftarrow U \rightarrow Y$ is blocked by $X$. Then, the intervention on $Z$ can be replaced by the observation of $Z$:
\begin{equation}
    p\left(y|x,do\left(z\right)\right) = p\left(y|x,z\right)
    \label{first\_part}
\end{equation}
$p\left(y|x,do\left(z\right)\right)$ has been computed. Now, it is the turn of $p\left(x|do\left(z\right)\right)$. Can the intervention on $Z$ be replaced by the observation of $Z$?
\begin{equation}
    p\left(x|do\left(z\right)\right) \stackrel{?}{=} p\left(x|z\right)
\end{equation}
Is $X \perp \perp Z$ in $G\_{\underline{Z}}$? No. From the Figure 2, it can be seen that $X$ and $Z$ are d-connected through the path $X \rightarrow Z$.

Can the intervention on $Z$ be removed?
\begin{equation}
    p\left(x|do\left(z\right)\right) \stackrel{?}{=} p\left(x\right)
\end{equation}
Is $X \perp \perp Z$ in $G\_{\overline{Z}}$? Yes. From the Figure 3, it can be seen that $X$ and $Z$ are d-separated since the path $X \leftarrow U \rightarrow Y \leftarrow Z$ is blocked by the collision node $Y$. Hence, the intervention can be removed to yield the following equality:
\begin{equation}
    p\left(x|do\left(z\right)\right) = p\left(x\right)
    \label{second\_part}
\end{equation}

Now, the computation result of the causal effect $p\left(x,y|do\left(z\right)\right)$ can be written using the equations (\ref{solvable\_decomposition}), (\ref{first\_part}) and (\ref{second\_part}) as follows:
\begin{equation}
    p\left(x,y|do\left(z\right)\right)=p\left(y|x,z\right)p\left(x\right)
\end{equation}
## Conclusion
The computation of the causal effect $p\left(x,y|do\left(z\right)\right)$ for a causal model whose DAG is shown in the Figure 1 has been elaborated on. This problem is the fifth task on page 88 of [1].
## References
Judea Pearl, Causality: Models, Reasoning and Inference, Cambridge University Press, 2009.
