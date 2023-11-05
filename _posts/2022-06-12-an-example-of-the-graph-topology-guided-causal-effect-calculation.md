---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: An Example Of The Graph Topology Guided Causal Effect Calculation
---
## Introduction
First of all, this article is best viewed in Chromium and Google Chrome browsers. Some characters are not rendered correctly in Firefox. In this article, an example is to be given for the graph topology guided causal effect calculation. The graph topology guided causal effect calculation is demonstrated on the page 93 of [1]. A similar technique is to be applied to calculate the causal effect of $X$ on $Y$ for the directed acyclic graph (DAG) shown in the subfigure (g) of the Figure 3.8 on the page 92 of [1].
## The DAG
The DAG to be studied for the calculation of the causal effect of $X$ on $Y$ is shown in the <a href="#topologyGuidedCausalEffectDag1" >Figure 1</a>.
<figure id="topologyGuidedCausalEffectDag1">
   <img src="/assets/topologyGuidedCausalEffectDag1.png" style="max-width: 600px;">
   <figcaption>Figure 1. The DAG of the model to be studied for the causal effect of $X$ on $Y$.</figcaption>
</figure>
This DAG can be redrawn in the <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a> to make the unobserved variables explicit.
<figure id="topologyGuidedCausalEffectDag2">
   <img src="/assets/topologyGuidedCausalEffectDag2.png" style="max-width: 600px;">
   <figcaption>Figure 2. The version of the <a href="#topologyGuidedCausalEffectDag1" >Figure 1</a> in which unobserved variables are explicit.</figcaption>
</figure>
## The Backdoor Criterion
First, the backdoor criterion is checked to see if it can handle the calculation of the causal effect. The backdoor path $X \leftarrow U\_{1} \rightarrow Y$ cannot be blocked since $U\_{1}$ is unobserved. The existance of this backdoor path which can never be blocked makes it impossible to use the adjustment formula for the calculation of the causal effect.
## The Rules Of Do-calculus
The first rule is the replacement of the intervention with the related observation. Can the intervention on $X$ be replaced with an observation of $X$, i.e.
\begin{equation}
    p\left(y|do\left(x\right)\right) \stackrel{?}{=} p\left(y|x\right)
\end{equation}
Provided the original DAG is denoted by $G$, if $X$ and $Y$ are d-separated in the DAG $G\_{\underline{X}}$, then the replacement can be made.
<figure id="topologyGuidedCausalEffectDag3">
   <img src="/assets/topologyGuidedCausalEffectDag3.png" style="max-width: 600px;">
   <figcaption>Figure 3. The DAG $G_{\underline{X}}$.</figcaption>
</figure>
As can be seen in the <a href="#topologyGuidedCausalEffectDag3" >Figure 3</a>, there are the following unblocked backdoor paths between $X$ and $Y$:
\begin{equation}
    \begin{array}{l}
        X \leftarrow U\_{1} \rightarrow Y \newline
        X \leftarrow U\_{2} \rightarrow Z\_{2} \rightarrow Z\_{1} \rightarrow Y \newline
        X \leftarrow U\_{2} \rightarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \newline
        X \leftarrow U\_{3} \rightarrow Z\_{3} \rightarrow Y \newline
        X \leftarrow U\_{3} \rightarrow Z\_{3} \leftarrow Z\_{2} \rightarrow Z\_{1} \rightarrow Y \newline
        X \leftarrow U\_{3} \rightarrow Z\_{3} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y\newline
        X \leftarrow Z\_{2} \rightarrow Z\_{1} \rightarrow Y \newline
        X \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \newline
        X \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y
    \end{array}
\end{equation}
Hence, $X$ and $Y$ are not d-separated in the DAG $G\_{\underline{X}}$. This implies that 
\begin{equation}
    p\left(y|do\left(x\right)\right) \neq p\left(y|x\right)
