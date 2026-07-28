# Image Processing: From Pixels to Perception

[Back to the main portfolio](../README.md)

## Project Overview

This project introduces the foundations of digital image processing by treating an image as a numerical matrix. The notebook demonstrates how pixel values, color channels, and local neighborhoods can be manipulated to change an image's appearance and extract useful visual information.

The work progresses from basic matrix inspection to grayscale conversion, brightness and contrast adjustment, neighborhood operations, histogram analysis, geometric transformations, edge detection, and multi-step artistic processing pipelines.

## Problem Statement

How can a computer represent and modify an image using numerical operations?

This project explores how common image-processing techniques transform pixel data and how those transformations affect image appearance, contrast, structure, and visual detail.

## Learning Objectives

- Understand how digital images are stored as matrices.
- Inspect image dimensions, pixel values, and RGB color channels.
- Convert color images to grayscale.
- Apply point operations such as brightness and contrast adjustment.
- Apply neighborhood-based operations such as smoothing and filtering.
- Analyze and modify image histograms.
- Perform geometric transformations.
- Combine multiple operations into reusable image-processing pipelines.

## Approach

1. Configure the Python image-processing environment.
2. Create or load a sample image.
3. Inspect the image matrix, shape, data type, and pixel values.
4. Separate and visualize the red, green, and blue channels.
5. Convert the image to grayscale and compare memory requirements.
6. Apply point operations to control brightness and contrast.
7. Apply neighborhood operations and filters.
8. Analyze histograms and perform histogram equalization.
9. Apply geometric transformations.
10. Build creative processing pipelines, including vintage, dramatic, soft-glow, and social-media-style effects.

## Image Source and Dataset Handling

This project does not require a large training dataset. The notebook creates a synthetic test image and also supports loading an image from a URL or uploading a local image in Google Colab.

Because the project works with individual sample images rather than a large public dataset, no external dataset is stored in this repository.

## Technologies Used

- Python
- Jupyter Notebook / Google Colab
- NumPy
- OpenCV
- Pillow
- Matplotlib
- Requests

## Results

The project produces qualitative visual results rather than classification metrics. The saved outputs demonstrate:

- Image representation as a matrix
- RGB channel separation
- Grayscale conversion
- Point and neighborhood operations
- Histogram-based enhancement
- Geometric transformations
- Edge detection
- Multi-stage image-processing pipelines

### Selected Visualizations

#### Image Matrix Representation

![Image matrix representation](Results/image%20matrix.png)

#### RGB Channel Separation

![RGB channels](Results/rgb%20channels.png)

#### Grayscale Conversion

![Grayscale conversion](Results/convert%20grayscale.png)

#### Image-Processing Pipeline

![Image-processing pipeline](Results/process%20pipeline.png)

#### Final Lab Summary

![Final lab summary](Results/lab%20summary.png)

Additional outputs are available in the [`Results`](Results/) folder.

## Key Findings

- A digital image can be processed directly as a NumPy array of pixel values.
- Grayscale images require less memory because they use one intensity channel instead of three RGB channels.
- Point operations change individual pixels, while neighborhood operations use surrounding pixels to smooth, sharpen, or detect structure.
- Histogram analysis helps explain an image's brightness and contrast distribution.
- Combining several simple operations can create more advanced visual effects.

## How to Run

### Google Colab

1. Open [`L02_Chow_Tobias_ITAI1378.ipynb`](L02_Chow_Tobias_ITAI1378.ipynb).
2. Select **Open in Colab** or upload the notebook to Google Colab.
3. Run the installation and import cells.
4. Run all cells from top to bottom.
5. Use the generated sample image, download the notebook's sample image, or upload your own image when prompted.

### Local Environment

```bash
git clone https://github.com/TobiasC05/Tobias-C-AI-Portfolio.git
cd Tobias-C-AI-Portfolio/Project2-ImageProcessing
pip install numpy matplotlib opencv-python-headless pillow requests jupyter
jupyter notebook L02_Chow_Tobias_ITAI1378.ipynb
