### 1. What are the 5 levels of MLOps Readiness Level? Explain each of them

1. **Level 0: No MLOps** Processes are entirely manual, with no centralized tracking or automation.  
2. **Level 1: DevOps but no MLOps** Automation is limited to application builds and tests, while model training and tracking remain manual.  
3. **Level 2: Automated training** Model training is automated and traceable, with centralized tracking and version management.  
4. **Level 3: Automated model deployment** Deployments are automated with full traceability and integrated tests to evaluate models in production.  
5. **Level 4: Full MOPs automated operations** Operations are fully automated, with data pipelines, automatic retraining, and seamless collaboration between teams.

---

### 2. What are the parts/components of an MLOps system?

- **Data storage and versioning:** Tools, processes, multiple versions, datasets  
- **Model training and experiment tracking:** Environment, reproducibility, automation  
- **Model deployment in production:** Production-ready, infrastructure, batch/stream processing  
- **Monitoring:** Metrics, drift detection, dashboards  
- **Continuous learning:** Updates, evolving data, retraining strategies  
- **Integration and collaboration:** Teamwork, communication, cross-functional  
- **Automation:** Efficiency, repetitive tasks, pipelines  
- **Infrastructure:** Cloud, on-premises, edge, scalability  
- **Technology:** Serverless, batch, low-latency, deployment methods  
- **Model optimization:** Quantization, pruning, distillation, performance  
- **Risk management:** Evaluation, mitigation, reliability  
- **Business analysis:** Metrics impact, ROI, stakeholder communication  

---

### 3. Can you name at least 5 metrics relevant to evaluate an MLOps system?

- **Latency (response time):** Real-time, low delay, critical for fast responses  
- **Throughput (requests per second):** High volume, data processing, performance  
- **Resource utilization (GPU, CPU, memory, I/O):** Bottlenecks, optimization, hardware monitoring  
- **Model and data drift:** Degradation, distribution changes, reliability  
- **Data quality:** Missing values, outliers, invalid data, impact on performance  
- **Service Level Agreement (SLA):** Availability, uptime, operational efficiency  
- **Model accuracy:** Precision, recall, F1 score, regression errors (MAE, MSE)  
- **Prediction confidence:** Certainty, reliability, output confidence scores  
- **Costs:** Infrastructure, API usage, hosting expenses

---

### 4. What are the Advantages/Inconveniences of deploying a model to the cloud?

**Advantages (+):**  

- **Reduction of technological complexity:** Cloud providers handle infrastructure, simplifying deployment and maintenance.  
- **"Infinite" scalability:** Cloud platforms adapt resources to application needs, managing variable workloads effectively.  
- **Low initial costs:** Pay-as-you-go models eliminate the need for physical infrastructure investment.  
- **Specific MLOps services:** Cloud platforms offer tailored tools for training, deploying, and monitoring models.  
- **Standard model APIs:** Prebuilt APIs for tasks like object detection or LLMs reduce the need for self-hosting models.  

**Inconveniences (-):**  

- **Cost:** Usage costs can increase significantly with heavy resource consumption, requiring careful monitoring.  
- **Privacy:** Sensitive data, such as medical records, may require additional security measures to ensure confidentiality.  
- **Infrastructure complexity:** Choosing the right cloud technologies and architectures (e.g., serverless, dedicated servers) can be challenging.  
- **Vendor lock-in:** Dependence on specific platforms can make migration to another provider difficult.  

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

1. **Dedicated Servers:** Services run on pre-reserved resources (physical or virtual) with guaranteed availability and low latency but inefficient scaling for low request volumes.  
2. **Serverless Systems:** Functions execute on demand without dedicated infrastructure, offering cost efficiency for low usage but with cold start delays and size limitations.  
3. **Batch Processing:** Workloads are processed in bulk when resources are available, suitable for non-urgent tasks like data analysis or model training.  
4. **Stream Processing:** Continuous data streams are processed in real-time using frameworks like Kafka, ideal for handling frequent, non-interactive data flows.  

