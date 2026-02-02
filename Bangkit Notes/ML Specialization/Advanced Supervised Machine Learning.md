## Neural Network Intuition
- A type of algorithm that is inspired by neuron in our brain. 
- Neural networks have taken off in the last few years because of the availability of large datasets and the availability of powerful computers, which allows us to train neural networks.
- In neural network, there's a thing called layer that contains a bunch of neuron(based on how many we set) that process our inputs.
	![[neu_1.PNG]]

**Neural Network Model**
- Neural Network model consists of three kinds of layer: Input layer(layer 0), Hidden layer, and Output layer. 
- Here's a example case for neural network
	Say we want to predict yes or no from an input contained 4 number like this
	![[nue_mod_2.PNG]]
	- As we can see, Hidden layer took an input from input layer or layer 0 and process it using sigmoid function as the activation function since we want to predict yes or no. 
	- There are 3 unit of neuron that perform a little bit of logistic regression in each neuron. The neuron will takes two input $w,\:b$ and process it in logistic function $a_{1}, a_{2}, a_{3}$. The output will be vector $\overrightarrow a$ consisted of 3 number: $0.3, 0.7, 0.2$. 
	- Number in square bracket indicates in which layer the quantity is associated to. Example: 
		$a_{n}^{[1]} = g(\overrightarrow w_{n}^{\:[1]}\: \cdot\:\overrightarrow x_{n}^{\:[1]}\: +b^{\:[1]})$ means this function occurs at layer 1
		
	![[neu_mod_3.PNG]]
	- Output from layer 1 will be input for layer 2 and processed by function in layer 2. The output will be single number that is used to decide whether yes or no for the prediction.
		![[neu_mod_4.PNG]]
- So for the computation inside a layer in hidden layer is denoted by: $\overrightarrow a^{\:[n]} = g(\overrightarrow w^{\:[n]}\:\cdot\:\overrightarrow x^{\:[n-1]}\:+b^{[n]})$ with $n$ means which layer they are associated to and $\overrightarrow a$  means the activation output. 
- Forward propagation refers to process that feed input data in the forward direction through the network and calculate it in neuron. 

**TensorFlow Implementation**
- Neural network can be used for inferencing from given input. Here's an example:
	Say we want to classify whether a coffee good or bad based on temperature and duration
	![[tf_im_3.PNG]]
	We can see that the classified as good coffee is in the triangle area. Now, our task is use the neural network to classify them
	![[tf_im_4.PNG]]
	Say, we have a new data in vector, 200 for temperature and 17 for duration and we will calculate that data to get the category. 
	![[tf_im_5.PNG]]
	From illustration above, the data is coded into an array using Numpy library. After that, we compute the data in layer 1 with 3 units of neuron. We use activation sigmoid to get the probability whether it's good or not but in array(vector $\overrightarrow a$) and then pass the activation output to the second layer with the same activation function that is sigmoid. Consider, the result we get is 0.8 and we will classify, 'is 0.8 good or bad coffee?'.
- In code, what is the difference when we use only 1 square bracket and 2 square brackets?
	- When we use two square brackets, the library will create 2D array with row and column, corresponds with the matrix or vector 
	- When we use only one square brackets, the library only will create a linear array in Python
	![[tf_im_6.PNG]]
- In TensorFlow there's a thing called tensor which is a data type that the TensorFlow team had created in order to store and carry out computations on matrices efficiently
- Explanation for example case in TensorFlow implementation:
	![[tf_im_7.PNG]]
- Example of forward propagation implementation from scratch:
	![[tf_im_8.PNG]]

### Additional: Speculations on Artificial General Intelligence
- AI is actually includes two different thing which are Artificial Narrow Intelligence and Artificial General Intelligence
	- Artificial Narrow Intelligence or ANI: an AI system that does one thing, a narrow task, sometimes really well and can be incredibly valuable. Example: smart speaker or self-driving car or web search, or AI applied to specific applications such as farming or factories. 
	- Artificial General Intelligence: an AI system that hopefully can do what human can do. 
