---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Some Elaboration On The Sequential Backdoor Criterion
---
## Introduction
In this article, the proof of theorem about the sequential backdoor criterion is 
elaborated on. The theorem is given on the page 121 of <a href="#Pearl">[1]</a>. 
Its proof is also given in the same reference.

## The Sequential Backdoor Criterion
The sequential backdoor criterion gives the conditions for 
$P\left(y|do\left(x\_{1}\right), ...,do\left(x\_{n}\right)\right )$ to be identifiable. 
$P\left(y|do\left(x\_{1}\right), ...,do\left(x\_{n}\right)\right )$ represents the 
effect of the unconditional plan 
$\left(do\left(x\_{1}\right), ...,do\left(x\_{n}\right)\right)$ on the variable $Y$. 
The sequential backdoor theorem is quoted from the page 121 of 
<a href="#Pearl">[1]</a> as follows:

**The Sequential Backdoor Criterion Theorem:** The probability
\begin{equation}
    P\left(y|do\left(x\_{1}\right), ... , do\left(x\_{n}\right)\right)
\end{equation}
is identifiable if, for every $1 \leq k \leq n$, there exists a set $Z\_{k}$ 
of covariates satisfying the following (sequential back-door) conditions:
\begin{equation}
    Z\_{k} \subseteq N\_{k}
\end{equation}
(i.e., $Z\_{k}$ consists of nondescendants of $\left \lbrace X\_{k}, X\_{k+1},
... , X\_{n} \right \rbrace$) 
and 
\begin{equation}
	\left ( \left ( Y 
	\text{ d-separated from } 
	X\_{k} \right ) \big | X\_{1}, ... , X\_{k-1}, Z\_{1}, Z\_{2}, ... , Z\_{k} \right ) 
	\text{ in } G\_{ \underline{X}\_{k}, \overline{X}\_{k+1}, ... , \overline{X}\_{n} }
	\label{theSecondCond}
\end{equation}
When these conditions are satisfied, the effect of the plan is given by

\begin{equation}
    P\left(y|do\left(x\_{1}\right), ... , do\left(x\_{n}\right)\right)=\sum\_{
        z\_{1}, ... , z\_{n}}P\left(y|z\_{1}, ... ,z\_{n}, x\_{1}, ... , x\_{n}\right)
		\times \prod\_{k=1}^{n} P\left(z\_{k}|z\_{1}, ... , z\_{k-1}, x\_{1}, ... , 
    x\_{k-1}\right)
\end{equation}

Some definitions related with the theorem are to be made. The problem has a 
directed acyclic graph (DAG) denoted by $G$. $G$ has a vertex set $V$. $V$ is 
composed of four disjoint sets as follows:
1. $X$ is the set of control variables.
2. $Z$ is the set of observed variables or the covariates.
3. $U$ is the set of unobserved variables or the latent variables.
4. $Y$ is the outcome variable.

The control variables are ordered, which means that every $X\_{k}$ is a nondescendant 
of $X\_{j}$ for $j>k$. The outcome is a descendant of $X\_{n}$. $N\_{k}$ represents 
the set of covariates which are nondescendants of any variable in 
$\left \lbrace X\_{k} , X\_{k+1} , ... , X\_{n} \right \rbrace$. 

## Elaboration On The Proof
As stated in <a href="#Pearl">[1]</a>, the first condition to be satisfied is 
the following:
\begin{equation}
	P\left ( z\_{k}|z\_{1}, ... , z\_{k-1}, x\_{1}, ... , x\_{k-1}, \hat{x}\_{k}, 
	\hat{x}\_{k+1} , ... , \hat{x}\_{n}  \right ) = P\left ( z\_{k}|z\_{1}, ... , 
	z\_{k-1}, x\_{1}, ... , x\_{k-1} \right )
	\label{firstCond}
\end{equation}
It is indicated in <a href="#Pearl">[1]</a> that the relation $Z\_{k} \subseteq N\_{k}$ implies 
$Z\_{k} \subseteq N\_{j}$ for all $j \geq k$ and then the equality in the equation 
(\ref{firstCond}) is valid due to the third rule of the do-calculus since there 
is not a directed path from any node in $\left \lbrace Z\_{1}, ... , Z\_{k}, X\_{1}, 
... , X\_{k-1}  \right \rbrace$ to any node in $\left \lbrace X\_{k}, ... , X\_{n} 
\right \rbrace$. 

Let this part be elaborated on. According to the third rule of the do-calculus, 
the equality in the equation (\ref{firstCond}) is valid if the following 
d-separation condition holds:
\begin{equation}
	\left ( \left ( Z\_{k} \text{ d-separated from } \left \lbrace X\_{k}, ... , 
	X\_{n} \right \rbrace \right ) \big | Z\_{1}, ... , Z\_{k-1}, X\_{1}, ... , 
	X\_{k-1} \right ) \text{ in } G\_{\overline{\left \lbrace X\_{k}, ... , X\_{n} 
	\right \rbrace \left ( Z\_{1}, ... , Z\_{k-1}, X\_{1}, ... , X\_{k-1} \right )}}
	\label{dSep1}
