---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: An Analytical Solution For The Problem Of One-To-One Mapping Between A Binary Image And A Filter
--- 
## Introduction 

In this article, an analytical solution is made for the problem of one-to-one 
mapping between a binary image and a filter. This problem was solved by means 
of gradient-based optimization. The solution with optimization is given in 
<a href="#numerical">[1]</a>. Let a summary of the problem be given. There is a 
binary image. The black pixels are represented by $-1$ whereas the white pixels 
are denoted by $1$. The image is divided into $m\times n$ blocks. The aim is to 
find a filter of the same size as the blocks. The inner product of the filter 
with a block should yield a number which is unique to the block. So, a one-to-
one mapping between an image and the filter is to be found. 

## The Necessity Of An Analytical Solution 
A binary image of dimensions $m \times n$ can have $2^{m\times n}$ different 
arrangements of pixel values. So, there can be $2^{m\times n}$ different images. 
The gradient-based method needs to build a matrix with a row number given as 
follows: 
\begin{equation} 
\left ( 2^{mn}-1 \right ) + \left ( 2^{mn}-2 \right ) + 
\left ( 2^{mn}-3 \right ) + \ldots + 3 + 2 + 1 = 
\frac{\left ( 2^{mn} -1 \right ) \left ( 2^{mn} - 1 + 1 \right )}{2}=
\frac{ 2^{mn} \left ( 2^{mn} - 1 \right )}{2}
\end{equation} 
Each row of the matrix is a vector of $mn$ components. On a computer with a 
single core of 1.60 GHz, the optimization becomes too slow for $mn \geq 11$. 
$mn=12$ yields $8386560$ rows. $mn=16$ yields $2147450880$ rows. So, an 
analytical solution is necessary. 

## The Analytical Solution 
The optimization results are first to be summarized. They are going to be 
examined during the analytical solution. The filters are going to be shown in 
row vector forms instead of matrix forms. For $mn=5$ and an initial random filter 
\begin{equation} 
\begin{bmatrix} 
0.94305611 & 0.51132755 & 0.97624371 & 0.08083602 & 0.60735583
\end{bmatrix}, 
\end{equation} 
the final random filter is 
\begin{equation} 
\begin{bmatrix} 
-1.67258483 & -0.83371858 & -0.41564267 & -0.20954087 & -0.10139561
\end{bmatrix} 
\label{mn5OptRes}
\end{equation} 
There is a pattern in the final filter found by the weighted gradient-descent 
optimization with momentum. The ratio of the consecutive components from left 
to right is approximately $2$. For $mn=6$ and an initial random filter 
\begin{equation} 
\begin{bmatrix} 
0.94305611 & 0.51132755 & 0.97624371 & 0.08083602 & 0.60735583 & 0.37648658
\end{bmatrix}, 
\end{equation} 
the final random filter is 
\begin{equation} 
\begin{bmatrix} 
-3.37984328 & -1.69863671 & -0.83552461 & -0.40841674 & -0.20248713 & 
-0.10095605
\end{bmatrix}
\label{mn6OptRes}
\end{equation}
The ratio of the consecutive components from left to right is again 
approximately $2$. For $mn=7$ and an initial random filter 
\begin{equation} 
\begin{bmatrix} 
0.94305611 & 0.51132755 & 0.97624371 & 0.08083602 & 0.60735583 & 0.37648658 & 
0.80190121
\end{bmatrix}, 
\end{equation} 
the final random filter is 
\begin{equation} 
\begin{bmatrix} 
-6.74899202 & -3.3842036 & -1.68931222 & -0.83778554 & -0.41793618 & -0.21290442 
& -0.10454221
\end{bmatrix}
\label{mn7OptRes}
\end{equation}
The ratio of the consecutive components from left to right is again 
approximately $2$. For $mn=8$ and an initial random filter 
\begin{equation} 
\begin{bmatrix} 
0.94305611 & 0.51132755 & 0.97624371 & 0.08083602 & 0.60735583 & 0.37648658 & 
0.80190121 & 0.17452782
\end{bmatrix}, 
\end{equation} 
the final random filter is 
\begin{equation} 
\begin{bmatrix} 
13.33272769 & -6.65447224 & -3.32388674 & -1.67464761 & -0.82252621 & 
-0.40711857 & -0.20502906 & -0.10168881
\end{bmatrix}
\label{mn8OptRes}
\end{equation}
The ratio of the consecutive components from left to right is again 
approximately $2$. For $mn=9$ and an initial random filter 
\begin{equation} 
\begin{bmatrix} 
0.94305611 & 0.51132755 & 0.97624371 & 0.08083602 & 0.60735583 & 0.37648658 & 
0.80190121 & 0.17452782 & 0.87163527
\end{bmatrix}, 
\end{equation} 
the final random filter is 
\begin{equation} 
\begin{bmatrix} 
-26.33596196 & -13.17132984 & -6.58279745 & -3.27809463 & -1.63547214 & 
-0.81862719 & -0.41314859 & -0.20197537 & -0.10000619
\end{bmatrix}
\label{mn9OptRes}
\end{equation}
The ratio of the consecutive components from left to right is again 
approximately $2$. For $mn=10$ and an initial random filter 
\begin{equation} 
\begin{bmatrix} 
0.94305611 & 0.51132755 & 0.97624371 & 0.08083602 & 0.60735583 & 0.37648658 & 
0.80190121 & 0.17452782 & 0.87163527 & 0.5439414
\end{bmatrix}, 
\end{equation} 
the final random filter is 
\begin{equation} 
\begin{bmatrix} 
-52.50742635 & -26.23634966 & -13.14157011 & -6.60822192 & -3.24059522 & 
-1.62076676 & -0.81094173 & -0.40274117 & -0.20011447 &-0.10009161
\end{bmatrix}
\label{mn10OptRes}
\end{equation}
The ratio of the consecutive components from left to right is again 
approximately $2$. 

