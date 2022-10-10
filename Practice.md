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




