---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Inferring An Unknown Vector Using Noisy Measurements From Multiple Devices
---

## Introduction
In this article, a linear Gaussian system is used to infer an unknown vector from noisy measurements obtained by multiple measurement sources. The information from multiple measuring devices is combined and this is called the sensor fusion. A sample implementation is given in a Jupyter notebook on the link indicated in the conclusion section.
## Problem Description
There is an unknown vector $\mathbf{x}$. It has a multivariate Gaussian distribution. This distribution is called the prior and given by
\begin{equation}
    p\left(\mathbf{x}\right)=N\left(\boldsymbol{\mu}\_{x}, \boldsymbol{\Sigma}\_{x}\right)
\end{equation}
The number of measurement devices is $m$ where $m > 1$. The measurement devices are independent of each other. There are $N\_{k}$ measurements from the $k^{th}$ measurement device. The likelihood of the $i^{th}$ measurement from the $k^{th}$ device is as follows:
\begin{equation}
    p\left(\mathbf{y}\_{k}^{i}|\mathbf{x}\right)\propto N\left(\mathbf{x}, \boldsymbol{\Sigma}\_{y\_{\_{k}}}\right)
\end{equation}
There are $N\_{k}$ independent measurements from the $k^{th}$ device. The mean of these $N\_{k}$ measurements is taken as the final measurement:
\begin{equation}
    \bar{\mathbf{y}}\_{k}=\frac{1}{N\_{k}}\sum\_{i=1}^{N\_{k}}\mathbf{y}^{i}\_{k}
\end{equation}
The aim is to find the posterior distribution
\begin{equation}
    p\left(\mathbf{x}\big|\left[\bar{\mathbf{y}}\_{1}^{T} \ \bar{\mathbf{y}}\_{2}^{T} \ \bar{\mathbf{y}}\_{3}^{T} \dotso  \ \bar{\mathbf{y}}\_{m}^{T}\right]^{T}\right).
\end{equation}
## Solution
It can be proven that $\bar{\mathbf{y}}\_{k}$ has the following likelihood:
\begin{equation}
    p\left(\bar{\mathbf{y}}\_{k}|\mathbf{x}\right) \propto N\left(\mathbf{x},\frac{1}{N\_{k}}\boldsymbol{\Sigma}\_{y\_{\_{k}}}\right)
\end{equation}
where
\begin{equation}
    \boldsymbol{\Sigma}\_{k}\triangleq \frac{1}{N\_{k}}\boldsymbol{\Sigma}\_{y\_{\_{k}}}
\end{equation}
Let the likelihood
\begin{equation}
    p\left(\left[\bar{\mathbf{y}}\_{1}^{T} \ \bar{\mathbf{y}}\_{2}^{T} \ \bar{\mathbf{y}}\_{3}^{T} \dotso  \ \bar{\mathbf{y}}\_{m}^{T}\right]^{T}\big | \mathbf{x}\right)
\end{equation}
be determined. The measurement sources are independent of each other. Hence:
\begin{equation}
    p\left(\left[\bar{\mathbf{y}}\_{1}^{T} \ \bar{\mathbf{y}}\_{2}^{T} \ \bar{\mathbf{y}}\_{3}^{T} \dotso  \ \bar{\mathbf{y}}\_{m}^{T}\right]^{T}\big | \mathbf{x}\right)=p\left(\bar{\mathbf{y}}\_{1}| \mathbf{x}\right)p\left(\bar{\mathbf{y}}\_{2}| \mathbf{x}\right)p\left(\bar{\mathbf{y}}\_{3}| \mathbf{x}\right)\dotso p\left(\bar{\mathbf{y}}\_{m}| \mathbf{x}\right)\propto 
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi\right)^{N\_{1}/2}\left |\boldsymbol{\Sigma}\_{1} \right |^{1/2}}\exp\left[-\frac{1}{2}\left(\bar{\mathbf{y}}\_{1}-\mathbf{x}\right)^{T}\boldsymbol{\Sigma}\_{1}^{-1}\left(\bar{\mathbf{y}}\_{1}-\mathbf{x}\right)\right] \times
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi\right)^{N\_{2}/2}\left |\boldsymbol{\Sigma}\_{2} \right |^{1/2}}\exp\left[-\frac{1}{2}\left(\bar{\mathbf{y}}\_{2}-\mathbf{x}\right)^{T}\boldsymbol{\Sigma}^{-1}\_{2}\left(\bar{\mathbf{y}}\_{2}-\mathbf{x}\right)\right] \times
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi\right)^{N\_{3}/2}\left |\boldsymbol{\Sigma}\_{3} \right |^{1/2}}\exp\left[-\frac{1}{2}\left(\bar{\mathbf{y}}\_{3}-\mathbf{x}\right)^{T}\boldsymbol{\Sigma}^{-1}\_{3}\left(\bar{\mathbf{y}}\_{3}-\mathbf{x}\right)\right] \times \dotso \times
\end{equation}
\begin{equation}
    \frac{1}{\left(2\pi\right)^{N\_{m}/2}\left |\boldsymbol{\Sigma}\_{m} \right |^{1/2}}\exp\left[-\frac{1}{2}\left(\bar{\mathbf{y}}\_{m}-\mathbf{x}\right)^{T}\boldsymbol{\Sigma}^{-1}\_{m}\left(\bar{\mathbf{y}}\_{m}-\mathbf{x}\right)\right] \Rightarrow
