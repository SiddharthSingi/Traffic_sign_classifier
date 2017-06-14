
# Traffic_sign_classifier
Using deep neural nets to classify German traffic datatset.
## Project Summary
In this project I have used Deep Learning to train my model to be able to correctly identify images of German Traffic Signs. I then 
tested my model on new images taken from the internet and images of traffic signs that i clicked in Mumbai.

# Data Set Summary & Exploration
I used the pandas library to calculate the summary statistics of the traffic signs dataset.
  * The size of training set is 34799
  * The size of the validation set is 4410
  * The size of test set is 12630
  * The shape of a traffic sign image is 32x32x1
  * The number of unique classes/labels in the data set is 43
  
  
This barchart shows how the data is classified in  different classes
![class_dataset](https://cloud.githubusercontent.com/assets/26694585/24799185/88b2656c-1bb7-11e7-8bda-e2cedf91ec59.png)



**Build a Traffic Sign Recognition Project**

The steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./examples/visualization.jpg "Visualization"
[image2]: ./examples/grayscale.jpg "Grayscaling"
[image3]: ./examples/random_noise.jpg "Random Noise"
[image4]: ./examples/placeholder.png "Traffic Sign 1"
[image5]: ./examples/placeholder.png "Traffic Sign 2"
[image6]: ./examples/placeholder.png "Traffic Sign 3"
[image7]: ./examples/placeholder.png "Traffic Sign 4"
[image8]: ./examples/placeholder.png "Traffic Sign 5"

## Rubric Points
###Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/481/view) individually and describe how I addressed each point in my implementation.  

---
###Writeup / README

####1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. You can use this template as a guide for writing the report. The submission includes the project code.

You're reading it! and here is a link to my [project code](https://github.com/udacity/CarND-Traffic-Sign-Classifier-Project/blob/master/Traffic_Sign_Classifier.ipynb)


### Data Set Summary & Exploration
I used the pandas library to calculate the summary statistics of the traffic signs dataset.
  * The size of training set is 34799
  * The size of the validation set is 4410
  * The size of test set is 12630
  * The shape of a traffic sign image is 32x32x1
  * The number of unique classes/labels in the data set is 43
  
  
This barchart shows how the data is classified in  different classes
![class_dataset](https://cloud.githubusercontent.com/assets/26694585/24799185/88b2656c-1bb7-11e7-8bda-e2cedf91ec59.png)


###Design and Test a Model Architecture

####1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, and provide example images of the additional data. Then describe the characteristics of the augmented training set like number of images in the set, number of images for each class, etc.)

As a first step, I decided to convert the images to grayscale because the shape of the traffic signs are more important than its color in identification of its class. Also using colored images requires more processing power which is not worth the small increment in the accuracy.
Here is an example of a traffic sign image before and after grayscaling.

![grayscale](https://user-images.githubusercontent.com/26694585/27131584-eabb39a4-5128-11e7-8573-03ec0cb6aeef.jpg)



As a last step, I normalized the image data between -0.5 to 0.5. I performed normalization so that all my data is on the same scale, and the updated weights value each feature equally. If the data is not normalized the backpropogated error change for the weights will differ, and the network will not train well.

I decided to generate additional data from both the internet and by also clicking photos of road signs in Mumbai, India. I felt that taking photos locally can help test my network better.


To add more data to the the data set, I clicked images from my phone and took photos from the internet. I then cropped these images in a 
32x32x3 format


####2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

My final model consisted of the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x3 RGB image   							| 
| Convolution 5x5     	| 1x1 stride, valid padding, outputs 28x28x6 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 14x14x6 				|
| Convolution 5x5	    | 1x1 stride, valid padding, outputs 10x10x16     									|
| RELU					|	Activation Layer											|
| Max pooling	      	| 2x2 stride,  outputs 5x5xx16				|
| Fully connected		| Output shape 400       									|
| Fully Connected				| Output shape 120      									|
| Dropout     | Keep probability = 0.7   |
|	Fully Connected					|	Output shape 84											|
| Dropout     | Keep probability = 0.7   |
|	Fully Connected					|	Output shape 43											|
| Softmax             | Activation Layer          |
 


####3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

To train the model, I used an AdamOptimizer to minimize the cross entropy loss of my softmax outputs. I used the default learning rate of 0.001, a batch_size of 128 and trained my model on 12 epochs. To initiate the weights I used truncate_normal with mean = 0, and standard deviation = 0.1

####4. Describe the approach taken for finding a solution and getting the validation set accuracy to be at least 0.93. Include in the discussion the results on the training, validation and test sets and where in the code these were calculated. Your approach may have been an iterative process, in which case, outline the steps you took to get to the final solution and why you chose those steps. Perhaps your solution involved an already well known implementation or architecture. In this case, discuss why you think the architecture is suitable for the current problem.

My final model results were:
* training set accuracy of 
* validation set accuracy of ? 
* test set accuracy of ?

If an iterative approach was chosen:
* What was the first architecture that was tried and why was it chosen?
* What were some problems with the initial architecture?
* How was the architecture adjusted and why was it adjusted? Typical adjustments could include choosing a different model architecture, adding or taking away layers (pooling, dropout, convolution, etc), using an activation function or changing the activation function. One common justification for adjusting an architecture would be due to overfitting or underfitting. A high accuracy on the training set but low accuracy on the validation set indicates over fitting; a low accuracy on both sets indicates under fitting.
* Which parameters were tuned? How were they adjusted and why?
* What are some of the important design choices and why were they chosen? For example, why might a convolution layer work well with this problem? How might a dropout layer help with creating a successful model?

If a well known architecture was chosen:
* What architecture was chosen?
LeNet Lab
* Why did you believe it would be relevant to the traffic sign application?
* How does the final model's accuracy on the training, validation and test set provide evidence that the model is working well?
 

###Test a Model on New Images

####1. Choose five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

Here are five German traffic signs that I found on the web:

![alt text][image4] ![alt text][image5] ![alt text][image6] 
![alt text][image7] ![alt text][image8]

The first image might be difficult to classify because ...

####2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set (OPTIONAL: Discuss the results in more detail as described in the "Stand Out Suggestions" part of the rubric).

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| Stop Sign      		| Stop sign   									| 
| U-turn     			| U-turn 										|
| Yield					| Yield											|
| 100 km/h	      		| Bumpy Road					 				|
| Slippery Road			| Slippery Road      							|


The model was able to correctly guess 4 of the 5 traffic signs, which gives an accuracy of 80%. This compares favorably to the accuracy on the test set of ...

####3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability. (OPTIONAL: as described in the "Stand Out Suggestions" part of the rubric, visualizations can also be provided such as bar charts)

The code for making predictions on my final model is located in the 11th cell of the Ipython notebook.

For the first image, the model is relatively sure that this is a stop sign (probability of 0.6), and the image does contain a stop sign. The top five soft max probabilities were

| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .60         			| Stop sign   									| 
| .20     				| U-turn 										|
| .05					| Yield											|
| .04	      			| Bumpy Road					 				|
| .01				    | Slippery Road      							|


For the second image ... 

### (Optional) Visualizing the Neural Network (See Step 4 of the Ipython notebook for more details)
####1. Discuss the visual output of your trained network's feature maps. What characteristics did the neural network use to make classifications?

