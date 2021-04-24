---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: The Bayesian Linear Regression And The Ridge Regression As An Outcome
---
## Introduction
In this article, the linear regression is studied using the Bayesian framework. The likelihood of the available data, the prior and the posterior for the linear regression parameters are determined. The prior is chosen in such a way that the linear regression parameters have small magnitudes around zero. The ridge regression is defined using the posterior for the linear regression parameters. The posterior predictive distribution is determined for the target variable of the linear regression.
## The Bayesian Linear Regression
The linear regression model is used to estimate the target variable $y$ which is usually assumed to have the following distribution for a sample input $\mathbf{x}$:
\begin{equation}
    p\left(y|\mathbf{x}, \mathbf{w}\right)=\mathcal{N}\left(y|\mathbf{w}^{T}.\mathbf{x}, \sigma^{2}\right)
    \label{linearRegModel}
\end{equation}
$\mathbf{w}$ is the parameter vector to be determined. The maximum likelihood estimator for $\mathbf{w}$ is a solution. In order to get the Bayesian solution for $\mathbf{w}$, a prior for it must be decided on. Combining the likelihood and the prior yields the posterior for $\mathbf{w}$.

When a linear regression model overfits the available data, it is observed that some of the elements of $\mathbf{w}$ have very large magnitudes. Hence, a prior for $\mathbf{w}$ can be chosen in such a way that $\mathbf{w}$ have elements with small magnitudes. The following prior can be a good choice as indicated in [1]:
\begin{equation}
    p\left(\mathbf{w}\right)=\prod\_{i=1}^{N} \mathcal{N}\left(w\_{i}|0, \sigma\_{w}^{2}\right)
\end{equation}
So, the entries of $\mathbf{w}$ are believed to be independently around $0$ with a standard deviation of $\sigma\_{w}$.

Let the likelihood of the available data be calculated. It is assumed that there are $N$ samples given as follows:
\begin{equation}
    \mathcal{D}=\left \{\left(\mathbf{x}\_{1}, y\_{1}\right), \left(\mathbf{x}\_{2}, y\_{2}\right), \dotso , \left(\mathbf{x}\_{N}, y\_{N}\right) \right \}
\end{equation}
The likelihood is the joint probability of the $N$ samples. The $N$ samples are assumed to be independent. Then, the likelihood $p\left(\mathcal{D}|\mathbf{w}\right)$ is formulated as follows:
\begin{equation}
    p\left(\mathcal{D}|\mathbf{w}\right)=\prod\_{i=1}^{N}p\left(y\_{i}|\mathbf{x}\_{i}, \mathbf{w}\right) \propto \prod\_{i=1}^{N} \mathcal{N} \left(y\_{i}|\mathbf{w}^{T}.\mathbf{x}\_{i}, \sigma^{2}\right)
\end{equation}
It is the turn of the posterior for $\mathbf{w}$ after the prior for $\mathbf{w}$ and the likelihood of the available data:
\begin{equation}
    p\left(\mathbf{w}|\mathcal{D}\right)=\frac{p\left(\mathcal{D}|\mathbf{w}\right)p\left(\mathbf{w}\right)}{p\left(\mathcal{D}\right)} \Rightarrow
\end{equation}
\begin{equation}
    p\left(\mathbf{w}|\mathcal{D}\right) \propto p\left(\mathcal{D}|\mathbf{w}\right)p\left(\mathbf{w}\right)
\end{equation}
Now, let the product of the likelihood and the prior be calculated:
\begin{equation}
    p\left(\mathcal{D}|\mathbf{w}\right)p\left(\mathbf{w}\right) \propto \prod\_{i=1}^{N} \mathcal{N} \left(y\_{i}|\mathbf{w}^{T}.\mathbf{x}\_{i}, \sigma^{2}\right)\prod\_{j=1}^{N} \mathcal{N}\left(w\_{j}|0, \sigma\_{w}^{2}\right)=