Let an image with $mn=2$ be examined first. Let the filter which is to generate 
unique identities be given by 
\begin{equation} 
\begin{bmatrix} 
f_{1} & f_{2}
\end{bmatrix} 
\end{equation}
There can be four different images which are written in their row vector forms 
as follows: 
\begin{gather} 
\begin{bmatrix} 
-1 & -1
\end{bmatrix} \label{img1} \newline
\begin{bmatrix} 
-1 & 1
\end{bmatrix} \label{img2} \newline 
\begin{bmatrix} 
1 & -1
\end{bmatrix} \label{img3} \newline
\begin{bmatrix} 
1 & 1
\end{bmatrix} \label{img4} \newline
\end{gather}
The inner products of the filter with these images are given by 
\begin{gather} 
-f_{1} - f_{2} \newline
-f_{1} + f_{2} \newline 
f_{1} - f_{2} \newline 
f_{1} + f_{2}
\end{gather} 
The absolute values of the differences between the inner products should be 
greater than the set threshold, $t$, for the generation of unique identities. 
In general, there will be 
\begin{equation} 
2^{mn} \choose 2
\end{equation} 
differences. So, for $mn=2$, there are $6$ conditions to be satisfied:
\begin{gather} 
\left | -2f_{2}\right | > t \label{ineqCond1} \newline 
\left | -2f_{1}\right | > t \label{ineqCond2} \newline 
\left | -2f_{1} - 2f_{2}\right | > t \label{ineqCond3} \newline 
\left | -2f_{1} + 2f_{2}\right | > t \label{ineqCond4} \newline 
\left | -2f_{1}\right | > t \newline 
\left | -2f_{2}\right | > t
\end{gather}
Some of the conditions to be satisfied are the same as each other. The reason is 
that there are some pairs of images one of which is equal to $-1$ times the 
other. The image in the equation \eqref{img1} is $-1$ times the one in the 
equation \eqref{img4}. The image in the equation \eqref{img2} is $-1$ times the 
one in the equation \eqref{img3}. The inequalities to start with are the ones 
involving single components of the filter since they are much more easier to 
analyse. They are the ones in the equations \eqref{ineqCond1} and 
\eqref{ineqCond2}. 
\begin{equation} 
\left | -2f_{2}\right | > t \implies -2f_{2} > t \text{ or } -2f_{2} < -t
\end{equation}
\begin{equation} 
\left | -2f_{1}\right | > t \implies -2f_{1} > t \text{ or } -2f_{1} < -t
\end{equation} 
In all the samples of optimization results, the last components of the 
optimized filters are a little smaller than $-0.1$. The threshold $t$ in these 
optimizations is $0.2$. So, the optimization chooses $-2f_{2} > t$ as the 
solution. Additionally, in all the samples of optimization results, the filter 
components are of the same sign. Then, the optimization chooses $-2f_{1} > t$ as 
the solution. There are two conditions left to be satisfied. One of them is  
\begin{equation} 
\left | -2f_{1} - 2f_{2} \right | > t \implies -2f_{1} - 2f_{2} > t \text{ or } 
-2f_{1} - 2f_{2} < -t \label{ineqCond5}
\end{equation} 
The choices of the optimization as $-2f_{1} > t$ and $-2f_{2} > t$ satisfy 
the first possibility which is $-2f_{1} - 2f_{2} > t$. With $-2f_{1} > t$ and 
$-2f_{2} > t$, $-2f_{1} - 2f_{2} < -t$  can never be satisfied. The inequality 
in the equation \eqref{ineqCond4} is expanded as follows: 
\begin{equation} 
\left | -2f_{1} + 2f_{2}\right | > t \implies -2f_{1} + 2f_{2} > t \text{ or } 
-2f_{1} + 2f_{2} < -t \label{ineqCond6}
\end{equation}
Let the inequality $-2f_{1} + 2f_{2} > t$ be worked on: 
\begin{gather} 
-2f_{1} + 2f_{2} > t \implies 2f_{2} > t+2f_{1} \implies 
f_{2} > \frac{t}{2}+f_{1}
\end{gather} 
Let the resulting inequality be combined with $-2f_{1} > t$ and $-2f_{2} > t$: 
\begin{equation}
\left. 
\begin{array}{l} 
-2f_{1} > t \newline 
-2f_{2} > t \newline 
f_{2} > \frac{t}{2}+f_{1}
\end{array}
\right \rbrace \implies 
\left. 
\begin{array}{l} 
f_{1}<-\frac{t}{2} \newline 
f_{2}<-\frac{t}{2} \newline 
f_{2} > \frac{t}{2}+f_{1}
\end{array}
\right \rbrace \implies 
\begin{array}{l} 
f_{1}<-\frac{t}{2} \newline 
\frac{t}{2}+f_{1} < f_{2} < -\frac{t}{2}
\end{array}
\end{equation} 
So, an analytical solution for $mn=2$ is given as follows:
\begin{equation} 
\begin{array}{l} 
f_{1}<-t \newline 
\frac{t}{2}+f_{1} < f_{2} < -\frac{t}{2}
\end{array} 
\label{soln1}
\end{equation} 
Some samples from the solution set given in the equation \eqref{soln1} are as 
follows: 
\begin{gather} 
f_{1}=-1.1t, \ -0.6t < f_{2} < -0.5t \newline 
f_{1}=-2.0t, \ -1.5t < f_{2} < -0.5t \newline 
f_{1}=-3.0t, \ -2.5t < f_{2} < -0.5t
\end{gather}
Let the inequality $-2f_{1} + 2f_{2} > t$ be worked on in another way: 
\begin{gather} 
-2f_{1} + 2f_{2} > t \implies -2f_{1} > t-2f_{2} \implies 
f_{1} < -\frac{t}{2}+f_{2}
\end{gather} 
Let the resulting inequality be combined with $-2f_{1} > t$ and $-2f_{2} > t$: 
\begin{equation} 
\left. 
\begin{array}{l}
-2f_{1} > t \newline 
-2f_{2} > t \newline 
f_{1} < -\frac{t}{2}+f_{2} 
\end{array}
\right \rbrace \implies 
\left. 
\begin{array}{l}
f_{1} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2}+f_{2} 
\end{array}
\right \rbrace \implies 
\begin{array}{l}
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2}+f_{2} 
\end{array}
\end{equation}
So, another analytical solution for $mn=2$ is given as follows: 
\begin{equation}
\begin{array}{l}
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2}+f_{2} 
\end{array} 
\label{soln2}
\end{equation}
Some samples from the solution set given in the equation \eqref{soln2} are as 
follows:  
\begin{gather}
f_{2}=-0.55t, \ f_{1} < -1.05t \newline 
f_{2}=-1.0t, \ f_{1} < -1.5t \newline 
f_{2}=-1.5t, \ f_{1} < -2.0t 
\end{gather} 
Let the second inequality in the equation \eqref{ineqCond6} be worked on: 
\begin{equation} 
-2f_{1}+2f_{2}<-t \implies 2f_{2} < 2f_{1}-t \implies f_{2} < f_{1}-\frac{t}{2}
\end{equation}
Let the resulting inequality be combined with $-2f_{1} > t$ and $-2f_{2} > t$: 
\begin{equation}
\left. 
\begin{array}{l} 
-2f_{1} > t \newline 
-2f_{2} > t \newline 
f_{2} < f_{1}-\frac{t}{2}
\end{array}
\right \rbrace \implies 
\left. 
\begin{array}{l} 
f_{1}< -\frac{t}{2} \newline 
f_{2}< -\frac{t}{2} \newline 
f_{2} < f_{1}-\frac{t}{2}
\end{array}
\right \rbrace \implies 
\begin{array}{l} 
f_{1}< -\frac{t}{2} \newline 
f_{2} < f_{1}-\frac{t}{2}
\end{array}
\end{equation}
So, another analytical solution for $mn=2$ is given as follows: 
\begin{equation}
\begin{array}{l} 
f_{1}< -\frac{t}{2} \newline 
f_{2} < f_{1}-\frac{t}{2}
\end{array}
\end{equation} 
In fact, this solution is the solution in the equation \eqref{soln2} with 
$f_{1}$ and $f_{2}$ exchanged. Let the inequality $-2f_{1}+2f_{2}<-t$ be solved 
in another way: 
\begin{equation} 
-2f_{1}+2f_{2}<-t \implies -2f_{1} < -t-2f_{2} \implies 
f_{1} > \frac{t}{2}+f_{2}
\end{equation} 
Let the resulting inequality be combined with $-2f_{1} > t$ and $-2f_{2} > t$: 
\begin{equation}
\left. 
\begin{array}{l} 
-2f_{1} > t \newline 
-2f_{2} > t \newline 
f_{1} > \frac{t}{2}+f_{2}
\end{array}
\right \rbrace \implies 
\left. 
\begin{array}{l} 
f_{1}< -\frac{t}{2} \newline 
f_{2}< -\frac{t}{2} \newline 
f_{1} > \frac{t}{2}+f_{2}
\end{array}
\right \rbrace \implies 
\begin{array}{l} 
f_{2}< -\frac{t}{2} \newline 
-\frac{t}{2} > f_{1} > \frac{t}{2}+f_{2}
\end{array}
\end{equation} 
So, another analytical solution for $mn=2$ is given as follows: 
\begin{equation}
\begin{array}{l} 
f_{2}< -\frac{t}{2} \newline 
-\frac{t}{2} > f_{1} > \frac{t}{2}+f_{2} 
\end{array}
\end{equation}
And this solution is the solution in the equation \eqref{soln1} with $f_{1}$ and 
$f_{2}$ exchanged. 

Other analytical solutions can be searched for by starting with the following 
solutions:
\begin{gather} 
2f_{2}  > t \newline 
2f_{1}  > t
\end{gather} 
Now, let the case for which $mn=3$ be dealt with. The filter is given by 
\begin{equation} 
\begin{bmatrix} 
f_{1} & f_{2} & f_{3}
\end{bmatrix}
\end{equation} 
There can be $8$ different images: 
\begin{equation} 
\begin{array}{c} 
\begin{bmatrix} 
-1 & -1 & -1 
\end{bmatrix} \newline  
\begin{bmatrix} 
-1 & -1 & 1 
\end{bmatrix} \newline  
\begin{bmatrix} 
-1 & 1 & -1 
\end{bmatrix} \newline  
\begin{bmatrix} 
-1 & 1 & 1 
\end{bmatrix} \newline 
\begin{bmatrix} 
1 & -1 & -1 
\end{bmatrix} \newline  
\begin{bmatrix} 
1 & -1 & 1 
\end{bmatrix} \newline  
\begin{bmatrix} 
1 & 1 & -1 
\end{bmatrix} \newline  
\begin{bmatrix} 
1 & 1 & 1 
\end{bmatrix}
\end{array}  
\end{equation} 
The inner product of the filter with these images are as follows: 
\begin{equation} 
\begin{array}{c} 
-f_{1}-f_{2}-f_{3} 
\newline  
-f_{1}-f_{2}+f_{3} 
\newline  
-f_{1}+f_{2}-f_{3} 
\newline  
-f_{1}+f_{2}+f_{3} 
\newline 
f_{1}-f_{2}-f_{3} 
\newline  
f_{1}-f_{2}+f_{3}
\newline  
f_{1}+f_{2}-f_{3}
\newline  
f_{1}+f_{2}+f_{3}
\end{array}  
\label{innerProds3}
\end{equation} 
The differences between the inner products can be found by subtracting from each 
inner product the ones under it. For example, the first row of differences in 
the equation \eqref{differences} is obtained by subtracting from the first inner 
product the ones underneath it. The second row is obtained by subtracting from 
the second inner product the ones below it. In this way, the differences in the 
equation \eqref{differences} are gotten.
\begin{equation} 
\begin{array}{|c|c|c|c|c|c|c} 
-2f_{3} & -2f_{2} & -2f_{2}-2f_{3} & -2f_{1} & -2f_{1}-2f_{3} & -2f_{1}-2f_{2} & 
-2f_{1}-2f_{2}-2f_{3} \newline 
-2f_{2}+2f_{3} & -2f_{2} & -2f_{1}+2f_{3} & -2f_{1} & -2f_{1}-2f_{2}+2f_{3} & 
-2f_{1}-2f_{2} & \newline 
-2f_{3} & -2f_{1}+2f_{2} & -2f_{1}+2f_{2}-2f_{3} & -2f_{1} & -2f_{1}-2f_{3} & & 
& \newline 
-2f_{1}+2f_{2}+2f_{3} & -2f_{1}+2f_{2} & -2f_{1}+2f_{3} & -2f_{1} & & & & 
\newline 
-2f_{3} & -2f_{2} & -2f_{2}-2f_{3} & & & & & \newline 
-2f_{2}+2f_{3} & -2f_{2} & & & & & & \newline 
-2f_{3}
\end{array} 
\end{equation} 
There are multiple instances of the same difference. Let these multiple 
occurrences be removed to obtain the following minimal and complete set of 
differences: 
\begin{equation} 
\begin{array}{|c|c|c|c|c|c|c} 
-2f_{3} & -2f_{2} & -2f_{2}-2f_{3} & -2f_{1} & -2f_{1}-2f_{3} & -2f_{1}-2f_{2} & 
-2f_{1}-2f_{2}-2f_{3} \newline 
-2f_{2}+2f_{3} &  & -2f_{1}+2f_{3} &  & -2f_{1}-2f_{2}+2f_{3} & 
 & \newline 
 & -2f_{1}+2f_{2} & -2f_{1}+2f_{2}-2f_{3} &  &  & & 
