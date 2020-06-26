---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Backward Prediction Forward Prediction And Interpolation With Noise Free Data Using Jointly Gaussian Vectors
---
## Introduction
In this article, it is assumed that there is a one dimensional signal. This signal is noise free. Estimation is applied to the signal using the marginal and conditional probability information from the distribution of two vectors which are jointly Gaussian. At the end of the article, a link is given to a Jupyter notebook. This notebook contains the Python code for an implementation.

## Marginal and Conditional Distributions of Two Jointly Gaussian Vectors
The vector $\mathbf{x}$ is composed of or can be separated into two vectors $\mathbf{x}\_{1}$ and $\mathbf{x}\_{2}$:
\begin{equation}
    \mathbf{x}=\begin{bmatrix}
        \mathbf{x}\_{1} \newline
        \mathbf{x}\_{2}
    \end{bmatrix}
\end{equation}
Let $\mathbf{x}\_{1}$ and $\mathbf{x}\_{2}$ be jointly Gaussian with the following mean, covariance and precision:
\begin{equation}
    \boldsymbol{\mu}=\begin{bmatrix}
        \boldsymbol{\mu}\_{1} \newline
        \boldsymbol{\mu}\_{2}
    \end{bmatrix}, \boldsymbol{\Sigma}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{11} & \boldsymbol{\Sigma}\_{12} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22} \newline
    \end{bmatrix}, \boldsymbol{\Lambda}=\boldsymbol{\Sigma}^{-1}=\begin{bmatrix}
        \boldsymbol{\Lambda}\_{11} & \boldsymbol{\Lambda}\_{12} \newline
        \boldsymbol{\Lambda}\_{21} & \boldsymbol{\Lambda}\_{22}
    \end{bmatrix}
\end{equation}
Then, the marginal densities are given as follows:
\begin{equation}
    p\left(\mathbf{x}\_{1}\right)=N\left(\mathbf{x}\_{1}|\boldsymbol{\mu}\_{1}, \boldsymbol{\Sigma}\_{11}\right)
\end{equation}
\begin{equation}
    p\left(\mathbf{x}\_{2}\right)=N\left(\mathbf{x}\_{2}|\boldsymbol{\mu}\_{2}, \boldsymbol{\Sigma}\_{22}\right)
\end{equation}
The conditional density $p\left(\mathbf{x}\_{1}|\mathbf{x}\_{2}\right)$ is given by the following:
\begin{equation}
    p\left(\mathbf{x}\_{1}|\mathbf{x}\_{2}\right)=N\left(\mathbf{x}\_{1}|\boldsymbol{\mu}\_{1|2}, \boldsymbol{\Sigma}\_{1|2}\right)
\end{equation}
where
\begin{equation}
    \boldsymbol{\mu}\_{1|2}=\boldsymbol{\mu}\_{1}-\boldsymbol{\Lambda}\_{11}^{-1}\boldsymbol{\Lambda}\_{12}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{1|2}=\boldsymbol{\Lambda}\_{11}^{-1}
\end{equation}

## The Problem Definition
There is a one dimensional function $f$ defined on an interval $\left[0, T\right]$. The interval is divided into $D$ equal parts:
\begin{equation}
    h=\frac{T}{D}
\end{equation}
The function is defined at points $s\_{j}$ where
\begin{equation}
    s\_{j}=jh \, \left(j=1,2,3, \dotso , D-1, D\right )
\end{equation}
The function values are denoted by $x\_{j}$:
\begin{equation}
    x\_{j}=f\left(s\_{j}\right)
\end{equation}
Hence, the function values can be considered as a vector $\mathbf{x}$ of $D$ elements. This vector can be divided into two parts $\mathbf{x}\_{1}$ and $\mathbf{x}\_{2}$:
\begin{equation}
    \mathbf{x}=\begin{bmatrix}
        \mathbf{x}\_{1} \newline
        \mathbf{x}\_{2}
    \end{bmatrix}
\end{equation}
The problem is to determine $\mathbf{x}\_{1}$ given $\mathbf{x}\_{2}$ or $\mathbf{x}\_{2}$ given $\mathbf{x}\_{1}$. 

## The Solution
It is natural to assume that the function is smooth. This prior can be encoded to the solution by
\begin{equation}
    x\_{j}=\frac{1}{2}\left(x\_{j-1}+x\_{j+1}\right)+\epsilon\_{j} \, \left(j=2,3,4, \dotso , D-1\right)
