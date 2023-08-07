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

**Sensitivity and robustness**

Sensitive to changes, not be affected by some observations

Simple experiment (make a small change) and check the metric

A versus A experiment, compare people who see the same thing

Log and history

**Variability**

Start with absolute difference

Calculate percentage change

<img width="759" alt="image" src="https://user-images.githubusercontent.com/76275089/171098404-4eb9ca7c-8d71-470c-9ffa-3986f43dc2ae.png">

**Nonparametric method**

Model without make assumptions

Sign test: collect data positive or negative, use binomial

**Empirical variability**

Perform AA tests: 

- Compare results to what you expect (sanity check)

- Estimate variance and calculate confidence

- Directly estimate confidence interval

Bootstrap: run one AA test, random sample from each side, use as a simulated experiment, repeat to get many experiments

Empirical confidence interval (directly estimate confidence interval) : select middle 95%, remove first and last 2.5%

Analytical: calculate standard deviation, multiply z-score


## Design A/B testing

**Unit of diversion**

- User id(account): stable, unchanging, personally identifiable

- Anoymous(cookie): specific to browser and device, users can clear cookie

- Event: no consistent experience, only for ones that are not visible user experience

- Device id: for mobile device

- IP address

Consideration:

- Consistency: user visibility (if a change is visible to user, use user id / cookie), measurement (when testing latency, IP address may be the only choice)

- Ethical considerations: whether can data identify user, user consent (user id has lots of personal data, requires consent)

- Variability: when unit of analysis = unit of diversion, empirical variability tends to be lower and closer to analytical estimate

Unit of analysis: the denominator of the proability

**Inter- vs. Intra-User Experiments**

If do event based diversion, there could be mix of users from both sides

Intra-user experiment: expose the same user to a feature on and off over time, compare based on time windows

- Need to be careful with time periods e.g. Christmas

- Whether users get used to the feature

Interleaved experiments: expose the same user to a feature on and off at the same time e.g. reordering a list

**Target population**
  
- Limited amount to avoid press
  
- Avoid testing for multiple lanaguages
  
- Limit to certain kinds of browsers

- Target certain group of users to avoid dilution

**Population vs Cohort**

Cohort: people who enter the experiment at the same time

- Look for learning effects

- Examining user retention

- Want to increase user activity

- Anything requiring users to be established

e.g. Having existing course and change structure of lesson

Unit of division: user-id, cannot run on all users in the course

Choose cohort based on the time of starting the course after the start of experiment

**Size**

Reduce size

- Increase dmin, alpha, beta

- Change unit of diversion to be the same as unit of analysis

- Target experiment to specific traffic

Don't know the fraction: run a pilot experiment or observe the data for first several days

**Duration vs Exposure**

- Account for variability: longer to account for changes between weekday and weekend, holiday or not

- Risky or not, limit exposure to avoid media

- Learning effect: whether user adopt to the change, need time

Choose unit of diversion correctly

Dosage, use cohort instead of population

Pre-period and post-period AA test: difference is learning effect


## Analyzing results

**Sanity checks**

- Population sizing method: check experiment population and control population are comparable

- Invariants check: some metrics should not change during the experiment

**Choosing invariants**

If unit of metric is larger than unit of diversion, the matric should be invariant

e.g. Run experiment for 2 weeks, unit of diversion: cookie

Total control: 64454, total experiment: 61818, check whether the difference is within expectation

Given the cookie is randomly assigned to control or experiment with probability of 0.5

1. Compute the standard deviation of binomial with probability of 0.5, $SD = \sqrt{\frac{0.5*0.5}{64454+61818}} = 0.0014$

2. Multiply the z-score to get margin of error, $m = 1.96*SD = 0.0027$

3. Compute the confidence interval around 0.5, confidence interval is 0.4873 to 0.5027 

4. Check whether the actual fraction is within the interval, the actual is 0.5104, so not within the interval

Look into day by day data to find the reason

Do not move forward if does not pass sanity check

- Communicate with engineering
  
- Retrospective analysis
  
- Compare with pre-period data

Common reason: 

- Data capture: when capturing new experience, probably not captured correctly

- Experiment setup: whether filters are setup correctly
  
- Infrastructures
  
- Learning effect: not much changes in the beginning, increasing over time

**Single metric**

e.g. Change color of start now button, metric: click-through-rate, unit of diversion: cookie

$N_{cont}$: 7370, $X_{cont}$: 352, $N_{exp}$: 7270, $X_{exp}$: 565

1. Sanity check: pass

2. Emperical SE: given 0.0035 with 10000 pageviews per group

   SE is proportional to $\sqrt{\frac{1}{N_1} + \frac{1}{N_2}}$

   $\frac{0.0035}{\sqrt{\frac{1}{10000} + \frac{1}{10000}}} = \frac{SE}{\sqrt{\frac{1}{7370} + \frac{1}{7270}}}$

   SE = 0.0041

3. $\hat{d}$ = experiment CTR - control CTR = 0.03

   m = 0.0041 * 1.96 = 0.008

   Confidence interval: 0.022 to 0.038, does not include 0, so launch the feature