\end{equation}
\begin{equation}
    \prod\_{i=1}^{N}\frac{1}{\sqrt{2\pi \sigma^{2}}}\exp \left[-\frac{\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}}{2\sigma^{2}}\right] \prod\_{j=1}^{N}\frac{1}{\sqrt{2\pi \sigma\_{w}^{2}}}\exp \left(-\frac{w\_{j}^{2}}{2\sigma\_{w}^{2}}\right)=
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi \sigma^{2}\right)^{N/2}}\exp\left[-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}\right]\frac{1}{\left(2\pi \sigma\_{w}^{2}\right)^{N/2}}\exp\left(-\frac{1}{2\sigma\_{w}^{2}}\sum\_{j=1}^{N}w\_{j}^{2}\right)=
\end{equation}
\begin{equation}
    \frac{1}{\left(4\pi^{2} \sigma^{2} \sigma\_{w}^{2}\right)^{N/2}}\exp\left[-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}\right]\frac{1}{\left(2\pi \sigma\_{w}^{2}\right)^{N/2}} \exp \left[-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}\right]=
\end{equation}
\begin{equation}
    p\left(\mathcal{D}|\mathbf{w}\right)p\left(\mathbf{w}\right) \propto \frac{1}{\left(4\pi^{2} \sigma^{2} \sigma\_{w}^{2}\right)^{N/2}}\exp \left[-\frac{1}{2\sigma^{2}}\left (\sum\_{i=1}^{N}\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}\right )-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}\right]
    \label{posterior1}
\end{equation}
The posterior dis\-tri\-bu\-tion has just been found to be proportional to an exponential expression. Hence, it will be wise to check if it can be written as a multivariate Gaussian distribution for $\mathbf{w}$. The exponent is to be expanded for easy detection of similarity to a multivariate Gaussian distribution:
\begin{equation}
    -\frac{1}{2\sigma^{2}}\left (\sum\_{i=1}^{N}\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}\right )-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}=
\end{equation}
\begin{equation}
    -\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}\left [\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right).\left(y\_{i}-\mathbf{x}\_{i}^{T}.\mathbf{w}\right)\right ]-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}=
\end{equation}
\begin{equation}
    -\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N} \left(y\_{i}^{2}-y\_{i}\mathbf{x}\_{i}^{T}.\mathbf{w}-y\_{i}\mathbf{w}^{T}.\mathbf{x}\_{i}+\mathbf{w}^{T}.\mathbf{x}\_{i}\mathbf{x}\_{i}^{T}.\mathbf{w}\right)-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}=
\end{equation}
\begin{equation}
    -\frac{1}{2\sigma^{2}}\left(\sum\_{i=1}^{N} y\_{i}^{2}-\sum\_{i=1}^{N}y\_{i}\mathbf{x}\_{i}^{T}.\mathbf{w}-\sum\_{i=1}^{N}y\_{i}\mathbf{w}^{T}.\mathbf{x}\_{i}+\sum\_{i=1}^{N}\mathbf{w}^{T}.\mathbf{x}\_{i}\mathbf{x}\_{i}^{T}.\mathbf{w}\right)-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{I}.\mathbf{w} \Rightarrow
\end{equation}
\begin{equation}
    -\frac{1}{2\sigma^{2}}\left (\sum\_{i=1}^{N}\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}\right )-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}=
\end{equation}
\begin{equation}
    \mathbf{w}^{T}.\left(-\frac{1}{2\sigma\_{w}^{2}}\mathbf{I}-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}\mathbf{x}\_{i}\mathbf{x}\_{i}^{T}\right).\mathbf{w}-2\mathbf{w}^{T}.\left(\sum\_{i=1}^{N}\left(-\frac{1}{2\sigma^{2}}\right)y\_{i}\mathbf{x}\_{i}\right)+\sum\_{i=1}^{N} \left(-\frac{1}{2\sigma^{2}}\right)y\_{i}^{2}
    \label{posterior2}
\end{equation}
The square of the Mahalanobis distance for a multivariate Gaussian distribution of $\mathbf{w}$ with mean $\boldsymbol{\mu}$ and covariance $\boldsymbol{\Sigma}$ can be written and expressed in more detail as follows:
\begin{equation}
    \left(\mathbf{w}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{w}-\boldsymbol{\mu}\right)=\left(\mathbf{w}^{T}-\boldsymbol{\mu}^{T}\right)\left(\boldsymbol{\Sigma}^{-1}\mathbf{w}-\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    \mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{w}-\mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{w}+\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu} \Rightarrow