& \newline 
-2f_{1}+2f_{2}+2f_{3} &  &  &  & & & &
\end{array} 
\label{differences}
\end{equation} 
The set is minimal in the sense that no difference is equal to $-1$ times any 
other difference and all differences are unique. The set is complete in the 
sense that all possible unique differences are included. Using these properties, 
the set of differences can be written by heart: 
\begin{equation} 
\begin{array}{|c|c|c|c|} 
-2f_{1} & -2f_{1}-2f_{2} & -2f_{2}-2f_{3} & -2f_{1}-2f_{2}-
2f_{3} \newline 
-2f_{2} & -2f_{1}+2f_{2} & -2f_{2}+2f_{3} & 
-2f_{1}-2f_{2}+2f_{3} \newline 
-2f_{3} & -2f_{1}+2f_{3} & & -2f_{1}+2f_{2}-2f_{3} \newline 
& -2f_{1}-2f_{3} & & -2f_{1}+2f_{2}+2f_{3}
\end{array} 
\label{diff3}
\end{equation}
Let the set of differences for $mn=4$ be written by heart using the mentioned 
properties: 
\begin{equation} 
\begin{array}{|c|c|c|c|c|c|c|c|c|}
-2f_{1} & -2f_{1}-2f_{2} & -2f_{2}-2f_{3} & -2f_{3}-2f_{4} & 
-2f_{1}-2f_{2}-2f_{3} & -2f_{1}-2f_{2}-2f_{4} & -2f_{1}-2f_{3}-2f_{4} & 
-2f_{2}-2f_{3}-2f_{4} & -2f_{1}-2f_{2}-2f_{3}-2f_{4} \newline
-2f_{2} & -2f_{1}+2f_{2} & -2f_{2}+2f_{3} & -2f_{3}+2f_{4} & 
-2f_{1}-2f_{2}+2f_{3} & -2f_{1}-2f_{2}+2f_{4} & -2f_{1}-2f_{3}+2f_{4} & 
-2f_{2}-2f_{3}+2f_{4} & -2f_{1}-2f_{2}-2f_{3}+2f_{4} \newline
-2f_{3} & -2f_{1}-2f_{3} & -2f_{2}-2f_{4} & & -2f_{1}+2f_{2}-2f_{3} & 
-2f_{1}+2f_{2}-2f_{4} & -2f_{1}+2f_{3}-2f_{4} & -2f_{2}+2f_{3}-2f_{4} & 
-2f_{1}-2f_{2}+2f_{3}-2f_{4} \newline
-2f_{4} & -2f_{1}+2f_{3} & -2f_{2}+2f_{4} & & -2f_{1}+2f_{2}+2f_{3} & 
-2f_{1}+2f_{2}+2f_{4} & -2f_{1}+2f_{3}+2f_{4} & -2f_{2}+2f_{3}+2f_{4} & 
-2f_{1}-2f_{2}+2f_{3}+2f_{4} \newline 
 & -2f_{1}-2f_{4} & & & & & & & -2f_{1}+2f_{2}-2f_{3}-2f_{4}  \newline 
 & -2f_{1}+2f_{4} & & & & & & & -2f_{1}+2f_{2}-2f_{3}+2f_{4} \newline 
 & & & & & & & & -2f_{1}+2f_{2}+2f_{3}-2f_{4} \newline
 & & & & & & & & -2f_{1}+2f_{2}+2f_{3}+2f_{4}
\end{array} 
\label{diff4}
\end{equation}
Now, let the optimization problem be analytically solved for the differences 
given in the equation \eqref{diff3}. First, the inequalities with only one 
filter coefficient are to be dealt with. This is the first level of the 
solution. The solution is made as follows:
\begin{gather} 
\left |-2f_{1} \right | > t \implies f_{1} < -\frac{t}{2} \text{ or } 
f_{1} > \frac{t}{2} \newline 
\left |-2f_{2} \right | > t \implies f_{2} < -\frac{t}{2} \text{ or } 
f_{2} > \frac{t}{2} \newline 
\left |-2f_{3} \right | > t \implies f_{3} < -\frac{t}{2} \text{ or } 
f_{3} > \frac{t}{2} 
\end{gather} 
The gradient based optimization chooses the following solutions: 
\begin{gather} 
f_{1} < -\frac{t}{2} \label{mn3Soln1} \newline
f_{2} < -\frac{t}{2} \label{mn3Soln2} \newline
f_{3} < -\frac{t}{2} \label{mn3Soln3}
\end{gather} 
Let the analytical solution be continued with this choice. After the first level 
of the solution, the second level is incorporating the information coming from 
the inequalities with two filter coefficients into the first-level solution. 
The inequality to be dealt with is 
\begin{equation} 
\left | -2f_{1} - 2f_{2} \right | > t
\end{equation}
It implies the following: 
\begin{equation} 
-2f_{1}-2f_{2} > t \text{ and } -2f_{1}-2f_{2}<-t
\end{equation} 
It can be easily observed that the solutions in the equations \eqref{mn3Soln1}, 
\eqref{mn3Soln2} and \eqref{mn3Soln3} satisfy $-2f_{1}-2f_{2}<-t$. Obviously, 
they do not satisfy the opposite inequality $-2f_{1}-2f_{2} > t$. The next 
inequality to be considered in the equation \eqref{diff3} is $\left | -2f_{1} + 
2 f_{2} \right | > t$. 
\begin{equation} 
\left | -2f_{1} + 2 f_{2} \right | > t \implies -2f_{1}+2f_{2} > t \text{ or } 
-2f_{1}+2f_{2} < -t
\end{equation} 
Let it be assumed that $ -2 f_{1} + 2 f_{2} > t $ is to be satisfied by the 
analytical solution. Then: 
\begin{equation} 
-2 f_{1} + 2 f_{2} > t \implies 2 f_{2} > t + 2 f_{1} \implies f_{2} > 
\frac{t}{2} + f_{1} \implies 
\begin{cases} 
f_{1} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} \newline 
f_{2} > \frac{t}{2} + f_{1}
\end{cases} \implies 
\begin{cases} 
f_{1} < -t \newline 
f_{1} + \frac{t}{2} < f_{2} < -\frac{t}{2}
\end{cases}
\end{equation} 
is a solution that is obtained with the inclusion of 
$-2f_{1}+2f_{2} > t$. Another solution can be obtained as follows: 
\begin{equation} 
-2f_{1}+2f_{2} > t \implies -2f_{1} > t-2f_{2} \implies f_{1} < -\frac{t}{2}+
f_{2} \implies 
\begin{cases} 
f_{1}<-\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2}+f_{2}
\end{cases} \implies 
\begin{cases} 
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2}+f_{2}
\end{cases} 
\end{equation} 
is another solution corresponding to the inclusion of 
$-2f_{1}+2f_{2} > t$. Let the remaining four inequalities be processed. They 
are as follows: 
\begin{gather} 
\left | -2f_{1}-2f_{3} \right | > t \newline 
\left | -2f_{2}-2f_{3} \right | > t \newline 
\left | -2f_{1}+2f_{3} \right | > t \newline 
\left | -2f_{2}+2f_{3} \right | > t
\end{gather} 
The solutions in the equations \eqref{mn3Soln1}, \eqref{mn3Soln2} and 
\eqref{mn3Soln3} satisfy $-2f_{1}-2f_{3} < -t$ and $-2f_{2}-2f_{3} < -t$ coming 
from $\left | -2f_{1}-2f_{3} \right | > t$ and 
$\left | -2f_{2}-2f_{3} \right | > t$ respectively. 
$\left | -2f_{1}+2f_{3} \right | > t$ and $\left | -2f_{2}+2f_{3} \right | > t$ 
can be solved in a way similar to the solution of 
$\left | -2f_{1}+2f_{2} \right | > t$. Therefore, the following are the possible 
solutions obtained by the inclusion of the inequalities $-2f_{1}+2f_{2} > t$, 
$-2f_{1}+2f_{3} > t$ and $ -2f_{2}+2f_{3}  > t$: 
\begin{gather} 
-2f_{1}+2f_{2} > t \implies 
\begin{cases} 
f_{1} < -t \newline 
\frac{t}{2}+f_{1} < f_{2} < -\frac{t}{2}
\end{cases} 
\text{ or } 
\begin{cases} 
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2} + f_{2}
\end{cases} \label{mn3Level21} \newline 
-2f_{1}+2f_{3} > t \implies 
\begin{cases} 
f_{1} < -t \newline 
\frac{t}{2}+f_{1} < f_{3} < -\frac{t}{2}
\end{cases} 
\text{ or } 
\begin{cases} 
f_{3} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2} + f_{3}
\end{cases} \label{mn3Level22} \newline 
-2f_{2}+2f_{3} > t \implies 
\begin{cases} 
f_{2} < -t \newline 
\frac{t}{2}+f_{2} < f_{3} < -\frac{t}{2}
\end{cases} 
\text{ or } 
\begin{cases} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} + f_{3}
\end{cases} \label{mn3Level23}
\end{gather}
It should be remembered that there are possibly 10 more solutions that can be 
obtained by taking into account the forms $-2f_{1}+2f_{2} < -t$, 
$-2f_{1}+2f_{3} < -t$ and $-2f_{2}+2f_{3} < -t$. From 8 possible combinations of 
the solutions in the equations \eqref{mn3Level21}, \eqref{mn3Level22} and 
\eqref{mn3Level23}, let the following one be chosen: 
\begin{equation} 
\begin{array}{c}
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2}+f_{2}
\end{array} 
\ \text{ and } \ 
\begin{array}{c}
f_{3} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2}+f_{3}
\end{array} 
\ \text{ and } \ 
\begin{array}{c}
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2}+f_{3}
\end{array} 
\end{equation} 
This combination yields the following second-level solution: 
\begin{equation} 
\begin{array}{c} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2}
\end{array} \label{mn3SecondLevel1}
\end{equation}
Another combination is as follows: 
\begin{equation} 
\begin{array}{c} 
f_{1} < -t \newline 
\frac{t}{2}+f_{1} < f_{2} < -\frac{t}{2}
\end{array} 
\ \text{ and } \ 
\begin{array}{c} 
f_{1} < -t \newline 
\frac{t}{2}+f_{1} < f_{3} < -\frac{t}{2}
\end{array} 
\ \text{ and } \ 
\begin{array}{c} 
f_{2} < -t \newline 
\frac{t}{2}+f_{2} < f_{3} < -\frac{t}{2}
\end{array} 
\end{equation}
The inequalities $f_{1} < -t$, $f_{2}<-t$ and 
$\frac{t}{2}+f_{1} < f_{2} < -\frac{t}{2}$ imply $f_{1} < -\frac{3t}{2}$. Therefore, this combination yields the following second-level solution: 
\begin{equation} 
\begin{array}{c}
f_{1} < -\frac{3t}{2} \newline 
\frac{t}{2}+f_{1} < f_{2} < -t \newline 
\frac{t}{2}+f_{2} < f_{3} < -\frac{t}{2}
\end{array} \label{mn3SecondLevel2}
\end{equation} 
Other combinations can be handled similarly to obtain other second-level 
solutions. 

