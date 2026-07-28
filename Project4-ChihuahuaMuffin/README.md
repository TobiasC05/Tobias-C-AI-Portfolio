# Chihuahua vs. Muffin Image Classification

[Back to the main portfolio](../README.md)

## Project Overview

This project builds and trains a basic deep-learning neural network to distinguish between images of Chihuahuas and muffins.

The two classes can appear visually similar because Chihuahua faces and muffins may share comparable shapes, colors, and textures. The project demonstrates the complete image-classification workflow, including image preprocessing, dataset loading, neural-network construction, model training, validation, and prediction visualization.

This project was completed for **ITAI 1378 – Computer Vision** using Python and PyTorch.

## Problem Statement

Can a neural network correctly determine whether an image contains a Chihuahua or a muffin?

This is a binary image-classification problem with two output classes:

- Chihuahua
- Muffin

The model receives an RGB image as input and produces a prediction indicating which of the two classes is more likely.

## Learning Objectives

- Understand the basic structure of a neural network.
- Prepare image data for deep-learning models.
- Convert images into PyTorch tensors.
- Organize images into training and validation datasets.
- Create data loaders for batch processing.
- Build a fully connected neural network with PyTorch.
- Train the model using forward propagation and backpropagation.
- Evaluate the model on images that were not used for training.
- Visualize correct and incorrect predictions.

## Dataset

The dataset contains labeled images of Chihuahuas and muffins.

It is organized into separate training and validation folders:

```text
data/
├── train/
│   ├── chihuahua/
│   └── muffin/
└── validation/
    ├── chihuahua/
    └── muffin/
```

The original workshop dataset contains:

- 120 training images
- 30 validation images
- 2 image classes

The image dataset is not stored directly in this portfolio repository. It can be obtained from the original workshop repository:

https://github.com/mlatsjsu/workshop-chihuahua-vs-muffin/tree/master/data

After downloading it, place the `data` folder inside the project directory unless the notebook already contains a cell that downloads or accesses the data.

## Dataset Handling

The images are loaded using PyTorch's `ImageFolder` utility. The folder names are used automatically as class labels.

The preprocessing pipeline performs the following operations:

1. Resize each image to a consistent size.
2. Convert the image into a PyTorch tensor.
3. Normalize the RGB pixel values.
4. Group images into training and validation datasets.
5. Load images in batches using PyTorch data loaders.

The validation dataset remains separate from the training dataset so that the model can be evaluated on images it did not use during training.

## Approach

### 1. Import Required Libraries

The notebook imports PyTorch, Torchvision, Pillow, Matplotlib, and other supporting libraries.

### 2. Build the Neural Network

A custom PyTorch neural network is created by extending `torch.nn.Module`.

The model uses:

- One flattened RGB image as its input
- Multiple fully connected layers
- ReLU activation functions
- Two output values representing Chihuahua and muffin
- A probability-based final prediction

### 3. Prepare the Image Data

All images are resized, converted to tensors, normalized, and loaded into training and validation batches.

### 4. Train the Model

The model is trained over multiple epochs.

For each training batch, the notebook performs:

1. A forward pass through the neural network
2. Loss calculation
3. Gradient calculation through backpropagation
4. Weight updates using an optimizer

### 5. Validate the Model

After training, the model predicts the classes of images from the validation dataset.

The predicted class is compared with the true class to determine whether each prediction is correct.

### 6. Visualize the Results

The notebook displays each validation image with:

- Predicted class
- True class
- Green text for correct predictions
- Red text for incorrect predictions

## Model Architecture

The project uses a basic fully connected neural network rather than a convolutional neural network.

A simplified representation of the architecture is:

```text
RGB Image
    ↓
Resize and Normalize
    ↓
Flatten Image into One Feature Vector
    ↓
Fully Connected Layer
    ↓
ReLU Activation
    ↓
Fully Connected Hidden Layers
    ↓
ReLU Activations
    ↓
Two-Class Output
    ↓
Chihuahua or Muffin
```

Because the image is flattened before entering the model, the network learns from individual pixel values without explicitly preserving the spatial relationships between nearby pixels.

## Loss Function and Optimizer

The model uses a classification loss function to measure the difference between its predictions and the correct image labels.

An optimizer then updates the model's weights to reduce this error during training.

The notebook demonstrates the importance of parameters such as:

