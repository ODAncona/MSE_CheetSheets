## MLOps readiness level

Microsoft defines 5 levels of MLOps maturity:

0: No MLOps => Manual builds, trainings and testing, no centralized tracking of model performance
1: DevOps but no MLOps => Automated builds and tests, but still manual training, testing and tracking
2: Automated training => Automated model training, centralized tracking of model performance, model
management, easy to reproduce models, manual but low friction releases
3: Automated model deployment => Integrated A/B testing, full traceability from deployment to original data, low friction
releases
4: Full MOPs automated operations => Automated model training and testing, verbose centralized metrics for deployed model,
full system is automated, production systems help to improve models

## Parts of MLOps system

- Data storage/Versioning
- Model training/Experiments
- Serving models in production


## Infrastructure types

- Cloud Based
- On-premise servers
- Edge computing
- Mix

## Metrics for MLOps system

Advantages(+) and disadvantages(-) encompasses:

- Cost
- Privacy
- Scalability
- Technological complexity
- Latency (time to response)
- Throughput (requests per second)
- Bandwidth (Input and output data size)

## Cloud Infrastructure

MLOps application can be deployed into a
public cloud such as GPC, AWS, Azure, etc...

(+)
- Reduced technological complexity
- "Infinite" scaling
- Low initial costs

(-)

## On premise Infrastructure

Reproduce a production environnement locally.

(+)
For privacy or cost reasons
We control the dataflow

(-)
requires in-house knowhow and hardware
scaling become difficult

## Edge Infrastructure

Edge devices are usually specialized hardware (IoT, Mobile devices, FPGA, Jetson, Webbrowser)

(-)
smaller models

## Cloud Technologies

- Dedicated servers/services (microservice or similar)
- Serverless architectures (Lambdas functions)
- Batch processing (Kubernetes tasks, CI/CD Runners, Ray etc.)
- Stream processing (Kafka etc.)

## Dedicated Server

Those can be
- Actual physical machines
- Virtual machines
- Containers

We have reserved resources for our model in advance => It is always available with no waiting time.

(-)
Scaling is not optimal.
expensive in a low usage environment.

## Serverless Architecture

Serverless functions are essentially docker containers started on demand. Serverless systems, like amazon lambda, allow you to execute specific code without a dedicated server.

(+)
You are billed per usage/call
(-)
Model need to be loaded into memory, for a cold start
Cold Start problem

## Batch Processing

When reactivity is not important, it is sometimes interesting to process ML workloads in batches. Frameworks like Ray or Kubernetes Tasks allow you to do this.
You define a "task" who will be executed when resources are available. The results are stored on different systems. A group of multi-purpose worker nodes share the workload.

## Model Deployment

When deploying a model, we want to do so using the least amount of resources necessary. Therefore, we can use optimization for this. Such as :

- Quantization
- LoRa
- Prunning
- Distillation
- Model Compilation

## Quantization

Quantization is when you reduce the weight of a DeepLearning Model. To get a quantized model, two approaches are possible:
1) Post-Training Quantization (PTQ) => The model is quantized after being trained
2) Quantization-Aware Training (QAT)=> Train the model with fake quantization to minimize accuracy loss

PTQ is a good approach for simple models and if you can accept some accuracy loss, it is easy to put in place
QAT is more complex and costly, but will give you the best results in terms of accuracy

## LoRa
Low-rank adaptation is a technique where we create a companion model, which influences how the original model works.

(+)
Require significantly less resources
(-)
LoRAs do have a reduced accuracy compared to a full fine-tune

## Prunning

Most models do not need all the weights and connections to work well. With prunning we simplify the original model, while keeping ist accuracy mostly intact.

(-)
There is a trade-off with accuracy

## Distillation

Model distillation allows you to take a large model and reduce its size. The idea is to train a small model (student), based on the outputs of a  large model (teacher model). In normal training, we calculate the loss by comparing the predictions with the groundthruth. During distillation, we train on the predictions of the teacher model, not the groundthruth.

(+)
The results are often much better than training the small model with only the training data.

## Model compilation

Specific compilers and runtime environments exist to execute models faster than standard frameworks.
=> yolo
=> pytorch

## Model Drift

Model drift occurs when a model's performance, which was initially measured on a test set, degrades in production over time due to changes in the concept being modeled, shifts in data distribution (including data quality), or the dynamic nature of the real world, making continuous monitoring essential. There are different types of drift:

Concept Drift: A change in the relationship between inputs and outputs p(Y|X).
Prediction Drift: a change in the distribution of the predicted label p(ŷ|X), meaning that there was a change in the relationship between the input of the model and the model’s prediction.
Feature Drift: A change in the input feature distribution p(X).
Label Drift: A change in the distribution of target labels p(Y).

## Concept Drift

Concept drift occurs when the relationship between input features and target outputs (p(Y|X)) changes over time. This means the underlying pattern the model learned during training is no longer valid in production. For example, a fraud detection model might struggle if fraud patterns evolve, leading to degraded performance as the model's learned boundaries no longer align with reality.

