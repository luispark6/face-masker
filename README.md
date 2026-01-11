# face-masker Project Structure

This document describes the directory layout for a face blurring application built with a React frontend and FastAPI backend.

## Directory Layout

```
project-root/
├─ docker-compose.yml
├─ .env
├─ backend/
│  ├─ Dockerfile
│  └─ app/
│     └─ main.py
├─ frontend/
│  ├─ Dockerfile
│  └─ src/
└─ volumes/
   ├─ db/
   └─ models/
```

## Directory & File Descriptions

### Root Level

- **`docker-compose.yml`** - Docker Compose configuration file that orchestrates the multi-container application (frontend, backend, and any associated services)
- **`.env`** - Environment variables file containing configuration settings for the application (API keys, database credentials, etc.)

### `/backend`

Contains the FastAPI backend application responsible for processing images and performing face detection/blurring.

- **`Dockerfile`** - Container definition for building the backend Python environment
- **`app/main.py`** - Main FastAPI application entry point containing API routes and face blurring logic

### `/frontend`

Houses the React frontend application that provides the user interface for uploading images and displaying results.

- **`Dockerfile`** - Container definition for building the frontend Node.js environment
- **`src/`** - Source code directory for React components, styles, and application logic

### `/volumes`

Persistent storage volumes mounted by Docker containers.

- **`db/`** - Database storage directory (if applicable for storing metadata, user data, or processing history)


## Application Flow

1. Users interact with the React frontend to upload images
2. Frontend sends image data to the FastAPI backend via HTTP requests
3. Backend processes the image using face detection models stored in `/volumes/models`
4. Detected faces are blurred and the processed image is returned to the frontend
5. Results are displayed to the user in the React interface

## Development Setup

The application is containerized using Docker, with services defined in `docker-compose.yml`. To run the application:

```bash
docker-compose up
```

Environment-specific configurations should be set in the `.env` file before starting the containers.