- Learning rate
- Number of epochs
- Batch size
- Image dimensions
- Number and size of hidden layers
- Optimizer selection

## Results

The saved validation visualization contains predictions for 30 validation images.

Based on the displayed results:

| Measurement | Result |
|---|---:|
| Validation images | 30 |
| Correct predictions | 29 |
| Incorrect predictions | 1 |
| Approximate validation accuracy | 96.7% |

The model correctly identified most Chihuahua and muffin images.

The single visible error occurred when one muffin image was predicted as a Chihuahua.

Because the validation dataset is small, the result should be interpreted as performance on this specific group of images rather than proof that the model will achieve the same accuracy on all unfamiliar Chihuahua and muffin images.

## Results and Visualizations

### Validation Predictions

![Chihuahua and muffin validation predictions](Results/CMresults.png)

Green labels indicate correct predictions, while the red label identifies an incorrect prediction.

Additional project documentation is available here:

- [Project notebook](Workshop_1.ipynb)
- [Project PDF](Results/L04_TobiasChow_ITAI_1378.pdf)
- [Saved results](Results/)

## Key Findings

- A basic neural network can learn to distinguish between Chihuahua and muffin images.
- Image resizing and normalization help create consistent model inputs.
- Separating training and validation images is important for measuring generalization.
- The model correctly classified nearly all images in the validation set.
- Visually similar objects can still confuse the classifier.
- Looking at individual predictions provides more information than accuracy alone.
- Hyperparameters such as learning rate, epochs, and layer size can significantly affect model performance.

## Limitations

- The dataset contains a relatively small number of images.
- The validation result is based on only 30 images.
- A fully connected network flattens the image and does not directly preserve spatial relationships.
- The model may not generalize well to photographs with unfamiliar lighting, backgrounds, camera angles, or image quality.
- Additional images and data augmentation would provide a stronger evaluation.
- A convolutional neural network would be better designed to learn spatial patterns such as edges, shapes, and textures.

## Possible Improvements

Future improvements could include:

- Adding more training and validation images
- Applying image augmentation
- Testing different learning rates
- Increasing or reducing the number of training epochs
- Comparing different optimizers
- Adding dropout to reduce overfitting
- Recording training and validation loss curves
- Creating a confusion matrix
- Reporting precision, recall, and F1-score
- Replacing the fully connected model with a convolutional neural network

The CNN version of this classification problem is explored separately in Project 5.

## Technologies Used

- Python
- Jupyter Notebook
- Google Colab
- PyTorch
- Torchvision
- Pillow
- Matplotlib
- tqdm

## Requirements

Install the required packages using:

```bash
pip install -r requirements.txt
```

The `requirements.txt` file should contain:

```text
numpy
matplotlib
Pillow
torch
torchvision
tqdm
```

## How to Run

### Option 1: Google Colab

1. Open [`Workshop_1.ipynb`](Workshop_1.ipynb).
2. Upload or open the notebook in Google Colab.
3. Upload the dataset or connect Google Drive.
4. Confirm that the following folders are available:

```text
data/train/chihuahua
data/train/muffin
data/validation/chihuahua
data/validation/muffin
```

5. Run all notebook cells from top to bottom.
6. Review the training output and validation predictions.

### Option 2: Run Locally

Clone the portfolio repository:

```bash
git clone https://github.com/TobiasC05/Tobias-C-AI-Portfolio.git
```

Move into the project folder:

```bash
cd Tobias-C-AI-Portfolio/Project4-ChihuahuaMuffin
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

Download the original dataset and place the `data` folder inside the project folder.

Start Jupyter Notebook:

```bash
jupyter notebook Workshop_1.ipynb
```

Run the notebook cells in order.

## Repository Contents

```text
Project4-ChihuahuaMuffin/
├── README.md
├── requirements.txt
├── Workshop_1.ipynb
└── Results/
    ├── CMresults.png
    └── L04_TobiasChow_ITAI_1378.pdf
```

## Attribution

This project was completed as part of ITAI 1378 coursework and was based on the Chihuahua-versus-muffin introductory PyTorch workshop.

Original workshop:

https://github.com/mlatsjsu/workshop-chihuahua-vs-muffin

The notebook should be reviewed for any additional attribution or course-specific academic-integrity requirements.

## Author

**Tobias Chow**  
ITAI 1378 – Computer Vision
