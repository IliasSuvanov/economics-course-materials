---
sort: 3
---

# Input-Output Analysis

Shortly, Input-output analyses flow of products among industries. For instance, cars are made of tires, glass, steel, and many other products which are made by different producers. Here output of one company is input to other and vice versa.

## Matrix operations

### Addition

$$\begin{matrix}
1&	2 \\
4&	4
\end{matrix}

+

\begin{matrix}
0.5&	60 \\
6&	0
\end{matrix}

=

\begin{matrix}
1.5&	62 \\
10&	4
\end{matrix}


# Input-output


Assume there are 2 industries in economy: households(H) and firms(F). $1 output of H require 5 cents of H and 50 cents of F. $1 output of F require 35 and 15 cents correspondingly. It can be represented as matrix of technical coefficients:


|     |   H  |   F  |
| ---- | ---- | ---- |
|  H   |  0.5  |  0.35 |
|  F   |  0.5  |  0.15  |


(Carefully look how to build matrices of technical coefficients)
Now, suppose we need to produce 500 monetary units of H and 300 units of F. Then:
.05 * 500 = 25 H required for production of 500 H
.5 * 500 = 250 F required for production of 500 H
.35 * 300 = 105 H required for production of 300 F
.15 * 300 = 45 F required for production of 300 F
What left:
500 H – 25 H – 105 H = 370 H as remainder
300 F – 250 F – 45 F = 5 F as remainder
Now that 370 H and 5 F could be used for final demand.
- How much output is available for final demand given the total output level?
- How much total output is required to satisfy a given level of final demand?
These questions could be answered using just one equation:
x = Ax + d,
where x = total output vector; A = matrix of technical coefficients; d = final demand

