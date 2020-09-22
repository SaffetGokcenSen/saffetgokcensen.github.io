---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Inferring The Mean Of A Multivariate Normal Distribution With Known Covariance From The Available Data
---
## Introduction
It is assumed that there is a set of vector data. These vectors are assumed to be from a multivariate Gaussian distribution:
\begin{equation}
    \textbf{x}\_{i} \sim N\left(\boldsymbol{\mu}, \boldsymbol{\Sigma}\right) \ \left(i=1, 2, 3, \dotso , N\right)
\end{equation}
It is assumed that $\boldsymbol{\mu}$ is unknown while $\boldsymbol{\Sigma}$ is known. First, the likelihood of the data given the mean and the covariance will be obtained. Then, the prior for the mean will be set. Lastly, the posterior distribution of $\boldsymbol{\mu}$ is to be obtained. The link for a sample implementation in a Jupyter notebook is given in the conclusion section.
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
The exponent in the equation (\ref{likelihood\_1}) can be written as follows:
\begin{equation}
    \sum\_{i=1}^{N}-\frac{1}{2}\left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1} \left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\begin{bmatrix}
        \mathbf{x}\_{1} \newline
        \mathbf{x}\_{2} \newline
        \mathbf{x}\_{3} \newline
        \vdots \newline
        \mathbf{x}\_{n}
    \end{bmatrix}-\begin{bmatrix}
        \boldsymbol{\mu} \newline
        \boldsymbol{\mu} \newline
        \boldsymbol{\mu} \newline
        \vdots \newline
        \boldsymbol{\mu}
    \end{bmatrix}\right)^{T}\begin{bmatrix}
        \boldsymbol{\Sigma}^{-1} & \mathbf{0} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}^{-1} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \mathbf{0} & \boldsymbol{\Sigma}^{-1} & \dotso & \mathbf{0} \newline
        \vdots & \vdots & \vdots & \dotso & \vdots \newline
        \mathbf{0} & \mathbf{0} & \mathbf{0} & \dotso & \boldsymbol{\Sigma}^{-1}
    \end{bmatrix}\left(\begin{bmatrix}
        \mathbf{x}\_{1} \newline
        \mathbf{x}\_{2} \newline
        \mathbf{x}\_{3} \newline
        \vdots \newline
        \mathbf{x}\_{n}
    \end{bmatrix}-\begin{bmatrix}
        \boldsymbol{\mu} \newline
        \boldsymbol{\mu} \newline
        \boldsymbol{\mu} \newline
        \vdots \newline
        \boldsymbol{\mu}
    \end{bmatrix}\right)
\end{equation}
Hence, the likelihood is an $ND$ variate Gaussian with the mean
\begin{equation}
    \begin{bmatrix}
        \boldsymbol{\mu} \newline
        \boldsymbol{\mu} \newline
        \boldsymbol{\mu} \newline
        \vdots \newline
        \boldsymbol{\mu}
    \end{bmatrix}
\end{equation}
and the covariance
\begin{equation}
    \begin{bmatrix}
        \boldsymbol{\Sigma} & \mathbf{0} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma} & \mathbf{0} &\dotso & \mathbf{0} \newline
        \vdots & \vdots & \vdots & \dotso & \vdots \newline
        \mathbf{0} & \mathbf{0} & \mathbf{0} & \dotso & \boldsymbol{\Sigma}
    \end{bmatrix}.
\end{equation}
## The Posterior
The prior for the mean of the data at hand is chosen as a Gaussian which is given as follows:
\begin{equation}
    p\left(\boldsymbol{\mu}\right)=N\left(\boldsymbol{\mu}| \boldsymbol{\mu}\_{0}, \boldsymbol{\Sigma}\_{0}\right)=\frac{1}{\left(2\pi\right)^{D/2}\left | \boldsymbol{\Sigma}\_{0} \right |^{1/2}}\exp\left[-\frac{1}{2}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{0}\right)^{T}\boldsymbol{\Sigma}\_{0}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{0}\right)\right]
    \label{prior}
\end{equation}
The posterior for the mean of the data at hand is proportional to the product of the prior and the likelihood:
\begin{equation}
    p\left(\boldsymbol{\mu}|\mathbf{X}, \boldsymbol{\Sigma}\right)=\frac{p\left(\boldsymbol{\mu}\right)p\left(\mathbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)}{p\left(\mathbf{X}|\mathbf{\Sigma}\right)} \Rightarrow
\end{equation}
\begin{equation}
    p\left(\boldsymbol{\mu}|\mathbf{X}, \boldsymbol{\Sigma}\right) \propto p\left(\boldsymbol{\mu}\right)p\left(\mathbf{X}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right)=
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi\right)^{D/2}\left | \boldsymbol{\Sigma}\_{0} \right |^{1/2}}\exp\left[-\frac{1}{2}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{0}\right)^{T}\boldsymbol{\Sigma}\_{0}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{0}\right)\right]\times
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi\right)^{ND/2}\left | \boldsymbol{\Sigma}\right |^{N/2}}\exp \left[\sum\_{i=1}^{N}-\frac{1}{2}\left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1} \left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)\right]\Rightarrow
\end{equation}
\begin{equation}
    p\left(\boldsymbol{\mu}|\mathbf{X}, \boldsymbol{\Sigma}\right) \propto \frac{1}{\left(2\pi\right)^{\left(N+1\right)D/2}\left | \boldsymbol{\Sigma}\right |^{\left(N+1\right)/2}} \times