---

### 7. What are the pro/cons of a Dedicated Server to deploy a service?

Advantages (+):

- **Immediate availability**: Pre-reserved resources ensure the service is always available with low latency, ideal for real-time applications.
- **Guaranteed resources**: Stability and performance as resources are exclusively allocated to the service.

Inconveniences (-):

- **Step scaling**: Resources scale in fixed steps (e.g., 1, 2, 3 servers), leading to inefficiency during low workloads.
- **Potentially high cost**: Reserved resources can be expensive in low-usage environments, as they remain underutilized.
- **Maintenance overhead**: Requires manual management, updates, and monitoring, increasing operational complexity.
- **Risk of underutilization**: Resources may not be fully utilized, leading to wasted capacity and costs.

---

### 8. What are the Advantages/Inconveniences of deploying a model on serverless infrastructure?

Advantages (+):

- **Cost-efficient for low usage**: Pay-per-use model minimizes expenses during low or variable workloads.
- **No server management**: Simplifies operations as the cloud provider handles the infrastructure.
- **Automatic scalability**: Dynamically adjusts resources to meet demand without manual intervention.

Inconveniences (-):

- **Model size limitations**: Constraints on memory and model size can restrict deployment of large models like LLMs.
- **Cold start latency**: Initial function calls can experience higher latency due to model loading.
- **Limited real-time responsiveness**: May not suit applications needing immediate response times.
- **Reduced control**: Delegates infrastructure management, limiting custom configurations.
- **Debugging complexity**: Abstracted infrastructure can make debugging more challenging.

Summary:
Serverless deployment is ideal for variable workloads and low-utilization scenarios, but limitations in control, latency, and model size make it less suitable for large-scale or real-time applications.

---

### 9. Can you name five different optimization techniques to deploy a model in production?

### Techniques for Model Optimization in Production  

1. **Quantization:** Reduced precision, int8, memory efficiency, faster inference, PTQ/QAT  
2. **Pruning:** Model simplification, weight removal, smaller size, faster execution  
3. **Distillation:** Teacher-student models, smaller model, preserved accuracy, imitation learning  
4. **Model Compilation:** Optimized execution, fused kernels, faster runtime, torch.compile  
5. **Low-Rank Adaptation (LoRA):** Companion model, resource efficiency, modular adaptation, case-specific usage  

---

### 10. What are the two different types of quantization? Which one is the most performant in what case?

**Post-Training Quantization (PTQ)**: Quantifies a pre-trained model by reducing precision (e.g., from float32 to int8) without retraining, enabling memory and computation efficiency with potential accuracy trade-offs.

Advantages (+):

- **Simplicity**: Easy to implement on pre-trained models.
- **Speed**: Quick to apply with minimal effort using tools like TensorFlow or PyTorch.

Inconveniences (-):

- **Accuracy loss**: Can degrade model precision, especially for lower-bit quantization (e.g., int4).

**Quantization-Aware Training (QAT)**: Simulates quantization during model training, allowing the model to adapt to lower precision, providing higher accuracy but requiring more resources.

Advantages (+):

- **Better accuracy**: Minimizes accuracy loss by adapting the model during training.
- **Robustness**: Improves the model's performance under quantized conditions.

Inconveniences (-):

- **Complexity**: Requires modifications to the training process.
- **Time and resources**: Longer training times and higher computational costs.

---

### 11. What is LoRa? What is its purpose? How does it work? What are pros and cons?

LoRA enables resource-efficient fine-tuning of large models by introducing a small, low-rank companion model that modifies the behavior of the main model without altering its core parameters.

**How it works**

1) Low-Rank Companion Model: Adds a low-rank matrix to targeted layers of the main model, which stores trainable parameters for fine-tuning.
2) Selective Fine-Tuning: Only updates the parameters in the low-rank matrix during fine-tuning, leaving the original model weights unchanged.
3) Influence on Main Model: Adjustments in the low-rank matrix affect the main model’s output without direct weight modification.
4) Flexibility: Multiple LoRAs can be created for different tasks or clients, swapping them in and out while keeping the main model fixed in memory.

