## Collaborative filtering

if two people had the same preferences in the past, there is a high probability that it will also be the case in the future

#### Pros
- simple data collection
- existing knowledge can be used
#### Cons
- cold start problem 
- low scalability 
- often thin datasets 

$$\operatorname{sim}(a,b)  
= \frac{1}{1 + \sqrt{\sum_{p\in P}\bigl(u(a,p)-u(b,p)\bigr)^2}}$$
u() rating of

u_ average rating of A

$$u’(a,s)  
= \overline{u}(a)

- \frac{\sum_{b\in kNN(s,a)} \operatorname{sim}(a,b)\bigl(u(b,s)-\overline{u}(b)\bigr)}  
    {\sum_{b\in kNN(s,a)} \operatorname{sim}(a,b)}$$

## Content-based filtering

Based on similarity of objects

$$\operatorname{sim}(s,t) = \frac{2\cdot |K(s)\cap K(t)|}{|K(s)| + |K(t)|}$$
$$u’(a,s) = \frac{\sum_{t\in kNN(s,a)} \operatorname{sim}(s,t)u(a,t)}  
{\sum_{t\in kNN(s,a)} \operatorname{sim}(s,t)}$$
## Knowledge based filtering 

The user specifies his preferences directly through search masks or queries


## Evaluation of recommendation services

- Variety of feedback
	- Shows products from different manufacturers instead of just one manufacturer
- Novelty value
	- Occasionally show songs by an as yet unknown artist
- Robustness against fraud
	- A company should not be able to have its own products displayed preferentially
- Privacy
	- It should not be possible to identify the purchases of individual user
- Determinism 
- Traceability
	- Display of "Customers who bought A also bought B"