\end{equation}
\begin{equation}
    \exp \left[-\frac{1}{2}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{0}\right)^{T}\boldsymbol{\Sigma}\_{0}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{0}\right)+\sum\_{i=1}^{N}-\frac{1}{2}\left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1} \left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)\right]
    \label{posterior\_1}
\end{equation}
Let the exponent in the equation (\ref{posterior\_1}) be examined to put it into the standard form of a multivariate Gaussian. The exponent of a multivariate Gaussian is as follows:
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\right)=-\frac{1}{2}\left(\mathbf{x}^{T}-\boldsymbol{\mu}^{T}\right)\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}^{T}-\boldsymbol{\mu}^{T}\right)\left(\boldsymbol{\Sigma}^{-1}\mathbf{x}-\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\mathbf{x}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}+\frac{1}{2}\mathbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}+\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}-\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu} \Rightarrow
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\mathbf{x}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1}\left(\mathbf{x}-\boldsymbol{\mu}\right)=-\frac{1}{2}\mathbf{x}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}+\mathbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}
    \label{standard\_exponent}
\end{equation}
From the equation (\ref{standard\_exponent}), it can be seen that the standard exponent has a quadratic term of $\mathbf{x}$, a linear term of $\mathbf{x}$ and a constant term independent of $\mathbf{x}$. The quadratic term contains the information for the precision which is the inverse of the covariance. The linear term carries the information for the mean. Considering this analysis of the exponent of the multivariate normal, the covariance and the mean of the posterior distribution is to be obtained from the exponent in the equation (\ref{posterior\_1}):
\begin{equation}
    -\frac{1}{2}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{0}\right)^{T}\boldsymbol{\Sigma}\_{0}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{0}\right)+\sum\_{i=1}^{N}-\frac{1}{2}\left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1} \left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\left(\boldsymbol{\mu}^{T}-\boldsymbol{\mu}\_{0}^{T}\right)\left(\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}-\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}\right)-\frac{1}{2}\sum\_{i=1}^{N}\left(\textbf{x}\_{i}^{T}-\boldsymbol{\mu}^{T}\right)\left(\boldsymbol{\Sigma}^{-1}\boldsymbol{x}\_{i}-\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}+\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}+\frac{1}{2}\boldsymbol{\mu}\_{0}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}-\frac{1}{2}\boldsymbol{\mu}\_{0}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}-
\end{equation}
\begin{equation}
    \frac{1}{2}\sum\_{i=1}^{N}\left(\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}-\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}-\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}+\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right)=
\end{equation}
\begin{equation}
    -\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}+\frac{1}{2}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}+\frac{1}{2}\boldsymbol{\mu}\_{0}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}-\frac{1}{2}\boldsymbol{\mu}\_{0}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}-
\end{equation}
\begin{equation}
    \frac{1}{2}\sum\_{i=1}^{N}\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}+\sum\_{i=1}^{N}\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}-\frac{1}{2}N\boldsymbol{\mu}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}=
\end{equation}
\begin{equation}
    -\frac{1}{2}\boldsymbol{\mu}^{T}\left(\boldsymbol{\Sigma}\_{0}^{-1}+N\boldsymbol{\Sigma}^{-1}\right)\boldsymbol{\mu}+\boldsymbol{\mu}^{T}\left(\frac{1}{2}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}+\frac{1}{2}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}+\boldsymbol{\Sigma}^{-1}\sum\_{i=1}^{N}\mathbf{x}\_{i}\right)-
\end{equation}
\begin{equation}
    \frac{1}{2}\boldsymbol{\mu}\_{0}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}-\frac{1}{2}\sum\_{i=1}^{N}\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}=
\end{equation}
\begin{equation}
    -\frac{1}{2}\boldsymbol{\mu}^{T}\left(\boldsymbol{\Sigma}\_{0}^{-1}+N\boldsymbol{\Sigma}^{-1}\right)\boldsymbol{\mu}+\boldsymbol{\mu}^{T}\left(\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}+\boldsymbol{\Sigma}^{-1}\sum\_{i=1}^{N}\mathbf{x}\_{i}\right)-
\end{equation}
\begin{equation}
    \frac{1}{2}\boldsymbol{\mu}\_{0}^{T}\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}-\frac{1}{2}\sum\_{i=1}^{N}\mathbf{x}\_{i}^{T}\boldsymbol{\Sigma}^{-1}\mathbf{x}\_{i}
