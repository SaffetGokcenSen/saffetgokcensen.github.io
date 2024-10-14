---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: In Ideal Randomized Experiments, Association Is Causation
--- 
## 1. Introduction 
The title is the last sentence of the first paragraph on the page 15 of 
<a href="#whatif">[1]</a>. In this article, the example which is concluded by 
this sentence is to be summarized. The results of this example are presented 
and discussed. Then, the operation which represents randomization in the causal 
inference framework of Judea Pearl is to be stated. Then, it is proven that this 
operation in the causal inference framework of Judea Pearl allows association to 
be equal to causation.

## 2. The Example <a name="secondSection"><a/>
The example given in <a href="#whatif">[1]</a> is to be summarized in this 
section. There is a population with a lot of members. A coin is flipped for each 
person in this population. If the coin turns tails, the person is assigned to 
the treatment group. Otherwise, the person is assigned to the placebo group. The 
coin is not a fair one. Therefore, the treatment group is more crowded than 
the placebo group. After the experiment is concluded, the results are obtained 
as follows: 
\begin{gather}
	P\left(Y=1|A=1\right) = 0.4 \label{rctRes1} \newline
	P\left(Y=1|A=0\right) = 0.7 \label{rctRes2}
\end{gather} 
where $A=1$ represents the application of the treatment and $A=0$ denotes the 
application of the placebo. $Y=1$ means that the individual dies and $Y=0$ means 
that the individual survives. Now, what would be the results of the experiment 
if an individual were assigned to the placebo group when the coin turned tails 
and to the treatment group in the case of heads? The results would be the same as 
the ones in the equations \eqref{rctRes1} and \eqref{rctRes2}. The reason is the 
way the treatment and the placebo groups are formed. They are formed in a totally 
randomized manner by means of coin tosses. The randomization makes the treatment 
and the non-treatment groups exchangeable. These groups are comparable to each 
other since they are randomly created. The fact that the results of the 
experiment would be the same as the ones in the equations \eqref{rctRes1} and 
\eqref{rctRes2} if the treatment and non-treatment groups were exchanged can 
mathematically be expressed as follows:
\begin{gather} 
	P\left(Y^{a=0}=1|A=1\right)=P\left(Y=1|A=0\right)=P\left(Y^{a=0}=1|A=0
	\right)  \label{counterfact1}
\newline 
	P\left(Y^{a=1}=1|A=0\right)=P\left(Y=1|A=1\right)=P\left(Y^{a=1}=1|A=1
	\right) \label{counterfact2}
\end{gather}
$P\left(Y^{a=0}=1|A=1\right)$ in the equation \eqref{counterfact1} is the 
probability of the unobserved  counterfactual outcome of death if the treatment 
group were the non-treatment group. $P\left(Y^{a=1}=1|A=0\right)$ in the equation 
\eqref{counterfact2} is the probability of the unobserved counterfactual outcome 
of death if the non-treatment group were the treatment group. Therefore, 
randomization allows calculating the probabilities of counterfactual outcomes. 
The equalities in the equations \eqref{counterfact1} and \eqref{counterfact2} 
can be compactly written as follows: 
\begin{equation}
	P\left(Y^{a}=1|A=1\right) = P\left(Y^{a}=1|A=0\right) 
	\label{compact1}
\end{equation} 
Since $A$ and $Y$ are binary variables, the relation in the equation 
\eqref{compact1} states that $Y^{a}$ and $A$ are independent. 

Let $P\left(Y^{a}=1\right)$ be calculated using the results derived by means of 
randomization:
\begin{gather} 
	P\left(Y^{a}=1\right)=P\left(Y^{a}=1, A=1\right)+P\left(Y^{a}=1, A=0
	\right)=
	P\left(Y^{a}=1|A=1\right)P\left(A=1\right)+
	P\left(Y^{a}=1|A=0\right)P\left(A=0\right)= \newline
	P\left(Y^{a}=1|A=1\right)P\left(A=1\right)+
	P\left(Y^{a}=1|A=1\right)P\left(A=0\right)=
	P\left(Y^{a}=1|A=1\right) \underbrace{\left(P\left(A=1\right) +
	P\left(A=0\right)\right)}_{1} \implies \newline 
	P\left(Y^{a}=1\right)=P\left(Y^{a}=1|A=1\right) \implies 
	P\left(Y^{a}=1\right)=P\left(Y^{a}=1|A=1\right)=P\left(Y^{a}=1|A=0\right) 
	\label{basic}
