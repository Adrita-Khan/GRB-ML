**Stacked ensemble** model for predicting redshift values from **gamma-ray burst (GRB)** data. Below is the breakdown of the base model architecture:

## Base Model Architecture

The system uses **4 different Deep Neural Network (DNN) regressors** as base models, each with distinct architectures:

### Model 1: Simple Deep Network
- **Hidden layers**: 2 layers with [64, 50] neurons
- **Activation function**: ReLU
- **Architecture**: Input → 64 neurons → 50 neurons → Output

### Model 2: Medium Depth Network
- **Hidden layers**: 3 layers with [128, 64, 32] neurons
- **Activation function**: ReLU
- **Architecture**: Input → 128 neurons → 64 neurons → 32 neurons → Output

### Model 3: Complex Network
- **Hidden layers**: 4 layers with [141, 77, 83, 66] neurons
- **Activation function**: ReLU
- **Architecture**: Input → 141 neurons → 77 neurons → 83 neurons → 66 neurons → Output

### Model 4: Deep Hierarchical Network
- **Hidden layers**: 5 layers with [156, 85, 42, 30, 22] neurons
- **Activation function**: ReLU
- **Architecture**: Input → 156 neurons → 85 neurons → 42 neurons → 30 neurons → 22 neurons → Output

## Common Base Model Characteristics

All base models share these specifications:
- **Framework**: TensorFlow Estimator API (`tf.estimator.DNNRegressor`)
- **Input features**: 5 features (T90, Ep, Sbolo - log-transformed; Alpha, Beta - raw spectral indices)
- **Feature preprocessing**: StandardScaler normalization
- **Optimizer**: Stochastic Gradient Descent (SGD) with learning rate 0.1
- **Loss function**: Mean squared error with `sum_over_batch_size` reduction
- **Training steps**: 5,000 iterations each
- **Batch size**: 120 for training, varies for prediction

## Ensemble (Stacking) Architecture

The stacking approach works as follows:

1. **Base Level**: Each of the 4 DNN models trains independently on the same training data
2. **Meta Level**: A Random Forest regressor serves as the meta-model
3. **Prediction Process**: 
   - Each base model makes predictions
   - These predictions become input features for the meta-model
   - The meta-model produces the final prediction

## Key Design Decisions

- **Diverse architectures**: Different depths and widths to capture various patterns
- **Progressive complexity**: Models range from simple (2 layers) to deep (5 layers)
- **Ensemble diversity**: Different network topologies should learn complementary representations
- **Meta-learning**: Random Forest combines base model outputs, potentially capturing non-linear relationships between their predictions

This architecture is designed to leverage the strengths of multiple neural networks while using ensemble learning to improve overall prediction accuracy for redshift estimation from GRB observational data.
