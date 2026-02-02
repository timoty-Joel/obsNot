## Introduction to Machine Learning

>"Machine Learning is a field of study that gives computer the ability to learn without explicitly programmed" 
>~ Arthur Samuel 

**Supervised Learning**
→ Refers to algorithm that takes input x and result the outcome y or output mappings
→ Characteristics of supervised learning is that we have to give our algorithm the examples to learn (including the right answer that is y from given input x)
Example:
![[w1_1.PNG]]

→ There are two major type of supervised learning:
	1. Regression
		This type is used to predict continuous values from given input/s. Regression used numerical data to predict numerical data.
		Example:
		![[w1_2.PNG]]
		The example above is a regression type of supervised learning. This type is intended to predict house prices based on the given input/s. Input in the example above is house size.  
		~
	2. Classification
		Classification is used to predict categorical data from given input/s. Classification predicts a small finite limited set of possible output categories such as 0, 1 and 2 but not all possible numbers in between like 0.5 or 1.7. 
		Example:
		![[w1_3.PNG]]
		In example above, the classification model is used to predict whether the patient's tumor is malignant(dangerous) or benign(not-dangerous). 
		~

**Unsupervised Learning**
→ Kind of learning that is aimed to find structures, patterns or something interesting from given dataset. 
→ In unsupervised learning, data in the given dataset is unlabeled so we don't have to label all the data, instead, the algorithm will find the pattern from the dataset. Also there's no output labels(the right answer) such as y in the dataset. 
Example:
	![[w1_4.PNG]]
	In the example above, there are similar articles title below the first article's title. That is what clustering(one of unsupervised algorithm) does. Clustering algorithm group the article on news based on the title's similarity, as u can see there are: panda, twin and zoo.

**Regression Model**
- Linear Regression
	![[w1_lin_1.PNG]]
	- A linear regression model will fit a straight line to the data, that the straight line allows us to predict the numerical output from given data. 
	- Just like the other algorithm is supervised learning, in this linear regression, we have to divide the dataset into two group: train set and test set. 
	- Linear Regression with one variable will takes one features as input and try to predict the possible output using mathematical formula

	![[w1_lin_2.PNG]]
	- Function f will predict the y using the streamline of the function
	- w and b are the parameters of the model we make. Parameters of a model is the variables you can adjust during training in order to improve the model
	- The algorithm learns from this data and generates the best-fit line like the line in the picture

**Cost Function**
- The cost function <ins>measures the difference</ins> between the predicted values of the model and the actual target values
![[w1_cost_1.PNG]]
- We could find the value of w and b to fit the best to the data by comparing between y-hat(predicted value) and the actual y. The difference is called the error, we're measuring how far off to prediction is from the target
- When the training set gets bigger, the calculations of cost function also getting bigger. So we could calculate the average so that cost function doesn't automatically get bigger as the training set size gets larger

![[w1_cost_3.PNG]]
- As you can see from the picture above, we search the best line to fit to the data by experimenting each w one by one to find the minimum cost
- Besides using graph, there's also another way to visualize the cost function by using contour plot
![[w1_cost_4.PNG]]

**Gradient Descent**
- An optimization algorithm to minimize the cost function that is used when training a model
- How to Gradient Descent works?
	- Initialize the parameters w and b, for an example: w = 0  and b = 0
	- Calculate the cost function J(w,b).
	- Calculate the partial derivatives of J(w,b):
		- We calculate the partial derivatives of J(w, b) with respect to w
		- After that calculate the partial derivatives of J(w, b) with respect to b
	- Update the parameters w and b → Using gradient function:
		- Parameter w: the initial w is updated subtracted with learning rate times (partial derivative of J(w, b) with respect to w)
		- Parameter b: the initial b is updated by subtracted with learning rate times (partial derivative of J(w, b) with respect to w)
	- Repeat steps 2 to 4 until convergence.
	
