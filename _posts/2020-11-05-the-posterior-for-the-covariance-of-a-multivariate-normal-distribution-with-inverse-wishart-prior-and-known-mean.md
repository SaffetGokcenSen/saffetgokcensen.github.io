---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: The Posterior For The Covariance Of A Multivariate Normal Distribution With Inverse Wishart Prior And Known Mean
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
    \label{posterior\_distribution}
\end{equation}
So, if the prior is chosen as an inverse Wishart distribution, then the posterior is also an inverse Wishart distribution. Hence, it has been shown that the inverse Wishart distribution is conjugate prior to the likelihood for the covariance of a multivariate normal distribution.
## Maximum Likelihood Estimate Versus Maximum A Posteriori Estimate
The maximum likelihood estimate (MLE) for the covariance of a multivariate normal distribution is given as follows:
\begin{equation}
    \boldsymbol{\Sigma}\_{\_{\text{MLE}}}=\frac{1}{N}\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}-\bar{\mathbf{x}}\right)\left(\mathbf{x}\_{i}-\bar{\mathbf{x}}\right)^{T}
\end{equation}
$\bar{\mathbf{x}}$ is the maximum likelihood estimation for the mean of the distribution:
\begin{equation}
    \bar{\mathbf{x}}=\boldsymbol{\mu}\_{\_{\text{MLE}}}=\frac{1}{N}\sum\_{i=1}^{N}\mathbf{x}\_{i}
\end{equation}
The MLE for the covariance matrix must be a positive definite matrix. Hence, for any nonzero $\mathbf{p} \in R^{D}$, the following relation must be satisfied:
\begin{equation}
    \mathbf{p}^{T}\boldsymbol{\Sigma}\_{\_{\text{MLE}}}\mathbf{p}>0
\end{equation}
Let the conditions for which the MLE is positive definite be determined. Let the MLE be written in a more compact form. In order to achieve this, let the matrix $\mathbf{G}$ be defined as follows:
\begin{equation}
    \mathbf{G}=\begin{bmatrix}
        \left(\mathbf{x}\_{1}-\bar{\mathbf{x}}\right) & \left(\mathbf{x}\_{2}-\bar{\mathbf{x}}\right ) & \dotso & \left(\mathbf{x}\_{N}-\bar{\mathbf{x}}\right )
    \end{bmatrix}.
\end{equation}
Then, the MLE can be expressed as follows:
\begin{equation}
    \boldsymbol{\Sigma}\_{\_{\text{MLE}}}=\frac{1}{N}\mathbf{G}\mathbf{G}^{T}
\end{equation}
The condition for positive definiteness can be written as in the following form:
\begin{equation}
    \mathbf{p}^{T}\boldsymbol{\Sigma}\_{\_{\text{MLE}}}\mathbf{p}>0 \Rightarrow \mathbf{p}^{T}\frac{1}{N}\mathbf{G}\mathbf{G}^{T}\mathbf{p}>0 \Rightarrow \mathbf{p}^{T}\mathbf{G}\mathbf{G}^{T}\mathbf{p}>0 \Rightarrow \left(\mathbf{G}^{T}\mathbf{p}\right)^{T}\left(\mathbf{G}^{T}\mathbf{p}\right) > 0 \Rightarrow
\end{equation}
\begin{equation}
    \| \mathbf{G}^{T}\mathbf{p} \|^{2}>0 \label{positive\_definiteness}
\end{equation}
If the equality in equation (\ref{positive\_definiteness}) is to hold for any nonzero $\mathbf{p} \in R^{D}$, then $\mathbf{G}^{T}\mathbf{p}$ must never vanish, which means that the columns of $\mathbf{G}^{T}$ must be linearly independent. $\mathbf{G}$ is of dimension $D \times N$. $\mathbf{G}^{T}$ is of dimension $N \times D$. If $N < D$, it is impossible for the columns of $\mathbf{G}^{T}$ to be linearly independent. So, if the number of data samples is less than the number of features, the MLE cannot be positive definite. If $N\geq D$, the columns of the MLE may be linearly independent, but they are not guaranteed to be linearly independent. Hence, if the number of samples is greater than or equal to the number of features, the MLE is not guaranteed to be positive definite.

