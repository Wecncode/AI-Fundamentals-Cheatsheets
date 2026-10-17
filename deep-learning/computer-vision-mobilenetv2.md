# Computer Vision with MobileNetV2

## 1. What Is Computer Vision?

Computer vision is a field of artificial intelligence that enables computers to interpret images and videos. Image classification is a common computer vision task in which a model assigns an input image to one of several classes.

Examples include animal classification, plant disease detection, object recognition, and medical image analysis.

## 2. The CIFAR-10 Dataset

CIFAR-10 is a benchmark dataset containing 60,000 colour images divided into 10 classes:

- Airplane
- Automobile
- Bird
- Cat
- Deer
- Dog
- Frog
- Horse
- Ship
- Truck

The standard split contains 50,000 training images and 10,000 test images. Each original image has dimensions of 32 × 32 pixels with three colour channels.

## 3. Transfer Learning

Transfer learning reuses knowledge learned by a model on a large dataset to help solve another task.

MobileNetV2 is a convolutional neural network designed for efficient image feature extraction. It uses inverted residual blocks and linear bottlenecks to reduce computational cost.

A typical transfer-learning workflow is:

1. Load a MobileNetV2 model pretrained on ImageNet.
2. Remove or replace its original classification head.
3. Add a classification head for the target classes.
4. Freeze the pretrained backbone while training the new head.
5. Optionally unfreeze selected backbone layers and fine-tune with a low learning rate.
6. Evaluate the resulting model on unseen test data.


## 4. Image Preprocessing

The input images must match the model's expected input format.

In this experiment, CIFAR-10 images were resized to 96 × 96 pixels and preprocessed using the MobileNetV2 preprocessing function.

Example:

```python
import tensorflow as tf

# Assume image contains the original image data.
image = tf.image.resize(
    tf.cast(image, tf.float32),
    (96, 96)
)

image = tf.keras.applications.mobilenet_v2.preprocess_input(image)
```

The variable `image` represents an image tensor. The same preprocessing must be applied during training, evaluation, and prediction.

Resizing changes the spatial dimensions but does not add new visual information to the original image.

## 5. Model Evaluation

Accuracy measures the proportion of predictions that are correct.

Precision measures how many predictions assigned to a class are correct. Recall measures how many actual examples of a class are identified correctly. The F1-score is the harmonic mean of precision and recall.

For a binary class-specific calculation:

- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN)
- F1-score = 2 × (Precision × Recall) / (Precision + Recall)

Here, TP means true positives, FP means false positives, and FN means false negatives.

A confusion matrix shows which actual classes are being predicted as other classes. Per-class metrics are important because overall accuracy can hide weaknesses affecting particular categories.

## 6. Case Study: MobileNetV2 on CIFAR-10

Two models were evaluated on the same 10,000-image CIFAR-10 test set.

| Experiment | Test accuracy | Correct predictions |
|---|---:|---:|
| Fine-tuned MobileNetV2 baseline | 85.60% | 8,560 / 10,000 |
| MobileNetV2 with CutMix | 83.70% | 8,370 / 10,000 |

The CutMix experiment reduced overall test accuracy by 1.90 percentage points. Therefore, it was not selected as the best-performing model in this experiment.

### Cat and Dog Classification Errors

| Error type | Baseline | CutMix |
|---|---:|---:|
| Actual cats predicted as dogs | 95 | 157 |
| Actual dogs predicted as cats | 137 | 63 |

CutMix reduced Dog-to-Cat errors but increased Cat-to-Dog errors. This illustrates why an augmentation technique should be evaluated across classes instead of being judged by one metric alone.

These results apply to this particular training setup and test set. They do not establish that CutMix will perform worse on every dataset or model.

## 7. Data Augmentation

Data augmentation creates modified training examples to help a model generalize. Common methods include:

- Horizontal flipping
- Small rotations and translations
- Random cropping
- Colour and contrast adjustments
- MixUp, which combines examples through weighted interpolation
- CutMix, which replaces an image region with a patch from another image and adjusts training labels according to the mixed image content

Augmentation should be selected and tuned using training and validation data. Final model selection should consider held-out test performance and per-class metrics.

## 8. Practical Lessons

1. Establish a baseline before testing improvements.
2. Keep preprocessing consistent across all evaluation stages.
3. Use validation data to guide model selection.
4. Reserve the test set for final evaluation and avoid repeatedly tuning against its results.
5. Compare accuracy, precision, recall, F1-score, and confusion matrices.
6. Keep experiment artifacts separate so a weaker model does not overwrite the best model.
7. Record hyperparameters, dataset splits, random seeds, and software versions to improve reproducibility.
8. Treat model confidence as a score unless probability calibration has been assessed.

## 9. Conclusion

MobileNetV2 provides a practical starting point for transfer learning in image classification. The CIFAR-10 case study demonstrates the importance of comparing experimental changes against a baseline and examining class-specific errors before adopting a new training technique.