\end{equation}
\begin{equation}
    p\left(\left[\bar{\mathbf{y}}\_{1}^{T} \ \bar{\mathbf{y}}\_{2}^{T} \ \bar{\mathbf{y}}\_{3}^{T} \dotso  \ \bar{\mathbf{y}}\_{m}^{T}\right]^{T}\big | \mathbf{x}\right)\propto \frac{1}{\prod\_{k=1}^{m}\left(2\pi\right)^{N\_{k}/2}\left |\boldsymbol{\Sigma}\_{k} \right |^{1/2}}\exp \left[\sum\_{k=1}^{m} -\frac{1}{2}\left(\bar{\mathbf{y}}\_{k}-\mathbf{x}\right)^{T}\boldsymbol{\Sigma}\_{k}^{-1}\left(\bar{\mathbf{y}}\_{k}-\mathbf{x}\right)\right]
    \label{likelihood}
\end{equation}
Then, the exponential in the equation (\ref{likelihood}) can be written as follows:
\begin{equation}
    \sum\_{k=1}^{m} -\frac{1}{2}\left(\bar{\mathbf{y}}\_{k}-\mathbf{x}\right)^{T}\boldsymbol{\Sigma}\_{k}\left(\bar{\mathbf{y}}\_{k}-\mathbf{x}\right)=-\frac{1}{2}\left (\begin{bmatrix}
        \bar{\mathbf{y}}\_{1} \newline
        \bar{\mathbf{y}}\_{2} \newline
        \bar{\mathbf{y}}\_{3} \newline
        \vdots \newline
        \bar{\mathbf{y}}\_{m}
    \end{bmatrix}-\begin{bmatrix}
        \mathbf{x} \newline
        \mathbf{x} \newline
        \mathbf{x} \newline
        \vdots \newline
        \mathbf{x}
    \end{bmatrix}\right )^{T}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{1} & \mathbf{0} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{2} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \mathbf{0} & \boldsymbol{\Sigma}\_{3} & \dotso & \mathbf{0} \newline
        \vdots & \vdots & \vdots & \vdots & \vdots \newline
        \mathbf{0} & \mathbf{0} & \mathbf{0} & \dotso & \boldsymbol{\Sigma}\_{m}
    \end{bmatrix}\left (\begin{bmatrix}
        \bar{\mathbf{y}}\_{1} \newline
        \bar{\mathbf{y}}\_{2} \newline
        \bar{\mathbf{y}}\_{3} \newline
        \vdots \newline
        \bar{\mathbf{y}}\_{m}
    \end{bmatrix}-\begin{bmatrix}
        \mathbf{x} \newline
        \mathbf{x} \newline
        \mathbf{x} \newline
        \vdots \newline
        \mathbf{x}
    \end{bmatrix}\right )
\end{equation}
Hence, the likelihood is proportional to a multivariate normal distribution with mean and covariance given as follows:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{y}}=\begin{bmatrix}
        \mathbf{x} \newline
        \mathbf{x} \newline
        \mathbf{x} \newline
        \vdots \newline
        \mathbf{x}
    \end{bmatrix}, \boldsymbol{\Sigma}\_{\mathbf{y}}=\begin{bmatrix}
        \boldsymbol{\Sigma}\_{1} & \mathbf{0} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{2} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \mathbf{0} & \boldsymbol{\Sigma}\_{3} & \dotso & \mathbf{0} \newline
        \vdots & \vdots & \vdots & \vdots & \vdots \newline
        \mathbf{0} & \mathbf{0} & \mathbf{0} & \dotso & \boldsymbol{\Sigma}\_{m}
    \end{bmatrix}