\end{equation}
$\left \lbrace X\_{k}, ... , X\_{n} \right \rbrace \left ( Z\_{1}, ... , Z\_{k-1}, 
X\_{1}, ... , X\_{k-1} \right )$ is the set of $\left \lbrace X\_{k}, ... , X\_{n} 
\right \rbrace$ which are not an\-ces\-tors of $\left \lbrace Z\_{1}, ... , Z\_{k-1}, 
X\_{1}, ... , X\_{k-1} \right \rbrace$. It is known that $Z\_{k} \subseteq N\_{k}$, which 
means that there are no directed paths from any element in 
$\left \lbrace X\_{k}, ...,X\_{n} \right \rbrace$ to $Z\_{k}$. Therefore, none of 
$\left \lbrace X\_{k}, ... , X\_{n} \right \rbrace$ can be an ancestor of $Z\_{k}$. 
$Z\_{k-1} \subseteq N\_{k-1}$ is also valid, which means that none of 
$\left \lbrace X\_{k-1}, X\_{k}, ... , X\_{n} \right \rbrace$ can be an ancestor of 
$Z\_{k-1}$. Repeating the same reasoning for $k-2, k-3, ... , 1$, it can be deduced
that none of $\left \lbrace X\_{k}, ...,X\_{n} \right \rbrace$ can be an ancestor of 
any element in $\left \lbrace Z\_{1}, Z\_{2}, ... , Z\_{k} \right \rbrace$. The control 
variables are in such an order that $X\_{j}$ is a nondescendant of $X\_{k}$ for $j<k$. 
Then, there are no directed paths from any element in $\left \lbrace X\_{k}, ...
, X\_{n} \right \rbrace$ to any element in $\left \lbrace X\_{1}, ... , X\_{k-1} 
\right \rbrace$. This implies that no element in $\left \lbrace X\_{k}, ... , 
X\_{n} \right \rbrace$ can be an ancestor of any element in $\left \lbrace X\_{1},
... , X\_{k-1} \right \rbrace$. Adding the conclusion stated just a few lines ago, 
it can be said that no element in $\left \lbrace X\_{k}, ... X\_{n} \right \rbrace$ 
can be an ancestor of any element in $\left \lbrace Z\_{1}, ... , Z\_{k}, X\_{1}, ...
, X\_{k-1} \right \rbrace$. This result is to be often used in the rest of the 
article. Therefore, let it be underlined as a particular equation:
\begin{equation}
	\text{ There cannot be a directed path from any element in } \left \lbrace 
	X\_{k}, ... , X\_{n} \right \rbrace \text{ to any element } \text{ in } 
	\left \lbrace Z\_{1}, ... , Z\_{k}, X\_{1}, ... , X\_{k-1} \right \rbrace .
	\label{directedPathReq}
\end{equation}
Then, the following equality can be written:
\begin{equation}
	\left \lbrace X\_{k}, ... , X\_{n} \right \rbrace \left ( Z\_{1}, ... , Z\_{k-1},
X\_{1}, ... , X\_{k-1} \right )=\left \lbrace X\_{k}, ... , X\_{n} \right \rbrace
\end{equation}
The condition in the equation (\ref{dSep1}) can be simplified to the following one:
\begin{equation}
	\left ( \left ( Z\_{k} \text{ d-separated from } \left \lbrace X\_{k}, ... ,
        X\_{n} \right \rbrace \right ) \big | Z\_{1}, ... , Z\_{k-1}, X\_{1}, ... ,
	X\_{k-1} \right ) \text{ in } G\_{\overline{X}\_{k}, \overline{X}\_{k+1}, ...
	\overline{X}\_{n}}
	\label{dSep1Simplified}
\end{equation}
Now, let it be investigated if this condition holds. Let the d-separation of 
$Z\_{k}$ and $X\_{k}$ be first examined. The d-separation of $Z\_{k}$ and the other 
variables $X\_{k+1}, ... , X\_{n}$ will be similar. Since $Z\_{k} \subseteq N\_{k}$, 
$Z\_{k}$ is a nondescendant of $X\_{k}$. There cannot be a directed path from 
$X\_{k}$ to $Z\_{k}$. If $X\_{k}$ and $Z\_{k}$ were to be d-connected, then the 
following conditions related with the paths between $Z\_{k}$ and $X\_{k}$ would 
hold:
\begin{equation}
	\text{ The paths between } Z\_{k} \text{ and } X\_{k} \text{ must include at 
	least either a fork or a collider since there cannot be a directed path from } 
	X\_{k} \text{ to } Z\_{k} \text{. A chain may or may not exist in addition 
	to a fork or a collider. All these paths must be unblocked.}
