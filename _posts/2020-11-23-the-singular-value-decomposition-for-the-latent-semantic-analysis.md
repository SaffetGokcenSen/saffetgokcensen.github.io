---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: The Singular Value Decomposition For The Latent Semantic Analysis
---
## Introduction
Latent semantic analysis (LSA) is used to extract the topics of the documents in a corpus. LSA is based on the singular value decomposition (SVD). In this article, it is going to be presented how SVD discovers the hidden topics in a corpus of documents.
## Term Frequency Inverse Document Frequency (TF-IDF)
A document is a collection of words which are also called tokens. In order to process this text using a machine learning model, the text must be expressed in terms of numbers. One of the ways of converting text to numbers is term frequency-inverse document frequency (TF-IDF) measure.

Before defining TF-IDF measure, let a few definitions be given. A text made of words or tokens is called a document. The collection of documents is called a corpus. The tokens or words in this text form the vocabulary.

Term frequency is a measure of the frequency of a token in a document. It is given by the following expression:
\begin{equation}
    \text{TF}=\log \left(\frac{1+\text{token count}}{\text{document length}}\right)
\end{equation}
Inverse document frequency is a measure of the importance of a token across the documents in the corpus. It is mathematically given as follows:
\begin{equation}
    \text{IDF}=\log \left(\frac{\text{count of documents in the corpus}}{1+\text{count of documents containing the token}}\right)
\end{equation}
Hence, TF-IDF of a token in a corpus is
\begin{equation}
    \text{TF-IDF}=\log \left(\frac{1+\text{token count}}{\text{document length}}\right)\times \log \left(\frac{\text{count of documents in the corpus}}{1+\text{count of documents containing the token}}\right).
\end{equation}
If a token has a high term frequency in a document, then this is a clue that it is important for the document. But, the same token may be very frequent in the other documents of the corpus. Then, this token is not a distinguishing factor for documents. On the other hand, if the token is rare in the other documents, then this token is a distinguishing term for the document. In this case, both TF and IDF will be high.

A document in a corpus can be numerically represented using TF-IDF measure. TF-IDF of each token from the vocabulary is calculated for the document. This vector is the numerical representation for the document. The whole corpus can then be described by means of a matrix whose entries are TF-IDFs. Each row of the matrix corresponds to the TF-IDF vector for the corresponding document. The matrix is of dimension $m \times n$ where $m$ is the number of documents in the corpus and $n$ is the number of tokens in the vocabulary.

## SVD For The Latent Semantic Analysis
A corpus consisting of documents should have a distribution of topics. The documents in the corpus sheould be about several topics. How can these topics be extracted using the TF-IDF descriptions of the documents? Semantic is synonym to meaning and latent means hidden. By means of latent semantic analysis, the topics hidden in the corpus of documents are discovered. There are ways of doing latent semantic analysis. SVD is the method to be used here.

Assume that there is a matrix $A$ of dimension $m \times n$. This matrix can be factored to three matrices as follows:
\begin{equation}
    A=U\Sigma V^{T}
    \label{SVD}
\end{equation}
where $U$ is of dimension $m \times m$, $\Sigma$ is of dimension $m \times n$ and $V$ is of dimension $n \times n$. The columns of $U$ are the eigenvectors of $AA^{T}$. The columns of $V$ are the eigenvectors of $A^{T}A$. $\Sigma$ is a matrix whose nonzero entries are on the diagonal and are equal the square roots of the eigenvalues of $AA^{T}$ or $A^{T}A$. They are arranged in a decreasing order.

Let $A$ be the token-document matrix which is the transpose of the TF-IDF matrix explained in the previous section. Then, each column of $A$ is the TF-IDF vector for the corresponding document. Each row is the TF-IDF vector of a token across the documents of the corpus. $m$ is the number of tokens in the vocabulary and $n$ is the number of documents in the corpus.

Let $A$ be written in terms of its rows:
\begin{equation}
    A=\begin{bmatrix}
        r\_{1} \newline
        r\_{2} \newline
        \vdots \newline
        r\_{m}
    \end{bmatrix}
\end{equation}
Then:
\begin{equation}
    A^{T}=\begin{bmatrix}
        r\_{1}^{T} & r\_{2}^{T} & \dotso & r\_{n}^{T}
    \end{bmatrix}
\end{equation}
and
\begin{equation}
    AA^{T}=\begin{bmatrix}
        r\_{1}r\_{1}^{T} & r\_{1}r\_{2}^{T} & \dotso & r\_{1}r\_{m}^{T} \newline
        r\_{2}r\_{1}^{T} & r\_{2}r\_{2}^{T} & \dotso & r\_{2}r\_{m}^{T} \newline
        \vdots & \vdots & \vdots & \vdots \newline
        r\_{m}r\_{1}^{T} & r\_{m}r\_{2}^{T} & \dotso & r\_{m}r\_{m}^{T} \newline
    \end{bmatrix}
