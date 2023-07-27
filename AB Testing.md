## Can and can't do with A/B testing

Need clear control and experiment group

Cannot take too long e.g. cannot AB testing on website selling cars because it takes too long 

Change aversion: old users may resist against the new version e.g. cannot AB testing on updating brand because users require time to get used to it

Novelty effect: old users may all go for the new experience, then the test set has everything

Other techniques: user log, user experience research (qualitative data)

## Overview Example

e.g. Online finance course website

Customer funnel: visit homepage -- explore site -- create account -- complete

Hypothesis: change button from orange to pink will increase how many students explore courses

Metric: 

- Total number of course completed: no, take too much time

- Number of clicks: no, number vs proportion

- Click through rate = number of clicks / number of page views, measure usability

- Click through probability = unique visitors who click / unique visitors to page, measure total impact

Updated hypothesis: change button from orange to pink will increase the click through probability of the button

## Significance

**Binomial distribution**

2 types of outcome

Independent events

Identical distribution, same p for all

Mean = p

Std dev = $\sqrt{\frac{p(1-p)}{N}}$

**Confidence interval**

$\hat{p} = \frac{X}{N}$

X: number of users who clicked

N: number of users

To use normal: check $N*\hat{p} > 5$ and $N*(1-\hat{p}) > 5$

$m = z * SE = z * \sqrt{\frac{\hat{p}(1-\hat{p})}{N}}$

m: margin of error, add and minus mean to find the bound

