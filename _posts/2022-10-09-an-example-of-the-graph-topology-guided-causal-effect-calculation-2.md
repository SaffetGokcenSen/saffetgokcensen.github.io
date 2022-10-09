---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: An Example Of The Graph Topology Guided Causal Effect Calculation 2
---

## Introduction

In this article, some graphs are examined to determine if they can be utilized in calculating a causal effect in a given directed acyclic graph (DAG). Each graph is studied to detect if only this graph is enough to calculate the causal effect. The examined graphs are the (b), (c) and (d) parts of the Figure 3.8 on page 92 of <a href="#Pearl">[1]</a>. The DAG for which the causal effect is to be calculated is the (g) part of the Figure 3.8 on page 92 of <a href="#Pearl">[1]</a>.

## The Topology Guided Causal Effect Calculation

In the topology guided causal effect calculation, a subgraph of the DAG under investigation is examined to determine if it is appropriate to be used in the calculation of the causal effect. If it is appropriate, then the know-how from that subgraph is utilized. The graph in the Figure 3.8 (e) is said to be suitable in <a href="#Pearl">[1]</a> for the calculation of
$p\left(y|do\left(x\right)\right)$ in the graph (g) of the Figure 3.8. In <a href="#myBlog">[2]</a>, it is shown in detail how the graph in the Figure 3.8 (e) can be used to calculate this causal effect. Each one of the graphs in the Figure 3.8 (b), (c) and (d) is to be checked if only the checked graph is enough to calculate the causal effect in the graph (g) of the Figure 3.8.

## The Examination of The Graphs

The causal effect of $X$ on $Y$ is to be calculated for the DAG in the <a href="#topologyGuidedCausalEffectDag1" >Figure 1</a>.
<figure id="topologyGuidedCausalEffectDag1">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag1.png" style="max-width: 400px;">
   <figcaption>Figure 1. The DAG for which the causal effect of $X$ on $Y$ is to be calculated.</figcaption>
</figure>
The unobserved variables are made explicit to obtain the version shown in the <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a>. This graph will be called $G$ throughout the article.
<figure id="topologyGuidedCausalEffectDag2">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag2.png" style="max-width: 400px;">
   <figcaption>Figure 2. The DAG under investigation with the unobserved variables made explicit.</figcaption>
</figure>
The graph in the Figure 3.8 (b) of <a href="#Pearl">[1]</a> is drawn in the <a href="#topologyGuidedCausalEffectDag3" >Figure 3</a>.
<figure id="topologyGuidedCausalEffectDag3">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag3.png" style="max-width: 250px;">
   <figcaption>Figure 3. The graph in the Figure 3.8 (b) of <a href="#Pearl">[1]</a>.</figcaption>
</figure>
The subgraph of $G$ matching to this graph is indicated in red in the <a href="#topologyGuidedCausalEffectDag4" >Figure 4</a>.
<figure id="topologyGuidedCausalEffectDag4">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag4.png" style="max-width: 400px;">
   <figcaption>Figure 4. The subgraph of G matching to the graph in the Figure 3.8 (b) of <a href="#Pearl">[1]</a> is indicated in red.</figcaption>
</figure>
Let it be studied if only the graph in the <a href="#topologyGuidedCausalEffectDag5" >Figure 5</a> is enough to help determining the causal effect of $X$ on $Y$ in $G$. In the graph, the causal effect of $Z\_{2}$ on $Y$ is identifiable. The causal effect of $Z\_{2}$ on $Y$ is due to the post-intervention distribution which is valid in the mutilated graphs formed by removing arrows entering $Z\_{2}$. If the dependencies in the mutilated graphs happen to be similar, then the causal effect of $Z\_{2}$ on $Y$ in $G$ can be calculated using the know-how from the graph in the <a href="#topologyGuidedCausalEffectDag5" >Figure 5</a>.
<figure id="topologyGuidedCausalEffectDag5">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag5.png" style="max-width: 400px;">
   <figcaption>Figure 5. The graph in which $p\left(y|do\left(z_{2}\right)\right)$ is identifiable. This is the subgraph shown in red in the <a href="#topologyGuidedCausalEffectDag4" >Figure 4</a>.</figcaption>
</figure>
Let it be assumed that the dependencies in the mutilated graphs were similar. Then, $p\left(y|do\left(z\_{2}\right)\right)$ could be calculated in $G$. That is why this causal quantity should be incorporated into the calculation of $p\left(y|do\left(x\right)\right)$. This can be done using the following expansion:
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{2}}p\left(y,z\_{2}|do\left(x\right)\right)=\sum\_{z\_{2}}\frac{p\left(y,z\_{2}|do\left(x\right)\right)}{p\left(z\_{2}|do\left(x\right)\right)}p\left(z\_{2}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{2}}p\left(y|z\_{2},do\left(x\right)\right)p\left(z\_{2}|do\left(x\right)\right)
    \label{expansion\_one}