\end{equation}
\begin{equation}
	\text{The middle nodes of the forks cannot be from the set } \left \lbrace 
	Z\_{1}, ... , Z\_{k-1}, X\_{1}, ... , X\_{k-1} \right \rbrace \text{ since 
	these are conditioned on in the equation (\ref{dSep1Simplified}).}
	\label{midFork}
\end{equation}
\begin{equation}
	\text{The edge nodes of the forks cannot be from the set } \left \lbrace 
	X\_{k}, ... , X\_{n} \right \rbrace \text{ since the condition in the equation 
	(\ref{dSep1Simplified}) must hold in } G\_{\overline{X}\_{k}, \overline{X}\_{k+1}, 
	... \overline{X}\_{n}} \text{ in which no edges can enter } \left \lbrace X\_{k}, 
	... , X\_{n} \right \rbrace.
	\label{edgeFork}
\end{equation}
\begin{equation}
	\text{The collider nodes must be from the set } \left \lbrace Z\_{1}, ... , 
	Z\_{k-1}, X\_{1}, ... , X\_{k-1} \right \rbrace \text{ since these nodes are 
	conditioned on in the equation (\ref{dSep1Simplified}) and unblock the colliders.}
	\label{collider}
\end{equation}
\begin{equation}
	\text{The inner nodes in a chain cannot be from the set } \left \lbrace Z\_{1}, 
	... , Z\_{k-1}, X\_{1}, ... , X\_{k-1} \right \rbrace \text{ since they are 
	conditioned on and block the chains.}
	\label{chain1}
\end{equation}
\begin{equation}
	\text{The inner nodes of the chains cannot be from the set } \left \lbrace 
	X\_{k}, ... , X\_{n} \right \rbrace \text{ since no edges can enter them in 
	the graph } G\_{\overline{X}\_{k}, \overline{X}\_{k+1}, ... \overline{X}\_{n}}\text{.}
	\label{chain2}
\end{equation}

From the condition (\ref{midFork}) and the condition (\ref{edgeFork}), it can be 
deduced that the middle nodes of the forks must be from the set $\left \lbrace 
X\_{k}, ... , X\_{n} \right \rbrace$ and the edge nodes of the forks must be 
from the set $\left \lbrace Z\_{1}, ... , Z\_{k-1}, X\_{1}, ... , X\_{k-1} \right 
\rbrace$. But this is in conflict with the requirement given in 
(\ref{directedPathReq}). As a result, there cannot be an unblocked fork between 
$X\_{k}$ and $Z\_{k}$. From the condition (\ref{collider}) and the requirement in 
(\ref{directedPathReq}), it is determined that the parent nodes of colliders 
cannot be from the set $\left \lbrace X\_{k}, ... , X\_{n} \right \rbrace$. The 
collider node and the parent nodes of the collider can be only from the set 
$\left \lbrace Z\_{1}, ... , Z\_{k-1}, X\_{1}, ... , X\_{k-1} \right \rbrace$ provided 
$Z\_{k} \subseteq N\_{k}$ and the order in the control variables are respected. From 
the conditions (\ref{chain1}) and (\ref{chain2}), it is concluded that the inner nodes 
of chains can only be $Z\_{k}$ as an observable variable. An unobserved variable 
can also be an inner node. The initial node of a chain may be a variable from 
$\left \lbrace X\_{k}, ... , X\_{n} \right \rbrace$ or a variable from $\left 
\lbrace Z\_{1}, ... , Z\_{k-1}, X\_{1}, ... , X\_{k-1} \right \rbrace$ or $Z\_{k}$ or 
an unobserved variable. The last node of a chain may be a variable from $\left 
\lbrace Z\_{1}, ... , Z\_{k-1}, X\_{1}, ... , X\_{k-1} \right \rbrace$ or $Z\_{k}$ or 
an unobserved variable. In any case, there must be at least an unobserved variable 
in a chain due to the equation (\ref{directedPathReq}), the conditions (\ref{chain1}) 
and (\ref{chain2}). As a result, there can be only colliders between $X\_{k}$ and 
$Z\_{k}$ if unobserved variables are excluded for the time being. The allowed 
collider is shown in the Figure <a href="#colliderOfCovariates">1</a>.
<figure id="colliderOfCovariates">
<img src="/assets/colliderOfObserved.png" style="max-width: 600px;">
<figcaption>Figure 1. The collider which is allowed to build the path between 
$X_{k}$ and $Z_{k}$. </figcaption>
</figure> 
This collider can be connected to $X\_{k}$ in either of the ways shown in the 
<figure id="XkConnection1">
<img src="/assets/XkConnection1.png" style="max-width: 600px;">
<figcaption>Figure 2. The first possible connection of the collider in the Figure 
<a href="#colliderOfCovariates">1</a> to $X_{k}$. </figcaption>
</figure>
Figures <a href="#XkConnection1">2</a>, <a href="#XkConnection2">3</a>, 
<a href="#XkConnection3">4</a> and <a href="#XkConnection4">5</a>.
<figure id="XkConnection2">
<img src="/assets/XkConnection2.png" style="max-width: 600px;">
<figcaption>Figure 3. The second possible connection of the collider in the Figure 
<a href="#colliderOfCovariates">1</a> to $X_{k}$. </figcaption>
</figure>
<figure id="XkConnection3">
<img src="/assets/XkConnection3.png" style="max-width: 600px;">
<figcaption>Figure 4. The third possible connection of the collider in the Figure 
<a href="#colliderOfCovariates">1</a> to $X_{k}$. </figcaption>
</figure>
<figure id="XkConnection4">
<img src="/assets/XkConnection4.png" style="max-width: 600px;">
<figcaption>Figure 5. The fourth possible connection of the collider in the Figure 
	<a href="#colliderOfCovariates">1</a> to $X_{k}$. </figcaption>
