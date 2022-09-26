---
sort: 2
---

# Interpreting regression with logarithm

```warning
Keep in mind difference between percentage points and perncet points change. For example, if the internet company A increased 5G coverage from 20 percent to 60 percent, we see here 40 percentage points increase, and not 40 percent increase in coverage. 
40 percent increase from 20 percent coverage would be equal to 20*1.4 = 28 percent 5G coverage.
```


Interpretation of regression coefficients with logarithm can be grouped in four categories presented below.

| Model | Dependent variable | Independent Variable | Interpretation |
| ---- | ----| ----| ----| 
| Level-level | y | x | $$\Delta y = \beta \Delta x $$|
| Level - log | y | log(y) | $$\Delta y = (\beta /100)\%\Delta x $$|
| Log-level | log(y) | x | $$ \% \Delta y = (100 \beta_1)\Delta x $$|
| Log - log | log(y) | log(x) | $$ \% \Delta y = \beta_1 % \Delta x $$|


Suppose we have data of 5 people on their ages and wages. We want to find out the relationship between age and wage. The basic idea is that the older person becomes, the more experience he accumulates and hence higher salary he would have.

```R
names <- c("Alex", "John", "Michael", "Joe", "Wu")
wages <- c(30000, 25000, 32000, 50000, 43000)
ages <- c(27, 25, 23, 30, 31)
df <- data.frame(names, wages, ages)
```


```R
head(df)
```


<table class="dataframe">
<caption>A data.frame: 5 × 3</caption>
<thead>
	<tr><th></th><th scope=col>names</th><th scope=col>wages</th><th scope=col>ages</th></tr>
	<tr><th></th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row>1</th><td>Alex   </td><td>30000</td><td>NA</td></tr>
	<tr><th scope=row>2</th><td>John   </td><td>25000</td><td>25</td></tr>
	<tr><th scope=row>3</th><td>Michael</td><td>   NA</td><td>23</td></tr>
	<tr><th scope=row>4</th><td>Joe    </td><td>50000</td><td>30</td></tr>
	<tr><th scope=row>5</th><td>Wu     </td><td>43000</td><td>NA</td></tr>
</tbody>
</table>

---

## Level - level regression

Regression formula is 

$$ wages = intercept + \beta*ages + error\_term $$

```R
model_lev_lev <- lm(data=df, wages~ages)
summary(model)
```
```
Call:
lm(formula = wages ~ ages, data = df)

Residuals:
    1     2     3     4     5 
-5518 -5696  6125  7250 -2161 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept)   -29571      29636  -0.998    0.392
ages            2411       1083   2.226    0.112

Residual standard error: 7249 on 3 degrees of freedom
Multiple R-squared:  0.6229,	Adjusted R-squared:  0.4972 
F-statistic: 4.955 on 1 and 3 DF,  p-value: 0.1124
```

The interpretation of log-level regression is that 1 unit(year) increase in _ages_ variable will on average correspond to 2411 units($) increase in wages. In other words, if the person becomes one year older on average he can expect increase in salary by 2411 dollars.

---

## Log-level regression

Regression formula is 

$$ log(wages) = intercept + \beta*ages + error\_term $$

```R
model_lev_log <- lm(data=df, log(wages)~ages)
summary(model_lev_log)
```
```
Call:
lm(formula = log(wages) ~ ages, data = df)

Residuals:
    1     2     3     4     5 
-5921 -6028  6274  7380 -1705 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept)  -173632      99333  -1.748    0.179
log(ages)      63581      30111   2.112    0.125

Residual standard error: 7486 on 3 degrees of freedom
Multiple R-squared:  0.5978,	Adjusted R-squared:  0.4637 
F-statistic: 4.459 on 1 and 3 DF,  p-value: 0.1252
```

The interpretation of level-log regression is that 1 unit(year) increase in _ages_ variable will on average correspond to (100*0.06537)% = 6.5% percent increase in wages. 

---

## Level-log regression

Regression formula is 

$$ wages = intercept + \beta*log(ages) + error\_term $$

```R
model_lev_log <- lm(data=df, log(wages)~ages)
summary(model_lev_log)
```
```
Call:
lm(formula = wages ~ log(ages), data = df)

Residuals:
    1     2     3     4     5 
-5921 -6028  6274  7380 -1705 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept)  -173632      99333  -1.748    0.179
log(ages)      63581      30111   2.112    0.125

Residual standard error: 7486 on 3 degrees of freedom
Multiple R-squared:  0.5978,	Adjusted R-squared:  0.4637 
F-statistic: 4.459 on 1 and 3 DF,  p-value: 0.1252
```

The interpretation of log-level regression is that 1 percent increase in _ages_ variable will on average correspond to 63581*/100 = 635.81 unit($) increase in wages. 

---


## Log-log regression

Regression formula is 

$$ log(wages) = intercept + \beta*log(ages) + error\_term $$

```R
model_log_log <- lm(data=df, log(wages)~log(ages))
summary(model_lev_log)
```
```
Call:
lm(formula = log(wages) ~ log(ages), data = df)

Residuals:
       1        2        3        4        5 
-0.14847 -0.19844  0.19182  0.18115 -0.02606 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept)   4.7892     2.7803   1.723    0.183
log(ages)     1.7198     0.8428   2.041    0.134

Residual standard error: 0.2095 on 3 degrees of freedom
Multiple R-squared:  0.5812,	Adjusted R-squared:  0.4417 
F-statistic: 4.164 on 1 and 3 DF,  p-value: 0.134
```

The interpretation of log-level regression is that 1 percent increase in _ages_ variable will on average correspond to 1.7198 % increase in _wages_. 

---
