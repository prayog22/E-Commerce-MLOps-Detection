# E-commerce Recommendation System with MLOps

This project implements an e-commerce recommendation system using machine learning, integrated with MLOps practices for training, tracking, and serving the model. It leverages MLflow for experiment tracking and model serving, Terraform for infrastructure provisioning, and GitHub Actions for CI/CD automation.

## Project Overview

The goal of this project is to build and deploy a recommendation system that suggests products to users based on their ratings or interactions. The pipeline includes model training, deployment, and serving, all orchestrated with modern MLOps tools.

- **Model Training**: A recommendation model is trained using the `src/train.py` script, with MLflow for logging metrics, parameters, and artifacts.
- **Model Serving**: The trained model is served using `src/serve.py` with MLflow's built-in serving capabilities.
- **Infrastructure**: AWS resources (S3 for storage, EC2 for serving) are provisioned using Terraform.
- **CI/CD**: GitHub Actions automates the training and deployment process via the `train-deploy.yml` workflow.

## Directory Structure
ecomm-recommendation-mlops/

├── .github/                   
│   └── workflows/              
│       └── train-deploy.yml     training and deployment
├── infra/                      
│   ├── main.tf

│   └── variables.tf

├── src/

│   ├── train.py

│   └── serve.py

├── data/

│   └── user_ratings.csv

├── requirements.txt

├── README.md

└── .gitignore



## Prerequisites

To set up and run this project locally or deploy it, ensure you have the following installed:

- Python 3.8+
- Terraform (for infrastructure setup)
- AWS CLI (configured with credentials)
- Git
- (Optional) MLflow for local experimentation

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/<your-username>/ecomm-recommendation-mlops.git
   cd ecomm-recommendation-mlops


## 2. Install Dependencies:
```
pip install -r requirements.txt
```

## 3. Prepare Data:
* Place your dataset (e.g., user_ratings.csv) in the data/ directory.

* Note: The data/ directory is not tracked by Git (see .gitignore).

## 4. Train the Model Locally:
```
python src/train.py
```
## 5. Serve the Model Locally:
```
python src/serve.py
```
### Alternatively, use MLflow's serving command after training:
```
mlflow models serve -m runs:/<run-id>/model --port 5000
```
## 6. Set Up Infrastructure:
```
cd infra
terraform init
terraform apply
```
* Provide necessary variables (e.g., AWS credentials) in variables.tf or via a terraform.tfvars file.

## 7. CI/CD with GitHub Actions:
* Push changes to your repository.

* The .github/workflows/train-deploy.yml workflow will automatically trigger training and deployment on push to the main branch.

## Usage
* Training: Run src/train.py to train the model with your dataset.
* Serving: Use src/serve.py or MLflow to serve predictions via an API endpoint.
* Deployment: Infrastructure is managed via Terraform, and the CI/CD pipeline deploys the model to an EC2 instance.

## Notes 
* Ensure your AWS credentials are configured for Terraform and MLflow to interact with S3.
* The sample dataset (user_ratings.csv) is not included; replace it with your own data.
* Customize the recommendation algorithm in src/train.py as needed.
