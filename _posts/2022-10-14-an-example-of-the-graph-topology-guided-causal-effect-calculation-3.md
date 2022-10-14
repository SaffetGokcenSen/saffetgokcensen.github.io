---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: An Example Of The Graph Topology Guided Causal Effect Calculation 3
---

## Introduction

In this article, a causal effect calculation will be carried out using the graph topology guidance. The causal effect is the causal effect of $X$ on $Y$ in the directed acyclic graph (DAG) given in the Figure 3.8 (g) on the page 92 of <a href="#Pearl">[1]</a>. Its calculation has been explained in detail using the topology guidance of the DAG in the Figure 3.8 (e) in <a href="#myBlog">[2]</a>. In <a href="#myBlog2">[3]</a>, it has been shown that the DAG in the Figure 3.8 (c) can also guide the calculation of the causal effect. In this article, the details and the result of this topology guided calculation is going to be given.

## Topology Guided Causal Effect Calculation

The topology guided causal effect calculation is using the know-how obtained from a DAG while finding a causal effect. If some conditions which have been explained in <a href="#myBlog">[2]</a> and <a href="#myBlog2">[3]</a> are satisfied, then the know-how is applied in another DAG to find the target causal effect. The former is a subgraph of the latter.

## The Calculation Of The Causal Effect

The DAG in which the causal effect of $X$ on $Y$ is to be found is given in the <a href="#topologyGuidedCausalEffectDag1" >Figure 1</a>.
<figure id="topologyGuidedCausalEffectDag1">
   <img src="/assets/graphTopologyGuidedCausalEffectCalculation3/topologyGuidedCausalEffectDag1.png" style="max-width: 600px;">
   <figcaption>Figure 1. The DAG in which the causal effect of $X$ on $Y$ is to be calculated.</figcaption>
</figure>
The unobserved variables are made explicit to get the DAG shown in the <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a>. This DAG will be called $G$ from now on in this article.
<figure id="topologyGuidedCausalEffectDag2">
   <img src="/assets/graphTopologyGuidedCausalEffectCalculation3/topologyGuidedCausalEffectDag2.png" style="max-width: 600px;">
   <figcaption>Figure 2. The unobserved variables are explicitly drawn for the DAG in the <a href="#topologyGuidedCausalEffectDag1" >Figure 1</a>.</figcaption>
</figure>
The DAG which will guide the calculation of $p\left(y|do\left(x\right)\right)$ is shown in the <a href="#topologyGuidedCausalEffectDag3" >Figure 3</a>.
<figure id="topologyGuidedCausalEffectDag3">
   <img src="/assets/graphTopologyGuidedCausalEffectCalculation3/topologyGuidedCausalEffectDag3.png" style="max-width: 200px;">
   <figcaption>Figure 3. The DAG which will guide the calculation of the causal effect.</figcaption>
</figure>
The subgraph of $G$ which is the guiding DAG is shown in red in the <a href="#topologyGuidedCausalEffectDag4" >Figure 4</a>.
<figure id="topologyGuidedCausalEffectDag4">
   <img src="/assets/graphTopologyGuidedCausalEffectCalculation3/topologyGuidedCausalEffectDag4.png" style="max-width: 600px;">
   <figcaption>Figure 4. The subgraph of $G$ which will guide the causal effect calculation is shown in red.</figcaption>
</figure>
In the <a href="#topologyGuidedCausalEffectDag5" >Figure 5</a>, the guiding DAG is drawn alone. This DAG will be called $D$ from now on in this article. In $D$, the causal effect of $Z_{1}$ on $Y$, i.e. $p\left(y|do\left(z_{1}\right)\right)$, is identifiable. In <a href="#myBlog2">[3]</a>, it has been shown that the know-how for $p\left(y|do\left(z_{1}\right), z_{2}\right)$ is required.
<figure id="topologyGuidedCausalEffectDag5">
   <img src="/assets/graphTopologyGuidedCausalEffectCalculation3/topologyGuidedCausalEffectDag5.png" style="max-width: 600px;">
   <figcaption>Figure 5. The DAG which will guide the calculation of the causal effect with the variable names from $G$.</figcaption>
</figure>
The rules of do-calculus will first be used. Can the intervention on $Z_{1}$ be replaced with observing $Z_{1}$? Is $p\left(y|do\left(z_{1}\right), z_{2}\right)$ equal to $p\left(y|z_{1}, z_{2}\right)$? For this replacement or equality to be valid, $Y$ and $Z_{1}$ must be conditionally d-separated given $Z_{2}$ in the graph $D_{\underline{Z_{1}}}$. $D_{\underline{Z_{1}}}$ is shown in the <a href="#topologyGuidedCausalEffectDag6" >Figure 6</a>.
<figure id="topologyGuidedCausalEffectDag6">
   <img src="/assets/graphTopologyGuidedCausalEffectCalculation3/topologyGuidedCausalEffectDag6.png" style="max-width: 600px;">
   <figcaption>Figure 6. The DAG $D_{\underline{Z_{1}}}$.</figcaption>
</figure>
There are two paths from $Z_{1}$ to $Y$. They are as follows:
\begin{equation}
    \begin{array}{l}
        1) \, Z_{1} \leftarrow Z_{2} \rightarrow Y \newline
        2) \, Z_{1} \leftarrow Z_{2} \leftarrow U_{4} \rightarrow Y
    \end{array}
\end{equation}
These paths are blocked due to conditioning on $Z_{2}$. Hence, $Y$ and $Z_{1}$ are conditionally d-separated given $Z_{2}$ in the graph $D_{\underline{Z_{1}}}$, which means that $p\left(y|do\left(z_{1}\right), z_{2}\right)$ can be written as $p\left(y|z_{1}, z_{2}\right)$. Hence, $p\left(y|do\left(z_{1}\right), z_{2}\right)$ in the equation (27) in <a href="#myBlog2">[3]</a> can be replaced with $p\left(y|z_{1}, z_{2}\right)$.

## Conclusion
The causal effect calculation by the guidance of the DAG in the <a href="#topologyGuidedCausalEffectDag5" >Figure 5</a> has been carried out.

## References

<span id="Pearl"> [1] Judea Pearl, *Causality: Models, Reasoning and Inference*, Cambridge University Press, 2009.</span>

<span id="myBlog"> [2] [https://saffetgokcensen.github.io/blog/2022/06/12/an-example-of-the-graph-topology-guided-causal-effect-calculation](https://saffetgokcensen.github.io/blog/2022/06/12/an-example-of-the-graph-topology-guided-causal-effect-calculation)</span>

<span id="myBlog2"> [2] [https://saffetgokcensen.github.io/blog/2022/10/09/an-example-of-the-graph-topology-guided-causal-effect-calculation-2](https://saffetgokcensen.github.io/blog/2022/10/09/an-example-of-the-graph-topology-guided-causal-effect-calculation-2)</span>
