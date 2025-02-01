# Assignment 2: Creating a Container and Pushing to a Repository

## Overview
This project involves creating a simple program, containerizing it with Docker, adding a database container, and pushing the image to Docker Hub.

## Steps Followed

### 1. **Writing a Simple Program**
A Python script (`hello.py`) was created that prints:
```python
print("Hello World! I am Irfan Mansuri")
```

### 2. **Containerizing the Application**
A `Dockerfile` was created to package the Python script into a container:
```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY hello.py /app/hello.py

CMD ["python", "/app/hello.py"]
```

### 3. **Adding a Database Container**
A `docker-compose.yml` file was created to set up both the application and a PostgreSQL database:
```yaml
version: '3.8'

services:
  app:
    build: .
    container_name: hello_app
    depends_on:
      - db

  db:
    image: postgres:latest
    container_name: hello_db
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydatabase
    ports:
      - "5432:5432"
```

### 4. **Building and Running the Containers**
Run the following commands:
```sh
docker-compose build
docker-compose up -d
docker ps  # Verify containers are running
docker logs hello_app  # Check output
```
Expected output:
```
Hello World! I am Irfan Mansuri
```

### 5. **Tagging and Pushing to Docker Hub**
1. Log in to Docker Hub:
   ```sh
   docker login
   ```
2. Tag the image:
   ```sh
   docker tag taskb-app iffyann/ell887:latest
   ```
3. Push the image:
   ```sh
   docker push iffyann/ell887:latest
   ```


