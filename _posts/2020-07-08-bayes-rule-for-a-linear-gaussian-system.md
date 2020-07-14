---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Bayes Rule For A Linear Gaussian System
---
## Introduction
In this article, a linear Gaussian system is defined. After the prior, the likelihood are defined for the linear Gaussian system, the mathematical expression for the posterior is derived. That is the mean, the Bayes rule for a linear Gaussian system is obtained.
## Bayes Rule for A Linear Gaussian System
Let $\mathbf{x}$ be a random vector with $D\_{x}$ elements. It has a multivariate Gaussian distribution whose probability density function (pdf) is given as follows:
\begin{equation}
    p\left(\mathbf{x}\right)=\frac{1}{\left(2\pi\right)^{D\_{x}/2}\left | \Sigma\_{x} \right |^{1/2}}\exp \left[-\frac{1}{2}\left(\mathbf{x}-\boldsymbol{\mu}\_{x}\right)^{T}\boldsymbol{\Sigma}\_{x}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\_{x}\right)\right]
\end{equation}
There is another random vector $\mathbf{y}\in R^{D\_{y}}$. The conditional distribution of $\mathbf{y}$ given $\mathbf{x}$ is given as follows:
\begin{equation}
    p\left(\mathbf{y}|\mathbf{x}\right)=N\left(\mathbf{y}|\mathbf{A}\mathbf{x}+\mathbf{b}, \boldsymbol{\Sigma}\_{y}\right)
\end{equation}
As can be seen from the above definition, the mean of $p\left(\mathbf{y}|\mathbf{x}\right)$ is equal to $\mathbf{A}\mathbf{x}+\mathbf{b}$. Hence, this is an example for a linear Gaussian system. In this linear Gaussian system, the prior is $p\left(\mathbf{x}\right)$ and the likelihood is $p\left(\mathbf{y}|\mathbf{x}\right)$. The posterior is $p\left(\mathbf{x}|\mathbf{y}\right)$. The mathematical expression for $p\left(\mathbf{x}|\mathbf{y}\right)$ is the Bayes rule for this linear Gaussian system. This mathematical expression is to be derived using the conditional obtained from the joint Gaussian distribution of two random vectors.
## Derivation
Let the Bayes rule for a linear Gaussian system be derived. First, the joint distribution of $\mathbf{x}$ and $\mathbf{y}$ is to be written:
\begin{equation}
    p\left(\mathbf{x}, \mathbf{y}\right)=p\left(\mathbf{x}\right)p\left(\mathbf{y}|\mathbf{x}\right)=\frac{1}{\left(2\pi\right)^{D\_{x}/2}\left |\boldsymbol{\Sigma}\_{x}\right |^{1/2}}\exp \left[-\frac{1}{2}\left(\mathbf{x}-\boldsymbol{\mu}\_{x}\right)^{T}\boldsymbol{\Sigma}\_{x}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\_{x}\right)\right] \times
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi\right)^{D\_{y}/2}\left |\boldsymbol{\Sigma}\_{y}\right |^{1/2}}\exp \left[-\frac{1}{2}\left(\mathbf{y}-\boldsymbol{\mu}\_{y}\right)^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\boldsymbol{\mu}\_{y}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    p\left(\mathbf{x}, \mathbf{y}\right)=
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi\right)^{\left(D\_{x}+D\_{y}\right)/2}\left |\boldsymbol{\Sigma}\_{x}\boldsymbol{\Sigma}\_{y}\right |^{1/2}} \exp \left[-\frac{1}{2}\left(\mathbf{x}-\boldsymbol{\mu}\_{x}\right)^{T}\boldsymbol{\Sigma}\_{x}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\_{x}\right)-\frac{1}{2}\left(\mathbf{y}-\boldsymbol{\mu}\_{y}\right)^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\boldsymbol{\mu}\_{y}\right)\right]
\end{equation}
In order to determine if the resulting distribution is multivariate Gaussian, the exponent will be examined. The exponent of a multivariate Gaussian distribution with $\mathbf{z}$ being the random vector is as follows:
\begin{equation}
    -\frac{1}{2}\left(\mathbf{z}-\boldsymbol{\mu}\_{z}\right)^{T}\boldsymbol{\Sigma}\_{z}^{-1}\left(\mathbf{z}-\boldsymbol{\mu}\_{z}\right)
