# CNN-to-classify-ImageNet-images
In this project CNN was implemented to classify Corgi dog images from the ImageNet consisting of two different Corgi breeds: Pembroke and Cardigan. Two folders were provided containing training and test data (training_data and testing_data respectively) which each had subfolders containing images of Pembroke corgis and Cardigan corgis. The objective was to design a deep learning model and train the CNN to classify the test data into two image labels with minimum error (high accuracy). Writeup by: Nader Ekramirad Spring 2020 Experiments: The main steps:
1.	Data loading and preparation (normalization between 0 and 1)
2.	Define the model class (set Hyperparameters)
3.	Forward run and calculating loss
4.	Backpropagate predefined number of times (epoch loop) and optimize weights
5.	Predict the labels of test images and calculate accuracy OpenCV was used to load datasets into PyTorch. To do that a function was written which took the “folder path”, “images size” and “classes” as input arguments and returned images (normalized pixel values), labels, image names and classes. Then a class was defined which converted the NumPy array images to torch tensors (with four dimensions as batch size, channels, image width and image height) and labels to a tensor with maximum index value for each image (0 or 1 based on which index being the value of “1”). After dataset preparation, the first step was to define the model which was an inherent class of “nn.Module” class. To do so, the structure of neural network was designed and then the important hyperparameters was set. This network has three convolution layers with a filter size of 3×3 and 32 filters at first and second layers and 64 at the third one. After each convolution layer the output was normalized using “nn.BatchNorm2d” function and then activated using ReLU function followed by a pooling operation ( 2×2 max pooling). The was also a hidden layer at the fully connected layers with 128 nodes. At the final two nodes, SoftMax was used to calculate the probabilities associated with each output. After defining the model, a forward pass was run using a batch of training images and the loss was calculated by “cross-entropy” method. Also, “stochastic gradient descent” method was selected to do the optimization in the backward pass. In order to fully train the model, a training loop was defined to go through the input to output for the defined number of epochs. Finally, after getting the model trained, the test data images were fed into the model and the accuracy of it performance was calculated. Results: For the training dataset, using the following hyperparameters as; learning rate=0.0000001, batch size of four and number of epochs=1000, the model gave an accuracy of 82.09%. But for the test dataset, with the same hyperparameters, the model gave an accuracy of 75%.

