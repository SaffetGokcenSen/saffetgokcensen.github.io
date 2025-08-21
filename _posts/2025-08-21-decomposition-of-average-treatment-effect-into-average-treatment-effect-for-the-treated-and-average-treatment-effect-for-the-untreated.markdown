---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Decomposition Of Average Treatment Effect (ATE) Into Average Treatment Effect For The Treated (ATT) And Average Treatment Effect For The Untreated (ATU)
--- 

## Introduction 
Causal inference has two frameworks. One of them is the Pearlian framework and 
the other is the potential outcome framework. In this article, some work related to the potential outcome framework will be done. The average treatment 
effect (ATE) will be decomposed into the average treatment effect for the 
treated (ATT) and the average treatment effect for the untreated (ATU). The 
symbols used in the article are like the ones in <a href="#mixtape">[1]</a>.

## Decomposition 
The average treatment effect is given by the following: 
\begin{equation} 
\text{ATE} = E\left[\delta_{i}\right] 
\end{equation} 
$\delta_{i}$ is the unit specific causal effect. It is defined as follows: 
\begin{equation} 
\delta_{i} = Y_{i}^{1} - Y_{i}^{0}
\end{equation} 
$Y_{i}^{1}$ is the response of the unit $i$ to the treatment. $Y_{i}^{0}$ is 
the response of the unit $i$ to the untreatment. If a unit $i$ is treated, then 
this is represented as 
\begin{equation} 
D_{i}=1 
\end{equation} 
On the other hand, if a unit $i$ is untreated or in the control group, then 
this is denoted by the following: 
\begin{equation} 
D_{i}=0 
\end{equation} 
Let the average treatment effect be written in a more detailed way: 
\begin{gather} 
\text{ATE} = E\left[Y_{i}^{1}-Y_{i}^{0}\right]=E\left[Y_{i}^{1}\right]-
E\left[Y_{i}^{0}\right]=\sum_{i} y_{i}^{1} P\left(y_{i}^{1}\right)-
\sum_{i}y_{i}^{0}P\left(y_{i}^{0}\right)= \newline 
\sum_{i}y_{i}^{1} \left(P\left(y_{i}^{1}, D_{i}=0\right)+P\left(y_{i}^{1}, 
D_{i}=1\right)\right) - \sum_{i} y_{i}^{0} \left(P\left(y_{i}^{0}, 
D_{i}=0\right)+P\left(y_{i}^{0}, D_{i}=1\right)\right)= \newline 
\sum_{i} y_{i}^{1}P\left(y_{i}^{1}, D_{i}=0\right) +
\sum_{i} y_{i}^{1}P\left(y_{i}^{1}, D_{i}=1\right) - 
\sum_{i} y_{i}^{0}P\left(y_{i}^{0}, D_{i}=0\right) -
\sum_{i} y_{i}^{0}P\left(y_{i}^{0}, D_{i}=1\right)= \newline 
\sum_{i}y_{i}^{1} P\left(y_{i}^{1}|D_{i}=0\right) P\left(D_{i}=0\right) +
\sum_{i}y_{i}^{1} P\left(y_{i}^{1}|D_{i}=1\right) P\left(D_{i}=1\right) -
\sum_{i}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=0\right) P\left(D_{i}=0\right) -
\sum_{i}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=1\right) P\left(D_{i}=1\right) 
\label{eqn1}
\end{gather} 
Each addend in the sum in the equation \eqref{eqn1} is expanded into terms 
involving the units in the treated group and in the untreated (control) group. 
Let each expansion be made as follows: 
\begin{gather} 
\sum_{i}y_{i}^{1} P\left(y_{i}^{1}|D_{i}=0\right) P\left(D_{i}=0\right) = 
\sum_{\text{treated}}y_{i}^{1} P\left(y_{i}^{1}|D_{i}=0\right) 
\underbrace{P\left(D_{i}=0\right)}\_{0}+
\sum_{\text{untreated}}y_{i}^{1} P\left(y_{i}^{1}|D_{i}=0\right) 
\underbrace{P\left(D_{i}=0\right)}\_{1-p}= 
\left(1-p\right)\sum_{\text{untreated}}y_{i}^{1} 
P\left(y_{i}^{1}|D_{i}=0\right) \newline
\sum_{i}y_{i}^{1} P\left(y_{i}^{1}|D_{i}=1\right) P\left(D_{i}=1\right)= 
\sum_{\text{treated}} y_{i}^{1} P\left(y_{i}^{1}|D_{i}=1\right) 
\underbrace{P\left(D_{i}=1\right)}\_{p}+
\sum_{\text{untreated}}y_{i}^{1} P\left(y_{i}^{1}|D_{i}=1\right) 
\underbrace{P\left(D_{i}=1\right)}\_{0}=p \sum_{\text{treated}} y_{i}^{1} 
P\left(y_{i}^{1}|D_{i}=1\right) \newline 
\sum_{i}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=0\right) P\left(D_{i}=0\right)=
\sum_{\text{treated}}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=0\right) 
\underbrace{P\left(D_{i}=0\right)}\_{0}+
\sum_{\text{untreated}}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=0\right) 
\underbrace{P\left(D_{i}=0\right)}\_{1-p}=\left(1-p\right) 
\sum_{\text{untreated}}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=0\right) \newline
\sum_{i}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=1\right) P\left(D_{i}=1\right) =
\sum_{\text{treated}}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=1\right) 
\underbrace{P\left(D_{i}=1\right)}\_{p} +
\sum_{\text{untreated}}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=1\right) 
\underbrace{P\left(D_{i}=1\right)}\_{0}=p
\sum_{\text{treated}}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=1\right) 
\end{gather} 
Let each expansion result be put into the equation \eqref{eqn1}: 
\begin{gather} 
\text{ATE}=
\left(1-p\right) 
\sum_{\text{untreated}} y_{i}^{1} P\left(y_{i}^{1}|D_{i}=0\right) + 
p \sum_{\text{treated}} y_{i}^{1} P\left(y_{i}^{1}|D_{i}=1\right) - 
\left(1-p\right) 
\sum_{\text{untreated}}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=0\right) - 
p \sum_{\text{treated}}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=1\right) \implies 
\newline 
\text{ATE} = p \left(\sum_{\text{treated}} y_{i}^{1} 
P\left(y_{i}^{1}|D_{i}=1\right) - \sum_{\text{treated}}y_{i}^{0} 
P\left(y_{i}^{0}|D_{i}=1\right)\right) + 
\left(1-p\right)\left(\sum_{\text{untreated}} y_{i}^{1} P\left(y_{i}^{1}|D_{i}=0\right)-\sum_{\text{untreated}}y_{i}^{0} P\left(y_{i}^{0}|D_{i}=0\right)\right) \implies \newline
\text{ATE}=p\left(\text{ATT}\right)+\left(1-p\right)\left(\text{ATU}\right)
\end{gather}
As a result, the decomposition of the average treatment effect into the average 
treatment effect for the treated and the average treatment effect for the 
untreated has been completed. 

## Conclusion 
The decomposition of the average treatment effect into the average treatment 
effect for the treated and the average treatment effect for the untreated has 
been performed. 

## References 
<span id="Mixtape"> [1] [Scott Cunningham, Causal Inference The Mixtape.](https://mixtape.scunning.com/)</span>
