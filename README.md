# vie-ai
 # VIE-AI Dashboard Deployment

This repository contains the deployment configuration for the VIE-AI XAI Dashboard application. The application comes as a pre-built Docker image with all data and models included - no additional data files needed.

## Prerequisites

- Docker and Docker Compose installed
- Access to the URBREATH container registry (`registry.urbreath.tech`)

## Quick Start

1. Clone this repository:
```bash
git clone <repository-url>
cd <repository-name>
```

2. Edit the `.env` file to specify ports, data and, model paths.

3. Start the application:
```bash
docker-compose up -d
```

4. Access the XAI dashboards:

- Homepage: `https://vie-ai-dev.urbreath.tech/`
- Flooding: `https://vie-ai-dev.urbreath.tech/flooding/`
- Classification: `https://vie-ai-dev.urbreath.tech/classification/`
- Temperature Anomalies: `https://vie-ai-dev.urbreath.tech/ficlima/`
- Infiltration: `https://vie-ai-dev.urbreath.tech/infiltration/`

These routes are managed and proxied to specific internal ports by Nginx.
---

## Configuration Overview

### .env

Configure the following in your `.env` file:

| Variable                       | Description                             | Example Value                  |
|--------------------------------|-----------------------------------------|--------------------------------|
| HOMEPAGE_PORT                  | Homepage dashboard port                 | 8050                           |
| FLOODING_PORT                  | Flooding dashboard port                 | 8060                           |
| CLASSIFICATION_PORT            | Classification dashboard port           | 8061                           |
| FICLIMA_PORT                   | Temp-anomalies dashboard port           | 8062                           |
| INFILTRATION_PORT              | Infiltration dashboard port             | 8063                           |
| FLOODING_MODEL_PATH            | Path to flooding model                  | /app/saved_model/flooding_model_components_new.pkl |
| CLASSIFICATION_MODEL_PATH      | Path to classification model            | /app/saved_model/iris_model_components.pkl |
| FICLIMA_MODEL_PATH             | Path to temperature anomalies model     | /app/saved_model/rf_model_Lag3_160840.joblib |
| INFILTRATION_MODEL_PATH        | Path to infiltration model              | /app/saved_model/leuven_infiltration_model_complete1.pkl |
| METEO_DATA_PATH                | Path to meteorological data             | /app/data/test_data22-24.csv   |
| SOIL_DATA_PATH                 | Path to soil data                       | /app/data/soil_data.csv        |
| FICLIMA_DATA_PATH              | Path to temp. anomalies input data      | /app/data/ficlima/sample_Lag3_160840.csv |
| INFILTRATION_DATA_PATH         | Path to infiltration input data         | /app/data/infiltration_model_data/synthetic_dashboard_input.csv |


The application will automatically:
- Load pre-built datasets
- Initialize the trained machine learning models
- Start the XAI dashboards interface

### nginx.conf

Handles reverse proxying for each dashboard route.  
Example routes:
- `/` → Homepage (port 8050)
- `/flooding/` → Flooding dashboard (port 8060)
- `/classification/` → Classification dashboard (port 8061)
- `/filcima/` → Temperature anomalies dashboard (port 8062)
- `/infiltration/` → Infiltration dashboard (port 8063)
---

## Application Features

Based on the startup logs, the application includes:
- Data processing from CSV files
- Feature engineering
- Machine learning dummy model training (Random Forest, Gradient Boosting)
- XAI (Explainable AI) dashboard interface

## Troubleshooting

### Container Issues
```bash
# Check container status
docker-compose ps

# View application logs
docker-compose logs dashboard

# Restart the application
docker-compose restart
```

No additional data files need to be provided - everything is self-contained.
