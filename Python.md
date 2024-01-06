![image](https://github.com/zhiweigu2000/Job-finding/assets/76275089/e8557c06-f9ba-47e0-aef9-aca1a0c1478f)
![image](https://github.com/zhiweigu2000/Job-finding/assets/76275089/4052f817-1a92-493d-a1b4-496e1923488d)

### Machine learning

from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.20, random_state=42)


from sklearn.linear_model import LogisticRegression

from sklearn.metrics import accuracy_score, f1_score, precision_score, recall_score

logreg = LogisticRegression(random_state=42)

logreg.fit(X_train, y_train)

y_pred = logreg.predict(X_test)

accuracy_score(y_test, y_pred)


from sklearn.model_selection import GridSearchCV

param_grid = {
    'C': [0.01, 0.1, 1],
    'penalty': ['l1', 'l2'],
    'solver': ['liblinear', "lbfgs"]
}

grid_search = GridSearchCV(logreg, param_grid, scoring='f1', cv=5, verbose = 2)

grid_search.fit(X_resampled, y_resampled)
