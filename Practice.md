## [Amazon Data Scientist Mock Interview - Fraud Model](https://www.youtube.com/watch?v=68I67w63IpY)

### Machine learning

**What is variance and bias trade off?**

Bias represents the distance between predicted values and the actual values

Variance represents the spread of the data

When a model is too simple, or under-fitted, it has high bias because its preductions are inaccurate. It has low variance because it is less likely to change

When a model is too complicted, or over-fitted, it has low bias, but high variance, meaning that the model could not generalize well to unseen data

The total error of a model is bias^2 + variance + irreducible error. A good model needs to balance between these two factors to have a suitable level of complexity, reaching lowest total error. 

If the flexibility of the decision boundary increase, what will happen?

Overfit, highly flexible model may fit the training data very closely, variance increase, bias decrease

**What is the difference between boosting and bagging?**

Both ensemble techniques

Boosting is building a new model on the top of the old model, focus on where the previous model did not perform well, to form a strong learner, such as adaboost

Bagging is using multiple subsamples of the data to train multiple weak learners, combine these weak models together and giving a majority vote, such as random forest

When you increase the number of trees, how are the bia and variance affected by the boosting and bagging model?

Boosting: tend to overfit, model fits the training data really well, bias decreases, variance increases

Bagging: reduce the impact of noise, variance decreases, less likely to affect bias

### Case

**How would you detect seller fraud on amazon?**

Seller fraud: sellers to misrepresent themselves, or the products they're selling, buyers make purchases they do not expect

Transactions: success vs refund

Seller: review, withdraw money, IP address

Listing: title, image, description

Label: transaction is fraud

**Feature selection**

Target variable: class imblanace, 1/0

If item match description: 1/0

Tenure of listing

Number of reviews

Percentage of positive reviews

Frequency of withdraw money: categorical

Number of past transactions

Percentage of successful transactions

LASSO regularizer, PCA to select features

**Performance**

Train test split

Cross validation

ROC curve

F1 score

Accuracy may be biased / inflated

**Fraud transaction to seller**

Apply on historical data, find decision boundary


## [Facebook Data Scientist Mock Interview - Segment Influencers](https://www.youtube.com/watch?v=XOJk0AKIqv8)

### Statistics

**How do you derive the beta coefficient from multivariate regression?**

For a multivariate regression, we used multiple independent variables to predict one dependent variable. The coefficient for independent vriables are known as the beta coefficients. It explains how much the dependent variable is going to change on average when the independent variable is changed. 

OLS $\hat{\beta} = (X^TX)^{-1}X^TY$

Maximum likelihood estimator

**Suppose the data with target variable is zero-inflated, how would you deal with your model?**

Why are there so many zero? Is it an error or the actual value?

Model the data for being zero and not being zero, check beta coefficient

**How to interpret confidence interval for logistics regression?**

Confidence interval explains how likely the range will cover the true value, in this case means 95% of the time, this confidence interval range will cover the true beta coefficient for the logistics regression. It represents the uncertainty around the variable. 

What if the interval include 1?

An odds ratio of 1 implies no effect on the odds of the event occurring, which means it is statiscally not significant. 

### SQL

Message table: user_id, user_name, date, message_sent, message_received

**For each day, return the name of user who received the highest message_sent to message_received ratio**

SELECT user_name, date, ROW_NUMBER() OVER (PARTITION BY date ORDER BY message_sent/message_received DESC) AS rnk
FROM Message 
WHERE rnk = 1

**For each user, return the first date when the user receive 0 message**

SELECT user_id, MIN(date)
FROM Message
WHERE message_received = 0
GROUP BY user_id

### Case

**How do you determine if a user is an influencer on Ins?**

Influencer is someone who could spread information or ideas through interactions on ins

Number of followers

Number of posts per day

Number of interaction (view, like, comment) received per post

Paid ads

What is the goal? Match advertisers to influencers

How to actually bin users?

- Unsupervised: clustering
- Supervised: number of paid ads

**How to segment influencer population?**

Group into different categories

Different topics / tags

Features: content of posts (nlp), followers (gender, age, location, interest)

