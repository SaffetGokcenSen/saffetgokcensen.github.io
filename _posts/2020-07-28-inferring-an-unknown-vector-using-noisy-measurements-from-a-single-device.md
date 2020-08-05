---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Inferring An Unknown Vector Using Noisy Measurements From A Single Device
---

## Introduction

In this article, a linear Gaussian system is used to infer an unknown vector from noisy measurements obtained by a single measurement source. A sample implementation is in a Jupyter notebook on the link given in the conclusion section.

## Problem Description
There is an unknown vector $\mathbf{x}$. It has a multivariate Gaussian distribution. This distribution is called the prior and given by
\begin{equation}
    p\left(\mathbf{x}\right)=N\left(\boldsymbol{\mu}\_{0}, \boldsymbol{\Sigma}\_{0}\right)
\end{equation}
There are $N$ measurements from a single measurement device. The likelihood is as follows:
\begin{equation}
    p\left(\mathbf{y}\_{i}|\mathbf{x}\right)=N\left(\mathbf{x}, \boldsymbol{\Sigma}\_{y}\right)
\end{equation}
where $\mathbf{y}\_{i}$ is a single measurement. Since there is a single measurement device, there is only one covariance for the measurements. There are $N$ independent measurements. The mean of these $N$ measurements is taken as the final measurement:
\begin{equation}
    \bar{\mathbf{y}}=\frac{1}{N}\sum\_{i=1}^{N}\mathbf{y}\_{i}
\end{equation}

## Solution
Let the mean and the covariance of the random vector $\bar{\mathbf{y}}$ be determined. The measurements are assumed to be independent. $\mathbf{\bar{y}}$ is multivariate Gaussian. Its mean is derived as follows:
\begin{equation}
    \text{E}\left[\mathbf{\bar{y}}\right]=\text{E}\left[\frac{1}{N}\sum\_{i=1}^{N}\mathbf{y}\_{i}\right]=\frac{1}{N}\sum\_{i=1}^{N}\text{E}\left[\mathbf{y}\_{i}\right]=\frac{1}{N}\sum\_{i=1}^{N}\mathbf{x}\Rightarrow
\end{equation}
\begin{equation}
    \text{E}\left[\mathbf{\bar{y}}\right]=\mathbf{x}
\end{equation}
Its covariance is derived as follows:
\begin{equation}
    \text{Cov}\left(\mathbf{\bar{y}}\right)=\text{E}\left[\left(\bar{\mathbf{y}}-\text{E}\left[\bar{\mathbf{y}}\right]\right)\left(\bar{\mathbf{y}}-\text{E}\left[\bar{\mathbf{y}}\right]\right)^{T}\right]=\text{E}\left[\left(\bar{\mathbf{y}}-\mathbf{x}\right)\left(\bar{\mathbf{y}}-\mathbf{x}\right)^{T}\right]=
\end{equation}
\begin{equation}
    \text{E}\left[\left(\bar{\mathbf{y}}-\mathbf{x}\right)\left(\bar{\mathbf{y}}^{T}-\mathbf{x}^{T}\right)\right]=\text{E}\left[\bar{\mathbf{y}}\bar{\mathbf{y}}^{T}-\bar{\mathbf{y}}\mathbf{x}^{T}-\mathbf{x}\bar{\mathbf{y}}^{T}+\mathbf{x}\mathbf{x}^{T}\right]=
\end{equation}
\begin{equation}
    \text{E}\left[\bar{\mathbf{y}}\bar{\mathbf{y}}^{T}\right]-\text{E}\left[\bar{\mathbf{y}}\right]\mathbf{x}^{T}-\mathbf{x}\text{E}\left[\bar{\mathbf{y}}^{T}\right]+\mathbf{x}\mathbf{x}^{T}=\text{E}\left[\bar{\mathbf{y}}\bar{\mathbf{y}}^{T}\right]-\mathbf{x}\mathbf{x}^{T}-\mathbf{x}\mathbf{x}^{T}+\mathbf{x}\mathbf{x}^{T} \Rightarrow
\end{equation}
\begin{equation}
    \text{Cov}\left(\mathbf{\bar{y}}\right)=\text{E}\left[\bar{\mathbf{y}}\bar{\mathbf{y}}^{T}\right]-\mathbf{x}\mathbf{x}^{T}