\end{equation}
In the expansion above, $p\left(y|z\_{2},do\left(x\right)\right)$ term should be converted to $p\left(y|do\left(z\_{2}\right)\right)$. Can the intervention on $X$ be replaced with observing $X$? Is $p\left(y|z\_{2},do\left(x\right)\right)$ equal to $p\left(y|z\_{2},x\right)$? This is possible if $Y$ and $X$ are conditionally d-separated given $Z\_{2}$ in the graph $G\_{\underline{X}}$. $G\_{\underline{X}}$ is shown in the <a href="#topologyGuidedCausalEffectDag6" >Figure 6</a>. $Y$ and $X$ can never be conditionally d-separated given $Z\_{2}$ in the graph $G\_{\underline{X}}$ due to the following unblocked paths:
\begin{equation}
    \begin{array}{l}
        1) \, X \leftarrow U\_{1} \rightarrow Y \newline
        2) \, X \leftarrow U\_{3} \rightarrow Z\_{3} \rightarrow Y 
    \end{array}
\end{equation}
Therefore, $p\left(y|z\_{2},do\left(x\right)\right)$ cannot be equal to $p\left(y|z\_{2},x\right)$. Can these paths be blocked by conditioning on either $Z\_{1}$ or $Z\_{3}$? $X \leftarrow U\_{3} \rightarrow Z\_{3} \rightarrow Y$ can be blocked by conditioning on $Z\_{3}$. However, this is not enough since $X \leftarrow U\_{1} \rightarrow Y$ can never be blocked due to the unobserved variable $U\_{1}$. As a result, $p\left(y|z\_{2}, do\left(x\right)\right)$ cannot be written as $p\left(y|z\_{2}, x\right)$.
<figure id="topologyGuidedCausalEffectDag6">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag10.png" style="max-width: 400px;">
   <figcaption>Figure 6. The graph $G_{\underline{X}}$.</figcaption>
</figure>
For $p\left(y|z\_{2},do\left(x\right)\right)$ in the equation (\ref{expansion\_one}), can the intervention on $X$ be removed, i.e. is $p\left(y|z\_{2},do\left(x\right)\right)$ equal to $p\left(y|z\_{2}\right)$? The removal is possible if $Y$ and $X$ are conditionally d-separated given $Z\_{2}$ in the graph $G\_{\overline{X\left(Z\_{2}\right)}}$. $X\left(Z\_{2}\right)$ represents $X$ which are not ancestors of $Z\_{2}$ in $G$. $X$ is not an ancestor of $Z\_{2}$, which means that $G\_{\overline{X\left(Z\_{2}\right)}}=G\_{\overline{X}}$. $G\_{\overline{X}}$ is shown in the <a href="#topologyGuidedCausalEffectDag7" >Figure 7</a>. As can easily be seen from the figure, $Y$ and $X$ are d-connected through the path $X \rightarrow Z\_{1} \rightarrow Y$ in the graph $G\_{\overline{X}}$. Hence, $p\left(y|z\_{2},do\left(x\right)\right)$ cannot be equal to $p\left(y|z\_{2}\right)$. Can this d-connection be disturbed by conditioning on either $Z\_{1}$ or $Z\_{3}$? If $Z\_{1}$ is conditioned on, then $Y$ and $X$ might seem to become d-separated. However, this d-separation is not possible because $X$ is an ancestor of $Z\_{1}$ implying $G\_{\overline{X\left(Z\_{1}, Z\_{2}\right)}}=G$. In $G$, $Y$ and $X$ are not conditionally d-separated given $Z\_{1}$ and $Z\_{2}$ meaning $p\left(y|z\_{1}, z\_{2},do\left(x\right)\right) \neq p\left(y|z\_{1}, z\_{2}\right)$. Conditioning on $Z\_{3}$ cannot disturb the fact that $Y$ and $X$ are d-connected in $G\_{\overline{X}}$. As a result, $p\left(y|z\_{2}, do\left(x\right)\right)$ cannot be written as $p\left(y|z\_{2}\right)$.
<figure id="topologyGuidedCausalEffectDag7">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag19.png" style="max-width: 400px;">
   <figcaption>Figure 7. The graph $G_{\overline{X}}$.</figcaption>
</figure>
For $p\left(y|z\_{2},do\left(x\right)\right)$ in the equation (\ref{expansion\_one}), can observing $Z\_{2}$ be replaced with an intervention on $Z\_{2}$, i.e. is $p\left(y|z\_{2},do\left(x\right)\right)$ equal to $p\left(y|do\left(z\_{2}\right),do\left(x\right)\right)$? The replacement or the equality is achievable if $Y$ and $Z\_{2}$ are conditionally d-separated given $X$ in the graph $G\_{\overline{X}\underline{Z\_{2}}}$. The graph $G\_{\overline{X}\underline{Z\_{2}}}$ is given in the <a href="#topologyGuidedCausalEffectDag8" >Figure 8</a>. $Y$ and $Z\_{2}$ aren't conditionally d-separated given $X$ in the graph $G\_{\overline{X}\underline{Z\_{2}}}$ because of the unblocked path $Z\_{2} \leftarrow U\_{4} \rightarrow Y$. There is no way of unblocking this path because $U\_{4}$ is an unobserved variable. Therefore, $p\left(y|z\_{2},do\left(x\right)\right)$ cannot be equal to $p\left(y|do\left(z\_{2}\right),do\left(x\right)\right)$.
<figure id="topologyGuidedCausalEffectDag8">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag20.png" style="max-width: 400px;">
   <figcaption>Figure 8. The graph $G_{\overline{X}\underline{Z_{2}}}$.</figcaption>
