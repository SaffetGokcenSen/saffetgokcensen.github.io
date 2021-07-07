---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: The Bayesian Linear Regression
---
## Introduction
In this article, the linear regression is studied using the Bayesian framework. The likelihood of the available data, the prior and the posterior for the linear regression parameters are determined. The prior is chosen in such a way that the linear regression parameters have small magnitudes around zero. The posterior predictive distribution is determined for the target variable of the linear regression. In order to determine the posterior predictive distribution easily, the problem is solved using the linear Gaussian system framework. The posterior of the linear regression parameters and the posterior predictive distribution of the target variable are demonstrated to solve a sample problem in a Jupyter notebook. The link for the notebook is given in the conclusion section.
## The Bayesian Linear Regression
The linear regression model is used to estimate the target variable $y$ which is usually assumed to have the following distribution for a sample input $\mathbf{x}$:
\begin{equation}
    p\left(y|\mathbf{x}, \mathbf{w}\right)=\mathcal{N}\left(y|\mathbf{w}^{T}\mathbf{x}, \sigma^{2}\right)
    \label{linearRegModel}
\end{equation}
$\mathbf{w}$ is the parameter vector to be determined. The maximum likelihood estimator for $\mathbf{w}$ is a solution. In order to get the Bayesian solution for $\mathbf{w}$, a prior for it must be decided on. Combining the likelihood and the prior yields the posterior for $\mathbf{w}$.

When a linear regression model overfits the available data, it is observed that some of the elements of $\mathbf{w}$ have very large magnitudes. Hence, a prior for $\mathbf{w}$ can be chosen in such a way that $\mathbf{w}$ has elements with small magnitudes. The following prior can be a good choice as indicated in [1]:
\begin{equation}
    p\left(\mathbf{w}\right)=\prod\_{i=1}^{N} \mathcal{N}\left(w\_{i}|0, \sigma\_{w}^{2}\right)
\end{equation}
So, the entries of $\mathbf{w}$ are believed to be independently around $0$ with a standard deviation of $\sigma\_{w}$. Let the prior for $\mathbf{w}$ be expressed as a multivariate Gaussian distribution:
\begin{equation}
    p\left(\mathbf{w}\right)=\prod\_{i=1}^{N} \mathcal{N}\left(w\_{i}|0, \sigma\_{w}^{2}\right)=\prod\_{i=1}^{N}\frac{1}{\sqrt{2\pi \sigma\_{w}^{2}}}\exp \left[-\frac{\left(w\_{i}-0\right)^{2}}{2\sigma\_{w}^{2}}\right] \Rightarrow
\end{equation}
\begin{equation}
    p\left(\mathbf{w}\right)=\frac{1}{\left(2\pi \sigma\_{w}^{2}\right)^{N/2}} \exp \left[\sum\_{i=1}^{N}\left(-\frac{w\_{i}^{2}}{2\sigma\_{w}^{2}}\right)\right]=\frac{1}{\left(2\pi\right)^{N/2}\left | \boldsymbol{\Sigma}\_{\mathbf{w}}\right |^{1/2}}\exp \left[-\frac{1}{2}\left(\mathbf{w}-\boldsymbol{\mu}\_{\mathbf{w}}\right)^{T}\boldsymbol{\Sigma}\_{\mathbf{w}}^{-1}\left(\mathbf{w}-\boldsymbol{\mu}\_{\mathbf{w}}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    p\left(\mathbf{w}\right)=\mathcal{N} \left(\mathbf{w}|\boldsymbol{\mu}\_{\mathbf{w}}, \boldsymbol{\Sigma}\_{\mathbf{w}}\right)
\end{equation}
where
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{w}}=\mathbf{0}\_{D}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{w}}=\sigma\_{w}^{2}\mathbf{I}\_{D}
\end{equation}
where $D$ is the number of features or the dimension of $\mathbf{w}$.

It is assumed that there are $N$ samples given as follows:
\begin{equation}
    \mathcal{D}=\left (\left(\mathbf{x}\_{1}, y\_{1}\right), \left(\mathbf{x}\_{2}, y\_{2}\right), \dotso , \left(\mathbf{x}\_{N}, y\_{N}\right) \right )
\end{equation}
The $N$ samples are assumed to be independent. Let the target samples be collected in a vector $\mathbf{y}$ which is defined as follows:
\begin{equation}
    \mathbf{y}=\begin{bmatrix}
        y\_{1} & y\_{2} & y\_{3} & \dotso & y\_{N}
    \end{bmatrix}^{T}
