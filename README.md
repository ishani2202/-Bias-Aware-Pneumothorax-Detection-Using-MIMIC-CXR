
# **PneumoScan: Bias-Aware Pneumothorax Detection Using MIMIC-CXR**

In this project, I analyzed the performance of a pre-trained model designed to diagnose [Pneumothorax](https://www.mayoclinic.org/diseases-conditions/pneumothorax/symptoms-causes/syc-20350367#:~:text=A%20pneumothorax%20(noo%2Dmoe%2D,a%20portion%20of%20the%20lung.) from chest X-rays. Pneumothorax, or collapsed lung, is a potentially life-threatening condition, making accurate and reliable diagnostic models essential for clinical workflows.

In this problem, I have worked with the [`MIMIC-CXR`](https://physionet.org/content/mimic-cxr/2.0.0/) dataset, which contains chest X-rays and radiology reports for patients at Beth Israel Deaconess Medical Center. The full dataset is accessible in two formats, one in [DICOM format](https://physionet.org/content/mimic-cxr/2.0.0/) with the full, de-identified free-text radiology reports, and one in a preprocessed, compressed [JPG format](https://physionet.org/content/mimic-cxr-jpg/2.0.0/) with structured labels derived from the radiology reports. 

---

## **Project Overview**

Pneumothorax detection is a crucial task in medical imaging, and automated tools can significantly enhance diagnosis. This project aims to:
- Evaluate the performance of a pre-trained model on the MIMIC-CXR dataset.
- Investigate biases, such as reliance on specific terms in radiology reports.
- Propose methods to mitigate biases and improve fairness.

The notebook includes:
1. Data loading and preparation.
2. Model evaluation with performance metrics.
3. Error analysis and visualization.
4. Bias detection and mitigation experiments.

---

## **Dataset**

The analysis uses the **MIMIC-CXR** dataset, which contains:
- Chest X-ray images.
- Radiology reports with diagnostic labels.
- Demographic metadata for subgroup analysis.

---

## **Features**

### **1. Data Preparation**
- Downloads and processes the following files:
  - Patient demographic data (`patients.csv`).
  - Radiology metadata (`mimic-cxr-2.0.0-metadata.csv`).
  - Evaluation set (`evaluation_set.csv`).
- Loads and visualizes X-ray images for exploratory analysis.

### **2. Model Evaluation**
- Loads a pre-trained DenseNet-121 model, commonly used for medical image classification.
- Uses additional PyTorch models like ResNet-50 for comparative analysis.
- Generates predictions and computes:
  - AUROC (Area Under the Receiver Operating Characteristic Curve): Measures classification performance.
  - Precision and Recall: Evaluates prediction accuracy and ability to identify true positives.
  - Confusion Matrix: Summarizes prediction outcomes.

### **3. Error Analysis**
- Reviews incorrect predictions using:
  - Sample X-ray images and associated radiology reports.
  - Keywords in reports, like "pigtail catheter," that may bias predictions.
- Visualizes model performance for deeper insights into failure cases.

### **4. Bias Mitigation**
- Tests the impact of excluding specific terms (e.g., "catheter") from radiology reports.
- Recomputes performance metrics to assess whether the model overly relies on textual artifacts.

---

## **Usage**

### **Prerequisites**
- Python 3.x
- Required libraries: `numpy`, `pandas`, `matplotlib`, `torch`, `sklearn`, `PIL`, `imageio`
- Google Cloud SDK (`gcloud`) for data retrieval.

### **Steps to Run**
1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <repository_name>
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Open the Jupyter Notebook:
   ```bash
   jupyter notebook MIMIC_CXR.ipynb
   ```
4. Follow the cells step-by-step to replicate the analysis and visualize results.

---

## **Results**

### **Key Findings**
1. **Model Performance:**
   - The DenseNet-121 model achieves high AUROC on the test set, indicating good classification ability.
   - Precision and recall values demonstrate effectiveness but room for improvement.

2. **Bias Detection:**
   - The model tends to rely on certain keywords in radiology reports (e.g., "pigtail catheter").
   - Demographic analysis reveals variations in performance across subgroups (e.g., gender).

3. **Bias Mitigation:**
   - Removing keywords reduces reliance on spurious correlations, leading to more robust predictions.

### **Visualization Examples**
- X-ray images with associated predictions and reports.
- Performance metrics across demographic groups.

---

## **Future Work**
- Train models with balanced datasets to improve fairness.
- Use advanced natural language processing to preprocess radiology reports.
- Validate findings in a real-world clinical setting.


---

## **License**
This repository is licensed under the MIT License.

---

## **Acknowledgments**
- Dataset: [MIMIC-CXR](https://physionet.org/content/mimic-cxr/2.0.0/) by PhysioNet.
- Pre-trained model and notebook adapted from MIT's **6.871 course materials**.
- Special thanks to collaborators and reviewers for their insights and feedback.