</figure>
After checking the ways of converting $p\left(y|z\_{2},do\left(x\right)\right)$ in the equation (\ref{expansion\_one}) to $p\left(y|do\left(z\_{2}\right)\right)$, it has been determined that this conversion is not possible. Hence, the know-how from the graph in the <a href="#topologyGuidedCausalEffectDag5" >Figure 5</a> cannot be used to calculate the causal effect in $G$ even if the dependencies in the mutilated graphs were similar.

It is the turn of the graph in the Figure 3.8 (c) of <a href="#Pearl">[1]</a>. It is drawn in the <a href="#topologyGuidedCausalEffectDag9" >Figure 9</a>.
<figure id="topologyGuidedCausalEffectDag9">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag7.png" style="max-width: 150px;">
   <figcaption>Figure 9. The graph in the Figure 3.8 (c) of <a href="#Pearl">[1]</a>.</figcaption>
</figure>
The subgraph of $G$ matching to this graph is shown in the <a href="#topologyGuidedCausalEffectDag10" >Figure 10</a>. If the dependencies in the mutilated form of this graph and that of $G$ are similar, then the know-how from the graph in the <a href="#topologyGuidedCausalEffectDag11" >Figure 11</a> can be used to calculate the causal effect of $Z\_{1}$ on $Y$ in $G$.
<figure id="topologyGuidedCausalEffectDag10">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag8.png" style="max-width: 400px;">
   <figcaption>Figure 10. The subgraph of $G$ matching to the graph in the Figure 3.8 (c) of <a href="#Pearl">[1]</a> is indicated in red.</figcaption>
</figure>
<figure id="topologyGuidedCausalEffectDag11">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag9.png" style="max-width: 400px;">
   <figcaption>Figure 11. The graph in which $p\left(y|do\left(z_{1}\right)\right)$ is identifiable. This is the subgraph shown in red in the <a href="#topologyGuidedCausalEffectDag10" >Figure 10</a>.</figcaption>
</figure>
Let it be assumed that the dependencies were similar. Then, $p\left(y|do\left(z\_{1}\right)\right)$ could be calculated in the $G$. $p\left(y|do\left(x\right)\right)$ should be written in a form which opens a way to incorporating the intervention of $Z\_{1}$ on $Y$ into the calculation. The following expansion can be used to reach such a form:
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}p\left(y,z\_{1}|do\left(x\right)\right)=\sum\_{z\_{1}}\frac{p\left(y,z\_{1}|do\left(x\right)\right)}{p\left(z\_{1}|do\left(x\right)\right)}p\left(z\_{1}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}p\left(y|z\_{1}, do\left(x\right)\right)p\left(z\_{1}|do\left(x\right)\right)
    \label{expansion\_two}
\end{equation}
The expansion in the line above contains $p\left(y|z\_{1}, do\left(x\right)\right)$. $p\left(y|z\_{1}, do\left(x\right)\right)$ should be transformed to $p\left(y|do\left(z\_{1}\right)\right)$. So, first of all, is it possible to replace the intervention on $X$ with observing $X$? Is $p\left(y|z\_{1}, do\left(x\right)\right)$ equal to $p\left(y|z\_{1}, x\right)$? This equality is possible if $Y$ and $X$ are conditionally d-separated given $Z\_{1}$ in the graph $G\_{\underline{X}}$. If $G\_{\underline{X}}$ in the <a href="#topologyGuidedCausalEffectDag6" >Figure 6</a> is examined, it can be detected that this conditional d-separation is impossible due to the following unblocked paths in $G\_{\underline{X}}$:
\begin{equation}
    \begin{array}{l}
        1) \, X \leftarrow U\_{1} \rightarrow Y \newline
        2) \, X \leftarrow U\_{2} \rightarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \newline
        3) \, X \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \newline
        4) \, X \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \newline
        5) \, X \leftarrow U\_{3} \rightarrow Z\_{3} \rightarrow Y
    \end{array}
    \label{inter_obs_rep_unblocked_paths1}
\end{equation}
Can the equality be made possible by conditioning on a variable? No, because $U\_{1}$ in the first unblocked path $X \leftarrow U\_{1} \rightarrow Y$ is unobserved and cannot be conditioned on for blocking the path. As a result, $p\left(y|z\_{1}, do\left(x\right)\right)$ cannot be written as $p\left(y|z\_{1}, x\right)$.

Another choice is to remove the intervention on $X$. Is 
$p\left(y|z\_{1}, do\left(x\right)\right)$ equal to $p\left(y|z\_{1}\right)$?
The removal of the intervention on $X$ is achievable if $Y$ and $X$ are conditionally d-separated given $Z\_{1}$ in the graph $G\_{\overline{X\left(Z\_{1}\right)}}$. $X\left(Z\_{1}\right)$ is the $X$ nodes which are not ancestors of $Z\_{1}$ in $G$.
As can be seen from the DAG in the <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a>, $X$ is an ancestor of $Z\_{1}$.
Hence, $G\_{\overline{X\left(Z\_{1}\right)}}$ is actually $G$.
In $G$, $Y$ and $X$ cannot be conditionally d-separated given $Z\_{1}$ due to the same unblocked paths as the ones in the equation (\ref{inter_obs_rep_unblocked_paths1}).
Can the equality be made possible by conditioning on a variable?
No, because $U\_{1}$ in the first unblocked path $X \leftarrow U\_{1} \rightarrow Y$ is unobserved and cannot be conditioned on for blocking the path.
As a result, $p\left(y|z\_{1}, do\left(x\right)\right)$ cannot be written as $p\left(y|z\_{1}\right)$.

