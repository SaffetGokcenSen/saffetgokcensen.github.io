---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Maximum Likelihood Estimators For Linear Regression Models With Varying Probability Distributions For The Target Variable
---
## Introduction
In this article, the linear regression model is defined in a probabilistic perspective as in [1]. Maximum likelihood estimators for the target variable are derived for different probability distributions of the target variable. It is shown that as the assumed probability distribution for the target variable changes from Gaussian to Laplace, the error to be minimized for finding the maximum likelihood estimator of the linear regression model changes from the mean squared error to the mean absolute error.
## Model Definition
It is assumed that there are $N$ samples of data. Each sample is denoted by the vector $\mathbf{x}\_{i}$ where $i$ is from $1$ to $N$. Each element of $\mathbf{x}\_{i}$ is a feature. It is assumed that there are $M$ features. The available data is stored in a matrix $\mathbf{X}$ a row of which is the transpose of $\mathbf{x}\_{i}$. Hence, the dimension of the matrix $\mathbf{X}$ is $M\times N$. There is a target $y\_{i}$ corresponding to each $\mathbf{x}\_{i}$. The linear regression model generally assumes that the targets are Gaussian distributed with a mean of the linear combination of the features and a variance of $\sigma^{2}$:
\begin{equation}
    p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right)\propto N\left(y\_{i}|\mathbf{w}^{T}.\mathbf{x}\_{i}, \sigma^{2}\right)
\end{equation}
The distribution of the targets can be assumed to be different from Gaussian. The supposition for the distribution of the targets depends on the problem and the available data. The vector $\mathbf{w}$ contains the parameters of the linear regression model. Let the target values be stored in a vector $\mathbf{y}$.
## The Maximum Likelihood Estimator
The maximum likelihood estimator for the parameters of the linear regression model is to be derived. The aim is to find the parameters $\mathbf{w}$ which maximizes the likelihood of the available data. This likelihood is given by the following expression:
\begin{equation}
    \text{likelihood}\left(\mathbf{w}\right) = p\left(\mathbf{y}|\mathbf{X}, \mathbf{w}\right)
\end{equation}
The maximum likelihood estimator is denoted by $\hat{\mathbf{w}}$. It satisfies the following equality:
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  p\left(\mathbf{y}|\mathbf{X}, \mathbf{w}\right)
\end{equation}
If it is assumed that the samples are independent and identically distributed (i.i.d), then:
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \ \prod\_{i=1}^{N} p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right)
\end{equation}
In order to avoid numerical underflow which is due to the multiplication of many small probabilities, the log-likelihood is used to obtain the maximum likelihood estimator. Numerically more stable form of the maximum likelihood estimator is as follows:
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  \sum\_{i=1}^{N} \log \left [p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right) \right ]
    \label{mle}
\end{equation}
$\log$ represents the natural logarithm function.

What is $p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right)$? It is generally assumed to be proportional to a Gaussian distribution. The mean of the distribution is $\mathbf{w}^{T}.\mathbf{x}\_{i}$ and the variance is $\sigma^{2}$:
\begin{equation}
    p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right) \propto \frac{1}{\sqrt{2\pi \sigma^{2}}}\exp \left[-\frac{\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}}{2\sigma^{2}}\right]
\end{equation}
Then, the equation (\ref{mle}) can be expanded as follows:
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  \sum\_{i=1}^{N} \log \left(\frac{1}{\sqrt{2\pi \sigma^{2}}}\exp \left[-\frac{\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}}{2\sigma^{2}}\right]\right) \Rightarrow
\end{equation}
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  \sum\_{i=1}^{N} \left (-\frac{1}{2}\log \left(2\pi \sigma^{2}\right)-\frac{\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}}{2\sigma^{2}}\right ) \Rightarrow
\end{equation}
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  \sum\_{i=1}^{N} \left (-1 \right )\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}
    \label{mle2}
\end{equation}
In other words, the mean squared error between the targets and the model estimates is minimized. Let the expression for the maximum likelihood estimator in the equation (\ref{mle2}) be written in terms of matrices:
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \   \left (-1 \right ) \begin{bmatrix}
        y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1} & y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2} & \dotso & y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N}
    \end{bmatrix}\begin{bmatrix}
        y\_{1}-\mathbf{x}\_{1}^{T}.\mathbf{w} \newline
        y\_{2}-\mathbf{x}\_{2}^{T}.\mathbf{w} \newline
        \vdots \newline
        y\_{N}-\mathbf{x}\_{N}^{T}.\mathbf{w}
    \end{bmatrix}
