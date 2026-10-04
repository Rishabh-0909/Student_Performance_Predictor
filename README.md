# 🎓 Student Performance Predictor

> **An end-to-end Machine Learning application that predicts a student's Mathematics score using demographic, academic, and test-performance features.**

<p align="center">





\

</p>

---

## 📌 Overview

**Student Performance Predictor** is a complete Machine Learning project designed to predict a student's **Mathematics score** based on demographic information, educational background, test preparation, and previous Reading and Writing scores.

The project follows a modular **end-to-end ML pipeline**, starting from data ingestion and preprocessing and ending with a deployed Flask web application capable of generating predictions from user-provided inputs.

### ✨ What makes this project different?

* 🔍 Exploratory Data Analysis
* 🧹 Automated data preprocessing
* 🔢 Numerical & categorical feature handling
* 🤖 Multiple regression algorithms
* ⚙️ Hyperparameter tuning
* 🏆 Automatic best-model selection
* 💾 Model & preprocessing serialization
* 🌐 Flask-based prediction interface
* 📝 Custom logging
* ⚠️ Custom exception handling
* 📦 Modular project architecture

---

## 🎯 Problem Statement

The objective is to build a regression model capable of predicting a student's **Mathematics score** using the following information:

| Feature                       | Description                                        |
| ----------------------------- | -------------------------------------------------- |
| `gender`                      | Student's gender                                   |
| `race_ethnicity`              | Student's race/ethnicity group                     |
| `parental_level_of_education` | Parent's highest education level                   |
| `lunch`                       | Type of lunch received                             |
| `test_preparation_course`     | Whether the student completed a preparation course |
| `reading_score`               | Student's Reading score                            |
| `writing_score`               | Student's Writing score                            |
| **`math_score`**              | **Target variable**                                |

### 🎯 Target Variable

```text
math_score
```

The problem is treated as a **supervised regression task**.

---

## 📊 Model Performance

The trained models are evaluated using the **R² (Coefficient of Determination)** metric.

### 🏆 Recorded Test Performance

<div align="center">

### **R² Score: 0.8786**

</div>

The recorded model explains approximately **87.86% of the variance** in Mathematics scores on the test dataset.

| Metric            |      Value |
| ----------------- | ---------: |
| Train/Test Split  |    80 / 20 |
| Random State      |         42 |
| Evaluation Metric |   R² Score |
| Recorded R²       | **0.8786** |

> **Note:** The reported score corresponds to the recorded test split and may vary if the dataset, preprocessing pipeline, random seed, or model configuration is changed.

---

# 🧠 Machine Learning Pipeline

```text
                         ┌─────────────────┐
                         │     Dataset     │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │ Data Ingestion  │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │ Train/Test Split│
                         └────────┬────────┘
                                  │
                                  ▼
                       ┌─────────────────────┐
                       │ Data Transformation │
                       │                     │
                       │ • Imputation        │
                       │ • Scaling           │
                       │ • One-Hot Encoding │
                       └──────────┬──────────┘
                                  │
                                  ▼
                       ┌─────────────────────┐
                       │   Model Training    │
                       └──────────┬──────────┘
                                  │
                                  ▼
                       ┌─────────────────────┐
                       │  Model Evaluation   │
                       └──────────┬──────────┘
                                  │
                                  ▼
                       ┌─────────────────────┐
                       │ Best Model Selection│
                       └──────────┬──────────┘
                                  │
                                  ▼
                 ┌─────────────────────────────────┐
                 │ Saved Model + Preprocessor      │
                 │                                 │
                 │ model.pkl                       │
                 │ preprocessor.pkl                │
                 └───────────────┬─────────────────┘
                                 │
                                 ▼
                       ┌─────────────────────┐
                       │ Flask Prediction App│
                       └─────────────────────┘
```

---

# 🤖 Machine Learning Models

The project compares multiple regression algorithms to identify the best-performing model.

### Models Evaluated

1. **Random Forest Regressor**
2. **Decision Tree Regressor**
3. **Gradient Boosting Regressor**
4. **Linear Regression**
5. **XGBoost Regressor**
6. **CatBoost Regressor**
7. **AdaBoost Regressor**

Each model is trained and evaluated using the same processed dataset.

The model with the best evaluation performance is automatically selected and serialized for deployment.

---

# 🔬 Data Preprocessing

The preprocessing pipeline handles numerical and categorical variables separately using a `ColumnTransformer`.

## 🔢 Numerical Features

Numerical features are processed using:

* Median imputation
* Standard scaling

```text
Numerical Data
      │
      ▼
Median Imputation
      │
      ▼
Standard Scaling
      │
      ▼
Processed Numerical Features
```

## 🔤 Categorical Features

Categorical features are processed using:

* Most-frequent imputation
* One-hot encoding
* Standard scaling where applicable

```text
Categorical Data
      │
      ▼
Most-Frequent Imputation
      │
      ▼
One-Hot Encoding
      │
      ▼
Processed Categorical Features
```

The complete fitted preprocessing pipeline is saved as:

```text
artifacts/preprocessor.pkl
```

This ensures that new user inputs are transformed consistently with the data used during model training.

---

# 🏗️ Project Architecture

The project follows a modular architecture separating data processing, model training, prediction, and application logic.

