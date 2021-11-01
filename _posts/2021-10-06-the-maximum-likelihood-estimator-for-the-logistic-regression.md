---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: The Maximum Likelihood Estimator For The Logistic Regression
---
## Introduction
In this article, the maximum likelihood estimator (MLE) for the logistic regression is to be derived. The convexity of the optimization of the MLE and the dependence of the convexity on the numerical values of the output will be examined.
## The Logistic Regression Model
The logistic regression model is a binary classifier. It is defined as follows [1]:
\begin{equation}
    p\left(y|\mathbf{x}\right)=\text{Ber} \left(y|\text{sigm}\left(\mathbf{w}^{T}\mathbf{x}\right)\right)
\end{equation}
where $\mathbf{x}$ is the input vector, $\mathbf{w}$ is the coefficient vector and $y$ is the output variable. $y$ can take on $t$ or $f$ values. $\text{Ber}$ denotes the Bernoulli distribution and $\text{sigm}$ denotes the sigmoid function.
## The MLE For The Logistic Regression
### Analytical Calculation Of The Critical Point Of The Negative Log-likelihood
It is assumed that there is a set of $N$ samples of data:
\begin{equation}
    \mathcal{D}=\left ( \left(y\_{1}, \mathbf{x}\_{1}\right), \dotso , \left(y\_{N}, \mathbf{x}\_{N}\right) \right )
\end{equation}
The data samples are assumed to be independent and identically distributed (i.i.d.). The i.i.d. assumption enables the likelihood of the data to be written as follows:
\begin{equation}
    \text{L}=p\left(\mathcal{D}\right)=\prod\_{i=1}^{N}p\left(y\_{i}, \mathbf{x}\_{i}\right) \Rightarrow
\end{equation}
\begin{equation}
    \text{L}=\prod\_{i=1}^{N} \text{Ber} \left(y\_{i}|\text{sigm}\left(\mathbf{w}^{T}\mathbf{x}\_{i}\right)\right) \Rightarrow
\end{equation}
\begin{equation}
    \text{L}=\prod\_{i=1}^{N} \left (\left[\text{sigm} \left(\mathbf{w}^{T}\mathbf{x}\_{i}\right)\right]^{\mathbb{I} \left(y\_{i}=t\right)}\left[1-\text{sigm} \left(\mathbf{w}^{T}\mathbf{x}\_{i}\right)\right]^{\mathbb{I} \left(y\_{i}=f\right)}\right )
\end{equation}
$\mathbb{I}$ represents the indicator function defined as follows:
\begin{equation}
    \mathbb{I}\left(x=a\right)=\begin{cases}
        1 & \text{ if } x=a \newline
        0 & \text{ if } x \neq a
    \end{cases}
\end{equation}
The negative log likelihood (NLL) is obtained by multiplying the natural logarithm of the likelihood by $-1$:
\begin{equation}
    \text{NLL}=-\sum\_{i=1}^{N}\left (\mathbb{I} \left(y\_{i}=t\right) \log \left[\text{sigm} \left(\mathbf{w}^{T}\mathbf{x}\_{i}\right)\right]+\mathbb{I}\left(y\_{i}=f\right) \log \left[1-\text{sigm} \left(\mathbf{w}^{T}\mathbf{x}\_{i}\right)\right]\right )
\end{equation}
Let the following definition be made for convenience:
\begin{equation}
    \theta\_{i} \triangleq \mathbf{w}^{T}\mathbf{x}\_{i}
    \label{theta\_def}
\end{equation}
Then, the negative log likelihood can be written as follows:
\begin{equation}
    \text{NLL}=-\sum\_{i=1}^{N}\left (\mathbb{I} \left(y\_{i}=t\right) \log \left[\text{sigm} \left(\theta\_{i}\right)\right]+\mathbb{I}\left(y\_{i}=f\right) \log \left[1-\text{sigm} \left(\theta\_{i}\right)\right]\right ) \Rightarrow
\end{equation}
\begin{equation}
    \text{NLL}=-\sum\_{i=1}^{N}\left (\mathbb{I} \left(y\_{i}=t\right) \log \left(\frac{1}{1+e^{-\theta\_{i}}}\right)+\mathbb{I}\left(y\_{i}=f\right) \log \left(1-\frac{1}{1+e^{-\theta\_{i}}}\right)\right ) \Rightarrow
