---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Inferring The Covariance Of A Multivariate Normal Distribution With Known Mean From The Available Data
---
## Introduction
It is assumed that there is a set of vector data. These vectors are assumed to be from a multivariate Gaussian distribution:
\begin{equation}
    \textbf{x}\_{i} \sim N\left(\boldsymbol{\mu}, \boldsymbol{\Sigma}\right) \ \left(i=1, 2, 3, \dotso , N\right)
\end{equation}
It is assumed that $\boldsymbol{\mu}$ is known while $\boldsymbol{\Sigma}$ is unknown. First, the likelihood of the data given the mean and the covariance will be obtained. Then, the prior for the covariance will be set. Lastly, the posterior distribution of $\boldsymbol{\Sigma}$ is to be obtained. 
## The Likelihood
The likelihood is the probability of the occurrence of the data at hand. In the calculation of the likelihood, data samples are supposed to be independent. The likelihood is denoted by $p\left(\textbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)$ and has the following mathematical expression:
\begin{equation}
    p\left (\textbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma} \right)=p\left(\textbf{x}\_{1}, \textbf{x}\_{2}, \textbf{x}\_{3}, \dotso , \textbf{x}\_{N}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right )=\prod\_{i=1}^{N} p\left(\textbf{x}\_{i}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=
\end{equation}
\begin{equation}
    \prod\_{i=1}^{N}\frac{1}{\left(2\pi\right)^{D/2}\left | \boldsymbol{\Sigma}\right |^{1/2}}\exp \left[-\frac{1}{2}\left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1} \left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    p\left (\textbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma} \right)=\frac{1}{\left(2\pi\right)^{ND/2}\left | \boldsymbol{\Sigma}\right |^{N/2}}\exp \left[\sum\_{i=1}^{N}-\frac{1}{2}\left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1} \left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)\right]
    \label{likelihood\_1}
\end{equation}
The inverse Wishart distribution is a choice for the prior of the covariance of a multivariate normal distribution. There can be other choices as the prior. In this article, the inverse Wishart distribution is to be used as the prior. Hence, the likelihood is to be made similar to the inverse Wishart distribution by rearranging the exponent. In this rearrangement, a relation from the matrix algebra will be used. The relation is as follows:
\begin{equation}
    \sum\_{i=1}^{N}\mathbf{b}\_{i}^{T}\mathbf{A}\mathbf{b}\_{i}=\text{Tr} \left(\mathbf{B}^{T}\mathbf{B}\mathbf{A}\right)
\end{equation}
where the $i^{\text{th}}$ column of $\mathbf{B}^{T}$ is $\mathbf{b}\_{i}$:
\begin{equation}
    \mathbf{B}^{T}=\begin{bmatrix}
        \mathbf{b}\_{1} & \mathbf{b}\_{2} & \dotso & \mathbf{b}\_{n}
    \end{bmatrix}
\end{equation}
Using this relation, let the exponent be rearranged as follows:
\begin{equation}
    \sum\_{i=1}^{N}-\frac{1}{2}\left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1} \left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)=-\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\mu}\boldsymbol{\Sigma}^{-1}\right)
\end{equation}
where
\begin{equation}
    \mathbf{S}\_{\mu}=\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}.
\end{equation}
Hence, the likelihood is written as follows:
\begin{equation}
    p\left (\textbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma} \right)=\frac{1}{\left(2\pi\right)^{ND/2}\left | \boldsymbol{\Sigma}\right |^{N/2}}\exp \left[\sum\_{i=1}^{N}-\frac{1}{2}\left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1} \left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    p\left (\textbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma} \right)=\frac{1}{\left(2\pi\right)^{ND/2}\left | \boldsymbol{\Sigma}\right |^{N/2}}\exp \left[-\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\mu}\boldsymbol{\Sigma}^{-1}\right)\right].
    \label{likelihood2}