\end{equation}
$p\left(\mathbf{y}|\mathbf{w}\right)$ is called the likelihood using the linear Gaussian system terminology. It is formulated as follows:
\begin{equation}
    p\left(\mathbf{y}|\mathbf{w}\right) = \prod\_{i=1}^{N}p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right) = \prod\_{i=1}^{N} \mathcal{N} \left(y\_{i}|\mathbf{w}^{T}\mathbf{x}\_{i}, \sigma^{2}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(\mathbf{y}|\mathbf{w}\right) = \prod\_{i=1}^{N} \frac{1}{\left(2\pi \sigma^{2}\right)^{1/2}}\exp \left[-\frac{\left(y\_{i}-\mathbf{w}^{T}\mathbf{x}\_{i}\right)^{2}}{2\sigma^{2}}\right] \Rightarrow
\end{equation}
\begin{equation}
    p\left(\mathbf{y}|\mathbf{w}\right) = \frac{1}{\left(2\pi \sigma^{2}\right)^{N/2}}\exp \left[\sum\_{i=1}^{N}-\frac{\left(y\_{i}-\mathbf{x}\_{i}^{T}\mathbf{w}\right)^{2}}{2\sigma^{2}}\right]\Rightarrow
\end{equation}
\begin{equation}
    p\left(\mathbf{y}|\mathbf{w}\right) = \frac{1}{\left(2\pi\right)^{N/2}\left| \boldsymbol{\Sigma}\_{y} \right|^{1/2}}\exp \left[-\frac{1}{2}\left(\mathbf{y}-\boldsymbol{\mu}\_{\mathbf{y}}\right)^{T}\boldsymbol{\Sigma}\_{\mathbf{y}}^{-1}\left(\mathbf{y}-\boldsymbol{\mu}\_{\mathbf{y}}\right)\right]
\end{equation}
where
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{y}}=\begin{bmatrix}
        \mathbf{x}\_{1}^{T}\mathbf{w} & \mathbf{x}\_{2}^{T}\mathbf{w} & \mathbf{x}\_{3}^{T}\mathbf{w} & \dotso & \mathbf{x}\_{N}^{T}\mathbf{w}
    \end{bmatrix}^{T}
\end{equation}
and
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{y}}=\sigma^{2}\mathbf{I}\_{N}
\end{equation}
Incorporating the linear Gaussian system framework into the solution will help calculating the posterior predictive distribution for $y$. In the linear Gaussian system framework, $\mathbf{y}$ is the observed vector and $\mathbf{w}$ is the target vector. $\boldsymbol{\mu}\_{\mathbf{y}}$ is to be expressed in terms of an affine transformation of $\mathbf{w}$:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{y}}=\mathbf{A}.\mathbf{w}+\mathbf{b}
\end{equation}
where
\begin{equation}
    \mathbf{A}=\begin{bmatrix}
        \mathbf{x}\_{1}^{T} \newline
        \mathbf{x}\_{2}^{T} \newline
        \mathbf{x}\_{3}^{T} \newline
        \vdots \newline
        \mathbf{x}\_{N}^{T} \newline
    \end{bmatrix}
\end{equation}
and
\begin{equation}
    \mathbf{b}=\mathbf{0}\_{N}
\end{equation}
As a result, the likelihood satisfies the following equality:
\begin{equation}
    p\left(\mathbf{y}|\mathbf{w}\right) = \mathcal{N} \left(\mathbf{y}|\mathbf{A}.\mathbf{w}+\mathbf{b}, \boldsymbol{\Sigma}\_{\mathbf{y}}\right)
\end{equation}
Given the linear Gaussian system defined by
\begin{equation}
    p\left(\mathbf{w}\right)=\mathcal{N} \left(\mathbf{w}|\boldsymbol{\mu}\_{\mathbf{w}}, \boldsymbol{\Sigma}\_{\mathbf{w}}\right)
\end{equation}
and
\begin{equation}
    p\left(\mathbf{y}|\mathbf{w}\right) = \mathcal{N} \left(\mathbf{y}|\mathbf{A}.\mathbf{w}+\mathbf{b}, \boldsymbol{\Sigma}\_{\mathbf{y}}\right),