\end{equation}
\begin{equation}
    \left(\mathbf{w}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{w}-\boldsymbol{\mu}\right)=\mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{w}-2\mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}
    \label{compSquare}
\end{equation}
The right side of the equation (\ref{compSquare}) is to be equated to the expression in the equation (\ref{posterior2}). The aim is to determine the covariance and the mean of the multivariate Gaussian distribution for the posterior of $\mathbf{w}$:
\begin{equation*}
    \mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{w}-2\mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}=
\end{equation*}
\begin{equation}
    \mathbf{w}^{T}.\left(-\frac{1}{2\sigma\_{w}^{2}}\mathbf{I}-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}\mathbf{x}\_{i}\mathbf{x}\_{i}^{T}\right).\mathbf{w}-2\mathbf{w}^{T}.\left(\sum\_{i=1}^{N}\left(-\frac{1}{2\sigma^{2}}\right)y\_{i}\mathbf{x}\_{i}\right)+\sum\_{i=1}^{N} \left(-\frac{1}{2\sigma^{2}}\right)y\_{i}^{2}
\end{equation}
From this equation, the covariance and the mean for the posterior distribution of $\mathbf{w}$ are respectively found out to be as follows:
\begin{equation}
    \boldsymbol{\Sigma}=\left(-\frac{1}{2\sigma\_{w}^{2}}\mathbf{I}-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}\mathbf{x}\_{i}\mathbf{x}\_{i}^{T}\right)^{-1}
    \label{posteriorCov}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}=\left(-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}y\_{i}\mathbf{x}\_{i}\right) \Rightarrow \boldsymbol{\mu}=\left(-\frac{1}{2\sigma\_{w}^{2}}\mathbf{I}-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}\mathbf{x}\_{i}\mathbf{x}\_{i}^{T}\right)^{-1}\left(-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}y\_{i}\mathbf{x}\_{i}\right)
    \label{posteriorMean}
\end{equation}
Hence, the posterior for $\mathbf{w}$ has been determined to be as follows:
\begin{equation}
    p\left(\mathbf{w}|\mathcal{D}\right)=\frac{1}{\left(2\pi\right)^{D/2}\left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left[-\frac{1}{2}\left(\mathbf{w}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{w}-\boldsymbol{\mu}\right)\right]
\end{equation}
where $\boldsymbol{\Sigma}$ and $\boldsymbol{\mu}$ are given respectively in (\ref{posteriorCov}) and (\ref{posteriorMean}).

Let the posterior predictive distribution be now calculated:
\begin{equation}
    p\left(y|\mathbf{x},\mathcal{D}\right)=\int p\left(\mathbf{w}|\mathcal{D}\right)p\left(y|\mathbf{x},\mathbf{w}\right)d\mathbf{w}=
\end{equation}
\begin{equation}
    \int \frac{1}{\left(2\pi\right)^{D/2}\left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left[-\frac{1}{2}\left(\mathbf{w}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{w}-\boldsymbol{\mu}\right)\right]\frac{1}{\left(2\pi \sigma^{2}\right)^{1/2}}\exp\left[-\frac{\left(y-\mathbf{w}^{T}.\mathbf{x}\right)}{2\sigma^{2}}\right]d\mathbf{w} \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|\mathbf{x},\mathcal{D}\right)=\int \frac{1}{\left(2\pi\right)^{D/2}\left | \boldsymbol{\Sigma} \right |^{1/2}\left(2\pi \sigma^{2}\right)^{1/2}} \exp \left[-\frac{1}{2}\left(\mathbf{w}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{w}-\boldsymbol{\mu}\right)-\frac{\left(y-\mathbf{w}^{T}.\mathbf{x}\right)}{2\sigma^{2}}\right]d\mathbf{w}
    \label{postPredInt}
\end{equation}
The kernel of the integral in (\ref{postPredInt}) is an exponential expression. Hence, this kernel may be written as a scaled version of a multivariate Gaussian distribution. Then, it will be easy to calculate the integral. To determine the covariance and the mean of this prospective multivariate Gaussian distribution, the exponent is expanded and arranged as follows:
\begin{equation}
    -\frac{1}{2}\left(\mathbf{w}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{w}-\boldsymbol{\mu}\right)-\frac{\left(y-\mathbf{w}^{T}.\mathbf{x}\right)}{2\sigma^{2}}=
\end{equation}
\begin{equation}
    -\frac{1}{2}\mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{w}+\mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\frac{\left(y-\mathbf{w}^{T}.\mathbf{x}\right)}{2\sigma^{2}}=
\end{equation}
\begin{equation}
    -\frac{1}{2}\mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{w}+\mathbf{w}^{T}\left(\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\mathbf{x}\right)-\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\frac{y}{2\sigma^{2}} \Rightarrow
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\mathbf{w}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{w}-\boldsymbol{\mu}\right)-\frac{\left(y-\mathbf{w}^{T}.\mathbf{x}\right)}{2\sigma^{2}}=-\frac{1}{2}\mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{w}+\mathbf{w}^{T}\left(\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\mathbf{x}\right)-\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\frac{y}{2\sigma^{2}}
    \label{postPredDist1}
