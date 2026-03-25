Underfitting:
- High bias (error based on wrong model assumptions)

Overfitting: 
- high variance model parameters change greatly when we train with a different training data set

-> reduce model complexity 

## Ridge Regression (l2 Regression)

Regularization term:
$$L(w) = \frac{1}{N} \sum_{i=1}^{N} \left( y_i - w^{T} x_i \right)^2
      + \lambda \sum_{i=1}^{p} w_i^{\,2}$$
unimportant coefficiants will approach zero
often called alpha

## Lasso Regression 
$$L(w) = \frac{1}{N} \sum_{i=1}^{N} \left( y_i - w^{T} x_i \right)^2
      + \lambda \sum_{i=1}^{p} |w_i|$$
unimportant coefficients will be zero
-> feature selection

## Hyperparameter search

1. Choose candidate set
2. Train model with hyperparameter 
3. Test Model performance on Validation data
4. Choose new hyperparameter 

#### Cross Validation
k-fold cross validation
1. Choose candidate set 𝐻.
2. For each 𝜆 ∈ 𝐻:
	a) Subdivide training data into 𝑘 equally sized validation data sets.
	b) For each validation dataset 𝑘𝑖:
		a) Train model 𝑓𝜆(𝑥) with Hyperparameter 𝜆 on training data except 𝑘𝑖.
		b) Test 𝑓𝜆(𝑥) on validation data 𝑘𝑖.
	c) Calculate average performance (MSE, R²) over all 𝑘𝑖
3. λmax := Parameter with best performance in 2c)
4. Train 𝑓𝜆𝑚𝑎𝑥 (𝑥) on all data (Training + Validation).

-> very high computational cost