- Despite we have made a lot of progresses in ANI, it doesn't mean we are near to the AGI. Much less a single logistic function is just so far from an accurate model of what the human brain actually does. 
- But there's still a hope for an AGI breakthrough:
	There have been some fascinating experiments done on animals that shows or strongly suggests that the same piece of biological brain tissue can do a surprisingly wide range of tasks. 
	This has led to the one learning algorithm hypothesis that maybe a lot of intelligence could be due to one or a small handful of learning algorithms. If only we could figure out what that one or small handful of algorithms are. 
	
	For an example: A result due to Roe et al showed that many different parts of the brain, just depending on what data is given can learn to see, or learn to feel, or learn to hear as if there was maybe one algorithm that just depending on what data or this given, learns to process that inputs accordingly.

**Vectorization**


## Neural Network Trainings

**Training in Detail**
- Previously we learn how logistic regression model was trained. Let's recall it:
	![[neu_train_1.PNG]]
	At first we have to specify the algorithm to compute the output based on given input x and parameters w, b. For logistic regression, we calculate $z$ first and then pass it to function $f(x)$ which is the logistic function. 
	The next step is specifying the loss and cost function for the logistic regression. As we can see, the definition of logistic loss is in the right side. After that, the cost function will calculate the average of loss function result. 
	The third step is training the model on data to minimize the cost. In training model, we use <ins>Gradient Descent</ins> to choose the best learning rate in order to minimize the cost. 
- Below this is an example the steps that we have to take in training model 
	![[neu_train_2.PNG]]
- Now, deep learning library has matured enough and we just have to use it properly in our task. Below this is an example of the steps when we use TensorFlow to train neural network model:
	- First, create the neural network model for logistic regression. 
		![[neu_train_3.PNG]]
		In this model, we use sigmoid function as the activation function to get logistic regression output and we set the units(neurons) in each layer. 
	- The second step, we define the loss and cost function for the logistic regression
		![[neu_train_4.PNG]]
		<ins>BinaryCrossEntropy</ins> is used because we want to do binary classification to predict whether the image is 0 or 1. Function $J$ is the cost function that aimed to calculate the cost overall parameters.
	- The third, we use Gradient Descent to find the best learning rate and the minimum cost for the model. 
		![[neu_train_5.PNG]]

**Activation Function**
- There are some alternative for sigmoid as activation function in neural network:
	- Some cases can't be solved by sigmoid function because their value can't be represented as 0 and 1. As an example, awareness about clothes or rate of knowledge maybe is better to be represented as probability of awareness or knowledge than 0 and 1 binary number. When we use sigmoid, the awareness or knowledge could be a negative number and it's not good. 
	- ReLu
		![[act_f_1.PNG]]
		Function above is called ReLu or Rectified Linear Unit. When the value of $z$ is smaller of equal to $0$ then, $g(z) = max(0, z)$. 
	- Leaky ReLu
	- Hyperbolic Tangent or tanh()
- Below this is a few of activation functions that common used
	![[act_f_2.PNG]]
- Choosing activation function is very important in building neural network model. When considering the activation function for output layer, it depends on what's the target 
	- If the target is binary classification then we naturally will choose sigmoid function
	- If the target is regression such as tomorrow stock's prediction, then we can choose linear activation function
	- If the target is regression with y only could be non-negative values, then we could choose ReLu as the activation function
- For the hidden layer, nowadays developers prefer to use ReLu as the activation function rather than sigmoid due to these reasons:
	- ReLu perform faster in neural network
	- ReLu only has one flat curve while sigmoid has two
		![[act_f_3.PNG]]
		You can see upper right and lower left, both have flat curve that can cause the gradient descent slower. When we have almost flat curves, the gradient descent will be like the right graph where gradient descent is slowing down in flat curves and the learning rate will only reduced a little bit. 
- Why we need activation function? 
	Because if the hidden layers were using linear activation function, then the neural network would be equivalent to a linear regression model, which defeats the purpose of using a neural network.

**Multiclass Classification**
- Multiclass Classification is a type of classification that allow us to categorize more than two classes but discrete. It means it couldn't be any number. 
	Here's an example for the difference between binary classification and multiclass classification
	![[multicl_1.PNG]]