\end{equation}
where $\boldsymbol{\epsilon}$ has a multivariate Gaussian distribution given as follows:
\begin{equation}
    \boldsymbol{\epsilon} \sim N \left(\mathbf{0}, \left(\frac{1}{\lambda}\right)\mathbf{I}\right)
\end{equation}
The smoothness prior yields the following matrix equation:
\begin{equation}
    \mathbf{L}\mathbf{x}=\boldsymbol{\epsilon}
\end{equation}
where
\begin{equation}
    \mathbf{L}=\frac{1}{2}\begin{bmatrix}
        -1 & 2 & -1 & 0 & 0 & \dotso & 0 & 0 & 0 \newline
        0 & -1 & 2 & -1 & 0 & \dotso & 0 & 0 & 0 \newline
        0 & 0 & -1 & 2 & -1 & \dotso & 0 & 0 & 0 \newline
        \vdots & \vdots & \vdots & \vdots & \vdots & \dotso & \vdots & \vdots & \vdots \newline
        0 & 0 & 0 & 0 & 0 & \dotso & -1 & 2 & -1
    \end{bmatrix},
\label{eq:L\_definition}
\end{equation}
\begin{equation}
    \mathbf{x}=\begin{bmatrix}
        x\_{1} \newline
        x\_{2} \newline
        x\_{3} \newline
        \vdots \newline
        x\_{D}
    \end{bmatrix},\boldsymbol{\epsilon}=
    \begin{bmatrix}
        \epsilon\_{2} \newline
        \epsilon\_{3} \newline
        \epsilon\_{4} \newline
        \vdots \newline
        \epsilon\_{D-1}
    \end{bmatrix}.
\end{equation}
The mean and covariance of $\mathbf{x}$ and $\boldsymbol{\epsilon}$ are related by the following equations:
\begin{equation}
    \mathbf{L}\boldsymbol{\mu}\_{\mathbf{x}}=\boldsymbol{\mu}\_{\boldsymbol{\epsilon}}
\end{equation}
\begin{equation}
    \mathbf{L}\boldsymbol{\Sigma}\_{\mathbf{x}}\mathbf{L}^{T}=\boldsymbol{\Sigma}\_{\boldsymbol{\epsilon}}
\end{equation}
$\mathbf{L}$ is of rank $D-2$. Hence, $\mathbf{L}^{-1}$ cannot be formally defined.
\begin{equation}
    \mathbf{L}\boldsymbol{\mu}\_{\mathbf{x}}=\boldsymbol{\mu}\_{\boldsymbol{\epsilon}} \Rightarrow \boldsymbol{\mu}\_{\mathbf{x}}=\mathbf{L}^{-1}\boldsymbol{\mu}\_{\boldsymbol{\epsilon}} \Rightarrow \boldsymbol{\mu}\_{\mathbf{x}}=\mathbf{0}
\end{equation}
\begin{equation}
    \mathbf{L}\boldsymbol{\Sigma}\_{\mathbf{x}}\mathbf{L}^{T}=\boldsymbol{\Sigma}\_{\boldsymbol{\epsilon}} \Rightarrow \boldsymbol{\Sigma}\_{\mathbf{x}}=\mathbf{L}^{-1}\boldsymbol{\Sigma}\_{\boldsymbol{\epsilon}}\left(\mathbf{L}^{T}\right)^{-1}=\mathbf{L}^{-1}\left(\frac{1}{\lambda}\mathbf{I}\right)\left(\mathbf{L}^{T}\right)^{-1} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{\mathbf{x}}=\left(\lambda\mathbf{L}^{T}\mathbf{L}\right)^{-1}
\end{equation}
Since $\mathbf{L}$ is not of full rank, $\boldsymbol{\Sigma}\_{\mathbf{x}}$ is not of full rank. This kind of a distribution is called an Intrinsic Gaussian Random Field. Although $p\left(\mathbf{x}\right)$ is an improper prior, the posterior which is $p\left(\mathbf{x}\_{1}|\mathbf{x}\_{2}\right)$ in this application is usually proper.

