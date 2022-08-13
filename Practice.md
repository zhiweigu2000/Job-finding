![image](https://user-images.githubusercontent.com/76275089/184062202-c227d555-795b-4cf1-b903-631fb36122a7.png)

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

![image](https://user-images.githubusercontent.com/76275089/184286197-a8b0c4a0-8e5a-4e1a-b3a8-b79cbf3a4776.png)

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

![image](https://user-images.githubusercontent.com/76275089/184458214-a379453f-8df7-48af-a770-e60aff4e9d72.png)

```SQL
SELECT round(count(friend_accept.acceptor_id) / count(friend_request.requester_id), 4)
FROM friend_request
JOIN friend_accept
ON friend_request.requester_id = friend_accept.requester_id AND friend_request.requested_id = friend_accept.acceptor_id
```