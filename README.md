# Traffic_sign_classifier
Using deep neural nets to classify German traffic datatset
# Data Set Summary & Exploration
I used the pandas library to calculate the summary statistics of the traffic signs dataset.
  * The size of training set is ?
  * The size of the validation set is ?
  * The size of test set is ?
  * The shape of a traffic sign image is ?
  * The number of unique classes/labels in the data set is ?
  
This barchart shows how the data is classified in  different classes
![class_dataset](https://cloud.githubusercontent.com/assets/26694585/24799185/88b2656c-1bb7-11e7-8bda-e2cedf91ec59.png)

As a first step, I decided to convert the images to grayscale because 
Here is an example of a traffic sign image before and after grayscaling.


As a last step, I normalized the image data between -0.5 to 0.5. I performed normalization so that all my data is on the same scale. If the data is not normalized the backpropogated error change for the weights will differ, and the network will not ttrain well.

I decided to generate additional data from both the internet and by also clicking photos of road signs in Mumbai, India. Since the training images of German traffic signs provided to us might have been taken from the internet, I felt that taking photos locally can help test my network better.
  