When searching for concept drift we view our data as a stream and proceed to examine how the evaluation metrics fluctuate over time.

If the input distribution p(X) changes but the true labels p(Y|X) don’t, we can classify it as a virtual drift, and conclude that we have a change in the input data that hasn’t affected the performance yet. If there is an actual change in the labels, i.e. p(Y|X) changed, that means that a real drift occurred during the time frame and we are detecting its effects.

## Data drift

Data drift, also known as feature drift, happens when the statistical distribution of the input features (p(X)) changes over time. This does not necessarily affect the model's performance immediately but can signal potential issues. For instance, a weather prediction model trained on historical temperature data might face data drift if global temperatures start to shift due to climate change.

## Feature drift

Feature drift is a specific type of data drift where one or more input features (X) have a change in their distribution. For example, in a housing price prediction model, if the average size of listed homes increases over time, the model may encounter feature drift. While the target variable relationship (p(Y|X)) might still hold initially, continuous drift can cause misalignment with the original training data.

## Label Drift

Label drift occurs when the distribution of the target variable (p(Y)) changes over time. This can happen independently of the input data distribution or concept changes. For example, in a sentiment analysis model, if a dataset shifts from balanced positive and negative reviews to predominantly negative ones, the model might misrepresent performance metrics due to the change in label proportions.

## Data Drift Monitoring

1) If for some reason we know the true label after a prediction, we can track the accuracy metrics of the model over time
2) Otherwise, we need to monitor the data drift

Basic tracking of data drift can be achieved easily with individual input/ output values:
- Track ratio of categorical values
- Track distribution of numerical values
- Classic statistical tests can be used (Fisher, Chi-squared etc.)

It has been shown that regularly retraining the model before the point of significant degradation has occurred helps alleviate the issue to some extent, but in many cases, it is simply not enough and in others may even make matters worse. Sometimes it’s hard to identify the point of the models’ significant degradation. We don’t always know the timeframe after which we need to retrain: a week may be too late, but hourly may cost too much to maintain. In many cases, the time window for retraining is in flux and so this parameter itself needs to be monitored and optimized. In many cases, retraining simply isn’t enough. A significant change in the concept may require an entirely new type of model. In some cases, the change originates from flaws in other parts of the pipeline such as schema changes, dropped fields, application bugs, and more. In such cases, retraining a model with flawed data may have no effect or possibly even exacerbate the problem.

The best way to avoid concept drift ruining your models is by staying on top of it with the help of monitoring tools.

## Complex data drift

For tabular data, detecting distribution drifts is relatively easy. Complex data, such as images, text or graphs require another strategy such as tracking embedding vectors.

## Monitoring

What to monitor ?
- SLA (Service Level Agreement)
- Uptime
- Performance
- Time to answer / Latency
- Number of requests
- Resources (GPU, CPU, Memory, I/O)
- Distributions
- Model/data drift
- Data quality
- Missing values, invalid values and outliers
- Model
- Accuracy
- Prediction confidence
- Model training
- Accuracy, etc.
- Other
- Costs (API, hosting)

## Continual Learning
Continuous learning allows us to regularly update in production. Various strategies exist to define which data will be used to train a new model. They can be stateless or statefull. Stateless training takes all data since a certain point in time. Stateful training finetunes a base model on a subset (usually most recent) of the data.

### Full Retraining
Full retraining involves completely re-training the model using both old and new datasets. While this method can restore performance and mitigate the effects of concept drift, it is computationally and memory-intensive, making it impractical for large datasets. It is best suited for smaller datasets where the cost of retraining remains manageable.

### Rehearsal Methods
Rehearsal methods use a representative sample of the old data alongside new data during training to mitigate catastrophic forgetting. By balancing historical knowledge with new learning, these methods provide an efficient approach to adapting the model without requiring a full retraining process, especially in dynamic environments.

### Dynamic Architecture
Dynamic architectures involve allowing the network topology to evolve as new data is introduced. This approach aims to incorporate new information without destroying existing knowledge. However, its complexity and the difficulty of implementing such evolving architectures often make it impractical in most real-world scenarios.

### Knowledge Distillation
Knowledge distillation uses a fixed teacher model to guide the training of a learner model with new data. The teacher retains the knowledge from the original dataset, and the learner is trained to adapt to new information. While effective in some cases, this method may not fully address the challenge of concept drift if the teacher model itself becomes outdated.

### Parameter Regularization
Parameter regularization aims to protect specific weights in the model to prevent them from being overwritten during training on new data. While promising in theory, the exact mechanisms of this approach can be complex and are not always intuitive. Advanced techniques are employed to identify and preserve critical parameters, ensuring the model retains past knowledge while integrating new information.

## Deployment strategies

Few strategies to deploy the model in a safe manner:

Shadow deployment => Deploy your model in parallel with the existing and compare their output
A/B testing => Serve the new model to a certain percentage of users and compare the results
Canary testing => Similar to A/B testing, but increase percentage of users over time if satisfactory
Interleaving experiments => Useful for ranking systems. Combine output of old and new model
