## logistic regression

$$f(x) = \frac{1}{1+e^{-x}}$$
decision boundary -> not the threshold value 

### Loss Function (log loss, cross entropy)

$$L(w) = -\sum_{i=1}^{N}
\begin{cases}
\log(\hat{y}_i), & \text{if } y_i = 1 \\[6pt]
\log(1 - \hat{y}_i), & \text{if } y_i = 0
\end{cases}
\qquad$$
$$L(w) = -\sum_{i=1}^{N} \Big[\, y_i \log(\hat{y}_i) + (1 - y_i)\log(1 - \hat{y}_i) \Big]$$
## Evaluation of classifiers

![[ZMF/Supervised ML/Media/Confusion Matrix.png]]
Accuracy, 
Precision, (What proportion of predicted positive cases ("1") are actually positiv)
Recall (What proportion of actual positive cases ("1") does the model recognize?)
and F1 Score

Type 1 error: when your model incorrectly predicts a positive outcome
Type 2 error: happens when your model fails to detect a real effect or positive case
## Receiver Operating Characteristic

Tracks true positive rate (sensitivity) 
	proportion of actual positives your model correctly captures
and false positive rate
	proportion of actual negatives your model accidentally flags as positive

A perfect classifier has FPR = 0 and TPR = 1
The Threshold that gives us the best point on the ROC curve should be chosen