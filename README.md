# AutoEncoders

Design a convolutional autoencoder in a deep learning framework of your choice (Tensorflow, Pytorch, etc.). The goal is to train the autoencoder for the unsupervised task of image reconstruction. In the architecture of the autoencoder it should be possible to specify the size of the bottleneck layer (i.e. the dimension of the learned latent space). You can use any open source multi-class image dataset you like for training. Split the dataset into a training and test set. Run two training sessions: first with a dimension of the bottleneck layer of 2 and second with a dimension > 2, determined empirically to show a good tradeoff for image reconstruction. Investigate how well the two models work for the task of image reconstruction on independent test data. 
 
Next, take a number of random samples from the test set of your dataset (e.g. 1000 random samples) and use the two trained models to obtain latent vectors for each test sample. Now visualize the latent vectors and show how the classes in the test set distribute over space. For the model with latent space dimension of 2 use a scatter plot. For the model with higher dimension, use e.g. an existing dimensionality reduction technique like UMAP or t-SNE for plotting or some other visualization method of your choice (you can use an existing implementation for this). Can you identify meaningful cluster structures for the test samples in the latent space? Do the classes cluster well? How do the two representations learned from the two models compare?

## Solution

The following code proposes two solutions. 
The first is the simplest architecture for an auto encoder, where the encoder relie on a flattening operation to move from a 3D to a 1D vector representation of the image and a fully-connected layer of the dimension of the latent space. The decoder takes the output of the encoder, passes it to a fully-connected 28x28 layer which is reshaped. The activation functions used are a ReLU for the hidden layer and a sigmoid for the output layer, to introduce non-linear relationships in data. A classical loss function (MSE) is used.

The second proposes a more complex structure, where Dense layers are used to compress the input tensor to the latent vector dimension, the Dropout layers help prevent overfitting by randomly setting input units to 0 with a frequency of rate at each step during training time, and a LeakyReLU is used to introduce non-linearities.
