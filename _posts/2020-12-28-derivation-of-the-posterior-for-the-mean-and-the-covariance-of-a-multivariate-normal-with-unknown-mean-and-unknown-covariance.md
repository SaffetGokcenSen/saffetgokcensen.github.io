---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Derivation Of The Posterior For The Mean And The Covariance Of A Multivariate Normal With Unknown Mean And Unknown Covariance
---
## Introduction
In this article, it is assumed there is a set of vector data which has a multivariate normal (MVN) distribution. The mean and the covariance of this data set are unknown. The aim is to calculate the posterior for the unknown mean and the covariance given the data set. The prior is chosen as the normal-inverse Wishart distribution so that the posterior is in the same mathematical form as the likelihood.
## The Likelihood
The number of samples in the data set is $N$ and the samples are supposed to be independent and identically distributed:
\begin{equation}
    \mathbf{x}\_{i} \sim N\left(\boldsymbol{\mu}, \boldsymbol{\Sigma}\right) \ \left(i=1, 2, 3, \dotso , N\right)
\end{equation}
Let the data set be denoted by $\mathbf{X}$. It is not important whether the data vectors are columns or rows of the matrix $\mathbf{X}$. It can be chosen according to the software package used. The likelihood is the probability of obtaining the data in hand. Due to the independence of the samples, the likelihood is the product of the probabilities of each sample:
\begin{equation}
    p\left(\mathbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=p\left(\mathbf{x}\_{1},\mathbf{x}\_{2}, \dotso , \mathbf{x}\_{N}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=\prod\_{i=1}^{N}p\left(\mathbf{x}\_{i}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=
\end{equation}
\begin{equation}
    \prod\_{i=1}^{N}\frac{1}{\left(2\pi\right)^{D/2}\left |\boldsymbol{\Sigma} \right |^{1/2}}\exp \left[-\frac{1}{2}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    p\left(\mathbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=\frac{1}{\left(2\pi\right)^{ND/2}\left | \boldsymbol{\Sigma} \right |^{N/2}}\exp \left[\sum\_{i=1}^{N} -\frac{1}{2}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)\right]
\end{equation}
The likelihood is to be put into a form which is shape compliant with an existing probability distribution called the normal-inverse Wishart distribution. This form can be achieved by using the following equality:
\begin{equation}
    \sum\_{i=1}^{N}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)=\text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)+N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)
    \label{key\_relation}
\end{equation}
where
\begin{equation}
    \mathbf{S}\_{\overline{\mathbf{x}}}=\sum\_{i=1}^{N} \left(\mathbf{x}\_{i}-\overline{\mathbf{x}}\right)\left(\mathbf{x}\_{i}-\overline{\mathbf{x}}\right)^{T}.
\end{equation}
In proving the validity of this equation, the following relation from linear algebra will be utilized:
\begin{equation}
    \sum\_{i=1}^{N}\mathbf{b}\_{i}^{T}\mathbf{A}\mathbf{b}\_{i}=\text{Tr} \left(\mathbf{B}^{T}\mathbf{B}\mathbf{A}\right)
    \label{basic\_eqn}
\end{equation}
where
\begin{equation}
    \mathbf{B}^{T}=\begin{bmatrix}
        \mathbf{b}\_{1} & \mathbf{b}\_{2} & \dotso & \mathbf{b}\_{N}
    \end{bmatrix}.
\end{equation}
Let the validity of the equation (\ref{key\_relation}) be proven:
\begin{equation}
    \text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)+N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)+\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}-\overline{\mathbf{x}}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}\_{i}-\overline{\mathbf{x}}\right)=
\end{equation}
\begin{equation}
    N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)+\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}-\overline{\mathbf{x}}\right)^{T}\left(\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}-\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}\right)=
\end{equation}
\begin{equation}
    N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)+\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}-\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}-\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}+\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}\right)=
\end{equation}
\begin{equation}
    N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)+\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}-2\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}+\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}\right)=
\end{equation}
\begin{equation}
    N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)+
\end{equation}
\begin{equation}
    \sum\_{i=1}^{N}\left(\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}-2\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}+\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}-2\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}+2\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}+ \right .
\end{equation}
\begin{equation}
    \left . \boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)+
\end{equation}
\begin{equation}
    \sum\_{i=1}^{N}\left(\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}-2\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i} + \boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right ) +
