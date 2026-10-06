# IoT EVT Detection

**Anomaly and Extreme Value Detection in IoT Sensor Data using Autoencoders and Extreme Value Theory**

## 📌 Project Overview

IoT devices continuously generate large volumes of sensor data. Detecting unusual or abnormal behavior in this data is important for identifying equipment failures, system faults, cyber-physical anomalies, and other unexpected events.

This project proposes an **IoT Event/Extreme Value Detection system** that combines **Deep Learning-based anomaly detection** with **Extreme Value Theory (EVT)**.

The system uses an **Autoencoder** to learn the normal behavior of IoT sensor data. Reconstruction errors produced by the Autoencoder are then analyzed using **Extreme Value Theory** to identify statistically significant extreme anomalies.

The overall objective is to develop a reliable and data-driven approach for detecting rare and abnormal events in IoT environments.

---

## 🎯 Objectives

The major objectives of this project are:

* Collect and preprocess IoT sensor datasets.
* Understand the normal behavior and distribution of sensor readings.
* Develop an Autoencoder-based anomaly detection model.
* Calculate reconstruction-based anomaly scores.
* Apply Extreme Value Theory to the anomaly-score distribution.
* Determine statistically meaningful thresholds for extreme anomalies.
* Detect and classify anomalous/extreme events.
* Evaluate the performance of the proposed approach.
* Visualize normal, anomalous, and extreme observations.

---

## 🧠 Proposed Methodology

The project follows a sequential machine-learning pipeline:

```text
IoT Sensor Dataset
        │
        ▼
Data Preprocessing
        │
        ▼
Feature Selection & Scaling
        │
        ▼
Autoencoder Training
        │
        ▼
Reconstruction Error
        │
        ▼
Anomaly Score
        │
        ▼
Extreme Value Theory (EVT)
        │
        ▼
Statistical Threshold
        │
        ▼
Anomaly / Extreme Event Detection
        │
        ▼
Evaluation & Visualization
```

### 1. Data Preprocessing

Raw IoT sensor data is cleaned and prepared for model training.

The preprocessing stage may include:

* Handling missing values
* Removing duplicate records
* Handling invalid sensor readings
* Feature selection
* Normalization/standardization
* Splitting data into training and testing sets

Processed datasets are stored in:

```text
data/processed/
```

### 2. Autoencoder

An Autoencoder is a neural network designed to learn a compressed representation of the input data and reconstruct the original input.

The model consists mainly of:

* Encoder
* Latent representation
* Decoder

During training, the Autoencoder learns the characteristics of **normal IoT sensor behavior**.

When abnormal data is passed through the model, its reconstruction error is expected to be higher.

### 3. Anomaly Score

The reconstruction error is used as an anomaly score.

A simple form of reconstruction error is:

```text
MSE = (1/n) Σ(xᵢ - x̂ᵢ)²
```

where:

* `xᵢ` = original sensor value
* `x̂ᵢ` = reconstructed sensor value
* `n` = number of features

Higher reconstruction errors indicate observations that differ significantly from learned normal behavior.

### 4. Extreme Value Theory

Instead of selecting an arbitrary anomaly threshold, the project applies **Extreme Value Theory (EVT)** to the tail of the anomaly-score distribution.

The objective is to model unusually large reconstruction errors and determine a statistically motivated threshold for extreme events.

This allows the system to focus specifically on the **extreme tail of the anomaly-score distribution**, which is particularly important when anomalous events are rare.

### 5. Event Detection

The final threshold obtained through the EVT-based approach is used to classify observations.

Conceptually:

```text
Anomaly Score ≤ EVT Threshold
        → Normal

Anomaly Score > EVT Threshold
        → Extreme Anomaly / Event
```

---

## 📂 Project Structure

```text
iot-evt-detection/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│
├── src/
│   ├── preprocessing.py
│   ├── autoencoder.py
│   ├── anomaly_score.py
│   ├── evt.py
│   ├── evaluation.py
│   └── visualization.py
│
├── experiments/
│
├── results/
│
├── models/
│
├── requirements.txt
└── README.md
```

