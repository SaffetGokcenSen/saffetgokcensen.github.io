---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Marginals and Conditionals from the Joint Gaussian Distribution of Two Random Vectors
---
## Introduction
Assume that there is a random vector $\mathbf{x}$ with a Gaussian distribution. If this random vector is separated into two parts and written in the form given as 
\begin{equation}
    \mathbf{x}=\begin{bmatrix}
        \mathbf{x}\_{1} \newline
        \mathbf{x}\_{2}
    \end{bmatrix},
\end{equation}
then what will be the distribution of  $\mathbf{x}\_{1}|\mathbf{x}\_{2}$ and $\mathbf{x}\_{2}$? This question is to be answered in this article.
## Derivation
The probability density function of the distribution of $\mathbf{x}$ is given as follows:
\begin{equation}
    p\left(\mathbf{x}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=\frac{1}{\left(2\pi\right)^{d/2}\left | \boldsymbol{\Sigma}\right |^{1/2}}\exp\left[-\frac{1}{2}\left(\mathbf{x}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\right)\right]
\end{equation}
where $\boldsymbol{\mu}$ is the mean vector and $\boldsymbol{\Sigma}$ is the positive definite and symmetric covariance matrix. When the $\mathbf{x}$ vector is separated into two parts $\mathbf{x}\_{1}$ and $\mathbf{x}\_{2}$, the mean vector $\boldsymbol{\mu}$ is also separated into two parts $\boldsymbol{\mu}\_{1}$ and $\boldsymbol{\mu}\_{2}$ accordingly. $\boldsymbol{x}\_{1}$ and $\boldsymbol{\mu}\_{1}$ are of dimension $d\_{1} \times 1$, $\boldsymbol{x}\_{2}$ and $\boldsymbol{\mu}\_{2}$ are of dimension $d\_{2} \times 1$. The covariance matrix is also partitioned into block matrices of appropriate dimensions as follows:
\begin{equation}
    \boldsymbol{\Sigma}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{11} & \boldsymbol{\Sigma}\_{12} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}
\end{equation}
$\boldsymbol{\Sigma}\_{11}$ is of dimension $d\_{1} \times d\_{1}$. $\boldsymbol{\Sigma}\_{12}$ is of dimension $d\_{1} \times d\_{2}$. $\boldsymbol{\Sigma}\_{21}$ is of dimension $d\_{2} \times d\_{1}$. $\boldsymbol{\Sigma}\_{22}$ is of dimension $d\_{2} \times d\_{2}$. Following [1], the covariance matrix is to be block diagonalized to decompose its inverse to the product of useful matrices:
\begin{equation}
    \begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix} \times
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11} & \boldsymbol{\Sigma}\_{12} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}=
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11}-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21} & \mathbf{0} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11}-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21} & \mathbf{0} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix} \times 
    \begin{bmatrix}
        \mathbf{I} & \mathbf{0} \newline
        -\boldsymbol{\Sigma}^{-1}\_{22}\boldsymbol{\Sigma}\_{21} & \mathbf{I}
    \end{bmatrix}=
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11}-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21} & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}
\end{equation}
Hence:
\begin{equation}
    \begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix} \times
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11} & \boldsymbol{\Sigma}\_{12} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix} \times
    \begin{bmatrix}
        \mathbf{I} & \mathbf{0} \newline
        -\boldsymbol{\Sigma}^{-1}\_{22}\boldsymbol{\Sigma}\_{21} & \mathbf{I}
    \end{bmatrix}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{11}-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21} & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}
\end{equation}
If the inverse of both sides of the equation is taken then:
\begin{equation}
    \begin{bmatrix}
        \mathbf{I} & \mathbf{0} \newline
        -\boldsymbol{\Sigma}^{-1}\_{22}\boldsymbol{\Sigma}\_{21} & \mathbf{I}
    \end{bmatrix}^{-1} \times
    \boldsymbol{\Sigma}^{-1} \times
    \begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix}^{-1}
    =
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11}-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21} & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}^{-1} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}^{-1}=
    \begin{bmatrix}
        \mathbf{I} & \mathbf{0} \newline
        -\boldsymbol{\Sigma}^{-1}\_{22}\boldsymbol{\Sigma}\_{21} & \mathbf{I}
    \end{bmatrix} \times 
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11}-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21} & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}^{-1} \times
    \begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}^{-1}=
    \begin{bmatrix}
        \mathbf{I} & \mathbf{0} \newline
        -\boldsymbol{\Sigma}^{-1}\_{22}\boldsymbol{\Sigma}\_{21} & \mathbf{I}
    \end{bmatrix} \times 
    \begin{bmatrix}
        \left (\boldsymbol{\Sigma}\_{11}-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21}\right )^{-1} & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{22}^{-1}
    \end{bmatrix} \times
    \begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix}