\end{equation}
Let this expression be written as a sum of a quadratic term of $\mathbf{z}$, a linear term of $\mathbf{z}$ and a constant term:
\begin{equation}
    -\frac{1}{2}\left(\mathbf{z}-\boldsymbol{\mu}\_{z}\right)^{T}\boldsymbol{\Sigma}\_{z}^{-1}\left(\mathbf{z}-\boldsymbol{\mu}\_{z}\right)=-\frac{1}{2}\left(\mathbf{z}^{T}-\boldsymbol{\mu}\_{z}^{T}\right)\left(\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}-\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}+\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}+\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}-\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}
\end{equation}
Since $\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}$ is a scalar, its transpose is equal to itself. In addition, since $\boldsymbol{\Sigma}\_{z}^{-1}$ is symmetric, its transpose is equal to itself. Hence:
\begin{equation}
    -\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}+\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}+\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}-\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}=
\end{equation}
\begin{equation}
    -\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}+\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}+\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}-\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}=
\end{equation}
\begin{equation}
    -\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}+\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}-\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z} \Rightarrow
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\mathbf{z}-\boldsymbol{\mu}\_{z}\right)^{T}\boldsymbol{\Sigma}\_{z}^{-1}\left(\mathbf{z}-\boldsymbol{\mu}\_{z}\right)=-\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}+\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}-\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}
\end{equation}
As can be seen from the above result, the quadratic term of $\mathbf{z}$ contains the information for the precision of the distribution. The linear term of $\mathbf{z}$ includes the information for the mean of the distribution.

The same reasoning is to be used for determining the precision and the mean of the joint distribution. Hence, let the exponent of the joint distribution be examined:
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}-\boldsymbol{\mu}\_{x}\right)^{T}\boldsymbol{\Sigma}\_{x}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\_{x}\right)-\frac{1}{2}\left(\mathbf{y}-\boldsymbol{\mu}\_{y}\right)^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\boldsymbol{\mu}\_{y}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}^{T}-\boldsymbol{\mu}\_{x}^{T}\right)\left(\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}-\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right)-\frac{1}{2}\left(\mathbf{y}^{T}-\boldsymbol{\mu}\_{y}^{T}\right)\left(\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}-\boldsymbol{\Sigma}\_{y}^{-1}\boldsymbol{\mu}\_{y}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}-\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}+\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right)-
\end{equation}
\begin{equation}
    \frac{1}{2}\left(\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}-\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\boldsymbol{\mu}\_{y}-\boldsymbol{\mu}\_{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}+\boldsymbol{\mu}\_{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\boldsymbol{\mu}\_{y}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}-\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}+\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right)-
\end{equation}
\begin{equation}
    \frac{1}{2}\left[\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}-\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{A}\mathbf{x}+\mathbf{b}\right)-\left(\mathbf{A}\mathbf{x}+\mathbf{b}\right)^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}+\left(\mathbf{A}\mathbf{x}+\mathbf{b}\right)^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{A}\mathbf{x}+\mathbf{b}\right)\right]=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}-\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}+\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right)-
\end{equation}
\begin{equation}
    \frac{1}{2}\left[\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}-\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}-\mathbf{x}^{T}\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}+\mathbf{x}^{T}\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}\right]-
\end{equation}
\begin{equation}
    \frac{1}{2}\left(-\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}-\mathbf{b}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}+\mathbf{x}^{T}\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b}+\mathbf{b}^{T}{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}+\mathbf{b}^{T}{\Sigma}\_{y}^{-1}\mathbf{b}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}+\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}-\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}-\mathbf{x}^{T}\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}+\mathbf{x}^{T}\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}\right)-
\end{equation}
\begin{equation}
    \frac{1}{2}(-\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}+\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}-\mathbf{b}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}+\mathbf{x}^{T}\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b}
\end{equation}
\begin{equation}
    +\mathbf{b}^{T}{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}+\mathbf{b}^{T}{\Sigma}\_{y}^{-1}\mathbf{b} )
\end{equation}
The first term of the above expression is quadratic in $\mathbf{x}$ and $\mathbf{y}$. It is to be written more compactly:
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}+\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}-\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}-\mathbf{x}^{T}\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}+\mathbf{x}^{T}\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left[\mathbf{x}^{T}\left(\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}\right)+ \mathbf{y}^{T}\left(\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}-\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}\right)\right]=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left[\mathbf{x}^{T}\left [\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)\mathbf{x}-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}\right ]\right]-\frac{1}{2}\left[\mathbf{y}^{T}\left(-\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}+\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    -\frac{1}{2}\mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\mathbf{z}=-\frac{1}{2}\begin{bmatrix}
        \mathbf{x} \newline
        \mathbf{y}
    \end{bmatrix}^{T}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}\begin{bmatrix}
        \mathbf{x} \newline
        \mathbf{y}
    \end{bmatrix}
