# Machine Learning Assignment: Focus Quality Assessment

## 1. Introduction & Context

This assignment is designed to assess your practical skills in solving a real-world computer vision problem.

We are developing an automated microscope system that captures high-resolution images of blood cells. A critical challenge is ensuring that every image captured is in perfect focus. To solve this, we are building a deep learning model to act as an intelligent "focus-picker."

Your task is to use the provided dataset to build, train, and evaluate a model that can accurately predict the focus quality of an image.

## 2. The Objective

Your goal is to train a deep learning model that takes a single image of a cropped White Blood Cell (WBC) and predicts a continuous **"focus score."** This score represents the image's position relative to the perfect focal plane. The final model needs to be in **TFLite format**.

## 3. The Dataset

You will be provided with the following:

- **`cell_stacks/` (directory):** This folder contains thousands of subdirectories, each representing a single, tracked WBC. Inside each subdirectory (e.g., `stack_001_cell_0/`), you will find a sequence of images (`0.jpg`, `1.jpg`, etc.) which is a Z-stack of that cell. These images are of varying, non-square dimensions.

- **`focus_labels.csv` (file):** This is the ground truth for our training. It contains two columns:
  - `image_path`: The relative path to an image (e.g., `cell_stacks/stack_001_cell_0/0.jpg`).
  - `focus_score`: The numerical label for that image. The scoring system is as follows:
    > - A score of **0.0** indicates the image is perfectly in focus.
    > - A negative score (e.g., -0.2, -0.4) indicates the image is pre-focal (the lens is too close).
    > - A positive score (e.g., 0.2, 0.4) indicates the image is post-focal (the lens is too far).
    > - The further the score is from 0.0, the more out of focus the image is.

## 4. Deliverables

Please package your submission as a single `.zip` archive containing the following:

1.  **`focus_model.tflite`**: The final, converted TFLite model file.
2.  **`best_model.h5`**: The saved Keras/TensorFlow model _before_ conversion.
3.  **Your Code**: A single Python script (`train.py`) or a well-commented Jupyter Notebook (`training.ipynb`).
4.  **`report.md`**: A brief report in Markdown format containing:
    - Your name.
    - The final **Test Mean Absolute Error (MAE)** achieved by your model.
    - A plot showing the training and validation loss curves over epochs.
    - A brief explanation of your approach, including the final model architecture you chose.

## 5. Guidelines, Communication & Tips

- This assignment is designed to be completed in a few hours of focused work. We are looking for a solid, fundamental implementation, not a state-of-the-art research paper. We respect your time and want this to be a positive and practical experience.

- **Embrace Modern Tools:** You are explicitly **allowed** to use AI chatbots (like ChatGPT, Gemini, etc.) as a tool. We view the ability to leverage these resources effectively for coding, debugging, and learning as a modern and essential engineering skill. Your real test is in understanding the problem, guiding the tools, and interpreting the results to build a successful solution.

- **Go Beyond the Baseline:** The provided data preparation steps are a recommended starting point. If you identify a potentially better way to preprocess the data, augment it, or even re-frame the labels, we strongly encourage you to explore it. Please document your reasoning and the results of your approach in your `report.md` file. Creative and well-justified problem-solving is highly valued.

- **We're Here to Help:** If you have any clarifying questions about the dataset, the objective, or the requirements, please do not hesitate to reach out. Clear and proactive communication is a skill we look for. You can reach me directly via:
  - **Email:** [apoorv@adsys.in](mailto:apoorv@adsys.in)
  - **WhatsApp:** +91-9982720855
