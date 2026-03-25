# Baseline Model: Linear Surrogate on SVD-Reduced Space

## Overview

The purpose of this milestone is to establish a foundational baseline model for the model order reduction (MOR) pipeline. Before implementing a complex Physics-Informed Neural Network (PINN) to capture non-linear dynamics, we first establish a linear baseline. This serves as a point of comparison to quantify the performance and accuracy gains achieved by the deep learning approaches in the main `Physics_Informed_Model_Order_Reduction_via_Neural_Networks (1).ipynb` notebook.

## Guidelines

### Choice of Model
The baseline model is a **Linear Regression (LR)** model operating on a reduced-order latent space. 
* **Why this model:** In standard MOR for finite element method (FEM) simulations, the simplest approach to map time steps (or system parameters) to a physical state is linear mapping. By combining Singular Value Decomposition (SVD) with linear regression, we create a classical Data-Driven surrogate. If the physical system exhibits highly non-linear transient behavior, this linear baseline will underfit, thereby justifying the need for neural network architectures.

### Feature Selection
Instead of training on the raw, high-dimensional spatial node data (e.g., 10,000 degrees of freedom), we use **Singular Value Decomposition (SVD)** to extract the dominant physical features.
* **Input Features:** Time steps ($t$).
* **Target Features:** The truncated latent space variables (the top $r=2$ to $r=6$ dominant SVD modes). These modes capture the majority of the system's variance and act as our reduced basis.

### Implementation
* **Data Preparation:** The full-order FEM data matrix $X$ is decomposed using SVD ($X = U \Sigma V^T$).
* **Reduction:** We truncate the matrices to the first $r$ modes. 
* **Model Training:** A standard Scikit-Learn or PyTorch linear regression model is fitted to predict the time-dependent coefficients of these dominant modes.
* **Reconstruction:** The predicted coefficients are multiplied by the spatial basis $U_r$ to reconstruct the full-order physical field.

### Evaluation
The model is evaluated using the **Mean Squared Error (MSE)** and **Relative $L_2$ Error** between the baseline's reconstructed physical field and the ground-truth full-order FEM solver output. A visualization comparing the exact state versus the baseline prediction at specific time steps is also generated to qualitatively assess spatial accuracy.

## Submission
The full implementation, including data generation, reduction, training, and evaluation, is contained in `baseline_model.ipynb`.