```text
Student_Performance_Predictor/
│
├── artifacts/
│   ├── data.csv
│   ├── train.csv
│   ├── test.csv
│   ├── model.pkl
│   └── preprocessor.pkl
│
├── notebook/
│   └── data/
│       └── stud.csv
│
├── src/
│   ├── components/
│   │   ├── data_ingestion.py
│   │   ├── data_transformation.py
│   │   └── model_trainer.py
│   │
│   ├── pipeline/
│   │   └── predict_pipeline.py
│   │
│   ├── exception.py
│   ├── logger.py
│   └── utils.py
│
├── templates/
│   ├── home.html
│   └── index.html
│
├── static/
│   └── style.css
│
├── app.py
├── requirements.txt
├── setup.py
├── .gitignore
├── LICENSE
└── README.md
```

---

# 🛠️ Tech Stack

### Machine Learning

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **XGBoost**
* **CatBoost**

### Backend

* **Flask**

### Frontend

* **HTML**
* **CSS**

### Development & Version Control

* **Git**
* **GitHub**

---

# 🌐 Flask Web Application

The project includes a web interface that allows users to enter the student's information and receive a predicted Mathematics score.

### User Inputs

```text
Gender
Race/Ethnicity
Parental Level of Education
Lunch
Test Preparation Course
Reading Score
Writing Score
```

### Prediction Flow

```text
User Input
    │
    ▼
Flask Application
    │
    ▼
Prediction Pipeline
    │
    ▼
Saved Preprocessor
    │
    ▼
Trained ML Model
    │
    ▼
Predicted Mathematics Score
```

The application loads the previously trained:

```text
artifacts/model.pkl
artifacts/preprocessor.pkl
```

rather than retraining the model every time a prediction is requested.

---

# ⚙️ Installation & Setup

## 1. Clone the Repository

```bash
git clone https://github.com/Rishabh-0909/student-performance-predictor.git
cd student-performance-predictor
```

## 2. Create a Virtual Environment

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

## 4. Run the Application

```bash
python app.py
```

## 5. Open in Browser

Visit:

```text
http://127.0.0.1:5000/
```

---

# 💾 Model Artifacts

The trained ML components are stored inside the `artifacts/` directory.

### Trained Model

```text
artifacts/model.pkl
```

### Preprocessing Pipeline

```text
artifacts/preprocessor.pkl
```

During prediction, both artifacts are loaded and used to process new inputs.

This separation allows the application to use the exact same transformations applied during training.

---

# 📈 Evaluation

The project uses **R² Score** as its primary regression evaluation metric.

### Why R²?

R² measures the proportion of variance in the target variable that can be explained by the model.

```text
R² = 1 - (Residual Sum of Squares / Total Sum of Squares)
```

A higher R² indicates that the model explains a larger proportion of the variation in Mathematics scores.

### Evaluation Configuration

| Configuration    | Value        |
| ---------------- | ------------ |
| Problem Type     | Regression   |
| Target           | `math_score` |
| Train/Test Split | 80/20        |
| Random State     | 42           |
| Metric           | R²           |
| Recorded Score   | **0.8786**   |

---

# 📁 Important Files

| File                     | Purpose                           |
| ------------------------ | --------------------------------- |
| `data_ingestion.py`      | Loads and splits the dataset      |
| `data_transformation.py` | Builds the preprocessing pipeline |
| `model_trainer.py`       | Trains and evaluates ML models    |
| `predict_pipeline.py`    | Handles inference on new data     |
| `exception.py`           | Custom exception handling         |
| `logger.py`              | Application logging               |
| `utils.py`               | Utility functions                 |
| `app.py`                 | Flask application                 |
| `model.pkl`              | Serialized trained model          |
| `preprocessor.pkl`       | Serialized preprocessing pipeline |

---

# 🔮 Future Improvements

The current implementation can be extended with:

* 🐳 **Docker containerization**
* ☁️ **Cloud deployment**
* 🔎 **SHAP model explainability**
* 🔁 **Cross-validation**
* 📦 **Batch prediction**
* 📜 **Prediction history**
* ⚙️ **CI/CD pipeline**
* 📊 **Model monitoring**
* 📈 **Interactive analytics dashboard**
* 🔐 **User authentication**
* 🧪 **Automated testing**

---

# 🚀 Possible Production Architecture

A future production-ready version could follow:

```text
                    ┌───────────────┐
                    │   Web Client  │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Flask / API   │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Prediction    │
                    │ Pipeline      │
                    └───────┬───────┘
                            │
                  ┌─────────┴─────────┐
                  ▼                   ▼
          ┌──────────────┐    ┌──────────────┐
          │ Preprocessor │    │ ML Model     │
          └──────────────┘    └──────────────┘
                  │                   │
                  └─────────┬─────────┘
                            ▼
                    ┌───────────────┐
                    │   Prediction  │
                    └───────────────┘
```

---

# ⚠️ Disclaimer

This project is intended for **educational and portfolio purposes**.

The predictions generated by the model are statistical estimates and should **not** be considered a definitive assessment of a student's academic ability or future performance.

---

# 📄 License

This project is licensed under the **MIT License**.

See the [`LICENSE`](LICENSE) file for more information.

---

# 👨‍💻 Author

## Rishabh Jha

**Electrical Engineering Student**

Machine Learning • Data Analytics • Software Development

<p align="center">

⭐ If you found this project useful, consider giving the repository a star!

</p>
