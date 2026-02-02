## Unsupervised Learning

**Clustering**
- Clustering is a technique in machine learning that is grouping similar data based on their characteristics or features. For an example: When we type 'Panda zoo' in search tools, we might get some article that contains panda or zoo or even both. 
- There are some step that we have to take in applying clustering. We do clustering by using an algorithm called K-means:
	- First, we randomly pick two points as the data centroid. Commonly, we can pick random data points from the set.  
		![[cluster_2.PNG]]
		In image above, there's 2 cluster because there are only 2 feature $x$. The data centroid point will be called $\mu$ (mu). The data centroid is vector with the same dimension as the data vector dimension that is 2.    
	- After that, we count each point distance to each centroid and group them together. We also have to assign each data point to the closest centroid 
		![[cluster_3.PNG]]
	- The next step is to move the centroid point to the average of assigned points
		![[cluster_4.PNG]]
		Remember that the value of each $x$ is vector corresponds to the number of feature. 
		But, what if there's any cluster doesn't have training examples after we move the centroid?
			To answer that, the most common thing that we could do is eliminate that cluster or set to be $k = k -1$. 	
		What if the data aren't well separated like this
			![[cluster_6.PNG]]
			Well, the algorithm seems will find the right cluster for that case. 
- Like the the other algorithm, K-means also has its function to minimize the cost of clustering, but how?
	- So K-means will minimize the squared distance between the data point $x^{(i)}$ and its cluster centroid $\mu_{c^{(i)}}$ without changing value of $c^{(i)}$ or the mu of cluster. After that, the algorithm will take the average of them. 
		![[cluster_7.PNG]]
		For an example, the algorithm will subtract the data point $s^{(10)}$ and $\mu_{c^{(10)}}$ as the distance between the $10^{th}$ data point. So, the what the algorithm really doing is trying to find the assignment of data point to which cluster centroid that minimize the distance. 
		![[cluster_8.PNG]]
	- The next step is moving the centroid to the location of the average from assigned data points. 
		![[cluster_9.PNG]]
		As we can see, at first the cost was $41$ when the centroid is placed closer to point 1. After that, we calculate the average of those two location and move the centroid to the corresponds location. 
- In applying K-means for clustering, sometimes we might find we're stucked in local minimum like this. 
	![[cluster_10.PNG]]
	That depends on what initial training example that we pick. So what can we do is iterate the k means multiple times using different initial training example as the centroid. 
	Here's an algorithm that we can use to avoid the high cost of K-means
	![[cluster_11.PNG]]
- Sometimes we will curious how to choose the number of K or cluster quantity. Basically, we can choose the number of k based on the elbow from the graph of K-means performance. 
	![[cluster_13.PNG]]
	But, what if the graph is looked like the right graph that is have no elbow
	Here's how to choose
	![[cluster_12.PNG]]



**Anomaly Detection**
- Anomaly detection is an algorithm of unsupervised learning that look at an unlabeled dataset of normal events and identify data points that don't confirm the normal behavior in the data
- A technique that we can do in anomaly detection is **Density Estimation**
	In density estimation we will calculate the probability of the data, so when we have a new data,  we have to calculate the probability of that data based on previous data or training data. 
	![[anom_1.PNG]]
	As we can see in the image, the center of the ellipse is the data with the highest probability. When the data is out from the ellipse then it would be detected as an anomaly. Data is out from the ellipse when the prob is smaller than $\epsilon$ (epsilon). 
- Gaussian Distribution is needed in applying anomaly detection
	- Gaussian Distribution is a bell-shaped curve distribution defined by the probability density function for a continuous random variable in a system.
	- As we can see image in below, the probability of data $x$ is depending of $\mu$ (mu) and $\sigma$ (sigma/standard deviation). If we put $x$ in function $p(x)$ we could get the bell-shaped distribution where mu is in the middle.![[gauss_1.PNG]]
	- This is how mu and sigma affect the distribution: ![[gauss_2.PNG]]
	- When using Gaussian distribution as an approachment, we have to estimate the parameter as well. We have to know what a good choice is for Mean parameter $\mu$ and Variance $\sigma^2$. 
		- Below this is an example for parameter estimation from a certain dataset.        ![[gauss_3.PNG]]