Can the observation for $Z\_{1}$ be replaced with the intervention on $Z\_{1}$ and can this replacement be used as a starting point to deal with the intervention on $X$? For $p\left(y|z\_{1}, do\left(x\right)\right)$ to be equal to $p\left(y|do\left(z\_{1}\right), do\left(x\right)\right)$, $Y$ and $Z\_{1}$ must be conditionally d-separated given $X$ in the graph $G\_{\overline{X}\underline{Z\_{1}}}$.
In the <a href="#topologyGuidedCausalEffectDag12" >Figure 12</a>, it is clear that this conditional d-separation is impossible due to the following unblocked paths between $Y$ and $Z\_{1}$:
\begin{equation}
    \begin{array}{l}
        1) \, Z\_{1} \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \newline
        2) \, Z\_{1} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y
    \end{array}
\end{equation}
Can the equality be made possible by conditioning on a variable? Yes, conditioning on $Z\_{2}$ blocks all the paths and makes $Y$ and $Z\_{1}$ conditionally d-separated given $X$ and $Z\_{2}$ in the graph $G\_{\overline{X}\underline{Z\_{1}}}$. That is, the following equation is valid:
\begin{equation}
    p\left(y|z\_{1}, z\_{2}, do\left(x\right)\right) = p\left(y|do\left(z\_{1}\right), z\_{2}, do\left(x\right)\right)
\end{equation}
<figure id="topologyGuidedCausalEffectDag12">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag11.png" style="max-width: 400px;">
   <figcaption>Figure 12. The graph $G_{\overline{X}\underline{Z_{1}}}$.</figcaption>
</figure>
Can the intervention on $X$ be eliminated or replaced with observing $X$ in $p\left(y|do\left(z\_{1}\right), z\_{2}, do\left(x\right)\right)$? Let it first be examined if the intervention on $X$ can be replaced with observing $X$? This is possible if $Y$ and $X$ are conditionally d-separated given $Z\_{1}$ and $Z\_{2}$ in $G\_{\underline{X}\overline{Z\_{1}}}$. $G\_{\underline{X}\overline{Z\_{1}}}$ is shown in the <a href="#topologyGuidedCausalEffectDag13" >Figure 13</a>. Due to the unblocked paths $X \leftarrow U\_{1} \rightarrow Y$ and $X \leftarrow U\_{3} \rightarrow Z\_{3} \rightarrow Y$, $Y$ and $X$ cannot be conditionally d-separated given $Z\_{1}$ and $Z\_{2}$ in $G\_{\underline{X}\overline{Z\_{1}}}$. The path $X \leftarrow U\_{1} \rightarrow Y$ can never be blocked due to the unobserved variable $U\_{1}$. Hence, $p\left(y|do\left(z\_{1}\right), z\_{2}, do\left(x\right)\right)$ cannot be written as $p\left(y|do\left(z\_{1}\right), z\_{2}, x\right)$.

Is it achievable to eliminate the intervention on $X$? Is $p\left(y|do\left(z\_{1}\right), z\_{2}, do\left(x\right)\right)$ equal to $p\left(y|do\left(z\_{1}\right), z\_{2}\right)$? The elimination of the intervention can be made if $Y$ and $X$ are conditionally d-separated given $Z\_{1}$ and $Z\_{2}$ in the graph $G\_{\overline{X\left(Z\_{2}\right)} \, \overline{Z\_{1}}}$. $\overline{X\left(Z\_{2}\right)}$ represents $X$ which are not ancestors of $Z\_{2}$ in $G\_{\overline{Z\_{1}}}$. As can be seen from the <a href="#topologyGuidedCausalEffectDag13" >Figure 13</a> which is infact also $G\_{\overline{Z\_{1}}}$, $X$ is not an ancestor of $Z\_{2}$ in $G\_{\overline{Z\_{1}}}$. Therefore, $G\_{\overline{X\left(Z\_{2}\right)} \, \overline{Z\_{1}}}$ is equal to $G\_{\overline{X} \, \overline{Z\_{1}}}$.
<figure id="topologyGuidedCausalEffectDag13">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag12.png" style="max-width: 400px;">
   <figcaption>Figure 13. The graph $G_{\underline{X}\overline{Z_{1}}}$.</figcaption>
</figure>
In the <a href="#topologyGuidedCausalEffectDag14" >Figure 14</a>, the graph $G\_{\overline{X} \, \overline{Z\_{1}}}$ is displayed. It can be seen from the graph that $Y$ and $X$ are conditionally d-separated given $Z\_{1}$ and $Z\_{2}$. Therefore:
\begin{equation}
    p\left(y|do\left(z\_{1}\right), z\_{2}, do\left(x\right)\right) = p\left(y|do\left(z\_{1}\right), z\_{2}\right)