</figure>
The connections in the Figures <a href="#XkConnection1">2</a> and 
<a href="#XkConnection3">4</a> are not allowed since no edges can enter $X\_{k}$ 
in the graph $G\_{\overline{X}\_{k}, \overline{X}\_{k+1}, ... \overline{X}\_{n}}$. 
The connections in the Figures <a href="#XkConnection2">3</a> and 
<a href="#XkConnection4">5</a> are not allowed due to the condition in the 
equation (\ref{directedPathReq}). Now that it has been shown that the collider in 
the Figure <a href="#colliderOfCovariates">1</a> cannot be connected to $X\_{k}$, 
$Z\_{k}$ and $X\_{k}$ cannot be d-connected by means of a non-directed path which 
is made of only covariates. All the reasoning used to reach this conclusion for 
$Z\_{k}$ and $X\_{k}$ is valid also for the d-connection between $Z\_{k}$ and 
$\left \lbrace X\_{k+1}, ... , X\_{n}  \right \rbrace$. Therefore, the d-separation 
condition in (\ref{dSep1}) has been proven for when the paths contain only 
covariates.

Now, let the cases when there are unobserved (latent) variables on the paths 
between $X\_{k}$ and $Z\_{k}$ be examined. Due to the requirement in the 
equation (\ref{directedPathReq}) and the conditions (\ref{midFork}) and 
(\ref{edgeFork}), the allowed forks with covariates and latent variables are shown 
in the Figure <a href="#forkCovAndLat">6</a>. 
<figure id="forkCovAndLat">
<img src="/assets/forkCovAndLat.png" style="max-width: 1000px;">
<figcaption>Figure 6. The allowed forks with covariates and latent variables. </figcaption>
</figure>
Due to the requirement in the equation (\ref{directedPathReq}) and the condition 
(\ref{collider}), the allowed colliders are given in the Figure 
<a href="#colliderCovAndLat">7</a>. 
<figure id="colliderCovAndLat">
<img src="/assets/colliderCovAndLat.png" style="max-width: 800px;">
<figcaption>Figure 7. The allowed colliders with covariates and latent variables. </figcaption>
</figure>
Due to the requirement in the equation (\ref{directedPathReq}) and the conditions 
(\ref{chain1}) and (\ref{chain2}), the allowed chains are shown in the Figure 
<a href="#chainCovAndLat">8</a>.
<figure id="chainCovAndLat">
<img src="/assets/chainCovAndLat.png" style="max-width: 800px;">
<figcaption>Figure 8. The allowed chains with covariates and latent variables. </figcaption>
</figure>
Since the d-separation of $Z\_{k}$ and $\left \lbrace X\_{k}, ... , X\_{n} \right 
\rbrace$ is examined, it is enough to go over the connections between the 
structures containing $\left \lbrace X\_{k}, ... , X\_{n} \right \rbrace$ and the 
other allowed ones. As a reminder, the allowed structures are the ones in the 
Figure <a href="#colliderOfCovariates">1</a>, Figure <a href="#forkCovAndLat">6</a>, Figure 
<a href="#colliderCovAndLat">7</a> and Figure <a href="#chainCovAndLat">8</a>.