Let $\mathbf{x}\_{2}$ be the $N$ noise free observations of the function and $\mathbf{x}\_{1}$ be the $D-N$ unknown function values to be estimated. $\mathbf{L}$ matrix is of dimension $\left(D-2\right) \times D$. It is partitioned into $\mathbf{L}\_{1}$ and $\mathbf{L}\_{2}$ where $\mathbf{L}\_{1}$ is of dimension $\left(D-2\right) \times \left(D-N\right)$ and $\mathbf{L}\_{2}$ is of dimension $\left(D-2\right) \times N$:
\begin{equation}
    \mathbf{L}=\begin{bmatrix}
        \mathbf{L}\_{1} & \mathbf{L}\_{2}
    \end{bmatrix} \Rightarrow \mathbf{L}^{T}\mathbf{L}=\begin{bmatrix}
        \mathbf{L}\_{1}^{T} \newline
        \mathbf{L}\_{2}^{T}
    \end{bmatrix}\begin{bmatrix}
        \mathbf{L}\_{1} & \mathbf{L}\_{2}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Lambda}=\lambda\mathbf{L}^{T}\mathbf{L}=\begin{bmatrix}
        \lambda\mathbf{L}\_{1}^{T}\mathbf{L}\_{1} & \lambda\mathbf{L}\_{1}^{T}\mathbf{L}\_{2} \newline
        \lambda\mathbf{L}\_{2}^{T}\mathbf{L}\_{1} & \lambda\mathbf{L}\_{2}^{T}\mathbf{L}\_{2}
    \end{bmatrix}
\end{equation}
The probability density function of the unknown values given the noise free observations of the function is given as follows:
\begin{equation}
    p\left(\mathbf{x}\_{1}|\mathbf{x}\_{2}\right)=N\left(\mathbf{x}\_{1}|\boldsymbol{\mu}\_{1|2}, \boldsymbol{\Sigma}\_{1|2}\right)
\end{equation}
where
\begin{equation}
    \boldsymbol{\mu}\_{1|2}=\boldsymbol{\mu}\_{1}-\boldsymbol{\Lambda}\_{11}^{-1}\boldsymbol{\Lambda}\_{12}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{12}=\boldsymbol{\Lambda}\_{11}^{-1}
\end{equation}
$\boldsymbol{\mu}\_{1|2}$ is the maximum a posteriori (MAP) estimation for $\mathbf{x}\_{1}:$ 
\begin{equation}
    \boldsymbol{\mu}\_{1|2}=\mathbf{0}-\boldsymbol{\Lambda}\_{11}^{-1}\boldsymbol{\Lambda}\_{12}\left(\mathbf{x}\_{2}-\mathbf{0}\right) \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{1|2}=-\boldsymbol{\Lambda}\_{11}^{-1}\boldsymbol{\Lambda}\_{12}\mathbf{x}\_{2}
\end{equation}
There is another point to consider. Determination of $\mathbf{x}\_{1}$ given $\mathbf{x}\_{2}$ is backward prediction provided $\mathbf{L}$ is defined by the equation (\ref{eq:L\_definition}). If appropriate permutations are applied to the columns of this matrix, then the backward prediction can be converted to a forward prediction or interpolation.

Let a small example be given. Let the $\mathbf{x}$ vector be given by
\begin{equation}
    \mathbf{x}=\begin{bmatrix}
        x\_{1} & x\_{2} & x\_{3} & x\_{4} & x\_{5}
    \end{bmatrix}
\end{equation}
Then, the smoothness prior will imply the following:
\begin{equation}
    -\frac{1}{2}x\_{1}+x\_{2}-\frac{1}{2}x\_{3}=\epsilon\_{1}
\end{equation}
\begin{equation}
    -\frac{1}{2}x\_{2}+x\_{3}-\frac{1}{2}x\_{4}=\epsilon\_{2}
\end{equation}
\begin{equation}
    -\frac{1}{2}x\_{3}+x\_{4}-\frac{1}{2}x\_{5}=\epsilon\_{3}
\end{equation}
And:
\begin{equation}
    \begin{bmatrix}
        -\frac{1}{2} & 1 & -\frac{1}{2} & 0 & 0 \newline
        0 & -\frac{1}{2} & 1 & -\frac{1}{2} & 0 \newline
        0 & 0 & -\frac{1}{2} & 1 & -\frac{1}{2}
    \end{bmatrix}\begin{bmatrix}
        x\_{1} \newline
        x\_{2} \newline
        x\_{3} \newline
        x\_{4} \newline
        x\_{5}
    \end{bmatrix}=\begin{bmatrix}
        \epsilon\_{1} \newline
        \epsilon\_{2} \newline
        \epsilon\_{3}
    \end{bmatrix}
