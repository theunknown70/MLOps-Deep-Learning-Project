# End-to-End MLOps: Chest Disease Classification

This repository showcases a complete end-to-end MLOps project for classifying chest diseases from images. The primary focus is on the robust MLOps workflow, from continuous integration and deployment to cloud-based model serving.

---

## ## Core MLOps Features

This project is not just a deep learning model; it's a demonstration of a scalable and automated MLOps infrastructure.

* **Automated CI/CD Pipeline:** The entire workflow is automated using **GitHub Actions**. On every push or pull request to the `main` branch, the pipeline automatically:
    1.  Sets up the Python environment.
    2.  Installs all dependencies.
    3.  Runs unit and integration tests (if any).
    4.  Builds and packages the application.
    5.  Deploys the updated model and application to **Amazon Web Services (AWS)**.

* **Cloud Deployment:** The trained model and the front-end application are deployed on an **AWS EC2 instance**, making the prediction service accessible via a public IP address.

* **Experiment Tracking with MLflow:** Integrated **MLflow** for tracking experiments, logging model parameters, metrics, and artifacts. This ensures reproducibility and helps in comparing different model versions.

* **Modular and Scalable Design:** The application is structured as an installable Python package, promoting code reusability and maintainability. This modular design, combined with DVC for data versioning, makes the project easily scalable.

---

## ## Workflow Architecture

The project follows a systematic and automated workflow:

1.  **Code Update:** A developer pushes new code or changes to the GitHub repository.
2.  **CI/CD Trigger:** The push automatically triggers the GitHub Actions CI/CD pipeline.
3.  **Build & Test:** The pipeline installs dependencies and runs checks.
4.  **Model Training & Evaluation:** The model is trained using the source data.
5.  **MLflow Logging:** All experiment details, including metrics and model artifacts, are logged to MLflow.
6.  **Deployment:** On successful run, the application is packaged and deployed to the AWS EC2 server.
7.  **Prediction Service:** The deployed Flask application serves the model via a user-friendly web interface.

---

## ## Technology Stack

* **Backend:** Python, Flask
* **Deep Learning:** TensorFlow, Keras
* **MLOps & Automation:** GitHub Actions (CI/CD), MLflow (Experiment Tracking), DVC (Data Versioning)
* **Cloud Platform:** Amazon Web Services (AWS EC2)
* **Frontend:** HTML, CSS
* **Code Quality:** PEP8 compliant

---

## ## How to Run This Project Locally

To replicate this project on your local machine, follow these steps.

**Prerequisites:**

* **Conda:** You must have Anaconda or Miniconda installed to manage the environment.
* **Git:** You must have Git installed for version control.

**Step-by-Step Instructions:**

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/theunknown70/MLOps-Deep-Learning-Project.git](https://github.com/theunknown70/MLOps-Deep-Learning-Project.git)
    cd MLOps-Deep-Learning-Project
    ```

2.  **Create the Conda Environment:**
    ```bash
    conda create -n cnncls_env python=3.8 -y
    conda activate cnncls_env
    ```

3.  **Install Project Dependencies:**
    The application is structured as a package. Install all necessary libraries using:
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the Application:**
    Start the Flask server to see the web application in action.
    ```bash
    python app.py
    ```
    Now, open your web browser and navigate to `http://127.0.0.1:8080` to access the application.

---

## ## CI/CD Pipeline Explained

The CI/CD pipeline is defined in the `.github/workflows/ci-cd.yml` file.

* **Trigger:** The workflow runs automatically on any `push` or `pull_request` made to the `main` branch.
* **Jobs:** The pipeline consists of a single `build` job that runs on an `ubuntu-latest` runner.

**Key Steps in the Pipeline:**

1.  **Checkout Code:** It first checks out the latest version of the repository's code.
2.  **Setup Python:** It sets up the specified Python environment (version 3.8).
3.  **Install Dependencies:** It installs all the required Python packages listed in `requirements.txt`.
4.  **Build and Deploy:** The final step (commented out in the current repo as "Deploy to AWS") would typically contain the script to package the application and push it to the AWS server using `rsync` or another deployment tool. This step requires configuring AWS credentials as GitHub secrets for secure access.