- In logistic regression, we can only calculate the probability between two possible outputs such as 0 and 1. However, there's a solution called <ins>softmax</ins>
	Softmax is a type of activation function that scales numbers into probabilities or calculate the probability of an input belonging to a certain class.
	For the formula, softmax will be: $a_{j} = \frac{e^{z_{j}}}{\sum_{k=1}^{N}\: e^{z_{k}}}$ 
	![[multicl_2.PNG]]
	With softmax, we can calculate the probabilities for each classes by dividing it with the total of all classes calculations.
	When we calculcate the cost for logistic regression, we just use $a_{1}$ and $a_{2}$. In Softmax regression, we calculate each loss of the class with the corresponding actual value.  
	![[multicl_3.PNG]] 
- Softmax can be used in neural network layers for calculate the probabilities of each class. 
	![[multicl_4.PNG]]
	Above is the illustration of neural network that contains softmax in layer 3. 
	This is an example of softmax implementation using TensorFlow
- **Additional: How to Overcome Numerical Round-Off Errors**
	Numerical roundoff errors is  the difference between an approximation of a number used in computation and its correct (true) value.
	Below is an example of numerical roundoff errors in simple way:
	![[num_err_2.PNG]]
	
	Numerical roundoff error occurs due to the finite amount of memory to represent the precision of floating numbers. 
	For an example: 
	![[num_err-1.PNG]]
	In the image above, the value between the first and the second formula are slightly different each other. In logistic regression and softmax regression, both use $e$ which is an infinite constant number so due to the finite amount of memory, it can cause slightly numerical roundoff error. 
	But there's a way to overcome that error by expand the formula in mathematical way.
	In logistic regression, we can expand the formula to be:
	$loss = -y\:\log\left( \frac{1}{1+e^{-z}}\right) - (1-y)\log\left( 1-\frac{1}{1+e^{-z}} \right)$ 
	With that formula, TensorFlow can be more flexible in computing the loss by insisting a as the intermediate quantity.
	
	Here's the implementation:
	![[num_err_3.PNG]]
		Logits are the outputs of a neural network before the activation function is applied or we could logits as value $z$.  Logits are often used in classification tasks, where the goal is to predict the class label of an input. For example, if you are trying to classify an image of a cat or a dog, the logits would be the probabilities that the image is a cat or a dog.  
		The softmax function is then applied to the logits to normalize them to sum to 1. This ensures that the probabilities of all classes add up to 1 and that the most likely class has the highest probability.  
		Converting the logits to probabilities makes understanding the neural network's final output easier. You might have seen the `from_logits=True` argument in TensorFlow loss functions. By default, the value is false, meaning that you should define an activation function in the output layer of the network. If you don’t set an activation function, you should set the `from_logits=True` on the loss function so that it knows it’s receiving logits and not probabilities.
	When we applied `from_logits = True`, we have to set linear function as the activation in output layer. The Softmax function would be automatically applied on the output values by the loss function. 
	
	Here's another implementation in Softmax regression:
	![[num_err_4.PNG]]

	![[num_err_5.PNG]]

**Multilabel Classification**
- Multilabel classification is a different type of classification problem called a multi-label classification problem, which is where associate of each image, they could be multiple labels.
- Here's an example of multilabel classification:
	![[multi_lab_1.PNG]]
	
	![[multi_lab_2.PNG]]

**Additional Neural Network Concepts**
- **ADAM** algorithm is an optimization algorithm that will automatically update the parameter in gradient descent of a neural network model. 
- ADAM stands for Adaptive Moment Estimation. 
- ADAM optimization algorithm can increase or decrease the alpha or learning rate based on the step in gradient descent
	- If the step keep bouncing back and forth, then the algorithm will reduce the learning rate a little bit, and *vice versa*.
	![[adam_1.PNG]]
	- In image above, the left is the gradient descent without ADAM optimization, while the right is the gradient descent with ADAM algorithm
- In ADAM algorithm, while doing gradient descent, the algorithm will use more than one learning rate 
	![[adam_2.PNG]]
- Here's the implementation of ADAM algorithm in neural network
	![[adam_3.PNG]]