\end{equation}
\begin{equation}
    \text{NLL}=-\sum\_{i=1}^{N}\left (\mathbb{I} \left(y\_{i}=t\right) \log \left(\frac{1}{1+e^{-\theta\_{i}}}\right)+\mathbb{I}\left(y\_{i}=f\right) \log \left(\frac{e^{-\theta\_{i}}}{1+e^{-\theta\_{i}}}\right)\right ) \Rightarrow
\end{equation}
\begin{equation}
    \text{NLL}=-\sum\_{i=1}^{N}\left (\mathbb{I} \left(y\_{i}=t\right) \log \left(\frac{1}{1+e^{-\theta\_{i}}}\right)+\mathbb{I}\left(y\_{i}=f\right) \log \left(\frac{1}{1+e^{\theta\_{i}}}\right)\right )
\end{equation}
Now that the negative log likelihood has been derived, let its gradient be calculated. The maximum likelihood estimator is at the $\mathbf{w}$ value where this gradient vanishes.
\begin{equation}
    \frac{\partial \text{NLL}}{\partial \mathbf{w}}=\begin{bmatrix}
        \frac{\partial \text{NLL}}{\partial w\_{1}} & \dotso & \frac{\partial \text{NLL}}{\partial w\_{K}}
    \end{bmatrix}^{T}
    \label{gradient}
\end{equation}
$K$ in the equation (\ref{gradient}) is the number of features.
\begin{equation}
    \frac{\partial \text{NLL}}{\partial w\_{j}}=\frac{\partial}{\partial w\_{j}}\left[-\sum\_{i=1}^{N}\left (\mathbb{I} \left(y\_{i}=t\right) \log \left(\frac{1}{1+e^{-\theta\_{i}}}\right)+\mathbb{I}\left(y\_{i}=f\right) \log \left(\frac{1}{1+e^{\theta\_{i}}}\right)\right )\right]=
\end{equation}
\begin{equation}
    -\sum\_{i=1}^{N}\left(\mathbb{I} \left(y\_{i}=t\right)\frac{\partial}{\partial \theta\_{i}}\left(\log \left(\frac{1}{1+e^{-\theta\_{i}}}\right)\right)\frac{\partial \theta\_{i}}{\partial w\_{j}}+\mathbb{I} \left(y\_{i}=f\right)\frac{\partial}{\partial \theta\_{i}}\left(\log \left(\frac{1}{1+e^{\theta\_{i}}}\right)\right)\frac{\partial \theta\_{i}}{\partial w\_{j}}\right)=
\end{equation}
\begin{equation}
    -\sum\_{i=1}^{N} \left(\mathbb{I} \left(y\_{i}=t\right)\frac{e^{-\theta\_{i}}}{1+e^{-\theta\_{i}}}x\_{i\_{j}}-\mathbb{I} \left(y\_{i}=f\right)\frac{e^{\theta\_{i}}}{1+e^{\theta\_{i}}}x\_{i\_{j}}\right)=
\end{equation}
\begin{equation}
    -\sum\_{i=1}^{N} \left(\mathbb{I} \left(y\_{i}=t\right)\frac{e^{-\theta\_{i}}}{1+e^{-\theta\_{i}}}x\_{i\_{j}}-\mathbb{I} \left(y\_{i}=f\right)\frac{1}{1+e^{-\theta\_{i}}}x\_{i\_{j}}\right) \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial \text{NLL}}{\partial w\_{j}}=\sum\_{i=1}^{N}\left(\frac{x\_{i\_{j}}}{1+e^{-\theta\_{i}}}\left[\mathbb{I} \left(y\_{i}=f\right)-\mathbb{I} \left(y\_{i}=t\right)e^{-\theta\_{i}}\right]\right)
\end{equation}
$x\_{i\_{j}}$ is the $j^{th}$ element of the vector $\mathbf{x}\_{i}$. Let the following definition be made for the ease of notation:
\begin{equation}
    v\_{i}\triangleq \frac{1}{1+e^{-\theta\_{i}}}
    \label{v\_def}