There are two structures containing $\left \lbrace X\_{k}, ... , X\_{n} \right 
\rbrace$, the one in <a href="#forkCovAndLat">6</a>a) and <a href="#chainCovAndLat">8</a>a). It is 
first to be examined if a valid connection can be made to the one in 
<a href="#forkCovAndLat">6</a>a). <a href="#forkCovAndLat">6</a>b), <a href="#forkCovAndLat">6</a>d) and 
<a href="#forkCovAndLat">6</a>e) cannot be connected to <a href="#forkCovAndLat">6</a>a) because the 
condition in the equation (\ref{directedPathReq}) is violated. The connection of 
<a href="#forkCovAndLat">6</a>c) to <a href="#forkCovAndLat">6</a>e) creates a blocked path due to a 
blocked collider. The connection of either of <a href="#colliderCovAndLat">7</a>a), 
<a href="#colliderCovAndLat">7</a>b) and <a href="#colliderCovAndLat">7</a>c) to <a href="#forkCovAndLat">6</a>a) 
violates the condition in the equation (\ref{directedPathReq}). The connection of 
<a href="#chainCovAndLat">8</a>b) to <a href="#forkCovAndLat">6</a>a) creates a blocked collider and a 
violation of the condition in the equation (\ref{directedPathReq}). One possible 
connection of <a href="#chainCovAndLat">8</a>c) to <a href="#forkCovAndLat">6</a>a) creates a blocked 
collider and a copy of <a href="#chainCovAndLat">8</a>a). The other possible connection 
creates a blocked collider. One possible connection of <a href="#chainCovAndLat">8</a>d) to 
<a href="#forkCovAndLat">6</a>a) creates a blocked collider and the violation of the 
condition in the equation (\ref{directedPathReq}).  The other possible connection 
violates the condition in the equation (\ref{directedPathReq}). One possible 
connection of <a href="#chainCovAndLat">8</a>e) to <a href="#forkCovAndLat">6</a>a) violates the 
condition the equation (\ref{directedPathReq}). The other possible connection 
creates a blocked collider and a violation of the condition in the equation 
(\ref{directedPathReq}). One possible connection of <a href="#chainCovAndLat">8</a>f) to 
<a href="#forkCovAndLat">6</a>a) violates the condition in the equation 
(\ref{directedPathReq}). The other possible connection creates a blocked 
collider. One possible connection of <a href="#chainCovAndLat">8</a>g) to 
<a href="#forkCovAndLat">6</a>a) creates a blocked collider and a copy of 
<a href="#chainCovAndLat">8</a>a). The other possible connection creates a blocked collider. 
Hence, it has been determined that none of the structures in the figures 
<a href="#forkCovAndLat">6</a> and <a href="#chainCovAndLat">8</a> can be connected to 
<a href="#forkCovAndLat">6</a>a) to yield an unblocked path that satisfies the condition 
in the equation (\ref{directedPathReq}).

