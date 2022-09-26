---
sort: 3
---


# Econometric models

## Probit and logit models

In the probit and logit models dependent variable is dummy variable (0 and 1). For example, whether you defaulted on your credit or not. Whether you are eligible for the program or not, etc etc.


### Data source
For more details please refere to AER package documentation, page 140. [link](https://cran.r-project.org/web/packages/AER/AER.pdf)
Cross-section data about resume, call-back and employer information for 4,870 fictitious resumes
sent in response to employment advertisements in Chicago and Boston in 2001, in a randomized
controlled experiment conducted by Bertrand and Mullainathan (2004). The resumes contained
information concerning the ethnicity of the applicant. Because ethnicity is not typically included
on a resume, resumes were differentiated on the basis of so-called “Caucasian sounding names”
(such as Emily Walsh or Gregory Baker) and “African American sounding names” (such as Lakisha
Washington or Jamal Jones). A large collection of fictitious resumes were created and the presupposed ethnicity (based on the sound of the name) was randomly assigned to each resume. These
resumes were sent to prospective employers to see which resumes generated a phone call from the
prospective employer.

### Logit model

```scss
library(AER)
data(ResumeNames)
head(ResumeNames)
```


<table class="dataframe">
<caption>A data.frame: 6 × 27</caption>
<thead>
	<tr><th></th><th scope=col>name</th><th scope=col>gender</th><th scope=col>ethnicity</th><th scope=col>quality</th><th scope=col>call</th><th scope=col>city</th><th scope=col>jobs</th><th scope=col>experience</th><th scope=col>honors</th><th scope=col>volunteer</th><th scope=col>...</th><th scope=col>minimum</th><th scope=col>equal</th><th scope=col>wanted</th><th scope=col>requirements</th><th scope=col>reqexp</th><th scope=col>reqcomm</th><th scope=col>reqeduc</th><th scope=col>reqcomp</th><th scope=col>reqorg</th><th scope=col>industry</th></tr>
	<tr><th></th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>...</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;fct&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row>1</th><td>Allison</td><td>female</td><td>cauc</td><td>low </td><td>no</td><td>chicago</td><td>2</td><td> 6</td><td>no </td><td>no </td><td>...</td><td>5   </td><td>yes</td><td>supervisor</td><td>yes</td><td>yes</td><td>no</td><td>no</td><td>yes</td><td>no </td><td>manufacturing                   </td></tr>
	<tr><th scope=row>2</th><td>Kristen</td><td>female</td><td>cauc</td><td>high</td><td>no</td><td>chicago</td><td>3</td><td> 6</td><td>no </td><td>yes</td><td>...</td><td>5   </td><td>yes</td><td>supervisor</td><td>yes</td><td>yes</td><td>no</td><td>no</td><td>yes</td><td>no </td><td>manufacturing                   </td></tr>
	<tr><th scope=row>3</th><td>Lakisha</td><td>female</td><td>afam</td><td>low </td><td>no</td><td>chicago</td><td>1</td><td> 6</td><td>no </td><td>no </td><td>...</td><td>5   </td><td>yes</td><td>supervisor</td><td>yes</td><td>yes</td><td>no</td><td>no</td><td>yes</td><td>no </td><td>manufacturing                   </td></tr>
	<tr><th scope=row>4</th><td>Latonya</td><td>female</td><td>afam</td><td>high</td><td>no</td><td>chicago</td><td>4</td><td> 6</td><td>no </td><td>yes</td><td>...</td><td>5   </td><td>yes</td><td>supervisor</td><td>yes</td><td>yes</td><td>no</td><td>no</td><td>yes</td><td>no </td><td>manufacturing                   </td></tr>
	<tr><th scope=row>5</th><td>Carrie </td><td>female</td><td>cauc</td><td>high</td><td>no</td><td>chicago</td><td>3</td><td>22</td><td>no </td><td>no </td><td>...</td><td>some</td><td>yes</td><td>secretary </td><td>yes</td><td>yes</td><td>no</td><td>no</td><td>yes</td><td>yes</td><td>health/education/social services</td></tr>
	<tr><th scope=row>6</th><td>Jay    </td><td>male  </td><td>cauc</td><td>low </td><td>no</td><td>chicago</td><td>2</td><td> 6</td><td>yes</td><td>no </td><td>...</td><td>none</td><td>yes</td><td>other     </td><td>no </td><td>no </td><td>no</td><td>no</td><td>no </td><td>no </td><td>trade                           </td></tr>
</tbody>
</table>


```R
# encoding "call" column categorical levels into numerical
ResumeNames$call <- ifelse(ResumeNames$call == "yes", 1, 0)
# making logit model
model_logit <- glm(call ~ethnicity + gender + quality, data = ResumeNames)
summary(model_logit)
```

```
Call:
Call:
glm(formula = call ~ ethnicity + gender + quality, family = binomial(link = "logit"),
    data = ResumeNames)

Deviance Residuals:
    Min       1Q   Median       3Q      Max
-0.4770  -0.4356  -0.3867  -0.3525   2.4207

Coefficients:
              Estimate Std. Error z value Pr(>|z|)
(Intercept)    -2.4350     0.1348 -18.058  < 2e-16 ***
ethnicityafam  -0.4399     0.1074  -4.096  4.2e-05 ***
genderfemale    0.1276     0.1289   0.990   0.3222
qualityhigh     0.1914     0.1059   1.806   0.0709 .
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 2726.9  on 4869  degrees of freedom
Residual deviance: 2705.7  on 4866  degrees of freedom
AIC: 2713.7

Number of Fisher Scoring iterations: 5
```

From the regression table we can see coefficient for **ethnicityafam** is **-0.4399**, that means that if the applicant have african american sounding name then he is less likely to recieve call back.

```warning
We can not interpret magnitude from the regression table for **logit** model, only we can interpret the direction of the effect i.e. more likely or less likely get called back.
```


### Probit model
Probit models are pretty much similiar to logit models(see above). Just in the `glm()` command we need to specify the `family` argument to be `family = binomial(link="logit")`.

```
model_probit <- glm(call ~ ethnicity + gender + quality, family = binomial (link="probit"), data = ResumeNames)
summary(model_probit)
```

```
Call:
glm(formula = call ~ ethnicity + gender + quality, family = binomial(link = "probit"),
    data = ResumeNames)

Deviance Residuals:
    Min       1Q   Median       3Q      Max
-0.4757  -0.4363  -0.3871  -0.3525   2.4225

Coefficients:
              Estimate Std. Error z value Pr(>|z|)
(Intercept)   -1.39798    0.06642 -21.047  < 2e-16 ***
ethnicityafam -0.21685    0.05282  -4.105 4.04e-05 ***
genderfemale   0.06208    0.06336   0.980   0.3272
qualityhigh    0.09305    0.05252   1.772   0.0764 .
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 2726.9  on 4869  degrees of freedom
Residual deviance: 2705.8  on 4866  degrees of freedom
AIC: 2713.8

Number of Fisher Scoring iterations: 5
```

From the regression table we can see coefficient for **ethnicityafam** is **-0.21685** (which is little bit different compared to logit model) that means that if the applicant have african american sounding name then he is less likely to recieve call back.

```warning
We can not interpret magnitude from the regression table for **probit** model, only we can interpret the direction of the effect i.e. more likely or less likely get called back.
```


### Average marginal effects
To have meaningful interpretation of effects we can calculate average marginal effects.

#### Logit model

```R
marginal_logit <- mean(dlogis(predict(model_logit, type="link")))
marginal_logit * coef(model_logit)
```

```
(Intercept) -0.179439881066858    ethnicityafam -0.324139363996093  genderfemale  0.00940104037935758  qualityhigh  0.0141013274125201
```

Interpretation of marginal effect for variable **ethnicityafam** is
**-0.324139363996093**, which means if the person has african american sounding name, then he is 32% less likely to get call back from potential employer.

#### Probit model

```R
marginal_probit <- mean(dnorm(predict(model_probit, type="link")))
marginal_probit * coef(model_probit)
```

```
(Intercept) -0.207308146098111 ethnicityafam -0.0321574328415445 genderfemale 0.00920546735038312 qualityhigh 0.0137988149880605
```

Interpretation of marginal effect for variable **ethnicityafam** is
**-0.0321574328415445**, which means if the person has african american sounding name, then he is 32% less likely to get call back from potential employer.

```note
We can see that coefficient for logit and probit models could be quite different, but the average marginal effects are on contrary quite similliar.
```

### Multinomial logit model
If the outcome variable is categorical variable without inherent oreder(regular categorical), such as car manufacturers. The we need to use multinomial logit model.

#### Data source
Data is on penguins and their characterstics. There is three type of penguins: Adelie, Gentoo and Chinstrap.
Data were collected and made available by Dr. Kristen Gorman and the Palmer Station, Antarctica LTER, a member of the Long Term Ecological Research Network.

```R
library(nnet)
df <- read.csv('https://raw.githubusercontent.com/mwaskom/seaborn-data/master/penguins.csv')
head(df)
```

```R
multinom_logit <- multinom(species ~ bill_length_mm + flipper_length_mm + body_mass_g + sex, data = df)
summary(multinom_logit)
```

```
Call:
multinom(formula = species ~ bill_length_mm + flipper_length_mm +
    body_mass_g + sex, data = df)

Coefficients:
          (Intercept) bill_length_mm flipper_length_mm  body_mass_g sexFEMALE   sexMale
Chinstrap   -126.8121       3.884542        0.05522745 -0.013713867  1.140113   -9.134096
Gentoo      -190.0349       1.235787        0.59656936  0.005336206 -2.307075   -17.078332

Std. Errors:
          (Intercept) bill_length_mm flipper_length_mm body_mass_g  sexFEMALE   sexMALE
Chinstrap 0.031418912      1.0980540         0.1551344 0.006644753 0.06812109   0.03713893
Gentoo    0.007206881      0.9901455         0.2358709 0.006981574 0.08631697   0.03341686

Residual Deviance: 7.341373
AIC: 31.34137
```

These are the logit coefficients relative to the reference category. For example, under ‘body_mass_g’, the **0.006644753** suggests that
for one unit increase in ‘body_mass_g’ weight, the logit coefficient for ‘Chinstrap’ relative to ‘Adelie’ will go up by that amount, **0.006644753**.
In other words, if your ‘body_mass_g’ weight increases one unit, the chances of the penguin to be identified as 'Chinstrap' compared to the chances of being identified as 'Adelie' are higher.

```note
Multinom() function does not provide p-values. Either you can compute them customly, or you can use package stargazer, that computes p-values for you.
```

```R
library(stargazer)
stargazer(multinom_logit, type="text")
```


```
==============================================
                      Dependent variable:
                  ----------------------------
                    Chinstrap       Gentoo
                       (1)            (2)
----------------------------------------------
bill_length_mm       3.885***        1.236
                     (1.098)        (0.990)

flipper_length_mm     0.055         0.597**
                     (0.155)        (0.236)

body_mass_g          -0.014**        0.005
                     (0.007)        (0.007)

sexFEMALE            1.140***      -2.307***
                     (0.068)        (0.086)

sexMALE             -9.134***     -17.078***
                     (0.037)        (0.033)

Constant           -126.812***    -190.035***
                     (0.031)        (0.007)

----------------------------------------------
Akaike Inf. Crit.     31.341        31.341
==============================================
Note:              *p<0.1; **p<0.05; ***p<0.01
```

#### Relative risk ratios
Relative risk ratios allow an easier interpretation of the logit coefficients. They are the
exponentiated value of the logit coefficients.

```R
multinom_logit_coeff <- exp(coef(multinom_logit))
stargazer(multinom_logit, type="text", coef=list(multinom_logit_coeff))
```

```
==============================================
                      Dependent variable:
                  ----------------------------
                    Chinstrap       Gentoo
                       (1)            (2)
----------------------------------------------
bill_length_mm        48.645         3.441
                     (1.098)        (0.990)

flipper_length_mm    1.057***      1.816***
                     (0.155)        (0.236)

body_mass_g          0.986***      1.005***
                     (0.007)        (0.007)

sexFEMALE            3.127***      0.100***
                     (0.068)        (0.086)

sexMALE             0.0001***     0.00000***
                     (0.037)        (0.033)

Constant              0.000          0.000
                     (0.031)        (0.007)

----------------------------------------------
Akaike Inf. Crit.     31.341        31.341
==============================================
Note:              *p<0.1; **p<0.05; ***p<0.01
```

- If we look at the first row of the regression table, we can interpret it as following:
    - keeping all other variables constant, if *bill_length_mm* varaible increases one unit(cm), you are 48.645 times more likely to be identified as Chinstrap penguin as compared to the Adelie penguins. The coefficient, however, is not significant.
    - Keeping all other variables constant, if *bill_length_mm* varaible increases one unit(cm), you are 3.441 times more likely to be identified as Gentoo penguin as compared to the Adelie penguins. The coefficient, however, is not significant.


### Mutlinomial probit model


## Polynomial regression

In some cases, the true relationship between the outcome and a predictor variable might not be linear.

There are different solutions extending the linear regression model for capturing these nonlinear effects, including:

- Polynomial regression. This is the simple approach to model non-linear relationships. It add polynomial terms or quadratic terms (square, cubes, etc) to a regression.

- Spline regression. Fits a smooth curve with a series of polynomial segments. The values delimiting the spline segments are called Knots.

- Generalized additive models (GAM). Fits spline models with automated selection of knots.

We'll use Boston data set. The median house value (mdev), in Boston Suburbs. Variable lstat (percentage of lower status of the population).

```R
library(tidyverse)
data("Boston", package = "MASS")
head(Boston)
```



<table class="dataframe">
<caption>A data.frame: 6 × 14</caption>
<thead>
	<tr><th></th><th scope=col>crim</th><th scope=col>zn</th><th scope=col>indus</th><th scope=col>chas</th><th scope=col>nox</th><th scope=col>rm</th><th scope=col>age</th><th scope=col>dis</th><th scope=col>rad</th><th scope=col>tax</th><th scope=col>ptratio</th><th scope=col>black</th><th scope=col>lstat</th><th scope=col>medv</th></tr>
	<tr><th></th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row>1</th><td>0.00632</td><td>18</td><td>2.31</td><td>0</td><td>0.538</td><td>6.575</td><td>65.2</td><td>4.0900</td><td>1</td><td>296</td><td>15.3</td><td>396.90</td><td>4.98</td><td>24.0</td></tr>
	<tr><th scope=row>2</th><td>0.02731</td><td> 0</td><td>7.07</td><td>0</td><td>0.469</td><td>6.421</td><td>78.9</td><td>4.9671</td><td>2</td><td>242</td><td>17.8</td><td>396.90</td><td>9.14</td><td>21.6</td></tr>
	<tr><th scope=row>3</th><td>0.02729</td><td> 0</td><td>7.07</td><td>0</td><td>0.469</td><td>7.185</td><td>61.1</td><td>4.9671</td><td>2</td><td>242</td><td>17.8</td><td>392.83</td><td>4.03</td><td>34.7</td></tr>
	<tr><th scope=row>4</th><td>0.03237</td><td> 0</td><td>2.18</td><td>0</td><td>0.458</td><td>6.998</td><td>45.8</td><td>6.0622</td><td>3</td><td>222</td><td>18.7</td><td>394.63</td><td>2.94</td><td>33.4</td></tr>
	<tr><th scope=row>5</th><td>0.06905</td><td> 0</td><td>2.18</td><td>0</td><td>0.458</td><td>7.147</td><td>54.2</td><td>6.0622</td><td>3</td><td>222</td><td>18.7</td><td>396.90</td><td>5.33</td><td>36.2</td></tr>
	<tr><th scope=row>6</th><td>0.02985</td><td> 0</td><td>2.18</td><td>0</td><td>0.458</td><td>6.430</td><td>58.7</td><td>6.0622</td><td>3</td><td>222</td><td>18.7</td><td>394.12</td><td>5.21</td><td>28.7</td></tr>
</tbody>
</table>


```R
ggplot(Boston, aes(lstat, medv) ) +
  geom_point() +
  geom_smooth(method='lm')
```

![png]({{site.baseurl}}/assets/images/pol_regression.png)

```R
model <- lm(medv ~ lstat, data = Boston)
summary(model)
```
```
Call:
lm(formula = medv ~ lstat, data = Boston)

Residuals:
    Min      1Q  Median      3Q     Max
-15.168  -3.990  -1.318   2.034  24.500

Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept) 34.55384    0.56263   61.41   <2e-16 ***
lstat       -0.95005    0.03873  -24.53   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 6.216 on 504 degrees of freedom
Multiple R-squared:  0.5441,	Adjusted R-squared:  0.5432
F-statistic: 601.6 on 1 and 504 DF,  p-value: < 2.2e-16
```

The polynomial regression adds polynomial or quadratic terms to the regression equation as follow:

$$medv = b0 + b1*lstat + b2*lstat^2$$

```R
model_pol <- lm(medv ~ lstat + I(lstat^2), data = Boston)
summary(model_pol)
```

```
Call:
lm(formula = medv ~ lstat + I(lstat^2), data = Boston)

Residuals:
     Min       1Q   Median       3Q      Max
-15.2834  -3.8313  -0.5295   2.3095  25.4148

Coefficients:
             Estimate Std. Error t value Pr(>|t|)
(Intercept) 42.862007   0.872084   49.15   <2e-16 ***
lstat       -2.332821   0.123803  -18.84   <2e-16 ***
I(lstat^2)   0.043547   0.003745   11.63   <2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 5.524 on 503 degrees of freedom
Multiple R-squared:  0.6407,	Adjusted R-squared:  0.6393
F-statistic: 448.5 on 2 and 503 DF,  p-value: < 2.2e-16
```

```R
model_pol6 <- lm(medv ~ poly(lstat, 6, raw = TRUE), data = Boston)
summary(model_pol6)
```

```
Call:
lm(formula = medv ~ poly(lstat, 6, raw = TRUE), data = Boston)

Residuals:
     Min       1Q   Median       3Q      Max
-14.7317  -3.1571  -0.6941   2.0756  26.8994

Coefficients:
                              Estimate Std. Error t value Pr(>|t|)
(Intercept)                  7.304e+01  5.593e+00  13.059  < 2e-16 ***
poly(lstat, 6, raw = TRUE)1 -1.517e+01  2.965e+00  -5.115 4.49e-07 ***
poly(lstat, 6, raw = TRUE)2  1.930e+00  5.713e-01   3.378 0.000788 ***
poly(lstat, 6, raw = TRUE)3 -1.307e-01  5.202e-02  -2.513 0.012295 *
poly(lstat, 6, raw = TRUE)4  4.686e-03  2.407e-03   1.947 0.052066 .
poly(lstat, 6, raw = TRUE)5 -8.416e-05  5.450e-05  -1.544 0.123186
poly(lstat, 6, raw = TRUE)6  5.974e-07  4.783e-07   1.249 0.212313
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 5.212 on 499 degrees of freedom
Multiple R-squared:  0.6827,	Adjusted R-squared:  0.6789
F-statistic: 178.9 on 6 and 499 DF,  p-value: < 2.2e-16
```

```R
ggplot(Boston, aes(lstat, medv) ) +
  geom_point() +
  geom_smooth(method = lm, formula = y ~ poly(x, 4, raw = TRUE))
```

![polynomial regression 4th power]({{site.baseurl}}/assets/images/pol_regression_1.png)


## Quantile regression

Quantile regression is an extension of linear regression used when the conditions of linear regression are not met.
One advantage of quantile regression relative to ordinary least squares regression is that the quantile regression estimates are more robust against outliers in the response measurements.

```warning
For quantile regression to be feasible, dependent variable should have not many zeros or repeated values
```


