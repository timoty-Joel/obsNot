
### Introduction to Computer Vision
- Computer Vision is a field of machine learning that enables computer to understand, identify and labels what is interpreted in an image. 
	- For initial practice, we can use MNIST dataset from TensorFlow that contain numerous of images. ![[Bangkit Notes/Deep Learning/C1/CV_1.PNG]]Fashion MNIST contains around 70k images with 10 categories of clothes. The images has been rescaled to $28$ x $28$ pixel. 
- We can use neural network to build a model that can identify images. For an example:
	We can use MNIST dataset to build our CV model that identify clothes images that will be given. We can load the dataset by using API call from TensorFlow: `tf.keras.datasets.fashion_mnist`. In MNIST data, the images has been labeled with number. Why? Because, if the images is labeled with a language, say it english, the model wouldn't work for another language. So the simplest way is label it with a set of numbers.
- In training the model, we can set a **Callback** function when we fit the model. Callback is a tool in machine learning that allow us to automate certain processes during the training phase of model. There are some type of callback: Early stopping, Checkpoint, and Reduce on Plateau. 
	- For an example: ![[Bangkit Notes/Deep Learning/C1/CV_2.PNG]] Above, the kind of callback is Checkpoint. So when the loss function is below 0.4 the training phase will be stopped. When it stopped, then the message will be printed. ![[Bangkit Notes/Deep Learning/C1/CV_3.PNG]] After defined function on_epoch_end the myCallback class, we call it first then apply it to the model.fit
- In computer vision model, there are things called convolution layer and pooling layer inside the hidden layer. Convolution and pooling layer work in the model by processing the images. How Convolutions and Pooling work in computer vision model? and Why we need that?
	Why we need it in CNN:
	- Convolutional layer is very important in CNN because it is used to extract the feature from given data. 
	- Convolution can help the computer to determine features that could be missed in flattening an image into pixel values
	How it works: 
	- In convolution layer, images is convoluted with a kernel (or filter). ![[CV_7.webp]]                                        Above is an example of the kernel that is used in convolutional layer. 
	- Convolution phase consists of multiplication each pixel and its filter and summing them. ![[CV_6.PNG]]Image above shows us the new pixel of 192 is the sum of the 192 and its neighbor multiplication to the filter(red). ![[CV_4.gif]]
	- After convoluting each pixel in the images, we go to the pooling layer. There are  types of pooling that are common used: MaxPooling and AveragePooling. ![[Pooling_1.PNG]]In MaxPooling, we selects the maximum element from the region of the feature map, output after the max-pooling layer would be a **feature map containing the most prominent (brighter pixels) features** of the previous feature map. 
 