As the third level of the analytical solution, the inequalities with three 
filter coefficients are processed to update the second-level solutions. Let the 
second level solution to be updated be chosen from the ones in the equations 
\eqref{mn3SecondLevel1} and \eqref{mn3SecondLevel2} as 
\begin{equation} 
\begin{array}{c} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2}
\end{array} 
\end{equation}
This solution satisfies $-2f_{1}-2f_{2}-2f_{3} < -t$ which is an implication of 
$\left | -2f_{1}-2f_{2}-2f_{3} \right | > t$. The next inequality with all the 
filter coefficients is as follows with its implications: 
\begin{equation} 
\left | -2f_{1}-2f_{2}+2f_{3} \right | > t \implies -2f_{1}-2f_{2}+2f_{3} > t 
\text{ or } -2f_{1}-2f_{2}+2f_{3} < -t
\end{equation} 
First, let $-2f_{1} -2f_{2}+2f_{3} > t$ be combined with the second-level 
solution. Let the combination be made by using the implied constraint on $f_{1}$: 
\begin{equation} 
-2f_{1} -2f_{2}+2f_{3} > t \implies -2f_{1} > t+2f_{2}-2f_{3} \implies 
f_{1} < -\frac{t}{2}-f_{2}+f_{3}
\end{equation} 
Let this constraint be combined with the second-level solution: 
\begin{equation} 
\left.
\begin{array}{c}
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2} \newline 
f_{1} < -\frac{t}{2}-f_{2}+f_{3}
\end{array} \right \rbrace \implies 
\begin{array}{c}
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < \min \left ( -\frac{t}{2} + f_{2}, -\frac{t}{2}-f_{2}+f_{3} \right )
\end{array}
\end{equation}
\begin{equation}
f_{2} < -\frac{t}{2}+f_{3} \implies 0 < -\frac{t}{2}-f_{2}+f_{3} \implies 
\min \left ( -\frac{t}{2} + f_{2}, -\frac{t}{2}-f_{2}+f_{3} \right ) = 
-\frac{t}{2} + f_{2}
\end{equation} 
Then, the combination with the second-level solution yields the following: 
\begin{equation} 
\begin{array}{c}
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2}
\end{array} \label{mn3SecondLevelComb1}
\end{equation}
This time, let the combination be made using the constraint on $f_{2}$: 
\begin{equation} 
-2f_{1} -2f_{2}+2f_{3} > t \implies -2f_{2} > t +2f_{1} -2f_{3} \implies 
f_{2} < -\frac{t}{2}-f_{1}+f_{3}
\end{equation}
Let this constraint be combined with the second-level solution: 
\begin{equation} 
\left. 
\begin{array}{c} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2} \newline 
f_{2} < -\frac{t}{2}-f_{1}+f_{3}
\end{array}
\right \rbrace \implies 
\begin{array}{c}
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} +f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2}
\end{array}
\end{equation}
The result is the same as the one in the equation \eqref{mn3SecondLevelComb1}. 
It is the turn of the constraint on $f_{3}$: 
\begin{equation} 
-2f_{1} -2f_{2}+2f_{3} > t \implies 2f_{3} > t +2f_{1}+2f_{2} \implies 
f_{3} > \frac{t}{2}+f_{1}+f_{2}
\end{equation} 
Let this constraint be combined with the second-level solution to produce the 
following: 
\begin{equation} 
\left. 
\begin{array}{c} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2} \newline 
f_{3} > \frac{t}{2}+f_{1}+f_{2}
\end{array} 
\right \rbrace \implies 
\begin{array}{c} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} +f_{3} \newline 
f_{1} < -\frac{t}{2}+f_{2} \text{ and } f_{3} > \frac{t}{2} + f_{1} +f_{2}
\end{array} \label{mn3SecondLevelComb2}
\end{equation} 
Other results can be obtained by combining $-2f_{1}-2f_{2}+2f_{3} < -t$ with the 
chosen second level solution. 

Now, the third inequality with all the filter coefficients is to be processed 
to update one of the results in the equations \eqref{mn3SecondLevelComb1} or 
\eqref{mn3SecondLevelComb2}. This inequality and its implications are as 
follows: 
\begin{equation} 
\left | -2f_{1} +2f_{2}-2f_{3} \right | > t \implies -2f_{1} +2f_{2}-2f_{3} > t 
\text{ or } -2f_{1} +2f_{2}-2f_{3} < -t
\end{equation} 
Let the inequality $-2f_{1}+2f_{2}-2f_{3} > t$ be taken into consideration. Its 
implication for $f_{1}$ is as follows: 
\begin{equation} 
-2f_{1}+2f_{2}-2f_{3} > t \implies -2f_{1} > t-2f_{2}+2f_{3} \implies 
f_{1} < -\frac{t}{2}+f_{2}-f_{3}
\end{equation} 
Let this implication be combined with the result in the equation 
\eqref{mn3SecondLevelComb1}: 
\begin{equation} 
\left .
\begin{array}{c}
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2}+f_{3} \newline 
f_{1} < -\frac{t}{2}+f_{2} \newline 
f_{1} < -\frac{t}{2}+f_{2}-f_{3}
\end{array} 
\right \rbrace \implies 
\begin{array}{c} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2}+f_{3} \newline 
f_{1} < -\frac{t}{2}+f_{2} 
\end{array} \label{mn3SecondLevelComb3}
\end{equation} 
Other results can be obtained by considering the implications for $f_{2}$ or 
$f_{3}$. The inequality $-2f_{1}+2f_{2}-2f_{3}<-t$ can also be processed to 
obtain other results, as well. 

Lastly, the inequality $|-2f_{1}+2f_{2}+2f_{3}| > t$ is to be incorporated into 
the result in the equation \eqref{mn3SecondLevelComb3}. This inequality can be 
decomposed into two inequalities as follows: 
\begin{equation} 
|-2f_{1}+2f_{2}+2f_{3}| > t \implies -2f_{1}+2f_{2}+2f_{3} > t \text{ or } 
-2f_{1}+2f_{2}+2f_{3} < -t
\end{equation} 
Let $-2f_{1}+2f_{2}+2f_{3} > t$ be combined with the result in the equation 
\eqref{mn3SecondLevelComb3}. The implication of this inequality for $f_{1}$ is 
as follows: 
\begin{equation} 
-2f_{1}+2f_{2}+2f_{3} > t \implies -2f_{1} > t - 2f_{2} - 2f_{3} \implies 
f_{1} < -\frac{t}{2}+f_{2}+f_{3}
\end{equation} 
Let this implication be combined with the result in the equation 
\eqref{mn3SecondLevelComb3}: 
\begin{equation} 
\left .
\begin{array}{c} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2}+f_{3} \newline 
f_{1} < -\frac{t}{2}+f_{2} \newline 
f_{1} < -\frac{t}{2}+f_{2}+f_{3}
\end{array} 
\right \rbrace \implies  
\begin{array}{c} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2}+f_{3} \newline 
f_{1} < -\frac{t}{2}+f_{2}+f_{3}
\end{array}
\end{equation} 
So, a solution has been analytically obtained for the optimization problem when 
$mn$ is equal to 3. This solution is rewritten as in the following: 
\begin{equation} 
\begin{array}{c} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2}+f_{3} \newline 
f_{1} < -\frac{t}{2}+f_{2}+f_{3}
\end{array} 
\label{theSolutionmn3}
\end{equation} 
It can be seen from the steps of the solution that there are possibly many more 
solutions other than the one in the equation \eqref{theSolutionmn3}. 