\end{equation}
The mean for the likelihood has the following relation with the prior mean $\mathbf{x}$:
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{y}}=\begin{bmatrix}
        \mathbf{x} \newline
        \mathbf{x} \newline
        \mathbf{x} \newline
        \vdots \newline
        \mathbf{x}
    \end{bmatrix}=\begin{bmatrix}
        \mathbf{I} \newline
        \mathbf{I} \newline
        \mathbf{I} \newline
        \vdots \newline
        \mathbf{I}
    \end{bmatrix}\mathbf{x}
\end{equation}
Hence,
\begin{equation}
    \boldsymbol{\mu}\_{\mathbf{y}}=\mathbf{A}\boldsymbol{\mu}\_{x}+\mathbf{b}
\end{equation}
where
\begin{equation}
    \mathbf{A}=\begin{bmatrix}
        \mathbf{I} \newline
        \mathbf{I} \newline
        \mathbf{I} \newline
        \vdots \newline
        \mathbf{I}
    \end{bmatrix}, \mathbf{b}=\mathbf{0}
\end{equation}
Given the prior $N\left(\mathbf{x}|\boldsymbol{\mu}\_{x}, \boldsymbol{\Sigma}\_{x}\right)$ and the likelihood proportional to $N\left(\mathbf{y}|\mathbf{A}\mathbf{x}+\mathbf{b}, \boldsymbol{\Sigma}\_{y}\right)$, it is known that the posterior $p\left(\mathbf{x}|\mathbf{y}\right)$ is given by either of the following two forms:
\begin{equation}
    p\left(\mathbf{x}|\mathbf{y}\right)=N\left(\mathbf{x}|\left(\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x|y}\right)\boldsymbol{\Sigma}\_{x}^{-1}\mathbf{A}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{x|y}\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}, \boldsymbol{\Sigma}\_{x|y}\right) \ \text{(first form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\Sigma}\_{x} \ \text{(first form)}
\end{equation}
\begin{equation}
    p\left(\mathbf{x}|\mathbf{y}\right)=N\left(\mathbf{x}|\boldsymbol{\Sigma}\_{x|y}\left[\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\left(\mathbf{y}-\mathbf{b}\right)+\boldsymbol{\Sigma}\_{x}^{-1}\boldsymbol{\mu}\_{x}\right], \boldsymbol{\Sigma}\_{x|y}\right) \ \text{(second form)}
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1} \ \text{(second form)}
\end{equation}
Let the first form of the posterior covariance matrix be calculated for the current problem:
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\right)^{-1}\mathbf{A}\boldsymbol{\Sigma}\_{x}=
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\mathbf{A}\boldsymbol{\Sigma}\_{x}\begin{bmatrix}
        \mathbf{I} & \mathbf{I} & \mathbf{I} & \dotso & \mathbf{I}
    \end{bmatrix}\right)^{-1}\begin{bmatrix}
        \mathbf{I} \newline
        \mathbf{I} \newline
        \mathbf{I} \newline
        \vdots \newline
        \mathbf{I}
    \end{bmatrix}\boldsymbol{\Sigma}\_{x}=
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\boldsymbol{\Sigma}\_{y}+\begin{bmatrix}
        \mathbf{I} \newline
        \mathbf{I} \newline
        \mathbf{I} \newline
        \vdots \newline
        \mathbf{I}
    \end{bmatrix}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{x}
    \end{bmatrix}\right)^{-1}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} \newline
        \vdots \newline
        \boldsymbol{\Sigma}\_{x}
    \end{bmatrix}=
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x}-\boldsymbol{\Sigma}\_{x}\mathbf{A}^{T}\left(\begin{bmatrix}
        \boldsymbol{\Sigma}\_{1} & \mathbf{0} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{2} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \mathbf{0} & \boldsymbol{\Sigma}\_{3} & \dotso & \mathbf{0} \newline
        \vdots & \vdots & \vdots & \vdots & \vdots \newline
        \mathbf{0} & \mathbf{0} & \mathbf{0} & \dotso & \boldsymbol{\Sigma}\_{m}
    \end{bmatrix}+ \begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{x} \newline
        \vdots & \vdots & \vdots & \dotso & \vdots \newline
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{x}
    \end{bmatrix}\right)^{-1}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} \newline
        \vdots \newline
        \boldsymbol{\Sigma}\_{x}
    \end{bmatrix} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\boldsymbol{\Sigma}\_{x}-\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{x}
    \end{bmatrix}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{1}+\boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{2}+\boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{3}+\boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{x} \newline
        \vdots & \vdots & \vdots & \dotso & \vdots \newline
        \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \boldsymbol{\Sigma}\_{x} & \dotso & \boldsymbol{\Sigma}\_{m}+\boldsymbol{\Sigma}\_{x}
    \end{bmatrix}^{-1}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} \newline
        \boldsymbol{\Sigma}\_{x} \newline
        \vdots \newline
        \boldsymbol{\Sigma}\_{x}
    \end{bmatrix}
