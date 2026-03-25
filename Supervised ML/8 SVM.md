Margin around the hyperplane

## Hard margin linear SVM

Goal: maximise the margin 
minimize: $0.5 w^T w$


![[Pasted image 20251207110528.png]]
1. Start from the familiar line form
	- In 2D a straight line is often written y = m x + c.
	- Move everything to one side: m x − y + c = 0.

2. Write the line as a vector (dot‑product) equation
	- m x − y + c = 0 is the same as [m , −1] · [x, y] + c = 0.
	- So you can set the weight vector w = (w1, w2) = (m, −1) and bias b = c.
	- Compactly: w^T x + b = 0 is the decision boundary (where x is the feature vector [x1, x2]^T).

3. Why the transpose notation appears
	- The slide shows a row vector (m, −1) and then its transpose to make it a column so it can be dotted with the column feature vector. That is just matrix/vector bookkeeping: (w)^T x = scalar.

4. Classification rule
	- Once you have w^T x + b, you classify by the sign:
	    - If w^T x + b ≥ 0 → Class +1
	    - If w^T x + b < 0 → Class −1
	- The example on the slide uses numbers: y ? 0.167 x + 2.334. Rearranged:  
	    0.167 x − y + 2.334 > 0 ⇒ class +1, otherwise class −1.  
	    So here w = [0.167, −1], b = 2.334

## Soft margin linear SVM
![[Pasted image 20251207151428.png]]


## Kernelized SVM 


### Hyper Parameter tuning 
Grid search
![[Pasted image 20251207152403.png]]
Random Search
evaluates a given number of random combinations by selecting a random value for each hyperparameter at every iteration

## Multiclass Classification
One vs One
One vs Rest

Use weight to balance non balanced Probelms