\end{equation}
Let
\begin{equation}
    \begin{bmatrix}
        y\_{1}-\mathbf{x}\_{1}^{T}.\mathbf{w} \newline
        y\_{2}-\mathbf{x}\_{2}^{T}.\mathbf{w} \newline
        \vdots \newline
        y\_{N}-\mathbf{x}\_{N}^{T}.\mathbf{w}
    \end{bmatrix}
\end{equation}
be written in a more compact form:
\begin{equation}
    \begin{bmatrix}
        y\_{1}-\mathbf{x}\_{1}^{T}.\mathbf{w} \newline
        y\_{2}-\mathbf{x}\_{2}^{T}.\mathbf{w} \newline
        \vdots \newline
        y\_{N}-\mathbf{x}\_{N}^{T}.\mathbf{w}
    \end{bmatrix}=\begin{bmatrix}
        y\_{1} \newline
        y\_{2} \newline
        \vdots \newline
        y\_{N}
    \end{bmatrix}-\begin{bmatrix}
        \mathbf{x}\_{1}^{T}.\mathbf{w} \newline
        \mathbf{x}\_{2}^{T}.\mathbf{w} \newline
        \vdots \newline
        \mathbf{x}\_{N}^{T}.\mathbf{w}
    \end{bmatrix}=\begin{bmatrix}
        y\_{1} \newline
        y\_{2} \newline
        \vdots \newline
        y\_{N}
    \end{bmatrix}-\begin{bmatrix}
        \mathbf{x}\_{1}^{T} \newline
        \mathbf{x}\_{2}^{T} \newline
        \vdots \newline
        \mathbf{x}\_{N}^{T}
    \end{bmatrix}.\mathbf{w} \Rightarrow
\end{equation}
\begin{equation}
    \begin{bmatrix}
        y\_{1}-\mathbf{x}\_{1}^{T}.\mathbf{w} \newline
        y\_{2}-\mathbf{x}\_{2}^{T}.\mathbf{w} \newline
        \vdots \newline
        y\_{N}-\mathbf{x}\_{N}^{T}.\mathbf{w}
    \end{bmatrix}=\mathbf{y}-\mathbf{X}.\mathbf{w}
\end{equation}
The more compact form of the maximum likelihood estimator can be expressed as follows:
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  \left(-1\right)\left(\mathbf{y}-\mathbf{X}.\mathbf{w}\right)^{T}\left(\mathbf{y}-\mathbf{X}.\mathbf{w}\right)
\end{equation}
The maximum likelihood estimator is at the critical point of 
\begin{equation}
    \left(-1\right)\left(\mathbf{y}-\mathbf{X}.\mathbf{w}\right)^{T}\left(\mathbf{y}-\mathbf{X}.\mathbf{w}\right).
\end{equation}
This critical point satisfies the following equation:
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left[\left(-1\right)\left(\mathbf{y}-\mathbf{X}.\mathbf{w}\right)^{T}\left(\mathbf{y}-\mathbf{X}.\mathbf{w}\right)\right]=0 \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left[\left(\mathbf{y}^{T}-\mathbf{w}^{T}.\mathbf{X}^{T}\right)\left(\mathbf{y}-\mathbf{X}.\mathbf{w}\right)\right]=0 \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}} \left(\mathbf{y}^{T}\mathbf{y}-\mathbf{y}^{T}\mathbf{X}\mathbf{w}-\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{y}+\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{X}\mathbf{w}\right)=0 \Rightarrow
\end{equation}
\begin{equation}
    -\frac{\partial}{\partial \mathbf{w}}\left(\mathbf{y}^{T}\mathbf{X}\mathbf{w}\right)-\frac{\partial}{\partial \mathbf{w}}\left(\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{y}\right)+\frac{\partial}{\partial \mathbf{w}}\left(\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{X}\mathbf{w}\right)=0
    \label{mle3}
