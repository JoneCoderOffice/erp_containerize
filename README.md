# ERP Containerization

This repository provides a Docker-based environment to orchestrate and run the full ERP ecosystem. It simplifies development and deployment by containerizing the backend, frontend, admin panel, and necessary infrastructure services.

## Services Overview

The setup includes the following services:

| Service | Port | Description |
| :--- | :--- | :--- |
| **Backend** | `8002` (HTTP), `8443` (HTTPS) | Core API built with PHP/Laravel. |
| **Web Frontend** | `3001` | The main customer-facing web application. |
| **Admin Panel** | `3002` | Dashboard for administrative management. |
| **Database** | `5432` | PostgreSQL 17 database. |
| **Redis** | `6378` | In-memory data store for caching and sessions. |

## Prerequisites

Ensure you have the following installed on your machine:
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Getting Started

Follow these steps to get the environment up and running:

### 1. Configure Environment Variables
Copy the example environment file to create your own configuration:
```bash
cp .env.example .env
```
Edit the `.env` file and ensure the project directory paths match your local setup:
- `BACKEND_PROJECT_DIR`: Path to the `erp_back` repository.
- `WEB_PROJECT_DIR`: Path to the `erp_web` repository.
- `ADMIN_PROJECT_DIR`: Path to the `erp_admin` repository.

### 2. Build and Start Containers
Run the following command to build the images and start the services in the background:
```bash
docker compose up --build -d
```

### 3. Access the Applications
Once the containers are running, you can access the applications at:
- **Backend API**: [http://localhost:8002](http://localhost:8002)
- **Web Frontend**: [http://localhost:3001](http://localhost:3001)
- **Admin Panel**: [http://localhost:3002](http://localhost:3002)

## Common Commands

- **Stop all services**:
  ```bash
  docker compose stop
  ```
- **Down all services (removes containers)**:
  ```bash
  docker compose down
  ```
- **View logs**:
  ```bash
  docker compose logs -f [service_name]
  ```
- **Access a container shell**:
  ```bash
  docker compose exec backend bash
  ```

## Volumes & Persistence
- **PostgreSQL Data**: Persisted in the `dbdata` volume.
- **Redis Data**: Persisted in the `redisdata` volume.
- **Application Code**: Mounted as volumes from your local machine, allowing for real-time development updates.