\end{equation}
the posterior $p\left(\mathbf{w}|\mathbf{y}\right)$ satisfies the following relations [2]:
\begin{equation}
    p\left(\mathbf{w}|\mathbf{y}\right)=N\left(\mathbf{w}|\left(\boldsymbol{\Sigma}\_{\mathbf{w}}-\boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\right)\boldsymbol{\Sigma}\_{\mathbf{w}}^{-1}\mathbf{A}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\boldsymbol{\Sigma}\_{\mathbf{w}}^{-1}\boldsymbol{\mu}\_{\mathbf{w}}, \boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\right) \text{ (first form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}=\boldsymbol{\Sigma}\_{\mathbf{w}}-\boldsymbol{\Sigma}\_{\mathbf{w}}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{\mathbf{w}}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\Sigma}\_{\mathbf{w}} \text{ (first form)}
\end{equation}
\begin{equation}
    p\left(\mathbf{w}|\mathbf{y}\right)=N\left(\mathbf{w}|\boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\left[\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{\mathbf{w}}^{-1}\boldsymbol{\mu}\_{\mathbf{w}}\right], \boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\right) \text{ (second form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{\mathbf{w}}|\mathbf{y}}=\left(\boldsymbol{\Sigma}\_{\mathbf{w}}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1} \text{ (second form)}
\end{equation}
The second form is to be used to obtain the covariance and the mean of the posterior for $\mathbf{w}$:
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{\mathbf{w}}|\mathbf{y}}=\left(\boldsymbol{\Sigma}\_{\mathbf{w}}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1}=\left(\frac{1}{\sigma\_{w}^{2}}\mathbf{I}\_{D}+ \begin{bmatrix}
        \mathbf{x}\_{1} & \mathbf{x}\_{2} & \mathbf{x}\_{3} & \dotso & \mathbf{x}\_{N}
    \end{bmatrix}\frac{1}{\sigma^{2}}\mathbf{I}\_{N}\begin{bmatrix}
        \mathbf{x}\_{1}^{T} \newline
        \mathbf{x}\_{2}^{T} \newline
        \mathbf{x}\_{3}^{T} \newline
        \vdots \newline
        \mathbf{x}\_{N}^{T}
    \end{bmatrix}\right)^{-1} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{\mathbf{w}}|\mathbf{y}}=\left(\frac{1}{\sigma\_{w}^{2}}\mathbf{I}\_{D}+\frac{1}{\sigma^{2}}\sum\_{i=1}^{N}\mathbf{x}\_{i}\mathbf{x}\_{i}^{T}\right)^{-1}
\end{equation}
It is the turn of the posterior mean $\boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}$:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}=\boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\left[\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{\mathbf{w}}^{-1}\boldsymbol{\mu}\_{\mathbf{w}}\right] \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}=\boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\left(\begin{bmatrix}
        \mathbf{x}\_{1} & \mathbf{x}\_{2} & \mathbf{x}\_{3} & \dotso & \mathbf{x}\_{N}
    \end{bmatrix}\frac{1}{\sigma^{2}}\mathbf{I}\_{N}\mathbf{y}+\frac{1}{\sigma\_{w}^{2}}\mathbf{I}\_{D} \ \mathbf{0}\_{D}\right) \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}=\boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\left(\frac{1}{\sigma^{2}}\begin{bmatrix}
        \mathbf{x}\_{1} & \mathbf{x}\_{2} & \mathbf{x}\_{3} & \dotso & \mathbf{x}\_{N}
    \end{bmatrix}\mathbf{y}\right) \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}=\left(\frac{1}{\sigma\_{w}^{2}}\mathbf{I}+\frac{1}{\sigma^{2}}\sum\_{i=1}^{N}\mathbf{x}\_{i}\mathbf{x}\_{i}^{T}\right)^{-1} \left(\frac{1}{\sigma^{2}}\sum\_{i=1}^{N}y\_{i}\mathbf{x}\_{i}\right)
\end{equation}
Now that the posterior distribution for $\mathbf{w}$ has been determined, the posterior predictive distribution for the target variable $y$ can be worked on. The posterior predictive distribution is $p\left(y|\mathbf{x}, \mathcal{D}\right)$. It is written in terms of an integral as follows:
\begin{equation}
    p\left(y|\mathbf{x}, \mathcal{D}\right)=\int p\left(y|\mathbf{w}, \mathbf{x}\right)p\left(\mathbf{w}|\mathcal{D}\right)d\mathbf{w} \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|\mathbf{x}, \mathcal{D}\right)=\int \mathcal{N} \left(y|\mathbf{x}^{T}\mathbf{w}, \sigma^{2}\right)\mathcal{N}\left(\mathbf{w}|\boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}, \boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\right) d\mathbf{w}
    \label{postPredDist}
