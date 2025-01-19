### 1. What are the 5 levels of MLOps Readiness Level? Explain each of them.

1. **Manual Process (Level 0)**: All ML steps, such as data preprocessing, training, evaluation, and deployment, are done manually without automation.
2. **ML Pipeline Automation (Level 1)**: Automates the ML pipeline but does not include CI/CD for production. Suitable for experiments but lacks scalability.
3. **CI/CD for ML (Level 2)**: Integrates CI/CD principles for both model and data changes. Ensures smooth integration, testing, and deployment of models.
4. **Continuous Training (CT) (Level 3)**: Automatically retrains models with fresh data in production. Includes monitoring for data and model drifts.
5. **Adaptive ML Systems (Level 4)**: Fully autonomous systems that self-adapt to changing data and operational conditions without manual intervention.

---

### 2. What are the parts/components of an MLOps system?
1. **Data Management**: Handling, preprocessing, and versioning datasets.
2. **Model Development**: Tools for training, validating, and iterating on ML models.
3. **Model Versioning**: Tracking changes in models.
4. **Model Deployment**: Serving models via APIs or batch processing.
5. **Monitoring**: Observing model performance and detecting drifts.
6. **Orchestration**: Automating and managing workflows and pipelines.
7. **Infrastructure Management**: Ensuring resources like storage and compute are available.
8. **Security and Governance**: Maintaining compliance and secure operations.

---

### 3. Can you name at least 5 metrics relevant to evaluate an MLOps system?
1. Deployment time (time to go from development to production).
2. Model latency (response time of predictions).
3. Pipeline execution time.
4. Data and model drift detection rates.
5. Infrastructure cost efficiency.

---

### 4. What are the Advantages/Inconveniences of deploying a model to the cloud?
**Advantages**:
- Scalability and elasticity.
- Cost-effective for variable workloads.
- Easy integration with CI/CD pipelines.
- Access to managed services like monitoring.

**Inconveniences**:
- Latency issues for real-time applications.
- Dependency on third-party providers.
- Potential data privacy and compliance concerns.
- Costs can scale unpredictably with usage.

---

### 5. What are the Advantages/Inconveniences of deploying a model on-premise?
**Advantages**:
- Data privacy and security control.
- Lower latency for local operations.
- Better suited for regulated industries.

**Inconveniences**:
- High initial infrastructure cost.
- Limited scalability.
- Maintenance and expertise requirements.

---

### 6. What are the four deployment paradigms to deploy a service?
1. **Batch Inference**: Predictions are generated for a dataset in bulk.
2. **Online Inference**: Real-time predictions for incoming requests.
3. **Streaming Inference**: Predictions on a continuous stream of data.
4. **Hybrid Inference**: Combines batch and online inference as needed.

---

### 7. What is the main advantage of a Dedicated Server to deploy a service?
**Advantage**: High performance with full resource control and predictability.

---

### 8. What are the disadvantages of a dedicated server for deploying a service?
- High initial cost.
- Scalability challenges.
- Maintenance overhead.
- Risk of underutilization.

---

### 9. What are the Advantages/Inconveniences of deploying a model on serverless infrastructure?
**Advantages**:
- No infrastructure management required.
- Pay-per-use model.
- Auto-scaling capabilities.

**Inconveniences**:
- Cold start latency.
- Limited configuration options.
- May not handle long-running tasks efficiently.

---

### 10. Can you name five different optimization techniques to deploy a model in production?
1. Quantization.
2. Pruning.
3. Knowledge distillation.
4. Hardware acceleration (e.g., GPUs, TPUs).
5. Model architecture optimization (e.g., lightweight architectures like MobileNet).

---

### 11. What are the two different types of quantization? Which one is the most performant?
1. **Post-training quantization**: Applies quantization after training.
2. **Quantization-aware training**: Incorporates quantization during training for better performance.
**Most Performant**: Quantization-aware training.

---