Analytical solutions for $mn=3$, $mn=4$, $mn=5$ and $mn=6$ will be 
systematically derived to form a basis for a general proof of a specific type 
of an analytical solution. First, the solution for $mn=3$ is to be derived. The 
$1^{st}$ level solution for $mn=3$ is as follows: 
\begin{gather} 
f_{1} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} \newline 
f_{3} < -\frac{t}{2} 
\end{gather} 
The $2^{nd}$ level solution is obtained by updating the $1^{st}$ level solution 
with the following inequalities: 
\begin{gather} 
-2f_{1} + 2f_{2} > t \implies f_{1} < -\frac{t}{2} + f_{2}  
\label{sysMn3Lev2-1} \newline 
-2f_{1} - 2f_{2} > t \implies f_{1} < -\frac{t}{2} - f_{2} 
\label{sysMn3Lev2-2} \newline 
-2f_{1} + 2f_{3} > t \implies f_{1} < -\frac{t}{2} + f_{3} 
\label{sysMn3Lev2-3} \newline 
-2f_{1} - 2f_{3} > t \implies f_{1} < -\frac{t}{2} - f_{3} 
\label{sysMn3Lev2-4} \newline 
-2f_{2} + 2f_{3} > t \implies f_{2} < -\frac{t}{2} + f_{3} 
\label{sysMn3Lev2-5} \newline
-2f_{2} - 2f_{3} > t \implies f_{2} < -\frac{t}{2} - f_{3} 
\label{sysMn3Lev2-6}
\end{gather} 
The inequality in the equation \eqref{sysMn3Lev2-1} provides a new upper bound 
for $f_{1}$. The inequality in the equation \eqref{sysMn3Lev2-2} is satisfied 
due to the inequality in the equation \eqref{sysMn3Lev2-1}. The reason is that  
\begin{equation} 
-\frac{t}{2}+f_{2} < -\frac{t}{2}-f_{2}
\end{equation} 
The inequalities in the equations \eqref{sysMn3Lev2-3} and \eqref{sysMn3Lev2-5} 
give new upper bounds for $f_{1}$ and $f_{2}$. The inequalities in the 
equations \eqref{sysMn3Lev2-4} and \eqref{sysMn3Lev2-6} are satisfied due to 
the inequalities in the equations \eqref{sysMn3Lev2-3} and \eqref{sysMn3Lev2-5} 
respectively. The new upper bound for $f_{2}$ is 
\begin{equation}
-\frac{t}{2}+f_{3} 
\end{equation} 
So, the $2^{nd}$ level solution for $f_{2}$ is as follows: 
\begin{equation} 
f_{2} < -\frac{t}{2}+f_{3} 
\label{mn3Lev2Solf2}
\end{equation} 
The upper bounds for $f_{1}$ are 
\begin{equation} 
-\frac{t}{2}+f_{2} \text{ and } -\frac{t}{2}+f_{3} 
\end{equation}
The smallest of them is 
\begin{equation} 
-\frac{t}{2}+f_{2} 
\end{equation} 
due to the relation in the equation \eqref{mn3Lev2Solf2}. The $2^{nd}$ level 
solution for $mn=3$ is concluded to be as follows: 
\begin{gather} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2}+f_{3} \newline 
f_{1} < -\frac{t}{2}+f_{2} 
\end{gather} 
The $3^{rd}$ level solution for $mn=3$ is to be obtained by using the following 
inequalities: 
\begin{gather} 
-2f_{1}+2f_{2}+2f_{3} > t \implies f_{1} < -\frac{t}{2} +f_{2}+f_{3} \newline
-2f_{1}+2f_{2}-2f_{3} > t \implies f_{1} < -\frac{t}{2} +f_{2}-f_{3} \newline
-2f_{1}-2f_{2}+2f_{3} > t \implies f_{1} < -\frac{t}{2} -f_{2}+f_{3} \newline
-2f_{1}-2f_{2}-2f_{3} > t \implies f_{1} < -\frac{t}{2} -f_{2}-f_{3}
\end{gather}
The smallest of the upper bounds for $f_{1}$ in these inequalities is 
\begin{equation}
-\frac{t}{2}+f_{2}+f_{3}
\end{equation} 
So, the update to the $2^{nd}$ level solution is 
\begin{equation} 
f_{1} < -\frac{t}{2}+f_{2}+f_{3}
\end{equation} 
The $3^{rd}$ level solution or the final solution for $mn=3$ is as follows: 
\begin{gather}
f_{3}<-\frac{t}{2} \newline 
f_{2}<-\frac{t}{2} + f_{3} \newline 
f_{1}<-\frac{t}{2}+f_{2}+f_{3} 
\end{gather} 
An analytical solution for $mn=4$ is to be built. The $1^{st}$ level solution 
is as follows: 
\begin{gather} 
f_{1} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} \newline 
f_{3} < -\frac{t}{2} \newline 
f_{4} < -\frac{t}{2}
\end{gather}
The $2^{nd}$ level solution is to be formed from the following inequalities: 
\begin{gather} 
-2f_{3} + 2f_{4} > t \implies f_{3} < -\frac{t}{2} + f_{4} 
\label{sysMn4Lev2-1} \newline
-2f_{2} + 2f_{3} > t \implies f_{2} < -\frac{t}{2} + f_{3} 
\label{sysMn4Lev2-2} \newline 
-2f_{2} + 2f_{4} > t \implies f_{2} < -\frac{t}{2} + f_{4} 
\label{sysMn4Lev2-3} \newline 
-2f_{1} + 2f_{2} > t \implies f_{1} < -\frac{t}{2} + f_{2} 
\label{sysMn4Lev2-4} \newline  
-2f_{1} + 2f_{3} > t \implies f_{1} < -\frac{t}{2} + f_{3} 
\label{sysMn4Lev2-5} \newline 
-2f_{1} + 2f_{4} > t \implies f_{1} < -\frac{t}{2} + f_{4} 
\label{sysMn4Lev2-6}
\end{gather} 
The inequality in the equation \eqref{sysMn4Lev2-1} provides a new upper bound 
for $f_{3}$. This bound is smaller than $-\frac{t}{2}$. So, the $2^{nd}$ level 
solution for $f_{3}$ is 
\begin{equation} 
f_{3} < -\frac{t}{2}+f_{4} \label{mn4Lev2Solf3}
\end{equation} 
The smaller one of the new upper bounds in the equations \eqref{sysMn4Lev2-2} 
and \eqref{sysMn4Lev2-3} is 
\begin{equation} 
-\frac{t}{2}+f_{3} 
\end{equation} 
The reason is the relation in the equation \eqref{mn4Lev2Solf3}. Therefore, the 
$2^{nd}$ level solution for $f_{2}$ is as follows: 
\begin{equation} 
f_{2} < -\frac{t}{2} + f_{3} \label{mn4Lev2Solf2}  
\end{equation} 
The inequalities in the equations \eqref{sysMn4Lev2-4}, \eqref{sysMn4Lev2-5} 
and \eqref{sysMn4Lev2-6} give new upper bounds for $f_{1}$. The smallest of 
them is 
\begin{equation} 
-\frac{t}{2}+f_{2}
\end{equation} 
because of the relations in the equations \eqref{mn4Lev2Solf3} and 
\eqref{mn4Lev2Solf2}. Hence, the $2^{nd}$ level solution for $f_{1}$ is as 
follows: 
\begin{equation} 
f_{1} < -\frac{t}{2} + f_{2}
\end{equation} 
The $2^{nd}$ level solution is summed up in the following: 
\begin{gather} 
f_{4} < -\frac{t}{2} \newline 
f_{3} < -\frac{t}{2} + f_{4} \newline 
f_{2} < -\frac{t}{2} + f_{3} \label{mn4Lev2f2Soln} \newline 
f_{1} < -\frac{t}{2} + f_{2}
\end{gather} 
The $3^{rd}$ level solution is built by updating the second level solution 
using the inequalities which provide new upper bounds. The derivations made so 
far show that the inequalities giving new lower bounds are the ones with left 
sides containing a particular type of linear combination of filter 
coefficients. The first sign of this linear combination is minus and the rest 
are plus. So, the inequalities containing this kind of linear combinations are 
to be worked on: 
\begin{gather} 
-2f_{2}+2f_{3}+2f_{4} > t \implies f_{2} < -\frac{t}{2} + f_{3} + f_{4} 
\label{sysMn4Lev3-1} \newline 
-2f_{1}+2f_{2}+2f_{3} > t \implies f_{1} < -\frac{t}{2} + f_{2} + f_{3} 
\label{sysMn4Lev3-2} \newline 
-2f_{1}+2f_{2}+2f_{4} > t \implies f_{1} < -\frac{t}{2} + f_{2} + f_{4} \label{sysMn4Lev3-3} \newline 
-2f_{1}+2f_{3}+2f_{4} > t \implies f_{1} < -\frac{t}{2} + f_{3} + f_{4} 
\label{sysMn4Lev3-4}
\end{gather} 
The inequality in the equation \eqref{sysMn4Lev3-1} gives $f_{2}$ an upper 
bound which is smaller than the one in the equation \eqref{mn4Lev2f2Soln}. So, 
the $3^{rd}$ level solution for $f_{2}$ is as follows: 
\begin{equation} 
f_{2} < -\frac{t}{2} + f_{3} + f_{4}
\end{equation} 
There are new upper bounds for $f_{1}$ in the equations \eqref{sysMn4Lev3-2}, 
\eqref{sysMn4Lev3-3} and \eqref{sysMn4Lev3-4}. The smallest of them is 
\begin{equation} 
-\frac{t}{2} + f_{2} + f_{3}
\end{equation} 
So, the $3^{rd}$ level solution for $f_{1}$ is 
\begin{equation} 
f_{1} < -\frac{t}{2} + f_{2} + f_{3}
\end{equation} 
The $3^{rd}$ level solution can be completely written now: 
\begin{gather} 
f_{4} < -\frac{t}{2} \newline 
f_{3} < -\frac{t}{2} + f_{4} \newline
f_{2} < -\frac{t}{2}+f_{3} +f_{4} \newline 
f_{1} < -\frac{t}{2}+f_{2}+f_{3}
\end{gather} 
The $4^{th}$ level solution or the final solution is to be found by updating 
the $3^{rd}$ level solution with the following inequality which supply a new 
upper bound: 
\begin{equation} 
-2f_{1}+2f_{2}+2f_{3}+2f_{4} > t \implies f_{1} < -\frac{t}{2} + f_{2}+f_{3}+
f_{4} 
\end{equation} 
So, the $4^{th}$ level or the final solution for $mn=4$ is as follows: 
\begin{gather}
f_{4} < -\frac{t}{2} \newline 
f_{3} < -\frac{t}{2} + f_{4} \newline
f_{2} < -\frac{t}{2}+f_{3} +f_{4} \newline 
f_{1} < -\frac{t}{2} + f_{2}+f_{3}+f_{4}
\end{gather} 
Let an analytical solution for $mn=5$ be constructed. The $1^{st}$ level 
solution is as follows: 
\begin{gather} 
f_{1} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} \newline 
f_{3} < -\frac{t}{2} \newline 
f_{4} < -\frac{t}{2} \label{sysMn5Lev1-4} \newline 
f_{5} < -\frac{t}{2}
\end{gather} 
By updating the $1^{st}$ level solution with inequalities yielding new upper 
bounds, the $2^{nd}$ level solution is to be found. The inequalities are as 
follows: 
\begin{gather} 
-2f_{4} + 2f_{5} > t \implies f_{4} < -\frac{t}{2} + f_{5} 
\label{sysMn5Lev2-1} \newline 
-2f_{3} + 2f_{4} > t \implies f_{3} < -\frac{t}{2} + f_{4} 
\label{sysMn5Lev2-2} \newline
-2f_{3} + 2f_{5} > t \implies f_{3} < -\frac{t}{2} + f_{5} 
\label{sysMn5Lev2-3} \newline 
-2f_{2} + 2f_{3} > t \implies f_{2} < -\frac{t}{2} + f_{3} 
\label{sysMn5Lev2-4} \newline
-2f_{2} + 2f_{4} > t \implies f_{2} < -\frac{t}{2} + f_{4} 
\label{sysMn5Lev2-5} \newline
-2f_{2} + 2f_{5} > t \implies f_{2} < -\frac{t}{2} + f_{5} 
\label{sysMn5Lev2-6} \newline
-2f_{1} + 2f_{2} > t \implies f_{1} < -\frac{t}{2} + f_{2} 
\label{sysMn5Lev2-7} \newline 
-2f_{1} + 2f_{3} > t \implies f_{1} < -\frac{t}{2} + f_{3} 
\label{sysMn5Lev2-8} \newline 
-2f_{1} + 2f_{4} > t \implies f_{1} < -\frac{t}{2} + f_{4} 
\label{sysMn5Lev2-9} \newline 
-2f_{1} + 2f_{5} > t \implies f_{1} < -\frac{t}{2} + f_{5} 
\label{sysMn5Lev2-10}
\end{gather} 
The inequality in the equation \eqref{sysMn5Lev2-1} gives a new upper bound 
for $f_{4}$. This new upper bound is smaller than the one in the equation 
\eqref{sysMn5Lev1-4}. So, the $2^{nd}$ level solution for $f_{4}$ is 
\begin{equation} 
f_{4} < -\frac{t}{2} + f_{5} 
\end{equation} 
Two upper bounds are presented for $f_{3}$ in the equations 
\eqref{sysMn5Lev2-2} and \eqref{sysMn5Lev2-3}. The smallest of them is 
\begin{equation} 
-\frac{t}{2} + f_{4}
\end{equation} 
So, the $2^{nd}$ level solution for $f_{3}$ is 
\begin{equation} 
f_{3} < -\frac{t}{2} + f_{4} 
\end{equation} 
The smallest of the new upper bounds derived in the equations 
\eqref{sysMn5Lev2-4}, \eqref{sysMn5Lev2-5} and \eqref{sysMn5Lev2-6} for $f_{2}$ 
is 
\begin{equation} 
-\frac{t}{2} + f_{3}
\end{equation}
Therefore, the $2^{nd}$ level solution for $f_{2}$ is 
\begin{equation}
f_{2} < -\frac{t}{2} + f_{3} 
\end{equation} 
There are four new upper bounds for $f_{1}$ in the equations 
\eqref{sysMn5Lev2-7}, \eqref{sysMn5Lev2-8}, 
\eqref{sysMn5Lev2-9} and \eqref{sysMn5Lev2-10}. The smallest of them is 
\begin{equation} 
-\frac{t}{2}+f_{2}
\end{equation} 
Hence, the $2^{nd}$ level solution for $f_{1}$ is 
\begin{equation} 
f_{1} < -\frac{t}{2} + f_{2}
\end{equation} 
The $2^{nd}$ level solution for $mn=5$ can be written as follows: 
\begin{gather} 
f_{5} < -\frac{t}{2} \newline 
f_{4} < -\frac{t}{2} + f_{5} \newline 
f_{3} < -\frac{t}{2} + f_{4} \label{Mn5Lev2Solnf3} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline
f_{1} < -\frac{t}{2} + f_{2}
\end{gather} 
The $3^{rd}$ level solution will be constructed by using the following 
inequalities which create new upper bounds: 
\begin{gather} 
-2f_{3}+2f_{4}+2f_{5} > t \implies f_{3} < -\frac{t}{2} + f_{4} + f_{5} 
\label{sysMn5Lev3-1} \newline 
-2f_{2} + 2f_{3} + 2f_{4} > t \implies f_{2} < -\frac{t}{2} + f_{3} + f_{4} 
\label{sysMn5Lev3-2} \newline 
-2f_{2} + 2f_{3} + 2f_{5} > t \implies f_{2} < -\frac{t}{2} + f_{3} + f_{5} 
\label{sysMn5Lev3-3} \newline 
-2f_{2} + 2f_{4} + 2f_{5} > t \implies f_{2} < -\frac{t}{2} + f_{4} + f_{5} 
\label{sysMn5Lev3-4} \newline 
-2f_{1} + 2f_{2} + 2f_{3} > t \implies f_{1} < -\frac{t}{2} + f_{2} + f_{3} 
\label{sysMn5Lev3-5} \newline 
-2f_{1} + 2f_{2} + 2f_{4} > t \implies f_{1} < -\frac{t}{2} + f_{2} + f_{4} 
\label{sysMn5Lev3-6} \newline 
-2f_{1} + 2f_{2} + 2f_{5} > t \implies f_{1} < -\frac{t}{2} + f_{2} + f_{5} 
\label{sysMn5Lev3-7} \newline 
-2f_{1} + 2f_{3} + 2f_{4} > t \implies f_{1} < -\frac{t}{2} + f_{3} + f_{4} 
\label{sysMn5Lev3-8} \newline
-2f_{1} + 2f_{3} + 2f_{5} > t \implies f_{1} < -\frac{t}{2} + f_{3} + f_{5} 
\label{sysMn5Lev3-9} \newline
-2f_{1} + 2f_{4} + 2f_{5} > t \implies f_{1} < -\frac{t}{2} + f_{4} + f_{5} 
\label{sysMn5Lev3-10} 
\end{gather} 
The inequality in the equation \eqref{sysMn5Lev3-1} gives an yields an upper 
bound which is smaller than the one in the equation \eqref{Mn5Lev2Solnf3}. So, 
the $3^{rd}$ level solution for $f_{3}$ is as follows: 
\begin{equation} 
f_{3} < -\frac{t}{2} + f_{4} + f_{5}  
\end{equation} 
Three upper bounds for $f_{2}$ are given in the equations 
\eqref{sysMn5Lev3-2}, \eqref{sysMn5Lev3-3} and \eqref{sysMn5Lev3-4}. The 
smallest of them is 
\begin{equation} 
-\frac{t}{2}+f_{3}+f_{4}
\end{equation} 
Hence, the $3^{rd}$ level solution for $f_{2}$ is 
\begin{equation} 
f_{2} < -\frac{t}{2} + f_{3} + f_{4}
\end{equation} 
There are six upper bounds for $f_{1}$ in the equations 
\eqref{sysMn5Lev3-5}, \eqref{sysMn5Lev3-6}, 
\eqref{sysMn5Lev3-7}, \eqref{sysMn5Lev3-8}, 
\eqref{sysMn5Lev3-9} and \eqref{sysMn5Lev3-10}. The smallest of them is 
\begin{equation} 
-\frac{t}{2}+f_{2}+f_{3}
\end{equation} 
Therefore, the $3^{rd}$ level solution for $f_{1}$ is 
\begin{equation} 
f_{1} < -\frac{t}{2} + f_{2} + f_{3} 
\end{equation} 
The $3^{rd}$ level solution for $mn=5$ is as follows: 
\begin{gather} 
f_{5} < -\frac{t}{2} \newline 
f_{4} < -\frac{t}{2} + f_{5} \newline 
f_{3} < -\frac{t}{2} + f_{4} + f_{5} \newline 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} \label{Mn5Lev3Solnf2}\newline 
f_{1} < -\frac{t}{2} + f_{2} + f_{3}
\end{gather} 
The $4^{th}$ level solution is to be constructed by updating the $3^{rd}$ 
level solution using the following inequalities which give new upper bounds: 
\begin{gather} 
-2f_{2} + 2f_{3} + 2f_{4} + 2f_{5} > t \implies f_{2} < -\frac{t}{2} + f_{3} + 
f_{4} + f_{5} \label{sysMn5Lev4-1} \newline 
-2f_{1} + 2f_{2} + 2f_{3} + 2f_{4} > t \implies f_{1} < -\frac{t}{2} + f_{2} + 
f_{3} + f_{4} \label{sysMn5Lev4-2} \newline 
-2f_{1} + 2f_{2} + 2f_{3} + 2f_{5} > t \implies f_{1} < -\frac{t}{2} + f_{2} + 
f_{3} + f_{5} \label{sysMn5Lev4-3} \newline 
-2f_{1} + 2f_{3} + 2f_{4} + 2f_{5} > t \implies f_{1} < -\frac{t}{2} + f_{3} + 
f_{4} + f_{5}\label{sysMn5Lev4-4}
\end{gather} 
The inequality in the equation \eqref{sysMn5Lev4-1} provides a new upper bound 
for $f_{2}$. This upper bound is smaller than the one in the equation 
\eqref{Mn5Lev3Solnf2}. So, the $4^{th}$ level solution for $f_{2}$ is 
\begin{equation} 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} + f_{5}
\end{equation} 
There are three new upper bounds for $f_{1}$ in the equations 
\eqref{sysMn5Lev4-2}, \eqref{sysMn5Lev4-3} and \eqref{sysMn5Lev4-4}. The 
smallest of them is 
\begin{equation} 
-\frac{t}{2} + f_{2} + f_{3} + f_{4}
\end{equation} 
So, the $4^{th}$ level solution for $f_{1}$ is 
\begin{equation} 
f_{1} < -\frac{t}{2} + f_{2} + f_{3} + f_{4}
\end{equation} 
The $4^{th}$ level solution for $mn=5$ can now be written as follows: 
\begin{gather} 
f_{5} < -\frac{t}{2} \newline 
f_{4} < -\frac{t}{2} + f_{5} \newline 
f_{3} < -\frac{t}{2} + f_{4} + f_{5} \newline 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} + f_{5} \newline 
f_{1} < -\frac{t}{2} + f_{2} + f_{3} + f_{4}
\end{gather} 
The $5^{th}$ level solution is obtained updating the $4^{th}$ level solution 
by using the following equation which sets a new upper bound for $f_{1}$: 
\begin{equation} 
-2f_{1} + 2f_{2} + 2f_{3} + 2f_{4} + 2f_{5} > t \implies f_{1} < -\frac{t}{2} + 
f_{2} + f_{3} + f_{4} + f_{5}
\end{equation} 
As a result, the $5^{th}$ level or the final solution for $mn=5$ is as follows: 
\begin{gather} 
f_{5} < -\frac{t}{2} \newline 
f_{4} < -\frac{t}{2} + f_{5} \newline 
f_{3} < -\frac{t}{2} + f_{4} + f_{5} \newline 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} + f_{5} \newline 
f_{1} < -\frac{t}{2} + f_{2} + f_{3} + f_{4} + f_{5}
\end{gather} 

