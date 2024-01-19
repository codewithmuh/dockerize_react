# Dockerize React Application

## Overview

This repository provides a guide on how to containerize a React application using Docker. Docker allows you to package an application and its dependencies into a container, making it portable and easy to deploy across different environments.

![Terraform course](https://github.com/codewithmuh/dockerize_react/assets/51082957/8bc53f54-3a61-4232-b363-a75811d7834a)

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- Docker: [Install Docker](https://docs.docker.com/get-docker/)
- Node.js: [Install Node.js](https://nodejs.org/)

## Getting Started

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/codewithmuh/dockerize_react.git
   cd dockerize_react
   ```
   
2. **Build the React Application:**

If you haven't already, build your React application:

   ```bash
   npm install
   npm run build
   ```
   
3. **Create a Dockerfile:**

Create a file named **Dockerfile** in the root of your project with the following content:


 ```bash
# Use Node.js Alpine base image
FROM node:alpine

# Create and set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package.json package-lock.json /app/

# Install dependencies
RUN npm install

# Copy the entire codebase to the working directory
COPY . /app/

# Expose the port your app runs on (replace <PORT_NUMBER> with your app's actual port)
EXPOSE 3000

# Define the command to start your application (replace "start" with the actual command to start your app)
CMD ["npm", "start"]
```

4. **Build the Docker Image:**

Build the Docker image using the following command:

```bash

docker build -t your-react-app .
Replace your-react-app with a suitable image name.
```
Run the Docker Container:

Run the Docker container using the following command:

```bash

docker run -d --name react-app -p 3000:3000 codewithmuh/react-app:latest
```

This maps port 3000 on your local machine to port 3000 in the Docker container.

Access Your React Application:

Open your web browser and navigate to **http://localhost:3000** to view your React application running inside a Docker container.

### Customization

If your React app uses a different port, update the **EXPOSE** and **docker run** commands accordingly.

Modify the Dockerfile to suit your specific project structure and dependencies.

Consider using a **.dockerignore** file to exclude unnecessary files and directories from being copied into the Docker image.

### Additional Resources

- React Documentation: [Install Docker](https://docs.docker.com/get-docker/)
- Docker Documentation: [Install Docker](https://react.dev/)

Feel free to contribute to this repository by opening issues or creating pull requests. Happy Dockerizing!
