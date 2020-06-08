---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: "A Numpy Neural Network"
date: 2020-05-31
---
A neural network with $3$ hidden layers is to be constructed. The gradient of the loss function with respect to the weights and biases of the hidden units are derived. In a separate Jupyter notebook, the forward propagation and backward propagation are implemented using numpy to fit the network to a dataset. The output data and the input data are created randomly. The activation functions of the hidden units are all relu except the last hidden layer.

The dimension of the input layer is $d\_{in}$. It means that there are $d\_{in}$ features. The dimensions of the first, second and third layers are $d\_{1}$, $d\_{2}$ and $d\_{out}$ respectively. Hence, there are $d\_{out}$ outputs. Let the batch size be $n$. Then, the input to the first hidden layer is a matrix $\textbf{x}$ of dimension $n \times d\_{in}$. The weight matrix of the first hidden layer is $\textbf{w}\_{1}$ of dimension $d\_{in} \times d\_{1}$. 
The bias matrix of the first hidden layer is $\textbf{b}\_{1}$ of dimension $1 \times d\_{1}$. The output of the first hidden layer is $\textbf{h}\_{1}$ given by
\begin{equation}
    \textbf{h}\_{1}=\textbf{x}. \textbf{w}\_{1} + \textbf{1}\_{\text{n}\times \text{1}}. \textbf{b}\_{1}
\end{equation}
\begin{equation}
    \textbf{h}\_{1\_{\text{relu}}}=\text{Relu}\left(\textbf{h}\_{1}\right)
\end{equation}
$\textbf{1}\_{\text{n}\times \text{1}}$ is a matrix of ones with dimension $\text{n} \times \text{1}$. Let $\textbf{1}\_{\text{n}\times \text{1}}. \textbf{b}\_{1}$ be denoted by $\textbf{B}\_{1}$. $\textbf{B}\_{1}$, $\textbf{h}\_{1}$ and $\textbf{h}\_{1\_{\text{relu}}}$ are of dimension $n \times d\_{1}$. The weight matrix of the second hidden layer is $\textbf{w}\_{2}$ of dimension $d\_{1} \times d\_{2}$. The bias matrix of the second hidden layer is $\textbf{b}\_{2}$ of dimension $1 \times d\_{2}$. The output of the second hidden layer is $\textbf{h}\_{2}$ given by
\begin{equation}
    \textbf{h}\_{2}=\textbf{h}\_{1\_{\text{relu}}}. \textbf{w}\_{2} + \textbf{1}\_{\text{n}\times \text{1}}.\textbf{b}\_{2}
\end{equation}
\begin{equation}
    \textbf{h}\_{2\_{\text{relu}}}=\text{Relu}\left(\textbf{h}\_{2}\right)
\end{equation}
Let $\textbf{x}\_{1}$ be denoted by $\textbf{B}\_{2}$. $\textbf{B}\_{2}$, $\textbf{h}\_{2}$ and $\textbf{h}\_{2\_{\text{relu}}}$ are of dimension $n \times d\_{2}$. The weight matrix of the third hidden layer is $\textbf{w}\_{3}$ of dimension $d\_{2} \times d\_{\text{out}}$. The bias matrix of the third hidden layer is $\textbf{b}\_{3}$ of dimension $1 \times d\_{\text{out}}$. The output of the third hidden layer is $y\_{\text{pred}}$ given by
\begin{equation}
    \textbf{y}\_{\text{pred}}=\textbf{h}\_{2\_{\text{relu}}}. \textbf{w}\_{3} + \textbf{1}\_{\text{n}\times \text{1}}.\textbf{b}\_{3}
\end{equation}
Let $\textbf{1}\_{\text{n}\times \text{1}}. \textbf{b}\_{3}$ be denoted by $\textbf{B}\_{3}$. $\textbf{B}\_{3}$ and $\textbf{y}\_{\text{pred}}$ are of dimension $n \times d\_{\text{out}}$. The loss function is the mean squared error function. Hence,
\begin{equation}
    \text{L}=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}} \left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}