- When we apply the gaussian distribution approachment to anomaly detection, here's how it works:
	- Consider we have a training set that consists of $\overrightarrow x^{\:(1)}$ to $\overrightarrow x^{\:(m)}$ where each $x$ has n features $x_{1}, x_{2},\:\dots,\:xn$ in vector as shown in the image below.  For the probability, we built our model like the function $p(x)$ that multiply each probability of each data $x$. ![[gauss_4.PNG]]
	- Below this is the step of anomaly detection algorithm consists of 3 steps. Since we have the data is in vector-shaped, we will compute and fit the parameters in vectorized formula. After that, we could computer the $p(x)$ with given $x_{j}$ and its variance and mu. After fit the training dataset, we test the model with a new data, if the probability of the new data is below $\epsilon$ (epsilon) then the new data might be anomalous. ![[gauss_5.PNG]]
	- Below this is an anomaly detection example case: ![[gauss_6.PNG]]
- In developing and evaluation an anomaly detection system, one of the important things that we could pay attention is to evaluating the system. Thus, we could do a better decision making and improve the system more quickly
	- When you are developing a learning algorithm, such as: choosing different features or trying different values of the parameters like epsilon, making decisions about whether or not to change a feature in a certain way or to increase or decrease epsilon or other parameters, making those decisions is much easier if you have a way to evaluate the learning algorithm.
	- We could do real-number evaluation to improve our learning algorithm. The way to do this is having a cross validation and test for our model. In real number evaluation, it would be useful when we have a small number of anomaly examples that we can create cross validation and test set. ![[eva_1.PNG]]
	
	- For an example of real-number evaluation:
		![[eva_2.PNG]]
		Say we have to monitoring aircraft engine to see how many anomalous engines out of normal engines. Let's say we've collected 10,000 good engines and 20 anomalous data from observation. In training set, we used 6,000 data from 10,000 and it's okay if there are a couple of anomalous engines are got slipped into training examples. In cross-validation we used 2,000 good examples and 10 anomalous examples. By taking cross validation, we could tune the epsilon or the threshold and tune the features such $x_{j}$ so that we can get a better accuracy
		
		In test set, we used 2,000 good examples and 10 anomalous examples. After we tuned the features and parameters such as epsilon, we try to predict the test set to see how well the model finding the 10 anomalous examples. We could see how many data that the model flag the normal as anomalous or anomalous as normal. 
		
		We could do a alternative way when we have a quite small dataset so we can't divide them into cross-validation set and test set. The way is only do the cross-validation without test set but also with some downside such higher risk of overfit some of our decision around epsilon, choosing feature and so on.
	- Here's an image about evaluation algorithm in anomaly detection. ![[eva_3.PNG]]
- When thinking about assuming the anomalous examples as $y=1$ and the normal examples as $y=0$, we might think what's the difference to supervised learning. Here's why
	![[vs_1.PNG]]
	When we have 20 anomalous examples, the type of anomaly could be variating. For an example: when we checking aircraft engines whether there are any problem or not, the type of the problem may vary. It's maybe difficult to unsupervised learning to detect those problems. So, when we have enough examples for similar kind of anomaly such as spam (cause they're trying to sell similar things), supervised learning maybe a good choose.
	Here's some other examples: 
	![[vs_2.PNG]]
- Sometimes is reality, we won't always get an ideal features for our dataset. Sometimes, it would be skewed like image below. At the bottom left of the image, we can see that the features is left-skewed, and we have to make it bell-shaped so it would fit the data well.  We can do some transformations or operations in order to make the plot more gaussian. We could try a few values and pick something that looks right to use, that will work well for all practical purposes.![[feat_1.PNG]]**Reminder: If we apply transformations to our training set, also apply it to our test and cross validation set.** 
- We can also carry out an error analysis to know what part is the algorithm isn't doing well whereas making error. For an example: Below this is a problem where the normal and anomalous examples are both comparable, so when we calculate a new data that is anomalous, the algorithm will detect it as a normal example. What can we do is create a new feature based on the case. In detecting fraud, besides number of transactions, we can also check the typing speed whether it's normal or unusual fast. The creation of a new feature will make the algorithm to detect anomaly easier![[feat_2.PNG]] Here's some other example: ![[feat_3.PNG]]

## Recommenders System
