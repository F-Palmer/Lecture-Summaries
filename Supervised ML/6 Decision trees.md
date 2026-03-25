very sensitive to overfitting
(High variance)

## Training 
1. Which feature is evaluated at this point?
2. At which value of the feature is the tree traversed further to the left or to the right

A split is good if the distribution of the label in the resulting subsets is as homogeneous as possible
Less uncertainty after the split → better feature.
The trick is to measure how much _uncertainty_ (entropy) gets removed by splitting on a feature

In Linear regression the feature with the largest coefficients is the most important one 
In Decision trees its the one closest to the root

### Entropy
The lower the entropy the more order (similar elements) in a set
$𝐻 = −(𝑝 \log 𝑝 + 𝑞 \log 𝑞)$
is the highest if p is 0.5

### Information Gain
$𝐼𝐺 (𝑉, 𝑊) = Η (𝑉) − Η(𝑉|𝑊)$
H(V) Entropy before split
H(V|W) Entropy after split
V = Label
W = some feature

Each subset after the split has its own entropy
A feature that makes the subsets “pure” (low entropy) will have high information gain
$$H(V \mid W) = - \sum_{j \, : \, \text{possible values of } W} 
P(w_j) \sum_{i=1}^{K} P(i \mid w_j) \log_2(P(i \mid w_j))$$
K = all Label values
We want a feature with low H(V|W) and high IG

### Numerical Features
different Possibilities for Splits -> split candidates

1. All values are candidates
2. Calculate n quantiles of the feature form the training data and select them as split candidates -> Statistical
3. n equal intervals

## Strategies to avoid overfitting 

Stop tree generation if:
- The node is pure
- No or only little reduction of entropy is possible at a node
- the defined max tree depth has been reached  (hyperparameter)
- there are fewer then n data points in the subset 

Prune trees 
Create large tree first and then prune the branches that have many leaves but increase the accuracy only little 
- accept a little bias and reduce the variance


If leaf is not pure -> 75% Bike

## Regression Trees
Decision Tree for regression problems

A leafs prediction is the average of all values of the target variable in the node
Not with Information Gain but which reduction in prediction error 

![[Screenshot 2025-12-06 at 11.40.53.png]]

## When is which better?
If the better decision boundary is liner or blocky