\end{equation}
Hence, the precision matrix of the joint distribution has been determined as follows:
\begin{equation}
    \boldsymbol{\Sigma}\_{z}^{-1}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}
\end{equation}
Now, let the term which is linear in $\mathbf{z}=\begin{bmatrix}
    \mathbf{x} \newline
    \mathbf{y}
\end{bmatrix}$ be determined:
\begin{equation}
    -\frac{1}{2}(-\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{x}+\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}-\mathbf{b}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{y}+\mathbf{x}^{T}\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b}
\end{equation}
\begin{equation}
    +\mathbf{b}^{T}{\Sigma}\_{y}^{-1}\mathbf{A}\mathbf{x}+\mathbf{b}^{T}{\Sigma}\_{y}^{-1}\mathbf{b} )=
\end{equation}
\begin{equation}
    \left(\frac{1}{2}\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}+\frac{1}{2}\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}+\frac{1}{2}\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}+\frac{1}{2}\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}-\frac{1}{2}\mathbf{x}^{T}\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b}-\frac{1}{2}\mathbf{x}^{T}\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b}\right)-
\end{equation}
\begin{equation}
    \frac{1}{2}\left(\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}+\mathbf{b}^{T}{\Sigma}\_{y}^{-1}\mathbf{b}\right)
\end{equation}
The expression in the first parentheses contains the term which is linear in $\begin{bmatrix}
    \mathbf{x} \newline
    \mathbf{y}
\end{bmatrix}$:
\begin{equation}
    \mathbf{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}=\mathbf{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}+\mathbf{y}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}-\mathbf{x}^{T}\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b} \Rightarrow
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \mathbf{x}^{T} & \mathbf{y}^{T}
    \end{bmatrix}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}\boldsymbol{\mu}\_{z}=\begin{bmatrix}
        \mathbf{x}^{T} & \mathbf{y}^{T}
    \end{bmatrix}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b} \newline
        \boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}\boldsymbol{\mu}\_{z}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b} \newline
        \boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{z}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}^{-1}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b} \newline
        \boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}
    \end{bmatrix}
\end{equation}
The inverse of the matrix in the above equation will be carried out using the formula for the inverse of a block matrix. It is as follows:
\begin{equation}
    \begin{bmatrix}
        \mathbf{A} & \mathbf{B} \newline
        \mathbf{C} & \mathbf{D}
    \end{bmatrix}^{-1}=\begin{bmatrix}
        \mathbf{M} & -\mathbf{M}\mathbf{B}\mathbf{D}^{-1} \newline
        -\mathbf{D}^{-1}\mathbf{C}\mathbf{M} & \mathbf{D}^{-1} + \mathbf{D}^{-1}\mathbf{C}\mathbf{M}\mathbf{B}\mathbf{D}^{-1}
    \end{bmatrix}
\end{equation}
In this formula, $\mathbf{M}^{-1}$ is the Schur complement of the matrix with respect to the submatrix $\mathbf{D}$. $\mathbf{M}$ is given by the following:
\begin{equation}
    \mathbf{M}=\left(\mathbf{A}-\mathbf{B}\mathbf{D}^{-1}\mathbf{C}\right)^{-1}
\end{equation}
Hence, $\mathbf{M}$ is calculated as follows:
\begin{equation}
    \mathbf{M}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}-\left(-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\right)\boldsymbol{\Sigma}\_{y}\left(-\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)\right)^{-1} \Rightarrow
\end{equation}
\begin{equation}
    \mathbf{M}=\boldsymbol{\Sigma}\_{x}
\end{equation}
Let the inverse formula be applied:
\begin{equation}
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}^{-1}=
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} & -\boldsymbol{\Sigma}\_{x}\left(-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\right)\boldsymbol{\Sigma}\_{y} \newline
        -\boldsymbol{\Sigma}\_{y}\left(-\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)\boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{y}+\boldsymbol{\Sigma}\_{y}\left(-\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)\boldsymbol{\Sigma}\_{x}\left(-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\right)\boldsymbol{\Sigma}\_{y}=
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}^{-1}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x}\mathbf{A}^{T} \newline
        \mathbf{A}\boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}
    \end{bmatrix}