Advantages (+):

-**Resource efficiency**: Reduces memory and computational requirements compared to full fine-tuning.
-**Faster training**: Fine-tuning the low-rank parameters is quicker.
-**Flexibility**: Enables swapping LoRAs for various use cases without reloading the main model.
-**Model integrity**: Keeps the main model unchanged, preserving its performance on other tasks.
-**Reusability**: The main model can be reused easily for other tasks with different LoRAs.

Inconveniences (-):

- **Slight accuracy reduction**: LoRA may yield lower precision than full fine-tuning.
- **Complexity**: Involves managing two models (main and companion).
- **Implementation-specific**: Requires tailored modifications to training pipelines and models.
- **Target layer selection**: Identifying the appropriate layers for low-rank adjustments can affect results

---

### 12. What is pruning? How does it work? What is the main tradeoff?

**Pruning**: A model optimization technique that removes non-essential weights or connections to simplify a model, reduce its size, and improve execution speed while maintaining acceptable accuracy.
**How it Works**:

1) Identifying non-essential elements: Weights or connections with low contribution (e.g., small absolute values or low impact) are identified.
2) Removing elements: These non-essential elements are removed, resulting in a smaller, less complex model.
3) Iterative tuning: The pruning process is often adjusted iteratively to balance model size reduction with accuracy preservation.
4) Integration with other techniques: Pruning is frequently combined with quantization or other methods to maximize optimization.

Advantages (+):

- **Model size reduction**: Less memory is required for storage, making deployment on resource-constrained devices easier.
- **Faster execution**: Fewer computations reduce inference time, beneficial for real-time applications.
- **Energy efficiency**: Reduced computations lead to lower energy consumption, ideal for battery-powered devices.
- **Simplified models**: A smaller model is often easier to interpret.

Inconveniences (-):

- **Accuracy loss**: Removing weights can degrade the model’s predictive performance.
- **Fine-tuning required**: Careful parameter tuning is necessary to maintain accuracy.
- **Architecture dependence**: The effectiveness of pruning varies by model architecture.
- **Iterative process**: Finding the right balance between size and accuracy can be time-consuming.

---

### 13. What is distillation? What is the principle? What are pros and cons?

Model distillation is an optimization technique where a smaller, faster "student" model is trained to replicate the predictions of a larger, more complex "teacher" model, transferring knowledge efficiently.

**How it Works**:

1) Teacher-student relationship: A large, accurate model (teacher) is used to train a smaller model (student) by transferring knowledge.
2) Training method: Instead of using ground truth labels, the student learns to mimic the teacher’s predictions, often working with probability distributions rather than simple outputs.
3) Rich information transfer: The student model benefits from the teacher's nuanced predictions (e.g., probability vectors) rather than binary or categorical labels.
4) Optimized performance: The student becomes more efficient, achieving better accuracy than direct training on the data.

Advantages (+):

- **Model size reduction**: Results in smaller models requiring less memory for storage and execution.
- **Faster execution**: Smaller models provide faster inference times, suitable for real-time applications.
- **Energy efficiency**: Reduced computational complexity saves energy, ideal for mobile and embedded devices.
- **Improved performance over direct training**: The student learns from a richer information source, improving its accuracy.
- **Edge deployment**: Compact models are well-suited for deployment in resource-constrained environments.

Inconveniences (-):

- **Requires a teacher model**: A high-quality teacher model must already exist, which can be resource-intensive to create.
- **Process complexity**: Managing and training both teacher and student models adds complexity.
- **Hyperparameter tuning**: Requires careful adjustments to maximize the student’s performance, which can be time-consuming.
- **Dependence on teacher quality**: A suboptimal teacher will limit the student’s performance.
- **Potential loss of precision**: While the student performs well, it may not match the teacher's precision in some cases.

---

### 14. What is model drift? What can cause it?

