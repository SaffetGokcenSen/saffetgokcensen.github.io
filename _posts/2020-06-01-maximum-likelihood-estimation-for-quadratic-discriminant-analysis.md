---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Maximum Likelihood Estimation For Quadratic Discriminant Analysis
---
Assume that there is a discrete generative model. A classification is to be made using this model. The probability of the output to be in the class $c$ is given as follows:
\begin{equation}
p\left (y=c|\textbf{x}, \boldsymbol{\theta}\right )=\frac{p\left (\textbf{x}|y=c, \boldsymbol{\theta} \right )p\left (y=c|\boldsymbol{\theta} \right )}{p\left ( \textbf{x}|\boldsymbol{\theta}\right )}
\end{equation}
If the class conditioned probability density function of the input is given by a multivariate Gaussian distribution, then this classification is called the quadratic discriminant classification. The maximum likelihood estimator for the quadratic discriminant classifier is to be derived. Hence, the likelihood of the data should be written first. The likelihood of a single data sample $\left (\textbf{x}\_{i}, y\_{i} \right )$ is as follows:
\begin{equation}
p\left (\textbf{x}\_{i}, y\_{i}|\boldsymbol{\theta}\right )=p\left (\textbf{x}\_{i}|y\_{i}, \boldsymbol{\theta} \right ) p\left (y\_{i}|\boldsymbol{\theta} \right )=\prod\_{c=1}^{C} p\left (y\_{i}|\boldsymbol{\theta}\_{c} \right )^{I\left (y\_{i}=c \right )}\prod\_{c=1}^{C}p\left (\textbf{x}\_{i}|y\_{i}, \boldsymbol{\theta}\_{c} \right )^{I\left (y\_{i}=c \right )}
\end{equation}
Assuming that the samples are independent and there are $N$ training samples, the likelihood of the data can now be written as follows:
\begin{equation}
p\left (D|\boldsymbol{\theta} \right )=\prod\_{i=1}^{N} p\left (\textbf{x}\_{i}, y\_{i}|\boldsymbol{\theta} \right )
\end{equation}
For the sake of avoiding any numerical underflow and computational simplicity, the logarithm of the above expression is taken to obtain the log-likelihood:
\begin{equation}
\log p\left (D|\boldsymbol{\theta} \right )=\sum\_{i=1}^{N} \log p\left (\textbf{x}\_{i}, y\_{i}|\boldsymbol{\theta} \right )=
\end{equation}
\begin{equation}
\sum\_{i=1}^{N} \log \left [\prod\_{c=1}^{C} p\left (y\_{i}|\boldsymbol{\theta}\_{c} \right )^{I\left (y\_{i}=c \right )}\prod\_{c=1}^{C}p\left (\textbf{x}\_{i}|y\_{i}, \boldsymbol{\theta}\_{c} \right )^{I\left (y\_{i}=c \right )}\right ]=
\end{equation}
\begin{equation}
\sum\_{i=1}^{N} \left [\sum\_{c=1}^{C} \log \left [ p\left (y\_{i}|\boldsymbol{\theta}\_{c} \right )^{I\left (y\_{i}=c \right )}\right ]+\sum\_{c=1}^{C}\log \left [p\left (\textbf{x}\_{i}|y\_{i}, \boldsymbol{\theta}\_{c} \right )^{I\left (y\_{i}=c \right )}\right ]\right ]=
\end{equation}
\begin{equation}
\sum\_{i=1}^{N} \left [\sum\_{c=1}^{C} I\left (y\_{i}=c \right )\log p\left (y\_{i}|\boldsymbol{\theta}\_{c} \right ) +\sum\_{c=1}^{C}I\left (y\_{i}=c \right )\log p\left (\textbf{x}\_{i}|y\_{i}, \boldsymbol{\theta}\_{c} \right )\right ]\Rightarrow
\end{equation}
\begin{equation}
\log p\left (D|\boldsymbol{\theta} \right )=\sum\_{c=1}^{C} N\_{c}\log p\left (y\_{i}=c|\boldsymbol{\theta}\_{c} \right ) +\sum\_{c=1}^{C} \sum\_{i:y\_{i}=c}\log p\left (\textbf{x}\_{i}|y\_{i}, \boldsymbol{\theta}\_{c} \right )
\end{equation}
The first term is maximized if the maximum likelihood estimator (MLE) for the class occurrences which is
\begin{equation}
\pi\_{c\_{MLE}}=\frac{N\_{c}}{N}
\end{equation}
is plugged in place of $p\left (y\_{i}=c|\boldsymbol{\theta}\_{c} \right )$. $N\_{c}$ is the number of occurrences of the class $c$. The second term is maximized if the maximum likelihood estimators for the means and covariances of the multivariate Gaussian distributions for the probability densities of the input features conditioned on the class label are used. The MLE's for the mean and covariances are as follows:
\begin{equation}
\boldsymbol{\mu}\_{c\_{MLE}}=\frac{1}{N\_{c}}\sum\_{i:y\_{i}=c} x\_{i}
\end{equation}
\begin{equation}
\boldsymbol{\Sigma}\_{c\_{MLE}} = \frac{1}{N\_{c}} \sum\_{i:y\_{i}=c} \left (\textbf{x}\_{i}-\boldsymbol{\mu}\_{c\_{MLE}} \right )\left (\textbf{x}\_{i}-\boldsymbol{\mu}\_{c\_{MLE}} \right )^{T}
\end{equation}
A sample for the maximum likelihood estimation is given on [this link](https://github.com/SaffetGokcenSen/Gaussian-Models/blob/master/mle_for_quadratic_discriminant%20_analysis.ipynb).

$\textbf{References}$

Machine Learning A Probabilistic Perspective, Kevin P. Murphy