\end{equation}
The derivative of the loss function $\text{L}$ with respect to the matrix $\textbf{w}\_{3}$ is a matrix of dimension $1\times \left(\text{d}\_{2}.\text{d}\_{\text{out}}\right)$. The element in the column $\text{k}.\text{l}$ of this matrix is given by
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{3}}\right )\_{1\left (\text{k}.\text{l} \right)}=\frac{\partial L}{\partial w\_{3\_{\text{k}\text{l}}}}=\frac{\partial}{\partial w\_{3\_{\text{k}\text{l}}}}\left [\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}} \left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}\frac{\partial}{\partial w\_{3\_{\text{k}\text{l}}}}\left [\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{3\_{\text{k}\text{l}}}}
\end{equation}
$y\_{\text{pred}\_{\text{ij}}}$ is equal to the following:
\begin{equation}
    y\_{\text{pred}\_{\text{ij}}} = \sum\_{m=1}^{d\_{2}} h\_{2\_{\text{relu}\_{\text{im}}}}  w\_{3\_{\text{mj}}} + B\_{3\_{\text{ij}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{3\_{\text{k}\text{l}}}}=h\_{2\_{\text{relu}\_{\text{im}}}}I\left (\text{m=k} \ \& \ \text{j=l}\right)
\end{equation}
Let the derivation for $\left (\frac{\partial \text{L}}{\partial \textbf{w}\_{3}}\right )\_{1\left (\text{k}.\text{l} \right)}$ be completed:
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{3}}\right )\_{1\left (\text{k}.\text{l} \right)}=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )h\_{2\_{\text{relu}\_{\text{im}}}}I\left (\text{m=k} \ \& \ \text{j=l}\right) \Rightarrow
\end{equation}
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{3}}\right )\_{1\left (\text{k}.\text{l} \right)}=\sum\_{i=1}^{n}2\left (y\_{\text{pred}\_{\text{il}}}-y\_{\text{il}}\right )h\_{2\_{\text{relu}\_{\text{ik}}}} \Rightarrow
\end{equation}
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{3}}\right )\_{1\left (\text{k}.\text{l} \right)}=\left [\textbf{h}\_{2\_{\text{relu}}}^{T}.2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right)\right ]\_{\text{kl}}
\end{equation}
If $\frac{\partial \text{L}}{\partial \textbf{w}\_{3}}$ is put into the form of a matrix of dimension $\text{d}\_{2} \times \text{d}\_{\text{out}}$, then it's equal to $\textbf{h}\_{2\_{\text{relu}}}^{T}.2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right)$.

Now, let the derivative of the loss with respect to the $\textbf{b}\_{3}$ matrix be derived. It is a matrix of dimension $\text{1} \times \text{d}\_{\text{out}}$. The element in its $\text{k}^{\text{th}}$ column is given as follows:
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{3}}\right )\_{1\text{k}}=\frac{\partial L}{\partial b\_{3\_{\text{k}}}}=\frac{\partial}{\partial b\_{3\_{\text{k}}}}\left [\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}} \left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}\frac{\partial}{\partial b\_{3\_{\text{k}}}}\left [\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{3\_{\text{k}}}}
\end{equation}
\begin{equation}
    y\_{\text{pred}\_{\text{ij}}} = \sum\_{m=1}^{d\_{2}} h\_{2\_{\text{relu}\_{\text{im}}}}  w\_{3\_{\text{mj}}} + B\_{3\_{\text{ij}}} \Rightarrow \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{3\_{\text{k}}}}=\frac{\partial B\_{3\_{\text{ij}}}}{\partial b\_{3\_{\text{k}}}}=\frac{\partial b\_{3\_{\text{j}}}}{\partial b\_{3\_{\text{k}}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{3\_{\text{k}}}}=I\left (\text{j=k}\right)
\end{equation}
Hence:
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{3}}\right )\_{1\text{k}}=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{3\_{\text{k}}}} \Rightarrow
\end{equation}
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{3}}\right )\_{1\text{k}}=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )I\left (\text{j=k}\right) \Rightarrow
\end{equation}
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{3}}\right )\_{1\text{k}}=\sum\_{i=1}^{n}2\left (y\_{\text{pred}\_{\text{ik}}}-y\_{\text{ik}}\right )
\end{equation}
The $\text{k}^{\text{th}}$ column of $\frac{\partial \text{L}}{\partial \textbf{b}\_{3}}$ is equal to the sum of the elements of the $\text{k}^{\text{th}}$ column of $2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right)$.