\end{equation}
A very recent expression has been derived for the kernel of the integral in the equation (\ref{postPredDist}). Using the knowledge from the linear Gaussian framework, the product of the prior $p\left(\mathbf{w}\right)$ and the likelihood $p\left(\mathbf{y}|\mathbf{w}\right)$ has been shown to be proportional to $\mathcal{N}\left(\mathbf{w}|\boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}, \boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\right)$.
\begin{equation}
    p\left(\mathbf{w}|\mathbf{y}\right)=\frac{p\left(\mathbf{y}|\mathbf{w}\right)p\left(\mathbf{w}\right)}{p\left(\mathbf{y}\right)} \Rightarrow
\end{equation}
Hence, $p\left(\mathbf{y}|\mathbf{w}\right)p\left(\mathbf{w}\right)$ is proportional to $p\left(\mathbf{w}|\mathbf{y}\right)$ with the multiplicative inverse of $p\left(\mathbf{y}\right)$ being the proportionality constant. Rewriting the equation (\ref{postPredDist}) using the Bayes rule results in the following:
\begin{equation}
    p\left(y|\mathbf{x}, \mathcal{D}\right)=\int p\left(\mathbf{w}|y\right) p\left(y\right) d\mathbf{w}=p\left(y\right) \int p\left(\mathbf{w}|y\right) d\mathbf{w}=p\left(y\right)
\end{equation}
Therefore, the normalization constant $p\left(y\right)$ is the posterior predictive distribution. It can easily be calculated in the framework of linear Gaussian systems. From [2] and [3], $p\left(\mathbf{y}\right)$ can be expressed as follows:
\begin{equation}
    p\left(\mathbf{y}\right)=\mathcal{N} \left(\mathbf{y}|\mathbf{A}\boldsymbol{\mu}\_{\mathbf{w}}+\mathbf{b}, \boldsymbol{\Sigma}\_{\mathbf{y}}+\mathbf{A}\boldsymbol{\Sigma}\_{\mathbf{w}}\mathbf{A}^{T}\right)
\end{equation}
The kernel of the integral in the equation (\ref{postPredDist}) has
\begin{equation}
    p\left(y|\mathbf{w}, \mathbf{x}\right)=\mathcal{N} \left(y|\mathbf{x}^{T}\mathbf{w}, \sigma^{2}\right)
\end{equation}
which means that $\mathbf{A}=\mathbf{x}^{T}$, $\mathbf{b}=0$ and $\boldsymbol{\Sigma}\_{\mathbf{y}}=\sigma^{2}$ in the linear Gaussian system framework, and has
\begin{equation}
    p\left(\mathbf{w}\right)=\mathcal{N} \left(\mathbf{w}| \boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}, \boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\right)
\end{equation}
which means that
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{w}} \leftarrow \boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}
\end{equation}
and
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{w}} \leftarrow \boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}
\end{equation}
in the linear Gaussian framework. Then, the posterior predictive distribution will have the mean
\begin{equation}
    \mathbf{x}^{T}\boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}
\end{equation}
and the variance
\begin{equation}
    \sigma^{2}+\mathbf{x}^{T}\boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\mathbf{x}
\end{equation}
The posterior predictive distribution can symbolically be written as follows:
\begin{equation}
    p\left(y|\mathbf{w}, \mathbf{x}\right)=\mathcal{N}\left(y|\mathbf{x}^{T}\boldsymbol{\mu}\_{\mathbf{w}|\mathbf{y}}, \sigma^{2}+\mathbf{x}^{T}\boldsymbol{\Sigma}\_{\mathbf{w}|\mathbf{y}}\mathbf{x}\right)
\end{equation}
## Conclusion
The Bayesian linear regression has been studied. The linear Gaussian system framework has been shown to enable easy derivation of the posterior predictive distribution. The sample Jupyter notebook is at this [link](https://github.com/SaffetGokcenSen/Bayesian-Linear-Regression/blob/main/bayesian_linear_regression_model.ipynb).
## References
[1] Kevin P. Murphy, Machine Learning: A Probabilistic Perspective, The MIT Press, 2012
[2] Bayes Rule For A Linear Gaussian System, <https://saffetgokcensen.github.io/blog/2020/07/08/bayes-rule-for-a-linear-gaussian-system>
[3] Marginals and Conditionals from the Joint Gaussian Distribution of Two Random Vectors, <https://saffetgokcensen.github.io/blog/2020/06/04/marginals-and-conditionals-from-the-joint-gaussian-distribution-of-two-random-vectors>
