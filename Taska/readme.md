# Custom Nginx Web Server with ELL887 Endpoint

## Overview
This project sets up a custom Nginx container that serves a webpage at `http://localhost/ELL887`, displaying:
```
Hello World! I am Irfan Mansuri
```

## Project Structure
```
├── Dockerfile        # Defines the custom Nginx container
├── nginx.conf        # Custom Nginx configuration
├── index.html        # HTML file served
└── README.md         # Documentation
```

## Setup Instructions

### 1. Create the Repository on Your PC and the required files
```sh
 mkdir <repository-name>
 cd <repository-name>
```

### 2. Build the Docker Image
```sh
docker build -t custom-nginx .
```

### 3. Run the Container
```sh
docker run -d -p 80:80 custom-nginx
```

### 4. Access the Webpage
Open your browser and visit:
```
http://localhost/ELL887
```
You should see:
```
Hello World! I am Irfan Mansuri
```

## Troubleshooting
- **Issue: The page downloads instead of displaying**
  - Ensure the `nginx.conf` file includes `default_type text/html;` under the `/ELL887` location block.
  
- **Issue: Port 80 is already in use**
  - Run `docker ps` to check running containers.
  - Stop the conflicting container with `docker stop <container_id>`.
  - Restart the new container.

## Cleanup
To remove the container and free up resources:
```sh
docker ps  # Get container ID
docker stop <container_id>
docker rm <container_id>
docker rmi custom-nginx  # Remove the image if needed
```

## Author
- **irfan**

