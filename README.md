
# VIE-AI Dashboard

Provided by: **EXUS**

## Description

The VIE-AI Dashboard provides interactive explainable AI interfaces for multiple models, including flooding prediction, classification (ICCS models), temperature anomalies (FiClima model), and infiltration modeling. It handles data processing from CSV files, feature engineering, machine learning model loading (e.g., Random Forest, Gradient Boosting), and XAI explanations via dashboards proxied by Nginx.

## Installation Prerequisites

- Docker and Docker Compose installed
- Access to the URBREATH container registry: ```registry.urbreath.tech```

## Installation Instructions
VIE-AI Dashboard - Installation Instructions

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

4. Access the dashboards:

- Homepage: `https://vie-ai-dev.urbreath.tech/`
- Flooding: `https://vie-ai-dev.urbreath.tech/flooding/`
- Urban Heat Island (Randon Forrest): `https://vie-ai-dev.urbreath.tech/uhi-rf/`
- Urban Heat Island (Support Vector Classifier): `https://vie-ai-dev.urbreath.tech/uhi-svc/`
- Temperature Anomalies: `https://vie-ai-dev.urbreath.tech/ficlima/`
- Infiltration: `https://vie-ai-dev.urbreath.tech/infiltration/`

These routes are managed and proxied to specific internal ports by Nginx.

## Built Image Registry

- Registry URL: ```registry.urbreath.tech```
- Image Name: ```registry.urbreath.tech/vie-ai:v3```
- Version: `V3.0`

## License
This tool is licensed under Proprietary Software Licence - End-User License Agreement (EULA).