\end{equation}
The right side of the equation (\ref{postPredDist1}) is to be equated to the right side of
\begin{equation}
    -\frac{1}{2}\left(\mathbf{w}-\boldsymbol{\mu}\_{\text{k}}\right)^{T}\boldsymbol{\Sigma}^{-1}\_{\text{k}}\left(\mathbf{w}-\boldsymbol{\mu}\_{\text{k}}\right)=-\frac{1}{2}\mathbf{w}^{T}\boldsymbol{\Sigma}\_{\text{k}}^{-1}\mathbf{w}+\mathbf{w}^{T}\boldsymbol{\Sigma}\_{\text{k}}^{-1}\boldsymbol{\mu}\_{k}-\frac{1}{2}\boldsymbol{\mu}\_{k}^{T}\boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}
\end{equation}
where $\boldsymbol{\mu}\_{\text{k}}$ is the mean vector of and $\boldsymbol{\Sigma}\_{\text{k}}$ is the covariance of the multivariate Gaussian distribution in the kernel:
\begin{equation}
    -\frac{1}{2}\mathbf{w}^{T}\boldsymbol{\Sigma}\_{\text{k}}^{-1}\mathbf{w}+\mathbf{w}^{T}\boldsymbol{\Sigma}\_{\text{k}}^{-1}\boldsymbol{\mu}\_{k}-\frac{1}{2}\boldsymbol{\mu}\_{k}^{T}\boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}=-\frac{1}{2}\mathbf{w}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{w}+\mathbf{w}^{T}\left(\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\mathbf{x}\right)-\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\frac{y}{2\sigma^{2}}
\end{equation}
From the above equation, the following equalities can easily be written:
\begin{equation}
    \boldsymbol{\Sigma}\_{k}=\boldsymbol{\Sigma}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}=\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\mathbf{x} \Rightarrow \boldsymbol{\mu}\_{k}=\boldsymbol{\Sigma}\_{k}\left(\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\mathbf{x}\right)=\boldsymbol{\Sigma}\left(\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\mathbf{x}\right) \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{k}=\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\boldsymbol{\Sigma}\mathbf{x}