[z-score table](https://www2.math.upenn.edu/~chhays/zscoretable.pdf): use chart values (equals area below the curve) to find z-score

**Hypothesis testing**

Null hypothesis ($H_0$): $P(cont) - P(exp) = 0$

Alternative hypothesis ($H_A$): $P(cont) - P(exp) \neq 0$

Measure $\hat{P(cont)}$ and $\hat{P(exp)}$

Calculate $p-value = P(\hat{P(exp)} - \hat{P(cont)} | H_0) < 0.05$, reject null hypothesis

**Pooled standard error**

$\hat{p_{pool}} = \frac{X_{cont} + X_{exp}}{N_{cont} + N_{exp}}$

$SE_{pool} = \sqrt{\hat{p_{pool}} * (1-\hat{p_{pool}}) * (\frac{1}{N_{cont}} + \frac{1}{N_{exp}})}$

$\hat{d} = \hat{p_{exp}} - \hat{p_{cont}}$

$H_0: d = 0$

$\hat{d} \sim N(0, SE_{pool})$

If $\hat{d} > 1.96 * SE_{pool}$ or $\hat{d} < -1.96 * SE_{pool}$, reject null

**Practical significant**

Practical significant: lower, like 2%

Statistical power: how many are needed to give a significant result

Power and size tradeoff: smaller change to detect, larger experiment

Whole confidence interval above practical significant: launch

Whole confidence interval below practical significant: do not launch

Some part of confidence interval above practical significant: additional test

**Size**

$\alpha$ = P(reject null | null true)

$\beta$ = P(fail to reject | null false)

$1-\beta$ = sensitivity, usually 80%

Small sample: low $\alpha$, high $\beta$ 

Larger sample: same $\alpha$, lower $\beta$ 

[Sample size calculator](https://www.evanmiller.org/ab-testing/sample-size.html)


## Ethics

Risk: whether the risk exceeds the minimum risk

Benefit: how might the result help

Choice: what other choice do participants have, fewer alternative, more coercion

Privacy: what data is being collected, and what is the expectation of privacy and confidentiality


## Metric

**High level metrics**

Homepage visit: # users who visit homepage

Explore site: # users who view the course list, # users who view course details

Create account: # users who create accounts, # users who enroll in a course, # users who sign up for coaching

Complete: # users who enroll in a second course, # users who get jobs

**Difficult metrics**

- Don't have access to data

- Take too long

**Gather additional data**

- External data: companies that collect granular data, companies that run survey, academic research

- Observational analysis: show correlation not causation

- Discuss with others, company culture

- User Experience Research (UER): good for brainstorming, can use special equipment, need to validate result

- Focus group: bring users together, risk of group think

- Surveys: useful for metric that cannot collect directly, can not directly compare to other results

<img width="400" src="https://user-images.githubusercontent.com/76275089/170893575-db95315e-e070-41b4-8d90-5ae0e68018be.png">

e.g. 

Homepage visits: compare with external data

Course completion: UER to investigate low completion, compare with external data

Jobs: surveys

**Define metric**

High level metric: click through probability = # users who click / # users who visit

Def 1: for each time interval, # cookies that click / # cookies

Def 2: # pageviews with click within time interval / # pageviews

Def 3: # clicks / # pageviews

**Filter**

External: clicking on everything, people come to see the new feature, identity spam and fraud

Internal: only impact a subset e.g. only on mobile app, only English

Week over week / year over year plot: smooth out regular changes

**Summary metrics**

- Sums and counts

- Mean, median, percentile

- Probability and rate

- Ratios


### Invariant checking

Are the population the same?

### Evaluation

High level business metric: revenue, market share

Detailed metric: user experience, may to difficult to evaluate


## Sensitivity and robustness

Sensitive to changes, not be affected by some observations

Simple experiment and check the metric

A versus A experiment, compare people who see the same thing

Log and history

## Variability

Start with absolute difference

Calculate percentage change

<img width="759" alt="image" src="https://user-images.githubusercontent.com/76275089/171098404-4eb9ca7c-8d71-470c-9ffa-3986f43dc2ae.png">

## Nonparametric method

Model without make assumptions

Sign test: collect data positive or negative, use binomial

## Empirical variability

Perform AA tests: 

- Compare results to what you expect

- Estimate variance and calculate confidence

- Directly estimate confidence interval

Directly estimate confidence interval: select middle 95%, remove first and last 2.5%

Bootstrap: run one AA test, random sample from each side, use as a simulated experiment, repeat to get many experiments

## Design A/B testing

Unit of diversion

- User id(account): stable, unchanging, personally identifiable

- Anoymous(cookie): specific to browser and device, users can clear cookie

- Event: no consistent experience, only for ones that are not visible user experience

- Device id: for mobile device

- IP address

Consideration

- Consistency: user visibility, measurement

- Ethical considerations: can data identify user, user consent

- Variability: when unit of analysis = unit of diversion, variability tends to be lower and closer to analytical estimate

Unit of analysis: the denominator of the proability

## Population vs Cohort

Cohort: people who enter the experiment at the same time

- Look for learning effects

- Examining user retention

- Want to increase user activity

- Anything requiring users to be established

## Size

Reduce size

- Increase dmin, alpha, beta

- Change unit of diversion to be the same as unit of analysis

- Target experiment to specific traffic

Don't know the fraction: run a pilot experiment or observe the data for first several days

## Duration vs Exposure

Account for variability: long to account for changes between weekday and weekend

Risky or not

Learning effect: whether user adopt to the change, need time

Choose unit of diversion correctly

Dosage, use cohort instead of population

Pre-period and post-period AA test: difference is learning effect

## Sanity checks

- Population sizing method: check experiment population and control population are comparable

- Invariance check: some matrics should not change during the experiment, e.g. population sizing (# events, ccokies, users)

<img width="1914" alt="image" src="https://user-images.githubusercontent.com/76275089/172026159-1a61263c-2999-40ee-9ec9-e43c4f935d74.png">

Look into day by day data

Do not move forward if does not pass sanity check

Common reason: data capture

## Single metric

<img width="1850" alt="image" src="https://user-images.githubusercontent.com/76275089/172026948-428ca511-7bb1-4407-9276-e07d022a91d1.png">

Mistake: 0.0020 should be 0.0220

[Sign test](https://www.graphpad.com/quickcalcs/binomial1.cfm): count number of success, check p-value

Sign test has lower power

Separate weekday and weekend

Simpson's paradox: click through rate is higher for experiment for both groups, but the overall click through rate is lower for experiment

There are different number of users from each group

## Multiple metric

Probability of any false positive increases as you increase number of metrics

Need to use higher confidence level for each metric

Method 1: assume independence

overall = 1 - (1 - individual)^n

Method 2: Bonderroni correction

Garanteed to give overall at least as small as specified

individual = overall / n

Different strategies

- Control probability that any metric shows a false positive -- familywise error rate (FWER)

- Control false discovery rate (FDR) FDR = E[# false positives / # rejections]

Launch or not

- Do I have statistical significant and pratical significant result to launch the change?

- Do I understand what does this change do to user experience?

- Is this change worth it?

Changes over time: seasonality changes

Solution: hold back a small group of people, compare the result