An alternative to the MLE for the covariance is the maximum a posteriori (MAP) estimate. It is the mode of the posterior distribution for the covariance of the multivariate normal distribution. Provided the prior is an inverse Wishart distribution with scale matrix $\mathbf{S}\_{0}$ and degrees of freedom $\nu\_{0}$, the posterior distribution has been determined to be an inverse Wishart distribution with scale matrix $\mathbf{S}\_{0}+\mathbf{S}\_{\mu}$ and degrees of freedom $\nu\_{0}+N$. The mode of this distribution is
\begin{equation}
    \frac{\mathbf{S}\_{0}+\mathbf{S}\_{\mu}}{\nu\_{0}+N+D+1},
\end{equation}
which is the MAP estimate for the covariance.

An immediate question is about if the MAP estimate is guaranteed to be positive definite. The inverse Wishart distribution has a support over the positive definite matrices. Hence, the posterior which is an inverse Wishart distribution when the prior is also inverse Wishart must yield a positive definite mode which is the MAP estimate. So, the answer is that the MAP estimate must be positive definite.

The MAP estimate can be written in the following form:
\begin{equation}
    \boldsymbol{\Sigma}\_{\_{\text{MAP}}}=\frac{\mathbf{S}\_{0}+\mathbf{S}\_{\mu}}{\nu\_{0}+N+D+1}=\frac{\nu\_{0}+D+1}{\nu\_{0}+N+D+1}\frac{\mathbf{S}\_{0}}{\nu\_{0}+D+1}+\frac{N}{\nu\_{0}+N+D+1}\frac{\mathbf{S}\_{\mu}}{N}
\end{equation}
If $\frac{\nu\_{0}+D+1}{\nu\_{0}+N+D+1}$ is defined to be $\lambda$, then
\begin{equation}
    \boldsymbol{\Sigma}\_{\_{\text{MAP}}}=\lambda \frac{\mathbf{S}\_{0}}{\nu\_{0}+D+1}+\left(1-\lambda\right)\frac{\mathbf{S}\_{\mu}}{N}
\end{equation}
If there are enough samples, then $\boldsymbol{\Sigma}\_{\_{\text{MLE}}}$ is expected to be close to $\frac{\mathbf{S}\_{\mu}}{N}$. Hence, $\boldsymbol{\Sigma}\_{\_{\text{MAP}}}$ is a compromise between $\frac{\mathbf{S}\_{0}}{\nu\_{0}+D+1}$ and the MLE. $\lambda$ and $\mathbf{S}\_{0}$ are the parameters to be determined. $\lambda$ is usually found using cross validation. The prior covariance matrix $\mathbf{S}\_{0}$ is usually chosen as follows:
\begin{equation}
    \mathbf{S}\_{0}=\text{diag} \left(\boldsymbol{\Sigma}\_{\_{\text{MLE}}}\right)
\end{equation}
## Conclusion
The prior for the covariance of a multivariate normal distribution can be chosen in different ways. It has been shown that the inverse Wishart distribution is conjugate prior to the likelihood for the covariance of a multivariate normal distribution. It has been proven that the maximum likelihood estimator for the covariance is not positive definite when the number of samples is less than the dimension of the data. In addition, it has been shown that the maximum likelihood estimator for the covariance is not guaranteed to be positive definite even when the number of samples is greater than the data dimension. On the other hand, the maximum a posteriori estimate is always positive definite provided that the prior for the covariance is inverse Wishart.
## References
Inverse Wishart Distribution, Wikipedia.

A First Course In Bayesian Statistical Methods, Peter D. Hoff.

Pattern Recognition and Machine Learning, Christopher M. Bishop.

Machine Learning A Probabilistic Perspective, Kevin P. Murphy.