Now, let the connection of <a href="#chainCovAndLat">8</a>a) to the structures in the Figures 
<a href="#forkCovAndLat">6</a>, <a href="#colliderCovAndLat">7</a> and <a href="#chainCovAndLat">8</a> be examined.
One possible connection of <a href="#forkCovAndLat">6</a>b) to <a href="#chainCovAndLat">8</a>a) 
violates the condition in the equation (\ref{directedPathReq}) and keeps 
<a href="#chainCovAndLat">8</a>a). The other possible connection violates the condition in 
the equation (\ref{directedPathReq}). One possible connection of 
<a href="#forkCovAndLat">6</a>c) to <a href="#chainCovAndLat">8</a>a) creates a blocked collider. The 
other possible connection forms a blocked collider and keeps 
<a href="#chainCovAndLat">8</a>a). One of the four possible connections of 
<a href="#forkCovAndLat">6</a>d) to <a href="#chainCovAndLat">8</a>a) creates a chain similar to 
<a href="#chainCovAndLat">8</a>a) and violates the condition in the equation 
(\ref{directedPathReq}). Another of the four possible connections creates an 
unblocked collider. The other one of the four possible connections creates a 
copy of <a href="#chainCovAndLat">8</a>a), keeps it and violates the condition in the 
equation (\ref{directedPathReq}). The last one of the four possible connections 
creates a blocked collider and keeps <a href="#chainCovAndLat">8</a>a). One possible 
connection of <a href="#chainCovAndLat">8</a>a) to <a href="#forkCovAndLat">6</a>e) violates the 
requirement in the equation (\ref{directedPathReq}). The other possible 
connection keeps <a href="#chainCovAndLat">8</a>a) and violates the condition in the 
equation (\ref{directedPathReq}). Two of the four possible connections of 
<a href="#chainCovAndLat">8</a>a) to <a href="#colliderCovAndLat">7</a>a) are against the condition in 
the equation (\ref{directedPathReq}). The other two of the four possible 
connections keep <a href="#chainCovAndLat">8</a>a) and break the condition in the equation 
(\ref{directedPathReq}). One of the two possible connections of 
<a href="#chainCovAndLat">8</a>a) to <a href="#colliderCovAndLat">7</a>b) disobeys the requirement in 
the equation (\ref{directedPathReq}). The other one also violates the condition 
in the equation (\ref{directedPathReq}) and keeps <a href="#chainCovAndLat">8</a>a). The 
connection of <a href="#chainCovAndLat">8</a>a) to <a href="#colliderCovAndLat">7</a>c) yields the 
same results as the connection to <a href="#colliderCovAndLat">7</a>a). One possible 
connection of <a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>b) creates a blocked 
collider, keeps <a href="#chainCovAndLat">8</a>a) and <a href="#chainCovAndLat">8</a>b), creates a 
copy of <a href="#chainCovAndLat">8</a>c) and violates the condition in the equation 
(\ref{directedPathReq}). The other possible connection of <a href="#chainCovAndLat">8</a>a) 
to <a href="#chainCovAndLat">8</a>b) creates a blocked collider and violates the 
requirement in the equation (\ref{directedPathReq}). One of the four possible 
connections of <a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>c) creates a blocked 
collider, keeps <a href="#chainCovAndLat">8</a>a) and <a href="#chainCovAndLat">8</a>c), creates a copy 
of <a href="#chainCovAndLat">8</a>a) and violates the condition in the equation 
(\ref{directedPathReq}). Another of the four possible connections of 
<a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>c) creates a blocked collider, 
keeps <a href="#chainCovAndLat">8</a>a) and creates a chain similar to 
<a href="#chainCovAndLat">8</a>c). Another of the four possible connections of 
<a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>c) creates a blocked collider, 
keeps <a href="#chainCovAndLat">8</a>c) and creates a chain similar to <a href="#chainCovAndLat">8</a>a). 
The last of the four possible connections of <a href="#chainCovAndLat">8</a>a) to 
<a href="#chainCovAndLat">8</a>c) creates a blocked collider. One of the four possible 
connections of <a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>d) keeps 
<a href="#chainCovAndLat">8</a>a) and violates the condition in the equation 
(\ref{directedPathReq}). Another of the four possible connections of 
<a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>d) keeps <a href="#chainCovAndLat">8</a>a), 
violates the condition in the equation (\ref{directedPathReq}), keeps 
<a href="#chainCovAndLat">8</a>d) and creates a chain made of three latent variables. Another 
of the four possible connections violates the requirement in the equation 
(\ref{directedPathReq}). The last of the four possible connections creates a 
blocked collider, keeps <a href="#chainCovAndLat">8</a>d) and violates the condition in the 
equation (\ref{directedPathReq}). The connection of <a href="#chainCovAndLat">8</a>a) to 
<a href="#chainCovAndLat">8</a>e) yields the same results as the connection to 
<a href="#chainCovAndLat">8</a>d). One of the four possible connections of 
<a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>f) keeps <a href="#chainCovAndLat">8</a>a) 
and violates the condition in the equation (\ref{directedPathReq}). Another of 
the four possible connections of <a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>f) 
creates a blocked collider, keeps <a href="#chainCovAndLat">8</a>a) and creates a chain 
similar to <a href="#chainCovAndLat">8</a>f). Another of the four possible connections of 
<a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>f) violates the condition in the 
equation (\ref{directedPathReq}). The last one of the four possible connections 
of <a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>f) creates a blocked collider.
The connection of <a href="#chainCovAndLat">8</a>a) to <a href="#chainCovAndLat">8</a>g) yields the 
same results as the connection to <a href="#chainCovAndLat">8</a>c).

Therefore, it has been shown that $Z\_{k}$ and $\left \lbrace X\_{k}, ... , X\_{n} 
\right \rbrace $ cannot be d-connected by means of a non-directed path which 
contains latent variables. The elaboration for a non-directed path made of only 
covariates was made before this elaboration. 

Since the condition in the equation 
(\ref{dSep1Simplified}) is the simplified form of the condition in the equation 
(\ref{dSep1}) which is to be satisfied for the validity of the equality in the 
equation (\ref{firstCond}), the elaboration on the proof of the condition in the 
equation (\ref{dSep1}) has now been completed. 

The condition in the equation (\ref{theSecondCond}) is to be used in replacing 
an intervention with an observation. The second rule of the do-calculus is in 
action when replacing an intervention with an observation. Given that $G$ is 
a directed acyclic graph associated with a causal model and $P$ is the probability 
distribution induced by that model, 
\begin{equation}
	P\left ( y, | do\left(x \right ), do \left( z \right ),w \right ) = 
	P\left ( y, | do\left(x \right ), z, w \right ) \text{ if } \left ( 
	\left ( Y \text{ d-separated from } Z \right ) |X, W \right )  
	\text{ in } G\_{\overline{X} \underline{Z}}
	\label{secondRule}
\end{equation}
is the second rule of the do-calculus <a href="#Pearl">[1]</a>. 

