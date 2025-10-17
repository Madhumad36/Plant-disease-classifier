# README.md: Plant Disease Detector (MobileNetV2)

# Plant Disease Detector (4-Class CNN)

This project implements a highly accurate deep learning model using **Transfer Learning** to classify the health status and plant type from leaf images. The model can distinguish between healthy and diseased states for Pepper Bell and Tomato plants.

## Project Goal

To build an efficient and highly generalizable model capable of achieving near-perfect accuracy (Target: $>95\%$) on a 4-class image classification task, demonstrating proficiency in data pipeline construction, model architecture, and rigorous evaluation.

##  Key Results

  * **Model Architecture:** MobileNetV2 (Frozen Base) + Custom Classifier Head.
  * **Final Accuracy:** **$99\%$** on the unseen test dataset.
  * **Model Size:** Lightweight and optimized due to the use of MobileNetV2.

##  Repository Structure

```
├── newplantdisese.py        # Complete code (Data Split, Model, Training, Eval)
├── best_4_class_model.keras # Saved model weights (The final product)
├── /output.dataplant/       # Output folder containing the split data
│   ├── /train/
│   ├── /valid/
│   └── /test/
└── README.md
```

##  Requirements

This project requires a Python environment with GPU acceleration (recommended: Google Colab).

```bash
pip install tensorflow keras numpy scikit-learn pandas matplotlib tqdm
```

##  Usage (Model Training and Evaluation)

1.  **Setup and Data Ingestion:**

      * Mount your Google Drive in a Colab environment.
      * Ensure your four class folders are located at the specified `DATA_ROOT` path: `/content/drive/MyDrive/PlantVillage`.

2.  **Run `newplantdisese.py`:**

      * The script first executes the **stratified data splitting** (80/10/10) into the `/content/drive/MyDrive/output.dataplant` directory.
      * It then builds the **MobileNetV2 model** with a frozen base.
      * The model is trained for **10 epochs** using the training data.

3.  **Review Results:**

      * Check the final test accuracy. Since the project achieved $\mathbf{99\%}$ accuracy in the initial phase, **no further fine-tuning is required**.
      * Analyze the **Classification Report** and **Confusion Matrix** (printed at the end of the script) to confirm error distribution across the four classes.

## Class Labels

The model was trained to distinguish between the following four health conditions:

1.  `Pepper_bell___Bacterial_spot`
2.  `Pepper_bell___healthy`
3.  `Tomato___Bacterial_spot`
4.  `Tomato___healthy`

##  (Future Deployment)

The saved model (`best_4_class_model.keras`) is ready for deployment as a **Web API** (using frameworks like Flask or FastAPI) or as an **edge device application** (using TensorFlow Lite). The high accuracy makes it suitable for real-world use in a controlled agricultural setting.