\end{equation}
This definition implies that
\begin{equation}
    e^{-\theta\_{i}}=\frac{1}{v\_{i}}-1
    \label{v\_def\_imp}
\end{equation}
The definition in the equation (\ref{v\_def}) and its implication in the equation (\ref{v\_def\_imp}) are applied to the gradient and the following gradient expression is obtained:
\begin{equation}
    \frac{\partial \text{NLL}}{\partial w\_{j}}=\sum\_{i=1}^{N} \left(x\_{i\_{j}}\left[\mathbb{I}\left(y\_{i}=f\right)+\mathbb{I}\left(y\_{i}=t\right)\right]v\_{i}-x\_{i\_{j}}\mathbb{I}\left(y\_{i}=t\right)\right)
\end{equation}
$\mathbb{I}\left(y\_{i}=f\right)+\mathbb{I}\left(y\_{i}=t\right)$ is equal to $1$. Hence:
\begin{equation}
    \frac{\partial \text{NLL}}{\partial w\_{j}}=\sum\_{i=1}^{N} \left(x\_{i\_{j}}v\_{i}-x\_{i\_{j}}\mathbb{I}\left(y\_{i}=t\right)\right)
    \label{grad\_NLL}
\end{equation}
Vanishing of the gradient of the NLL with respect to $\mathbf{w}$ yields the following equations:
\begin{equation}
    \frac{\partial \text{NLL}}{\partial w\_{j}}=\sum\_{i=1}^{N} \left(x\_{i\_{j}}v\_{i}-x\_{i\_{j}}\mathbb{I}\left(y\_{i}=t\right)\right)=0 \ \left(j=1, \dotso , K\right) \Rightarrow
\end{equation}
\begin{equation}
    x\_{1\_{1}}v\_{1}+x\_{2\_{1}}v\_{2}+ \dotso + x\_{N\_{1}}v\_{N}=x\_{1\_{1}}\mathbb{I}\left(y\_{1}=t\right)+x\_{2\_{1}}\mathbb{I}\left(y\_{2}=t\right)+ \dotso +x\_{N\_{1}}\mathbb{I}\left(y\_{N}=t\right)
\end{equation}
\begin{equation}
    x\_{1\_{2}}v\_{1}+x\_{2\_{2}}v\_{2}+ \dotso + x\_{N\_{2}}v\_{N}=x\_{1\_{2}}\mathbb{I}\left(y\_{1}=t\right)+x\_{2\_{2}}\mathbb{I}\left(y\_{2}=t\right)+ \dotso +x\_{N\_{2}}\mathbb{I}\left(y\_{N}=t\right)
\end{equation}
\begin{equation}
    \vdots
\end{equation}
\begin{equation}
    x\_{1\_{K}}v\_{1}+x\_{2\_{K}}v\_{2}+ \dotso + x\_{N\_{K}}v\_{N}=x\_{1\_{K}}\mathbb{I}\left(y\_{1}=t\right)+x\_{2\_{K}}\mathbb{I}\left(y\_{2}=t\right)+ \dotso +x\_{N\_{K}}\mathbb{I}\left(y\_{N}=t\right)
\end{equation}
The above equations can be put into a compact matrix form as follows:
\begin{equation}
    \mathbf{X}\mathbf{v}=\mathbf{X}\mathbf{i} \Rightarrow \mathbf{X}\left(\mathbf{v}-\mathbf{i}\right)=\mathbf{0}
    \label{v\_equation}
\end{equation}
where
\begin{equation}
    \mathbf{X}=\begin{bmatrix}
        \mathbf{x}\_{1} & \mathbf{x}\_{2} & \dotso & \mathbf{x}\_{N}
    \end{bmatrix}
\end{equation}
\begin{equation}
    \mathbf{v}=\begin{bmatrix}
        v\_{1} & v\_{2} & \dotso & v\_{N}
    \end{bmatrix}^{T}