- Beside the neural network that is commonly known, there's another type called Convolutional Neural Network. 
- Previously, we know that in Dense layer, a neuron is a function for every activation input from the previous layer. 
- For an example, this is how convolutional layer works on images:
	![[conv_1.PNG]]
	Each neuron in convolutional layer will only looks at a region on the image. Say the blue neuron will only read the blue region on image, magenta neuron will only read the magenta region on the image, and so on. So, a neuron on convolutional layer won't read all of the pixel in an image.
- We could see the uses of convolutional layer on a case:
	![[conv_2.PNG]]
	In this case, we have a EKG data in 1D dimension that contain $x_{1},\:x_{2},\:x_{3},\: x_{4},\:\dots,\: x_{100}$. First, to simplify the visualization, we rotate the EKG data $90\degree$. Consider we have 9 units of neuron in convolutional layer. Let's say each layer will read 20 data. Thus, unit 1 will read $x_{1} - x_{20}$, unit 2 will read $x_{11} - x_{30}$, ... until unit 9 will read $x_{81} - x_{100}$. 
	Consider we have the second convolutional layer contain 3 units. Say each unit will read 5 data. Thus, unit 1 will read $a_{1}^{[1]} - a_{5}^{[1]}$, unit 2 will read $a_{3}^{[1]} - a_{7}^{[1]}$ and unit 3 will read $a_{5}^{[1]} - a_{9}^{[1]}$. The output layer will be sigmoid layer. 


## Advice for Applying Machine Learning

**Advice for Applying Machine Learning**
- Imagine we have built our model with regularization, normalization, etc. But what if there's still an error when training model ? What should we do?
	Here's what we can do:
	- Get more training examples
	- Try smaller sets of feature
	- Try getting additional features
	- Try adding polynomial features like $x_{1}^{2},\:x_{2}^{2},\:x_{1},\:x_{2}$
	- Try decreasing $\lambda$ in regularization
	- Try increasing $\lambda$ in regularization
- How to know that our model is doing well 
	- The answer is by training the model, splitting the dataset into two subset: training set and test set. 
		![[eval_1.PNG]]

	 - In order to evaluate the model, we need the cost function to see the error of test and training. Commonly, cost function will look like this
		![[eval_2.PNG]]
		So, basically the $Jtest$ and $Jtrain$ error function are just the same with the function without regularization.
		Here's this is a error function for classification problem
		![[eval_3.PNG]]
		But, there's another way that is commonly used. The way is to use the fraction of train set and test set that algorithm has misclassified
		![[eval_4.PNG]]
	- If the training set error is low, but the test set error is high, then the model is overfitting.
	- If the training set error is high, then the model is underfitting.
	- If the training set error is low, and the test set error is low, then the model is working well.
- Choosing well means saving a lot of time that would otherwise be wasted, but choosing correctly could be **tricky** 
- Since our model won't generalize well in real case, there's a method to make our model will generalize well when we fit it to test set. The method is called Cross Validation. Cross Validation is a procedure to evaluate the performance of learning models. 
	Imagine we have a list of regression model that we have to choose
	![[cv_1.PNG]]
	Say we choose the fifth model because the $Jtest$ is the lowest. But how can we know that the fifth model can generalize well?
	![[cv_2.PNG]]

	We can overcome the overly optimistic estimate by splitting the dataset into 3 groups:
	![[cv_3.PNG]]
	Here's the formula for compute the errors of the 3 groups of set
	![[cv_4.PNG]]

	Let's say, after we test the models with cross validation, we able to get the best model
	![[cv_5.PNG]]

**Bias and Variance**
- In building a machine learning model, we almost always find that it won't work as well as we wish at the first. Decide what to do in order to improve the performance is an important thing in building a machine learning model. Bias and Variance are found as a very good guidance for us. High bias or high variance could make our model perform badly because they make the model isn't able to capture the underlying pattern and sensitive to changes of data.
- What is the indicator of high bias or high variance?
	High Bias
	- $JTrain$ score is high
	- $JCrossValidation$ score is high
	High Variance
	- $JTrain$ score is low
	- $JCrossValidation$ score is high due to bad generalization
	
	Here's the curve about how degree of polynomial or model complexity affect the bias and variance
	![[diag_bv_1.PNG]]
		"$>$" means greater than
		"$\gg$"means much greater than
	
	But there will be a case where both high bias and high variance occur. Here's the indicator
	![[diag_bv_2.PNG]]
	It occurs when we fit the training set really well and we overfit in part of the input, and we don't even fit the training data well, and we underfit the part of the input
	
	The curve also occurs when we do regularization on the model but in mirrored way
	![[diag_bv_3.PNG]]