**Model Drift:** A phenomenon where the performance of a machine learning model deteriorates over time due to changes in the underlying data distribution or the concept it is modeling, necessitating monitoring and updates to maintain reliability.

**Causes**:

- **Concept drift (change in relationships between inputs and outputs)** : evolving target relationships, real-world changes, economic trends, demographic shifts, sudden/gradual/incremental/recurrent changes, p(Y|X) changes
- **Data drift (change in input data distribution)** : Feature or Label drift
- **Feature Drift**: Input distribution changes, population shifts, new user categories, regional variations, p(X) changes
- **Label Drift**: Output distribution changes, seasonal variations, p(Y) changes

---

### 15. What are the different ways concept drift can manifest?

1. **Sudden Drift**: Abrupt change in data distribution.
2. **Gradual Drift**: Slow changes over time.
3. **Incremental Drift**: Continuous, small changes.
4. **Recurring Drift**: Periodic or cyclic changes.

---

### 16. What is concept drift?

**Concept Drift**: A change in the statistical relationship between input data and target output over time.

---

### 17. How to monitor drift?

### Methods for Monitoring Model Drift  

- **Performance Metrics Monitoring:** Track performance metrics (e.g., accuracy, precision, recall) over time to detect model decay when true labels are available.  
- **Data Distribution Monitoring:** Analyze changes in input/output data distributions using statistical tests, categorical ratios, or numerical value distributions.  
- **Monitoring Tools and Libraries:** Use tools like **Alibi-detect**, **Evidently.AI**, or **Weights&Biases** for automated drift detection and monitoring.  
- **Streaming Data Analysis:** Evaluate metrics periodically in a data stream to identify virtual or real drift and distinguish between sudden, gradual, or recurrent changes.  
- **Alert Systems and Feedback Loops:** Implement alerts to notify of anomalies and integrate user feedback for model improvements.  

---

### 18. What is continual learning? Give a definition

**Continual Learning**: A dynamic approach aimed at regularly updating machine learning models in production to adapt to evolving data distributions and maintain optimal performance over time. It addresses challenges such as model drift, concept changes, and insufficient initial training data, ensuring models remain relevant and effective in changing environments without the need for complete retraining.

---

### 19. Can you explain what catastrophic forgetting is?

**Catastrophic Forgetting**: is a phenomenon in machine learning where a model loses its ability to recall previously learned knowledge when it is trained on new data. This occurs because the process of updating the model's parameters to accommodate new information overwrites the existing knowledge, leading to a significant degradation in performance on earlier tasks. It is a common challenge in continual learning scenarios where models must adapt to changing data distributions without forgetting past tasks or information.

---

### 20. What are the main strategies of continual learning? Can you explain them?

- **Stateless Training**: A strategy where a new model is trained from scratch using all available data since a specific point, offering comprehensive updates but at high computational costs.  
- **Stateful Training**: Involves fine-tuning a pre-trained model on a subset of recent data, enabling quick updates with fewer resources but limiting the ability to accommodate significant changes.
- **Combined Approaches**: Periodically trains a robust base model while frequently fine-tuning it with new data, balancing thorough updates and adaptability.  
- **Transfer Learning**: Reuses knowledge from a pre-trained model for a new task, allowing efficient adaptation to new contexts while retaining prior expertise.  
- **Low-Rank Adaptation (LoRA)**: Uses lightweight companion models to influence a primary model, enabling fast, resource-efficient updates and flexibility for various use cases.  
- **Continuous Monitoring**: Monitors model performance and data distributions to detect drift and trigger updates as needed, ensuring sustained reliability and relevance.  

---

### 21. What is full retraining?

**Full Retraining**: Training a model from scratch with all available data, including historical and new.

---

### 22. What are rehearsal methods?

**Rehearsal Methods**: Store and replay a subset of historical data during training to reduce forgetting.

**Replay Method**: Replay is a strategy used in machine learning, especially in continual learning, to prevent catastrophic forgetting. It involves replaying past data to help the model retain previously learned information while adapting to new data.