\end{equation}
Let each of the partial derivatives be calculated:
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{y}^{T}\mathbf{X}\mathbf{w}\right)=\frac{\partial}{\partial \mathbf{w}} \left[\left(\mathbf{y}^{T}\mathbf{X}\right)\_{1}w\_{1}+\left(\mathbf{y}^{T}\mathbf{X}\right)\_{2}w\_{2}+ \dotso + \left(\mathbf{y}^{T}\mathbf{X}\right)\_{M}w\_{M}\right] \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{y}^{T}\mathbf{X}\mathbf{w}\right)=
    \begin{bmatrix}
        \frac{\partial}{\partial w\_{1}}\left(\left(\mathbf{y}^{T}\mathbf{X}\right)\_{1}w\_{1}+\left(\mathbf{y}^{T}\mathbf{X}\right)\_{2}w\_{2}+ \dotso + \left(\mathbf{y}^{T}\mathbf{X}\right)\_{M}w\_{M}\right) \newline
        \frac{\partial}{\partial w\_{2}}\left(\left(\mathbf{y}^{T}\mathbf{X}\right)\_{1}w\_{1}+\left(\mathbf{y}^{T}\mathbf{X}\right)\_{2}w\_{2}+ \dotso + \left(\mathbf{y}^{T}\mathbf{X}\right)\_{M}w\_{M}\right) \newline
        \vdots \newline
        \frac{\partial}{\partial w\_{M}}\left(\left(\mathbf{y}^{T}\mathbf{X}\right)\_{1}w\_{1}+\left(\mathbf{y}^{T}\mathbf{X}\right)\_{2}w\_{2}+ \dotso + \left(\mathbf{y}^{T}\mathbf{X}\right)\_{M}w\_{M}\right)
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{y}^{T}\mathbf{X}\mathbf{w}\right)=
    \begin{bmatrix}
        \left(\mathbf{y}^{T}\mathbf{X}\right)\_{1} \newline
        \left(\mathbf{y}^{T}\mathbf{X}\right)\_{2} \newline
        \vdots \newline
        \left(\mathbf{y}^{T}\mathbf{X}\right)\_{M}
    \end{bmatrix} \Rightarrow \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{y}^{T}\mathbf{X}\mathbf{w}\right)=\mathbf{X}^{T}\mathbf{y}
\end{equation}
As to the second partial derivative:
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{y}\right)=\frac{\partial}{\partial \mathbf{w}} \left[w\_{1}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{1}+w\_{2}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{2}+ \dotso + w\_{M}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{M}\right] \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{y}\right)=
    \begin{bmatrix}
        \frac{\partial}{\partial w\_{1}}\left(w\_{1}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{1}+w\_{2}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{2}+ \dotso + w\_{M}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{M}\right) \newline
        \frac{\partial}{\partial w\_{2}}\left(w\_{1}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{1}+w\_{2}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{2}+ \dotso + w\_{M}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{M}\right) \newline
        \vdots \newline
        \frac{\partial}{\partial w\_{M}}\left(w\_{1}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{1}+w\_{2}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{2}+ \dotso + w\_{M}\left(\mathbf{X}^{T}\mathbf{y}\right)\_{M}\right) \newline
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{y}\right)=
    \begin{bmatrix}
        \left(\mathbf{X}^{T}\mathbf{y}\right)\_{1} \newline
        \left(\mathbf{X}^{T}\mathbf{y}\right)\_{2} \newline
        \vdots \newline
        \left(\mathbf{X}^{T}\mathbf{y}\right)\_{M}
    \end{bmatrix} \Rightarrow \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{y}\right)=\mathbf{X}^{T}\mathbf{y}
\end{equation}
Now, it is the turn of the third partial derivative:
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{X}\mathbf{w}\right )=\frac{\partial}{\partial \mathbf{w}}\left(\left(\mathbf{X}\mathbf{w}\right)^{T}\mathbf{X}\mathbf{w}\right )=
\end{equation}
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left( \right .
\end{equation}
\begin{equation}
    \left(X\_{11}w\_{1}+X\_{12}w\_{2}+\dotso + X\_{1M}w\_{M}\right)^{2} +
\end{equation}
\begin{equation}
    \left(X\_{21}w\_{1}+X\_{22}w\_{2}+\dotso + X\_{2M}w\_{M}\right)^{2} +
\end{equation}
\begin{equation}
    \vdots
\end{equation}
\begin{equation}
    \left(X\_{N1}w\_{1}+X\_{N2}w\_{2}+\dotso + X\_{NM}w\_{M}\right)^{2}
\end{equation}
\begin{equation}
    \left . \right )=