\end{equation}
\begin{equation}
    \sum\_{i=1}^{N}\left(-2\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}+\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}+2\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}-\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)+\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)
\end{equation}
\begin{equation}
    -2N\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}+N\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}+2N\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}-N\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}=
\end{equation}
\begin{equation}
    N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)+\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)-N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)\Rightarrow
\end{equation}
\begin{equation}
    \text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)+N\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\overline{\mathbf{x}}-\boldsymbol{\mu}\right)=\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)
\end{equation}
Now that the relation in the equation (\ref{key\_relation}) has been proven, the likelihood can be written as in the following form:
\begin{equation}
    p\left(\mathbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=\frac{1}{\left(2\pi\right)^{ND/2}\left | \boldsymbol{\Sigma} \right |^{N/2}}\exp \left[\sum\_{i=1}^{N} -\frac{1}{2}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}\_{i}-\boldsymbol{\mu}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    p\left(\mathbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=\frac{1}{\left(2\pi\right)^{ND/2}\left | \boldsymbol{\Sigma} \right |^{N/2}}\exp \left[-\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)\right] \exp \left[-\frac{N}{2}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)\right]
    \label{likelihood}
\end{equation}
The probability density function (pdf) for the normal-inverse-Wishart distribution is defined as follows:
\begin{equation}
    \text{NIW}\left(\boldsymbol{\mu}, \boldsymbol{\Sigma}| \alpha , \boldsymbol{\Psi} , \gamma , \boldsymbol{\delta}\right)=\frac{\gamma^{D/2}\left | \boldsymbol{\Psi}\right |^{\alpha /2}\left | \boldsymbol{\Sigma}\right |^{-\frac{\alpha + D + 2}{2}}}{\left(2\pi\right)^{D/2}2^{\frac{\alpha D}{2}}\Gamma\_{D}\left(\frac{\alpha}{2}\right)}\exp \left[-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\boldsymbol{\Sigma}^{-1}\right)\right]\exp \left[-\frac{\gamma}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right)\right]
    \label{NIW}
\end{equation}
where $\boldsymbol{\mu}\_{0} \in \text{R}^{D}$, $\lambda > 0$, positive definite $\boldsymbol{\Psi} \in \text{R}^{D\times D}$ is the inverse scale matrix and $\nu > D-1$.  
The likelihood in the equation (\ref{likelihood}) and the pdf for the normal-inverse-Wishart in the equation (\ref{NIW}) are seen to be similar to each other if their exponential parts are compared.
## The Posterior
The posterior of the distribution of $\boldsymbol{\mu}$ and $\boldsymbol{\Sigma}$ given the available data $\mathbf{X}$ is to be calculated using the Bayes rule:
\begin{equation}
    p\left(\boldsymbol{\mu}, \boldsymbol{\Sigma}|\mathbf{X}\right)=\frac{p\left(\mathbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)p\left(\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)}{p\left(\mathbf{X}\right)} \Rightarrow
\end{equation}
\begin{equation}
    p\left(\boldsymbol{\mu}, \boldsymbol{\Sigma}|\mathbf{X}\right) \propto p\left(\mathbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)p\left(\boldsymbol{\mu}, \boldsymbol{\Sigma}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(\boldsymbol{\mu}, \boldsymbol{\Sigma}|\mathbf{X}\right) \propto \exp \left[-\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)\right] \exp \left[-\frac{N}{2}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)\right] \times
\end{equation}
\begin{equation}
    \exp \left[-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\_{0}\boldsymbol{\Sigma}^{-1}\right)\right]\exp \left[-\frac{\gamma\_{0}}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)\right]
\end{equation}
The posterior distribution can be written as a normal-inverse Wishart distribution, as well. The parameters of this distribution are to be calculated in terms of those of the prior and the likelihood distributions. Reasoning similar to completing the square operations in Gaussian distributions, first $\gamma$ and $\boldsymbol{\delta}$ will be calculated using the following equality:
\begin{equation}
    -\frac{N}{2}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)-\frac{\gamma\_{0}}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)=-\frac{\gamma}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right) \Rightarrow