\end{equation}
Let $\text{E}\left[\bar{\mathbf{y}}\bar{\mathbf{y}}^{T}\right]$ be calculated:
\begin{equation}
    \text{E}\left[\bar{\mathbf{y}}\bar{\mathbf{y}}^{T}\right]=\text{E}\left[\frac{1}{N}\sum\_{i=1}^{N}\mathbf{y}\_{i}\frac{1}{N}\sum\_{j=1}^{N}\mathbf{y}\_{j}^{T}\right]=\frac{1}{N^{2}}\text{E}\left[\sum\_{i=1}^{N}\sum\_{j=1}^{N}\mathbf{y}\_{i}\mathbf{y}\_{j}^{T}\right]=
\end{equation}
\begin{equation}
    \frac{1}{N^{2}}\text{E}\left[\sum\_{i=1}^{N}\sum\_{j=1}^{N}\left(\mathbf{y}\_{i}-\text{E}\left[\mathbf{y}\_{i}\right]+\text{E}\left[\mathbf{y}\_{i}\right]\right)\left(\mathbf{y}\_{j}-\text{E}\left[\mathbf{y}\_{j}\right]+\text{E}\left[\mathbf{y}\_{j}\right]\right)^{T}\right]=
\end{equation}
\begin{equation}
    \frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\left(\mathbf{y}\_{i}-\mathbf{x}+\mathbf{x}\right)\left(\mathbf{y}\_{j}-\mathbf{x}+\mathbf{x}\right)^{T}\right]=
\end{equation}
\begin{equation}
    \frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\left(\mathbf{y}\_{i}-\mathbf{x}+\mathbf{x}\right)\left(\mathbf{y}\_{j}-\mathbf{x}+\mathbf{x}\right)^{T}\right] \Rightarrow
\end{equation}
\begin{equation}
    \text{E}\left[\bar{\mathbf{y}}\bar{\mathbf{y}}^{T}\right]=\frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\left(\mathbf{y}\_{i}-\mathbf{x}\right)\left(\mathbf{y}\_{j}-\mathbf{x}\right)^{T}\right]+
\end{equation}
\begin{equation}
    \frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\left(\mathbf{y}\_{i}-\mathbf{x}\right)\mathbf{x}^{T}\right]+\frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\mathbf{x}\left(\mathbf{y}\_{j}-\mathbf{x}\right)^{T}\right]+\frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\mathbf{x}\mathbf{x}^{T}\right]
\end{equation}
Each of the terms are calculated:
\begin{equation}
    \frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\left(\mathbf{y}\_{i}-\mathbf{x}\right)\left(\mathbf{y}\_{j}-\mathbf{x}\right)^{T}\right]=\frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{Cov}\left(\mathbf{y}\_{i}\right)\delta\left[i-j\right]=\frac{1}{N^{2}}N\text{Cov}\left[\mathbf{y}\_{i}\right]\Rightarrow
\end{equation}
\begin{equation}
    \frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\left(\mathbf{y}\_{i}-\mathbf{x}\right)\left(\mathbf{y}\_{j}-\mathbf{x}\right)^{T}\right]=\frac{1}{N}\boldsymbol{\Sigma}\_{y}
\end{equation}
\begin{equation}
    \frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\left(\mathbf{y}\_{i}-\mathbf{x}\right)\mathbf{x}^{T}\right]=\mathbf{0}
\end{equation}
\begin{equation}
    \frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\mathbf{x}\left(\mathbf{y}\_{j}-\mathbf{x}\right)^{T}\right]=\mathbf{0}
\end{equation}
\begin{equation}
    \frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\mathbf{x}\mathbf{x}^{T}\right]=\frac{1}{N^{2}}N^{2}\text{E}\left[\mathbf{x}\mathbf{x}^{T}\right] \Rightarrow
\end{equation}
\begin{equation}
    \frac{1}{N^{2}}\sum\_{i=1}^{N}\sum\_{j=1}^{N}\text{E}\left[\mathbf{x}\mathbf{x}^{T}\right]=\text{E}\left[\mathbf{x}\mathbf{x}^{T}\right]
\end{equation}
Then:
\begin{equation}
    \text{E}\left[\mathbf{y}\mathbf{y}^{T}\right]=\frac{1}{N}\boldsymbol{\Sigma}\_{y}+\mathbf{0}+\mathbf{0}+\text{E}\left[\mathbf{x}\mathbf{x}^{T}\right]\Rightarrow