\end{equation}
## The Posterior
The prior for the covariance of a multivariate Gaussian distribution can be chosen in several ways. This is a subject of ongoing research. In this article, the inverse Wishart distribution is to be used as the prior. The inverse Wishart distribution is a conjugate prior to the likelihood. It has the following probability density function:
\begin{equation}
    \text{IW}\left(\mathbf{X}| \boldsymbol{\Psi}, \nu\right)=\frac{\left \vert \boldsymbol{\Psi} \right \vert^{\nu / 2}}{2^{\nu p /2}\Gamma\_{p}\left(\frac{\nu}{2}\right)}\left \vert \mathbf{X} \right \vert^{-\left(\nu + p + 1\right)/2}\exp \left[-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\mathbf{X}^{-1}\right)\right]
    \label{inverse\_Wishart}
\end{equation}
where $\mathbf{X}$ and $\boldsymbol{\Psi}$ are $p \times p$ positive definite matrices, $\nu > p-1$. $\boldsymbol{\Psi}$ is called the scale matrix and $\nu$ is the degrees of freedom. $\Gamma\_{p}$ denotes the multivariate Gamma function.

If the equation (\ref{likelihood2}) and (\ref{inverse\_Wishart}) are compared, then it can be observed that they have the same exponential dependence.

Let the prior for the covariance of the multivariate normal distribution be set using the inverse Wishart distribution as follows:
\begin{equation}
    p\left(\boldsymbol{\Sigma}\right)=\frac{\left \vert \mathbf{S}\_{0} \right \vert^{\nu\_{0} / 2}}{2^{\nu\_{0} D /2}\Gamma\_{D}\left(\frac{\nu\_{0}}{2}\right)}\left \vert \boldsymbol{\Sigma} \right \vert^{-\left(\nu\_{0} + D + 1\right)/2}\exp \left[-\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{0}\boldsymbol{\Sigma}^{-1}\right)\right]
    \label{prior}
\end{equation}
The posterior for the covariance, $p \left(\boldsymbol{\Sigma}|\mathbf{X}, \boldsymbol{\mu}\right)$, is the normalized product of the prior and the likelihood:
\begin{equation}
    p \left(\boldsymbol{\Sigma}|\mathbf{X}, \boldsymbol{\mu}\right)=\frac{p\left(\boldsymbol{\Sigma}\right)p\left (\textbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma} \right)}{p\left(\mathbf{X}|\boldsymbol
    \mu\right)} \Rightarrow
\end{equation}
\begin{equation}
    p \left(\boldsymbol{\Sigma}|\mathbf{X}, \boldsymbol{\mu}\right) \propto p\left(\boldsymbol{\Sigma}\right)p\left (\textbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma} \right) =
\end{equation}
\begin{equation}
    \left \vert \boldsymbol{\Sigma} \right \vert^{-\left(\nu\_{0} + D + 1\right)/2}\exp \left[-\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{0}\boldsymbol{\Sigma}^{-1}\right)\right]\left | \boldsymbol{\Sigma}\right |^{-N/2}\exp \left[-\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\mu}\boldsymbol{\Sigma}^{-1}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    p \left(\boldsymbol{\Sigma}|\mathbf{X}, \boldsymbol{\mu}\right) \propto \left \vert \boldsymbol{\Sigma} \right \vert^{-\left(N+\nu\_{0} + D + 1\right)/2} \exp\left[-\frac{1}{2}\text{Tr}\left(\left(\mathbf{S}\_{\mu}+\mathbf{S}\_{0}\right)\boldsymbol{\Sigma}^{-1}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    p \left(\boldsymbol{\Sigma}|\mathbf{X}, \boldsymbol{\mu}\right) = \text{IW} \left(\boldsymbol{\Sigma}|\left(\mathbf{S}\_{0}+\mathbf{S}\_{\mu}\right), \left(\nu\_{0}+N\right)\right)
\end{equation}
So, if the prior is chosen as an inverse Wishart distribution, then the posterior is also an inverse Wishart distribution. Hence, it has been shown that the inverse Wishart distribution is conjugate prior to the likelihood for the covariance of a multivariate normal distribution.
## Conclusion
The prior for the covariance of a multivariate normal distribution can be chosen in different ways. It has been shown that the inverse Wishart distribution is conjugate prior to the likelihood for the covariance of a multivariate normal distribution.
## References
Inverse Wishart Distribution, Wikipedia.

A First Course In Bayesian Statistical Methods, Peter D. Hoff.

Pattern Recognition and Machine Learning, Christopher M. Bishop.

Machine Learning A Probabilistic Perspective, Kevin P. Murphy.