\end{equation}
\begin{equation}
    -\frac{N}{2}\left(\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-2\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}+\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}\right)-\frac{\gamma\_{0}}{2}\left(\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-2\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\delta}\_{0}+\boldsymbol{\delta}\_{0}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\delta}\_{0}\right)=
\end{equation}
\begin{equation}
    -\frac{\gamma}{2}\left(\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-2\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\delta}+\boldsymbol{\delta}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\delta}\right) \Rightarrow
\end{equation}
\begin{equation}
    -\frac{N}{2}-\frac{\gamma\_{0}}{2}=-\frac{\gamma}{2}, \, N\overline{\mathbf{x}}+\gamma\_{0}\boldsymbol{\delta}\_{0}=\gamma \boldsymbol{\delta} \Rightarrow
    \label{simplifying\_relations}
\end{equation}
\begin{equation}
    \gamma = N+\gamma\_{0}
\end{equation}
\begin{equation}
    \boldsymbol{\delta}=\frac{N\overline{\mathbf{x}}+\gamma\_{0}\boldsymbol{\delta}\_{0}}{\gamma}
\end{equation}
After determining $\gamma$ and $\delta$, it is now $\boldsymbol{\Psi}$'s turn. $\boldsymbol{\Psi}$ is the inverse scale matrix of the posterior distribution.
\begin{equation}
    \exp \left[-\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)\right] \exp \left[-\frac{N}{2}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)\right] \times
\end{equation}
\begin{equation}
    \exp \left[-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\_{0}\boldsymbol{\Sigma}^{-1}\right)\right]\exp \left[-\frac{\gamma\_{0}}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)\right]=
\end{equation}
\begin{equation}
    \exp \left[-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\boldsymbol{\Sigma}^{-1}\right)\right]\exp \left[-\frac{\gamma}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    \exp \left[-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\boldsymbol{\Sigma}^{-1}\right)\right]=
\end{equation}
\begin{equation}
    \exp \left[-\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)\right] \exp \left[-\frac{N}{2}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)\right] \times
\end{equation}
\begin{equation}
    \exp \left[-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\_{0}\boldsymbol{\Sigma}^{-1}\right)\right]\exp \left[-\frac{\gamma\_{0}}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)\right]\exp \left[\frac{\gamma}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    -\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\boldsymbol{\Sigma}^{-1}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)-\frac{N}{2}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\overline{\mathbf{x}}\right)-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\_{0}\boldsymbol{\Sigma}^{-1}\right)-
\end{equation}
\begin{equation}
    \frac{\gamma\_{0}}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\_{0}\right)+\frac{\gamma}{2}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\delta}\right)
\end{equation}
Using the relations in the equation (\ref{simplifying\_relations}), the following equality is obtained:
\begin{equation}
    -\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\boldsymbol{\Sigma}^{-1}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\_{0}\boldsymbol{\Sigma}^{-1}\right)-\frac{N}{2}\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}-\frac{\gamma\_{0}}{2}\boldsymbol{\delta}\_{0}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\delta}\_{0}+\frac{\gamma}{2}\boldsymbol{\delta}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\delta}
    \label{trace\_eqn\_1}
\end{equation}
The equation (\ref{basic\_eqn}) is used to transform vector outer products to $\text{Tr}$ expressions as follows:
\begin{equation}
    \sum\_{i=1}^{N}\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}=\text{Tr}\left(\begin{bmatrix}
        \overline{\mathbf{x}} & \overline{\mathbf{x}} & \dotso & \overline{\mathbf{x}}
    \end{bmatrix}\begin{bmatrix}
        \overline{\mathbf{x}}^{T} \newline
        \overline{\mathbf{x}}^{T} \newline
        \vdots \newline
        \overline{\mathbf{x}}^{T}
    \end{bmatrix}\right) \Rightarrow
\end{equation}
\begin{equation}
    N\overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}=\text{Tr}\left(N\overline{\mathbf{x}}\, \overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\right) \Rightarrow
\end{equation}
\begin{equation}
    \overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\overline{\mathbf{x}}=\frac{1}{N}\text{Tr}\left(N\overline{\mathbf{x}}\, \overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\right)
\end{equation}
In a similar way, the following equalities can also be reached:
\begin{equation}
    \boldsymbol{\delta}\_{0}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\delta}\_{0}=\frac{1}{N}\text{Tr}\left(N\boldsymbol{\delta}\_{0}\boldsymbol{\delta}\_{0}^{T}\boldsymbol{\Sigma}^{-1}\right)
