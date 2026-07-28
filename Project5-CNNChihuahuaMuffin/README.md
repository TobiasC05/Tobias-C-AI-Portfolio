# Chihuahua vs. Muffin Classification with a Convolutional Neural Network

[Back to the main portfolio](../README.md)

## Project overview

This project revisits the Chihuahua-versus-muffin image-classification problem using a convolutional neural network, or CNN.

Chihuahua faces and muffins can look surprisingly similar because both may contain comparable colors, rounded shapes, textures, and visual patterns. Unlike the fully connected neural network used in Project 4, this project uses convolutional layers that preserve spatial information and learn visual features directly from the images.

The project demonstrates image preprocessing, CNN construction, model training, validation, and prediction visualization using Python and TensorFlow/Keras.

## Problem statement

Can a convolutional neural network correctly distinguish images of Chihuahuas from images of muffins?

This is a binary image-classification problem with two output classes:

- Chihuahua
- Muffin

The model receives an RGB image and predicts which of the two classes is most likely represented.

## Learning objectives

- Understand the purpose of convolutional neural networks.
- Prepare image data for CNN training.
- Resize and normalize image inputs.
- Use convolutional layers to learn image features.
- Apply pooling to reduce feature-map dimensions.
- Train a binary image-classification model.
- Evaluate the model using validation images.
- Visualize correct and incorrect predictions.
- Compare a CNN with the fully connected model used in Project 4.

## Dataset

The project uses a labeled image dataset containing two classes:

```text
dataset/
├── chihuahua/
│   └── image files
└── muffin/
    └── image files
```

The images are divided into training and validation sets.

The dataset is not stored directly in this portfolio repository because it contains many image files. It can be obtained from the original Chihuahua-versus-muffin workshop dataset:

https://github.com/mlatsjsu/workshop-chihuahua-vs-muffin/tree/master/data

After downloading the dataset, organize it according to the folder structure expected by the notebook.

## Dataset Handling

The notebook prepares the images before sending them into the CNN.

The preprocessing workflow includes:

1. Loading images from their class folders.
2. Assigning labels based on folder names.
3. Resizing all images to a consistent size.
4. Converting images into numerical arrays.
5. Normalizing pixel values.
6. Separating training and validation data.
7. Loading images in batches during training.

The validation images are kept separate from the training images so that the model can be evaluated on data it did not use to update its weights.

## Approach

### 1. Import libraries

The notebook imports the libraries required for:

- Image loading
- Numerical processing
- CNN construction
- Model training
- Evaluation
- Result visualization

### 2. Load and preprocess images

The images are resized and normalized so that every image has the same input dimensions and pixel-value range.

### 3. Construct the CNN

A convolutional neural network is created for binary classification.

The model uses convolutional operations to detect useful visual patterns such as:

- Edges
- Curves
- Colors
- Textures
- Shapes
- Higher-level object features

### 4. Reduce feature dimensions

Pooling layers reduce the width and height of feature maps while preserving important learned information.

This helps reduce computation and makes the model less sensitive to small image-position changes.

### 5. Convert Features into a prediction

The learned feature maps are flattened or pooled before being passed to the final classification layers.

The output represents the model's prediction of either:

- Chihuahua
- Muffin

### 6. Train the model

During training, the model repeatedly:

1. Processes a batch of images.
2. Produces class predictions.
3. Calculates prediction error using a loss function.
4. Uses backpropagation to calculate gradients.
5. Updates its weights through an optimizer.
6. Repeats the process across multiple epochs.

### 7. Evaluate the model

The trained model is evaluated using validation images that were not used to update the model.

The predicted class is compared with the correct class for each image.

### 8. Visualize predictions

The notebook displays a grid of validation images containing:

- The predicted class
- The true class
- Green text for correct predictions
- Red text for incorrect predictions

## CNN Architecture

A simplified representation of the model workflow is:

```text
RGB Image
    ↓
Resize and Normalize
    ↓
Convolutional Layer
    ↓
Activation Function
    ↓
Pooling Layer
    ↓
Additional Convolution and Pooling
    ↓
Flattened or Pooled Features
    ↓
Fully Connected Classification Layer
    ↓
Chihuahua or Muffin
```

The exact layer sizes, number of filters, image dimensions, activation functions, and other training settings are available in the executed notebook.

## Why use a CNN?

A fully connected neural network flattens an image before processing it. This removes much of the original spatial relationship between neighboring pixels.

A CNN processes local areas of the image and learns filters that recognize visual patterns. This makes CNNs better suited for image-classification problems.

CNNs can learn:

- Where edges appear
- How textures are arranged
- Which shapes occur together
- How local patterns form larger visual features

## Results

The saved validation visualization contains predictions for 30 images.

