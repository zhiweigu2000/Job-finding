# Probability Notes

Conditional probability: P(A|B) = P(AB) / P(B)

Independent events: P(AB) = P(A)* P(B)


## Expectation

![image](https://user-images.githubusercontent.com/76275089/127007620-90ba7d1c-a7d6-4ec1-a75f-751472f4cceb.png)

Addition rule: E(X+Y) = E(X) + E(Y)

Indicator: E(I) = P(A), E(X) = P(A1) + P(A2) + ...


Tail sum formula

![image](https://user-images.githubusercontent.com/76275089/127009830-f8db9c88-f0eb-44ef-b4f5-0df95597198b.png)

Markov's inequality

If X > 0, then P(X >= a) <= E(X)/a for every a > 0

![image](https://user-images.githubusercontent.com/76275089/127011327-bba6de29-3073-4fd6-9899-7d66cf623e4a.png)

E(aX+b) = aE(X) + b


## Standard deviation

![image](https://user-images.githubusercontent.com/76275089/127164059-36491ba7-de67-4d06-983d-bf59fcc4785c.png)

Var(X) = E(X^2) - (E(X))^2

SD(aX+ b) = |a|SD(X)

Standardization: X* = (X - E(X))/SD(X), E(X*) = 0, SD(X*) = 1

P(X <= b) = P(X* <= (b-E(X))/SD(X))

![image](https://user-images.githubusercontent.com/76275089/127167393-3e9c296f-fce8-43f9-a7ed-25db105f23a5.png)

If X and Y are independent, Var(X) + Var(Y) = Var(X + Y)

![image](https://user-images.githubusercontent.com/76275089/127168250-8ced2ac7-ff94-4662-9a0f-a08f0b356d04.png)


## Uniform distribution

f(x) = 1/(b - a) for a < x < b

E(X) = (a + b)/2

Var(X) = (b - a) ^ 2/12


## Binomial distribution 

![image](https://user-images.githubusercontent.com/76275089/126997510-55c19c86-02a2-402f-9c8e-26b5a9e9ec78.png)

![image](https://user-images.githubusercontent.com/76275089/126998892-aab62834-2b3c-42ba-92ae-2882d43985a9.png)

E(X) = np

Var(X) = np(1 - p)


## Possion distribution

Binomial distribution when p is nearly 0, n closes to infinite

![image](https://user-images.githubusercontent.com/76275089/127008287-01ab230b-589e-4add-af2e-2eaa0e6803c0.png)

![image](https://user-images.githubusercontent.com/76275089/127169902-a1c024bb-8690-4c2b-b278-51bc629ef48f.png)


## Geometric distribution




## Exponential distribution

![image](https://user-images.githubusercontent.com/76275089/127177889-2952802b-1f3d-42af-8eb5-a12e9ff2316e.png)

Memoryless property: given survival to time t, the chance of surviving a further time s is the same as the chance of surviving to time s in the first place

![image](https://user-images.githubusercontent.com/76275089/127178761-a9e503a7-eb64-45c1-9118-f7c9c2c8c2cc.png)


## Gamma distribution

![image](https://user-images.githubusercontent.com/76275089/127178807-2493408f-2c06-4b22-aa67-94a1958ff468.png)


## Beta distribution

![image](https://user-images.githubusercontent.com/76275089/127180798-25d5a198-a0d3-4d5f-8fd4-88eddfb67c23.png)

E(X) = r/(r + s)


## Change of variable

![image](https://user-images.githubusercontent.com/76275089/127179828-32e5c51c-2086-4d81-82cd-bd10ff42be57.png)


## Cumulative distribution function

A probability distribution over the line is completely determined by its cdf

Fmax(x) = F1(x)F2(x)...Fn(x)

Fmin(x) = 1 - (1-F1(x))(1-F2(x))...(1-Fn(x))


## Conditional expectation

E(X+Y|A) = E(X|A) + E(Y|A)

![image](https://user-images.githubusercontent.com/76275089/128298547-2afd61df-69f8-4472-a43c-aefe45a9371c.png)

E(Y) = E[E(Y|X)]

![image](https://user-images.githubusercontent.com/76275089/128299255-3cdd4a50-b8bd-4173-84d0-f8859ac5bc76.png)

![image](https://user-images.githubusercontent.com/76275089/128299376-cf96d63f-768c-4b97-8d69-c4ddc928684a.png)






















