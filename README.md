# Lightbulb Project

- BACKEND - Python Django
- FRONTEND - React with Typescript & Vite for local development

## Prerequisites

- Docker
- Docker Compose

## Quick Start

1. Clone the repository:
```bash
git clone <repository-url>
cd Lightbulb
```

2. Build and run the containers:
```bash
# Build the Docker image locally first
docker build -t bank .

# Run it
docker-compose up --build
```

3. Then run:
```bash
# Run migrations
docker-compose exec web python3 manage.py migrate

# Create superuser
docker-compose exec web python3 manage.py createsuperuser
```

3. Now you can access the backend at:
```
http://127.0.0.1:8001 or localhost:8001
http://127.0.0.1:8001/api
http://127.0.0.1:8001/api/swagger
```
And frontend at (login with your superuser credentials created previously):
```
http://127.0.0.1:3000 
```
4. Shut all the services down:
```
docker-compose down 
```

## Environment Variables

The following environment variables can be adjusted in .env:

- `DEBUG`: Set to 1 for development
- `POSTGRES_DB`: Database name
- `POSTGRES_USER`: Database user
- `POSTGRES_PASSWORD`: Database password
- `BACKEND_PORT`: Port allocated for the Django app


### Docker Configuration

The project uses following Docker configurations:

1. `Dockerfile`: Builds the Python/Django application image
   - Uses Python 3.12 slim base image
   - Installs system and Python dependencies
   - Sets up the application environment

2. `frontend/Dockerfile`: Builds the React application image
   - Uses node:18-alpine as a base image
   - Serves frontend files
   - Vite for seamless local development

2. `docker-compose.yml`: Orchestrates the application services
   - `web`: Django application service
     - Builds from Dockerfile
     - Maps container's internal port 8000 to outside 8001
     - Mounts code for development
     - Connects to PostgreSQL
   - `db`: PostgreSQL database service
     - Uses PostgreSQL 13
     - Persists data using Docker volumes
     - Configurable through environment variables
   - `frontend`: React App on Typescript

## CI/CD Environment

Check README inside corresponding folder


## License

[Your chosen license]