\end{equation}
<figure id="topologyGuidedCausalEffectDag14">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag13.png" style="max-width: 400px;">
   <figcaption>Figure 14. The graph $G_{\overline{X} \, \overline{Z_{1}}}$.</figcaption>
</figure>
So, the following chain of equalities has been proven:
\begin{equation}
    p\left(y|z\_{1}, z\_{2}, do\left(x\right)\right)=p\left(y|do\left(z\_{1}\right), z\_{2}, do\left(x\right)\right)=p\left(y|do\left(z\_{1}\right), z\_{2}\right)
    \label{chainOfEqualities}
\end{equation}
Then, it is time to incorporate $Z\_{2}$ into the expansion in the equation (\ref{expansion\_two}) so that the chain of equalities can be used. This incorporation can be done either using 
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\left(\sum\_{z\_{2}}p\left(y, z\_{2}|z\_{1}, do\left(x\right)\right)\right)p\left(z\_{1}|do\left(x\right)\right)
    \label{z1z2expansion1}
\end{equation}
or using
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\sum\_{z\_{2}}p\left(y,z\_{1}, z\_{2}|do\left(x\right)\right)
    \label{z1z2expansion2}
\end{equation}
In the first way of incorporation given in the equation (\ref{z1z2expansion1}), the result is 
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\left(\sum\_{z\_{2}}p\left(y | z\_{1}, z\_{2}, do\left(x\right)\right)p\left(z\_{2}|do\left(x\right)\right)\right)p\left(z\_{1}|do\left(x\right)\right)
\end{equation}
This form is not preferred since it seems lengthy, if not impossible, to calculate $p\left(z\_{1}|do\left(x\right)\right)$ in $G$ in the <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a>.

In the second way of incorporation given in the equation (\ref{z1z2expansion2}), the result is obtained as follows:
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\sum\_{z\_{2}}p\left(y,z\_{1}, z\_{2}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\sum\_{z\_{2}}\frac{p\left(y,z\_{1}, z\_{2}|do\left(x\right)\right)}{p\left(z\_{1}, z\_{2}|do\left(x\right)\right)}p\left(z\_{1}, z\_{2}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\sum\_{z\_{2}}p\left(y|z\_{1}, z\_{2},do\left(x\right)\right)p\left(z\_{1}, z\_{2}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\sum\_{z\_{2}}p\left(y|z\_{1}, z\_{2},do\left(x\right)\right)\frac{p\left(z\_{1}, z\_{2}|do\left(x\right)\right)}{p\left(z\_{2}|do\left(x\right)\right)}p\left(z\_{2}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\sum\_{z\_{2}}p\left(y|z\_{1}, z\_{2},do\left(x\right)\right)p\left(z\_{1}|z\_{2},do\left(x\right)\right)p\left(z\_{2}|do\left(x\right)\right)
\end{equation}
Using the equality given in the equation (\ref{chainOfEqualities}), the following final form can be obtained:
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\sum\_{z\_{2}}p\left(y|do\left(z\_{1}\right),z\_{2}\right)p\left(z\_{1}|z\_{2},do\left(x\right)\right)p\left(z\_{2}|do\left(x\right)\right)
    \label{expansion\_three}
\end{equation}
In the above expansion, there is the term $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$. The DAG in the <a href="#topologyGuidedCausalEffectDag11" >Figure 11</a> can be used to calculate $p\left(y|do\left(z\_{1}\right)\right)$. So, can this DAG help to calculate also $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$? The intervention on $Z\_{1}$ can be calculated using the probability distribution represented by the mutilated DAG in the <a href="#topologyGuidedCausalEffectDag15" >Figure 15</a>. Conditioning on $Z\_{2}$ does not disturb the dependencies in the mutilated DAG. Hence, it is expected that $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$ can also be calculated by the help of the DAG in the <a href="#topologyGuidedCausalEffectDag11" >Figure 11</a>.

Now, it is time to examine if $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$ can be calculated for $G$ shown in the <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a> using the graph in the <a href="#topologyGuidedCausalEffectDag11" >Figure 11</a>. Let the graph in the <a href="#topologyGuidedCausalEffectDag11" >Figure 11</a> be denoted by $G\_{2}$, if $G\_{\overline{Z\_{1}}}$ and $G\_{2\_{\overline{Z\_{1}}}}$ share similar dependencies while $Z\_{2}$ is conditioned on, then the know-how from $G\_{2}$ can be utilized to calculate $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$ in the DAG. The graph $G\_{\overline{Z\_{1}}}$ is shown in the <a href="#topologyGuidedCausalEffectDag16" >Figure 16</a> and the graph $G\_{2\_{\overline{Z\_{1}}}}$ is shown in the <a href="#topologyGuidedCausalEffectDag15" >Figure 15</a>.
<figure id="topologyGuidedCausalEffectDag15">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag15.png" style="max-width: 400px;">
   <figcaption>Figure 15. The graph $G_{2_{\overline{Z_{1}}}}$.</figcaption>
</figure>
<figure id="topologyGuidedCausalEffectDag16">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag14.png" style="max-width: 400px;">
   <figcaption>Figure 16. The graph $G_{\overline{Z_{1}}}$.</figcaption>
</figure>
In $G\_{2\_{\overline{Z\_{1}}}}$, there is only the path $Z\_{1} \rightarrow Y$ between $Z\_{1}$ and $Y$. This path is unblocked. $Z\_{1} \rightarrow Y$ is also the only path between $Z\_{1}$ and $Y$ in $G\_{\overline{Z\_{1}}}$. This path is also unblocked. Therefore, $G\_{2\_{\overline{Z\_{1}}}}$ and $G\_{\overline{Z\_{1}}}$ share similar dependencies between $Y$ and $Z\_{1}$. 

In $G\_{2\_{\overline{Z\_{1}}}}$, the paths between $Z\_{1}$ and $Z\_{2}$ are as follows:
\begin{equation}
    \begin{array}{l}
        1) \, Z\_{1} \rightarrow Y \leftarrow Z\_{2} \newline
        2) \, Z\_{1} \rightarrow Y \leftarrow U\_{4} \rightarrow Z\_{2}
    \end{array}
\end{equation}
Both of the paths above are blocked. In $G\_{\overline{Z\_{1}}}$, the paths between $Z\_{1}$ and $Z\_{2}$ are as follows:
\begin{equation}
    \begin{array}{l}
        1) \, Z\_{1} \rightarrow Y \leftarrow U\_{1} \rightarrow X \leftarrow U\_{2} \rightarrow Z\_{2} \newline
        2) \, Z\_{1} \rightarrow Y \leftarrow U\_{1} \rightarrow X \leftarrow Z\_{2} \newline
        3) \, Z\_{1} \rightarrow Y \leftarrow U\_{1} \rightarrow X \leftarrow U\_{3} \rightarrow Z\_{3} \leftarrow Z\_{2} \newline
        4) \, Z\_{1} \rightarrow Y \leftarrow Z\_{3} \leftarrow U\_{3} \rightarrow X \leftarrow U\_{2} \rightarrow Z\_{2} \newline
        5) \, Z\_{1} \rightarrow Y \leftarrow Z\_{3} \leftarrow U\_{3} \rightarrow X \leftarrow Z\_{2} \newline
        6) \, Z\_{1} \rightarrow Y \leftarrow Z\_{3} \leftarrow Z\_{2} \newline
        7) \, Z\_{1} \rightarrow Y \leftarrow U\_{4} \rightarrow Z\_{2}
    \end{array}