\end{equation}
The other choice is the removal of the intervention. Can the intervention on $X$ be removed, i.e.
\begin{equation}
    p\left(y|do\left(x\right)\right) \stackrel{?}{=} p\left(y\right)
\end{equation}
This equality is possible if $X$ and $Y$ are d-separated in the DAG $G\_{\overline{X}}$.
<figure id="topologyGuidedCausalEffectDag4">
   <img src="/assets/topologyGuidedCausalEffectDag4.png" style="max-width: 600px;">
   <figcaption>Figure 4. The DAG $G_{\overline{X}}$.</figcaption>
</figure>
From the <a href="#topologyGuidedCausalEffectDag4" >Figure 4</a>, it can be detected that the path $X \rightarrow Z\_{1} \rightarrow Y$ between $X$ and $Y$ is unblocked. Hence, $X$ and $Y$ are not d-separated in the DAG $G\_{\overline{X}}$. This implies that
\begin{equation}
    p\left(y|do\left(x\right)\right) \neq p\left(y\right)
\end{equation}
As a result, a solution for the causal effect of $X$ on $Y$ couldn't be found by means of the simple application of the rules of the do-calculus.
## Topology Guided Causal Effect Calculation
The idea behind the topology guided causal effect calculation is detecting sub\-graphs of the DAG under investigation in such a way that these subgraphs identify causal effects which can be combined to obtain the target causal effect. There are such subgraphs in the DAG shown in the <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a>. In the <a href="#topologyGuidedCausalEffectDag5" >Figure 5</a>, the red subgraph is an identifying DAG.
<figure id="topologyGuidedCausalEffectDag5">
   <img src="/assets/topologyGuidedCausalEffectDag5.png" style="max-width: 600px;">
   <figcaption>Figure 5. The red subgraph is an identifying DAG.</figcaption>
</figure>
Considering that this subgraph can prospectively be used for the calculation of the causal quantity $p\left(y|do\left(x\right)\right)$, let the causal quantity be expanded as in the following total probability form:
\begin{equation}
    p\left(y|do\left(x\right)\right) = \sum\_{z\_{1}} p\left(y,z\_{1}|do\left(x\right)\right)
\end{equation}
$p\left(y,z\_{1}|do\left(x\right)\right)$ can be identified by the subgraph. In this identification, the follow\-ing form of the joint distribution is used:
\begin{equation}
    p\left(y,z\_{1}|do\left(x\right)\right)=p\left(y|z\_{1},do\left(x\right)\right)p\left(z\_{1}|do\left(x\right)\right)
\end{equation}
But, can this identification be used in the DAG of <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a>? This identification can be used in the original DAG only if the dependencies in the manipulated subgraph are similar to those in the manipulated original DAG. The manipulated subgraph is shown in the <a href="#topologyGuidedCausalEffectDag8" >Figure 6</a>.
<figure id="topologyGuidedCausalEffectDag8">
   <img src="/assets/topologyGuidedCausalEffectDag8.png" style="max-width: 300px;">
   <figcaption>Figure 6. The manipulated subgraph.</figcaption>
</figure>
The manipulated original DAG is shown in the <a href="#manipulatedOriginalDAG" >Figure 7</a>.
<figure id="manipulatedOriginalDAG">
   <img src="/assets/topologyGuidedCausalEffectDag4.png" style="max-width: 600px;">
   <figcaption>Figure 7. The manipulated original DAG.</figcaption>