The derivative of $\text{L}$ with respect to the matrix $\textbf{w}\_{2}$ is to be derived. It is a matrix of dimension $1 \times \left(\text{d}\_{1}.\text{d}\_{2}\right)$. The element in the column $\text{k}.\text{l}$ of this matrix is given by
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{2}}\right )\_{1\left (\text{k}.\text{l} \right)}=\frac{\partial L}{\partial w\_{2\_{\text{k}\text{l}}}}=\frac{\partial}{\partial w\_{2\_{\text{k}\text{l}}}}\left [\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}} \left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}\frac{\partial}{\partial w\_{2\_{\text{k}\text{l}}}}\left [\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{2\_{\text{k}\text{l}}}}
\end{equation}
\begin{equation}
    y\_{\text{pred}\_{\text{ij}}} = \sum\_{m=1}^{d\_{2}} h\_{2\_{\text{relu}\_{\text{im}}}}  w\_{3\_{\text{mj}}} + B\_{3\_{\text{ij}}} = \sum\_{m=1}^{d\_{2}} h\_{2\_{\text{relu}\_{\text{im}}}}  w\_{3\_{\text{mj}}} + B\_{3\_{\text{ij}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{2\_{\text{k}\text{l}}}}=\sum\_{m=1}^{d\_{2}} \frac{\partial h\_{2\_{\text{relu}\_{\text{im}}}}}{\partial w\_{2\_{\text{k}\text{l}}}}  w\_{3\_{\text{mj}}}=\sum\_{m=1}^{d\_{2}} \frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{im}}}}\right )}{\partial w\_{2\_{\text{k}\text{l}}}}  w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}} \frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{im}}}}\right )}{\partial h\_{2\_{\_{\text{im}}}}}\frac{\partial h\_{2\_{\_{\text{im}}}}}{\partial w\_{2\_{\text{k}\text{l}}}}  w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}} \frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{im}}}}\right )}{\partial h\_{2\_{\_{\text{im}}}}}\frac{\partial }{\partial w\_{2\_{\text{k}\text{l}}}}\left (\sum\_{p=1}^{d\_{1}} h\_{1\_{\text{relu}\_{\text{ip}}}}  w\_{2\_{\text{pm}}} + B\_{2\_{\text{im}}} \right )w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}} \frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{im}}}}\right )}{\partial h\_{2\_{\_{\text{im}}}}} h\_{1\_{\text{relu}\_{\text{ip}}}} I\left(\text{p=k} \ \& \ \text{m=l} \right) w\_{3\_{\text{mj}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{2\_{\text{k}\text{l}}}}=\frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{il}}}}\right )}{\partial h\_{2\_{\_{\text{il}}}}} h\_{1\_{\text{relu}\_{\text{ik}}}}w\_{3\_{\text{lj}}}
\end{equation}
Going on with the derivation:
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{2}}\right )\_{1\left (\text{k}.\text{l} \right)}=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{2\_{\text{k}\text{l}}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{il}}}}\right )}{\partial h\_{2\_{\_{\text{il}}}}} h\_{1\_{\text{relu}\_{\text{ik}}}}w\_{3\_{\text{lj}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{il}}}}\right )}{\partial h\_{2\_{\_{\text{il}}}}} h\_{1\_{\text{relu}\_{\text{ik}}}}\left (\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )w\_{3\_{\text{lj}}}\right ) \Rightarrow
\end{equation}
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{2}}\right )\_{1\left (\text{k}.\text{l} \right)}=\sum\_{i=1}^{n}h\_{1\_{\text{relu}\_{\text{ik}}}}\frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{il}}}}\right )}{\partial h\_{2\_{\_{\text{il}}}}} \left[2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right]\_{\text{il}}
\end{equation}
Let the following definition be made for the matrix $\textbf{A}$:
\begin{equation}
    \text{A}\_{\text{il}}=\frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{il}}}}\right )}{\partial h\_{2\_{\_{\text{il}}}}}=
    \begin{cases}
        1 & \text{ if } h\_{2\_{\text{il}}} \geq 0 \newline
        0 & \text{ if } h\_{2\_{\text{il}}} < 0
    \end{cases}