\end{equation}
All the paths listed in the equation above are blocked. Hence, $G\_{2\_{\overline{Z\_{1}}}}$ and $G\_{\overline{Z\_{1}}}$ share similar dependencies between $Z\_{1}$ and $Z\_{2}$.

In $G\_{2\_{\overline{Z\_{1}}}}$, the paths between $Y$ and $Z\_{2}$ are as follows:
\begin{equation}
    \begin{array}{l}
        1) \, Y \leftarrow Z\_{2} \newline
        2) \, Y \leftarrow U\_{4} \rightarrow Z\_{2}
    \end{array}
\end{equation}
Both of the paths above are unblocked. In $G\_{\overline{Z\_{1}}}$, the paths between $Y$ and $Z\_{2}$ are as follows:
\begin{equation}
    \begin{array}{l}
        1) \, Y \leftarrow U\_{1} \rightarrow X \leftarrow U\_{2} \rightarrow Z\_{2} \newline
        2) \, Y \leftarrow U\_{1} \rightarrow X \leftarrow Z\_{2} \newline
        3) \, Y \leftarrow U\_{1} \rightarrow X \leftarrow U\_{3} \rightarrow Z\_{3} \leftarrow Z\_{2} \newline
        4) \, Y \leftarrow Z\_{3} \leftarrow U\_{3} \rightarrow X \leftarrow U\_{2} \rightarrow Z\_{2} \newline
        5) \, Y \leftarrow Z\_{3} \leftarrow U\_{3} \rightarrow X \leftarrow Z\_{2} \newline
        6) \, Y \leftarrow Z\_{3} \leftarrow Z\_{2} \newline
        7) \, Y \leftarrow U\_{4} \rightarrow Z\_{2}
    \end{array}
\end{equation}
The first five paths listed above are all blocked. The sixth and the seventh ones are unblocked and the same as the ones in $G\_{2\_{\overline{Z\_{1}}}}$. Therefore, $G\_{2\_{\overline{Z\_{1}}}}$ and $G\_{\overline{Z\_{1}}}$ share similar dependencies between $Y$ and $Z\_{2}$. 

As a result, $G\_{2\_{\overline{Z\_{1}}}}$ and $G\_{\overline{Z\_{1}}}$ share similar dependencies and the know-how from $G\_{2}$ can be used to calculate $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$ in $G$.

