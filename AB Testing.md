## Can and can't do with A/B testing

Need clear control and experiment group

Cannot take too long

Change aversion: old users may resist against the new version

Novelty effect: old users may all go for the new experience, then the test set has everything

Other techniques: user log, user experience research(qualitative data)

## Example

Customer funnel: visit -- explore site -- create account -- complete

Hypothesis: change button from orange to pink will increase how many students explore courses

Metric: 

Click through rate = number of clicks / number of page views, measure usability

Click through probability = unique visitors who click / unique visitors to page, measure total impact

## Significance

Binomial distribution:

2 types of outcome

Independent events

Identical distribution, same p for all

Confidence interval:

<img width="148" alt="image" src="https://user-images.githubusercontent.com/76275089/169205373-240f3ad7-97b1-4aed-ba2f-bc5ea50781de.png">

[z-score table](https://www2.math.upenn.edu/~chhays/zscoretable.pdf)

Null hypothesis (H0): P(cont) - P(exp) = 0

Alternative hypothesis (HA): P(cont) - P(exp) != 0

p-value = P(P(exp) - P(cont) | H0) < 0.05, reject null hypothesis

Pooled standard error

<img width="1308" alt="image" src="https://user-images.githubusercontent.com/76275089/169208187-4c3d7b16-0d49-40d9-983f-04d8c28076df.png">

Practical significant: lower, like 2%

Statistical power: how many are needed to give a significant result

Power and size tradeoff: smaller change to detect, larger experiment

Whole confidence interval above practical significant: launch

Whole confidence interval below practical significant: do not launch

Some part of confidence interval above practical significant: additional test

## Ethics

Risk: whether the risk exceeds the minimum risk

Benefit: how might the result help

Choice: what other choice do participants have, fewer alternative, more coercion

Privacy: what data is being collected, and what is the expectation of privacy and confidentiality

## Metric

### Invariant checking

Are the population the same?

### Evaluation

High level business metric: revenue, market share

Detailed metric: user experience, may to difficult to evaluate

### Define matric

High level concepts

Business objective

Single or multiple: composite metric, look into multiple metric

Customer funnel

Difficult metric: don't have access to data, take too long

Generate metric:

- External data: companies that collect granular data, companies that run survey, academic research

- Observational analysis: show correlation not causation

- Discuss with others, company culture

- User Experience Research (UER): good for brainstorming, can use special equipment, need to validate result

- Focus group: bring users together, risk of group think

- Surveys: useful for metric that cannot collect directly, can not directly compare to other results

<img width="353" alt="image" src="https://user-images.githubusercontent.com/76275089/170893575-db95315e-e070-41b4-8d90-5ae0e68018be.png">

High level metric: click through probability = # users who click / # users who visit

Def 1: for each time interval, # cookies that click / # cookies

Def 2: # pageviews with click within time interval / # pageviews

Def 3: # clicks / # pageviews