\end{equation}
\begin{equation}
    \mathbf{i}=\begin{bmatrix}
        \mathbb{I}\left(y\_{1}=t\right) & \mathbb{I}\left(y\_{2}=t\right) & \dotso & \mathbb{I}\left(y\_{N}=t\right) 
    \end{bmatrix}^{T}
\end{equation}
The equation (\ref{v\_equation}) tells that $\mathbf{v}$ is the sum of $\mathbf{i}$ and the null space of $\mathbf{X}$. According to the equation (\ref{v\_def}), $v\_{i}$ must be in the interval $\left(0, 1\right)$. Hence, the solution for $\mathbf{v}$ must be chosen keeping this condition in mind. After the determination of $\mathbf{v}$, $\boldsymbol{\theta}$ vector can be found using the equation (\ref{v\_def\_imp}). The definition in the equation (\ref{theta\_def}) implies the following matrix equation:
\begin{equation}
    \boldsymbol{\theta}=\mathbf{X}\mathbf{w}
    \label{theta\_def\_matrix}
\end{equation}
The solution of the matrix equation (\ref{theta\_def\_matrix}) gives the MLE for the vector $\mathbf{w}$. The solution path for $\mathbf{w}\_{\text{MLE}}$ starting from the equation (\ref{v\_equation}) and ending at the equation (\ref{theta\_def\_matrix}) is somewhat labyrinthine. Another way for the solution is to apply an optimization algorithm directly to the NLL.
### Finding The Critical Point Of The NLL By Means Of An Optimization Algorithm
As shown in the previous section, the analytical calculation of the critical point of the NLL is a little complicated. Applying a numerical optimization algorithm to the NLL is another way of finding the critical point of the NLL. Let it be determined if the NLL is a convex function of the vector $\mathbf{w}$. If the Hessian of the NLL with respect to $\mathbf{w}$ is positive definite, then the NLL is a convex function of $\mathbf{w}$.

The Hessian of the NLL with respect to $\mathbf{w}$ is calculated as follows:
\begin{equation}
    H\_{jk}=\frac{\partial^{2}\text{NLL}}{\partial w\_{j} \partial w\_{k}}
\end{equation}
Using the result given in the equation (\ref{grad\_NLL}):
\begin{equation}
    H\_{jk}=\frac{\partial}{\partial w\_{j}} \left(\sum\_{i=1}^{N} \left(x\_{i\_{k}}v\_{i}-x\_{i\_{k}}\mathbb{I}\left(y\_{i}=t\right)\right)\right)=\sum\_{i=1}^{N}x\_{i\_{k}}\frac{\partial v\_{i}}{\partial \theta\_{i}}\frac{\partial \theta\_{i}}{\partial w\_{j}} \Rightarrow
\end{equation}
\begin{equation}
    H\_{jk}=\sum\_{i=1}^{N} x\_{i\_{j}}x\_{i\_{k}}\frac{e^{-\theta\_{i}}}{\left(1+e^{-\theta\_{i}}\right)^{2}}
    \label{Hessian}
\end{equation}
Now that the Hessian has been derived, let it be checked if it is positive definite. From the equation (\ref{Hessian}), it can be seen that the Hessian is a symmetric matrix. There is a mathematical fact related with the positive definiteness of symmetric matrices. A symmetric matrix is positive definite if all of its diagonal entries are positive and each diagonal entry is greater than the sum of the absolute values of all other entries in the corresponding row/column. Are the diagonal entries of the Hessian positive?
\begin{equation}
    H\_{jj}=\sum\_{i=1}^{N} x\_{i\_{j}}x\_{i\_{j}}\frac{e^{-\theta\_{i}}}{\left(1+e^{-\theta\_{i}}\right)^{2}}=\sum\_{i=1}^{N} x\_{i\_{j}}^{2}\frac{e^{-\theta\_{i}}}{\left(1+e^{-\theta\_{i}}\right)^{2}}
    \label{diagonal}
