## Can and can't do with AB testing

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