\end{equation}
What is the meaning of a column of the matrix $AA^{T}$? The $i^{th}$ column is a measure of the correlation between $r\_{i}$ and the other rows of $A$. Each $r\_{i}$ corresponds to a token in the vocabulary. It is the TF-IDF vector of the token across the documents in the corpus. It is a measure of the token's importance related with the topic of the documents. If the tokens are similar in meaning to each other, then TF-IDF vectors of them across the documents are expected to be similar to each other. What is the function of $AA^{T}$ when it is multiplied from left with a column vector $x$, i.e. $\left(AA^{T}\right)x$? What kind of a transformation does $AA^{T}$ apply to $x$? This multiplication takes the linear combination of the columns of $AA^{T}$. The product vector has entries which are linear combinations of each token's measures for the correlations with the other tokens. So, the $i^{th}$ entry is a number which is a weighted sum of pairwise meaning similarities of the $i^{th}$ token with other tokens. So, this product vector is related with the meanings of the tokens. The meanings of the tokens are related with the topic of the document the tokens are in. What can be said about an eigenvector of $AA^{T}$? Let this eigenvector be denoted by $u$. Then, it satisfies the following:
\begin{equation}
    \left(AA^{T}\right)u=\lambda\_{u} u
\end{equation}
where $\lambda\_{u}$ is the corresponding eigenvalue. The eigenvector is such a special vector that when it is left multiplied by $AA^{T}$, a multiple of it is obtained. So, it should be a fundamental vector related with the pairwise meaning relations of the tokens across the documents of the corpus. The columns of the $U$ matrix in the SVD factorization for $A$ are these $u$ vectors. The columns of $U$ are also known to be orthonormal. Hence, the $u$ vectors are basis vectors for the vector space $R^{m}$. They are really fundamental vectors for the token-topic relations across the documents. Each of them represents a certain dimension of the token-topic relations across the documents of the corpus.

After examining $AA^{T}$, it is the turn of $A^{T}A$. Let $A$ be expressed in terms of its columns:
\begin{equation}
    A=\begin{bmatrix}
        c\_{1} & c\_{2} & \dotso & c\_{n}
    \end{bmatrix}
\end{equation}
Then:
\begin{equation}
    A^{T}=\begin{bmatrix}
        c\_{1}^{T} \newline
        c\_{2}^{T} \newline
        \vdots \newline
        c\_{n}^{T}
    \end{bmatrix}
\end{equation}
and
\begin{equation}
    A^{T}A=\begin{bmatrix}
        c\_{1}^{T}c\_{1} & c\_{1}^{T}c\_{2} & \dotso & c\_{1}^{T}c\_{n} \newline
        c\_{2}^{T}c\_{1} & c\_{2}^{T}c\_{2} & \dotso & c\_{2}^{T}c\_{n} \newline
        \vdots & \vdots & \vdots & \vdots \newline
        c\_{n}^{T}c\_{1} & c\_{n}^{T}c\_{2} & \dotso & c\_{n}^{T}c\_{n}
    \end{bmatrix}
\end{equation}
The $i^{th}$ column of $A^{T}A$ is the measure of the correlation of $c\_{i}$ with the other columns of $A$. $c\_{i}$ is the TF-IDF vector for the $i^{th}$ document. Hence, $i^{th}$ column of $A^{T}A$ is a measure of the pairwise meaning similarity between documents of the corpus. Compared to the $AA^{T}$ case when token-topic relations are in the columns, there are the document-topic relations in the columns of $A^{T}A$. When a column vector $x$ is left multiplied with $A^{T}A$, the resulting column vector entries are linear combinations of the pairwise topic relations of each document with the rest. The product is related with the topics of the documents. As to the eigenvectors $v$ of $A^{T}A$, they satisfy the following relation:
\begin{equation}
    \left(A^{T}A\right)v=\lambda\_{v}v
\end{equation}
When eigenvectors $v$ are multiplied from left by $A^{T}A$, the product is a multiple of $v$. Hence, eigenvectors $v$ give the sense of being a set of special vectors related with the meaning across the documents of the corpus. These $v$ vectors are known to be the columns of $V$ in the SVD factorization of $A$. These columns are also orthonormal, which means that they form a basis for the vector space $R^{n}$. Hence, each $v$ should be representing a dimension of the pairwise meaning, i.e. topic, relations across the documents of the corpus.

Multiplying from right both sides of the equation (\ref{SVD}) with $V$ and using the orthonormality property of the columns of $V$ which is $V^{T}V=I\_{n}$, the following equality is obtained:
\begin{equation}
    AV=U\Sigma
\end{equation}
This equation implies the following:
\begin{equation}
    Av\_{j}=\sigma\_{j}u\_{j}
\end{equation}
$A$ is the token-document matrix. $v\_{j}$ is the document-topic vector. $u\_{j}$ is the token-topic vector.

The SVD factorization is not used in its full form. Truncation is often applied to the factorization by taking only a certain number of $v$ and $u$ in the factorization. This number is determined according to the magnitude of singular values. If the first $p$ of the singular values are taken into account, then the truncated $U$ will be of dimension $m\times p$, the truncated $\Sigma$ will be of dimension $p\times p$ and the truncated $V$ will be of dimension $n \times p$. The number of hidden topics will be $p$.
## Conclusion
The hidden topics in a corpus of documents can be discovered to an extent by using the SVD factorization of the token-document matrix of the corpus. It has been shown why this discovery is possible.
## References
Linear Algebra and Its Applications, Gilbert Strang.

Natural Language Processing In Action, Hobson Lane, Cole Howard, Hannes Max Hapke.