- In Gradient Descent, there's learning rate. Learning rate: hyperparameter that controls how much to change(step size) at each iteration while moving to find the minimum cost. The lower the value, the slower we travel along the downward slope
	- Why is it important:
	![[w1_grad_2.PNG]]
- For visualization: 
![[w1_grad_1.PNG]]


## Regression with Input Multiple Variables
- In regression, we won't have only 1 features, there will be more features or input to predict the output.
- Below, there's an example of multiple features:
	![[w2_mf_1.PNG]]
- Previously, the model we have was only $f_w~_b(x) = wx + b$. But, when we have multiple features the model will be $f_{w}~_{b} = w_{1}x_{1}+w_{2}x_{2}+\dots+w_{n}x_{n}+b$. 
- We can define the equation above with $\overrightarrow w$  and $\overrightarrow b$ as the list that contain numbers of feature. Example: $\overrightarrow w = [w_{1},w_{2},w_{3},\dots,w_{n}]$ and $\overrightarrow x = [x_{1},x_{2},x_{3},\dots,x_{n}]$
	- We can consider the list of numbers as a vector
- So the model can be rewritten as:
	$f_{w}~_{b} = \overrightarrow w \cdot \overrightarrow x+b$ = $w_{1}x_{1}+w_{2}x_{2}+\dots+w_{n}x_{n}+b$  

**Vectorization**
- Refers to technique that makes our code execution faster. Previously in python code, we used to do for-loops to multiply each w to each feature x, like this
	![[w2_vector_1.PNG]]
- Vectorization is a classic approach of converting input data from its raw format (i.e. text) into vectors of real numbers which is the format that ML models support. So we treat the inputs like vector. 
	![[w2_vector_2.PNG]] 
- Vectorization can be much faster because the Numpy library is able to use parallel hardware in our computer. 
- Visualization in vectorization:
	![[w2_vector_3.PNG]]

	![[w2_vector_4.PNG]]

**Gradient Descent for Multiple Linear Regression**
- Previously, we know that there are difference between vectorized model and non-vectorized. Here's the recap:
	![[w2_vector_5.PNG]]
- There are also difference when we use linear regression with one feature and multiple features:
	![[w2_vector_6.PNG]]
	- In differences above, when we use only one feature, variable w is just only one so we could write $f_{w}~_{b}$ . Meanwhile, when we have multiple features, we have to write it $f\:_{{\overrightarrow w}\:{b}}$ because we consider the multiple features as a list of numbers in math aka vectors 
![[w2_vector_7.PNG]]

**Feature Scaling**
- Refers to process of normalizing the range of features in dataset. Basically normalized the range of features from a large gap of range into comparable range of features
- For an example:
	- Consider we have a data like this
		![[w2_scale_1.PNG]]
		From data above, we can see the range of size feature is from 300 up to 2000 and the range of bedroom's numbers is 0 - 5. 
	- Imagine, we have to predict this data from given data above
		![[w2_scale_2.PNG]]
	- So, what is the size of the parameters? We could estimate the size of w$_{1}$ and w$_{2}$ like this:
		Say w$_{1}$ and w$_{2}$ are both 50 and 0.1, also the bias is 50
		![[Pasted image 20240404012312.png]]
		If we calculate those parameters like the picture above, we will obtain 1 million for the price of the house which is very large compared to 500k.
		In another case, say w$_{1}$ and w$_{2}$ are 0.1 and 50, also the bias is still 50. 
		![[w2_scale_3.PNG]] 
		When we use 0.1 for w$_{1}$ and 50 for w$_{2}$, we obtained a more reasonable output. That means the good model is likely learn to choose the large parameter for the small range and small parameter for the large range. 
	- This is the correlation between those two parameters:
		![[w2_scale_4.PNG]]
		We could notice that the horizontal axis is larger that the vertical axis. When we see the contour plot for parameters, we can notice that parameter for size is smaller than parameter for numbers of bedroom. 
		So, the gradient descent will be like this:
		![[w2_scale_5.PNG]] 
	- When we do the feature scaling, the features range is more likely comparable:
		![[w2_scale_6.PNG]]