The systematic procedure for finding a specific type of analytical solution for 
$mn=3$, $mn=4$ and $mn=5$ must have given a feeling for the solution for 
$mn=12$. In fact, this feeling implies the following solution for $mn=12$: 
\begin{equation} 
\begin{array}{c}
f_{12} < -\frac{t}{2} \newline 
f_{11} < -\frac{t}{2} + f_{12} \newline 
f_{10} < -\frac{t}{2} + f_{11} + f_{12} \newline 
f_{9}  < -\frac{t}{2} + f_{10} + f_{11} + f_{12} \newline 
f_{8} <  -\frac{t}{2} + f_{9} + f_{10} + f_{11} + f_{12} \newline 
f_{7} <  -\frac{t}{2} + f_{8} + f_{9} + f_{10} + f_{11} + f_{12} \newline 
f_{6} <  -\frac{t}{2} + f_{7} + f_{8} + f_{9} + f_{10} + f_{11} + f_{12} 
\newline 
f_{5} <  -\frac{t}{2} + f_{6} + f_{7} + f_{8} + f_{9} + f_{10} + f_{11} + 
f_{12} \newline 
f_{4} <  -\frac{t}{2} + f_{5} + f_{6} + f_{7} + f_{8} + f_{9} + f_{10} + 
f_{11} + f_{12} \newline 
f_{3} <  -\frac{t}{2} + f_{4} + f_{5} + f_{6} + f_{7} + f_{8} + f_{9} + 
f_{10} + f_{11} + f_{12} \newline 
f_{2} <  -\frac{t}{2} + f_{3} + f_{4} + f_{5} + f_{6} + f_{7} + f_{8} + f_{9} + 
f_{10} + f_{11} + f_{12} \newline 
f_{1} <  -\frac{t}{2} + f_{2} + f_{3} + f_{4} + f_{5} + f_{6} + f_{7} + f_{8} + 
f_{9} + f_{10} + f_{11} + f_{12} 
\end{array} 
\label{mn12Solution}
\end{equation} 
Now, the procedure applied to the cases of $mn=3$, $mn=4$, $mn=5$ and $mn=12$ 
will be generalized to any $mn$ value by proving a theorem. 

