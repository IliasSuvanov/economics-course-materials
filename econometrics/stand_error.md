---
sort: 9
text: |
  ABCDEFGHIJKLMNOPQRSTUVWXYZ
  abcdefghijklmnopqrstuvwxyz
  1234567890
  一二三四五六七八九十百千萬上中下左右大小春夏秋冬東南西北金木水火土
  ‘?’“!”(%)[#]{@}/&\<-+÷×=>®©$€£¥¢:;,.*
---

## Standard error


The standard error (SE) of a statistic (usually an estimate of a parameter) is the standard deviation of its sampling distribution or an estimate of that standard deviation. 

Let estimate regression, on how price affects number of packs of cigarettes smoked. 

We will use cross-section data on cigarette consumption for 46 US States, for the year 1992.

A data frame containing 46 observations on 3 variables.
- *packs* Logarithm of cigarette consumption (in packs) per person of smoking age (> 16 years).
- *price* Logarithm of real price of cigarette in each state.
- *income* Logarithm of real disposable income (per capita) in each state.

We will regress packs on prices, and get estimate $$\beta$$.
$$ packs_i = \beta price_i + \epsilon_i $$

In R we just supply data and run commands, and R will give us estimate of $$\beta$$.

```scss
# uploading library Aplied Econometrics with R. We will use dataset # CigarettesB from there.
library(AER)
data("CigarettesB")
model <- lm(data = CigarettesB, packs~price)
summary(model)
```

```
Call:
lm(formula = packs ~ price, data = CigarettesB)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.45472 -0.09968  0.00612  0.11553  0.29346 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)   5.0941     0.0627  81.247  < 2e-16 ***
price        -1.1983     0.2818  -4.253 0.000108 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.163 on 44 degrees of freedom
Multiple R-squared:  0.2913,	Adjusted R-squared:  0.2752 
F-statistic: 18.08 on 1 and 44 DF,  p-value: 0.0001085
```

Our estimate $$\hat{beta}$$ is -1.1983, which means that with 1 dollar increase in prices of cigarets, there is -1.19% decrease in consumption of cigaretes. 
However we need not only to get $$\hat{\beta}$$ estimate, but we also need to know how precies our estimate of $$\hat{\beta}$$ is. To answer this question, we can look at "standard errors" in our regression table. *Standard error* of our estimate is the standard deviation of our estimate $$\hat{\beta}$$ around the truth.
Standard error basically tells us, how precise our estimate is.


## Adjusted $$\bar{R^2}$$

$$\bar{R^2} = 1- \frac{(1-R^2)}{N-k-1}$$, where N is the number of rows in our spreadsheet, k is the number of columns.
From basic theory of regression we know that number of rows in our table has to be bigger than the number of columns, i.e. $$N\beq k$$.
Adjusted $$\bar{R^2}$$ is an attempt to account for the phenomenon of the R2 automatically and spuriously increasing when extra explanatory variables are added to the model.