---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Inferring An Unknown Scalar From Noisy Measurements Using A Linear Gaussian System
---

## Introduction
In this article, an unknown scalar is estimated from noisy measurements using a linear Gaussian system.

## The Problem Definition
There are $N$ noisy measurements. They are denoted by $y\_{i}$. It is assumed that the measurements satisfy the following relation:
\begin{equation}
    y\_{i}=x+\epsilon
\end{equation}
where $\epsilon$ is the noise and $x$ is the actual signal under the measurement. The measurements are assumed to have the following likelihood:
\begin{equation}
    p\left(y\_{i}|x\right)=N\left(y\_{i}|x, \lambda\_{y}^{-1}\right)
\end{equation}
where $\lambda\_{y}=1/\sigma^{2}$. The underlying signal $x$ is supposed to have the following prior:
\begin{equation}
    p\left(x\right)=N\left(x|\mu\_{0}, \lambda\_{0}^{-1}\right)
\end{equation}
The aim is to obtain the posterior $p\left(x|y\_{1},y\_{2},y\_{3},\dotso , y\_{N}\right)$.

## The Solution
The problem can be solved using a linear Gaussian system. A linear Gaussian system can be defined as in the following lines. The prior for $\mathbf{x}$ is $N\left(\mathbf{x}|\boldsymbol{\mu}\_{x}, \boldsymbol{\Sigma}\_{x}\right)$ and the likelihood for $\mathbf{y}$ is $N\left(\mathbf{y}|\mathbf{A}\mathbf{x}+\mathbf{b}, \boldsymbol{\Sigma}\_{y}\right)$. The posterior for $\mathbf{x}$ is $p\left(\mathbf{x}|\mathbf{y}\right)$. This posterior is known to be given as follows:
\begin{equation}
    p\left(\mathbf{x}|\mathbf{y}\right)=N\left(\mathbf{x}|\boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}, \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\right)
\end{equation}
where
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\left(\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\right)\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x} \text{ (first form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\Sigma}\_{x} \text{ (first form)}
\end{equation}
or
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\left[\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right] \text{ (second form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1} \text{ (second form)}
\end{equation}
The appropriate one of the two forms is to be used for the solution.

The underlying variable $x$ is a scalar. There are $N$ scalar measurements. The measurements can be put into the form of a vector $\mathbf{y}$ given by
\begin{equation}
    \mathbf{y}=\begin{bmatrix}
        y\_{1} & y\_{2} & \dotso & y\_{N}
    \end{bmatrix}^{T}
\end{equation}
It is given that the mean of each measurement is $x$. Then, the mean of the likelihood is
\begin{equation}
    \mathbf{A}x=\begin{bmatrix}
        x & x & \dotso & x
    \end{bmatrix}^{T}
\end{equation}
where
\begin{equation}
    \mathbf{A}=\mathbf{1}=\begin{bmatrix}
        1 & 1 & \dotso & 1
    \end{bmatrix}^{T}.
\end{equation}
$\mathbf{A}$ is of dimension $N \times 1$. The measurements are independently made. Hence, the covariance matrix for the likelihood is as follows:
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{y}}=\lambda\_{y}^{-1}\mathbf{I}
\end{equation}
$\boldsymbol{\Sigma}\_{\mathbf{y}}$ is of dimension $N \times N$.

Now, the results for $p\left(x|\mathbf{y}\right)$ can be used. There are two possible forms. Let the possible forms for the covariance be examined. The first form is as follows:
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\Sigma}\_{x} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\lambda\_{0}^{-1}-\lambda\_{0}^{-1}\mathbf{1}^{T}\left(\lambda\_{y}^{-1}\mathbf{I}+\mathbf{1}\lambda\_{0}^{-1}\mathbf{1}^{T}\right)^{-1}\mathbf{1}\lambda\_{0}^{-1}
\end{equation}
Now, the second form:
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\left(\lambda\_{0}+\mathbf{1}^{T}\lambda\_{y}\mathbf{I}\mathbf{1}\right)^{-1}=\left(\lambda\_{0}+\lambda\_{y}\mathbf{1}^{T}\mathbf{1}\right)^{-1} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}=\frac{1}{\lambda\_{0}+N\lambda\_{y}}
\end{equation}
It is obvious that the second form is much easier to calculate and it is readily calculated.

Let the two forms for $\boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}$ be compared. The first form is
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\left(\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\right)\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x},
\end{equation}
but since $\mathbf{A}=\mathbf{1}$ is of dimension $N \times 1$, its inverse is not defined. Hence, the first form will not be used. The second form is as follows:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\boldsymbol{\Sigma}\_{\mathbf{x}|\mathbf{y}}\left[\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right]=
\end{equation}
\begin{equation}
    \frac{1}{\lambda\_{0}+N\lambda\_{y}}\left(\mathbf{1}^{T}\lambda\_{y}\mathbf{I}\mathbf{y}+\lambda\_{0}\mu\_{0}\right)=\frac{1}{\lambda\_{0}+N\lambda\_{y}}\left(\lambda\_{y}\mathbf{1}^{T}\mathbf{y}+\lambda\_{0}\mu\_{0}\right)=
\end{equation}
\begin{equation}
    \frac{1}{\lambda\_{0}+N\lambda\_{y}}\left(\lambda\_{y}\sum\_{i=1}^{N}y\_{i}+\lambda\_{0}\mu\_{0}\right)=\frac{1}{\lambda\_{0}+N\lambda\_{y}}\left(\lambda\_{y}N\frac{1}{N}\sum\_{i=1}^{N}y\_{i}+\lambda\_{0}\mu\_{0}\right)=
\end{equation}
\begin{equation}
    \frac{1}{\lambda\_{0}+N\lambda\_{y}}\left(\lambda\_{y}N\bar{y}+\lambda\_{0}\mu\_{0}\right)\Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{x}|\mathbf{y}}=\frac{N\lambda\_{y}}{\lambda\_{0}+N\lambda\_{y}}\bar{y}+\frac{\lambda\_{0}}{\lambda\_{0}+N\lambda\_{y}}\mu\_{0}
\end{equation}
So, the posterior has the following distribution:
\begin{equation}
    p\left(x|\mathbf{y}\right)=N\left(x\bigg |\left (\frac{N\lambda\_{y}}{\lambda\_{0}+N\lambda\_{y}}\bar{y}+\frac{\lambda\_{0}}{\lambda\_{0}+N\lambda\_{y}}\mu\_{0}\right ), \frac{1}{\lambda\_{0}+N\lambda\_{y}}\right)
\end{equation}

## Conclusion
From the measurements for an unknown scalar, it is estimated using a linear Gaussian system. The estimation for the unknown scalar quantity is expressed as a posterior probability density function.

## References
[1] Machine Learning A Probabilistic Perspective, Kevin P. Murphy.

[2] Bayes Rule For A Linear Gaussian System, <https://saffetgokcensen.github.io/blog/2020/07/08/bayes-rule-for-a-linear-gaussian-system>