**Theorem:** Let there be a filter of size $mn=N$. The $k^{th}$ level solution 
is as follows: 
\begin{equation} 
f_{i} < -\frac{t}{2} \text{ if } k=1
\end{equation}
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} + f_{i+2} + \ldots + f_{i+k-1} \left (i+1 \leq 
i+k-1 \leq N \right ) \text{ if } 2 \leq k \leq N
\end{equation} 
where 
\begin{equation} 
1 \leq i \leq N
\end{equation} 

Let the theorem be first applied to the cases of $mn=3$, $mn=4$ and $mn=5$. 
Then, it is going to be proven. $mn=3$ and $k=1$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} \text{ for } 1 \leq i \leq 3 \implies 
\begin{cases} 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2} 
\end{cases}
\end{equation} 
$mn=3$ and $k=2$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} \text{ for } 1 \leq i \leq 3 \implies 
\begin{cases} 
f_{3} < -\frac{t}{2} & \left (i+1 \leq 3 \right ) \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2} 
\end{cases}
\end{equation} 
$mn=3$ and $k=3$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} + f_{i+2} \text{ for } 1 \leq i \leq 3 \implies 
\begin{cases} 
f_{3} < -\frac{t}{2} & \left ( i+1 \leq i+2 \leq 3 \right ) \newline 
f_{2} < -\frac{t}{2} + f_{3} & \left ( i+2 \leq 3 \right ) \newline 
f_{1} < -\frac{t}{2} + f_{2} + f_{3}
\end{cases} 
\end{equation}  
All the results for $mn=3$ agree with the ones derived previously. 

$mn=4$ and $k=1$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} \text{ for } 1 \leq i \leq 4 \implies 
\begin{cases} 
f_{4} < -\frac{t}{2} \newline 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2}
\end{cases}
\end{equation} 
$mn=4$ and $k=2$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} \text{ for } 1 \leq i \leq 4 \implies 
\begin{cases} 
f_{4} < -\frac{t}{2} & \left ( i+1 \leq 4 \right ) \newline 
f_{3} < -\frac{t}{2} + f_{4} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2}
\end{cases}
\end{equation} 
$mn=4$ and $k=3$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} + f_{i+2} \text{ for } 1 \leq i \leq 4 \implies 
\begin{cases} 
f_{4} < -\frac{t}{2} & \left (i+1 \leq i+2 \leq 4 \right ) \newline 
f_{3} < -\frac{t}{2} + f_{4} & \left (i+2 \leq 4 \right) \newline 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} \newline 
f_{1} < -\frac{t}{2} + f_{2} + f_{3} 
\end{cases} 
\end{equation} 
$mn=4$ and $k=4$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} + f_{i+2} + f_{i+3} \text{ for } 1\leq i \leq 4 
\implies 
\begin{cases} 
f_{4} < -\frac{t}{2} & \left(i+1 \leq i+2 \leq i+3 \leq 4\right) \newline
f_{3} < -\frac{t}{2} + f_{4} & \left(i+2 \leq i+3 \leq 4 \right) \newline 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} & \left(i+3 \leq 4 \right) \newline 
f_{1} < -\frac{t}{2} + f_{2} + f_{3} + f_{4} 
\end{cases} 
\end{equation}
All the results for $mn=4$ agree with the ones derived previously. 

$mn=5$ and $k=1$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} \text{ for } 1 \leq i \leq 5 \implies 
\begin{cases} 
f_{5} < -\frac{t}{2} \newline 
f_{4} < -\frac{t}{2} \newline 
f_{3} < -\frac{t}{2} \newline 
f_{2} < -\frac{t}{2} \newline 
f_{1} < -\frac{t}{2} 
\end{cases} 
\end{equation} 
$mn=5$ and $k=2$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} \text{ for } 1 \leq i \leq 5 \implies 
\begin{cases} 
f_{5} < -\frac{t}{2} & \left(i+1 \leq 5\right) \newline 
f_{4} < -\frac{t}{2} + f_{5} \newline 
f_{3} < -\frac{t}{2} + f_{4} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2}
\end{cases} 
\end{equation}
$mn=5$ and $k=3$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} + f_{i+2} \text{ for } 1 \leq i \leq 5 \implies 
\begin{cases} 
f_{5} < -\frac{t}{2} & \left(i+1 \leq i+2 \leq 5\right) \newline 
f_{4} < -\frac{t}{2} + f_{5} & \left(i+2 \leq 5\right) \newline 
f_{3} < -\frac{t}{2} + f_{4} + f_{5} \newline 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} \newline 
f_{1} < -\frac{t}{2} + f_{2} + f_{3}
\end{cases}
\end{equation} 
$mn=5$ and $k=4$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} + f_{i+2} + f_{i+3} \text{ for } 1\leq i \leq 5 
\implies 
\begin{cases} 
f_{5} < -\frac{t}{2} & \left(i+1 \leq i+2 \leq i+3 \leq 5\right) \newline 
f_{4} < -\frac{t}{2} + f_{5} & \left(i+2 \leq i+3 \leq 5\right) \newline 
f_{3} < -\frac{t}{2} + f_{4} + f_{5} & \left(i+3 \leq 5\right) \newline 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} + f_{5} \newline 
f_{1} < -\frac{t}{2} + f_{2} + f_{3} + f_{4}
\end{cases}
\end{equation} 
$mn=5$ and $k=5$ imply 
\begin{equation} 
f_{i} < -\frac{t}{2} + f_{i+1} + f_{i+2} + f_{i+3} + f_{i+4} \text{ for } 
1 \leq i \leq 5 \implies 
\begin{cases} 
f_{5} < -\frac{t}{2} & \left(i+1 \leq i+2 \leq i+3 \leq i+4 \leq 5\right) 
\newline 
f_{4} < -\frac{t}{2} + f_{5} & \left(i+2 \leq i+3 \leq i+4 \leq 5\right) 
\newline 
f_{3} < -\frac{t}{2} + f_{4} + f_{5} & \left(i+3 \leq i+4 \leq 5\right) 
\newline 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} + f_{5} & \left(i+4 \leq 5\right) \newline 
f_{1} < -\frac{t}{2} + f_{2} + f_{3} + f_{4} + f_{5}
\end{cases}
\end{equation} 
All the results for $mn=5$ agree with the ones derived previously. 