\end{equation}
After determining the mean vector and the covariance matrix of the multivariate Gaussian distribution in the kernel, the kernel can be written as follows:
\begin{equation}
    \frac{1}{\left(2\pi\right)^{D/2}\left | \boldsymbol{\Sigma} \right |^{1/2}\left(2\pi \sigma^{2}\right)^{1/2}} \exp \left[-\frac{1}{2}\left(\mathbf{w}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{w}-\boldsymbol{\mu}\right)-\frac{\left(y-\mathbf{w}^{T}.\mathbf{x}\right)}{2\sigma^{2}}\right]=
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi\right)^{D/2}\left | \boldsymbol{\Sigma} \right |^{1/2}\left(2\pi \sigma^{2}\right)^{1/2}}\exp\left[-\frac{1}{2}\left(\mathbf{w}-\boldsymbol{\mu}\_{\text{k}}\right)^{T}\boldsymbol{\Sigma}^{-1}\_{\text{k}}\left(\mathbf{w}-\boldsymbol{\mu}\_{\text{k}}\right)\right]\exp \left(\frac{1}{2}\boldsymbol{\mu}\_{k}^{T}\boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}-\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\frac{y}{2\sigma^{2}}\right)
\end{equation}
Then, the integral in the equation (\ref{postPredInt}) will be equal to the following:
\begin{equation}
    p\left(y|\mathbf{x},\mathcal{D}\right)=\frac{1}{\left(2\pi\right)^{D/2}\left | \boldsymbol{\Sigma} \right |^{1/2}\left(2\pi \sigma^{2}\right)^{1/2}}\exp \left(\frac{1}{2}\boldsymbol{\mu}\_{k}^{T}\boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}-\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\frac{y}{2\sigma^{2}}\right)\left(2\pi\right)^{D/2}\left |\boldsymbol{\Sigma}\_{k}\right |^{1/2} \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|\mathbf{x},\mathcal{D}\right)=\frac{1}{\left(2\pi \sigma^{2}\right)^{1/2}}\exp \left(\frac{1}{2}\boldsymbol{\mu}\_{k}^{T}\boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}-\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\frac{y}{2\sigma^{2}}\right) \Rightarrow
\end{equation}
\begin{equation}
    p\left(y|\mathbf{x},\mathcal{D}\right)=\frac{1}{\left(2\pi \sigma^{2}\right)^{1/2}}\exp \left[-\frac{1}{2\sigma^{2}}\left(y-\sigma^{2}\boldsymbol{\mu}\_{k}^{T}\boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}+\sigma^{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right)\right]
    \label{postPredDistFin}
\end{equation}
Hence, the posterior predictive distribution for the target variable $y$ given the input vector $\mathbf{x}$ and the available data $\mathcal{D}$ has been found to be a Gaussian with mean 
\begin{equation}
    \sigma^{2}\boldsymbol{\mu}\_{k}^{T}\boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}-\sigma^{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}
    \label{postPredDistMean}
\end{equation}
and variance $\sigma^{2}$. Let the mean be simplified by inserting the values of $\boldsymbol{\mu}\_{k}$ and $\boldsymbol{\Sigma}\_{k}$ into the equation (\ref{postPredDistMean}):
\begin{equation}
    \sigma^{2}\boldsymbol{\mu}\_{k}^{T}\boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}-\sigma^{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}=\sigma^{2}\left(\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\boldsymbol{\Sigma}\mathbf{x}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\boldsymbol{\Sigma}\mathbf{x}\right)-\sigma^{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}=
\end{equation}
\begin{equation}
    \sigma^{2}\left(\boldsymbol{\mu}^{T}+\frac{1}{2\sigma^{2}}\mathbf{x}^{T}\boldsymbol{\Sigma}^{T}\right)\left(\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\mathbf{x}\right)-\sigma^{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}=
\end{equation}
\begin{equation}
    \sigma^{2}\left(\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\frac{1}{2\sigma^{2}}\boldsymbol{\mu}^{T}\mathbf{x}+\frac{1}{2\sigma^{2}}\mathbf{x}^{T}\boldsymbol{\mu}+\frac{1}{4\sigma^{4}}\mathbf{x}^{T}\boldsymbol{\Sigma}\mathbf{x}-\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right) \Rightarrow
\end{equation}
\begin{equation}
    \sigma^{2}\boldsymbol{\mu}\_{k}^{T}\boldsymbol{\Sigma}\_{k}^{-1}\boldsymbol{\mu}\_{k}-\sigma^{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}=\boldsymbol{\mu}^{T}\mathbf{x}+\frac{1}{4\sigma^{2}}\mathbf{x}^{T}\boldsymbol{\Sigma}\mathbf{x}
\end{equation}
So, the posterior predictive distribution for $y$ has its very final form as follows:
\begin{equation}
    p\left(y|\mathbf{x}, \mathcal{D}\right)=\mathcal{N}\left(y|\left(\boldsymbol{\mu}^{T}\mathbf{x}+\frac{1}{4\sigma^{2}}\mathbf{x}^{T}\boldsymbol{\Sigma}\mathbf{x}\right), \sigma^{2}\right)