- How do we implement feature scaling?
	- Remember this data
		![[w2_scale_7.PNG]] 
	- Because the range of the data is large, we can scale them into a smaller range in this way
		![[w2_scale_8.PNG]]
		
- We can also do 'Mean Normalization' by doing this:
	- Find the average of each feature on the dataset called Mu ($\mu$) 
	- Subtract each value on each feature to the Mu and divide to the value from max value minus min value
	![[w2_scale_9.PNG]]
	
- There's also another rescaling way named Z-score Normalization:
	- First, determine the Mu ($\mu$) as the mean of each feature. Then, calculate the standard deviation $\sigma = \sqrt{\frac{{\sum(xi-\mu)^2}}{N}}$ 
	- After that, subtract each value of each feature to the mean Mu and then divide it by the standard deviation
	![[w2_scale_19.PNG]]
	
- It's okay to have ranges like:
	- $-1 \leq x_{i} \leq 1$
	- $-2\leq x_{i}\leq 0.5$, or
	- $0.3\leq x_{i}\leq 0.3$ 
	Because it's still not in large range of values. It's okay to rescale it as we want but it's also okay that we leave it alone
	But, if we have range like $-100\leq x_{i}\leq 100$, then we have to rescale it because it's a large range. 

**Checking the Gradient Descent Convergence**
- Remember that we use Gradient Descent to find the best parameter w and b in minimizing the cost
![[w2_check_1.PNG]]
- Each point in the curve( Learning Curve ) is corresponds with each number of iterations for function $J(\overrightarrow w, b)$. The right curve is when the function $J(\overrightarrow w, b)$ is decreased after every iterations. 
- As we can see, after 300 iterations the curve seems flattened, so it's converged. 
- Note that for different application, we could obtain different number of iterations until its converged

**Choosing Learning Rate**
- Note: If our curve goes up sometimes and sometimes goes down, it's a sign that our model isn't working properly
	![[w2_learning_1.PNG]] 
	It can be caused by a bug in the code or learning rate is too large
	![[w2_learning_3.PNG]] 
	Curve also above can be caused by learning rate that is too large or bug in the code. Example: We write the code like this $w_{1} = w_{1} + \alpha d_{1}$ . In that code, we use add instead of subtract that causing the cost move further from minimum cost. 
	
- Learning rate that is too small also can cause the gradient descent work slowly 
![[w2_learning_2.PNG]] 
- A way that we can do in choosing learning rate is we can set a list of learning rate that we can try
	![[w2_learning_4.PNG]]
	For each value, after we finish do the gradient descent, we could increase the value upto 0.003 from 0.001 
	![[w2_learning_5.PNG]] 
	We can keep doing this until we found the value of that's too small and then also make sure I've found a value that's too large. We could slowly try to pick the largest possible learning rate
	![[w2_learning_6.PNG]] 

**Feature Engineering** 
- Refers to process transforming raw data into relevant information for the machine learning model.
- We can do feature engineering to create a new feature from raw feature. Example: We can create a new feature 'Area of House' from two feature 'Width' and 'Frontage' feature. 
- Feature engineering including: 
	- Feature Extraction
	- Feature Creation
	- Exploratory Data Analysis
	- Transformation
	- Benchmark

**Polynomial Regression**
- Form of regression analysis in which the relationship between the independent variables and dependent variables are modeled in the $n^{th}$ degree polynomial
- Imagine we have data like this:
![[w2_pol_1.PNG]]
- From the data above we could notice that it doesn't look like straight line. So we could fit a curve, quadratic? cubic?
	- Based on the plot, it couldn't be quadratic, because it would look like this
		![[w2_pol_2.PNG]] 
		When we use it to predict, the curve will goes down after reach the maximum because it's quadratic
		Maybe we could fit the data with curve like:
		![[w2_pol_3.PNG]] 
		Using the $3^{th}$ polynom. 