\end{equation}
Now that the inverse has been calculated, the mean of the joint distribution can be obtained:
\begin{equation}
    \boldsymbol{\mu}\_{z}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}^{-1}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b} \newline
        \boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{z}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x}\mathbf{A}^{T} \newline
        \mathbf{A}\boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}
    \end{bmatrix}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{A}^{T}{\Sigma}\_{y}^{-1}\mathbf{b} \newline
        \boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{z}=\begin{bmatrix}
        \boldsymbol{\mu}\_{x} \newline
        \mathbf{A}\boldsymbol{\mu}\_{x}+\mathbf{b}
    \end{bmatrix}
\end{equation}
As a final check for the joint distribution's being multivariate Gaussian, it is to be verified that
\begin{equation}
    -\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}=-\frac{1}{2}\left(\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}+\mathbf{b}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}\right).
\end{equation}
So, let $-\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}$ be calculated:
\begin{equation}
    -\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}=
\end{equation}
\begin{equation}
    -\frac{1}{2}\begin{bmatrix}
        \boldsymbol{\mu}\_{x}^{T} & \left(\mathbf{A}\boldsymbol{\mu}\_{x}+\mathbf{b}\right)^{T}
    \end{bmatrix}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}\begin{bmatrix}
        \boldsymbol{\mu}\_{x} \newline
        \mathbf{A}\boldsymbol{\mu}\_{x}+\mathbf{b}
    \end{bmatrix}=
\end{equation}
\begin{equation}
    -\frac{1}{2}\begin{bmatrix}
        \boldsymbol{\mu}\_{x}^{T} & \left(\mathbf{A}\boldsymbol{\mu}\_{x}+\mathbf{b}\right)^{T}
    \end{bmatrix}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b} \newline
        \boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    -\frac{1}{2}\boldsymbol{\mu}\_{z}^{T}\boldsymbol{\Sigma}\_{z}^{-1}\boldsymbol{\mu}\_{z}=-\frac{1}{2}\left(\boldsymbol{\mu}\_{x}^{T}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}+\mathbf{b}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{b}\right)
\end{equation}
Hence, the verification has been made. So, what is the conclusion for the time being? The joint distribution $p\left(\mathbf{z}\right)=p\left(\mathbf{x}, \mathbf{y}\right)$ is multivariate Gaussian with the precision matrix
\begin{equation}
    \boldsymbol{\Sigma}\_{z}^{-1}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & -\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1} \newline
        -\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A} & \boldsymbol{\Sigma}\_{y}^{-1}
    \end{bmatrix}
\end{equation}
or covariance matrix
\begin{equation}
    \boldsymbol{\Sigma}\_{z}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x}\mathbf{A}^{T} \newline
        \mathbf{A}\boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}
    \end{bmatrix}
\end{equation}
and the mean
\begin{equation}
    \boldsymbol{\mu}\_{z}=\begin{bmatrix}
        \boldsymbol{\mu}\_{x} \newline
        \mathbf{A}\boldsymbol{\mu}\_{x}+\mathbf{b}
    \end{bmatrix}.
\end{equation}
$\mathbf{x}$ and $\mathbf{y}$ are jointly Gaussian. Hence, $p\left(\mathbf{x}|\mathbf{y}\right)$ can be written using the conditional information from the joint Gaussian distribution of two random vectors. Let a reminder be given for the conditional expression. Assume that $\left(\mathbf{x}\_{1}, \mathbf{x}\_{2}\right)$ be jointly Gaussian with the mean 
\begin{equation}
    \boldsymbol{\mu}=\begin{bmatrix}
        \boldsymbol{\mu}\_{1} \newline
        \boldsymbol{\mu}\_{2}
    \end{bmatrix}
\end{equation}
and the covariance matrix
\begin{equation}
    \boldsymbol{\Sigma}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{11} & \boldsymbol{\Sigma}\_{12} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix},
\end{equation}
then:
\begin{equation}
    p\left(\mathbf{x}\_{1}|\mathbf{x}\_{2}\right)=N\left(\mathbf{x}\_{1}|\boldsymbol{\mu}\_{1}+\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right), \boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)
\end{equation}
$\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}$ is the Schur complement of $\boldsymbol{\Sigma}$ with respect to $\boldsymbol{\Sigma}\_{22}$ and 
\begin{equation}
    \boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}=\boldsymbol{\Sigma}\_{11}-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21}.