Now that the theorem has been applied to several cases for some $mn$ values, 
its proof can be made. First, the $1^{st}$ level solution for $mn=N$ will be 
derived. Let a filter of $N$ components be represented by the following row 
vector: 
\begin{equation} 
f=
\begin{bmatrix} 
f_{1} & f_{2} & \ldots & f_{N-1} & f_{N}
\end{bmatrix} 
\end{equation} 
There can be two pixel vectors whose components are the same except the one in 
the $i^{th}$ location where $1 \leq i \leq N$. Let the common values be denoted 
by $c_{c}$. Then, such two vectors $v_{1}$ and $v_{2}$ can be as follows: 
\begin{gather} 
v_{1}=
\begin{bmatrix} 
c_{c} & c_{c} & \ldots & -1 & \ldots & c_{c} & c_{c}
\end{bmatrix} \newline 
v_{2}=
\begin{bmatrix} 
c_{c} & c_{c} & \ldots & 1 & \ldots & c_{c} & c_{c}
\end{bmatrix} 
\end{gather} 
The inner products of the filter with the vectors will be as follows: 
\begin{gather} 
v_{1}.f=c_{c}f_{1} + c_{c}f_{2}+ \ldots + \left(-1\right)f_{i} + \ldots + 
c_{c}f_{N-1} + c_{c} f_{N} 
\end{gather} 
\begin{gather} 
v_{2}.f=c_{c}f_{1} + c_{c}f_{2}+ \ldots + \left(1\right)f_{i} + \ldots + 
c_{c}f_{N-1} + c_{c} f_{N} 
\end{gather} 
The difference of the two inner products will be as follows: 
\begin{equation} 
v_{1}.f-v_{2}.f=-2f_{i} 
\end{equation} 
The magnitude of this inner product difference must be greater than the 
threshold $t$: 
\begin{equation} 
\left |-2f_{i} \right | > t \implies -2f_{i} > t \text{ or } -2f_{i} < -t
\end{equation} 
Taking the first inequality implies 
\begin{equation} 
-2f_{i} > t \implies f_{i} < -\frac{t}{2} 
\end{equation} 
So, the form of the $1^{st}$ level solution has been proven.

Now, the general form of the $k^{th}$ level solution will be derived. The 
$k^{th}$ level solution is obtained from inequalities which involve the linear 
combinations containing $k$ filter components. For reaching the specific type 
of analytic solution this proof seeks, the first coefficient, the coefficient 
of $f_{i}$ is $-2$. The other coefficients are $2$. The general form of this 
inequality is as follows: 
\begin{equation} 
-2f_{i} + \text{LC}\_{k-1} > t 
\end{equation} 
$\text{LC}\_{k-1}$ represents all linear combinations of the filter 
coefficients from the following set: 
\begin{equation} 
\left \lbrace f_{i+1}, f_{i+2}, \ldots , f_{N} \right \rbrace 
\label{lcSet} 
\end{equation} 
$\text{LC}\_{k-1}$ has $k-1$ components and all the coefficients are $2$. Let 
the inequality be solved: 
\begin{equation} 
-2f_{i} + \text{LC}\_{k-1} > t \implies -2f_{i} > t - \text{LC}\_{k-1} 
\implies f_{i} < -\frac{t}{2} + \frac{1}{2} \text{LC}\_{k-1} 
\label{proofSoln1}
\end{equation} 
$\frac{1}{2} \text{LC}\_{k-1}$ represents all possible linear combinations of 
the filter coefficients from the set in the equation \eqref{lcSet}. The 
coefficients in these linear combinations are all $1$. There are more than one  
upper bounds given for $f_{i}$ in the equation \eqref{proofSoln1}. The smallest 
of them should be chosen as the upper bound for the $k^{th}$ level solution. 
Let the smallest be found. For $k=2$, the following solution is obtained: 
\begin{gather} 
f_{N} < -\frac{t}{2} \newline 
f_{N-1} < -\frac{t}{2} + f_{N} \newline 
f_{N-2} < -\frac{t}{2} + f_{N-1} \newline 
\vdots \newline
f_{3} < -\frac{t}{2} + f_{4} \newline 
f_{2} < -\frac{t}{2} + f_{3} \newline 
f_{1} < -\frac{t}{2} + f_{2}
\end{gather} 
The solution for $k=2$ implies the following ordering among the filter 
coefficients: 
\begin{equation} 
f_{1} < f_{2} < f_{3} < \ldots < f_{N-2} < f_{N-1} < f_{N} 
\label{ordering}
\end{equation} 
Assuming that this ordering is true for $k=p^{th}$ level, it will be shown 
that the ordering stays the same for the level $p+1$. For the level $p+1$, 
the upper bound for $f_{i}$ is updated by adding $f_{i+p}$ because 
$f_{i+p}$ is the smallest filter coefficient according to the assumption that 
the ordering in the equation \eqref{ordering} is maintained. The upper bound 
for $f_{i+1}$ is updated by adding $f_{i+p+1}$ since it is the smallest filter 
coefficient according to the assumed ordering. The assumed ordering implies 
\begin{equation} 
f_{i+p} < f_{i+p+1}
\end{equation} 
So, the ordering between $f_{i}$ and $f_{i+1}$ does not change for the level 
$p+1$. It has been shown that the assumed ordering for $p^{th}$ level does not 
change for the level $p+1$. As a result, the ordering in the equation 
\eqref{ordering} is true for all levels of the solution. Then, the smallest of 
the upper bounds given for $f_{i}$ in the equation \eqref{proofSoln1} can now 
be written. It should be as follows: 
\begin{equation} 
-\frac{t}{2} + f_{i+1} + f_{i+2} + \ldots + f_{i+k-1}  
\end{equation} 
where 
\begin{equation} 
i+ k - 1 \leq N
\end{equation} 
The proof for the general form of the $k^{th}$ level solution has ended. 

The solutions found by the gradient-based optimization are to be commented on by taking the proven analytical solution into consideration. For $mn=5$, 
$f_{5}$ of the filter in the equation \eqref{mn5OptRes} is $-0.10139561$. The 
analytical solution for $f_{5}$ is 
\begin{equation}
f_{5} < -\frac{t}{2} \implies f_{5} < -\frac{0.2}{2} \implies f_{5} < -0.1
\end{equation} 
So, the solution found by optimization for $f_{5}$ is in agreement with the 
analytical solution. $f_{4}$ in the equation \eqref{mn5OptRes} is 
$-0.20954087$. The analytical solution is 
\begin{equation} 
f_{4} < -\frac{t}{2} + f_{5} \implies f_{4} < -\frac{0.2}{2} + -0.10139561 
\implies f_{4} < -0.20139561
\end{equation} 
So, the optimization's solution is in agreement with the analytical solution. 
$f_{3}$ in the equation \eqref{mn5OptRes} is $-0.41564267$. The analytical 
solution is 
\begin{equation} 
f_{3} < -\frac{t}{2} + f_{4} + f_{5} \implies f_{3} < -\frac{0.2}{2} + 
\left(-0.20954087 \right) + \left(-0.10139561\right) \implies f_{3} < 
-0.4109365
\end{equation} 
The optimization's solution agrees with the analytical solution again. $f_{2}$ 
in the equation \eqref{mn5OptRes} is $-0.83371858$. The analytical solution is 
\begin{equation} 
f_{2} < -\frac{t}{2} + f_{3} + f_{4} + f_{5} \implies f_{2} < -\frac{0.2}{2} + 
\left(-0.41564267\right) + \left(-0.20954087\right) + \left(-0.10139561\right) 
\implies f_{2} < -0.8265791
\end{equation} 
There is again an agreement between the optimization's solution and the 
analytical solution. $f_{1}$ in the equation \eqref{mn5OptRes} is 
$-1.67258483$. The analytical solution is 
\begin{equation} 
f_{1} < -\frac{t}{2} + f_{2}+f_{3}+f_{4} +f_{5} \implies f_{1} < 
-\frac{0.2}{2} + \left(-0.83371858\right) + \left(-0.41564267\right) + 
\left(-0.20954087\right) + \left(-0.10139561\right) \implies 
f_{1} <-1.660298 
\end{equation} 
The optimization's solution is again in agreement with the analytical 
solution. Optimization solutions  for other $mn$ values can also be compared to 
the analytical solution. 

The observation that the ratio of the consecutive components from left to right 
in the optimization solutions is approximately 2 has come out to be a 
misleading observation. 

## An Application Of The Analytical Solution 
The solution in the equation \eqref{mn12Solution} for $mn=12$ is tested to 
determine if it yields unique identity numbers for binary images of the same 
dimension. The threshold $t$ is chosen to be equal to $1.0$. A numerical 
solution is as follows: 
\begin{equation} 
\begin{bmatrix} 
-1370.0 & -683.4 & -342.0 & -170.7 & -85.5 & -42.6 & -21.4 & -10.6 & -5.4 & -2.6 & -1.4 & -0.6 
\end{bmatrix} 
\label{numSolmn12}
\end{equation} 
This numerical solution is tested using the Python code at the link 
<a href="#testLink">[2]</a>. As a result of the test, it is verified that the 
identities generated by the filter in the \eqref{numSolmn12} are far from each 
other with a distance greater than $1.0$.

## Conclusion 
An analytical solution for the problem of generating unique identities for 
binary images has been found. A proof has been made for the general form of 
this analytical solution has been made. It has also been shown that there are 
analytical solutions in other mathematical forms, as well.

## References 

<span id="numerical"> [1] [https://saffetgokcensen.github.io/blog/2024/11/05/one-to-one-mapping-between-an-image-and-a-filter](https://saffetgokcensen.github.io/blog/2024/11/05/one-to-one-mapping-between-an-image-and-a-filter)</span>

<span id="testLink"> [2] [https://github.com/SaffetGokcenSen/anAnalyticalSolutionForOneToOneMappingFromAFilterToABinaryImage/blob/main/testSolutionMn12.py](https://github.com/SaffetGokcenSen/anAnalyticalSolutionForOneToOneMappingFromAFilterToABinaryImage/blob/main/testSolutionMn12.py)</span>