\end{equation}
If $\frac{\partial \text{L}}{\partial \textbf{w}\_{2}}$ is put into a matrix of dimension $d\_{1} \times d\_{2}$, then it is equal to
\begin{equation}
    \textbf{h}\_{1\_{\text{relu}}}^{T}.\left (\textbf{A} \circ \left (2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right )\right )
\end{equation}
where $\circ$ denotes the Hadamard or Schur product of two matrices.

The derivative of $\text{L}$ with respect to the bias matrix $\textbf{b}\_{2}$ is going to be obtained. It is a matrix of $1 \times \text{d}\_{2}$. The element in its $\text{k}^{\text{th}}$ column is given as follows:
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{2}}\right )\_{1\text{k}}=\frac{\partial L}{\partial b\_{2\_{\text{k}}}}=\frac{\partial}{\partial b\_{2\_{\text{k}}}}\left [\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}} \left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}\frac{\partial}{\partial b\_{2\_{\text{k}}}}\left [\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{2\_{\text{k}}}}
\end{equation}
\begin{equation}
    y\_{\text{pred}\_{\text{ij}}} = \sum\_{m=1}^{d\_{2}} h\_{2\_{\text{relu}\_{\text{im}}}}  w\_{3\_{\text{mj}}} + B\_{3\_{\text{ij}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{2\_{\text{k}}}}=\sum\_{m=1}^{d\_{2}} \frac{\partial h\_{2\_{\text{relu}\_{\text{im}}}}}{\partial b\_{2\_{\text{k}}}}  w\_{3\_{\text{mj}}}=\sum\_{m=1}^{d\_{2}} \frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{im}}}}\right )}{\partial b\_{2\_{\text{k}}}}  w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}} \frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{im}}}}\right )}{\partial h\_{2\_{\_{\text{im}}}}}\frac{\partial h\_{2\_{\_{\text{im}}}}}{\partial b\_{2\_{\text{k}}}}  w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}} \frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{im}}}}\right )}{\partial h\_{2\_{\_{\text{im}}}}}\frac{\partial }{\partial b\_{2\_{\text{k}}}}\left (\sum\_{p=1}^{d\_{1}} h\_{1\_{\text{relu}\_{\text{ip}}}}  w\_{2\_{\text{pm}}} + B\_{2\_{\text{im}}} \right )w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}} \frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{im}}}}\right )}{\partial h\_{2\_{\_{\text{im}}}}}\frac{\partial b\_{2\_{\text{m}}}}{\partial b\_{2\_{\text{k}}}}w\_{3\_{\text{mj}}}=\sum\_{m=1}^{d\_{2}} \frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{im}}}}\right )}{\partial h\_{2\_{\_{\text{im}}}}}  I\left(\text{m=k}\right) w\_{3\_{\text{mj}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{2\_{\text{k}}}}=\frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{ik}}}}\right )}{\partial h\_{2\_{\_{\text{ik}}}}} w\_{3\_{\text{kj}}}
\end{equation}
Going on with the derivation:
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{2}}\right )\_{1\text{k}}=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{2\_{\text{k}}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{ik}}}}\right )}{\partial h\_{2\_{\_{\text{ik}}}}} w\_{3\_{\text{kj}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{ik}}}}\right )}{\partial h\_{2\_{\_{\text{ik}}}}} \left (\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )w\_{3\_{\text{kj}}}\right ) \Rightarrow
\end{equation}
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{2}}\right )\_{1\text{k}}=\sum\_{i=1}^{n}\frac{\partial \text{Relu} \left (h\_{2\_{\_{\text{ik}}}}\right )}{\partial h\_{2\_{\_{\text{ik}}}}} \left[2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right]\_{\text{ik}}
\end{equation}
The $\text{k}^{\text{th}}$ column of $\frac{\partial \text{L}}{\partial \textbf{b}\_{2}}$ is equal to the sum of the elements in the $\text{k}^{\text{th}}$ column of $\textbf{A} \circ \left[2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right]$.

