
# A/B Test Analysis: Checkout Simplification

## 1. Sample Size Calculation

Before running the experiment, we need to determine how many users are required in each group.

The sample size depends on four main parameters:

* **Baseline conversion rate:** 10%
* **Minimum Detectable Effect (MDE):** 1 percentage point
* **Significance level (α):** 0.05
* **Statistical power:** 80%

### Experiment Assumptions

| Parameter                          |              Value |
| ---------------------------------- | -----------------: |
| Baseline conversion rate           |                10% |
| Expected Treatment conversion rate |                11% |
| MDE                                | 1 percentage point |
| Significance level (α)             |               0.05 |
| Confidence level                   |                95% |
| Statistical power                  |                80% |

The experiment is designed to detect an increase from **10% to 11% conversion rate**.

A two-sided hypothesis test will be used, with a significance level of 5% and statistical power of 80%.


### Sample Size Formula

For a two-proportion A/B test, the required sample size per group can be estimated using:

$$
n =
\frac{
\left[
Z_{\alpha/2}\sqrt{2\bar{p}(1-\bar{p})}
+
Z_{\beta}\sqrt{p_A(1-p_A)+p_B(1-p_B)}
\right]^2
}
{(p_B-p_A)^2}
$$


Where:

Control conversion rate:

$$
p_A = 0.10
$$

Expected Treatment conversion rate:

$$
p_B = 0.11
$$

Average conversion rate:

$$
\bar{p} = 0.105
$$

Critical value for a 95% confidence level in a two-sided test:

$$
Z_{\alpha/2} = 1.96
$$

Critical value for 80% statistical power:

$$
Z_{\beta} = 0.84
$$

Using these values, the required sample size is approximately **14,700 users per group**, or approximately **29,400 users in total**.

A relatively small MDE of 1 percentage point requires a relatively large sample to detect the difference with 95% confidence and 80% statistical power.


## 2. Experiment Duration

The experiment should run long enough to reach the required sample size while capturing normal variations in user behavior.

For this case study, we assume a minimum test duration of **2 weeks**. This allows the experiment to cover multiple weekday and weekend cycles and reduces the risk of drawing conclusions from short-term fluctuations.

The experiment should not be stopped early simply because statistical significance is reached. The predefined sample size and test duration should be respected to reduce the risk of false-positive conclusions.


## 3. Experiment Results

After reaching the required sample size, we observe the following results:

| Group         |  Users | Purchases | Conversion Rate |
| ------------- | -----: | --------: | --------------: |
| Control (A)   | 14,700 |     1,470 |           10.0% |
| Treatment (B) | 14,700 |     1,617 |           11.0% |

### Conversion Rate

Conversion rate is calculated as:

$$
Conversion\ Rate = \frac{Purchases}{Users}
$$

For the Control group:

$$
\frac{1470}{14700} = 0.10
$$

Conversion rate = **10.0%**

For the Treatment group:

$$
\frac{1617}{14700} = 0.11
$$

Conversion rate = **11.0%**

### Absolute Lift

The absolute lift is the difference between the two conversion rates:

$$
11.0 - 10.0 = 1.0
$$

Absolute lift = **1.0 percentage point**

### Relative Lift

The relative lift measures the percentage increase compared with the Control group:

$$
\frac{11.0 - 10.0}{10.0} = 0.10
$$

Relative lift = **10%**

### Summary

The Treatment group increased conversion from **10.0% to 11.0%**.

This represents:

* **1.0 percentage point absolute lift**
* **10% relative lift**

## 4. Statistical Significance

The observed difference in conversion rates may be caused by random variation. To determine whether the difference is statistically significant, we use a **two-proportion z-test**.

### Hypotheses

**Null Hypothesis (H₀):**

There is no difference in conversion rates between the Control and Treatment groups.

**Alternative Hypothesis (H₁):**

There is a difference in conversion rates between the Control and Treatment groups.

### Pooled Conversion Rate

Under the null hypothesis, we assume that both groups have the same underlying conversion rate.

$$
\hat{p} =
\frac{1470 + 1617}
{14700 + 14700}
= 0.105
$$

### Standard Error

The standard error is calculated as:

$$
SE =
\sqrt{
\hat{p}(1-\hat{p})
\left(
\frac{1}{n_A}+\frac{1}{n_B}
\right)
}
$$

Using the observed data:

$$
SE \approx 0.003576
$$

### Z-Statistic

The z-statistic is calculated as:

$$
z =
\frac{p_B-p_A}{SE}
$$

$$
z =
\frac{0.11-0.10}{0.003576}
\approx 2.80
$$

