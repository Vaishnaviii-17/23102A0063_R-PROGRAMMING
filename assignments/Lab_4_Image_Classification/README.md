# Lab 4 – Image Classification and Recognition Using R, Keras and TensorFlow

## 1. Project Title

**Image Classification and Recognition Using R, Keras and TensorFlow**

## 2. Objective

The objective of this project is to implement an image classification and recognition system using R Programming. The project follows the workflow demonstrated in the prescribed video tutorial and uses the `EBImage`, `keras3`, and `tensorflow` packages for image processing and deep learning.

The project demonstrates how images can be loaded, explored, resized, reshaped, converted into numerical features, one-hot encoded, and classified using a neural network model.

The complete project is implemented and executed in Google Colab using an R runtime.

---

## 3. Problem Description

The project performs binary image classification using a small image dataset containing two classes:

* **C**
* **P**

The images are processed using the `EBImage` package and converted into numerical feature vectors suitable for input to a neural network.

A sequential neural network is then created using Keras with TensorFlow as the backend. The model is trained using the prepared training data and evaluated using the test data. Predictions and a confusion matrix are generated to verify the correctness of the classification.

---

## 4. Reference Video

The implementation is based on the prescribed video tutorial:

**Deep Learning with Keras in R – Image Classification and Recognition**

https://www.youtube.com/watch?v=iExh0qj2Ouo&list=PLpaxqU9O4beceS4RxsJESmFGUqpwm2_P&index=4

The major stages followed from the tutorial are:

1. Load packages
2. Read images
3. Explore images and image data
4. Resize images
5. Reshape image data
6. Row bind image features
7. Perform one-hot encoding
8. Create the neural network model
9. Compile the model
10. Fit/train the model
11. Evaluate the model
12. Make predictions
13. Generate a confusion matrix

---

## 5. Dataset Information

The dataset contains **12 images** belonging to two classes.

| Class     | Number of Images |
| --------- | ---------------: |
| C         |                6 |
| P         |                6 |
| **Total** |           **12** |

The image files are:

### Class C

* c1.jpg
* c2.jpg
* c3.jpg
* c4.jpg
* c5.jpg
* c6.jpg

### Class P

* p1.jpg
* p2.jpg
* p3.jpg
* p4.jpg
* p5.jpg
* p6.jpg

The images are included in the `data/images/` directory of this project.

---

## 6. Software and Libraries Used

### Software

* R 4.6.1
* Google Colab
* Python 3.10.12
* TensorFlow 2.21.0

### R Packages

* `keras3` 1.5.1
* `tensorflow`
* `EBImage`

### Python Environment

The Keras/TensorFlow environment was configured using the `r-keras` Python virtual environment.

---

## 7. Image Preprocessing

The images are first loaded using the `EBImage` package.

The preprocessing workflow consists of:

### 7.1 Image Loading

The 12 image files are read into R using `readImage()`.

### 7.2 Image Exploration

The loaded images and their dimensions are examined to understand the image data before processing.

### 7.3 Image Resizing

Each image is resized to:

**28 × 28 pixels**

The images contain three color channels:

**28 × 28 × 3**

### 7.4 Reshaping

Each image is converted into a numerical vector.

The number of features per image is:

**28 × 28 × 3 = 2352**

Therefore, the complete feature matrix contains:

**12 × 2352**

features.

### 7.5 Normalization

Pixel values are normalized to a range suitable for neural network training.

### 7.6 One-Hot Encoding

The two classes are converted into one-hot encoded labels for categorical classification.

The resulting label matrix has dimensions:

**12 × 2**

---

## 8. Training and Testing Data

The dataset is divided into training and testing subsets.

| Dataset  | Number of Images |
| -------- | ---------------: |
| Training |               10 |
| Testing  |                2 |
| Total    |               12 |

For the executed experiment, the two test images were:

* c1.jpg
* p1.jpg

---

## 9. Neural Network Architecture

A sequential neural network is implemented using Keras.

The architecture is:

```text
Input Layer
2352 features
      |
      v
Dense Layer
256 neurons
ReLU activation
      |
      v
Dense Layer
128 neurons
ReLU activation
      |
      v
Output Layer
2 neurons
Softmax activation
```

### Model Configuration

| Parameter                   |                    Value |
| --------------------------- | -----------------------: |
| Input features              |                     2352 |
| Hidden Layer 1              |              256 neurons |
| Hidden Layer 2              |              128 neurons |
| Output classes              |                        2 |
| Activation in hidden layers |                     ReLU |
| Output activation           |                  Softmax |
| Optimizer                   |                     Adam |
| Loss function               | Categorical Crossentropy |
| Epochs                      |                       30 |
| Batch size                  |                        2 |

---

## 10. Model Training

The neural network is trained using the training subset.

The model is compiled using:

* **Adam optimizer**
* **Categorical Crossentropy loss**
* **Accuracy metric**

The model is trained for **30 epochs**.

---

## 11. Model Evaluation

The trained model is evaluated using both the training and testing datasets.

### Training Accuracy

**100%**

### Testing Accuracy

**100%**

The testing accuracy is based on the two images in the test split.

Because the test set contains only two images, the result should be interpreted as **100% accuracy on this particular two-image test set**, rather than as evidence of general performance on a large unseen dataset.

