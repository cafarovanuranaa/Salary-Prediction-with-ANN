# Salary-Prediction-with-ANN
This project is structured into four main stages: data preprocessing, model development, performance evaluation, and final deployment on new employee data.
## Project Stages

### Step 1 – Data Preprocessing

The following data preparation steps were applied:

- Removed missing rows (only a small number were incomplete)
- Standardized inconsistent values in the "Education Level" column (e.g., `"phD"` → `"PhD"`)
- Calculated job-level statistics such as mean and sum of experience by job title
- Applied one-hot encoding for categorical features
- Scaled numeric features using `StandardScaler`

---

### Step 2 – Model Building and Hyperparameter Tuning

A fully connected neural network was developed using TensorFlow (Keras) with the following structure:

- Two hidden layers (ReLU activation)
- One output layer (ReLU activation)
- Loss function: `mean_absolute_error`
- Optimizers considered: `adam`, `sgd`, `rmsprop`, `adagrad`

Hyperparameters such as the number of units per layer, learning rate, batch size, and optimizer type were tuned using the Optuna framework.

The objective metric for optimization was the R² score on the test dataset.

---

### Step 3 – Model Evaluation

After identifying the best configuration from Optuna, the final model was trained on the full training set. The performance was measured as follows:
Train	4311	20676.368576
1	Test	5755	20561.493950

| Dataset | R² Score | MAE    |
|---------|----------|--------|
| Train   | ~0.74    | ~20676 |
| Test    | ~0.76    | ~20561 |

---

### Step 4 – Deployment on New Employee Data

A new dataset containing employee profiles was processed using the same preprocessing pipeline. The trained model was then used to predict the expected salary for each entry.

The results were stored in a new column named `predicted_Salary` within the same DataFrame.
