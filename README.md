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

Step 2: Preprocessing
Seeing how the images represent traffic signs, and color is not something that we wish to identify, converting the images to grayscale would allow us to ignore color while training the network. Converting an image to grayscale is easily done by calculating the mean of each pixel across all three RGB levels.

Next, the data is normalized. This would greatly reduce the magnitude of the values we work with. In this case, it is important to do so, since the values of the images vary greatly, and the learning rate might not have the desired effect due to these large differences.

Finally, the data is shuffled before being passed on. This allows us to avoid having entire minibatches of highly correlated examples.

Step 3: Design and Test a Model Architecture
The Lenet model is modified according to the article that was linked, which was written by Pierre Sermanet and Yann LeCun. Here, a third convolution layer is added, and both layers 2 and 3 are flattened and concatenated. The new concatenated layer is then passed on to the fully connected layers, which were reduced to two instead of three. Validation gives a 95.6% accuracy.

The main reason that this architecture was chosen, was due to the fact that the original LeNet architecture did not provide satisfactory results (Around 5% accuracy). The was mainly due to the fact that there were only two convolutional layers used. Adding a third convolutional layer allows the network to work with more complex identification, such as identifying a traffic sign. From the very first epoch, we can see how an accuracy of over 70% is achieved, which is clearly higher than 5%, which proves that we are on the right track.

Worth mentioning here is that the article seems to use only one fully connected layer, whereas this project uses two. Both were tested, and it was found that two fully connected layers gave a slight increase in accuracy. The reason for choosing one over the other is further explained in step 5.

Step 4: Parameter truning
At first, a constant learning rate of 0.0001 was chosen, which resulted in slow improvement on the learning rate from early on. A bigger learning rate would surpass 90% somewhat quicker, but would not reach the same accuracty as a smaller learning rate would with more epochs. For this reason, descending learning rate was chosen, where the first three epochs would use a learning rate of 0.001, epochs four through ten would use a learning rate of 0.0005, and all epochs above 10 (11 and on) would use a learning rate of 0.0001. The idea behind this choice is to accelerate the improvement of the validation accuracy, while still reaching the same validation accuracy as a lower learning rate would reach using a less amount of epochs. No more than a total of 15 epochs were chosen, since no real improvement was gained after the 12th epoch.

A batch size of 128 was chosen, since too low of a batch size seemed to increase computation time, but a higher batch size did not seem all that necessary.

Step 5: Test a Model on New Images
In this step, the model is tested using both the test dataset and a few other pictures. When using the test dataset, an accuracy of 94.5% is obtained, which is greater than the  minimum requirement of 93%. Success!

New images:
Next, some images were downloaded using a quick google search for some of the German traffic signs used. These images were then processed the same way the gived datasets were, and the results were presented in the end. The lowest uncertainty noted in this comparison was for the "Children crossing" sign, with an accuracy of 93.62%. This still meets the minimum requirement, showing that the model successfully meets the necessary requirements to pass. The model was able to successfully classify all 5 images, which results in 100% accuracy for these images. The main reason for this rate of accuracy is that the chosen images look a lot like the ones used for training. When testing this model with an image of a traffic sign that was located at the bottom right of the image, with more padding to its left and above it, the model was unable to classify the image, which resulted in a total accuracy of 80% if it was replaced with one of the 5 images tested.

Worth mentioning here is that one fully connected layer instead of two was tested according to the article, and only an accuracy of 80% was obtained on the softmax probabilities test, since one image failed to receive a correct prediction, which is why two, fully connected layers were chosen over one in the end. It may of course be possible to eliminate all errors for the softmax text if more epochs are used for both, but I will settle for a working model using 15 epochs.