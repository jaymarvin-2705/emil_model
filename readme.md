# Student Performance Predictor

A simple Machine Learning application developed using Python, Scikit-learn, Joblib, and Streamlit. The application predicts a student's performance based on study hours and attendance percentage.

This project is designed for **IT Elective 3 — AI: Machine Learning** as a practical demonstration of model persistence and basic Machine Learning deployment.

## 1. Project Overview

The Student Performance Predictor demonstrates how to:

- Train a Machine Learning model using sample student data.
- Save a trained model using Joblib.
- Load and reuse a saved model without retraining it.
- Accept study hours and attendance percentage as inputs.
- Generate Pass/Fail predictions using a Decision Tree Classifier.
- Display predictions through an interactive Streamlit web application.
- Visualize predicted classes at different attendance percentages.

**Important:** This project uses fictional training data for educational purposes. Predictions are demonstrations and must not be treated as reliable assessments of actual student performance.

## 2. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Scikit-learn | Machine Learning model training and prediction |
| Joblib | Saving and loading the trained model |
| Streamlit | Building the interactive web interface |
| Pandas | Organizing data for visualization |

## 3. Project Structure

```text
emil/
│
├── train_model.py
├── streamlit_app.py
├── README.md
│
└── models/
    └── student_pass_model.joblib
```

### File descriptions

- `train_model.py` — trains the Decision Tree model and saves it.
- `streamlit_app.py` — runs the web application and displays predictions.
- `models/student_pass_model.joblib` — contains the saved trained model.
- `README.md` — documents the project and explains how to run it.

The `models/` directory and model file are generated when the training script runs.

## 4. Features

### Student Information Input

Users can enter:

- Student name
- Study hours per day, from 0 to 24
- Attendance percentage, from 0% to 100%

### Machine Learning Prediction

The application uses a Decision Tree Classifier to predict one of two classes:

- **Pass (1)**
- **Fail (0)**

The model uses two input features:

1. Study hours
2. Attendance percentage

### Prediction Visualization

The application displays a chart showing predicted classes at different attendance percentages while keeping the entered study hours constant.

The chart uses the following numerical encoding:

- `0` = Fail
- `1` = Pass

These values represent predicted classes, not probabilities or percentages.

## 5. Installation Guide

### Step 1: Install Python

Install Python 3.10 or later.

Check your installation:

```bash
python --version
```

On Windows, you can also use:

```powershell
py --version
```

### Step 2: Open the Project Folder

Open the `ml_model_deployment` folder in Visual Studio Code.

Open a terminal using **Terminal → New Terminal**.

### Step 3: Create a Virtual Environment

On Windows:

```powershell
python -m venv .venv
```

Activate the environment in PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

Alternatively, use Command Prompt:

```cmd
.venv\Scripts\activate.bat
```

### Step 4: Install Dependencies

Run:

```bash
python -m pip install --upgrade pip
pip install scikit-learn joblib streamlit pandas
```

Verify the installation:

```bash
python -c "import sklearn, joblib, streamlit, pandas; print('Installation successful!')"
```

## 6. Train and Save the Model

Before launching the application for the first time, train the model.

Run:

```bash
python train_model.py
```

The script trains a Decision Tree Classifier and saves the model to:

```text
models/student_pass_model.joblib
```

Expected terminal output:

```text
Model trained successfully!
Features: Study hours and attendance percentage.
Saved to models/student_pass_model.joblib
```

The actual messages depend on the print statements in your training script.

**Note:** The training script must use two features in the same order expected by the application: study hours first, followed by attendance percentage.

## 7. Run the Streamlit Application

After training the model, execute:

```bash
streamlit run streamlit_app.py
```

Streamlit will provide a local web address, usually:

```text
http://localhost:8501
```

Open the address in your browser if it does not open automatically.

### How to Use the Application

1. Enter the student's name.
2. Enter the number of study hours per day.
3. Enter the attendance percentage.
4. Click **Predict Performance**.
5. Review the predicted result.
6. Examine the attendance chart.

The application loads the saved model and uses it to generate predictions.

## 8. How Model Persistence Works

Model persistence allows a trained Machine Learning model to be saved and reused.

The training script uses:

```python
joblib.dump(model, "models/student_pass_model.joblib")
```

This saves the trained model.

The application uses:

```python
model = joblib.load("models/student_pass_model.joblib")
```

This loads the saved model into memory.

Predictions are then generated using:

```python
prediction = model.predict([
    [study_hours, attendance]
])[0]
```

The model does not need to be retrained every time a user requests a prediction.

Retraining is necessary when you want to update the model using new training data, change its training process, or improve its learned behavior.

## 9. Sample Prediction

Suppose the user enters:

| Input | Value |
|---|---|
| Student name | Alex |
| Study hours | 5 |
| Attendance | 80% |

The application passes the two numerical features to the model.

The model returns either `0` or `1`, which the application converts into `Fail` or `Pass`.

**The predicted result depends on the trained model.** The example inputs do not guarantee a particular result.

## 10. Troubleshooting

### Error: Model file not found

Example:

```text
FileNotFoundError:
models/student_pass_model.joblib
```

**Solution:**

Run the training script first:

```bash
python train_model.py
```

Make sure you launch Streamlit from the project root directory.

### Error: No module named 'streamlit'

Install the required packages:

```bash
python -m pip install streamlit joblib scikit-learn pandas
```

Make sure your virtual environment is activated.

### Error: Number of features does not match

This may happen if you load an older model trained using only study hours.

**Solution:**

Retrain the updated model using both study hours and attendance:

```bash
python train_model.py
```

Then restart Streamlit.

### Error: Streamlit command not found

Run Streamlit through Python:

```bash
python -m streamlit run streamlit_app.py
```

### Error: Port 8501 is already in use

Run the application on another port:

```bash
streamlit run streamlit_app.py --server.port 8502
```

## 11. Limitations

- The model uses a small, fictional dataset.
- Its predictions are not validated against real student outcomes.
- The model only predicts Pass or Fail.
- The chart shows predicted classes rather than probabilities.
- The application does not save student records or prediction history.
- The project is intended for classroom learning, not official academic decision-making.

For future improvements, the model could be trained and evaluated using a larger, representative dataset with appropriate privacy protections. Additional features and evaluation metrics could also be introduced.

## 12. Learning Outcomes

After completing this project, students should be able to:

1. Explain model persistence and deployment.
2. Train a basic Machine Learning classifier.
3. Save and load a model using Joblib.
4. Make predictions using multiple input features.
5. Build an interactive application using Streamlit.
6. Display predictions using a chart.
7. Explain the limitations of predictions generated from a small training dataset.

## 13. Author and Academic Information

**Project:** Student Performance Predictor  
**Subject:** IT Elective 3 — AI: Machine Learning  
**Language:** Python  
**Application Framework:** Streamlit  
**Model:** Decision Tree Classifier  
**Purpose:** Educational demonstration of Machine Learning model persistence and deployment

---

*This project is intended for educational use. Its predictions should not be used as the sole basis for actual academic decisions.*