\end{equation}
The inversion in the above equation can be numerically an ill-conditioned operation. It can be prone to numerical instabilities. Hence, care should be taken while using this form. The sample Jupyter notebook whose link is given in the conclusion section demonstrates such an ill-conditioned case.

Let the second form for the posterior covariance be calculated:
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\boldsymbol{\Sigma}\_{y}^{-1}\mathbf{A}\right)^{-1}=
\end{equation}
\begin{equation}
    \left(\boldsymbol{\Sigma}\_{x}^{-1}+\mathbf{A}^{T}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{1}^{-1} & \mathbf{0} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \boldsymbol{\Sigma}\_{2}^{-1} & \mathbf{0} & \dotso & \mathbf{0} \newline
        \mathbf{0} & \mathbf{0} & \boldsymbol{\Sigma}\_{3}^{-1} & \dotso & \mathbf{0} \newline
        \vdots & \vdots & \vdots & \vdots & \vdots \newline
        \mathbf{0} & \mathbf{0} & \mathbf{0} & \dotso & \boldsymbol{\Sigma}\_{m}^{-1}
    \end{bmatrix}\begin{bmatrix}
        \mathbf{I} \newline
        \mathbf{I} \newline
        \mathbf{I} \newline
        \vdots \newline
        \mathbf{I}
    \end{bmatrix}\right)^{-1}=
\end{equation}
\begin{equation}
    \left(\boldsymbol{\Sigma}\_{x}^{-1}+\begin{bmatrix}
        \mathbf{I} & \mathbf{I} & \mathbf{I} & \dotso & \mathbf{I}
    \end{bmatrix}\begin{bmatrix}
        \boldsymbol{\Sigma}\_{1}^{-1} \newline
        \boldsymbol{\Sigma}\_{2}^{-1} \newline
        \boldsymbol{\Sigma}\_{3}^{-1} \newline
        \vdots \newline
        \boldsymbol{\Sigma}\_{m}^{-1}
    \end{bmatrix}\right)^{-1} \Rightarrow
\end{equation}
\begin{equation}
    \boldsymbol{\Sigma}\_{x|y}=\left(\boldsymbol{\Sigma}\_{x}^{-1}+\sum\_{k=1}^{m}\boldsymbol{\Sigma}\_{k}^{-1}\right)^{-1}
\end{equation}
Obviously, the second form of the posterior covariance is easier to compute. It seems to be numerically more stable than the first form.
## Conclusion
There are more than one measurement devices which are independent of each other. Measurements are made for an unknown vector by these devices. The prior for the unknown vector is multivariate Gaussian and it is known. Additionally, likelihoods for the measurement devices are also known and they are all proportional to multivariate Gaussians. The prior and likelihoods form a linear Gaussian system. The posterior for the unknown vector has been calculated. A sample implementation can be found in the Jupyter notebook given on [this link](https://github.com/SaffetGokcenSen/Gaussian-Models/blob/master/inferring_an_unknown_vector_from_noisy_measurements_sensor_fusion.ipynb).
## References
[1] Machine Learning A Probabilistic Perspective, Kevin P. Murphy.

[2] <https://github.com/probml/pmtk3/blob/master/demos/sensorFusion2d.m>

[3] Inferring An Uknown Vector Using Noisy Measurements From A Single Device, <https://saffetgokcensen.github.io/blog/2020/07/28/inferring-an-unknown-vector-using-noisy-measurements-from-a-single-device>

[4] Bayes Rule For A Linear Gaussian System, <https://saffetgokcensen.github.io/blog/2020/07/08/bayes-rule-for-a-linear-gaussian-system>