Now, let the effect of the plan be calculated:
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right )  
	\right ) = \sum\_{z\_{1}} P \left ( y,z\_{1}|do\left (x\_{1} \right ), ... 
	, do \left (x\_{n}\right )  \right ) \Rightarrow
\end{equation}
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) = \sum\_{z\_{1}} P \left ( y|z\_{1}, do\left (x\_{1} \right ), ... 
	, do \left (x\_{n}\right )  \right ) P \left ( z\_{1}|do\left (x\_{1} \right 
	), ... , do \left (x\_{n}\right )  \right )
	\label{effectPlan1}
\end{equation}
$P \left ( z\_{1}|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right )  \right 
)$ in the equation (\ref{effectPlan1}) can be written as $P\left (z\_{1} \right )$ 
due to the condition in the equation (\ref{directedPathReq}). Therefore:
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) = \sum\_{z\_{1}} P \left ( y|z\_{1}, do\left (x\_{1} \right ), ... 
	, do \left (x\_{n}\right )  \right ) P \left ( z\_{1} \right )
	\label{effectPlan2}
\end{equation}
Can $P \left ( y|z\_{1}, do\left (x\_{1} \right ), ... , do \left (x\_{n}\right )  
\right )$ in the equation (\ref{effectPlan2}) be modified in the sense that the 
intervention on $X\_{1}$ is replaced with observing $X\_{1}$? According to the 
second rule of the do-calculus in the equation (\ref{secondRule}), 
\begin{equation}
	\left ( \left ( Y  \text{ d-separated from } X\_{1} \right )\big | Z\_{1}, 
	X\_{2}, ... , X\_{n} \right ) \text{ in } G\_{\underline{X}\_{1}, 
	\overline{X}\_{2}...\overline{X}\_{n}} 
	\label{doCalcExpansion1}
\end{equation}
is the condition to be satisfied for this replacement. Let the condition in the 
equation (\ref{theSecondCond}) be rewritten: 
\begin{equation}
	\left(\left ( Y \text{ d-separated from } X\_{k} \right )\big | X\_{1}, 
	... , X\_{k-1}, Z\_{1}, Z\_{2}, ... , Z\_{k}\right) \text{ in } 
	G\_{\underline{X}\_{k}, \overline{X}\_{k+1}, ... , \overline{X}\_{n}}
\end{equation}
For $k=1$, this condition states that 
\begin{equation}
	\left ( \left ( Y  \text{ d-separated from } X\_{1} \right )\big | Z\_{1} 
	\right ) \text{ in } G\_{\underline{X}\_{1}, \overline{X}\_{2}...
	\overline{X}\_{n}} 
	\label{condk=1}
\end{equation}
Is the condition in the equation (\ref{doCalcExpansion1}) the same as the one 
in the equation (\ref{condk=1})? In the graph $G\_{\underline{X}\_{1}, 
\overline{X}\_{2} ... \overline{X}\_{n}}$, there are no arrows entering $X\_{2}, 
... X\_{n}$. Therefore, they cannot be on a path between $Y$ and $X\_{1}$. Then, 
it does not affect the d-separability of $Y$ and $X\_{1}$ whether $X\_{2}, ... 
X\_{n}$ are conditioned or not. This means that the condition in the equation 
(\ref{doCalcExpansion1}) is the same as the one in the equation (\ref{condk=1}).

Hence, the expansion in the equation (\ref{effectPlan2}) can be 
simplified to the following:
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) = \sum\_{z\_{1}} P \left ( y|z\_{1}, x\_{1} ,do \left (x\_{2} \right 
	) ,  ... , do \left (x\_{n} \right )  \right ) P \left ( z\_{1} \right )
\end{equation}
After the simplification, the expansion continues and $P \left ( y|z\_{1}, x\_{1} 
, ... , do \left (x\_{n} \right )  \right )$ is written using the total probabilty 
rule with the expansion over $Z\_{2}$:
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) = \sum\_{z\_{1}} \left (\sum\_{z\_{2}} P \left ( y, z\_{2}|z\_{1}, 
	x\_{1}, do\left(x\_{2} \right ), ... , do \left (x\_{n}\right )  \right )
	\right ) P \left ( z\_{1} \right ) \Rightarrow 
\end{equation}
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) = \sum\_{z\_{1}} \left (\sum\_{z\_{2}} P \left ( y| z\_{2}, z\_{1}, 
	x\_{1}, do\left ( x\_{2}\right ), ... , do \left (x\_{n}\right )  \right )
	P \left ( z\_{2}| z\_{1},x\_{1} ,do \left (x\_{2} \right ), ... , do \left 
	(x\_{n}\right )  \right ) \right ) P \left ( z\_{1} \right )
	\label{effectPlan3}
