# Dataset Characteristics

**[Notebook](Physics_Informed_Model_Order_Reduction_via_Neural_Networks%20(1).ipynb)**

## Dataset Information

### Dataset Source
- **Dataset Link:** Synthetically generated within the notebook. The data simulates the output of a heavy Finite Element Method (FEM) solver.
- **Dataset Owner/Contact:** N/A (Generated programmatically)

### Dataset Characteristics
- **Number of Observations:** 10,000 spatial nodes. The temporal resolution spans 50 discrete time steps.
- **Number of Features:** 50 original dimensions (representing the time steps), which are subsequently reduced to a compact latent space (2 to 6 dominant modes) via Singular Value Decomposition (SVD).

### Target Variable/Label
- **Label Name:** Physical State / Field Solution (e.g., displacement, temperature)
- **Label Type:** Regression
- **Label Description:** The label represents the solution to the governing physical equations at a specific spatial node and time step. The predictive task is to use a neural network surrogate to map the reduced input space to these physical states in real-time, bypassing the computationally expensive FEM solver.
- **Label Values:** Continuous real numbers corresponding to the physical field values.
- **Label Distribution:** Determined by the underlying Partial Differential Equations (PDEs), initial conditions, and boundary conditions applied during the synthetic data generation.

### Feature Description
- **Feature 1 (Spatial Domain):** High-dimensional spatial coordinate data mapping the 10,000 nodes of the simulation mesh.
- **Feature 2 (Temporal Domain):** 50 distinct temporal snapshots capturing the transient evolution of the physical system.
- **Feature Group (Reduced Physics Basis):** The truncated latent features (the top 2 to 6 modes) extracted via SVD. These features capture the most dominant variance and physical behaviors of the system, acting as the low-dimensional inputs for the surrogate neural network.

## Exploratory Data Analysis

The exploratory data analysis and preprocessing are conducted in the [Physics_Informed_Model_Order_Reduction_via_Neural_Networks (1).ipynb](Physics_Informed_Model_Order_Reduction_via_Neural_Networks%20(1).ipynb) notebook, which includes:

- Generation and shaping of the synthetic FEM data matrix (10,000 x 50).
- Computation of Singular Value Decomposition (SVD) to extract the primary physics basis.
- Model order reduction evaluating the truncation from 50 dimensions down to the top 2 to 6 modes.
- Training convergence tracking for the PyTorch-based surrogate neural network (monitoring loss reduction across hundreds of epochs).