\end{equation}
In the above equation, $\left (\boldsymbol{\Sigma}\_{11}-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21}\right )$ is called the Schur complement of $\boldsymbol{\Sigma}$ with respect to $\boldsymbol{\Sigma}\_{22}$ and denoted by $\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}$. Let the inverse of $\boldsymbol{\Sigma}$ be written using the notation for the Schur complement of $\boldsymbol{\Sigma}$ with respect to $\boldsymbol{\Sigma}\_{22}$:
\begin{equation}
    \boldsymbol{\Sigma}^{-1}=
    \begin{bmatrix}
        \mathbf{I} & \mathbf{0} \newline
        -\boldsymbol{\Sigma}^{-1}\_{22}\boldsymbol{\Sigma}\_{21} & \mathbf{I}
    \end{bmatrix} \times 
    \begin{bmatrix}
        \left (\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right )^{-1} & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{22}^{-1}
    \end{bmatrix} \times
    \begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix}
\end{equation}
This expression for the covariance inverse is to be used in the exponential of the probability density function:
\begin{equation}
    \left(\mathbf{x}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\right)=\left(\begin{bmatrix}
        \mathbf{x}\_{1} \newline
        \mathbf{x}\_{2}
    \end{bmatrix}-\begin{bmatrix}
        \boldsymbol{\mu}\_{1} \newline
        \boldsymbol{\mu}\_{2}
    \end{bmatrix}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\begin{bmatrix}
        \mathbf{x}\_{1} \newline
        \mathbf{x}\_{2}
    \end{bmatrix}-\begin{bmatrix}
        \boldsymbol{\mu}\_{1} \newline
        \boldsymbol{\mu}\_{2}
    \end{bmatrix}\right)=
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \mathbf{x}\_{1}-\boldsymbol{\mu}\_{1} \newline
        \mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}
    \end{bmatrix}^{T}\boldsymbol{\Sigma}^{-1}\begin{bmatrix}
        \mathbf{x}\_{1}-\boldsymbol{\mu}\_{1} \newline
        \mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}
    \end{bmatrix}=
    \begin{bmatrix}
        \left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)^{T} & \left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}
    \end{bmatrix}\boldsymbol{\Sigma}^{-1}
    \begin{bmatrix}
            \mathbf{x}\_{1}-\boldsymbol{\mu}\_{1} \newline
            \mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}
    \end{bmatrix}=
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)^{T} & \left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}
    \end{bmatrix} \times
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \mathbf{I} & \mathbf{0} \newline
        -\boldsymbol{\Sigma}^{-1}\_{22}\boldsymbol{\Sigma}\_{21} & \mathbf{I}
    \end{bmatrix} \times 
    \begin{bmatrix}
        \left (\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right )^{-1} & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{22}^{-1}
    \end{bmatrix} \times
    \begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix}\times
    \begin{bmatrix}
        \mathbf{x}\_{1}-\boldsymbol{\mu}\_{1} \newline
        \mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}
    \end{bmatrix}=
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)^{T}-\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21} & \left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}
    \end{bmatrix}\times
    \begin{bmatrix}
        \left (\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right )^{-1} & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{22}^{-1}
    \end{bmatrix} \times
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right) \newline
        \left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)
    \end{bmatrix}=
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)^{T}\left (\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right )^{-1}-\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21}\left (\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right )^{-1} & \left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}\boldsymbol{\Sigma}\_{22}^{-1}
    \end{bmatrix}\times
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right) \newline
        \left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)
    \end{bmatrix}=
\end{equation}
\begin{equation}
    \left (\left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)^{T}\left (\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right )^{-1}-\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21}\left (\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right )^{-1}\right )\times
\end{equation}
\begin{equation}
    \left(\left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)\right)+\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)\Rightarrow
\end{equation}
\begin{equation}
    \left(\mathbf{x}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    \left (\left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)^{T}-\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}\boldsymbol{\Sigma}\_{22}^{-1}\boldsymbol{\Sigma}\_{21}\right )\left (\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right )^{-1}\left(\left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)\right)+
\end{equation}
\begin{equation}
    \left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)^{T}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)
\end{equation}
From the above equation, it can be observed that the exponential of the density function has been decomposed to two exponentials. One of them is for the probably Gaussian distribution with covariance $\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}$ and mean $\left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)$. The other is for the probably Gaussian distribution with covariance $\boldsymbol{\Sigma}\_{22}$ and mean $\boldsymbol{\mu}\_{2}$.

The exponentials have been identified for two Gaussian distributions. However, the normalizing factors must also be checked. The normalizing factor for the initial Gaussian distribution is as follows:
\begin{equation}
    \frac{1}{\left(2\pi\right)^{d/2}\left | \boldsymbol{\Sigma} \right |^{1/2}}
\end{equation}
The normalizing factor for the probably Gaussian distribution with covariance $\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}$ and mean $\left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)$ is
\begin{equation}
    \frac{1}{\left(2\pi\right)^{d\_{1}/2}\left |\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22} \right |^{1/2}}.
\end{equation}
The normalizing factor for the probably Gaussian distribution with covariance  $\boldsymbol{\Sigma}\_{22}$ and mean $\boldsymbol{\mu}\_{2}$ is
\begin{equation}
    \frac{1}{\left(2\pi\right)^{d\_{2}/2}\left |\boldsymbol{\Sigma}\_{22} \right |^{1/2}}.
