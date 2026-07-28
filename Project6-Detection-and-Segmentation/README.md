# Object Detection and Image Segmentation with YOLO11 and SAM 2

[Back to the main portfolio](../README.md)

## Project overview

This project explores two advanced computer-vision tasks beyond image classification:

- **Object detection**, which identifies objects and draws bounding boxes around them
- **Image segmentation**, which assigns pixels to object regions and creates detailed masks

The notebook applies YOLO11 to soccer and street scenes, examines detection confidence and segmentation-mask outputs, compares confidence-threshold settings, and demonstrates SAM 2 segmentation.

This project was completed for **ITAI 1378 – Computer Vision**.

## Problem statement

How can a computer-vision system locate multiple objects in an image and separate those objects at the pixel level?

A traditional image-classification model normally returns one label for an entire image. Object detection and segmentation provide more detailed information.

Object detection determines:

- What objects are present
- Where each object is located
- The confidence of each prediction

Image segmentation determines:

- Which pixels belong to each object
- The detailed boundaries of detected objects

## Learning objectives

- Understand the difference between classification, detection, and segmentation.
- Run pretrained YOLO11 models on new images.
- Interpret bounding boxes, class labels, and confidence scores.
- Generate instance-segmentation masks.
- Compare results using different confidence thresholds.
- Isolate individual object masks.
- Use SAM 2 for prompt-based segmentation.
- Understand Intersection over Union, or IoU.
- Evaluate detection and segmentation results visually.

## Approach

1. Configure the object-detection and segmentation environment.
2. Import the required Python libraries.
3. Load sample soccer and street images.
4. Run YOLO11 object detection.
5. Visualize bounding boxes, class labels, and confidence scores.
6. Run YOLO11 instance segmentation.
7. Extract and visualize segmentation masks.
8. Compare predictions at different confidence thresholds.
9. Isolate an individual object mask, including a bus-mask example.
10. Apply SAM 2 segmentation.
11. Examine Intersection over Union as an evaluation concept.
12. Save important outputs in the `Results` folder.

## Image and dataset handling

This project performs inference on sample images instead of training a new model on a large labeled dataset.

The demonstrated inputs include:

- A soccer scene
- A street scene containing several objects

The images are loaded using the download or image-loading cells included in the notebook.

Large datasets and pretrained model-weight files are not stored directly in this repository. Required model weights may be downloaded automatically when the notebook is executed.

## Object detection

Object detection identifies objects and provides a rectangular bounding box around each detected object.

A typical detection contains:

- A predicted class
- A confidence score
- Bounding-box coordinates
- The location of the object in the image

A simplified detection workflow is:

```text
Input Image
    ↓
YOLO11 Detection Model
    ↓
Object Predictions
    ↓
Class Labels
Bounding Boxes
Confidence Scores
```

## Image segmentation

Image segmentation provides a more detailed result than object detection.

Instead of representing an object only with a rectangular box, segmentation predicts which individual pixels belong to the object.

A simplified segmentation workflow is:

```text
Input Image
    ↓
Segmentation Model
    ↓
Detected Objects
    ↓
Pixel-Level Masks
```

This makes segmentation useful when the exact shape or boundary of an object is important.

## YOLO11

YOLO stands for **You Only Look Once**.

YOLO11 is used in this project for object detection and instance segmentation.

The model outputs can include:

- Object class labels
- Detection confidence scores
- Bounding boxes
- Segmentation masks

YOLO models are designed to process an image in a single prediction workflow, making them suitable for real-time and near-real-time computer-vision applications.

## SAM 2

SAM 2 stands for **Segment Anything Model 2**.

SAM 2 is a prompt-based segmentation model. A prompt tells the model which object or region should be segmented.

Possible prompts can include:

- Bounding boxes
- Points
- Selected image regions

In this project, SAM 2 demonstrates how a detected object can be separated from the rest of the image using a detailed pixel-level mask.

## Confidence thresholds

Each YOLO prediction includes a confidence score.

The confidence threshold controls which detections are kept.

### Lower confidence threshold

A lower threshold may:

- Keep more object detections
- Detect less obvious objects
- Include more incorrect predictions

### Higher confidence threshold

A higher threshold may:

- Keep fewer detections
- Remove uncertain predictions
- Miss objects that were detected with lower confidence

The project compares threshold settings to demonstrate how confidence filtering affects the final output.

## Intersection over union

Intersection over Union, or IoU, measures the overlap between a predicted region and a reference region.

```text
IoU = Area of Intersection / Area of Union
```

IoU values range from 0 to 1:

- An IoU near **0** indicates little or no overlap.
- A moderate IoU indicates partial overlap.
- An IoU near **1** indicates strong overlap.

IoU can be applied to bounding boxes and segmentation masks.

## Technologies used

- Python
- Jupyter Notebook
- Google Colab
- Ultralytics YOLO
- YOLO11
- SAM 2
- PyTorch
- Torchvision
- OpenCV
- NumPy
- Matplotlib
- Pillow
- Requests

## Requirements

Install the main required packages using:

```bash
pip install -r requirements.txt
```

The `requirements.txt` file should contain:

```text
numpy
matplotlib
Pillow
requests
opencv-python-headless
torch
torchvision
ultralytics
```

SAM 2 may require an additional installation command. Follow the installation cells included in the notebook for the exact SAM 2 setup used in the project.

## Results

The project demonstrates:

- Object detection in a soccer scene
- Object detection in a street scene
- Predicted object classes
- Bounding boxes and confidence scores
- YOLO11 segmentation masks
- Confidence-threshold comparisons
- Isolation of an individual bus mask
- SAM 2 segmentation
- IoU evaluation concepts