\end{equation}
It is obvious that $H\_{jj}$ is never negative since it is the sum of non-negative numbers. Can it be zero? It can be zero if it happens that the samples of a feature or some features are all zero. If the samples of a feature are all zero, this means that there is no variance in the feature. Then, this feature will not be of much use for the model and will be discarded. Hence, it can be concluded that all of the diagonal elements are positive. Let the second condition be checked. Is each diagonal entry greater than the sum of the absolute values of all other entries in the corresponding row/column? Let the row corresponding to $H\_{jj}$ be considered. The sum of the absolute values of the entries in this row is to be written:
\begin{equation}
    \left | H\_{j\_{1}}\right | + \left | H\_{j\_{2}}\right | + \left | H\_{j\_{3}}\right | + \dotso + \left | H\_{j\_{K}} \right |=\sum\_{i=1}^{N}\left | x\_{i\_{j}}\right | \left(\sum\_{m=1}^{N}\left | x\_{m\_{K}}\right | \right)\frac{e^{-\theta\_{i}}}{\left(1+e^{-\theta\_{i}}\right)^{2}}
    \label{row\_abs\_sum}
\end{equation}
If the equations (\ref{diagonal}) and (\ref{row\_abs\_sum}) are compared, it can be detected that
\begin{equation}
    H\_{jj} > \left | H\_{j\_{1}}\right | + \left | H\_{j\_{2}}\right | + \left | H\_{j\_{3}}\right | + \dotso + \left | H\_{j\_{K}} \right |
\end{equation}
is not always true. Let this fact be demonstrated by a simple example. Let $A$ be a symmetric matrix with positive diagonal elements:
\begin{equation}
    A=\begin{bmatrix}
        0.10 & 0.10 & 0.20 & 0.30 \newline
        0.10 & 0.10 & 0.40 & 0.13 \newline
        0.20 & 0.40 & 3.00 & 0.22 \newline
        0.30 & 0.13 & 0.22 & 4.00
    \end{bmatrix}
\end{equation}
The eigenvalues of this matrix are 
\begin{equation}
    \lambda\_{1}= -0.01181238, \lambda\_{2}=0.11944441, \lambda\_{3}=4.08717927, \lambda\_{4}=3.0051887
\end{equation}
Not all of the eigenvalues are positive. Hence, this matrix is not a positive definite matrix. 

Since it has been shown that the Hessian of the negative log-likelihood given by 
\begin{equation}
        \text{NLL}=-\sum\_{i=1}^{N}\left (\mathbb{I} \left(y\_{i}=t\right) \log \left(\frac{1}{1+e^{-\theta\_{i}}}\right)+\mathbb{I}\left(y\_{i}=f\right) \log \left(\frac{1}{1+e^{\theta\_{i}}}\right)\right )
\end{equation}
cannot be guaranteed to be positive definite, the optimization of the negative log-likelihood is not a convex problem.
### Can NLL Be Put Into A Convex Form?
It is claimed in [1] that the NLL will be convex if the output label for the true class and the false class are chosen as $+1$ and $-1$. This claim is to be checked. 

Let the logistic regression model be rewritten with the output labels $+1$ and $-1$ taken into consideration:
\begin{equation}
    p\left(y|\mathbf{x}\right)=\text{Ber}\left(y|\text{sigm}\left(\mathbf{w}^{T}\mathbf{x}\right)\right)=\begin{cases}
        \frac{1}{1+\exp{\left(-\mathbf{w}^{T}\mathbf{x}\right)}} & \text{ if } y=1 \newline
        1-\frac{1}{1+\exp{\left(-\mathbf{w}^{T}\mathbf{x}\right)}} & \text{ if } y=-1
    \end{cases} \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|\mathbf{x}\right)=\begin{cases}
        \frac{1}{1+\exp{\left(-\mathbf{w}^{T}\mathbf{x}\right)}} & \text{ if } y=1 \newline
        \frac{1}{1+\exp{\left(\mathbf{w}^{T}\mathbf{x}\right)}} & \text{ if } y=-1
    \end{cases}\Rightarrow
\end{equation}
\begin{equation}
    p\left(y|\mathbf{x}\right)=\frac{1}{1+\exp{\left(-y\mathbf{w}^{T}\mathbf{x}\right)}}
    \label{log\_reg\_new}
\end{equation}
The NLL will be written using the logistic regression equation (\ref{log\_reg\_new}):
\begin{equation}
    \text{L}=p\left(\mathcal{D}\right)=\prod\_{i=1}^{N}p\left(y\_{i}, \mathbf{x}\_{i}\right) \Rightarrow