\end{equation}
Does the following equality hold?
\begin{equation}
    \frac{1}{\left(2\pi\right)^{d/2}\left | \boldsymbol{\Sigma} \right |^{1/2}}=\frac{1}{\left(2\pi\right)^{d\_{1}/2}\left |\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22} \right |^{1/2}}\times \frac{1}{\left(2\pi\right)^{d\_{2}/2}\left |\boldsymbol{\Sigma}\_{22} \right |^{1/2}}
\end{equation}
If $\left | \boldsymbol{\Sigma} \right |^{1/2}=\left |\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22} \right |^{1/2}\left |\boldsymbol{\Sigma}\_{22} \right |^{1/2}$, then the equality holds since $d=d\_{1}+d\_{2}$. The following equality is going to be used again:
\begin{equation}
    \begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix} \times
    \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11} & \boldsymbol{\Sigma}\_{12} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}=
    \begin{bmatrix}
        \boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22} & \mathbf{0} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \text{det}\begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix} \times
    \text{det} \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11} & \boldsymbol{\Sigma}\_{12} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}=\text{det}\begin{bmatrix}
        \boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22} & \mathbf{0} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}
\end{equation}
 It is known that the determinant of a block triangular matrix is equal to the product of the determinants of the matrices on its diagonal. Then:
 \begin{equation}
    \text{det}\begin{bmatrix}
        \mathbf{I} & -\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1} \newline
        \mathbf{0} & \mathbf{I}
    \end{bmatrix} \times
    \text{det} \begin{bmatrix}
        \boldsymbol{\Sigma}\_{11} & \boldsymbol{\Sigma}\_{12} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}=\text{det}\begin{bmatrix}
        \boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22} & \mathbf{0} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \left(\text{det}\left(\mathbf{I}\right)\text{det}\left(\mathbf{I}\right)\right)\times \text{det}\left(\boldsymbol{\Sigma}\right)=\text{det}\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\text{det}\left(\boldsymbol{\Sigma}\_{22}\right) \Rightarrow
\end{equation}
\begin{equation}
    \text{det}\left(\boldsymbol{\Sigma}\right)=\text{det}\left(\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22}\right)\text{det}\left(\boldsymbol{\Sigma}\_{22}\right)
\end{equation}
Hence, it has been proven that $\left | \boldsymbol{\Sigma} \right |^{1/2}=\left |\boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22} \right |^{1/2}\left |\boldsymbol{\Sigma}\_{22} \right |^{1/2}$. The normalizing factor of the initial distribution also properly decomposes into normalizing factors for Gaussian distributions.

The following decomposition has been shown to hold:
\begin{equation}
    N\left(\left(\mathbf{x}\_{1}, \mathbf{x}\_{2}\right)|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=
\end{equation}
\begin{equation}
    N\left(?|\left (\left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)\right ), \boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22} \right)N\left(\mathbf{x}\_{2}|\boldsymbol{\mu}\_{2}, \boldsymbol{\Sigma}\_{22}\right)
\end{equation}
What should $?$ stand for? Bayes rule implies that it is for $\mathbf{x}\_{1}|\mathbf{x}\_{2}$.
## Conclusion
Given that the probability density function of the distribution of $\mathbf{x}=\left(\mathbf{x}\_{1}, \mathbf{x}\_{2}\right)$ is
\begin{equation}
    p\left(\left(\mathbf{x}\_{1}, \mathbf{x}\_{2}\right)|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=\frac{1}{\left(2\pi\right)^{d/2}\left | \boldsymbol{\Sigma}\right |^{1/2}}\exp\left[-\frac{1}{2}\left(\mathbf{x}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\right)\right]
\end{equation}
where $\boldsymbol{\mu}$ is the mean vector and 
\begin{equation}
    \boldsymbol{\Sigma}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{11} & \boldsymbol{\Sigma}\_{12} \newline
        \boldsymbol{\Sigma}\_{21} & \boldsymbol{\Sigma}\_{22}
    \end{bmatrix}
\end{equation}
is the positive definite and symmetric covariance matrix, the following results hold:
\begin{equation}
    p\left(\mathbf{x}\_{1}|\mathbf{x}\_{2}\right)=N\left(\mathbf{x}\_{1}|\left (\left(\mathbf{x}\_{1}-\boldsymbol{\mu}\_{1}\right)-\boldsymbol{\Sigma}\_{12}\boldsymbol{\Sigma}\_{22}^{-1}\left(\mathbf{x}\_{2}-\boldsymbol{\mu}\_{2}\right)\right ), \boldsymbol{\Sigma}/\boldsymbol{\Sigma}\_{22} \right)
\end{equation}
\begin{equation}
    p\left(\mathbf{x}\_{2}\right)=N\left(\mathbf{x}\_{2}|\boldsymbol{\mu}\_{2}, \boldsymbol{\Sigma}\_{22}\right)
\end{equation}
## References

[1] Machine Learning A Probabilistic Perspective, Kevin P. Murphy.