This project focuses mainly on qualitative visual evaluation rather than training-performance metrics because pretrained models are applied to sample images.

## Results and visualizations

### YOLO11 soccer detection

![YOLO11 soccer detection](Results/Yolo11result%20soccer.png)

The model detects and labels objects appearing in the soccer scene.

### YOLO11 street detection

![YOLO11 street detection](Results/Yolo11result%20street.png)

The street-scene result demonstrates object detection in a more complex environment containing multiple object classes.

### YOLO11 soccer segmentation

![YOLO11 soccer segmentation](Results/yolo11mask%20soccer.png)

This output demonstrates pixel-level masks for detected objects in the soccer image.

### YOLO11 street segmentation

![YOLO11 street segmentation](Results/yolo11mask%20street.png)

This output demonstrates segmentation masks in the street scene.

### Street mask comparison

![YOLO11 street mask comparison](Results/Yolo11resultmask%20street%20comp.png)

This visualization compares object-detection and segmentation-mask results.

### Confidence-threshold comparison

![Confidence threshold comparison](Results/threshold%20comp.png)

The comparison demonstrates how changing the confidence threshold affects the number of retained detections.

### Bus mask

![Bus mask](Results/bus%20mask%20only.png)

This result isolates the segmentation mask for a selected bus object.

### SAM 2 segmentation

![SAM 2 segmentation](Results/sam2.png)

This output demonstrates prompt-based segmentation using SAM 2.

### IoU evaluation

![IoU evaluation](Results/evaluate.png)

This visualization explains different levels of overlap between predicted and reference regions.

Additional documentation is available here:

- [Project notebook](L06_TobiasChow_ITAI_1378.ipynb)
- [Lab journal](Results/L06_TobiasChow_ITAI_1378_LabJournal.pdf)
- [Saved results](Results/)

## Key findings

- Object detection provides object class and location information.
- Image segmentation provides more precise pixel-level object boundaries.
- YOLO11 can perform both object detection and instance segmentation.
- Confidence thresholds affect the number and quality of retained predictions.
- Lower thresholds may detect additional objects but may also introduce uncertain results.
- Higher thresholds reduce uncertain detections but may remove valid objects.
- Individual segmentation masks can be extracted for further image processing.
- SAM 2 can produce detailed masks using prompts that identify the desired object.
- IoU provides a useful method for evaluating the overlap between predicted and reference regions.
- Visual inspection remains important when evaluating results from complex scenes.

## Limitations

- The project uses a small number of sample images.
- The models are pretrained and are not trained specifically for these images.
- No labeled ground-truth dataset is included for formal quantitative evaluation.
- Detection quality may change with lighting, image resolution, camera angle, and object size.
- Small or partially hidden objects may be more difficult to detect.
- Confidence scores do not always guarantee that a prediction is correct.
- Segmentation masks may not perfectly follow complicated object boundaries.
- Model performance and inference speed may vary between CPU and GPU environments.

## Possible improvements

Future improvements could include:

- Testing additional images and object categories
- Comparing several YOLO11 model sizes
- Measuring inference speed on CPU and GPU
- Comparing different confidence thresholds systematically
- Comparing different IoU thresholds
- Evaluating results on a labeled dataset
- Calculating precision and recall
- Calculating mean Average Precision
- Measuring mask IoU
- Comparing YOLO11 segmentation with SAM 2 segmentation
- Applying the models to video
- Tracking objects across video frames
- Training or fine-tuning a model on a custom dataset

## Real-world applications

Object detection and image segmentation can be applied to:

- Autonomous vehicles
- Traffic monitoring
- Sports analytics
- Medical imaging
- Robotics
- Manufacturing inspection
- Security systems
- Agriculture
- Satellite imagery
- Inventory monitoring
- Video analysis

## How to Run

### Option 1: On Google Colab

1. Open [`L06_TobiasChow_ITAI_1378.ipynb`](L06_TobiasChow_ITAI_1378.ipynb).
2. Open or upload the notebook in Google Colab.
3. Select **Runtime > Change runtime type**.
4. Select a GPU runtime when available.
5. Run the installation cells exactly as written.
6. Restart the runtime if requested after installing packages.
7. Run all notebook cells from top to bottom.
8. Allow the pretrained model weights to download.
9. Review the detection, segmentation, threshold, SAM 2, and IoU outputs.

### Option 2: Run on local environment

Clone the portfolio repository:

```bash
git clone https://github.com/TobiasC05/Tobias-C-AI-Portfolio.git
```

Move into the Project 6 folder:

```bash
cd Tobias-C-AI-Portfolio/Project6-Detection-and-Segmentation
```

Install the main dependencies:

```bash
pip install -r requirements.txt
```

Start Jupyter Notebook:

```bash
jupyter notebook L06_TobiasChow_ITAI_1378.ipynb
```

Run the notebook cells in order.

SAM 2 may require additional installation steps. Follow the commands included in the notebook.

## Repository contents

```text
Project6-Detection-and-Segmentation/
├── README.md
├── requirements.txt
├── L06_TobiasChow_ITAI_1378.ipynb
└── Results/
    ├── L06_TobiasChow_ITAI_1378_LabJournal.pdf
    ├── Yolo11result soccer.png
    ├── Yolo11result street.png
    ├── Yolo11resultmask street comp.png
    ├── bus mask only.png
    ├── evaluate.png
    ├── sam2.png
    ├── threshold comp.png
    ├── yolo11mask soccer.png
    └── yolo11mask street.png
```

The `.ipynb` notebook is the primary project file. The PDF is included as supporting documentation and does not replace the required Jupyter notebook.

## Author

**Tobias Chow**  
ITAI 1378 – Computer Vision