\end{equation}
\begin{equation}
    \begin{bmatrix}
        2 X\_{11}\left(\mathbf{X}\mathbf{w}\right)\_{\text{row 1}}+2 X\_{21}\left(\mathbf{X}\mathbf{w}\right)\_{\text{row 2}}+ \dotso + 2 X\_{N1}\left(\mathbf{X}\mathbf{w}\right)\_{\text{row N}} \newline
        2 X\_{12}\left(\mathbf{X}\mathbf{w}\right)\_{\text{row 1}}+2 X\_{22}\left(\mathbf{X}\mathbf{w}\right)\_{\text{row 2}}+ \dotso + 2 X\_{N2}\left(\mathbf{X}\mathbf{w}\right)\_{\text{row N}} \newline
        \vdots \newline
        2 X\_{1M}\left(\mathbf{X}\mathbf{w}\right)\_{\text{row 1}}+2 X\_{2M}\left(\mathbf{X}\mathbf{w}\right)\_{\text{row 2}}+ \dotso + 2 X\_{NM}\left(\mathbf{X}\mathbf{w}\right)\_{\text{row N}}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left(\mathbf{w}^{T}\mathbf{X}^{T}\mathbf{X}\mathbf{w}\right )=2\mathbf{X}^{T}\mathbf{X}\mathbf{w}
\end{equation}
The expressions for the partial derivatives are put into the equation (\ref{mle3}) to get the following:
\begin{equation}
    -\mathbf{X}^{T}\mathbf{y}-\mathbf{X}^{T}\mathbf{y}+2\mathbf{X}^{T}\mathbf{X}\mathbf{w}=0 \Rightarrow
\end{equation}
\begin{equation}
    2\mathbf{X}^{T}\mathbf{X}\mathbf{w}=2\mathbf{X}^{T}\mathbf{y} \Rightarrow \mathbf{X}^{T}\mathbf{X}\mathbf{w}=\mathbf{X}^{T}\mathbf{y} \Rightarrow
\end{equation}
\begin{equation}
    \hat{\mathbf{w}}=\left(\mathbf{X}^{T}\mathbf{X}\right)^{-1}\mathbf{X}^{T}\mathbf{y}
    \label{mle4}
\end{equation}
The maximum likelihood estimator for the parameters $\mathbf{w}$ of the linear regression model when the target variables are assumed to be Gaussian distributed with the mean $\mathbf{w}^{T}.\mathbf{x}$ and the variance $\sigma^{2}$ has been found to be given as in the equation (\ref{mle4}).
## What If The Targets Have A Laplace Distribution?
The maximum likelihood estimator for the parameters of the linear regression model has been derived when the targets are supposed to be Gaussian distributed with the mean $\mathbf{w}^{T}.\mathbf{x}$ and the variance $\sigma^{2}$. What will be the solution for the linear regression model if the targets do not have this Gaussian distribution?

For example, let the distribution of the targets be Laplace with the location equal to $\mathbf{w}^{T}.\mathbf{x}$ and the scale equal to $1$. Then:
\begin{equation}
    p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right)\propto \frac{1}{2} \exp \left(-\left | y\_{i} - \mathbf{w}^{T}.\mathbf{x}\_{i} \right |\right)
\end{equation}
The maximum likelihood estimator for the parameters $\mathbf{w}$ will be derived for this linear regression model. Assuming the samples are i.i.d., the likelihood of the samples is given as follows:
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  \prod\_{i=1}^{N} p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right)=\underset{\mathbf{w}}{\mathrm{argmax}} \  \prod\_{i=1}^{N} \frac{1}{2} \exp \left(-\left | y\_{i} - \mathbf{w}^{T}.\mathbf{x}\_{i} \right |\right)
\end{equation}
In order to avoid numerical underflow due to the multiplication of many small probabilities, the following form is used for the maximum likelihood estimator:
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  \prod\_{i=1}^{N} p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right)=\underset{\mathbf{w}}{\mathrm{argmax}} \  \sum\_{i=1}^{N} \log \left [p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right)\right ] \Rightarrow
\end{equation}
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  \sum\_{i=1}^{N} \left (-\log 2-\left | y\_{i} - \mathbf{w}^{T}.\mathbf{x}\_{i} \right | \right ) \Rightarrow
\end{equation}
\begin{equation}
    \hat{\mathbf{w}} = \underset{\mathbf{w}}{\mathrm{argmax}} \  \sum\_{i=1}^{N} \left (-1 \right )\left | y\_{i} - \mathbf{w}^{T}.\mathbf{x}\_{i} \right |
\end{equation}
In other words, the mean absolute error between the targets and the model estimates is minimized.

The maximum likelihood estimator is at the critical point which is the solution of 
\begin{equation}
    \frac{\partial}{\partial \mathbf{w}}\left (\sum\_{i=1}^{N} \left (-1 \right )\left | y\_{i} - \mathbf{w}^{T}.\mathbf{x}\_{i} \right |\right)=0 \Rightarrow