\end{equation}
where $\boldsymbol{\Sigma}$ and $\boldsymbol{\mu}$ are given respectively in (\ref{posteriorCov}) and (\ref{posteriorMean}). $\sigma^{2}$ is the varaince of the distribution defined in the equation (\ref{linearRegModel}).
## The Ridge Regression
The ridge regression is defined using the posterior for the $\mathbf{w}$ parameters. The posterior is proportional to the product of the prior and the likelihood as given in the equation (\ref{posterior1}). The maximum a posteriori (MAP) estimate for $\mathbf{w}$ is the $\mathbf{w}\_{\_{\text{MAP}}}$ which maximizes the posterior. For a better insight, it is defined using the expression in the equation (\ref{posterior1}) as follows:
\begin{equation}
    \mathbf{w}\_{\_{\text{MAP}}}=\underset{\mathbf{w}}{\mathrm{argmax}} \ \frac{1}{\left(4\pi^{2} \sigma^{2} \sigma\_{w}^{2}\right)^{N/2}}\exp \left[-\frac{1}{2\sigma^{2}}\left (\sum\_{i=1}^{N}\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}\right )-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}\right]
\end{equation}
Since $\log$ is a monotonically increasing function, the MAP estimate can also be defined as follows:
\begin{equation}
    \mathbf{w}\_{\_{\text{MAP}}}=\underset{\mathbf{w}}{\mathrm{argmax}} \ \log \left(\frac{1}{\left(4\pi^{2} \sigma^{2} \sigma\_{w}^{2}\right)^{N/2}}\exp \left[-\frac{1}{2\sigma^{2}}\left (\sum\_{i=1}^{N}\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}\right )-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}\right]\right) \Rightarrow
\end{equation}
\begin{equation}
    \mathbf{w}\_{\_{\text{MAP}}}=\underset{\mathbf{w}}{\mathrm{argmax}} \ \left (-\frac{1}{2\sigma^{2}}\left (\sum\_{i=1}^{N}\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}\right )-\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}\right ) \Rightarrow
\end{equation}
\begin{equation}
    \mathbf{w}\_{\_{\text{MAP}}}=\underset{\mathbf{w}}{\mathrm{argmin}} \ \left (\frac{1}{2\sigma^{2}}\left (\sum\_{i=1}^{N}\left(y\_{i}-\mathbf{w}^{T}.\mathbf{x}\_{i}\right)^{2}\right )+\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}\right )
    \label{mapEstimate}
\end{equation}
The expression to be minimized for the MAP estimate is composed of the term minimized for getting the maximum likelihood estimator and an additional term related with the $l\_{2}$ norm of the parameter vector $\mathbf{w}$. Hence, the MAP estimate is obtained by decreasing the magnitudes of the elements of the $\mathbf{w}$ vector. The linear regression defined using the MAP estimate is called the ridge regression. The ridge regression applies a regularization to the classical linear regression by means of the term $\frac{1}{2\sigma\_{w}^{2}}\mathbf{w}^{T}.\mathbf{w}$ in the equation (\ref{mapEstimate}). The expression for the MAP estimate can easily be obtained from the posterior distribution which is a multivariate Gaussian distribution. The mode of this distribution is the mean of the posterior distribution given in the equation (\ref{posteriorMean}):
\begin{equation}
    \mathbf{w}\_{\_{\text{MAP}}}=\left(-\frac{1}{2\sigma\_{w}^{2}}\mathbf{I}-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}\mathbf{x}\_{i}\mathbf{x}\_{i}^{T}\right)^{-1}\left(-\frac{1}{2\sigma^{2}}\sum\_{i=1}^{N}y\_{i}\mathbf{x}\_{i}\right)
\end{equation}
## Conclusion
The linear regression has been studied using the Bayesian framework. The prior for the linear regression parameters have been defined in such a way that the parameters have small magnitudes around zero. The ridge regression has been defined using the MAP estimate. The posterior predictive distribution for the target variable of the linear regression has been determined, as well.
## References
[1] Kevin P. Murphy, Machine Learning: A Probabilistic Perspective, The MIT Press, 2012.