- In building machine learning model, we can't directly conclude that our model has high bias or high variance by only looking at the error percentage. We need another element at judging our model called **baseline level of performance**. Baseline level of performance is the level of error that we can expect from our model
	- Example: 
		![[baseline_1.PNG]]
		When training our model, we get 10.8% error at our model but looking at the human error performance has awaken us that it's only 0.2% from human error. It means that our model performed quite well. However, there's a 4.0% gap to the cross validation, that means our model has high variance because it much worse that the training error. 
- Here's some example of baseline level of performance:
	![[basline_2.PNG]]
	We can compare it to human level of error, competing algorithms performance such as previous implementation by someone or competitor's algorithm, and we also can compare to our prior experience using that algorithm. 
- Here's an example of comparing error to the baseline level
	![[baseline_3.PNG]]

**Learning Curve**
- Learning curve is a plot of model learning performance over experience or time.
	![[learn_curve_1.PNG]]
	Above is an illustration about learning curves. As we can see $Jtrain$ is getting bigger as the training set get bigger because it's hard to fit them all perfectly. While, the $Jcv$ score getting lower as the training set get bigger because the model learn better and better
- How is the learning curve when the bias is high or the variance is high?
	**High Bias**
	A model with high bias will have a learning curve like this
	![[learn_curve_2.PNG]]
	If the model has high bias, the $Jtrain$ and $Jcv$ won't meet each other even if with bigger size of training set. As we can see, the score of $Jtrain$ also much bigger than the human level performance. 
	
	**High Variance**
	Model that has high variance will has a learning curve like this
	![[learn_curve_3.PNG]]
	When we have a high variance learning curve, we could overcome it by getting more and more training set size bigger. Also, the $Jcv$ score curve getting closer and closer to the human level performance. The gap between the $Jtrain$ and $Jcv$ will get closer. 

**Machine Learning Development Process**
- In developing machine learning model, there's a development process loop consists of choosing model or architecture, training model and diagnostics. 
	![[dev_pro_1.PNG]]
	First, we have to choose the architecture of our system which means choosing your machine learning model as well as deciding what data to use, maybe picking the hyperparameters, and so on.
	After that we have to implement and train our model until it generalize well. We can't expect that our model will work perfectly at the first try, thus we need to diagnose our model. 
	We can choose another architecture and do the iterations until we get the performance that we want
- In improving a machine learning model, there's a term that is very important after the bias and variance called **error analysis**. 
- Error analysis is a process of looking at misclassification and try to find the cause of model mistakes. In error analysis, we can search for a sample of the misclassified data from cross validation set and group them into common traits or common properties
	- For example:
		![[error_an_1.PNG]]
		With 500 example from cross val, the model misclassified 100 of 500. After that, we manually classified them into several group. From the list, we can conclude that pharma spam and emails that are trying to phishing us are a huge problems.
		
		By grouping those errors, we can decide what the most fruitful error we pay attention to like we might build a new features that are related to say specific names of drugs or specific names of pharmaceutical products, or getting more data about Pharma spam, or build a better model to detect the phishing emails. 

- When dealing with some cases like high variance, we might want to get more and more data. Here's the tips of adding data:
	- Adding more data is tempting, but it is not always the best solution because trying to get more data of all types can be slow and expensive. 
	- We could focus on adding more data of the types where analysis has indicated it might help
	- Using **data augmentation**:
		Data augmentation is the process of creating new data from the data we already have.
		For an example. a data augmentation will look like this
		![[data_aug_1.PNG]]
		This is just a simple example. As we can see, the initial image was the first A and we modify the image using a certain library. When we modify it, the image will be stretched, rotated, enlarged, shrinked or distorted like this
		![[data_aug_2.PNG]]
		
		While in audio data, example of data augmentation will be like this
		![[data_aug_3.PNG]]
		Data augmentation for speech can be done by adding some noise to the original audio as a addition training set for the model
		However, the noise or distortion that we add should represent the test set's distortion or noises or else it would be less helpful. 
		![[data_aug_4.PNG]]
	- Another thing that we can do is **Data Synthesis**:
		Data synthesis is a process of creating a new brand data for training but not from existing data. 
		Example:
			![[data_syn_1.PNG]]
			Say we have a data OCR from this image that generate this kind of data
			![[data_syn_2.PNG]]
			Since we have so many font in our device, we can produce the similar data as the OCR make
			From
			![[data_syn_3.PNG]]  
			To
			![[data_syn_4.PNG]] 