\end{equation}
The precision $\boldsymbol{\Lambda}\_{N}$ of the posterior distribution of the mean is spotted to be $\boldsymbol{\Sigma}\_{0}^{-1}+N\boldsymbol{\Sigma}^{-1}$. Then:
\begin{equation}
    \left(\boldsymbol{\Sigma}\_{0}^{-1}+N\boldsymbol{\Sigma}^{-1}\right)\boldsymbol{\mu}\_{N}=\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}+\boldsymbol{\Sigma}^{-1}\sum\_{i=1}^{N}\mathbf{x}\_{i} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\mu}\_{N}=\left(\boldsymbol{\Sigma}\_{0}^{-1}+N\boldsymbol{\Sigma}^{-1}\right)^{-1}\left(\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}+\boldsymbol{\Sigma}^{-1}\sum\_{i=1}^{N}\mathbf{x}\_{i}\right)
\end{equation}
To sum up, the mean and covariance of the posterior distribution for the mean have been determined as follows:
\begin{equation}
    \boldsymbol{\mu}\_{N}=\left(\boldsymbol{\Sigma}\_{0}^{-1}+N\boldsymbol{\Sigma}^{-1}\right)^{-1}\left(\boldsymbol{\Sigma}\_{0}^{-1}\boldsymbol{\mu}\_{0}+\boldsymbol{\Sigma}^{-1}\sum\_{i=1}^{N}\mathbf{x}\_{i}\right)
    \label{posterior\_mean\_N}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{N}=(\boldsymbol{\Sigma}\_{0}^{-1}+N\boldsymbol{\Sigma}^{-1})^{-1}
    \label{posterior\_covariance\_N}
\end{equation}
Hence, the posterior probability density function of the mean given the data and the known covariance is as follows:
\begin{equation}
    p\left(\boldsymbol{\mu}|\mathbf{X}, \boldsymbol{\Sigma}\right)=N\left(\boldsymbol{\mu}|\boldsymbol{\mu}\_{N}, \boldsymbol{\Sigma}\_{N}\right)
\end{equation}
## The Sequential Update Of The Posterior
It is assumed that there is a stream of data. As data arrives, the posterior for the mean of the multivariate Gaussian model under the data is sequentially updated. In the beginning of the data stream, the prior for the mean is given by the equation (\ref{prior}). Once a stream of data with $N$ samples arrives, the posterior for the mean is calculated as a multivariate Gaussian with the mean and the covariance indicated in the equations (\ref{posterior\_mean\_N}) and (\ref{posterior\_covariance\_N}) respectively. When a new set of data arrives, this posterior is used as a prior for the mean of the multivariate Gaussian distribution under the data. The updated posterior will be proportional to the product of the prior and the likelihood of the new data:
\begin{equation}
    p\left(\boldsymbol{\mu}|\mathbf{X}\_{\text{updated}}, \boldsymbol{\Sigma}\right) \propto p\left(\boldsymbol{\mu}|\mathbf{X}, \boldsymbol{\Sigma}\right) p\left(\mathbf{X}\_{\text{new}}|\boldsymbol{\mu}, \boldsymbol{\Sigma}\right) \propto
\end{equation}
\begin{equation}
    \exp\left[-\frac{1}{2}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{N}\right)^{T}\boldsymbol{\Sigma}\_{N}^{-1}\left(\boldsymbol{\mu}-\boldsymbol{\mu}\_{N}\right)\right]\exp \left[\sum\_{i=1}^{N\_{\text{new}}}-\frac{1}{2}\left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)^{T}\boldsymbol{\Sigma}^{-1} \left(\textbf{x}\_{i}-\boldsymbol{\mu}\right)\right]
\end{equation}
Following the steps shown in the previous section, the sequentially updated posterior of the mean can be shown to have the following mean and covariance:
\begin{equation}
    \boldsymbol{\mu}\_{N+N\_{\text{new}}}=\left(\boldsymbol{\Sigma}\_{N}^{-1}+N\_{\text{new}}\boldsymbol{\Sigma}^{-1}\right)^{-1}\left(\boldsymbol{\Sigma}\_{N}^{-1}\boldsymbol{\mu}\_{N}+\boldsymbol{\Sigma}^{-1}\sum\_{i=1}^{N\_{\text{new}}}\mathbf{x}\_{i}\right)
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{N+N\_{\text{new}}}=(\boldsymbol{\Sigma}\_{N}^{-1}+N\_{\text{new}}\boldsymbol{\Sigma}^{-1})^{-1}
\end{equation}
## Conclusion
The posterior probability density function for the mean of a multivariate Gaussian distribution has been found given the data and the known covariance of the multivariate Gaussian distribution. A typical use case which is the sequential update of the posterior has been considered. It has been shown how to update the posterior as new data arrives. A sample implementation in a Jupyter notebook is given on [this link](https://github.com/SaffetGokcenSen/Gaussian-Models/blob/master/inferring_the_mean_of_an_mvn.ipynb).
## References

Pattern Recognition and Machine Learning, Christopher M. Bishop.

Machine Learning A Probabilistic Perspective, Kevin P. Murphy.