Model: clustering

Evaluation: human labelers



<img src="https://user-images.githubusercontent.com/76275089/184062202-c227d555-795b-4cf1-b903-631fb36122a7.png" width=800>

```SQL
SELECT distinct(names) as users_less_than
FROM 
(
  SELECT users.id, users.name as names, count(transactions.id) as transactions, sum(transactions.quantity\*products.price) as totals
  FROM users
  LEFT JOIN transactions 
  ON transactions.user_id = users.id
  LEFT JOIN products
  ON products.id = transactions.product_id
  GROUP BY users.id
) temp
WHERE transactions<3 OR totals<500
```

<img src="https://user-images.githubusercontent.com/76275089/184286197-a8b0c4a0-8e5a-4e1a-b3a8-b79cbf3a4776.png" width=800>

```python
def stem(roots, setence):
    words = setence.split()
    for j in range(len(words)):
        for i in range(len(words[j])):
            if words[j][:i] in roots:
                words[j] = words[j][:i] 
                i = len(words[j])           
    new_sentence = " ".join(words)
    return new_sentence
```

<img src="https://user-images.githubusercontent.com/76275089/184458214-a379453f-8df7-48af-a770-e60aff4e9d72.png" width=800>

```SQL
SELECT round(count(friend_accept.acceptor_id) / count(friend_request.requester_id), 4)
FROM friend_request
JOIN friend_accept
ON friend_request.requester_id = friend_accept.requester_id AND friend_request.requested_id = friend_accept.acceptor_id
```

<img src="https://user-images.githubusercontent.com/76275089/184553413-2016f095-211d-4846-8dc3-11a156a59c17.png" width=800>

6 * 0.3^5 * 0.7 = 0.0102


<img src="https://user-images.githubusercontent.com/76275089/184553578-d916b5ff-26cd-471d-a763-a6c86dcabcfc.png" width=800>

```SQL
WITH temp1 as
(
  SELECT count(*) as change
  FROM account_status a
  JOIN account_status b
  ON a.account_id = b.account_id
  WHERE a.date = "2020-01-01" and a.status = "closed" and b.date = "2019-12-31" and b.status = "open"
),
temp2 as
(
  SELECT count(distinct account_id) as total
  FROM account_status a
  WHERE a.date = "2019-12-31" and a.status = "open"
)

SELECT round(temp1.change / temp2.total, 2) as percentage_closed
FROM temp1, temp2
```


<img src="https://user-images.githubusercontent.com/76275089/194732556-3f22e7bc-901b-4fdc-9a2a-da58861a7134.png" width=800>

1. 0.5 * 0.5 = 0.25
2. Binomial distribution (n, q), E = nq


<img src="https://user-images.githubusercontent.com/76275089/194732666-3e860a08-dd48-47d7-80f0-bd367e761156.png" width=800>

<img src="https://user-images.githubusercontent.com/76275089/194732683-4969f3af-d192-421b-a0ab-4abb93c5b29a.png" width=800>


<img src="https://user-images.githubusercontent.com/76275089/194732689-a306f519-cf24-4626-b4e6-8cad650e0b96.png" width=800>

1. 0.2 / (0.2 + 0.8 * 0.6^3)
2. 1
3. 0.2 / (0.2 + 0.8 * 0.6^n) < a
    0.2 < a(0.2 + 0.8 * 0.6^n)
    (1 - a)0.2 < 0.8 * 0.6^n
    1 - a < 4 * 0.6^n


<img src="https://user-images.githubusercontent.com/76275089/194732831-6915698b-cc89-47ad-be9d-3eaeeb5a4989.png" width=800>

(1/2)^6 * (6 * 5 * 4)/(3 * 2) = 0.3125

1/0.3125 = 3.2


<img src="https://user-images.githubusercontent.com/76275089/194957869-0d8eef86-cc8a-4369-a67c-e3d12ad047f9.png" width=800>

1/2 * (1/2 * 1/2 * 2 + 3/4 * 3/4 + 1/4 * 1/4) = 1/2 * (1/2 + 10/16) = 9/16




