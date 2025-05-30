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

2. Copy the environment template and configure your settings:
```bash
cp .env.example .env
```

3. Edit the `.env` file with your specific configuration:
```bash
# Dashboard port (default: 8050)
DASHBOARD_PORT=8050

# Path to meteorological data (used by the application internally)
METEO_DATA_PATH=/app/data/test_data22-24.csv

# Path to soil data (used by the application internally)
SOIL_DATA_PATH=/app/data/soil_data.csv
```

4. Start the application:
```bash
docker-compose up -d
```

5. Access the XAI dashboard at: `http://localhost:8050` (or your configured port)

The application will automatically:
- Load pre-built datasets
- Initialize the trained machine learning models
- Start the XAI dashboard interface

## Application Features

Based on the startup logs, the application includes:
- Data processing from CSV files
- Feature engineering
- Machine learning dummy model training (Random Forest, Gradient Boosting)
- XAI (Explainable AI) dashboard interface

## Configuration

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `DASHBOARD_PORT` | Port for the web dashboard | 8050 |
| `METEO_DATA_PATH` | Path to meteorological data | - |
| `SOIL_DATA_PATH` | Path to soil data | - |

### Volume Mounts

The application only requires one volume mount:
- `./logs:/app/logs` - Application logs (created automatically)

**Note:** All data files and trained models are included in the Docker image - no external data files required.

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

### Common Issues

1. **Port already in use**: Change `DASHBOARD_PORT` in your `.env` file
2. **Container registry access**: Ensure you have access to `registry.urbreath.tech`  
3. **Permission issues**: Check that the `logs/` directory can be created and has write permissions

## What's Included

The Docker image (`registry.urbreath.tech/vie-ai:v1`) contains:
- Complete VIE-AI application source code
- Pre-trained machine learning models (`flooding_model_components.pkl`)
- All required datasets (CSV files)
- Configured Python environment with all dependencies

No additional data files need to be provided - everything is self-contained.
