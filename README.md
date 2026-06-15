# 🚀 End-to-End MLOps Pipeline using DVC & AWS S3

> A hands-on MLOps learning project that demonstrates how to build reproducible Machine Learning pipelines using **DVC**, **DVCLive**, **AWS S3**, and **Git**. The use case for this project is **SMS Spam Classification**, while the primary focus is understanding MLOps workflows and best practices.

---

## 📌 Project Overview

This project implements a complete Machine Learning pipeline for **SMS Spam Classification** while following MLOps principles such as:

* Data versioning
* Pipeline orchestration
* Experiment tracking
* Model versioning
* Reproducibility
* Cloud-based artifact storage

The goal of this project was **not just to train a machine learning model**, but to understand **how machine learning systems are built, tracked, and maintained in production-like environments**.

---

## 🎯 Objectives

* Build an end-to-end ML pipeline using DVC.
* Understand DVC stages and dependency tracking.
* Implement experiment tracking with DVC Experiments and DVCLive.
* Store artifacts remotely using AWS S3.
* Learn how Git and DVC complement each other.
* Create reproducible and maintainable ML workflows.

---

## 🛠️ Tech Stack

| Category               | Technologies                 |
| ---------------------- | ---------------------------- |
| Programming Language   | Python                       |
| Machine Learning       | Scikit-learn                 |
| NLP                    | NLTK                         |
| Data Versioning        | DVC                          |
| Experiment Tracking    | DVC Experiments, DVCLive     |
| Cloud Storage          | AWS S3                       |
| Version Control        | Git & GitHub                 |
| Configuration          | YAML                         |
| Environment Management | Virtual Environment (`venv`) |

---

## 📂 Project Structure

```text
MLOPS-complete-pipeline/
│
├── data/
│   ├── raw/
│   │   ├── train.csv
│   │   └── test.csv
│   │
│   ├── interim/
│   │   ├── train_processed.csv
│   │   └── test_processed.csv
│   │
│   └── processed/
│       ├── train_tfidf.csv
│       └── test_tfidf.csv
│
├── dvclive/
│   ├── metrics.json
│   ├── params.yaml
│   └── plots/
│       └── metrics/
│
├── experiments/
│   ├── mynotebook.ipynb
│   └── spam.csv
│
├── logs/
│   ├── data_ingestion.log
│   ├── data_preprocessing.log
│   ├── feature_engineering.log
│   ├── model_building.log
│   └── model_evaluation.log
│
├── models/
│   └── model.pkl
│
├── reports/
│   └── metrics.json
│
├── src/
│   ├── data_ingestion.py
│   ├── data_preprocessing.py
│   ├── feature_engineering.py
│   ├── model_building.py
│   └── model_evaluation.py
│
├── dvc.yaml
├── dvc.lock
├── params.yaml
├── requirements.txt
└── README.md
```

---

## 🔄 Pipeline Architecture

```text
Raw Dataset
    ↓
Data Ingestion
    ↓
Data Preprocessing
    ↓
Feature Engineering (TF-IDF)
    ↓
Model Building
    ↓
Model Evaluation
    ↓
Metrics & Artifacts
    ↓
DVC Tracking
    ↓
AWS S3 Remote Storage
```

---

## ⚙️ Pipeline Stages

### 1. Data Ingestion

* Loads the SMS Spam dataset.
* Splits data into training and testing sets.
* Saves outputs to `data/raw`.

**Output:**

```text
data/raw/train.csv
data/raw/test.csv
```

---

### 2. Data Preprocessing

* Cleans the dataset.
* Renames columns.
* Removes unnecessary features.

**Output:**

```text
data/interim/
```

---

### 3. Feature Engineering

* Converts text to lowercase.
* Tokenizes text.
* Removes stopwords and punctuation.
* Applies stemming.
* Generates TF-IDF features.

**Output:**

```text
data/processed/
```

---

### 4. Model Building

* Trains a machine learning classifier.
* Uses parameters defined in `params.yaml`.

**Output:**

```text
models/model.pkl
```

---

### 5. Model Evaluation

* Evaluates the trained model.
* Logs evaluation metrics.

**Output:**

```text
reports/metrics.json
```

---

## 🔍 Logging

Each stage of the pipeline maintains dedicated logs to improve traceability and debugging.

```text
logs/
├── data_ingestion.log
├── data_preprocessing.log
├── feature_engineering.log
├── model_building.log
└── model_evaluation.log
```

---

## 🧪 Experiment Tracking

This project uses **DVC Experiments** and **DVCLive** to monitor experiments and compare model performance.

### Run an Experiment

```bash
dvc exp run
```

### View Experiments

```bash
dvc exp show
```

### Apply an Experiment

```bash
dvc exp apply <experiment-name>
```

### Commit Experiment Results

```bash
dvc commit
```

---

## 📈 DVCLive Integration

DVCLive automatically tracks and visualizes metrics during experimentation.

Tracked metrics include:

* Accuracy
* Precision
* Recall

Metrics are stored under:

```text
dvclive/
```

---

## ☁️ AWS S3 Integration

DVC remote storage is configured using AWS S3.

### Configure AWS CLI

```bash
aws configure
```

### Add S3 Remote

```bash
dvc remote add -d dvcstore s3://<bucket-name>
```

### Push Artifacts to S3

```bash
dvc push
```

### Pull Artifacts from S3

```bash
dvc pull
```

This enables:

* Dataset versioning
* Model artifact storage
* Team collaboration
* Experiment reproducibility

---

## 🔀 Git vs DVC

### Git Tracks

```text
Source Code
Configuration Files
DVC Metadata
```

Examples:

```text
src/
params.yaml
dvc.yaml
dvc.lock
```

---

### DVC Tracks

```text
Datasets
Models
Metrics
Pipeline Outputs
```

Examples:

```text
data/
models/
reports/
dvclive/
```

---

## 🚀 How to Run the Project

### Clone the Repository

```bash
git clone https://github.com/SUJALGOYALL/MLOPS-complete-pipeline.git
cd MLOPS-complete-pipeline
```

---

### Create Virtual Environment

```bash
python -m venv .venv
```

---

### Activate Environment

**Windows**

```bash
.venv\Scripts\activate
```

**Linux / macOS**

```bash
source .venv/bin/activate
```

---

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

### Reproduce the Entire Pipeline

```bash
dvc repro
```

---

### Pull Artifacts from DVC Remote

```bash
dvc pull
```

---

## 📚 Key Learnings

Through this project, I gained practical experience in:

* Designing reproducible ML pipelines.
* Using DVC for data and model versioning.
* Understanding `dvc.yaml` and `dvc.lock`.
* Managing dependencies between pipeline stages.
* Tracking experiments efficiently.
* Integrating cloud storage using AWS S3.
* Leveraging DVCLive for experiment monitoring.
* Combining Git and DVC for end-to-end MLOps workflows.

---

## 🔮 Future Improvements

* Add MLflow for advanced experiment tracking.
* Implement CI/CD using GitHub Actions.
* Containerize the application using Docker.
* Deploy the model as a REST API.
* Add data drift monitoring.

---

## 🙏 Acknowledgements

This project was developed as part of my journey to learn and understand MLOps concepts.

Special thanks to:

* YouTube Tutorial: https://youtu.be/SMt3T-K2b_4
* DVC Documentation: https://dvc.org/doc
* AWS Documentation: https://docs.aws.amazon.com/

---

## ⭐ Support

If you found this project helpful or insightful, consider giving it a **star** on GitHub.

It motivates me to continue building and sharing more projects!