\end{equation}
\begin{equation}
    \text{Cov}\left(\bar{\mathbf{y}}\right)=\frac{1}{N}\boldsymbol{\Sigma}\_{y}+\mathbf{0}+\mathbf{0}+\text{E}\left[\mathbf{x}\mathbf{x}^{T}\right]-\text{E}\left[\mathbf{x}\mathbf{x}^{T}\right]\Rightarrow
\end{equation}
\begin{equation}
    \text{Cov}\left(\bar{\mathbf{y}}\right)=\frac{1}{N}\boldsymbol{\Sigma}\_{y}
\end{equation}
Hence, $\bar{\mathbf{y}}$ has the following likelihood:
\begin{equation}
    p\left(\bar{\mathbf{y}}|\mathbf{x}\right)=N\left(\mathbf{x},\frac{1}{N}\boldsymbol{\Sigma}\_{y}\right)
\end{equation}
The prior $p\left(\mathbf{x}\right)$ and the likelihood $p\left(\bar{\mathbf{y}}|\mathbf{x}\right)$ are known. The posterior $p\left(\mathbf{x}|\bar{\mathbf{y}}\right)$ is to be obtained. Given the prior $N\left(\mathbf{x}|\boldsymbol{\mu}\_{x}, \boldsymbol{\Sigma}\_{x}\right)$ and the likelihood $N\left(\mathbf{y}|\mathbf{A}\mathbf{x}+\mathbf{b}, \boldsymbol{\Sigma}\_{y}\right)$, it is known that the posterior $p\left(\mathbf{x}|\mathbf{y}\right)$ is given by either of the following two forms:
\begin{equation}
    p\left(\mathbf{x}|\mathbf{y}\right)=N\left(\mathbf{x}|\left(\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x|y}\right)\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{x|y}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}, \boldsymbol{\Sigma}\_{x|y}\right) \ \text{(first form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\Sigma}\_{x} \ \text{(first form)}
\end{equation}
\begin{equation}
    p\left(\mathbf{x}|\mathbf{y}\right)=N\left(\mathbf{x}|\boldsymbol{\Sigma}\_{x|y}\left[\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right], \boldsymbol{\Sigma}\_{x|y}\right) \ \text{(second form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1} \ \text{(second form)}
\end{equation}
For the problem to be solved, $\boldsymbol{\mu}\_{x}=\boldsymbol{\mu}\_{0}$, $\boldsymbol{\Sigma}\_{x}=\boldsymbol{\Sigma}\_{0}$, $\mathbf{A}=\mathbf{I}$, $\mathbf{b}=\mathbf{0}$ and the covariance of the likelihood is $\frac{1}{N}\boldsymbol{\Sigma}\_{y}$. When these quantities are used in their places, two forms for the posterior are obtained as follows:
\begin{equation}
    p\left(\mathbf{x}|\bar{\mathbf{y}}\right)=N\left(\mathbf{x}|\left(\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x|y}\right)\boldsymbol{\Sigma}\_{x}^{-1}\bar{\mathbf{y}}+\boldsymbol{\Sigma}\_{x|y}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{0}, \boldsymbol{\Sigma}\_{x|y}\right) \ \text{(first form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\left(\boldsymbol{\Sigma}\_{y}/N+\boldsymbol{\Sigma}\_{x}\right)^{-1}\boldsymbol{\Sigma}\_{x} \ \text{(first form)}
\end{equation}
\begin{equation}
    p\left(\mathbf{x}|\bar{\mathbf{y}}\right)=N\left(\mathbf{x}|\boldsymbol{\Sigma}\_{x|y}\left(\left(\boldsymbol{\Sigma}\_{y}/N\right)^{-1}\bar{\mathbf{y}}+\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right), \boldsymbol{\Sigma}\_{x|y}\right) \ \text{(second form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\left(\boldsymbol{\Sigma}\_{y}/N\right)^{-1}\right)^{-1} \ \text{(second form)}
\end{equation}

## Conclusion
Given the prior for an unknown vector and the likelihood for the noisy measurements of it from a single measurement device, the posterior for the unknown vector has been calculated using a Gaussian linear system. A sample implementation is given in the Jupyter notebook on [this link](https://github.com/SaffetGokcenSen/Gaussian-Models/blob/master/inferring_an_unknown_vector_from_noisy_measurements.ipynb).

## References
[1] Machine Learning A Probabilistic Perspective, Kevin P. Murphy.

[2] Bayes Rule For A Linear Gaussian System, <https://saffetgokcensen.github.io/blog/2020/07/08/bayes-rule-for-a-linear-gaussian-system>