### P-Value

Because this is a two-sided test, the probability of observing a z-statistic at least as extreme as 2.80 in either direction is approximately:

$$
p\text{-value} \approx 0.0052
$$

Since:

$$
0.0052 < 0.05
$$

we reject the null hypothesis.

### Interpretation

The difference in conversion rates is **statistically significant at the 5% significance level**.

The Treatment group increased conversion from **10.0% to 11.0%**, and the observed difference is unlikely to be explained by random variation alone.

## 5. Conclusion

We found:

$$
p = 0.0052
$$

and:

$$
\alpha = 0.05
$$

Since:

$$
p < \alpha
$$

we **reject the null hypothesis**.

Therefore, there is **statistically significant evidence of a difference between the two groups**.

In an A/B test, this means the observed difference between the control and treatment groups is unlikely to be explained by random variation alone.

> **Conclusion:** The experiment result is statistically significant at the 5% significance level.



## 6. Practical Significance / Business Impact

Statistical significance tells us whether the observed difference is unlikely to be explained by random variation alone.

However, statistical significance does not tell us whether the difference is large enough to matter for the business.

Therefore, we also need to evaluate the **effect size**.

### Absolute Lift

The absolute difference in conversion rate is:

```math
Absolute\ Lift = Conversion_B - Conversion_A
```

### Relative Lift

Relative lift measures the improvement compared with the Control group:

```math
Relative\ Lift =
\frac{Conversion_B - Conversion_A}{Conversion_A}
```

The relative lift helps us understand the size of the improvement compared with the original conversion rate.

### Business Impact

We should also consider:

* How many additional purchases does the improvement generate?
* What is the additional revenue?
* What is the implementation cost?
* Is the improvement large enough to justify the change?
* Does the treatment negatively affect other important metrics?

> Statistical significance tells us whether the difference is likely real. Practical significance tells us whether the difference is large enough to matter.


## 7. Confidence Interval

A confidence interval gives us a range of plausible values for the true difference between the Control and Treatment groups.

For a difference in conversion rates:

```math
Difference = p_B - p_A
```

A 95% confidence interval can be calculated as:

```math
Difference
\pm
Z_{\alpha/2} \times SE
```

For a 95% confidence level:

```math
Z_{\alpha/2} = 1.96
```

The confidence interval helps us understand both the **estimated effect** and the **uncertainty around that estimate**.

### Interpretation

If the 95% confidence interval does not include zero, the result is consistent with a statistically significant difference at the 5% significance level.

The final confidence interval should be calculated using the actual Control and Treatment results from the experiment.

> The p-value helps us evaluate statistical significance, while the confidence interval helps us understand the likely size and precision of the effect.


## 8. Guardrail Metrics

Conversion rate is the primary metric, but increasing conversion should not negatively affect other important business outcomes.

We therefore evaluate the following guardrail metrics:

### Average Order Value (AOV)

We check whether the Treatment group changes the average value of completed orders.

```math
AOV =
\frac{Total\ Revenue}{Number\ of\ Orders}
```

### Payment Failure Rate

We check whether the simplified checkout affects payment success.

```math
Payment\ Failure\ Rate =
\frac{Failed\ Payments}{Payment\ Attempts}
```

### Cancellation Rate

We check whether the Treatment group produces more cancellations.

```math
Cancellation\ Rate =
\frac{Cancelled\ Orders}{Total\ Orders}
```

### Refund Rate

We also monitor whether the Treatment group results in more refunds.

```math
Refund\ Rate =
\frac{Refunded\ Orders}{Total\ Orders}
```

### Guardrail Interpretation

The treatment should not be evaluated based on conversion alone.

If conversion improves but important guardrail metrics deteriorate, we need to investigate the potential trade-off before considering a full rollout.


## 9. Business Recommendation

The experiment provides statistically significant evidence that the Treatment affects purchase conversion.

However, statistical significance alone is not sufficient to recommend a full rollout.

The final decision should consider:

1. The size of the conversion improvement.
2. The confidence interval around the estimated effect.
3. The impact on AOV.
4. Payment failure rate.
5. Cancellation rate.
6. Refund rate.
7. Additional revenue generated.
8. Implementation and operational costs.

If the conversion improvement is both **statistically significant and practically meaningful**, and the guardrail metrics do not show material negative effects, the company can consider rolling out the simplified checkout experience.

> **Final conclusion:** *The experiment provides statistically significant evidence of an effect on conversion. The business impact and guardrail metrics should be evaluated before making a final rollout decision.*
