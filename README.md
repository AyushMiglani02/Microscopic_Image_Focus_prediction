# Focus Quality Assessment Model

This repository contains a TFLite model for assessing focus quality in microscope images.

## Contents

- `focus_model.tflite`: Converted TFLite model for inference
- `focus_model_fp16.tflite`: Float16 quantized TFLite model (smaller size)
- `best_model.h5`: Original Keras/TensorFlow model before conversion
- `training_curves.png`: Plot of training and validation loss curves
- `report.md`: Report describing the approach, metrics, and results
- `focus_quality_assessment.ipynb`: Notebook showing the complete training process

## How to Run Inference

```python
import numpy as np
import tensorflow as tf
import cv2

# Load the TFLite model
interpreter = tf.lite.Interpreter(model_path="focus_model.tflite")
interpreter.allocate_tensors()

# Get input and output tensors
input_details = interpreter.get_input_details()
output_details = interpreter.get_output_details()

# Prepare an image
def preprocess_image(img_path, target_size=(224, 224)):
    img = cv2.imread(img_path)
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    img = cv2.resize(img, target_size)
    img = img.astype(np.float32) / 255.0
    return img

# Load and preprocess an image
image = preprocess_image("path/to/your/image.jpg")
input_tensor = np.expand_dims(image, axis=0)

# Run inference
interpreter.set_tensor(input_details[0]['index'], input_tensor)
interpreter.invoke()
focus_score = interpreter.get_tensor(output_details[0]['index'])[0][0]

print(f"Predicted focus score: {focus_score}")
```