## Classification 
- An algorithm that takes input and categorized the class based on inputs
- A classification where there are only two possible categories called Binary Classification. Example: We classify whether a tumor is malignant or benign

**Logistic Regression**
- In classification, logistic regression will fit a curve like this
![[log_1.PNG]] 
 - The output of logistic regression will always be 0 or 1, despite the algorithm set the threshold to 0.7 or 0.5.
 - In logistic regression, there's a mathematical function called sigmoid function or logistic function like this
	 ![[log_2.PNG]] 
 - The output of logistic function will be 0 or 1, using formula $g(z) = \frac{1}{1+e^{-z}}$. That's why when we have a large negative value, the output will be close to 0 and when we have a large positive value, the output will be close to 1. 
 - Logistic Algorithm consists of two steps:
	 - First, calculate the value of $z$ which is from linear regression formula $f_{\overrightarrow w,b}(x) = \overrightarrow w \cdot \overrightarrow x + b$ . The output will be $z$ 
	 - After that, we assign $z$ value to formula $g(z) = \frac{1}{1+e^{-z}}$ 

**Decision Boundary**
- Decision boundary is a horizontal line that separates 0 and 1 region 
- Formula $f_{\overrightarrow w,b}(x) = g(\overrightarrow w \cdot \overrightarrow x + b) = \frac{1}{1+e^{-(\overrightarrow w \cdot \overrightarrow x + b)}}$ can be interpreted as $P(y=1\:|\: x; \overrightarrow w,b)$ which means the probability of getting y is equal to 1 given x as input and w, b as parameters. 
- Let's say we set the threshold or the boundary to be 0.5. It means if $f_{\overrightarrow w,b}(x) \geq 0.5$ then the $\hat{y}$ or predicted y will be 1 and if the $f_{\overrightarrow w,b}(x) < 0.5$ then $\hat{y}$ will be 0
![[log_3.PNG]]


**Cost Function for Logistic Regression**
- In initial, we could say that the cost function in logistic regression is divided into two condition:
	- If $y = 1$ then the formula is: $-\log(f_{\overrightarrow w,b}(\overrightarrow x^{i}))$ 
		![[los_1.PNG]]
	- If $y = 0$ then the formula is: $-\log(1 - f_{\overrightarrow w,b}(\overrightarrow x^{i}))$ 
		![[los_2.PNG]]
	- With those choices of loss function, the overall cost function will be convex and we could find the global minimum
- Based on the previous equations, we can simplify the loss function into this formula
	![[los_3.PNG]]
	This formula is equivalent to the two formula above
	This is the case for that formula:
	- When $y = 1$ then 
		=> $-y^{(i)}\log(f_{\overrightarrow w,b}\:(\overrightarrow x^{\:i}))\: - \:(1-y^{(i)})\: \log(1 - f_{\overrightarrow w,b}(\overrightarrow x^{\:i}))$ 
		=> $-1\log(f_{\overrightarrow w,b}\:(\overrightarrow x^{\:i}))\: - \:(1-1)\: \log(1 - f_{\overrightarrow w,b}(\overrightarrow x^{\:i}))$  
		=> $-1\log(f_{\overrightarrow w,b}\:(\overrightarrow x^{\:i}))$ 
	- When $y = 0$ then
		=> $-y^{(i)}\log(f_{\overrightarrow w,b}\:(\overrightarrow x^{\:i}))\: - \:(1-y^{(i)})\: \log(1 - f_{\overrightarrow w,b}(\overrightarrow x^{\:i}))$
		=> $0\log(f_{\overrightarrow w,b}\:(\overrightarrow x^{\:i}))\: - \:(1-0)\: \log(1 - f_{\overrightarrow w,b}(\overrightarrow x^{\:i}))$
		=> $-\:(1-0)\:\log(1 - f_{\overrightarrow w,b}(\overrightarrow x^{\:i}))$
