# Lockedin DevOps and infrastructure

This repository contains configurations and pipelines for managing LockedIn DevOps environment. It includes configurations for Prometheus, Nginx, Jenkins, and Grafana dashboards.

## Project Structure

### 1. Prometheus
- **File**: [prometheus/prometheus.yml](prometheus/prometheus.yml)
- **Description**: Configuration file for Prometheus to scrape metrics from various targets:
  - **Nginx**: Metrics exposed by the Nginx exporter.
  - **Backend**: Metrics exposed at `/swagger-stats/metrics`.
  - **Node Exporter**: Metrics from the Node Exporter.

### 2. Nginx
- **File**: [nginx/nginx.config](nginx/nginx.config)
- **Description**: Nginx configuration file for serving the frontend and proxying API requests to the backend. It includes:
  - SSL configuration managed by Certbot.
  - CORS headers for API requests.

### 3. Jenkins
- **Files**:
  - [jenkins/Jenkinsfile_backend](jenkins/Jenkinsfile_backend)
  - [jenkins/jenkinsfile_frontend](jenkins/jenkinsfile_frontend)
- **Description**: Jenkins pipelines for building, testing, and deploying the backend and frontend Docker images. Key stages include:
  - Copying environment files.
  - Building Docker images.
  - Pushing images to Docker Hub.
  - Rebuilding Docker Compose services.

### 4. Grafana
- **File**: [Grafana/NginxDashboard](Grafana/NginxDashboard)
- **Description**: A Grafana dashboard for monitoring Nginx metrics, including:
  - Active connections.
  - Total requests.
  - Reading, writing, and waiting connections.

## How to Use

### Prometheus
1. Update the `prometheus.yml` file with the correct target addresses.
2. Start Prometheus using the configuration file.

### Nginx
1. Update the `nginx.config` file with the correct paths and domain.
2. Reload or restart the Nginx service to apply changes.

### Jenkins
1. Configure Jenkins with the required credentials (`lockedin-dockerhub`).
2. Add the Jenkinsfiles to your Jenkins jobs for CI/CD pipelines.

### Grafana
1. Import the `NginxDashboard` JSON file into Grafana.
2. Ensure Prometheus is configured as a data source in Grafana.

## Requirements
- **Prometheus**: For monitoring and alerting.
- **Nginx**: For serving the frontend and proxying API requests.
- **Jenkins**: For CI/CD pipelines.
- **Grafana**: For visualizing metrics.
