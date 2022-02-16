---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: Decision Boundaries For Quadratic Discriminant Analysis
---
Assume that a classification is to be made. Given the parameters $\boldsymbol{\theta}$ and the input vector $\textbf{x}$, the class of the output variable $y$ is to be determined. The probability density function of $y$ being from the class $c$ is modeled using a discrete generative model as follows:
\begin{equation}
p\left (y=c|\textbf{x}, \boldsymbol{\theta}\right )\propto \frac{p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )p\left ( y=c|\boldsymbol{\theta}\right )}{p\left (\textbf{x}|\boldsymbol{\theta} \right )}
\end{equation}
If a multivariate Gaussian distribution is used to model the class conditional density of the input vector, i.e. $p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )$, then this is called the quadratic discriminant analysis:
\begin{equation}
p\left (\textbf{x}|y=c, \boldsymbol{\theta}\right )=\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma}\_{c} \right |^{1/2}}\exp \left [-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )^{T}\boldsymbol{\Sigma}\_{c}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c} \right )\right ]
\end{equation}
The name "quadratic" comes from the fact that the decision boundaries separating classes are in general quadratic.
Let the decision boundary between two classes be drawn to illustrate the quadratic boundary. First, the following equation is to be solved:
\begin{equation}
p\left (y=c\_{1}|\textbf{x}, \boldsymbol{\theta}\right )=p\left (y=c\_{2}|\textbf{x}, \boldsymbol{\theta}\right ) \Rightarrow 
\end{equation}
\begin{equation}
\frac{p\left (\textbf{x}|y=c\_{1}, \boldsymbol{\theta}\right )p\left ( y=c\_{1}|\boldsymbol{\theta}\right )}{p\left (\textbf{x}|\boldsymbol{\theta} \right )}\propto \frac{p\left (\textbf{x}|y=c\_{2}, \boldsymbol{\theta}\right )p\left ( y=c\_{2}|\boldsymbol{\theta}\right )}{p\left (\textbf{x}|\boldsymbol{\theta} \right )} \Rightarrow
\end{equation}
\begin{equation}
p\left (\textbf{x}|y=c\_{1}, \boldsymbol{\theta}\right )p\left ( y=c\_{1}|\boldsymbol{\theta}\right )\propto p\left (\textbf{x}|y=c\_{2}, \boldsymbol{\theta}\right )p\left ( y=c\_{2}|\boldsymbol{\theta}\right ) \Rightarrow
\end{equation}
\begin{equation}
\pi\_{1}\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma}\_{c\_{1}} \right |^{1/2}}\exp \left [-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{c\_{1}} \right )^{T}\boldsymbol{\Sigma}\_{c\_{1}}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c\_{1}} \right )\right ] \propto
\end{equation}
\begin{equation}
\pi\_{2}\frac{1}{\left (2\pi \right )^{D/2} \left | \boldsymbol{\Sigma}\_{c\_{2}} \right |^{1/2}}\exp \left [-\frac{1}{2}\left (\textbf{x}-\boldsymbol{\mu}\_{c\_{2}} \right )^{T}\boldsymbol{\Sigma}\_{c\_{2}}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c\_{2}} \right )\right ]
\end{equation}
After taking the natural logarithm of both sides, the following simplified form is obtained:
\begin{equation}
0 = 
\end{equation}
\begin{equation}
\frac{1}{2}\left [ \left (\textbf{x}-\boldsymbol{\mu}\_{c\_{1}} \right )^{T}\boldsymbol{\Sigma}\_{c\_{1}}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c\_{1}} \right )- \left (\textbf{x}-\boldsymbol{\mu}\_{c\_{2}} \right )^{T}\boldsymbol{\Sigma}\_{c\_{2}}^{-1} \left (\textbf{x}-\boldsymbol{\mu}\_{c\_{2}} \right )\right ]+\frac{1}{2}\log \left (\frac{\left | \boldsymbol{\Sigma}\_{c\_{1}} \right |}{\left | \boldsymbol{\Sigma}\_{c\_{2}} \right |} \right )-\log\left (\frac{\pi\_{c\_{1}}}{\pi\_{c\_{2}}} \right )
\end{equation}
Since $\textbf{x}$, $\boldsymbol{\mu}\_{c\_{1}}$ and $\boldsymbol{\mu}\_{c\_{2}}$ are column vectors, $\left (\textbf{x}-\boldsymbol{\mu}\_{c\_{1}} \right )^{T}=\textbf{x}^{T}-\boldsymbol{\mu}\_{c\_{1}}^{T}$ and $\left (\textbf{x}-\boldsymbol{\mu}\_{c\_{2}} \right )^{T}=\textbf{x}^{T}-\boldsymbol{\mu}\_{c\_{2}}^{T}$. After these equalities are used in the above equation, the following final form is obtained:
\begin{equation}
0=
\end{equation}
\begin{equation}
\frac{1}{2}\textbf{x}^{T}\left (\boldsymbol{\Sigma}\_{c\_{1}}^{-1}-\boldsymbol{\Sigma}\_{c\_{2}}^{-1}\right )\textbf{x}-\textbf{x}^{T} \left (\boldsymbol{\Sigma}\_{c\_{1}}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\boldsymbol{\Sigma}\_{c\_{2}}^{-1}\boldsymbol{\mu}\_{c\_{2}} \right )+\frac{1}{2} \left (\boldsymbol{\mu}\_{c\_{1}}^{T} \boldsymbol{\Sigma}\_{c\_{1}}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\boldsymbol{\mu}\_{c\_{2}}^{T} \boldsymbol{\Sigma}\_{c\_{2}}^{-1}\boldsymbol{\mu}\_{c\_{2}}\right )+
\end{equation}
\begin{equation}
\frac{1}{2}\log \left (\frac{\left | \boldsymbol{\Sigma}\_{c\_{1}} \right |}{\left | \boldsymbol{\Sigma}\_{c\_{2}} \right |} \right )-\log \left (\frac{\pi\_{c\_{1}}}{\pi\_{c\_{2}}} \right )
\end{equation}
This is a quadratic form. Hence, the decision boundary between the two classes is quadratic. Now, let this boundary be drawn for $D=2$, i.e. for the case when the random vectors are of dimension 2. If $A \triangleq \boldsymbol{\Sigma}\_{c\_{1}}^{-1}-\boldsymbol{\Sigma}\_{c\_{2}}^{-1}$, $B \triangleq \boldsymbol{\Sigma}\_{c\_{1}}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\boldsymbol{\Sigma}\_{c\_{2}}^{-1}\boldsymbol{\mu}\_{c\_{2}}$ and $\textbf{x}=\left [x\_{1} \ x\_{2} \right ]^{T}$, then:
\begin{equation}
0=
\end{equation}
\begin{equation}
\frac{1}{2}a\_{22}x\_{2}^{2} + \left [ \frac{1}{2} \left (a\_{12}+a\_{21} \right )x\_{1}-b\_{21}\right ]x\_{2}+
\end{equation}
\begin{equation}
\left [\frac{1}{2}a\_{11}x\_{1}^{2}-b\_{11}x\_{1}+\frac{1}{2}\left ( \boldsymbol{\mu}\_{c\_{1}}^{T} \boldsymbol{\Sigma}\_{c\_{1}}^{-1}\boldsymbol{\mu}\_{c\_{1}}-\boldsymbol{\mu}\_{c\_{2}}^{T} \boldsymbol{\Sigma}\_{c\_{2}}^{-1}\boldsymbol{\mu}\_{c\_{2}}\right )+\frac{1}{2}\log \left (\frac{\left | \boldsymbol{\Sigma}\_{c\_{1}} \right |}{\left | \boldsymbol{\Sigma}\_{c\_{2}} \right |} \right )- \log \left (\frac{\pi\_{c\_{1}}}{\pi\_{c\_{2}}} \right )\right ]
\end{equation}
gives element $x\_{2}$ given element $x\_{1}$ of $\textbf{x}$. An example for such a boundary is drawn in a separate Jupyter notebook on [this link.](https://github.com/SaffetGokcenSen/Gaussian-Models/blob/master/decision_boundaries_for_quadratic_discriminant_analysis.ipynb)

$\textbf{References}$

Machine Learning A Probabilistic Perspective, Kevin P. Murphy
