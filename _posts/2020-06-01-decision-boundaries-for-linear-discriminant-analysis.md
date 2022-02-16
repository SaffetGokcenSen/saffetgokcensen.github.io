---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Decision Boundaries For Linear Discriminant Analysis
---
Assume that a classification is to be made. Given the parameters $\boldsymbol{\theta}$ and the input vector $\textbf{x}$, the class of the output variable $y$ is to be determined. The probability density function of $y$ being from the class $c$ is modeled using a discrete generative model as follows:
\begin{equation}
p\left (y=c|\textbf{x}, \boldsymbol{\theta}\right ) \propto \frac{p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )p\left ( y=c|\boldsymbol{\theta}\right )}{p\left (\textbf{x}|\boldsymbol{\theta} \right )}
\end{equation}
If a multivariate Gaussian distribution is used to model the class conditional density of the input vector, i.e. $p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )$, then this is called the quadratic discriminant analysis:
\begin{equation}
p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )=\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma}\_{c} \right |^{1/2}}\exp \left [-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )^{T}\boldsymbol{\Sigma}\_{c}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )\right ]
\end{equation}
A special case of the quadratic discriminant analysis is when the covariance matrix of the Gaussian distibution for the class conditional density of the input features is common to all of the classes. That is the mean,
\begin{equation}
\boldsymbol{\Sigma}\_{c}=\boldsymbol{\Sigma}
\end{equation}
for all of the classes $c$. Then, $p\left (y=c|\textbf{x}, \boldsymbol{\theta}\right )$ can be calculated as follows:
\begin{equation}
p\left (y=c|\textbf{x}, \boldsymbol{\theta}\right )\propto \frac{p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )p\left ( y=c|\boldsymbol{\theta}\right )}{p\left (\textbf{x}|\boldsymbol{\theta} \right )}=
\end{equation}
\begin{equation}
\frac{p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )p\left ( y=c|\boldsymbol{\theta}\right )}{\sum\_{s=1}^{C}p\left (x, y=s|\boldsymbol{\theta} \right )}=\frac{p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )p\left ( y=c|\boldsymbol{\theta}\right )}{\sum\_{s=1}^{C}p\left (\textbf{x}|y=s, \boldsymbol{\theta}\right )p\left ( y=s|\boldsymbol{\theta}\right )} \Rightarrow
\end{equation}
\begin{equation}
p\left (y=c|\textbf{x}, \boldsymbol{\theta}\right ) \propto \frac{\pi\_{c}p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )}{\sum\_{s=1}^{C}\pi\_{s}p\left (\textbf{x}|y=s, \boldsymbol{\theta}\right )} \Rightarrow
\end{equation}
\begin{equation}
p\left (y=c|\textbf{x}, \boldsymbol{\theta}\right ) \propto \frac{\pi\_{c}\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left [-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )^{T}\boldsymbol{\Sigma}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )\right ]}{\sum\_{s=1}^{C} \pi\_{s}\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left [-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{s} \right )^{T}\boldsymbol{\Sigma}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{s} \right )\right ]}
\end{equation}
Let the expression
\begin{equation}
-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )^{T}\boldsymbol{\Sigma}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )
\end{equation}
be simplified:
\begin{equation}
-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )^{T}\boldsymbol{\Sigma}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )=-\frac{1}{2}\left (\textbf{x}^{T}-\boldsymbol{\mu}\_{c}^{T} \right )\left ( \boldsymbol{\Sigma}^{-1}\textbf{x}-\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}\right )=
\end{equation}
\begin{equation}
-\frac{1}{2}\left (\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\textbf{x}-\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}-\boldsymbol{\mu}\_{c}^{T}\boldsymbol{\Sigma}^{-1}\textbf{x}+ \boldsymbol{\mu}\_{c}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}\right )=
\end{equation}
\begin{equation}
-\frac{1}{2}\left (\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\textbf{x}-2\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}+ \boldsymbol{\mu}\_{c}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}\right ) \Rightarrow
\end{equation}
\begin{equation}
-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )^{T}\boldsymbol{\Sigma}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )=-\frac{1}{2}\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\textbf{x}+\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}-\frac{1}{2}\boldsymbol{\mu}\_{c}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}
\end{equation}
The simplified expression is put into the class probability density conditioned on the input and parameters:
\begin{equation}
p\left (y=c|\textbf{x}, \boldsymbol{\theta}\right )\propto \frac{\pi\_{c}\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left [-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )^{T}\boldsymbol{\Sigma}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )\right ]}{\sum\_{s=1}^{C} \pi\_{s}\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left [-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{s} \right )^{T}\boldsymbol{\Sigma}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{s} \right )\right ]}=
\end{equation}
\begin{equation}
\frac{\pi\_{c}\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left [-\frac{1}{2}\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\textbf{x}+\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}-\frac{1}{2}\boldsymbol{\mu}\_{c}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}\right ]}{\sum\_{s=1}^{C} \pi\_{s}\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left [-\frac{1}{2}\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\textbf{x}+\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}-\frac{1}{2}\boldsymbol{\mu}\_{s}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}\right ]}=
\end{equation}
\begin{equation}
\frac{\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left ( -\frac{1}{2}\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\textbf{x}\right )\pi\_{c}\exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}-\frac{1}{2}\boldsymbol{\mu}\_{c}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}\right ]}{\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma} \right |^{1/2}}\exp \left (-\frac{1}{2}\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\textbf{x} \right )\sum\_{s=1}^{C} \pi\_{s}\exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}-\frac{1}{2}\boldsymbol{\mu}\_{s}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}\right ]}=
\end{equation}
\begin{equation}
\frac{\pi\_{c}\exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}-\frac{1}{2}\boldsymbol{\mu}\_{c}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}\right ]}{\sum\_{s=1}^{C} \pi\_{s}\exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}-\frac{1}{2}\boldsymbol{\mu}\_{s}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}\right ]} \Rightarrow
\end{equation}
\begin{equation}
p\left (y=c|\textbf{x}, \boldsymbol{\theta}\right )\propto \frac{\exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}+\log \pi\_{c}-\frac{1}{2}\boldsymbol{\mu}\_{c}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c}\right ]}{\sum\_{s=1}^{C} \exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}+\log \pi\_{s}-\frac{1}{2}\boldsymbol{\mu}\_{s}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}\right ]}
\end{equation}
The boundary separating two classes $c\_{1}$ and $c\_{2}$ is a linear function of $\textbf{x}$. Hence, this analysis is called the linear discriminant analysis. The equation for this linear boundary can be derived as follows:
\begin{equation}
p\left (y=c\_{1}|\textbf{x}, \boldsymbol{\theta}\right )=p\left (y=c\_{2}|\textbf{x}, \boldsymbol{\theta}\right ) \Rightarrow
\end{equation}
\begin{equation}
\frac{\exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}}+\log \pi\_{c\_{1}}-\frac{1}{2}\boldsymbol{\mu}\_{c\_{1}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}}\right ]}{\sum\_{s=1}^{C} \exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}+\log \pi\_{s}-\frac{1}{2}\boldsymbol{\mu}\_{s}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}\right ]}\propto
\end{equation}
\begin{equation}
\frac{\exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}}+\log \pi\_{c\_{2}}-\frac{1}{2}\boldsymbol{\mu}\_{c\_{2}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}}\right ]}{\sum\_{s=1}^{C} \exp \left [\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}+\log \pi\_{s}-\frac{1}{2}\boldsymbol{\mu}\_{s}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{s}\right ]} \Rightarrow
\end{equation}
\begin{equation}
\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}}+\log \pi\_{c\_{1}}-\frac{1}{2}\boldsymbol{\mu}\_{c\_{1}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}} \propto \textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}}+\log \pi\_{c\_{2}}-\frac{1}{2}\boldsymbol{\mu}\_{c\_{2}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}} \Rightarrow
\end{equation}
\begin{equation}
\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\textbf{x}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}}\propto \frac{1}{2}\boldsymbol{\mu}\_{c\_{1}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\frac{1}{2}\boldsymbol{\mu}\_{c\_{2}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}}+\log \pi\_{c\_{2}}-\log \pi\_{c\_{1}} \Rightarrow
\end{equation}
\begin{equation}
\textbf{x}^{T} \left (\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}} \right )\propto \frac{1}{2}\boldsymbol{\mu}\_{c\_{1}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\frac{1}{2}\boldsymbol{\mu}\_{c\_{2}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}}+\log \pi\_{c\_{2}}-\log \pi\_{c\_{1}}
\end{equation}
Assume that there are only two features which means that $\textbf{x}$ vector is two dimensional. Then, the equation of the boundary is as follows:
\begin{equation}
\beta\_{1}x\_{1}+ \beta\_{2}x\_{2}=\text{constant}
\end{equation}
where
\begin{equation}
\textbf{x}=\begin{bmatrix}
x\_{1} \newline
x\_{2}
\end{bmatrix}, \boldsymbol{\beta}=\begin{bmatrix}
\beta\_{1} \newline
\beta\_{2}
\end{bmatrix}=\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}}, 
\end{equation}
\begin{equation}
\text{constant}=\frac{1}{2}\boldsymbol{\mu}\_{c\_{1}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\frac{1}{2}\boldsymbol{\mu}\_{c\_{2}}^{T}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\_{c\_{2}}+\log \pi\_{c\_{2}}-\log \pi\_{c\_{1}}
\end{equation}
An example boundary is drawn in the Jupyter notebook on [this link.](https://github.com/SaffetGokcenSen/Gaussian-Models/blob/master/decision_boundaries_for_linear_discriminant_analysis.ipynb)

$\textbf{References}$

Machine Learning A Probabilistic Perspective, Kevin P. Murphy