The derivative of the loss $\text{L}$ is to be derived with respect to the weight matrix $\textbf{w}\_{1}$. This derivative will be of dimension $1\times \left(\text{d}\_{\text{in}}.\text{d}\_{1}\right)$.
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{1}}\right )\_{1\left (\text{k}.\text{l} \right)}=\frac{\partial L}{\partial w\_{1\_{\text{k}\text{l}}}}=\frac{\partial}{\partial w\_{1\_{\text{k}\text{l}}}}\left [\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}} \left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}\frac{\partial}{\partial w\_{1\_{\text{k}\text{l}}}}\left [\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{1\_{\text{k}\text{l}}}}
\end{equation}
\begin{equation}
    y\_{\text{pred}\_{\text{ij}}} = \sum\_{m=1}^{d\_{2}} h\_{2\_{\text{relu}\_{\text{im}}}}  w\_{3\_{\text{mj}}} + B\_{3\_{\text{ij}}}=\sum\_{m=1}^{d\_{2}} \text{Relu}\left (h\_{2\_{\_{\text{im}}}} \right)  w\_{3\_{\text{mj}}} + B\_{3\_{\text{ij}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{1\_{\text{k}\text{l}}}}=\sum\_{m=1}^{d\_{2}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial h\_{2\_{\text{im}}}}{\partial w\_{1\_{\text{k}\text{l}}}}w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial }{\partial w\_{1\_{\text{k}\text{l}}}}\left (\sum\_{p=1}^{d\_{1}}h\_{1\_{\text{relu}\_{\text{ip}}}}w\_{2\_{\text{pm}}}+B\_{2\_{\text{im}}}\right)=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\sum\_{p=1}^{d\_{1}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ip}}}\right )}{\partial h\_{1\_{\text{ip}}}}\frac{\partial h\_{1\_{\text{ip}}}}{\partial w\_{1\_{\text{k}\text{l}}}} w\_{2\_{\text{pm}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\sum\_{p=1}^{d\_{1}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ip}}}\right )}{\partial h\_{1\_{\text{ip}}}}\frac{\partial}{\partial w\_{1\_{\text{k}\text{l}}}}\left(\sum\_{q=1}^{d\_{\text{in}}}x\_{\text{iq}}w\_{1\_{\text{qp}}}+B\_{1\_{\text{ip}}}\right) w\_{2\_{\text{pm}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\sum\_{p=1}^{d\_{1}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ip}}}\right )}{\partial h\_{1\_{\text{ip}}}}x\_{\text{iq}}I\left(\text{q=k} \ \& \ \text{p=l}\right )w\_{2\_{\text{pm}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{1\_{\text{k}\text{l}}}}=\sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{il}}}\right )}{\partial h\_{1\_{\text{il}}}}x\_{\text{ik}}w\_{2\_{\text{lm}}}
\end{equation}
Going on with the derivation of $\frac{\partial L}{\partial \textbf{w}\_{1}}$:
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{1}}\right )\_{1\left (\text{k}.\text{l} \right)}=\frac{\partial L}{\partial w\_{1\_{\text{k}\text{l}}}}=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial w\_{1\_{\text{k}\text{l}}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\left(\sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{il}}}\right )}{\partial h\_{1\_{\text{il}}}}x\_{\text{ik}}w\_{2\_{\text{lm}}}\right)=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}\sum\_{m=1}^{d\_{2}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{il}}}\right )}{\partial h\_{1\_{\text{il}}}}x\_{\text{ik}}w\_{2\_{\text{lm}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{m=1}^{d\_{2}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{il}}}\right )}{\partial h\_{1\_{\text{il}}}}x\_{\text{ik}}w\_{2\_{\text{lm}}}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\frac{\partial \text{Relu}\left (h\_{1\_{\text{il}}}\right )}{\partial h\_{1\_{\text{il}}}}x\_{\text{ik}}\sum\_{m=1}^{d\_{2}}w\_{2\_{\text{lm}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right)\_{\text{im}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}x\_{\text{ik}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{il}}}\right )}{\partial h\_{1\_{\text{il}}}}\left(\left(\textbf{A}\circ\left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right)\right).\textbf{w}\_{2}^{T}\right)\_{\text{il}}=
\end{equation}
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{w}\_{1}}\right )\_{1\left (\text{k}.\text{l} \right)}=\left(\textbf{x}^{T}.\left(\textbf{C}\circ\left(\left(\textbf{A}\circ\left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right)\right).\textbf{w}\_{2}^{T}\right)\right)\right)\_{\text{kl}}
\end{equation}
where the matrix $\textbf{C}$ is defined as:
\begin{equation}
    \text{C}\_{\text{il}}=\frac{\partial \text{Relu} \left (h\_{1\_{\_{\text{il}}}}\right )}{\partial h\_{1\_{\_{\text{il}}}}}=
    \begin{cases}
        1 & \text{ if } h\_{1\_{\text{il}}} \geq 0 \newline
        0 & \text{ if } h\_{1\_{\text{il}}} < 0 \ 
    \end{cases}
