# Physics-Informed Surrogates, Digital Twins, and Inverse Solvers

## Repository Link

[https://github.com/midhun8629-sudo/Physics-Informed-Model-Order-Reduction-MOR-via-Neural-Networks/blob/main/README.md]

## Description
This repository contains a robust computational framework designed to accelerate high-fidelity finite element method (FEM) simulations (such as those typically executed in Abaqus or COMSOL). By coupling Singular Value Decomposition (SVD) for dimensionality reduction with deep neural networks built in PyTorch, this project creates a near real-time surrogate model. The framework maps temporal and parametric inputs directly to a reduced physical state, acting as a highly efficient digital twin for transient materials engineering problems while circumventing the computational bottleneck of traditional numerical solvers.

### Task Type
Multivariate Regression / Time-Series Surrogate Modeling / Reduced Order Modeling (ROM)

### Results Summary

* **Key Result:** Successfully replaced a computationally heavy 10,000-degree-of-freedom transient FEM solver with a deep learning surrogate, achieving real-time inference speeds while maintaining strict physical accuracy.

#### Best Model Performance
- **Best Model:** PyTorch Multilayer Perceptron (MLP) operating on an SVD-reduced latent space.
- **Evaluation Metric:** Relative $L_2$ Error (computational mechanics standard) and Mean Squared Error (MSE).
- **Final Performance:** Achieved highly accurate spatial reconstruction of the physical field across 50 time steps, minimizing the $L_2$ norm of the residual error matrix.

#### Model Comparison
- **Baseline Performance:** SVD coupled with a classical Linear Regression model.
- **Improvement Over Baseline:** Significant reduction in reconstruction error. The neural network successfully captured complex, non-linear transient dynamics that the linear baseline underfit and failed to predict.
- **Best Alternative Model:** Proper Generalized Decomposition (PGD) or purely linear Proper Orthogonal Decomposition (POD).

#### Key Insights
- **Most Important Features:** The top $r=2$ to $r=6$ dominant spatial modes extracted via SVD, which capture the vast majority of the thermodynamic or mechanical variance in the system.
- **Model Strengths:** Delivers near-zero latency predictions; maintains physical interpretability by projecting neural network outputs back onto an orthogonal, mathematically sound spatial basis.
- **Model Limitations:** The data-driven nature of the SVD requires pre-computed high-fidelity snapshot matrices; purely data-driven MLPs may struggle to extrapolate outside the original training parameter domain without explicit PDE-loss regularization (PINN integration).
- **Academic & Engineering Impact:** Enables the rapid prototyping of material structures and the deployment of real-time digital twins. This massive reduction in computational cost is critical for multi-scale modeling, optimization loops, and inverse problem-solving in advanced computational mechanics pipelines.

## Documentation

1. **[Literature Review](0_LiteratureReview/README.md)**
2. **[Dataset Characteristics](1_DatasetCharacteristics/exploratory_data_analysis.ipynb)**
3. **[Baseline Model](2_BaselineModel/baseline_model.ipynb)**
4. **[Model Definition and Evaluation](3_Model/Physics_Informed_Model_Order_Reduction_via_Neural_Networks (1).ipynb)**
5. **[Presentation](4_Presentation/README.md)**