\end{equation}
There is another form of $p\left(\mathbf{x}\_{1}|\mathbf{x}\_{2}\right)$. It is in terms of the entries of the precision matrix:
\begin{equation}
    p\left(\mathbf{x}\_{1}|\mathbf{x}\_{2}\right)=N\left(\mathbf{x}\_{1}|\boldsymbol{\mu}\_{1}-\boldsymbol{\Lambda}\_{11}^{-1}\boldsymbol{\Lambda}\_{12}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right), \boldsymbol{\Lambda}\_{11}^{-1}\right)
\end{equation}
According to these reminders, $\mathbf{x}|\mathbf{y}$ is multivariate Gaussian with mean $\boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}$ and covariance $\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}$. Let the first form of the mean be calculated:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\mu}\_{x}+\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\left(\mathbf{y}-\left(\mathbf{A}\boldsymbol{\mu}\_{x}+\mathbf{b}\right)\right)=
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{x}+\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\left(\mathbf{y}-\mathbf{b}\right)-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\mu}\_{x}
\end{equation}
A compact expression is to be derived for $\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}$:
\begin{equation}
    \boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}=\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\Sigma}\_{x} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}=\left[\boldsymbol{\Sigma}\_{x}-\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\right]\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}
\end{equation}
Let this compact expression be used in the relation for $\boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}$:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\mu}\_{x}+\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\left(\mathbf{y}-\mathbf{b}\right)-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\mu}\_{x}=
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{x}+\left[\boldsymbol{\Sigma}\_{x}-\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\right]\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}\left(\mathbf{y}-\mathbf{b}\right)-\left[\boldsymbol{\Sigma}\_{x}-\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\right]\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}\mathbf{A}\boldsymbol{\mu}\_{x}=
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{x}+\left[\boldsymbol{\Sigma}\_{x}-\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\right]\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}\left(\mathbf{y}-\mathbf{b}\right)-\left[\boldsymbol{\Sigma}\_{x}-\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\right]\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\left[\boldsymbol{\Sigma}\_{x}-\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\right]\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}
\end{equation}
So, the first form for $\boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}$ has been found. It is the turn of the second form for the mean:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\mu}\_{x}-\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1}\left(-1\right)\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\left(\mathbf{A}\boldsymbol{\mu}\_{x}+\mathbf{b}\right)\right)
\end{equation}
In fact, $\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1}$ is the second form for the covariance $\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}$. Hence:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\mu}\_{x}+\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\left(\mathbf{A}\boldsymbol{\mu}\_{x}+\mathbf{b}\right)\right)=
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{x}+\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)-\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\boldsymbol{\mu}\_{x}=
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\left[\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}^{-1}\boldsymbol{\mu}\_{x}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\boldsymbol{\mu}\_{x}\right]
\end{equation}
Let a compact expression be derived for $\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\boldsymbol{\mu}\_{x}$:
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}^{-1}-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}=\boldsymbol{\Sigma}\_{x}^{-1} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}^{-1}\boldsymbol{\mu}\_{x}-\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\boldsymbol{\mu}\_{x}=\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}
\end{equation}
Let this compact expression be used in its place:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\left[\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right]
\end{equation}
Hence, the second form for $\boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}$ has been obtained.
and covariance
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\Sigma}\_{x}.
\end{equation}
As to the forms of the covariance $\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}$, the first and second forms for the covariances are respectively as follows:
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\Sigma}\_{x}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1}
\end{equation}

## Conclusion
The mathematical expression for $p\left(\mathbf{x}|\mathbf{y}\right)$ has been found given that $\mathbf{x}$ is multivariate Gaussian and $\mathbf{y}|\mathbf{x}$ is multivariate Gaussian with mean $\mathbf{A}\mathbf{x}+\mathbf{b}$. This mathematical expression has two forms as follows:
\begin{equation}
    p\left(\mathbf{x}|\mathbf{y}\right)=N\left(\mathbf{x}|\left[\boldsymbol{\Sigma}\_{x}-\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\right]\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}, \boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)
\end{equation}
\begin{equation}
    p\left(\mathbf{x}|\mathbf{y}\right)=N\left(\mathbf{x}|\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\left[\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right], \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\right)
\end{equation}

## References
[1] Pattern Recognition and Machine Learning, Christopher M. Bishop

[2] Machine Learning A Probabilistic Perspective, Kevin P. Murphy.

[3] Marginals and Conditionals from the Joint Gaussian Distribution of Two Random Vectors, <https://saffetgokcensen.github.io/blog/2020/06/04/marginals-and-conditionals-from-the-joint-gaussian-distribution-of-two-random-vectors>