\end{equation}
If $\frac{\partial \text{L}}{\partial \textbf{w}\_{1}}$ is put into the form of a matrix with dimension $\text{d}\_{\text{in}}\times \text{d}\_{1}$, then this matrix is given by $\textbf{x}^{T}.\left(\textbf{C}\circ\left(\left(\textbf{A}\circ\left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right)\right).\textbf{w}\_{2}^{T}\right)\right)$.

It is now the turn of the derivative of $\text{L}$ with respect to the bias matrix $\textbf{b}\_{1}$. This derivative is a matrix with dimension $1\times \text{d}\_{1}$:
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{1}}\right )\_{1\text{k}}=\frac{\partial L}{\partial b\_{1\_{\text{k}}}}=\frac{\partial}{\partial b\_{1\_{\text{k}}}}\left [\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}} \left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}\frac{\partial}{\partial b\_{1\_{\text{k}}}}\left [\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right)^{2}\right ]=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{1\_{\text{k}}}}
\end{equation}
\begin{equation}
    y\_{\text{pred}\_{\text{ij}}} = \sum\_{m=1}^{d\_{2}} h\_{2\_{\text{relu}\_{\text{im}}}}  w\_{3\_{\text{mj}}} + B\_{3\_{\text{ij}}}=\sum\_{m=1}^{d\_{2}} \text{Relu}\left (h\_{2\_{\_{\text{im}}}} \right)  w\_{3\_{\text{mj}}} + B\_{3\_{\text{ij}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{1\_{\text{k}\text{l}}}}=\sum\_{m=1}^{d\_{2}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial h\_{2\_{\text{im}}}}{\partial b\_{1\_{\text{k}}}}w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial }{\partial b\_{1\_{\text{k}}}}\left (\sum\_{p=1}^{d\_{1}}h\_{1\_{\text{relu}\_{\text{ip}}}}w\_{2\_{\text{pm}}}+B\_{2\_{\text{im}}}\right)=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\sum\_{p=1}^{d\_{1}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ip}}}\right )}{\partial h\_{1\_{\text{ip}}}}\frac{\partial h\_{1\_{\text{ip}}}}{\partial b\_{1\_{\text{k}}}} w\_{2\_{\text{pm}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\sum\_{p=1}^{d\_{1}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ip}}}\right )}{\partial h\_{1\_{\text{ip}}}}\frac{\partial}{\partial b\_{1\_{\text{k}}}}\left(\sum\_{q=1}^{d\_{\text{in}}}x\_{\text{iq}}w\_{1\_{\text{qp}}}+B\_{1\_{\text{ip}}}\right) w\_{2\_{\text{pm}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\sum\_{p=1}^{d\_{1}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ip}}}\right )}{\partial h\_{1\_{\text{ip}}}}\frac{\partial b\_{1\_{\text{p}}}}{\partial b\_{1\_{\text{k}}}} w\_{2\_{\text{pm}}}=
\end{equation}
\begin{equation}
    \sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\sum\_{p=1}^{d\_{1}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ip}}}\right )}{\partial h\_{1\_{\text{ip}}}}I\left(\text{p=k}\right )w\_{2\_{\text{pm}}} \Rightarrow
\end{equation}
\begin{equation}
    \frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{1\_{\text{k}}}}=\sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ik}}}\right )}{\partial h\_{1\_{\text{ik}}}}w\_{2\_{\text{km}}}