| Measurement | Result |
|---|---:|
| Validation images | 30 |
| Correct predictions | 29 |
| Incorrect predictions | 1 |
| Approximate validation accuracy | 96.7% |

The CNN correctly classified most of the displayed Chihuahua and muffin images.

The visible incorrect prediction occurred when one muffin image was classified as a Chihuahua.

Because the validation set contains only 30 images, the result represents performance on this particular validation sample and may not represent performance on every unfamiliar Chihuahua or muffin image.

## Results and visualizations

### CNN validation predictions

![CNN Chihuahua and muffin predictions](Results/CMCNNresults.png)

Green labels indicate correct predictions. The red label identifies the muffin image that the CNN incorrectly predicted as a Chihuahua.

Additional project documentation is available here:

- [Project notebook](CNN_1_Chihuahua_or_Muffin%20%281%29.ipynb)
- [Project PDF](Results/L05_TobiasChow_ITAI_1378.pdf)
- [Saved results](Results/)

## Key findings

- A CNN can learn useful visual features directly from labeled images.
- Convolutional layers preserve spatial relationships better than a basic fully connected network.
- The model correctly classified nearly all displayed validation images.
- Some muffins still contain shapes and textures that resemble Chihuahua faces.
- Reviewing incorrect predictions helps identify weaknesses that may not be visible from accuracy alone.
- Dataset size and image variety strongly affect how well the model generalizes.
- CNNs are better suited to image recognition than networks that rely only on flattened pixel values.

## Comparison with Project 4

| Project 4 | Project 5 |
|---|---|
| Fully connected neural network | Convolutional neural network |
| Flattens the image before classification | Preserves local spatial patterns |
| Learns from individual pixel values | Learns edges, textures, and shapes |
| Limited image-specific feature learning | Designed specifically for image data |
| Introductory neural-network approach | More advanced computer-vision approach |

Both projects demonstrate that neural networks can solve the Chihuahua-versus-muffin classification problem, but Project 5 uses an architecture that is more appropriate for computer vision.

## Technologies used

- Python
- Jupyter Notebook
- Google Colab
- TensorFlow
- Keras
- NumPy
- Matplotlib
- Pillow
- OpenCV
- scikit-learn

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
opencv-python-headless
scikit-learn
tensorflow
```

## Limitations

- The dataset is relatively small.
- The validation results are based on only 30 displayed images.
- Images with unusual lighting or backgrounds may be more difficult to classify.
- The model may learn background patterns in addition to the actual objects.
- Similar colors and textures can still cause classification errors.
- Performance may change when the model is tested on images from different sources.
- Validation accuracy alone does not fully describe model performance.

## Possible improvements

Future improvements could include:

- Adding more Chihuahua and muffin images
- Balancing the number of images in each class
- Applying image augmentation
- Adding dropout to reduce overfitting
- Using early stopping
- Saving the best validation model
- Testing different CNN architectures
- Adjusting the learning rate and batch size
- Comparing different optimizers
- Creating training and validation loss curves
- Generating a confusion matrix
- Reporting precision, recall, and F1-score
- Using transfer learning with a pretrained model such as MobileNet or ResNet
- Testing the model with completely new internet images

## How to Run

### Option 1: On Google Colab

1. Open [`CNN_1_Chihuahua_or_Muffin (1).ipynb`](CNN_1_Chihuahua_or_Muffin%20%281%29.ipynb).
2. Open or upload the notebook in Google Colab.
3. Select **Runtime > Change runtime type**.
4. Select a GPU runtime when available.
5. Upload the image dataset or connect Google Drive.
6. Update the dataset paths if necessary.
7. Run all cells from top to bottom.
8. Review the training output and validation predictions.

### Option 2: Run on a local environment

Clone the portfolio repository:

```bash
git clone https://github.com/TobiasC05/Tobias-C-AI-Portfolio.git
```

Move into the project folder:

```bash
cd Tobias-C-AI-Portfolio/Project5-CNNChihuahuaMuffin
```

Install the required packages:

```bash
pip install -r requirements.txt
```

Start Jupyter Notebook:

```bash
jupyter notebook "CNN_1_Chihuahua_or_Muffin (1).ipynb"
```

Run the notebook cells in order.

## Repository contents

```text
Project5-CNNChihuahuaMuffin/
├── README.md
├── requirements.txt
├── CNN_1_Chihuahua_or_Muffin (1).ipynb
└── Results/
    ├── CMCNNresults.png
    └── L05_TobiasChow_ITAI_1378.pdf
```

The `.ipynb` file is the main project notebook. The PDF is included only as supporting documentation and does not replace the required Jupyter notebook.

## Author

**Tobias Chow**  
ITAI 1378 – Computer Vision