</figure>
In the manipulated subgraph, there is only one path from $X$ to $Z\_{1}$ as $X \rightarrow Z\_{1}$. In the manipulated original DAG, there is also only one path from $X$ to $Z\_{1}$ as $X \rightarrow Z\_{1}$. It is obvious that the manipulated subgraph and the manipulated original DAG share similar dependencies for $p\left(z\_{1}|do\left(x\right)\right)$. As to $p\left(y|z\_{1},do\left(x\right)\right)$, in the <a href="#topologyGuidedCausalEffectDag8" >Figure 6</a>, there is only one path from $X$ to $Y$ as $X \rightarrow Z\_{1} \rightarrow Y$. In the <a href="#manipulatedOriginalDAG" >Figure 7</a>, there are additional two paths from $X$ to $Y$. They are $X\rightarrow Z\_{1} \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y$ and $X\rightarrow Z\_{1} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y$. These paths are unblocked to conditioning on $Z\_{1}$. The manipulated subgraph and the manipulated original graph do not share similar dependencies for $p\left(y|z\_{1},do\left(x\right)\right)$. After the examination of dependency similarity, it can be stated that the identification of $p\left(y, z\_{1}| do\left(x\right)\right)$ in the subgraph cannot be used in the original DAG. The paths $X\rightarrow Z\_{1} \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y$ and $X\rightarrow Z\_{1} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y$ can be blocked by conditioning on $Z\_{2}$. In order to attain conditioning on $Z\_{2}$, it is a good idea to start with the total probability rule over the two variables $Z\_{1}$ and $Z\_{2}$:
\begin{equation}
    p\left(y|do\left(x\right)\right) = \sum\_{z\_{1}} \sum\_{z\_{2}} p\left(y,z\_{1}, z\_{2}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x\right)\right) = \sum\_{z\_{1}} \sum\_{z\_{2}} p\left(y,z\_{1}|z\_{2},do\left(x\right)\right)p\left(z\_{2}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x\right)\right) = \sum\_{z\_{1}} \sum\_{z\_{2}} p\left(y|z\_{1},z\_{2},do\left(x\right)\right) p\left(z\_{1}|z\_{2},do\left(x\right)\right) p\left(z\_{2}|do\left(x\right)\right)
    \label{double\_total\_sum}
\end{equation}
There is now a conditioning on $Z\_{2}$ in $p\left(y|z\_{1},z\_{2},do\left(x\right)\right)$ as can be detected from the equation (\ref{double\_total\_sum}).

Let $p\left(z\_{1}|z\_{2},do\left(x\right)\right)$ be calculated first. From the <a href="#topologyGuidedCausalEffectDag2" >Figure 2</a>, the backdoor paths from $X$ to $Z\_{1}$ can be listed as follows:
\begin{equation}
    \begin{array}{l}
        1) \, X \leftarrow U\_{1} \rightarrow Y \leftarrow Z\_{1} \newline
        2) \, X \leftarrow U\_{2} \rightarrow Z\_{2} \rightarrow Z\_{1} \newline
        3) \, X \leftarrow U\_{2} \rightarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \leftarrow Z\_{1} \newline
        4) \, X \leftarrow U\_{2} \rightarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \leftarrow Z\_{1} \newline
        5) \, X \leftarrow U\_{3} \rightarrow Z\_{3} \rightarrow Y \leftarrow Z\_{1} \newline
        6) \, X \leftarrow U\_{3} \rightarrow Z\_{3} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \leftarrow Z\_{1} \newline
        7) \, X \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \leftarrow Z\_{1} \newline
        8) \, X \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \leftarrow Z\_{1} \newline
    \end{array}
\end{equation}
The first one is blocked due to the collider $U\_{1} \rightarrow Y \leftarrow Z\_{1}$. The second one is blocked due to conditioning on $Z\_{2}$. The third one is blocked due to conditioning on $Z\_{2}$ or the collider $Z\_{3} \rightarrow Y \leftarrow Z\_{1}$. The fourth one is blocked due to conditioning on $Z\_{2}$ or the collider $U\_{4} \rightarrow Y \leftarrow Z\_{1}$. The fifth one is blocked due to the collider $Z\_{3} \rightarrow Y \leftarrow Z\_{1}$. The sixth one is blocked due to conditioning on $Z\_{2}$ or the collider $U\_{4} \rightarrow Y \leftarrow Z\_{1}$. The seventh one is blocked due to conditioning on $Z\_{2}$ or the collider $Z\_{3} \rightarrow Y \leftarrow Z\_{1}$. The last one is blocked due to conditioning on $Z\_{2}$ or the collider $U\_{4} \rightarrow Y \leftarrow Z\_{1}$. Since all the backdoor paths from $X$ to $Z\_{1}$ are blocked, the following equality can safely be written:
\begin{equation}
    p\left(z\_{1}|z\_{2},do\left(x\right)\right)=p\left(z\_{1}|z\_{2},x\right)