### Directory and File Description

| File/Directory         | Purpose                                                 |
| ---------------------- | ------------------------------------------------------- |
| `data/raw/`            | Stores original, unmodified datasets                    |
| `data/processed/`      | Stores cleaned and transformed datasets                 |
| `notebooks/`           | Exploratory data analysis and experimentation           |
| `src/preprocessing.py` | Data cleaning and preprocessing                         |
| `src/autoencoder.py`   | Autoencoder architecture and training                   |
| `src/anomaly_score.py` | Reconstruction-error/anomaly-score calculation          |
| `src/evt.py`           | Extreme Value Theory implementation                     |
| `src/evaluation.py`    | Model and detection performance evaluation              |
| `src/visualization.py` | Graphs and result visualization                         |
| `experiments/`         | Experimental configurations and comparative experiments |
| `results/`             | Generated metrics, tables, and visual outputs           |
| `models/`              | Saved trained machine-learning models                   |
| `requirements.txt`     | Python dependencies                                     |
| `README.md`            | Project documentation                                   |

---

## 🛠️ Technologies Used

### Programming Language

* Python

### Machine Learning / Deep Learning

* TensorFlow / Keras
* Scikit-learn
* NumPy
* Pandas

### Statistical Analysis

* Extreme Value Theory
* Peaks Over Threshold (POT)
* Generalized Pareto Distribution (GPD)

### Visualization

* Matplotlib
* Seaborn

### Development Environment

* Jupyter Notebook
* VS Code
* Git / GitHub

---

## 📊 Dataset

The project uses IoT sensor datasets containing measurements representing normal and abnormal system behavior.

The dataset preparation process includes:

1. Dataset acquisition
2. Data exploration
3. Missing-value analysis
4. Feature analysis
5. Data cleaning
6. Feature scaling
7. Normal/anomalous data identification
8. Train-test splitting

The raw dataset is maintained separately from processed data to preserve reproducibility.

```text
data/raw/
      ↓
Preprocessing
      ↓
data/processed/
```

---

## 🔬 Experimental Approach

The project will evaluate the proposed approach through multiple experiments.

### Experiment 1 — Dataset Analysis

Analyze:

* Number of observations
* Number of features
* Sensor distributions
* Missing values
* Correlations
* Normal vs anomalous observations

### Experiment 2 — Autoencoder

Train the Autoencoder using primarily normal observations and analyze reconstruction errors.

### Experiment 3 — Anomaly Detection

Generate anomaly scores using reconstruction errors.

### Experiment 4 — EVT

Analyze the upper tail of the anomaly-score distribution and fit an appropriate extreme-value model.

### Experiment 5 — Threshold Selection

Compare the EVT-derived threshold with conventional threshold-selection methods.

### Experiment 6 — Performance Evaluation

Evaluate the detection system using appropriate classification and anomaly-detection metrics.

---

## 📈 Evaluation Metrics

Depending on the available ground-truth labels, the following metrics may be used:

* Accuracy
* Precision
* Recall
* F1-score
* ROC-AUC
* PR-AUC
* False Positive Rate
* False Negative Rate

For imbalanced anomaly-detection datasets, particular attention will be given to:

**Precision, Recall, F1-score and PR-AUC.**

---

## 📉 Expected Results

The expected outcome of the project is a detection pipeline capable of:

* Learning normal IoT sensor behavior.
* Producing meaningful anomaly scores.
* Identifying extreme values in the anomaly-score distribution.
* Automatically determining a statistically motivated detection threshold.
* Detecting rare/extreme IoT events with fewer arbitrary assumptions.
* Providing visual explanations of detected anomalies.

Example output:

```text
Sensor Observation
        │
        ▼
Autoencoder
        │
        ▼
Reconstruction Error
        │
        ▼
Anomaly Score
        │
        ▼
EVT Threshold
        │
   ┌────┴────┐
   ▼         ▼
 Normal    Extreme
           Anomaly
```

