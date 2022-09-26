---
sort: 10
---

# Fisher test
Use of Fisher exact test increased lately in addition to the standard classical statiscal measures.
Fisher introduced the notion of Randomized Control Trials.
He was thinking about agricultrue. Let say, Fisher had 50 different fields, where you can do different type of treatments, or in other words use different type of fertilizers. He was interested in the impact of those 50 fields. He was not interested in drawing conclusion for the all fields in that region, or in other words, he was not interested in general population, by only interested in his sample.

Usually, in statistics when you do analysis, you want to draw general conclusion about your population, for that you randomly sample observation from your population to draw statistical conclusion, about your population. But for Fisher, he was only interested in the sample.

```note
Even if you have entire population, there is uncertainty.Uncertainty from the Fisher test comes from the fact, that experimenter could decide to what observation in the sample assign treatment. 
```
Fisher was interested in the sharp Null hypothesis:
$$H_0 : Y_i(0) = Y_i(1)$$ for all $$i$$
Is that treatment is 0 for everybody. Note that it is not the same as the average treatment effect being 0, because it could well be that the treatment effect is 0 for nobody, but the average is still 0. 

For example, if half the class has a treatment effect
of plus 10 and half the class has a treatment
effect of minus 10, then the average treatment effect is 0,
but the treatment effect is 0 for nobody.


The sharp null allows us to determine for each unit the
counterfactual under $H_o$.

The beauty of it is that we can calculate, for any test
statistics we are interested in, the probability of the observed
value under the sharp null

So, suppose we choose as our statistic the absolute difference
in means by treatment status:

$$|T^{ave}(W, Y^{obs})| = | \bar{Y_t^{obs} - \bar{Y_c^{obs}}} $$

We can calculate the probability, over the randomization
distribution, of the statistic taking on a value as large, in
absolute value, as the actual value given the actual treatment
assigned.

This calculation gives us the p-value for this particular null
hypothesis:
$$ p = Pr(|T^{ave}(W, Y^{obs})|) \beq |T^{ave}(W^{obs}, Y^{obs})|


A randomized study where children were given honey or
nothing.
- Main outcome: cough severity the night after the assignment
(from 1 to 6)
- Imbens and Rubin (2015) use it to illustrate Fisher exact test
- First, assume we have the data for the first 6 children

| Unit | Potential $$Y_i(0)$$  Outcomes $$Y_i(1)$$

## Kolmogorov-Smirnov Test

In analyzing RCT, we have seen how to test the sharp null,
and how to test the hypothesis that the treatment has zero
effect on average.
We may also be interested in testing the hypothesis that the
distribution of $$Y (1)$$ and $$Y (0)$$ are different.
Kolmogorov-Smirnov statistic. let $$X_1, .., X_n$$ be a random
sample, with CDF F and $$Y_1, .., Y_m$ be a random sample, with
CDF G
• We are interested in testing the hypothesis
$$H_o : F = G$$
against
$$H_a : F = G$$