\end{equation}
Let $p\left(y|z\_{1},z\_{2},do\left(x\right)\right)$ be dealt with. In the calculation of this causal quantity, the know-how from the subgraph shown in red in the <a href="#topologyGuidedCausalEffectDag5" >Figure 5</a> is to be utilized. Can the observation of $Z\_{1}$ be replaced with the intervention on $Z\_{1}$? In other words,
\begin{equation}
    p\left(y|z\_{1},z\_{2},do\left(x\right)\right) \stackrel{?}{=} p\left(y|do\left(z\_{1}\right),z\_{2},do\left(x\right)\right)
\end{equation}
This is possible if $Y$ and $Z\_{1}$ are conditionally d-separated given $Z\_{2}$ and $X$ in $G\_{\overline{X}\underline{Z\_{1}}}$. $G\_{\overline{X}\underline{Z\_{1}}}$ is displayed in the <a href="#topologyGuidedCausalEffectDag9" >Figure 8</a>.
<figure id="topologyGuidedCausalEffectDag9">
   <img src="/assets/topologyGuidedCausalEffectDag9.png" style="max-width: 600px;">
   <figcaption>Figure 8. The graph $G_{\overline{X}\underline{Z_{1}}}$.</figcaption>
</figure>
The paths $Z\_{1} \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y$ and $Z\_{1} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y$ are both blocked by conditioning on $Z\_{2}$. Hence, $Y$ and $Z\_{1}$ are conditionally d-separated given $Z\_{2}$ and $X$ in $G\_{\overline{X}\underline{Z\_{1}}}$, which implies the following:
\begin{equation}
    p\left(y|z\_{1},z\_{2},do\left(x\right)\right) = p\left(y|do\left(z\_{1}\right),z\_{2},do\left(x\right)\right)
\end{equation}
Can the intervention on $X$ be removed? In other words, is $p\left(y|do\left(z\_{1}\right),z\_{2},do\left(x\right)\right)$ equal to $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$? This is possible if $Y$ and $X$ are conditionally d-separated given $Z\_{1}$ and $Z\_{2}$ in the graph $G\_{\overline{Z\_{1}} \, \overline{X\left(Z\_{2}\right)}}$. $X\left(Z\_{2}\right)$ denotes the set of $X$ nodes which are not ancestors of $Z\_{2}$ in $G\_{\overline{X}}$. If the <a href="#topologyGuidedCausalEffectDag4" >Figure 4</a> is inspected, then it can be determined that
\begin{equation}
    X\left(Z\_{2}\right)=X
\end{equation}
Therefore, the graph $G\_{\overline{Z\_{1}} \, \overline{X}}$ is needed. It is shown in the <a href="#topologyGuidedCausalEffectDag10" >Figure 9</a>.
<figure id="topologyGuidedCausalEffectDag10">
   <img src="/assets/topologyGuidedCausalEffectDag10.png" style="max-width: 600px;">
   <figcaption>Figure 9. The graph $G_{\overline{Z_{1}} \, \overline{X}}$.</figcaption>
</figure>
From this figure, it is clear that $Y$ and $X$ are conditionally d-separated given $Z\_{1}$ and $Z\_{2}$. Hence, the following equality can safely be written:
\begin{equation}
    p\left(y|do\left(z\_{1}\right),z\_{2},do\left(x\right)\right)=p\left(y|do\left(z\_{1}\right),z\_{2}\right)
    \label{simplification2}
