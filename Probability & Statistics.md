# Statistics

<img width="400" alt="image" src="https://github.com/zhiweigu2000/Job-finding/assets/76275089/978d3fd1-acd9-4b83-8360-2074e4266616">

t distribution vs normal distribution

<img width="400" alt="image" src="https://github.com/zhiweigu2000/Job-finding/assets/76275089/0904bb78-7775-4259-9fa1-a089a635c087">

Degree of freedom: number of pieces of info that can vary without violating restrictions

Number of pieces of independent info to estimate others

---
# Probability

Conditional probability: $P(A|B) = \frac{P(AB)}{P(B)}$

Independent: $P(AB) = P(A)* P(B)$


## Expectation

Expectation: 

Average of 
possible values of X, weighted by their probabilities 

$E(X) = \displaystyle\sum_{all x} xP(X=x)$

$E[g(x)] = \displaystyle\sum_{all x} g(x)P(X=x)$

$E(aX+b) = aE(X) + b$

$E(X+Y) = E(X) + E(Y)$

When X, Y independent, $E(XY) = E(X) * E(Y)$, $Var(X+Y) = Var(X) + Var(Y)$

Indicator: 

$E(I_A) = P(A)$, $E(X) = P(I_1) + P(I_2) + ...$

Tail sum formula: 

For X with possible values {0, 1, ..., n}, $E(X) = \displaystyle\sum_{j=1}^{n} P(X \geq j)$

e.g. Four dices are rolled. Let M be the minimum number rolled, find E(M)

$E(M) = P(M \geq 1) + P(M \geq 2) + P(M \geq 3) + P(M \geq 4) + P(M \geq 5) + P(M \geq 6)$

$=\left(\frac{6}{6}\right)^4 + \left(\frac{5}{6}\right)^4 + \left(\frac{4}{6}\right)^4 + \left(\frac{3}{6}\right)^4 + \left(\frac{2}{6}\right)^4 + \left(\frac{1}{6}\right)^4$

Markov's inequality:

If X > 0, then $P(X \geq a) \leq \frac{E(X)}{a}$ for every a > 0


## Standard deviation

Variance:

Mean squared deviation of X from its expected value 

$Var(X) = E[(X-\mu)^2]$

$SD(X) = \sqrt{Var(X)}$

$Var(X) = E(X^2) - (E(X))^2$

$Var(aX+b) = a^2Var(X)$

Standardization: 

