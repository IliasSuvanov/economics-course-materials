---
sort: 2
---

# System of Linear Equations: Matrices and Economic-Business Application

In economics and not only in it, problems can be represented as equations. Relationship of several equations form a system of equations. In order to solve those systems – Gauss’, Cramer’s and other methods used.

## Cramer’s rule

Given equation: We need to find x and y.

22x – 50y = 10

33x + 8y   = 181

Algorithm of solution:

1) represent as matrix:

22	-50	10

33	8	181

2) find determinant ∆: just imagine crossing a line from up to right down, these numbers get multiplied, answer column ignored at this part. Then got results subtract, from left side.

22·8 - 33·(-50) = 1826

3) next find ∆x: put answer column of matrix into x variables column

10	-50

181	8

And, make calculation as if you finding determinant of this matrix:

10·8 - 181·(-50) =  9130

4) do this to ∆y: put answer column of matrix to y variables column, solve it:

22·181 - 33·10 = 3652

5) Divide ∆x by ∆ and ∆y by ∆:

x = 9130 / 1826 = 5

y = 3652 / 1826 = 2

System solved! For 3 by 3 matrix technic is the same. For bigger than 3 by 3 matrices use Gauss method.

## Economic-Business problems solved using matrices

Given problem 1:

Factory produces 3 types of cars. Sedan require 2 days to assemble, 1 day to paint, and 2 days to check. SUV require 3, 2, and 5 days. Truck 15, 20, and 10 correspondingly. How much of each type of car made, if was spent 310 days for assembly, 290 for paint, and 300 for check?


This problem can be represented as system of equations: consider sedan as x, SUV as y, and spaceship as z. Adding assemble value of each will give total for assembly, and solving it give value for every car.

```
2x + 3y + 15z = 310
x + 2y + 20z = 290
2x + 5y + 10z = 300
```


Let’s solve using Cramer’s rule:

1) Represent as matrix:
$$\begin{matrix}
2&	3&	15&	310 \\
1&	2&	20&	290 \\
2&	5&	10&	300
\end{matrix} $$

```
Find determinant = 2*(2*10-5*20)-1*(3*10-5*15) +2*(3*20-2*15) = -55
Find ∆x: 310*(2*10-5*20)-290*(3*10-5*15) +300*(3*20-2*15) = -2750
Find ∆y: 2*(290*10-300*20)-1*(310*10-300*15) +2*(310*20-290*15) = -1100
Find ∆z: 2*(2*300-5*290)-1*(3*300-5*310) +2*(3*290-2*310) = -550
Find x, y, z:
x = -2750/-55 = 50
y = -1100/-55 = 20
z = -550/-55 = 10
```

Answer: 50 Sedans, 20 SUVs, and 10 Trucks

Problem 2:
Shop sells good for $100. Expects to make profit equaling to one third of costs. What is amount of cost and profit, if profit is difference of revenue and cost?
Assume profit as x and cost as y. If shop sells 1 unit of product it will be revenue. Consider $100 as revenue. If profit is difference of revenue and cost, then revenue is sum of profit and cost. It is known that x equals to 1/3 of y, then difference of x and 1/3 of y should equal zero.

Insert to system:
X + y = 100
X – 1/3y = 0

Solve system:

Find ∆, ∆x and ∆y:
1*-1/3 - 1·1 = -4/3
100*-1/3 - 0·1 = -100/3
1·0 - 1·100 = -100
Find x and y:
x = -100/3 / -4/3 = 25 is profit
y = -100 / -4/3 = 75 is costs

Problem 3:
A private investment club has $144,000 earmarked for investment in stocks. Management estimates that high-risk stocks will have a return rate of 16%/year; medium-risk stocks, 9%/year; and low-risk stocks, 4%/year. The members have decided that the investment in low-risk stocks should be equal to the sum of the investments in the stocks of the other two categories. Determine how much the club should invest in each type of stock if the investment goal is to have a return of $11,810/year on the total investment?

This problem can be represented as system of equations. Problem says that overall budget is 144,000, while we have three categories split, these three should be variables: l, m, and h. Logically l + m + h would give 144,000. It is given that one category should be sum of other two, l = m + h. In order to put it into system formulate equation as l – (m + h) = 0 or l – m – h = 0, nothing changes. It also says, goal to be 11,810 at corresponding rates. 0.04l + 0.09m + 0.16h = 11,810.

Build system:
l + m + h = 144000
0.04l + 0.09m + 0.16h = 11,810
l – m – h = 0

Represent as matrix:
1	1	1	144000
0.04	0.09	0.16	11810
1	-1	-1	0
Solve it:
Find ∆, ∆x and ∆y:
∆ = 7/50
∆l = 10080
∆m = 5180
∆h = 4900
Find l, m, and h values:
l = 72000
m = 37000
h = 35000

Thus, in economic problems requiring solving it as system of equations, one must carefully read problem, represent problem as system of equations correctly, and solve it using Cramer’s rule or Gauss or any other.