\end{equation}
Going on with the derivation of $\frac{\partial L}{\partial \textbf{b}\_{1}}$:
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{1}}\right )\_{1\text{k}}=\frac{\partial L}{\partial b\_{1\_{\text{k}}}}=\sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\frac{\partial y\_{\text{pred}\_{\text{ij}}}}{\partial b\_{1\_{\text{k}}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )\left(\sum\_{m=1}^{d\_{2}}w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ik}}}\right )}{\partial h\_{1\_{\text{ik}}}}w\_{2\_{\text{km}}}\right)=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{j=1}^{d\_{\text{out}}}\sum\_{m=1}^{d\_{2}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )w\_{3\_{\text{mj}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ik}}}\right )}{\partial h\_{1\_{\text{ik}}}}w\_{2\_{\text{km}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\sum\_{m=1}^{d\_{2}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ik}}}\right )}{\partial h\_{1\_{\text{ik}}}}w\_{2\_{\text{km}}}\sum\_{j=1}^{d\_{\text{out}}}2\left (y\_{\text{pred}\_{\text{ij}}}-y\_{\text{ij}}\right )w\_{3\_{\text{mj}}}=
\end{equation}
\begin{equation}
    \sum\_{i=1}^{n}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ik}}}\right )}{\partial h\_{1\_{\text{ik}}}}\sum\_{m=1}^{d\_{2}}w\_{2\_{\text{km}}}\frac{\partial \text{Relu}\left (h\_{2\_{\text{im}}}\right )}{\partial h\_{2\_{\text{im}}}}\left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right)\_{\text{im}} \Rightarrow
\end{equation}
\begin{equation}
    \left (\frac{\partial \text{L}}{\partial \textbf{b}\_{1}}\right )\_{1\text{k}}=\sum\_{i=1}^{n}\frac{\partial \text{Relu}\left (h\_{1\_{\text{ik}}}\right )}{\partial h\_{1\_{\text{ik}}}}\left(\left(\textbf{A}\circ\left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right)\right).\textbf{w}\_{2}^{T}\right)\_{\text{ik}}
\end{equation}
The $\text{k}^{\text{th}}$ column of $\frac{\partial \text{L}}{\partial \textbf{b}\_{1}}$ is equal to the sum of the elements in the $\text{k}^{\text{th}}$ column of $\textbf{C}\circ \left(\left(\textbf{A}\circ\left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right)\right).\textbf{w}\_{2}^{T}\right)$.

The gradient results can be summarized as follows:
\begin{equation}
    \frac{\partial \text{L}}{\partial \textbf{w}\_{3}} \rightarrow \textbf{h}\_{2\_{\text{relu}}}^{T}.2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right)
\end{equation}
\begin{equation}
    \left(\frac{\partial \text{L}}{\partial \textbf{b}\_{3}}\right)\_{\text{k}} = \sum\_{\text{i}=1}^{n} \left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right)\right)\_{\text{ik}}
\end{equation}
\begin{equation}
    \frac{\partial \text{L}}{\partial \textbf{w}\_{2}} \rightarrow \textbf{h}\_{1\_{\text{relu}}}^{T}.\left (\textbf{A} \circ \left (2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right )\right )
\end{equation}
\begin{equation}
    \left(\frac{\partial \text{L}}{\partial \textbf{b}\_{2}}\right)\_{\text{k}} = \sum\_{\text{i}=1}^{n} \left(\textbf{A} \circ \left (2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right )\right)\_{\text{ik}}
\end{equation}
\begin{equation}
    \frac{\partial \text{L}}{\partial \textbf{w}\_{1}} \rightarrow \textbf{x}^{T}.\left(\textbf{C}\circ\left(\left(\textbf{A}\circ\left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right)\right).\textbf{w}\_{2}^{T}\right)\right)
\end{equation}
\begin{equation}
    \left(\frac{\partial \text{L}}{\partial \textbf{b}\_{1}}\right)\_{\text{k}} = \sum\_{\text{i}=1}^{n}(\textbf{C}\circ\left(\left(\textbf{A}\circ\left(2\left(\textbf{y}\_{\text{pred}}-\textbf{y}\right).\textbf{w}\_{3}^{T}\right)\right).\textbf{w}\_{2}^{T}\right))\_{\text{ik}}
\end{equation}
The numerical implementation of the above gradients, the updates of the weight matrices and the bias matrices are carried out as a numpy neural network in a separate Jupyter notebook on [this link](https://github.com/SaffetGokcenSen/deep_learning/blob/master/numpy_neural_network.ipynb).