---

## 12. Prediction Results

The model was used to predict the classes of the test images.

| Image  | Actual Class | Predicted Class |
| ------ | ------------ | --------------- |
| c1.jpg | C            | C               |
| p1.jpg | P            | P               |

Both test images were classified correctly.

---

## 13. Confusion Matrix

The resulting confusion matrix is:

```text
             Predicted
             C    P
Actual C     1    0
       P     0    1
```

The diagonal values indicate that both test images were correctly classified.

---

## 14. Important Results

| Metric             | Result |
| ------------------ | -----: |
| Total Images       |     12 |
| Class C Images     |      6 |
| Class P Images     |      6 |
| Training Images    |     10 |
| Testing Images     |      2 |
| Image Width        |     28 |
| Image Height       |     28 |
| Channels           |      3 |
| Features per Image |   2352 |
| Hidden Layer 1     |    256 |
| Hidden Layer 2     |    128 |
| Output Classes     |      2 |
| Epochs             |     30 |
| Training Accuracy  |   100% |
| Testing Accuracy   |   100% |

---

## 15. Project Structure

```text
Lab_4_Image_Classification/
│
├── Lab_4_Image_Classification_R_Keras.ipynb
│
├── README.md
│
├── data/
│   └── images/
│       ├── c1.jpg
│       ├── c2.jpg
│       ├── c3.jpg
│       ├── c4.jpg
│       ├── c5.jpg
│       ├── c6.jpg
│       ├── p1.jpg
│       ├── p2.jpg
│       ├── p3.jpg
│       ├── p4.jpg
│       ├── p5.jpg
│       └── p6.jpg
│
├── output/
│   ├── final_results.csv
│   ├── predictions.csv
│   └── confusion_matrix.csv
│
└── screenshots/
    ├── dataset.png
    ├── resize.png
    ├── model_summary.png
    ├── training.png
    ├── predictions.png
    └── confusion_matrix.png
```

---

## 16. How to Execute the Project

### Option 1 – Google Colab

1. Open Google Colab.
2. Open the provided `.ipynb` notebook.
3. Change the runtime to **R**.
4. Ensure the required R packages are available:

   * `keras3`
   * `tensorflow`
   * `EBImage`
5. Upload or place the dataset in the required `data/images/` directory.
6. Execute the notebook cells in order.
7. Verify the generated model summary, training results, predictions, and confusion matrix.

### Option 2 – R Environment

The project can also be executed in an R environment with the required R packages and a compatible Python/TensorFlow installation.

---

## 17. Generated Outputs

The project generates the following result files:

* `final_results.csv` – summary of the project configuration and results
* `predictions.csv` – actual and predicted classes for test images
* `confusion_matrix.csv` – confusion matrix values

The notebook also displays:

* Image exploration results
* Resized images
* Model architecture
* Training history
* Evaluation results
* Predictions
* Confusion matrix

---

## 18. Screenshots

### Dataset and Class Information

The dataset contains 12 images divided equally between classes C and P.

![Dataset](screenshots/dataset.png)

### Resized Image

Images are resized to 28 × 28 pixels while retaining three color channels.

![Resized Image](screenshots/resize.png)

### Model Summary

The neural network consists of 2352 input features followed by hidden layers of 256 and 128 neurons and a two-class output layer.

![Model Summary](screenshots/model_summary.png)

### Training

The model is trained for 30 epochs using the Adam optimizer.

![Training](screenshots/training.png)

### Predictions

The test images c1.jpg and p1.jpg were correctly classified.

![Predictions](screenshots/predictions.png)

### Confusion Matrix

The confusion matrix shows correct classification for both test images.

![Confusion Matrix](screenshots/confusion_matrix.png)

---

## 19. Conclusion

The image classification project was successfully implemented using R Programming, EBImage, Keras, and TensorFlow.

The images were loaded, explored, resized to 28 × 28 × 3, converted into 2352 numerical features, and one-hot encoded. A sequential neural network with two hidden layers was trained for 30 epochs.

The implemented model achieved:

* **100% training accuracy**
* **100% accuracy on the two-image test set**

Both test images, c1.jpg and p1.jpg, were classified correctly, resulting in a diagonal confusion matrix with no misclassifications in the test split.

The project also demonstrates an end-to-end workflow involving data preparation, image processing, neural network implementation, model evaluation, prediction, result generation, documentation, and GitHub-based version control.

---

## 20. Version Control

Git and GitHub are used to maintain the project and document its development stages.

Meaningful commits are maintained for different stages of development, including:

```text
Initial Lab 4 project setup
Add image classification implementation
Add project results and screenshots
Add project README
```

The GitHub repository contains the complete project implementation, dataset/reference, outputs, screenshots, notebook, and documentation.

---

## 21. GitHub Repository

**Repository:**
https://github.com/Vaishnaviii-17/23102A0063_R-PROGRAMMING/tree/main/assignments/Lab_4_Image_Classification

---

## 22. Assignment Deliverables

The repository provides the required project components:

* Complete R project/source code
* Dataset used in the project
* Generated output/results
* README.md documentation
* Screenshots demonstrating successful execution
* Git version-control history
* GitHub repository for evaluation
