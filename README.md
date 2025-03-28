ecomm-recommendation-mlops/
├── .github/
│   └── workflows/
│       └── train-deploy.yml       # GitHub Actions workflow for CI/CD
├── infra/
│   ├── main.tf                    # Terraform config (S3, EC2 for MLflow serving)
│   └── variables.tf               # Terraform variables
├── src/
│   ├── train.py                   # Model training script with MLflow
│   └── serve.py                   # Script to serve the model with MLflow
├── data/                          # Placeholder for sample data (not tracked)
│   └── user_ratings.csv           # Example dataset (add to .gitignore)
├── requirements.txt               # Python dependencies
├── README.md                      # Project overview and setup instructions
└── .gitignore                     # Git ignore file