- If we plug in the simplified loss function to cost function, it will turn into
	![[los_4.PNG]] 

**Gradient Descent Implementation**
- As Gradient descent does in linear regression, Gradient Descent also works in logistic regression. 
- To do gradient descent for logistic regression, we need to calculate the partial derivatives of $J(w,b)$ concerning w and b 
![[los_5.PNG]]

**Overfitting Problem**
- Overfitting occurs when the model fits very well to training data but poorly generalize the new data
- Here's a visualization:
	![[overfit_1.PNG]]
- What can we do to solve this problem?
	- Collect more training data
	- Select only relevant feature or subset of features that you think are the most useful since there will be many features but insufficient data. This technique has a weakness that is the algorithm can throw away some of the information about the data 
	- Do regularization
		- Refers to technique that shrinks the coefficient estimates towards zero
		- Used to calibrate machine learning models in order to minimize the adjusted loss function and prevent overfitting or underfitting
		![[reg_1.PNG]] 
		- By convention, normally just reduce the size of the $w_{j}$ parameters, that is $w_{1}$ through $w_{n}$. If we want to reduce b, it won't make a huge difference. 
- Example case for regularization:
	Say we have this dataset
	![[reg_2.PNG]]
	As we can see, there's a bunch of features and consider it's hard to choose which feature we want to include and exclude.
	This is the case where regularization are needed. So we penalize all of the features a bit and shrinks them by adding a new term to the cost function
	=> $J(\overrightarrow w, b) = \frac{1}{2m} \sum_{i=1}^{m}(f_{\overrightarrow w,b}(\overrightarrow x^{\:i})-\:y_{i})^2\: + \: \frac{\lambda}{2m}\sum_{j=1}^{n}w_{j}^2$ 
	We can call the lambda as regularization parameter and we have to choose the right lambda. Additionally, by scaling both term by $2m$ it is easier to choose the right lambda. 
	
	![[reg_3.PNG]]
	In the implementation, we minimize the first term which is the original cost function is to encourage the algorithm to fit well and keep the second term minimize to prevent overfitting, also keep the parameter $w$ small. 
- Why it's important to choose the right lambda?
	- If the lambda is too small like $0$, then the model will become overfit since the coefficients aren't shrink
	- If the lambda is too large, the model will become underfit since the way to overcome the large lambda is to minimize the value of w very close to $0$
	![[reg_4.PNG]] 

**Regularized Linear Regression**
- Previously, we learned about linear regression without regularization, so the gradient descent would come just with the original cost function
- With regularization, the gradient descent in linear regression would be like this
	![[regu_lin_1.PNG]]
- Below this, there's a visualization about how gradient descent works with regularization
	![[regu_lin_2.PNG]]
	So with regularization, we just shrink the parameter $w_{j}$ a little bit on every iteration
- Also, this is how the derivative works behind the gradient descent with regularization
	![[regu_lin_3.PNG]]

**Logistic Regression with Regularization**
- Logistic regression with regularization is just similar to linear regression with regularization but with different definition for $f_{\overrightarrow w,b}(\overrightarrow x)$ 
- Now, let's say we have z as a high order polynomial fits that get passed to sigmoid function. When we work with many features in logistic regression, there's a risk that the model will be overfit. So we have to do regularization
![[regu_log_1.PNG]]
- How to implement the gradient descent in logistic regression?
	In logistic regression, we have this equation for cost function
	![[regu_log_2.PNG]]
	To get optimal parameters and regularize the $w_{j}$ parameter, we have to do gradient descent on logistic regression
	![[regu_log_3.PNG]]
	It's just similar to what we do to linear regression, but with different derivative with respect to $w$. 