- Since overall algorithm is working pretty well now due to machine learning enthusiast research. We can build a model using data-centric approach which is we pay attention more to the data. 

- For an app that doesn't have so much data, we could do a technique called **Transfer learning**. Transfer learning is a process of using a model that is already been trained by someone on different dataset to our new dataset. Here's the illustration:
	![[transfer_1.PNG]]
	Above is the illustration of transfer learning. At the first we build a neural network with 5 layers. Say, we have $1000$ output units(classes) from a large dataset. After training, consider we get the parameters $W^{[1]},\overrightarrow b^{\:[1]}$; $W^{[2]},\overrightarrow b^{\:[2]}$; $W^{[3]},\overrightarrow b^{\:[3]}$; $W^{[4]},\overrightarrow b^{\:[4]}$; and $W^{[5]},\overrightarrow b^{\:[5]}$ (Output layer). 
	In implementing transfer learning, we will take copy of the neural network model we made but we cut the last layer aka output layer and replace it with a much smaller output layer with just 10 rather than 1,000 output units. Those 10 layer will correspond to the 10 classes. 
	In transfer learning, what you can do is use the parameters from all the layers except the final output layer as a starting point for the parameters and then run an optimization algorithm such as gradient descent or the Adam optimization algorithm with the parameters initialized using the values from this neural network. 
	Notice there's two option of applying transfer learning:
	1. Only train output layers parameters
		Will suitable if we have a small training set. In option 1, we would just train the output layer and just hold the rest fix and don't even bother to change them, and use an algorithm like Stochastic gradient descent or the Adam optimization algorithm to only update $W^{[5]}, b^{[5]}$
	2. Train all the parameters
		Will suitable if we have a large training set. In option 2, we will train all the parameters in but the first four layers parameters would be initialized using the values that you had trained on top. 
- Why does transfer learning work?
	![[transfer_2.PNG]]
	Consider we want to build a neural network to detect handwritten digit. In image above, we have a neural network that has 4 layers. Each layer learned to detect each feature of a images such as edges, corners, and curves or basic shapes. For an example: layer 1 learned to detect edges, layer 2 learned to detect corners and layer 3 learned to detect curves. By learning to detect a lot of images, neural network will learn to those features.
	Thus, by learning to detect things as diverse as cats, dogs, car, people and so on, we help the model to learn detecting generic features. 
- Reminder: In transfer learning, we have to make sure that the input type is the same
	If we want to do transfer learning about computer vision, then we have to input images. 
![[transfer_3.PNG]]

- Here's the full cycle that we have to go through when building a machine learning model
	![[full_cycle_1.PNG]]
	- First, we have to define the scope of the project we going to build. In this phase we decide what is the project and what you want to work on. For example, I once decided to work on speech recognition for voice search. That is to do web search using speaking to your mobile phone rather than typing into your mobile phone.
	- After that, we have to collect the data. Decide what data we need to train our machine learning system and go and do the work to get the data we need.
	- After we get the data we need, then we can start to train the model we build. After we've started training the model, we could do the error analysis or a bias-variance analysis to tell us that we might want to collect more data. Maybe we could get more data of everything or just specific type where error analysis tells us that we want to improve the performance
	- The last part is deploying, monito and maintain our system. When we deploy a system we have to also make sure that we continue to monitor the performance of the system and to maintain the system in case the performance gets worse to bring us performance back up instead of just hosting your machine learning model on a server.

- Machine Learning is affecting billions of people and it is important to make it fair and ethical by making them unbiased and transparent
	There are some guidelines for us when building machine learning model
	![[fbe_1.PNG]]

