HW2
================
Zhuodiao Kuang
2023-09-30

# Problem 1

#### a) What is the probability that exactly 40 of these individuals will have at least one dental checkup?

Let X denote an individual in the study.

Let Y denote the number of individuals who will have at least one dental
checkup during a 2-year period.

$$X \sim Bernoulli(0.73) $$

$$Y \sim Bin(56, 0.73), n=56, p=0.73$$

$$P(Y = 40) = \frac{56!}{40!16!}(0.73)^{40}(0.27)^{16}$$
$$ \approx 0.1133$$

#### b) What is the probability that at least 40 of these individuals will have at least one dental checkup?

Let X denote an individual in the study.

Let Y denote the number of individuals who will have at least one dental
checkup during a 2-year period.

$$P(Y \ge 40) =\Sigma_{y=40}^{56} \frac{56!}{y!(56-y)!}(0.73)^{y}(0.27)^{1-y}$$

``` r
P=0
for (y in 40:56) {
  P = P + choose(56,y)*(0.73)^y*(0.27)^(56-y)
}
P
```

    ## [1] 0.6678734

So, the probability is about 0.6678.

#### c) Could you use an approximation method to calculate the probabilities above? If yes, calculate the probabilities using approximations and compare to exact values; otherwise, explain why approximation methods are not appropriate.

Approximation methods are not appropriate. we cam only use the Poisson
distribution to approximate the binomial distribution under certain
conditions, where $\lambda = np$. 1. n must be large(\>100) 2.
Probability of success, p, should be small(p\<0.01)

But this problem doesn’t satisfy these conditions.

#### d) How many individuals do you expect to have at least one dental checkup?

$$E(Y) = np = 56*0.73 = 40.88$$ So, I expect 41 individuals to have at
least one dental checkup.

#### e) What is the standard deviation of the number of individuals who will have at least one dental checkup?

$$Var(Y) = np(1-p) = 56*0.73*0.27 = 11.0376$$
$$std(Y) = \sqrt{Var(Y)} = 3.322$$

So, the standard deviation of the number of individuals who will have at
least one dental checkup is 3.322.

# Problem 2

#### a) What is the probability of having fewer than 3 tornadoes in the United States next year?

The probability distribution of a Poisson random variable
$X \sim Poi(6)$ is denoted by:

$$P(X=x) = f(x) = \frac{6^xe^{-6}}{x!}, x=0,1,2,...$$ Calculate:
$$P(X < 3 ) = \Sigma_{x=0}^2\frac{6^xe^{-6}}{x!} $$

$$= \frac{6^0e^{-6}}{0!}+\frac{6^1e^{-6}}{1!}+\frac{6^2e^{-6}}{2!}$$

$$=25e^{-6} \approx 0.062$$

#### b) What is the probability of having exactly 3 tornadoes in the United States next year?

Calculate: $$P(X = 3 ) = \frac{6^3e^{-6}}{3!} $$

$$=36e^{-6} \approx 0.089$$

#### c) What is the probability of having more than 3 tornadoes in the United States next year?

$$P(X>3) = 1-P(X \le 3) =1 - 61e^{-6} \approx 0.8488$$
