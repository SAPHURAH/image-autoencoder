
# Image Reconstruction Using an Autoencoder

## Project Overview

This project demonstrates how an autoencoder can learn to reconstruct handwritten digit images from the MNIST dataset.

An **autoencoder** is a type of neural network that learns to:

1. Compress an input into a smaller representation.
2. Reconstruct the original input from that smaller representation.

The project was implemented using PyTorch.

---

## Project Goal

The goal of this project is to understand how neural networks can learn useful representations of images through **compression and reconstruction**.

The model learns to take an image of a handwritten digit, compress the important information into a smaller representation, and then reconstruct the original image.

---

## Dataset

The project uses the **MNIST handwritten digit dataset**.

MNIST contains images of handwritten digits from **0 to 9**.

Each image is:

- 28 × 28 pixels
- Grayscale
- Represented using pixel values between 0 and 1 after conversion to tensors

The 28 × 28 image contains:

**28 × 28 = 784 pixels**

For this fully connected neural network, each image is flattened from:

**1 × 28 × 28**

into:

**784 values**

---

## Autoencoder Architecture

The autoencoder consists of two main parts:

```text
Input Image
     ↓
Encoder
     ↓
Latent Representation
     ↓
Decoder
     ↓
Reconstructed Image
````

### Encoder

The encoder compresses the 784-pixel image into a smaller representation.

```text
784 → 128 → 32
```

The layers are:

* Input: 784 values
* Hidden layer: 128 neurons
* Latent representation: 32 values

The **latent representation** is the smaller set of values that contains information the model learned to keep from the original image.

### Decoder

The decoder takes the 32-dimensional representation and reconstructs the original image.

```text
32 → 128 → 784
```

The reconstructed 784 values can then be reshaped back into a:

**28 × 28 image**

---

## Activation Functions

The model uses two activation functions.

### ReLU

**ReLU (Rectified Linear Unit)** is used in the hidden layers.

It helps the neural network learn non-linear patterns.

### Sigmoid

A **Sigmoid** activation function is used at the final decoder layer.

It produces values between:

**0 and 1**

This is useful because the MNIST pixel values are also represented between 0 and 1.

---

## Training

The autoencoder was trained using:

| Setting          | Value                    |
| ---------------- | ------------------------ |
| Loss Function    | Mean Squared Error (MSE) |
| Optimizer        | Adam                     |
| Learning Rate    | 0.001                    |
| Batch Size       | 64                       |
| Number of Epochs | 10                       |

### Mean Squared Error

**Mean Squared Error (MSE)** measures how different the reconstructed image is from the original image.

In simple terms:

> The smaller the MSE, the closer the reconstructed image is to the original image.

---

## Training Results

The training loss decreased over the 10 epochs:

```text
Epoch 1:  0.0363
Epoch 2:  0.0151
Epoch 3:  0.0118
Epoch 4:  0.0103
Epoch 5:  0.0093
Epoch 6:  0.0085
Epoch 7:  0.0080
Epoch 8:  0.0076
Epoch 9:  0.0073
Epoch 10: 0.0071
```

The decrease in loss shows that the model became better at reconstructing the training images during training.

---

## Reconstruction Results

The model was used to reconstruct MNIST images after training.

The results compare the original handwritten digits with their reconstructed versions.

![Reconstruction Results](images/reconstruction_results.png)

The reconstructed images generally preserve the main shape and structure of the original handwritten digits.

---

## How the Model Works

The complete process can be summarized as:

```text
MNIST Image
     ↓
28 × 28 Image
     ↓
Flatten
     ↓
784 Values
     ↓
Encoder
     ↓
128 Values
     ↓
32-Dimensional Latent Representation
     ↓
Decoder
     ↓
128 Values
     ↓
784 Values
     ↓
Reshape
     ↓
28 × 28 Reconstructed Image
```

The important idea is that the model is forced to pass the image through a much smaller representation of only **32 values**.

This encourages the network to learn important patterns in the images.

---

## What I Learned

Through this project, I learned how to:

* Work with image datasets using PyTorch
* Load the MNIST dataset using torchvision
* Convert images into tensors
* Understand image dimensions
* Flatten image data for a fully connected neural network
* Build an encoder
* Build a decoder
* Create an autoencoder using PyTorch
* Use ReLU and Sigmoid activation functions
* Train a neural network using batches
* Use Mean Squared Error for image reconstruction
* Use the Adam optimizer
* Monitor training loss
* Visualize reconstructed images

---

## Limitations

This project uses a relatively simple **fully connected autoencoder**.

Because the model uses fully connected layers rather than convolutional layers, it does not explicitly take advantage of the spatial structure of images.

The model is also primarily designed for **reconstruction**, rather than generating completely new images.

Basic autoencoders can learn useful compressed representations, but their latent spaces are not necessarily designed for controlled generation of new data.

---

## Future Improvements

Possible improvements to this project include:

* Building a convolutional autoencoder
* Experimenting with different latent-space sizes
* Comparing different activation functions
* Testing different optimizers and learning rates
* Evaluating reconstruction quality using additional metrics
* Comparing fully connected and convolutional autoencoders
* Exploring Variational Autoencoders (VAEs)
* Exploring how latent representations can be used for downstream tasks

---

## Technologies

* Python
* PyTorch
* torchvision
* NumPy
* Matplotlib
* Jupyter Notebook

---

## Project Structure

```text
image-autoencoder/
│
├── data/
│   └── MNIST/
│       └── raw/
│
├── images/
│   └── reconstruction_results.png
│
├── notebook/
│   └── 01_autoencoder.ipynb
│
└── README.md
```

---

## Conclusion

This project demonstrates how an autoencoder can learn a compressed representation of handwritten digit images and use that representation to reconstruct the original images.

The project provides a practical introduction to:

**image data → neural networks → latent representations → reconstruction**

It also provides a foundation for exploring more advanced generative models such as **Variational Autoencoders (VAEs), GANs, and diffusion models**.

```
```