\end{equation}
Now, $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$ is to be worked on. The experience from the subgraph shown in red in the <a href="#topologyGuidedCausalEffectDag5" >Figure 5</a> is going to be utilized again. The intervention in $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$ is to be replaced by an observation of $Z\_{1}$. This is possible if $Y$ and $Z\_{1}$ are conditionally d-separated given $Z\_{2}$ in $G\_{\underline{Z\_{1}}}$. The graph $G\_{\underline{Z\_{1}}}$ is displayed in the <a href="#topologyGuidedCausalEffectDag11" >Figure 10</a>.
<figure id="topologyGuidedCausalEffectDag11">
   <img src="/assets/topologyGuidedCausalEffectDag11.png" style="max-width: 600px;">
   <figcaption>Figure 10. The graph $G_{\underline{Z_{1}}}$.</figcaption>
</figure>
The backdoors from $Z\_{1}$ to $Y$ in $G\_{\underline{Z\_{1}}}$ are as follows:
\begin{equation}
    \begin{array}{l}
        1) \, Z\_{1} \leftarrow X \leftarrow U\_{2} \rightarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \newline
        2) \, Z\_{1} \leftarrow X \leftarrow U\_{2} \rightarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \newline
        3) \, Z\_{1} \leftarrow X \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \newline
        4) \, Z\_{1} \leftarrow X \leftarrow U\_{3} \rightarrow Z\_{3} \rightarrow Y \newline
        5) \, Z\_{1} \leftarrow X \leftarrow U\_{3} \rightarrow Z\_{3} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \newline
        6) \, Z\_{1} \leftarrow X \leftarrow U\_{1} \rightarrow Y
    \end{array}
    \label{backdoor\_z1\_y}
\end{equation}
Path 1 and path 3 are blocked due to conditioning on $Z\_{2}$. Path 2 is unblocked due to condition\-ing on $Z\_{2}$. Path 4 is unblocked. Path 5 is blocked due to conditioning on $Z\_{2}$ or the collider $U\_{3} \rightarrow Z\_{3} \leftarrow Z\_{2}$. Path 6 is unblocked. Conditioning on $X$ blocks path 2, path 4 and path 6 without disturbing the states of the paths 1, 3 and 5. Hence, in order to attain conditioning on $X$, $p\left(y|do\left(z\_{1}\right),z\_{2}\right)$ should be written as a total probability sum over all possible values of $X$:
\begin{equation}
    p\left(y|do\left(z\_{1}\right),z\_{2}\right)=\sum\_{x^{\prime}} p\left(y, x^{\prime}|do\left(z\_{1}\right),z\_{2}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(z\_{1}\right),z\_{2}\right)=\sum\_{x^{\prime}} p\left(y|x^{\prime}, do\left(z\_{1}\right),z\_{2}\right)p\left(x^{\prime}| do\left(z\_{1}\right),z\_{2}\right)
    \label{total\_sum\_on\_X}
\end{equation}
Let $p\left(x^{\prime}| do\left(z\_{1}\right),z\_{2}\right)$ be examined first. Can the intervention on $Z\_{1}$ be removed? The removal is possible if $X$ and $Z\_{1}$ are conditionally d-separated given $Z\_{2}$ in $G\_{\overline{Z\_{1}\left(Z\_{2}\right)}}$. $Z\_{1}\left(Z\_{2}\right)$ represents the set of $Z\_{1}$ nodes which are not ancestors of $Z\_{2}$ in $G\_{\overline{Z}\_{1}}$. $G\_{\overline{Z}\_{1}}$ is given in the <a href="#topologyGuidedCausalEffectDag12" >Figure 11</a>. It is evident from this figure that
\begin{equation}
    Z\_{1}\left(Z\_{2}\right)=Z\_{1} \Rightarrow G\_{\overline{Z\_{1}\left(Z\_{2}\right)}}=G\_{\overline{Z}\_{1}}