[Sign test](https://www.graphpad.com/quickcalcs/binomial1.cfm)

Sign test has lower power

1. Count total number, number of success
  
2. If no difference, 50% chance of positive change on each day, cannot assume normal
  
3. Check two-tail p-value

If confidence interval and sign test disagree, consider different subgroups

e.g. Separate weekday and weekend, weekdays may have no effect, weekends have effect

Simpson's paradox: click through rate is higher for experiment for both groups, but the overall click through rate is lower for experiment

There are different number of users from each group

Reasons:

- Something wrong with the set up

- Change affects two groups differently


**Multiple metric**

Probability of any false positive increases as you increase number of metrics

Need to use higher confidence level for each metric

Method 1: assume independence

$\alpha_{overall} = 1 - (1 - \alpha_{individual})^n

Method 2: Bonderroni correction

- Simple

- No assumption

- Garanteed to give $\alpha_{overall}$ at least as small as specified

$\alpha_{individual} = \frac{\alpha_{overall}}{n}$

Could be too conservative

Different strategies:

- Control probability that any metric shows a false positive -- familywise error rate (FWER)

- Control false discovery rate (FDR) FDR = E[# false positives / # rejections]

Launch or not:

- Do I have statistical significant and pratical significant result to launch the change?

- Do I understand what does this change do to user experience?

- Is this change worth it?


**Changes over time**

Effect may disappear when launch the change

Seasonality changes e.g. students, holidays

Solution: hold back a small group of people, comtinue to compare the result


## AB Testing Interview Questions

**Experiment design**

Start with offering outline, which one should I dive into?

Choosing the metric

Selecting the randomization unit

Calculating the sample size

Determining the minimum detectable effect

**Sample size estimation**

$n=\frac{\sigma^2(z_{\alpha/2}+z_{\beta})^2}{\delta^2}$

$\sigma^2$: estimation of variance, from historical data and tests, smaller variance, fewer samples

$\delta$: difference between control and treatment, use minimum detectable effect, need more data to detect smaller changes, smaller delta, more samples

When $\alpha = 0.05$, $\beta = 0.2$, $n=\frac{16\sigma^2}{\delta^2}$

When $\alpha = 0.01$, $\beta = 0.2$, $n=\frac{19\sigma^2}{\delta^2}$

When $\alpha = 0.05$, $\beta = 0.1$, $n=\frac{21\sigma^2}{\delta^2}$

$\alpha$: smaller alpha, higher confidence interval, more samples

$\beta$: smaller beta, greater power, more samples

**Metrics selection**

- Sensitive and timely e.g. CTR (immediately reflects performance), conversion rate

- Measurable e.g. CTB (can be obtained in real time)

- Attributable e.g. CTR (attribute higher CTR to design)

How to select:

Qualitative: user experience research, focus groups, surveys

Quantitative: data analysis

- Fully understand the goal of test e.g. growth, engagement, revenue

  e.g. Youtube hide dislike counts

  Goal: protect creators, especially small creators

  What is expected: small creators become more active

  Metrics: average time of Youtube per creator, average number of videos posted per creator

- Analyze user experience: consider the steps each users need to take

  e.g. Youtube hide dislike counts

  Desired outcome: fewer dislike on videos from small channels

  Control: users can see the number of dislikes

  Treatment: users cannot see the number of dislikes, but feedback is possible

  Metric: average number of dislike per viewer, idealy decrease for small creators

**Randomization Unit**

Randomization unit: unit of diversion

What to assign to control and experiment group

Impact user experience and metric

Commonly user: 

- User ID: stable across time and platform, require log in, need to be aware of confidentiality
  
- Cookie: specific to browser and device, identify users without log in

- Event: finer than user ID, do not require log in, do not distinguish users, offer more units, may lead to inconsistent experience to users, should not be used if changes are visible to users

- Session: continuous period of activities
   
- Devide ID: only more mobile device

Randomization unit should be at least as coarse as unit of analysis

**Multiple testing**

Test multiple variants of a feature

e.g. 10 tests running at the same time, 1 case won with p<0.05, should you make the change?

No. Should not use the same significance level, probability of false discovery increases

1. Use Bonferroni correction
  
   Significance level / number of tests = 0.05 / 10 = 0.005

   Tend to be too conservative

2. Control False Discovery Rate

**Primary effect**

Primary effect: people are reluctant to change

Novelty effect: people welcome the changes and use more

Effects will not last long

Rule out the possibility: run tests only on first time users

**Interference between variants**

Typical design: split users randomly, users are independent

Case: social network, two sided network

e.g. Test a new feature to increase posts created per user, assign each user randomly, the test won by 1% in terms of posts. What would happen after new feature is launched? Assume no novelty effect

Network effect: user behaviors are impacted by others

The effect can spillover the control group

The difference underestimates the treatment effect, so the difference will be more than 1%

e.g. Treatment group attracts more drivers, less drivers in the control group

Actual effect < treatment effect

e.g. A new feature provides coupons to riders

Goal: increase rides by decrease price

Testing strategy: evaluate the effect of the new feature

Two-sided markets: split by geolocations (NY vs SF), only works when treatment effect is in short time

Social network: 

- Network cluster: create network clusters, people interact mostly within the cluster

- Ego-network randomization: a cluster is compoased of an ego and her alters, user either has the feature or not