\end{equation}
\begin{equation}
    \boldsymbol{\delta}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\delta}=\frac{1}{N}\text{Tr}\left(N\boldsymbol{\delta}\boldsymbol{\delta}^{T}\boldsymbol{\Sigma}^{-1}\right)
\end{equation}
Using these equalities, the equation (\ref{trace\_eqn\_1}) can be transformed to the following:
\begin{equation}
    -\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\boldsymbol{\Sigma}^{-1}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\text{Tr}\left(\mathbf{S}\_{\overline{\mathbf{x}}}\boldsymbol{\Sigma}^{-1}\right)-\frac{1}{2}\text{Tr}\left(\boldsymbol{\Psi}\_{0}\boldsymbol{\Sigma}^{-1}\right)-\frac{1}{2}\text{Tr}\left(N\overline{\mathbf{x}}\, \overline{\mathbf{x}}^{T}\boldsymbol{\Sigma}^{-1}\right)-\frac{\gamma\_{0}}{2N}\text{Tr}\left(N\boldsymbol{\delta}\_{0}\boldsymbol{\delta}\_{0}^{T}\boldsymbol{\Sigma}^{-1}\right)+\frac{\gamma}{2N}\text{Tr}\left(N\boldsymbol{\delta}\boldsymbol{\delta}^{T}\boldsymbol{\Sigma}^{-1}\right)
\end{equation}
Then:
\begin{equation}
    -\frac{1}{2}\boldsymbol{\Psi}=-\frac{1}{2}\mathbf{S}\_{\overline{\mathbf{x}}}-\frac{1}{2}\boldsymbol{\Psi}\_{0}-\frac{1}{2}N\overline{\mathbf{x}}\, \overline{\mathbf{x}}^{T}-\frac{\gamma\_{0}}{2N}N\boldsymbol{\delta}\_{0}\boldsymbol{\delta}\_{0}^{T}+\frac{\gamma}{2N}N\boldsymbol{\delta}\boldsymbol{\delta}^{T} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Psi}=\mathbf{S}\_{\overline{\mathbf{x}}}+\boldsymbol{\Psi}\_{0}+N\overline{\mathbf{x}}\, \overline{\mathbf{x}}^{T}+\gamma\_{0}\boldsymbol{\delta}\_{0}\boldsymbol{\delta}\_{0}^{T}-\gamma\boldsymbol{\delta}\boldsymbol{\delta}^{T} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Psi}=\mathbf{S}\_{\overline{\mathbf{x}}}+\boldsymbol{\Psi}\_{0}+N\overline{\mathbf{x}}\, \overline{\mathbf{x}}^{T}+\gamma\_{0}\boldsymbol{\delta}\_{0}\boldsymbol{\delta}\_{0}^{T}-\gamma \frac{\left(N\overline{\mathbf{x}}+\gamma\_{0}\boldsymbol{\delta}\_{0}\right)}{\gamma}\frac{\left(N\overline{\mathbf{x}}+\gamma\_{0}\boldsymbol{\delta}\_{0}\right)^{T}}{\gamma}
\end{equation}
Using $\gamma = N + \gamma\_{0}$ in the above equation yields the final result as follows:
\begin{equation}
    \boldsymbol{\Psi}=\mathbf{S}\_{\overline{\mathbf{x}}}+\boldsymbol{\Psi}\_{0}+\frac{N\gamma\_{0}}{N+\gamma\_{0}}\left(\overline{\mathbf{x}}-\mathbf{\delta}\_{0}\right)\left(\overline{\mathbf{x}}-\mathbf{\delta}\_{0}\right)^{T}
\end{equation}
Hence, the parameters of the posterior distribution have been found in terms of the parameters of the likelihood and the prior.
## Conclusion
Given a set of data which is known to be from a multivariate normal distribution whose mean and covariance are unknown, the posterior distribution for the un\-known mean and the covariance have been found. The prior for the mean and covariance have been chosen as the normal-inverse Wishart distribution. The posterior has been found to be the normal-inverse Wishart distribution.
## References
Normal-inverse Wishart Distribution, Wikipedia.

Machine Learning A Probabilistic Perspective, Kevin P. Murphy.