\end{equation}
The backdoor paths from $X$ to $Z\_{1}$ are as follows:
\begin{equation}
    \begin{array}{l}
        1) \, X \leftarrow U\_{1} \rightarrow Y \leftarrow Z\_{1} \newline
        2) \, X \leftarrow U\_{2} \rightarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \leftarrow Z\_{1} \newline
        3) \, X \leftarrow U\_{2} \rightarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \leftarrow Z\_{1} \newline
        4) \, X \leftarrow Z\_{2} \rightarrow Z\_{3} \rightarrow Y \leftarrow Z\_{1} \newline
        5) \, X \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \leftarrow Z\_{1} \newline
        6) \, X \leftarrow U\_{3} \rightarrow Z\_{3} \rightarrow Y \leftarrow Z\_{1} \newline
        7) \, X \leftarrow U\_{3} \rightarrow Z\_{3} \leftarrow Z\_{2} \leftarrow U\_{4} \rightarrow Y \leftarrow Z\_{1}
    \end{array}
\end{equation}
<figure id="topologyGuidedCausalEffectDag12">
   <img src="/assets/topologyGuidedCausalEffectDag12.png" style="max-width: 600px;">
   <figcaption>Figure 11. The graph $G_{\overline{Z}_{1}}$.</figcaption>
</figure>
The first path is blocked due to the collider $U\_{1} \rightarrow Y \leftarrow Z\_{1}$. The second path is blocked due to conditioning on $Z\_{2}$ or the collider $Z\_{3} \rightarrow Y \leftarrow Z\_{1}$. The third path is blocked due to the collider $U\_{4} \rightarrow Y \leftarrow Z\_{1}$. The fourth path is blocked due to conditioning on $Z\_{2}$ or the collider $Z\_{3} \rightarrow Y \leftarrow Z\_{1}$. The fifth path is blocked due to conditioning on $Z\_{2}$ or the collider $U\_{4} \rightarrow Y \leftarrow Z\_{1}$. The sixth path is blocked due to the collider $Z\_{3} \rightarrow Y \leftarrow Z\_{1}$. The seventh path is blocked due to the collider $U\_{3} \rightarrow Z\_{3} \leftarrow Z\_{2}$ or conditioning on $Z\_{2}$ or the collider $U\_{4} \rightarrow Y \leftarrow Z\_{1}$. Since all the backdoor paths from $X$ to $Z\_{1}$ in $G\_{\overline{Z}\_{1}}$ are conditionally blocked given $Z\_{2}$, $X$ and $Z\_{1}$ are conditionally d-separated given $Z\_{2}$ in $G\_{\overline{Z}\_{1}}$. Therefore, the intervention on $Z\_{1}$ in $p\left(x^{\prime}| do\left(z\_{1}\right),z\_{2}\right)$ can be removed:
\begin{equation}
    p\left(x^{\prime}| do\left(z\_{1}\right),z\_{2}\right)=p\left(x^{\prime}| z\_{2}\right)
\end{equation}
As to $p\left(y|x^{\prime}, do\left(z\_{1}\right),z\_{2}\right)$, remembering the reasoning that led to the expansion in the equation (\ref{total\_sum\_on\_X}), it is already known that $Z\_{1}$ and $Y$ are conditionally d-separated given $X$ and $Z\_{2}$. Hence, the intervention on $Z\_{1}$ can be replaced with the observation of $Z\_{1}$:
\begin{equation}
    p\left(y|x^{\prime}, do\left(z\_{1}\right),z\_{2}\right)=p\left(y|x^{\prime}, z\_{1}, z\_{2}\right)
\end{equation}
As a result, the following equation can be written:
\begin{equation}
    p\left(y|do\left(z\_{1}\right),z\_{2}\right)=\sum\_{x^{\prime}} p\left(y|x^{\prime}, z\_{1}, z\_{2}\right)p\left(x^{\prime}| z\_{2}\right)
