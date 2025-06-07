# MLflow Workflow Example: Tracking, Logging, and Inference

This project serves as a practical guide to understanding and implementing a core MLflow workflow. It demonstrates how to leverage MLflow for managing your machine learning experiments, from model training and logging to deployment for inference, all while providing excellent traceability and reproducibility.

---

## What You'll Explore

This example meticulously covers the following essential stages of an MLflow-driven machine learning project:

* **Installing MLflow:** Setting up your environment to integrate MLflow's powerful capabilities.
* **Starting a Local MLflow Tracking Server:** Launching the central hub that stores all your experiment's metadata and artifacts.
* **Logging and Registering a Model with MLflow:** Demonstrating how to automatically capture model details, metrics, and parameters, and officially register your model for version control.
* **Loading a Logged Model for Inference using MLflow's `pyfunc` Flavor:** Retrieving a saved model and using MLflow's generic `pyfunc` interface to make new predictions.
* **Viewing the Experiment Results in the MLflow UI:** Navigating MLflow's intuitive web interface to visualize, compare, and manage your machine learning runs and registered models.

---

## How to Run This Example

Follow these simple steps to get this MLflow example up and running on your local machine:

1.  **Clone the Repository (if applicable):**
    If this content is part of a repository, first clone it:
    ```bash
    git clone <your-repository-url>
    cd <your-repository-directory>
    ```

2.  **Install MLflow:**
    Ensure you have MLflow installed in your Python environment.
    ```bash
    pip install mlflow scikit-learn
    ```

3.  **Start the MLflow Tracking Server:**
    Open your terminal and run the following command. This will launch the MLflow UI and set up the backend store for your experiment data.
    ```bash
    mlflow server --backend-store-uri sqlite:///mlflow.db --default-artifact-root ./mlruns --host 127.0.0.1 --port 5000
    ```
    * The `--backend-store-uri` specifies a local SQLite database (`mlflow.db`) to store run metadata (parameters, metrics, run IDs).
    * The `--default-artifact-root` points to `./mlruns`, a directory where model artifacts and other files will be saved.
    * The `--host` and `--port` define where the MLflow UI will be accessible.

4.  **Run the MLflow Python Script:**
    Save the Python code for logging and loading the model (provided in the sections below) into a file, for example, `mlflow_example.py`. Then, execute it from a **new terminal window** (keep the MLflow server running in the first one):
    ```bash
    python mlflow_example.py
    OR
    You can use Jupyter Notebook for .ipynb file execution
    ```
![image](https://github.com/user-attachments/assets/efcc1cc2-f8b9-4b41-ad24-0ba7d674d1eb)

    This script will train a model, log its details to MLflow, and then demonstrate how to load it back for inference.

5.  **Access the MLflow UI:**
    Open your web browser and navigate to the address specified when you started the server:
    ```
    [http://127.0.0.1:5000](http://127.0.0.1:5000)
    ```
    ![image](https://github.com/user-attachments/assets/8a51dcb4-11bc-4abe-8d24-148d8f2b6537)
    
    ![image](https://github.com/user-attachments/assets/e8cec496-8e88-4ed7-b671-e2bd0d3be98b)


    Here, you can visually explore all your experiment runs, compare results, and manage your registered models.

---

## Detailed Workflow Breakdown

### 1. Installing MLflow

The very first step for any MLflow project is to set up the library in your Python environment. This simple command ensures you have access to all of MLflow's powerful functionalities, from tracking experiments to managing models.

```bash
pip install mlflow

```


![image](https://github.com/user-attachments/assets/2252717c-612f-456f-b781-5a51a95e278e)

![image](https://github.com/user-attachments/assets/4195e77a-31f5-423a-b6d6-1ccdd4ed939e)






Also, 

In this we will have:

1. Run a hyperparameter sweep on a training script
2. Compare the results of the runs in the Mflow UI
3. Choose the best run and register it as a Model
4. Deploy the model to a REST API
5. Build a container image suitable for deployment to a cloud platform