---

## 🚀 Installation

Clone the repository:

```bash
git clone <repository-url>
cd iot-evt-detection
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the environment.

### Windows

```bash
venv\Scripts\activate
```

### Linux/macOS

```bash
source venv/bin/activate
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Project

### Step 1 — Prepare the Dataset

Place the original dataset inside:

```text
data/raw/
```

### Step 2 — Preprocess the Data

Run:

```bash
python src/preprocessing.py
```

The processed dataset will be stored in:

```text
data/processed/
```

### Step 3 — Train the Autoencoder

Run:

```bash
python src/autoencoder.py
```

The trained model will be stored in:

```text
models/
```

### Step 4 — Generate Anomaly Scores

Run:

```bash
python src/anomaly_score.py
```

### Step 5 — Apply EVT

Run:

```bash
python src/evt.py
```

### Step 6 — Evaluate the System

Run:

```bash
python src/evaluation.py
```

### Step 7 — Generate Visualizations

Run:

```bash
python src/visualization.py
```

Results will be stored in:

```text
results/
```

---

## 🔄 Reproducibility

To ensure reproducibility:

* Raw datasets are preserved in `data/raw/`.
* Data preprocessing is implemented programmatically.
* Model configurations are maintained in the source code/experiments.
* Trained models are stored in `models/`.
* Experimental results are stored in `results/`.
* Dependencies are specified in `requirements.txt`.

Random seeds should be fixed wherever applicable.

---

## 🔐 Applications

The proposed system can potentially be applied to:

* Industrial IoT monitoring
* Predictive maintenance
* Smart manufacturing
* Smart buildings
* Sensor fault detection
* Infrastructure monitoring
* Energy monitoring
* Cyber-physical systems
* IoT security monitoring

---

## ⚠️ Limitations

The project may have several limitations:

* Detection performance depends on the quality of the dataset.
* Autoencoders may fail to detect anomalies that resemble normal patterns.
* EVT performance depends on appropriate modeling of the extreme tail.
* Highly noisy sensor data may increase false positives.
* Results may vary across different IoT environments and datasets.

---

## 🔮 Future Scope

Future improvements may include:

* Real-time IoT stream processing
* Online/incremental learning
* LSTM/GRU-based Autoencoders for time-series data
* Transformer-based anomaly detection
* Multivariate EVT modeling
* Edge-device deployment
* Real-time alert generation
* Integration with IoT monitoring dashboards
* Explainable AI for anomaly detection
* Deployment using cloud/edge infrastructure

---

## 👥 Project Team

**Final Year Project — Computer Science and Engineering**

**Project Title:**
**IoT Event/Extreme Value Detection using Autoencoders and Extreme Value Theory**

**Team Members:**

* Member 1 — Name
* Member 2 — Name
* Member 3 — Name
* Member 4 — Name

**Project Guide:**
Guide Name

**Department:**
Department of Computer Science and Engineering

**Institution:**\

---

## 📜 Project Status

**Status:** Under Development

### Development Stages

* [x] Project architecture
* [ ] Dataset preprocessing
* [ ] Exploratory data analysis
* [ ] Autoencoder development
* [ ] Anomaly-score generation
* [ ] EVT implementation
* [ ] Threshold optimization
* [ ] Model evaluation
* [ ] Visualization
* [ ] Final experimentation
* [ ] Documentation
* [ ] Final presentation

---

## 📚 References

The implementation will be based on research literature related to:

* Autoencoder-based anomaly detection
* IoT anomaly detection
* Extreme Value Theory
* Peaks Over Threshold methodology
* Generalized Pareto Distribution
* Deep learning for time-series anomaly detection

Research papers and dataset sources used during the project will be documented here as the project progresses.

---

## 📄 License

This project is developed for **academic and educational purposes** as part of a Final Year Project in Computer Science and Engineering.
