# GRB Redshift Prediction ML Model Explanation

## Overview
This code implements a **stacked ensemble machine learning model** to predict the redshift (cosmological distance) of Gamma-Ray Bursts (GRBs) using observable spectral and temporal properties.

## Scientific Context

### Problem Statement
- **Redshift measurement challenge**: Determining GRB distances requires expensive spectroscopy
- **Missing data**: Many GRBs lack redshift measurements
- **Solution**: ML-based "pseudo-redshifts" enable large-scale statistical studies

### Input Features
- **T90**: Burst duration (seconds) - how long the GRB lasts
- **Alpha**: Low-energy spectral index - shape of spectrum at low energies
- **Beta**: High-energy spectral index - shape of spectrum at high energies  
- **Ep**: Peak energy of spectrum (keV) - energy where most photons are emitted
- **Sbolo**: Bolometric fluence (erg/cm²) - total energy received

## Data Preprocessing Pipeline

### 1. Data Loading & Selection
```python
url = 'https://raw.githubusercontent.com/Adrita-Khan/GRB-ML/main/Data/kw_band_flc.xlsx'
GBM_df = pd.read_excel(url)
Columns = ['Redshift', 'T90', 'Alpha', 'Beta', 'Ep', 'Sbolo']
```

### 2. Log Transformation
```python
log = np.log10(GBM_df[['T90', 'Ep', 'Sbolo']])
```
- **Why log transform**: T90, Ep, and Sbolo span several orders of magnitude
- **Alpha and Beta**: Keep original values (already well-scaled spectral indices)

### 3. Data Splitting & Standardization
```python
X_train, X_test, y_train, y_test = train_test_split(Data_X, Data_y, test_size=0.3, random_state=42)
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
```
- **70/30 split**: 70% training, 30% testing
- **StandardScaler**: Converts features to mean=0, std=1 for neural network stability

## Model Architecture: Stacked Ensemble

### Base Learners (4 Deep Neural Networks)

The ensemble uses 4 different neural network architectures as base learners:

#### Model 1: Simple Network
```python
Sequential([
    Dense(64, input_dim=X_train.shape[1], activation='relu'),
    Dense(50, activation='relu'),
    Dense(1, activation='linear')  # Regression output
])
```
- **2 hidden layers**: 64 → 50 neurons
- **Purpose**: Baseline simple model

#### Model 2: Deeper Network
```python
Sequential([
    Dense(128, input_dim=X_train.shape[1], activation='relu'),
    Dense(64, activation='relu'),
    Dense(32, activation='relu'),
    Dense(1, activation='linear')
])
```
- **3 hidden layers**: 128 → 64 → 32 neurons
- **Purpose**: Capture more complex patterns

#### Model 3: Wide & Deep
```python
Sequential([
    Dense(141, input_dim=X_train.shape[1], activation='relu'),
    Dense(77, activation='relu'),
    Dense(83, activation='relu'),
    Dense(66, activation='relu'),
    Dense(1, activation='linear')
])
```
- **4 hidden layers**: 141 → 77 → 83 → 66 neurons
- **Purpose**: Even more capacity for complex relationships

#### Model 4: Deepest Network
```python
Sequential([
    Dense(156, input_dim=X_train.shape[1], activation='relu'),
    Dense(85, activation='relu'),
    Dense(42, activation='relu'),
    Dense(30, activation='relu'),
    Dense(22, activation='relu'),
    Dense(1, activation='linear')
])
```
- **5 hidden layers**: 156 → 85 → 42 → 30 → 22 neurons
- **Purpose**: Maximum complexity capture

### Model Training Configuration
```python
model.compile(optimizer=SGD(learning_rate=0.01), loss='mean_squared_error')
model.fit(X_train_scaled, y_train, epochs=50, batch_size=120, verbose=0)
```
- **Optimizer**: Stochastic Gradient Descent with 0.01 learning rate
- **Loss**: Mean Squared Error (appropriate for regression)
- **Training**: 50 epochs with batch size 120

## Stacking Methodology

### Step 1: Base Model Predictions
```python
predictions_train = []
for model in models:
    prediction_train = model.predict(X_train_scaled)
    predictions_train.append(prediction_train.flatten())
```
Each base model makes predictions on training data.

### Step 2: Meta-Features Creation
```python
meta_features_train = np.column_stack(predictions_train)
```
Stack predictions as columns: [Model1_pred, Model2_pred, Model3_pred, Model4_pred]

### Step 3: Meta-Learner Training
```python
final_estimator = RandomForestRegressor()
final_estimator.fit(meta_features_train, y_train)
```
- **Meta-learner**: Random Forest Regressor
- **Input**: Predictions from 4 base models
- **Output**: Final redshift prediction

## Why This Architecture Works

### Ensemble Benefits
1. **Diversity**: Different network architectures capture different patterns
2. **Robustness**: Reduces overfitting compared to single models
3. **Improved Accuracy**: Meta-learner optimally combines base predictions

### Neural Network Choice
- **Universal Approximation**: Can model complex non-linear relationships between GRB properties and redshift
- **Multiple Architectures**: Different depths/widths capture different aspects of the data

### Random Forest Meta-Learner
- **Non-parametric**: No assumptions about relationship between base predictions
- **Feature Interactions**: Can capture complex interactions between base model outputs
- **Robust**: Less prone to overfitting than linear meta-learners

## Evaluation Metrics

### Performance Measures
```python
rmse = np.sqrt(mean_squared_error(y_test, stacked_predictions))
mae = mean_absolute_error(y_test, stacked_predictions)  
score = r2_score(y_test, stacked_predictions)
```
- **RMSE**: Root Mean Square Error (penalizes large errors)
- **MAE**: Mean Absolute Error (average prediction error)
- **R²**: Coefficient of determination (fraction of variance explained)

### Distribution Validation
```python
_, p_value = kstest(heights, heights1)
```
- **Kolmogorov-Smirnov Test**: Compares distributions of true vs predicted redshifts
- **High p-value** (>0.05): Distributions are statistically similar

## Practical Applications

### Scientific Impact
1. **Population Studies**: Explore GRB distribution across cosmic time
2. **Cosmological Analysis**: Constrain dark energy and star formation models
3. **Target Selection**: Identify high-redshift GRB candidates for follow-up
4. **Statistical Studies**: Enable large sample analyses without spectroscopy

### Data Filtering
```python
Band_flc = Band_flc[Band_flc['T90'] >= 2.1]  # Long GRBs only
Band_flc = Band_flc[Band_flc['Beta'] <= -2]  # Remove outliers
```
Focuses on long-duration GRBs with physically reasonable spectral parameters.


