# Machine Learning lecture note: Week 1
## What is Machine Learning?

So in terms of definition , machine learning means a program that can learn by itself without any programmer. Also, it can perform better in future judging by its probability, experience or data they will accumulate.

## Supervised Learning
A case that data have already organized and the relationship exists between data.
* Regression
* Classification →"T/F"

## Unsupervised Learning
Apart from supervised learning, we cannot know what relationship between data would have.
* Clustering → "grouping"
* Non-clustering → ex. Cocktail party
---
## Cost Function
### Model Representation
given Training set → establish Learning Algorithm → Hypothesis  
By this hypothesis, we can predict the value(Y) with the given datum(X).  
### Cost Function
Usage: for measuring accuracy of the hypothesis function 

$$ J(\theta_0, \theta_1) = \frac1{2m}\sum_{i=1}^m (h(x) - y)^2 $$

Simply it is a half of the mean of squared difference between the hypothesis and the real value.
However, this may raise some questions "Why it has to be squared?" or "Why it has to be divided into half?"  

#### "Why it has to be squared?"
According to central limit theorem(a.k.a CTL), the larger the number of independent cases of the data, the more likely they will fit in the gaussian distribution. Following the CTL, noises distribute normally to gaussian distribution called, gaussian noises.  

If you take a closer look at the cost function, you may have seen a similar function in statistics. Variance, meaning how well the data are distributed from the center(=mean).  
Overall, this can be interpreted as **minimizing variance = minimizing cost function**.  

So in conclustion, cost function is better than just merely using mean of absolute loss given that gaussian distribution is a great model for better prediction.

#### "Why it has to be divided into half?"  
   In the lecture, the purpose of dividing into half is for convenience. This, in fact, is related to gradient descent. This will be discussed later.

### Cost function Intuition 
There is a slight difference between the graphs in lecture part1 and 2.  
In part 1, hypothesis function is a simple linear function without y-intercept.  
This results in cost function to have 2 dimension graph x-axis as a slope, y-axis as value of cost function.  

Different from part 2, a new parameter(y-intercept) is added in hypothesis function. Although the cost function itself is a squared mean, the graph shows different from what we have saw in part 1, a contour graph like we see in geography.  

So in 2D expression, the height(cost function value) is represented as the color of the lines, lower heights = bluer lines. You can see it clearly when it represents in 3D.

We can understand the more parameters added to cost function the higher the dimension its graph will have.

---
## Parameter Learning
We know now what cost function looks like when hypothesis function has both $\theta_1$(slope) and $\theta_0$ (y-intercept). It would be easy to comprehend gradient descent

### Gradient Descent
Usage: for converging to the minumum cost
$$ \theta_j := \theta_j - \alpha \frac{d}{d\theta_j}J(\theta_0, \theta_1) $$
※ This has to be updated simultaneously.   

|parameter | description |
|---|---|
| $\alpha$ | Learning rate |  
| $\frac{d}{d\theta_j}J(\theta_0, \theta_1)$ | differentiated cost function as speed |

Learning rate decides total time to converge (small $\alpha$) or whether it converges or not (large $\alpha$). 
However, gradient descent actually converge to local minimum value, so it automatically take smaller steps even if $\alpha$ is a fixed value.  

Now we can understand now why cost function is divided by half, as it has to be differentiated!  

### Gradient Descent for Linear Regression
So using method above, in linear regression, gradient descent controlled each step converge to global minimum cost in the end. This is called **batch gradient descent** 
