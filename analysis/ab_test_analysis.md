
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