\end{equation}
Hence, $p\left(y|z\_{1}, z\_{2}, do\left(x\right)\right)$ in the expansion in the equation (\ref{double\_total\_sum}) has been shown to satisfy the following equality:
\begin{equation}
    p\left(y|z\_{1}, z\_{2}, do\left(x\right)\right)=\sum\_{x^{\prime}}p\left(y|x^{\prime},z\_{1},z\_{2}\right)p\left(x^{\prime}|z\_{2}\right)
\end{equation}
Now, it is the turn of $p\left(z\_{2}|do\left(x\right)\right)$ in the expansion given in the equation (\ref{double\_total\_sum}). Can the intervention on $X$ be removed? The removal is possible if $X$ and $Z\_{2}$ are d-separated in the graph $G\_{\overline{X}}$. $G\_{\overline{X}}$ is given in the <a href="#topologyGuidedCausalEffectDag4" >Figure 4</a>. The paths from $X$ to $Z\_{2}$ are listed below:
\begin{equation}
    \begin{array}{l}
        1) \, X \rightarrow Z\_{1} \leftarrow Z\_{2} \newline
        2) \, X \rightarrow Z\_{1} \rightarrow Y \leftarrow Z\_{3} \leftarrow Z\_{2} \newline
        3) \, X \rightarrow Z\_{1} \rightarrow Y \leftarrow U\_{4} \rightarrow Z\_{2}
    \end{array}
\end{equation}
The first path is blocked since it is a collider and $Z\_{1}$ is not conditioned on. The second path is blocked by the collider $Z\_{1} \rightarrow Y \leftarrow Z\_{3}$. The third path is also blocked due to the collider $Z\_{1} \rightarrow Y \leftarrow U\_{4}$. Therefore, $X$ and $Z\_{2}$ are d-separated in the graph $G\_{\overline{X}}$. This d-separation implies the following equality:
\begin{equation}
    p\left(z\_{2}|do\left(x\right)\right)=p\left(z\_{2}\right)
\end{equation}
So, finally, all the post-intervention probabilities in the equation (\ref{double\_total\_sum}) have been written in terms of pre-intervention probabilities. They are wrapped up as follows:
\begin{equation}
    p\left(y|z\_{1}, z\_{2}, do\left(x\right)\right)=\sum\_{x^{\prime}}p\left(y|x^{\prime},z\_{1},z\_{2}\right)p\left(x^{\prime}|z\_{2}\right)
\end{equation}
\begin{equation}
    p\left(z\_{1}|z\_{2},do\left(x\right) \right)=p\left(z\_{1}|z\_{2},x \right)
\end{equation}
\begin{equation}
    p\left(z\_{2}|do\left(x\right)\right)=p\left(z\_{2}\right)
\end{equation}
The causal effect of $X$ on $Y$ has been proven to satisfy the following:
\begin{equation}
    p\left(y|do\left(x\right)\right) = \sum\_{z\_{1}} \sum\_{z\_{2}} p\left(y|z\_{1},z\_{2},do\left(x\right)\right) p\left(z\_{1}|z\_{2},do\left(x\right)\right)p\left(z\_{2}|do\left(x\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|do\left(x\right)\right) = \sum\_{z\_{1}} \sum\_{z\_{2}}\sum\_{x^{\prime}}p\left(y|x^{\prime},z\_{1},z\_{2}\right)p\left(x^{\prime}|z\_{2}\right)p\left(z\_{1}|z\_{2},x \right)p\left(z\_{2}\right)
\end{equation}
## Conclusion
A causal effect which cannot be calculated using the backdoor criterion or simple application of the rules of the do-calculus has been demonstrated to be calculated by means of the topology of the graph. A subgraph of the problem graph is known to be an identifying graph. The know-how for this subgraph has been used to calculate the causal effect under investigation.
## References
[1] Judea Pearl, Causality: Models, Reasoning and Inference, Cambridge University Press, 2009.
