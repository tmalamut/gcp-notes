# Cloud TPU

### Definitions
* Hardware acceleration for ML
* Tensor Processing Units are Google's custom-developed application-specific integrated circuits used to accelerate machine learning workloads
* Cloud TPUs allow you to access TPUs from Compute Engine, GKE, and AI Platform

### Use Cases
* Cloud TPUs are optimized for specific workloads
* Suitable for the following:
    * Models dominated by matrix computations
    * Models with no custom TensorFlow/PyTorch/JAX operations inside the main training loop
    * Models the train for weeks or months
    * Large models with large effective batch sizes
* Not suitable for the following:
    * Linear algebra programs that require frequent branching or contain many element-wise algebra operations
    * Workloads that access memory in a sparse manner
    * Workloads that require high-precision arithmetic
    * Neural network workloads that contain custom operations in the main training loop