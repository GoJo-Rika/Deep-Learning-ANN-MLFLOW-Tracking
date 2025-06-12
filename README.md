**Deep Learning with MLflow**
==========================

**Project Overview**
-------------------

This project demonstrates the use of MLflow for managing the end-to-end machine learning lifecycle on the Wine-Quality dataset using a Keras Sequential model. The focus of this project is on the MLflow workflow and how it can be used to track and manage machine learning experiments.

**MLflow Structure**
-------------------

This project follows the MLflow structure, which consists of the following components:

* **MLflow Tracking**: used for logging and tracking experiments, including hyperparameters, metrics, and artifacts.
* **MLflow Projects**: used for packaging and deploying models.
* **MLflow Models**: used for serving and managing models.

**MLflow Commands**
------------------

Here are some common MLflow commands used in this project:

* `mlflow set_experiment`: sets the experiment name.
* `mlflow start_run`: starts a new run.
* `mlflow log_params`: logs hyperparameters.
* `mlflow log_metric`: logs metrics.
* `mlflow log_model`: logs the model.
* `mlflow register_model`: registers the model in the model registry.

**MLflow Workflow**
------------------
The `getting-started.ipynb` notebook executes the following MLflow workflow:

1. Sets the experiment name and starts a new run.
2. Logs hyperparameters and metrics.
3. Trains the ANN model using Keras.
4. Logs the model and registers it in the model registry.

The MLflow workflow consists of the following steps:

1. **Set Tracking URI**: Set the tracking URI to store the experiment results.
    ```python
    mlflow.set_tracking_uri(uri="http://127.0.0.1:5000")
    ```
2. **Set Experiment**: Set the experiment name to organize the runs. 
    ```python
    mlflow.set_experiment("wine-quality")
    ```
3. **Start Run**: Start a new run to track the experiment.
    ```python
    with mlflow.start_run():
        # MLflow code here
    ```
4. **Log Parameters**: Log the hyperparameters used in the experiment.
    ```python
    mlflow.log_params({"learning_rate": 0.01, "batch_size": 32})
    ```
5. **Log Metric**: Log the metrics used to evaluate the experiment.
    ```python
    mlflow.log_metric("accuracy", 0.9)
    ```
6. **Set Tag**: Set a tag to categorize the experiment for better organization and searchability.
    ```python
    mlflow.set_tag("model", "keras-sequential")
    ```
7. **Infer Signature**: Model signature defines the input and output schema of your model.
    ```python
    signature = infer_signature(X_train, model.predict(X_train))
    ```
8. **Log Model**: Log the model using MLflow for loading and deployment.
    ```python
    mlflow.keras.log_model(model, "model", signature=signature)
    ```
9. **Register Model**: Model registry is used to manage and version models.
    ```python
    mlflow.register_model(model_uri, "wine-quality")
    ```

**MLflow in Deep Learning Model**
---------------------------------

In this project, we use MLflow to track and manage the deep learning model. We start using MLflow after defining the model architecture and before training the model. We use MLflow to log the hyperparameters, metrics, and model.

* **Model Definition**: After defining the model architecture, we use MLflow to log the hyperparameters.
* **Model Training**: During model training, we use MLflow to log the metrics.
* **Model Evaluation**: After model evaluation, we use MLflow to log the final

**Example Use Cases**
--------------------

* Use MLflow to track and compare experiments.
* Use MLflow to deploy and serve models.
* Use MLflow to manage and version models.