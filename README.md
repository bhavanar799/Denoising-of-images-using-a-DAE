Denoising AutoEncoders In Machine Learning
Autoencoders are types of neural network architecture used for unsupervised learning. The architecture consists of an encoder and a decoder. The encoder encodes the input data into a lower dimensional space while the decode decodes the encoded data back to the original input. The network is trained to minimize the difference between decoded data and input. Autoencoders have the risk of becoming an Identify function meaning the output equals the input which makes the whole neural network of autoecoders useless. This generally happens when there are more nodes in the hidden layer than there are inputs.
Denoising Autoencoder (DAE)
Now, a denoising autoencoder is a modification of the original autoencoder in which instead of giving the original input we give a corrupted or noisy version of input to the encoder while decoder loss is calculated concerning original input only. This results in efficient learning of autoencoders and the risk of autoencoder becoming an identity function is significantly reduced.
Architecture of DAE
The denoising autoencoder (DAE) architecture resembles a standard autoencoder and consists of two main components:
Encoder:
•	The encoder is a neural network with one or more hidden layers.
•	It receives noisy input data instead of the original input and generates an encoding in a low-dimensional space.
•	There are several ways to generate a corrupted input. The most common being adding a Gaussian noise or randomly masking some of the inputs.
Decoder:
•	Similar to encoders, decoders are implemented as neural networks with one or more hidden layers.
•	It takes the encoding generated by the encoder as input and reconstructs the original data.
•	When calculating the Loss function it compares the output values with the original input, not with the corrupted input.
What DAE Learns?
The above architecture of using a corrupted input helps decrease the risk of overfitting and prevents the DAE from becoming an identity function.
•	If DAEs are trained with partially corrupted inputs (e.g., with masking values), they learn to impute or fill in missing information during the reconstruction process. This makes them useful for tasks involving incomplete datasets.
•	If DAEs are trained with partially noisy inputs (gaussian noise) DAEs tend to generalize well to unseen, real-world data with different levels of noise or corruption as they learn to extract robust features. This is beneficial in various applications where data quality is compromised, such as image denoising or signal processing.
Objective Function of DAE
The objective of DAE is to minimize the difference between the original input (clean input without the notice) and the reconstructed output. This is quantified using a reconstruction loss function. Two types of loss function are generally used depending on the type of input data.
Mean Squared Error (MSE):
If we have input image data in the form of floating pixel values i.e. values between (0 to 1) or (0 to 255) we use mse
 
Here,
•	each of xi is the pixel value of input data
•	yi is the pixel value of reconstructed data
o	yi = D(E(xi*noise) )
o	Where E represents encoder and D represents decoder
•	this is summed over all the training set
Binary Cross-Entropy (log-loss):
If we have input image data in the form of bits pixel values i.e. values will be either 0 or 1 only then we can use binary cross entrop loss for each pixel value
 
Here
•	each of xi is the pixel value of input data with value being only 0 or 1
•	yi is the pixel value of reconstructed data.
o	yi = D(E(xi*noise))
•	Where E represents encoder and D represents decoder
•	this is summed over all the training set
Training Process of DAE
The training of DAE consists of below steps:
•	Initialze ender and decoer with random weights
•	Noise is intentionally added to the input data.
•	Feedforward the input data through encoder and decoder to get the reconstructed image
•	Calculate the reconstruction loss as defined in our objective function w
•	Do backprogoagation and update weights.The goal during training is to minimize the reconstruction loss.
The training is typically done through optimization algorithms like stochastic gradient descent (SGD) or its variants.
Applications of DAE
•	Image Denoising: DAEs are widely employed for cleaning and enhancing images by removing noise.
•	Audio Denoising: DAEs can be applied to denoise audio signals, making them valuable in speech-enhancement tasks.
•	Sensor Data Processing: DAEs are valuable in processing sensor data, removing noise, and extracting relevant information from sensor readings.
•	Data Compression: Autoencoders, including DAEs, can be utilized for data compression by learning compact representations of input data.
•	Feature Learning: DAEs are effective in unsupervised feature learning, capturing relevant features in the data without explicit labels.