- **Memory of Real Samples:** Stores actual data samples from previous tasks and reuses them during training to prevent forgetting, but requires significant storage resources.  
- **Generative Replay:** Synthesizes past data using a generative model, avoiding storage issues, but can struggle to produce realistic data for complex tasks.  

---

### 23. What is the trick behind knowledge distillation?

**Trick**: The student model mimics the soft target probabilities of the teacher, capturing complex relationships.

**Model distillation:** A technique that trains a smaller, faster student model to replicate the behavior of a larger, more complex teacher model by learning from the teacher's probabilistic predictions, enabling resource-efficient deployment without significantly sacrificing performance.

---

### 24. What is parameter regularization?

**Parameter Regularization:** A technique that improves a model's generalization by adding penalties to the loss function during training, encouraging simpler weight configurations to prevent overfitting and, in the context of continual learning, mitigating catastrophic forgetting.  

---

### 25. What are deploying strategies to ensure the safety and good functionality of the model?

- **Shadow Deployment**: Deploys the new model in parallel with the existing one without exposing it to users, allowing validation and anomaly detection without risk to end-users.  
- **A/B Testing**: Serves the new model to a limited percentage of users and compares its performance to the existing model, enabling evaluation of real-world impact before full deployment.  
- **Canary Testing (Progressive Deployment)**: Gradually increases the percentage of users exposed to the new model over time, minimizing risks and allowing early detection of issues before wider deployment.  
- **Interleaving Experiments**: Combines outputs from old and new models, typically in ranking systems, to subtly and effectively compare their effectiveness in controlled environments.  
- **Continuous Monitoring**: Tracks model performance and data quality metrics in production to detect issues such as model or data drift, ensuring reliability and timely updates.  
- **Automatic Model Retraining**: Uses monitoring results to trigger automatic retraining of models to adapt to new data and maintain performance over time.  
- **Test Integration**: Implements unit and integration tests for model code and deployment processes, helping to identify potential issues before affecting production systems.  

---

### 27. Can you explain what Ray is and how it works?

**Ray**: Ray is a framework for parallel data processing, used primarily for batch processing tasks in machine learning workflows, enabling efficient resource utilization and scalability.  

## How It Works  

1. **Batch Processing:** Ray executes tasks in groups (batches) when resources are available, contrasting with real-time systems that process data as it arrives.  
2. **Flexibility:** Allows users to define tasks that are executed when resources are free, distributing workloads across a pool of worker nodes.  
3. **Parallelization:** Ray parallelizes computations across multiple nodes, accelerating processes by distributing tasks effectively.  
4. **Use Cases:** Tasks like daily data analysis or model training can be scheduled, with results stored in a database or other systems for later use.  
5. **MLOps Integration:** Ray supports automation in MLOps, particularly for model training and data preprocessing, where immediate responsiveness is not required.  
6. **Scalable Architecture:** Tasks are defined, distributed to a cluster of machines, and results are retrieved upon completion, enabling robust scalability.  

---

### 28. Explain canary testing

**Canary Testing**:  A strategy for releasing a new model version incrementally, deploying to a small subset of users to evaluate performance before full rollout.

---

### 30. Explain the steps of CRISP-DM

# CRISP-DM Steps  

- **Business Understanding**: Align project goals with business objectives.  -> Objectives, success criteria, business problem, requirements.  
- **Data Understanding**: Explore and assess the data to ensure relevance.  -> Explore, patterns, anomalies, data quality, visualization.  
- **Data Preparation**: Clean and transform data for modeling.  -> Cleaning, missing values, feature engineering, data splitting.  
- **Modeling**: Develop and validate predictive models.  -> Train, techniques, hyperparameters, validation, algorithms.  
- **Evaluation**: Ensure models meet both business and technical goals.  -> Metrics, validation, comparison, risks, performance.  
- **Deployment**: Integrate the model into production workflows.  -> Deploy, monitor, feedback, integration, maintenance.  