\end{gather}
The resultant equality in the equation \eqref{basic} implies the following: 
\begin{equation}
	P\left(Y^{a=1}=1\right)=P\left(Y^{a=1}=1|A=1\right) \implies 
	P\left(Y^{a=1}=1\right)=P\left(Y=1|A=1\right) 
	\label{basic2}
\end{equation} 
$P\left(Y^{a=1}=1\right)$ in the equation \eqref{basic2} is the probability of 
death if the whole population is given the treatment. So, it is a causation 
measure. $P\left(Y=1|A=1\right)$ in the same equation is the probability of death 
in the treatment group. So, it is an associational measure. Therefore, 
randomization makes the association measure equal to the causation measure. 
$P\left(Y^{a=1}=1\right)$ is not available from data. It is an unobserved 
counterfactual. Thanks to the randomization that it is equal to 
$P\left(Y=1|A=1\right)$.

The resultant equality in the equation \eqref{basic} implies the following: 
\begin{equation} 
	P\left(Y^{a=0}=1\right)=P\left(Y^{a=0}=1|A=0\right) \implies 
	P\left(Y^{a=0}=1\right)=P\left(Y=1|A=0\right) 
	\label{basic3}
\end{equation}
$P\left(Y^{a=0}=1\right)$ in the equation \eqref{basic3} is the probability of 
death if the population is not given the treatment. Hence, it is a causation 
measure. $P\left(Y=1|A=0\right)$ in the same equation is the probability of 
death in the non-treatment group. This is an associational measure. So, 
randomization enables the association measure and the causation measure to be 
the same. $P\left(Y^{a=0}=1\right)$ cannot be calculated from the available data. 
However, randomization allows it to be equal to $P\left(Y=1|A=0\right)$. 

## 3. The Operation Representing Randomization In Pearlian Framework Of Causality <a name="thirdSection"></a>
In the causal inference framework of Judea Pearl or in the Pearlian framework of 
causal inference, if a treatment is randomly applied, then the arrows entering 
the treatment node in the directed acyclic graph (DAG) are removed 
<a href="#primer">[2]</a>. The input to the treatment node will be from an 
exogenous variable which applies the treatment randomly. Will association be 
equal to causation in this setting? When the incoming arrows of the treatment 
node are removed, is there a possibility that there is a non-causal unblocked 
path from the treatment to the outcome? There will absolutely be at least one 
outgoing arrow from the treatment node. If there are more than one, then the same 
consideration for one of the outgoing arrows is valid for the rest. The outgoing 
arrow can be a part of either a collider or a chain. It cannot be a part of a 
fork because the center node of a fork does not accept incoming arrows. If the 
outgoing arrow is a part of a collider, then this path will be blocked. So, in 
this case, there is not a non-causal unblocked path from the treatment to 
the outcome. If the outgoing arrow is a part of a chain then, this will contribute 
to a causal path, not to a non-causal path. For the case of a chain, the same 
reasoning for the treatment node is employed for the center node of the chain. 
The outgoing row from the center node can be a part of a collider or a chain. 
Hence, this outgoing row can only contribute to a causal path, not to a 
non-causal path. Going on in this fashion, it can be seen that there cannot be 
a non-causal unblocked path from the randomized treatment node to the outcome. 
There can only be a causal unblocked path. This fact implies that 
\begin{equation}
	P\left(y|do\left(t\right)\right)=P\left(y|t\right)
\end{equation}
This is the mathematical expression in the Judea Pearl framework of causal inference for the fact that association is causation when the treatment is 
randomized. 

## 4. Conclusion 
It has been shown that randomization allows association to be equal to causation. 
The operation which represents randomization in the causal inference framework of 
Judea Pearl has been stated. It has been proven that this operation in the causal 
inference framework of Judea Pearl makes association equal to causation.

## References
<span id="whatif"> [1] Hernán MA, Robins JM (2020). [*Causal Inference: What If*](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/). Boca Raton: Chapman & Hall/CRC. </span>

<span id="primer"> [2] Judea Pearl, Madelyn Glymour, Nicholas P. Lewell, *Causal Inference in Statistics: A Primer*, Wiley, 2016.</span>