### 12. What is LoRa? What is its purpose? How does it work? What are pros and cons?
**LoRa**: A long-range, low-power wireless communication technology.
**Purpose**: Designed for IoT applications to transmit small amounts of data over long distances.
**How it Works**: Uses chirp spread spectrum modulation to achieve long-range communication.
**Pros**:
- Low power consumption.
- Long communication range.
**Cons**:
- Low data throughput.
- Limited to small payload sizes.

---

### 13. What is pruning? How does it work? What is the main tradeoff?
**Pruning**: Reduces the size of a model by removing redundant parameters.
**How it Works**: Identifies low-importance weights and sets them to zero.
**Tradeoff**: Gains in speed and memory at the cost of slight accuracy degradation.

---

### 14. What is distillation? What is the principle? What are pros and cons?
**Distillation**: A technique to transfer knowledge from a large model (teacher) to a smaller model (student).
**Principle**: The student learns from the teacher’s softened outputs.
**Pros**:
- Smaller model size.
- Faster inference.
**Cons**:
- Requires a well-trained teacher model.
- Can lose accuracy.

---

### 15. What is model drift? What can cause it?
**Model Drift**: Degradation in model performance over time due to changes in data distribution or environment.
**Causes**:
- Concept drift (change in relationships between inputs and outputs).
- Data drift (change in input data distribution).

---

### 16. What are the different ways concept drift can manifest?
1. **Sudden Drift**: Abrupt change in data distribution.
2. **Gradual Drift**: Slow changes over time.
3. **Recurring Drift**: Periodic or cyclic changes.
4. **Incremental Drift**: Continuous, small changes.

---

### 17. What is concept drift?
**Concept Drift**: A change in the statistical relationship between input data and target output over time.

---

### 18. How to monitor drift?
- Use data distribution monitoring tools.
- Track performance metrics like accuracy over time.
- Implement statistical tests to detect changes in data distribution.

---

### 19. What is continual learning? Give a definition.
**Continual Learning**: The ability of a model to learn continuously from new data while retaining knowledge from previous tasks.

---

### 20. Can you explain what catastrophic forgetting is?
**Catastrophic Forgetting**: When a model loses knowledge of previous tasks while learning a new one.

---

### 21. What are the main strategies of continual learning? Can you explain them?
1. **Regularization-based**: Adds constraints to prevent forgetting (e.g., Elastic Weight Consolidation).
2. **Rehearsal-based**: Maintains a subset of previous data for training.
3. **Dynamic Architectures**: Expands the model as new tasks are learned.

---

### 22. What is full retraining?
**Full Retraining**: Training a model from scratch with all available data, including historical and new.

---

### 23. What are rehearsal methods?
**Rehearsal Methods**: Store and replay a subset of historical data during training to reduce forgetting.

---

### 24. What is dynamic architecture?
**Dynamic Architecture**: Adapts or expands the model architecture to accommodate new tasks.

---

### 25. What is the trick behind knowledge distillation?
**Trick**: The student model mimics the soft target probabilities of the teacher, capturing complex relationships.

---

### 26. What is parameter regularization?
**Parameter Regularization**: Adds penalties to the loss function to retain critical parameters for old tasks.

---

### 27. What are deploying strategies to ensure the safety and good functionality of the model?
1. Canary testing.
2. Shadow deployment.
3. A/B testing.
4. Blue-green deployment.
5. Continuous monitoring.

---

### 28. Can you explain what Ray is and how it works?
**Ray**: A distributed framework for parallel computing, ideal for ML workflows. It simplifies distributed execution by providing APIs for tasks and actors.

---

### 29. Explain canary testing.
**Canary Testing**: Deploying a new model to a small subset of users to evaluate performance before full rollout.

---

### 30. What is the replay method?
**Replay Method**: Stores past data or summaries and reuses it during training to mitigate forgetting.

---

### 31. Explain the steps of CRISP-DM