The term $p\left(z\_{1}|z\_{2}, do\left(x\right)\right)$ in the equation (\ref{expansion\_three}) should be examined if it can be calculated using G. Can the intervention on $X$ be replaced with observing $X$? Can $p\left(z\_{1}|z\_{2}, do\left(x\right)\right)$ be written as $p\left(z\_{1}|z\_{2}, x\right)$? This is possible if $Z\_{1}$ and $X$ are conditionally d-separated given $X$ in the graph $G\_{\underline{X}}$. $G\_{\underline{X}}$ is shown in the <a href="#topologyGuidedCausalEffectDag6" >Figure 6</a>. The paths between $Z\_{1}$ and $X$ can be written as follows:
\begin{equation}
    \begin{array}{ll}
        1) \, Z\_{1} \rightarrow Y \leftarrow U\_{1} \rightarrow X &  8) \, Z\_{1} \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \leftarrow U\_{1} \rightarrow X \newline
        2) \, Z\_{1} \rightarrow Y \leftarrow Z\_{3} \leftarrow U\_{3} \rightarrow X & 9) \, Z\_{1} \leftarrow Z\_{2} \rightarrow Z\_{3} \leftarrow U\_{3} \rightarrow X \newline
        3) \, Z\_{1} \rightarrow Y \leftarrow Z\_{3} \leftarrow Z\_{2} \rightarrow X & 10) \, Z\_{1} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \leftarrow U\_{1} \rightarrow X \newline
        4) \, Z\_{1} \rightarrow Y \leftarrow Z\_{3} \leftarrow Z\_{2} \leftarrow U\_{2} \rightarrow X & 11) \, Z\_{1} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \leftarrow Z\_{3} \leftarrow U\_{3} \rightarrow X \newline
        5) \, Z\_{1} \rightarrow Y \leftarrow U\_{4} \rightarrow Z\_{2} \rightarrow X & 12) \, Z\_{1} \leftarrow Z\_{2} \leftarrow U\_{2} \rightarrow X \newline
        6) \, Z\_{1} \rightarrow Y \leftarrow U\_{4} \rightarrow Z\_{2} \leftarrow U\_{2} \rightarrow X & 13) \, Z\_{1} \leftarrow Z\_{2} \rightarrow X \newline
        7) \, Z\_{1} \rightarrow Y \leftarrow U\_{4} \rightarrow Z\_{2} \rightarrow Z\_{3} \leftarrow U\_{3} \rightarrow X
    \end{array}
\end{equation}
The first path is blocked due to the collider $Z\_{1} \rightarrow Y \leftarrow U\_{1}$.  The second path is blocked due to the collider $Z\_{1} \rightarrow Y \leftarrow Z\_{3}$. The third and fourth paths are blocked due to the collider $Z\_{1} \rightarrow Y \leftarrow Z\_{3}$ or conditioning on $Z\_{2}$. The fifth path is blocked due to the collider $Z\_{1} \rightarrow Y \leftarrow U\_{4}$ or conditioning on $Z\_{2}$. The sixth path is blocked due to the collider $Z\_{1} \rightarrow Y \leftarrow U\_{4}$. The seventh path is blocked due to the collider $Z\_{1} \rightarrow Y \leftarrow U\_{4}$ or conditioning on $Z\_{2}$ or the collider $Z\_{2} \rightarrow Z\_{3} \leftarrow U\_{3}$. The eighth path is blocked due to conditioning on $Z\_{2}$ or the collider $Z\_{3} \rightarrow Y \leftarrow U\_{1}$. The ninth path is blocked due to conditioning on $Z\_{2}$ or the collider $Z\_{2} \rightarrow Z\_{3} \leftarrow U\_{3}$. The tenth path is blocked due to conditioning on $Z\_{2}$ or the collider $U\_{4} \rightarrow Y \leftarrow U\_{1}$. The eleventh path is blocked due to conditioning on $Z\_{2}$ or the collider $U\_{4} \rightarrow Y \leftarrow Z\_{3}$. The twelfth and the thirteenth paths are blocked due to conditioning on $Z\_{2}$. Therefore, $Z\_{1}$ and $X$ are conditionally d-separated given $Z\_{2}$ in the graph $G\_{\underline{X}}$ and the following equality is valid:
\begin{equation}
    p\left(z\_{1}|z\_{2}, do\left(x\right)\right)=p\left(z\_{1}|z\_{2},x\right)
\end{equation}
After overcoming $p\left(z\_{1}|z\_{2}, do\left(x\right)\right)$ in the equation (\ref{expansion\_three}), it is the turn of $p\left(z\_{2}|do\left(x\right)\right)$. Can the intervention on $X$ be removed? Can $p\left(z\_{2}|do\left(x\right)\right)$ be written as $p\left(z\_{2}\right)$? This is possible if $Z\_{2}$ and $X$ are d-separated in the graph $G\_{\overline{X}}$. In the <a href="#topologyGuidedCausalEffectDag7" >Figure 7</a>, $G\_{\overline{X}}$ is drawn. The paths between $Z\_{2}$ and $X$ are as follows:
\begin{equation}
    \begin{array}{l}
        1) \, X \rightarrow Z\_{1} \leftarrow Z\_{2} \newline
        2) \, X \rightarrow Z\_{1} \rightarrow Y \leftarrow Z\_{3} \leftarrow Z\_{2} \newline
        3) \, X \rightarrow Z\_{1} \rightarrow Y \leftarrow U\_{4} \rightarrow Z\_{2}
    \end{array}