\end{equation}
\begin{equation}
    \sum\_{i=1}^{N}\frac{\partial}{\partial \mathbf{w}} \left (\left | y\_{i} - \mathbf{w}^{T}.\mathbf{x}\_{i} \right | \right )=0 \Rightarrow
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \sum\_{i=1}^{N} \frac{\partial}{\partial w\_{1}}\left (\left | y\_{i} - \mathbf{w}^{T}.\mathbf{x}\_{i} \right | \right ) \newline
        \sum\_{i=1}^{N} \frac{\partial}{\partial w\_{2}}\left (\left | y\_{i} - \mathbf{w}^{T}.\mathbf{x}\_{i} \right | \right ) \newline
        \vdots \newline
        \sum\_{i=1}^{N} \frac{\partial}{\partial w\_{M}}\left (\left | y\_{i} - \mathbf{w}^{T}.\mathbf{x}\_{i} \right | \right )
    \end{bmatrix}=0 \Rightarrow
\end{equation}
\begin{equation}
    \begin{bmatrix}
        \frac{\left | y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1} \right |}{y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1}}\mathbf{x\_{1\_{1}}} + \frac{\left | y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2} \right |}{y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2}}\mathbf{x\_{2\_{1}}} + \dotso + \frac{\left | y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N} \right |}{y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N}}\mathbf{x\_{N\_{1}}} \newline \newline
        \frac{\left | y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1} \right |}{y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1}}\mathbf{x\_{1\_{2}}} + \frac{\left | y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2} \right |}{y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2}}\mathbf{x\_{2\_{2}}} + \dotso + \frac{\left | y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N} \right |}{y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N}}\mathbf{x\_{N\_{2}}} \newline \newline
        \vdots \newline \newline
        \frac{\left | y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1} \right |}{y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1}}\mathbf{x\_{1\_{M}}} + \frac{\left | y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2} \right |}{y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2}}\mathbf{x\_{2\_{M}}} + \dotso + \frac{\left | y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N} \right |}{y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N}}\mathbf{x\_{N\_{M}}}
    \end{bmatrix}=0
\end{equation}
The above equality can be expanded as a set of $M$ equations as follows:
\begin{equation}
    \frac{\left | y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1} \right |}{y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1}}\mathbf{x\_{1\_{1}}} + \frac{\left | y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2} \right |}{y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2}}\mathbf{x\_{2\_{1}}} + \dotso + \frac{\left | y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N} \right |}{y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N}}\mathbf{x\_{N\_{1}}} = 0
\end{equation}
\begin{equation}
    \frac{\left | y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1} \right |}{y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1}}\mathbf{x\_{1\_{2}}} + \frac{\left | y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2} \right |}{y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2}}\mathbf{x\_{2\_{2}}} + \dotso + \frac{\left | y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N} \right |}{y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N}}\mathbf{x\_{N\_{2}}}=0
\end{equation}
\begin{equation}
    \vdots
\end{equation}
\begin{equation}
    \frac{\left | y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1} \right |}{y\_{1}-\mathbf{w}^{T}.\mathbf{x}\_{1}}\mathbf{x\_{1\_{M}}} + \frac{\left | y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2} \right |}{y\_{2}-\mathbf{w}^{T}.\mathbf{x}\_{2}}\mathbf{x\_{2\_{M}}} + \dotso + \frac{\left | y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N} \right |}{y\_{N}-\mathbf{w}^{T}.\mathbf{x}\_{N}}\mathbf{x\_{N\_{M}}}=0
\end{equation}
In this system of equations, the coefficients
\begin{equation}
    \frac{\left | y\_{k}-\mathbf{w}^{T}.\mathbf{x}\_{k} \right |}{y\_{k}-\mathbf{w}^{T}.\mathbf{x}\_{k}} \, \left(k=1, 2, \dotso , N\right)
\end{equation}
are either $-1$ or $1$. This system does not have an analytical solution for $\mathbf{w}$ and it may even not have a solution. The best approximate $\hat{\mathbf{w}}$ can be found by means of optimization.
## Conclusion
Maximum likelihood estimators for the target variable of the linear regression model have been derived for different probability distributions of the target variable. It has been shown that as the assumed probability distribution for the target variable changes from Gaussian to Laplace, the error to be minimized for finding the maximum likelihood estimator of the linear regression model changes from the mean squared error to the mean absolute error.
## References
[1] Kevin P. Murphy, Machine Learning: A Probabilistic Perspective, The MIT Press, 2012.