$X' = \frac{X - E(X)}{SD(X)}$, $E(X') = 0$, $SD(X') = 1$

$P(X <= b) = P(X' <= \frac{b-E(X)}{SD(X)})$

Chebychev's inequality:

$P[|X-E(X)| \geq kSD(X)] \leq \frac{1}{k^2}$

The probability that a random variable differs from its expected value by more than k sd is at most $1/k^2$

Central Limit Theorem:

$S_n = X_1 + .. + X_n$

For large n, the distribution of $S_n$ is approximately normal, with mean $E(S_n) = n\mu$ and standard deviation $SD(S_n) = \sigma\sqrt{n}$

$P(a \leq \frac{S_n - n\mu}{\sigma\sqrt{n}} \leq b) \approx \Phi(b) - \Phi(a)$, $\Phi$ is cdf


## Uniform distribution

$f(x) = \frac{1}{b - a}$ for $a < x < b$

$E(X) = \frac{a + b}{2}$

$Var(X) = \frac{(b - a) ^ 2}{12}$


## Binomial distribution 

k successes in n trails: $\binom{n}{k} p^k q^{n-k}$

$\binom{n}{k} = \frac{n!}{k!(n-k)!}$

$E(X) = np$

$Var(X) = np(1 - p)$


## Normal distribution

$y = \frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{1}{2}(x-\mu)^2 / \sigma^2}$

Normal approximation to binomial distribution:

For n independent trails with success probability p

$P(a \leq X \leq b) = P(a - \frac{1}{2} < X < b + \frac{1}{2}) \approx \Phi(\frac{b + \frac{1}{2} - \mu}{\sigma}) - \Phi(\frac{a - \frac{1}{2} - \mu}{\sigma})$

Confidence interval: $\hat{p} \pm 2/\sqrt{n}$

Sum of independent normal variables: 

If $X$ and $Y$ are independent with normal $(\lambda, \sigma^2)$ and normal $(\mu, \tau^2)$ distributions, then $X+Y$ has normal $(\lambda+\mu, \sigma^2+\tau^2)$ distirbution. 

$\Phi(-z) = 1 - \Phi(z)$

$\Phi(-z, z) = 2\Phi(z)-1$

$\Phi(-1, 1) = 68%$

$\Phi(-2, 2) = 95%$

$\Phi(-3, 3) = 99.7%$

$P(c < X < d) = P(a < Z < b) = \Phi(b) - \Phi(a)$ where $a = (c-\mu)/\sigma$, $Z = (X-\mu)/\sigma$, $d = (b-\mu)/\sigma$


## Possion distribution

Binomial distribution when p is nearly 0, n closes to infinite

$P(k) = e^{-\mu}\frac{\mu^k}{k!}$

$E(X) = \mu$

$Var(X) = \mu$

If $N_1, ..., N_j$ are independent Poisson random variables with parameter $\mu_1, ..., \mu_j$, then  $N_1 + ... + N_j$ is a independent Poisson random variable with parameter $\mu_1 + ... + \mu_j$


## Geometric distribution

X times to reach one success, X - 1 failures before success

$P(n) = P(T=n) = (1-p)^{n-1}p$

$E(T) = 1/p$

$SD(T) = \sqrt{1-p} / p$

Distribution of waiting times


## Conditional expectation

$P(X=x, Y=y) = P(X=x)P(Y=y|X=x)$

$E(X+Y|A) = E(X|A) + E(Y|A)$

Rule of average conditional expectation $E(Y) = \displaystyle\sum_{all x} E(Y|X=x)P(X=x)$

$E(Y) = E[E(Y|X)]$


## Covariance and correlation

$Cov(X, Y) = E[(X-E(X))(Y-E(Y))] = E(XY) - E(X)E(Y)$

$Var(X+Y) = Var(X) + Var(Y) + 2Cov(X, Y)$

$Cov(X, X) = Var(X)$

$Corr(X, Y) = \frac{Cov(X, Y)}{SD(X)SD(Y)}$

$-1\leq Corr(X, Y)\leq1$

Uncorrelated: $Corr(X, Y) = 0$, $Cov(X, Y) = 0$

Independent variables are uncorrelated, uncorrelated variables are not necessarily independent

----


## Exponential distribution

Distribution for decay

Exponential distribution is a continuous analog to geometric distribution

$f(t) = \lambda e^{-\lambda t}$

$P(a < T \leq b) = \int_a^b \lambda e^{-\lambda t} dt = e^{-\lambda a} - e^{-\lambda b}$

Exponential function survival function: 

$P(T>t) =  e^{-\lambda t}$

$E(T) = SD(T) = \frac{1}{\lambda}$

Memoryless property: given survival to time t, the chance of surviving a further time s is the same as the chance of surviving to time s in the first place

$P(T > t+s | T>t) = P(T>s)$

![image](https://user-images.githubusercontent.com/76275089/127178761-a9e503a7-eb64-45c1-9118-f7c9c2c8c2cc.png)


## Gamma distribution

![image](https://user-images.githubusercontent.com/76275089/127178807-2493408f-2c06-4b22-aa67-94a1958ff468.png)

$R_n^2 = Z_1^2 + Z_2^2 + ... + Z_n^2$ is $gamma(n/2, 1/2)$


## Beta distribution

![image](https://user-images.githubusercontent.com/76275089/127180798-25d5a198-a0d3-4d5f-8fd4-88eddfb67c23.png)

E(X) = r/(r + s)

The kth order statistics of n independent uniform (0, 1) random variables has beta(k, n - k + 1) distribution


## Rayleigh distribution

![image](https://user-images.githubusercontent.com/76275089/128637772-de825949-5e83-4d9f-82c1-6911ef5aebe0.png)


## Bivariate normal distribution

![image](https://user-images.githubusercontent.com/76275089/128687341-18c2bc1d-91f2-43aa-aa12-3f29dd2fac3f.png)

![image](https://user-images.githubusercontent.com/76275089/128687484-215d24ef-87de-4aa2-aee9-194ffa9095c0.png)


## Change of variable

One-to-one change of variable for densities:

$f_Y(y) = f_X(x) / |\frac{dy}{dx}|$ where $y = g(x)$

![image](https://user-images.githubusercontent.com/76275089/128604763-c70e1e67-5e0f-4d7a-9c33-5c9b3cb635f3.png)


## Cumulative distribution function

A probability distribution over the line is completely determined by its cdf

Fmax(x) = F1(x)F2(x)...Fn(x)

Fmin(x) = 1 - (1-F1(x))(1-F2(x))...(1-Fn(x))


## Kth order statistics

![image](https://user-images.githubusercontent.com/76275089/128604686-2ff06475-01bf-46f8-97d3-0e414df65c9b.png)


## Joint distribution

![image](https://user-images.githubusercontent.com/76275089/128637235-396964d3-5f9b-4034-be55-1264db42c413.png)

Margins 

![image](https://user-images.githubusercontent.com/76275089/128637168-fa06b671-d912-4651-a837-2d9210bc77ba.png)

Independence: f(x, y) = fx(x)fy(y)  
