\end{equation}
$P \left ( z\_{2}| z\_{1},x\_{1} ,do \left (x\_{2} \right ), ... , do \left (x\_{n}
\right )  \right )$ in the equation (\ref{effectPlan3}) can be written as 
$P \left ( z\_{2}| z\_{1},x\_{1}\right )$ due to the requirement in the equation 
(\ref{directedPathReq}). Therefore:
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) = \sum\_{z\_{1}} \left (\sum\_{z\_{2}} P \left ( y| z\_{2}, z\_{1}, 
	x\_{1}, do\left ( x\_{2}\right ), ... , do \left (x\_{n}\right )  \right )
	P \left ( z\_{2}| z\_{1},x\_{1}  \right ) \right ) P \left ( z\_{1} \right )
	\Rightarrow
\end{equation}
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) = \sum\_{z\_{1}} \sum\_{z\_{2}} P \left ( y| z\_{2}, z\_{1}, 
	x\_{1}, do\left ( x\_{2}\right ), ... , do \left (x\_{n}\right )  \right )
	P \left ( z\_{2}| z\_{1},x\_{1}  \right ) P \left ( z\_{1} \right )
	\label{effectPlan4}
\end{equation}
Can the intervention on $X\_{2}$ in $P \left ( y| z\_{2}, z\_{1},	x\_{1}, do\left 
( x\_{2}\right ), ... , do \left (x\_{n}\right )  \right )$ in the equation 
(\ref{effectPlan4}) be replaced with observing $X\_{2}$? This question can again 
be answered using the second rule of the do-calculus given in the equation 
(\ref{secondRule}). According to this rule, the following condition must be 
satisfied for the replacement to be valid:
\begin{equation}
	\left ( \left ( Y  \text{ d-separated from } X\_{2} \right )\big | Z\_{2}, 
	Z\_{1},X\_{1}, X\_{3}, ... , X\_{n} \right ) \text{ in } G\_{\underline{X}\_{2}, 
	\overline{X}\_{3}...\overline{X}\_{n}} 
	\label{doCalcExpansion2}
\end{equation}
The condition in the  equation (\ref{theSecondCond}) implies the following for 
$k=2$:
\begin{equation}
	\left ( \left ( Y  \text{ d-separated from } X\_{2} \right )\big | X\_{1}, 
	Z\_{1}, Z\_{2} \right ) \text{ in } G\_{\underline{X}\_{2}, \overline{X}\_{3}...
	\overline{X}\_{n}} 
	\label{condk=2}
\end{equation}
Since there are no arrows entering $X\_{3}, ... , X\_{n}$ in the DAG 
$G\_{\underline{X}\_{2}, \overline{X}\_{3}... \overline{X}\_{n}} $, a path on which 
either of $X\_{3}, ... , X\_{n}$ exists is not possible from $Y$ to $X\_{2}$. Then, 
the condition in the equation (\ref{doCalcExpansion2}) is the same as the one in 
the equation (\ref{condk=2}). Hence, the replacement of the intervention on 
$X\_{2}$ with observing $X\_{2}$ can be made to yield the following:
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) = \sum\_{z\_{1}} \sum\_{z\_{2}} P \left ( y| z\_{2}, z\_{1}, 
	x\_{1}, do\left ( x\_{2}\right ), ... , do \left (x\_{n}\right )  \right )
	P \left ( z\_{2}| z\_{1},x\_{1}  \right ) P \left ( z\_{1} \right ) \Rightarrow 
\end{equation}
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) = \sum\_{z\_{1}} \sum\_{z\_{2}} P \left ( y| z\_{2}, z\_{1}, 
	x\_{1}, x\_{2},do \left ( x\_{3} \right ) ... , do \left (x\_{n}\right )  
	\right ) P \left ( z\_{2}| z\_{1},x\_{1}  \right ) P \left ( z\_{1} \right ) 
\end{equation}

Repating similar operations for $k=3,...,n$, the following expression which is 
free of interventions is obtained at last:
\begin{equation}
	P \left ( y|do\left (x\_{1} \right ), ... , do \left (x\_{n}\right ) 
	\right ) =  \sum\_{z\_{n}} ... \sum\_{z\_{2}} \sum\_{z\_{1}} 
	P \left (y|z\_{1}, ... , z\_{n}, x\_{1}, ... , x\_{n} \right ) \times 
	P\left (z\_{1} \right )P\left (z\_{2}|z\_{1}, x\_{1} \right ) ... 
	P\left (z\_{n}|z\_{1}, x\_{1}, z\_{2}, x\_{2}, ... , z\_{n-1}, x\_{n-1} \right )
\end{equation}

## Conclusion
Some elaboration has been made on the proof of the sequential backdoor criteriron. 

## References

<span id="Pearl"> [1] Judea Pearl, *Causality: Models, Reasoning and Inference*, Cambridge University Press, 2009.</span>