\end{equation}
For the first case, assume that
\begin{equation}
    \mathbf{x}\_{1}=\begin{bmatrix}
        x\_{1} & x\_{2}
    \end{bmatrix}
\end{equation}
and
\begin{equation}
    \mathbf{x}\_{2}=\begin{bmatrix}
        x\_{3} & x\_{4} & x\_{5}
    \end{bmatrix}
\end{equation}
This is the backward prediction case. Given $\mathbf{x}\_{2}$, estimate $\mathbf{x}\_{1}$.

For the second case, assume that
\begin{equation}
    \mathbf{x}\_{1}=\begin{bmatrix}
        x\_{4} & x\_{5}
    \end{bmatrix}
\end{equation}
and
\begin{equation}
    \mathbf{x}\_{2}=\begin{bmatrix}
        x\_{1} & x\_{2} & x\_{3}
    \end{bmatrix}
\end{equation}
For this case, finding $\mathbf{x}\_{1}$ given $\mathbf{x}\_{2}$ is forward prediction. However, the matrix $\mathbf{L}$ must be updated according to the elements contained by $\mathbf{x}\_{1}$ and $\mathbf{x}\_{2}$:
\begin{equation}
    \begin{bmatrix}
        0 & 0 & -\frac{1}{2} & 1 & -\frac{1}{2} \newline
        -\frac{1}{2} & 0 & 0 & -\frac{1}{2} & 1 \newline
        1 & -\frac{1}{2} & 0 & 0 & -\frac{1}{2}
    \end{bmatrix}\begin{bmatrix}
        x\_{4} \newline
        x\_{5} \newline
        x\_{1} \newline
        x\_{2} \newline
        x\_{3}
    \end{bmatrix}=\begin{bmatrix}
        \epsilon\_{1} \newline
        \epsilon\_{2} \newline
        \epsilon\_{3}
    \end{bmatrix}
\end{equation}
For the third case, assume that
\begin{equation}
    \mathbf{x}\_{1}=\begin{bmatrix}
        x\_{2} & x\_{4}
    \end{bmatrix}
\end{equation}
and
\begin{equation}
    \mathbf{x}\_{2}=\begin{bmatrix}
        x\_{1} & x\_{3} & x\_{5}
    \end{bmatrix}
\end{equation}
For this case, estimating $\mathbf{x}\_{1}$ given $\mathbf{x}\_{2}$ is interpolation. Again, the matrix $\mathbf{L}$ should be updated accordingly:
\begin{equation}
    \begin{bmatrix}
        1 & 0 & -\frac{1}{2} & -\frac{1}{2} & 0 \newline
        -\frac{1}{2} & -\frac{1}{2} & 0 & 1 & 0 \newline
        0 & 1 & 0 & -\frac{1}{2} & -\frac{1}{2}
    \end{bmatrix}\begin{bmatrix}
        x\_{2} \newline
        x\_{4} \newline
        x\_{1} \newline
        x\_{3} \newline
        x\_{5}
    \end{bmatrix}=\begin{bmatrix}
        \epsilon\_{1} \newline
        \epsilon\_{2} \newline
        \epsilon\_{3}
    \end{bmatrix}
\end{equation}

## Conclusion
A numerical implementation is on the link \url{https://github.com/SaffetGokcenSen/Gaussian-Models/blob/master/estimating\_noise\_free\_data\_using\_jointly\_gaussian\_vectors.ipynb}. All of the algorithm and the numerical results depend on the assumption that the posterior is proper although the prior is improper. Another assumption is that the inverses are assumed to exist although they cannot be formally defined. Hence, the numerical results must be examined with these assumptions in mind. In addition, the coefficient $\lambda$ does not have any effect on the results. The interpolation results are more successful than the prediction results.

## References
Machine Learning A Probabilistic Perspective, Kevin P. Murphy.

Gaussian Markov Random Fields Theory and Applications, Havard Rue and Leonhard Held.

Lecture 5: Intrinsic GMRFs by David Bolin, <http://www.math.chalmers.se/~bodavid/GMRF2015/Lectures/F5slides.pdf>

<https://github.com/probml/pmtk3/blob/master/demos/gaussInterpDemo.m>
