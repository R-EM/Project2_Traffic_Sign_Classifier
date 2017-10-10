#**Traffic Sign Recognition** 

##Writeup


**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


Step 0: Load The Data
This step is very straight forward. Load the training, validation and testing datasets (both features and labels).

Step 1: Dataset Summary & Exploration
In this step, we begin by checking the sizes and shapes of each dataset. A list with this information is priented in the code.

Step 2: Design and Test a Model Architecture
In this step, the data is pre-processed by first converting the datasets to grayscale, then nomralising it, and finally shuffling it.

Next, the Lenet model is modified according o the article that was linked, which was written by Pierre Sermanet and Yann LeCun. Here, a third convolution layer is added, and both layers 2 and 3 are flattened and concatenated. The new concatenated layer is then passed on to one final, fully connected layer instead of three. Validation gives a 95.6% accuracy.

Step 3: Test a Model on New Images
In this step, the model is tested using both the test dataset and a few other pictures. When using the test dataset, an accuracy of 94.5% is obtained, which is greater than the  minimum requirement of 93%. Success!

Next, some images were downloaded using a quick google search for some of the German traffic signs used. These images were then processed the same way the gived datasets were, and the results were presented in the end. The lowest uncertainty noted in this comparison was for the "Children crossing" sign, with an accuracy of 93.62%. This still meets the minimum requirement, showing that the model successfully meets the necessary requirements to pass.