\end{equation}
\begin{equation}
    \text{L}=\prod\_{i=1}^{N} \left [\frac{1}{1+\exp{\left(-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}\right)}}\right ] \Rightarrow
\end{equation}
\begin{equation}
    \text{NLL}=-\sum\_{i=1}^{N} \log \left [\frac{1}{1+\exp{\left(-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}\right)}}\right ] \Rightarrow
\end{equation}
\begin{equation}
    \text{NLL}=\sum\_{i=1}^{N} \log \left [1+\exp{\left(-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}\right)}\right ]
\end{equation}
Let the gradient of this form of NLL be calculated with respect to $\mathbf{w}$:
\begin{equation}
    \frac{\partial \text{NLL}}{\partial \mathbf{w}}=\begin{bmatrix}
        \frac{\partial \text{NLL}}{\partial w\_{1}} \dotso \frac{\partial \text{NLL}}{\partial w\_{K}}
    \end{bmatrix}^{T}
\end{equation}
where
\begin{equation}
    \frac{\partial \text{NLL}}{\partial w\_{j}}=\sum\_{i=1}^{N}\left[\left(-1\right)\frac{y\_{i}x\_{i\_{j}}e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}{1+e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}\right] \ \left(j=1, \dotso , K\right)
\end{equation}
Let the Hessian of the NLL be calculated:
\begin{equation}
    \text{H}\_{mj}=\frac{\partial^{2} \text{NLL}}{\partial w\_{m} \partial w\_{j}}=\frac{\partial}{\partial w\_{m}}\sum\_{i=1}^{N}\left[\left(-1\right)\frac{y\_{i}x\_{i\_{j}}e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}{1+e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}\right]=\frac{\partial}{\partial w\_{m}}\sum\_{i=1}^{N}\left[\left(-1\right)\frac{y\_{i}x\_{i\_{j}}e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}{1+e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}\right] \Rightarrow
\end{equation}
\begin{equation}
    \text{H}\_{mj}=\sum\_{i=1}^{N}\left(-1\right)\frac{\partial}{\partial w\_{m}}\left[\frac{y\_{i}x\_{i\_{j}}e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}{1+e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}\right] \Rightarrow
\end{equation}
\begin{equation}
    \text{H}\_{mj}=\sum\_{i=1}^{N}\left[y\_{i}^{2}x\_{i\_{m}}x\_{i\_{j}}\frac{e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}{\left(1+e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}\right)^{2}}\right]
    \label{hessian\_-1\_1}
\end{equation}
$y\_{i}$ is either $-1$ or $+1$. Hence, $y\_{i}^{2}$ in the Hessian in the equation (\ref{hessian\_-1\_1}) is $1$. Then, the equation (\ref{hessian\_-1\_1}) can be modified as follows:
\begin{equation}
    \text{H}\_{mj}=\sum\_{i=1}^{N}\left[x\_{i\_{m}}x\_{i\_{j}}\frac{e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}}{\left(1+e^{-y\_{i}\mathbf{w}^{T}\mathbf{x}\_{i}}\right)^{2}}\right]
    \label{hessian\_-1\_1\_final}
\end{equation}
If the Hessian in the equation (\ref{hessian\_-1\_1\_final}) and the Hessian in the equation (\ref{Hessian}) are compared, then it can be detected that they are the same except the $y\_{i}$ term in the exponentials. Hence, the conclusions derived for the Hessian in the equation (\ref{Hessian}) are also valid for the Hessian in the equation (\ref{hessian\_-1\_1\_final}). This means that the NLL cannot be guaranteed to be convex function of $\mathbf{w}$ when the output labels are $-1$ and $+1$.
## Conclusion
The logistic regression model has been defined for the binary classification task. The NLL function has been derived for arbitrary output labels. The MLE for the unknown coefficient vector $\mathbf{w}$ has been derived. It has been shown that the NLL is not guaranteed to be a convex function of $\mathbf{w}$.
## References
[1] Kevin P. Murphy, Machine Learning: A Probabilistic Perspective, The MIT Press, 2012.