\end{equation}
The first path is blocked due to its collider structure. The second path is blocked due to the collider $Z\_{1} \rightarrow Y \leftarrow Z\_{3}$. The third path is blocked due to the collider $Z\_{1} \rightarrow Y \leftarrow U\_{4}$. Hence, $Z\_{2}$ and $X$ are d-separated in the graph $G\_{\overline{X}}$, which means that $p\left(z\_{2}|do\left(x\right)\right)$ can be written as $p\left(z\_{2}\right)$.

Resultantly, the expansion in the equation (\ref{expansion\_three}) can be expressed as follows:
\begin{equation}
    p\left(y|do\left(x\right)\right)=\sum\_{z\_{1}}\sum\_{z\_{2}}p\left(y|do\left(z\_{1}\right),z\_{2}\right)p\left(z\_{1}|z\_{2},x\right)p\left(z\_{2}\right)
    \label{expansion\_four}
\end{equation}
It has been proven that $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$ can be calculated using only the graph in the <a href="#topologyGuidedCausalEffectDag11" >Figure 11</a>. Hence, using the know-how from the graph in the <a href="#topologyGuidedCausalEffectDag11" >Figure 11</a> and the expansion in the equation (\ref{expansion\_four}), $p\left(y|do\left(x\right)\right)$ in $G$ can be calculated.

It is the turn of the graph in the Figure 3.8 (d) of <a href="#Pearl">[1]</a>. It is drawn in the <a href="#topologyGuidedCausalEffectDag17" >Figure 17</a>. The subgraph of $G$ matching to this graph is indicated in red in the <a href="#topologyGuidedCausalEffectDag18" >Figure 18</a>. If the dependencies in the mutilated form of this graph and that of $G$ are similar, then the know-how from the graph in the <a href="#topologyGuidedCausalEffectDag19" >Figure 19</a> can be used to calculate the causal effect of $X$ on $Z\_{1}$ in $G$. Let it be assumed that the dependencies were similar. $p(y|do(x))$ should be written in a form which opens a way to incorporating $p\left(z\_{1}|do\left(x\right)\right)$ into the calculation. The following expansion can be used to reach such a form:
\begin{equation}
    p(y|do(x))=\sum\_{z\_{1}}p\left(y,z\_{1}|do\left(x\right)\right)=\sum\_{z\_{1}}\frac{p\left(y,z\_{1}|do\left(x\right)\right)}{p\left(z\_{1}|do\left(x\right)\right)}p\left(z\_{1}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p(y|do(x))=\sum\_{z\_{1}}p\left(y|z\_{1}, do\left(x\right)\right)p\left(z\_{1}|do\left(x\right)\right)
    \label{expansion\_five}
\end{equation}
As can be seen from the equation (\ref{expansion\_five}), $p\left(z\_{1}|do\left(x\right)\right)$ has been incorporated into the calculation of the causal effect of $X$ on $Y$. Is there a way to calculate $p\left(y|z\_{1}, do\left(x\right)\right)$ using the know-how from the graph shown in the <a href="#topologyGuidedCausalEffectDag19" >Figure 19</a>? The know-how enables one to find the causal effect of $X$ on $Z\_{1}$, not on $Y$. The graph displayed in the <a href="#topologyGuidedCausalEffectDag19" >Figure 19</a> cannot be used to find $p\left(y|z\_{1},do\left(x\right)\right)$. Hence, using only the graph in the Figure 3.8 (d) of <a href="#Pearl">[1]</a>, it is not possible to calculate $p\left(y, do\left(x\right)\right)$ for $G$.
<figure id="topologyGuidedCausalEffectDag17">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag16.png" style="max-width: 150px;">
   <figcaption>Figure 17. The graph in the Figure 3.8 (d) of <a href="#Pearl">[1]</a>.</figcaption>
</figure>
<figure id="topologyGuidedCausalEffectDag18">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag17.png" style="max-width: 400px;">
   <figcaption>Figure 18. The subgraph of $G$ matching to the graph in the Figure 3.8 (d) of <a href="#Pearl">[1]</a> is indicated in red.</figcaption>
</figure>
<figure id="topologyGuidedCausalEffectDag19">
   <img src="/assets/graph_topology_guided_causal_effect_calculation_2/topologyGuidedCausalEffectDag18.png" style="max-width: 400px;">
   <figcaption>Figure 19. The graph in which $p\left(z_{1}|do\left(x\right)\right)$ is identifiable. This is the subgraph shown in red in the <a href="#topologyGuidedCausalEffectDag18" >Figure 18</a>.</figcaption>
</figure>

## Conclusion

The graphs in the Figure 3.8 (b), (c) and (d) of <a href="#Pearl">[1]</a> have been examined to determine if the causal effect of $X$ on $Y$ in $G$ shown in the <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a> can be calculated using only one of those three graphs. It has been shown that using only the graph in (b) or only the graph in (d) cannot help solving the causal effect. However, using only the graph in (c), the causal effect can be calculated.

## References

<span id="Pearl"> [1] Judea Pearl, *Causality: Models, Reasoning and Inference*, Cambridge University Press, 2009. </span>

<span id="myBlog"> [2] [https://saffetgokcensen.github.io/blog/2022/06/12/an-example-of-the-graph-topology-guided-causal-effect-calculation](https://saffetgokcensen.github.io/blog/2022/06/12/an-example-of-the-graph-topology-guided-causal-effect-calculation) </span>
