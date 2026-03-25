$\epsilon$ is a random normally distributed error term with expected value 0

> Residuals: 
> Difference between real value and predicted value

### Loss function
$$L(w_0, w_1) = \frac{1}{N} \sum_{i=1}^{N} \left( y_i - (w_0 + w_1 x_i) \right)^2$$
-> search for global minimum
best fit is with hats

> $R^2$:
> How much of the Variance observed in the data can be explained by this linear model

plane and hyper plane

$$L(w_0, \mathbf{w}) = \frac{1}{N} \sum_{i=1}^{N} \left( y_i - (w_0 + \mathbf{w}^T \mathbf{x}_i) \right)^2
$$
## Encoding categorical features

#### One-hot encoding

> Nominal Data:
> Without a natural order or rank

> Ordinal Data: 
> Have a predetermined or natural order

With one-hot encoding, the constant term 𝑤0 should be omitted in the model function
during regression, otherwise the solution $\hat{w}$ is no longer unique (=numerical difficulties and
problems in interpreting the values) -> `sklearn.linear_model.LinearRegression(…, fit_intercept=False, …)`
With any given category, you would end up with: $y = w_0 + w_j$ which is not solvable

Reduce the dimention of the one-hot vector by introducting a baseline category with only zeros -> called dummy encoding
Then $w_0$ does not need to be ommited
`pd.get_dummies(..., drop_first=True, ...)

## Interaction terms 

Normally it does not matter what the value of x1 is when we increase x2. Can be introduced with an interaction therm 





