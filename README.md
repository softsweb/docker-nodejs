# Docker Node.js

This is a minimal Node.js application that serves as a simple example for demonstrating how to containerize Node.js applications using Docker.

## Prerequisites

Ensure you have the following installed:
- [Docker](https://docs.docker.com/get-docker/)

## Project Structure

```bash
docker-nodejs-todo/
├── Dockerfile                # Dockerfile to build the Node.js app container
├── docker-compose.yml        # Docker Compose file for running the container
├── .dockerignore             # Files to ignore when building the Docker image
├── package.json              # App's dependencies and metadata
├── package-lock.json         # Lock file for exact dependency versions
├── src/                      # Application source files
│   ├── index.js              # Main application entry point
│   ├── routes/               # REST API routes for Todo app
│   │   ├── addItem.js
│   │   ├── deleteItem.js
│   │   ├── getItems.js
│   │   └── updateItem.js
│   └── static/               # Static files (HTML, CSS, JS)
│       ├── index.html        # Main frontend HTML file
│       ├── css/              # Static CSS files
│       └── js/               # Static JavaScript files
└── README.md                 # Project documentation
```

## Running the App

### Option 1: Using Docker Compose

1. Clone this repository:

    ```bash
    git clone https://github.com/softsweb/docker-nodejs.git
    cd docker-nodejs-todo
    ```

2. Build and run the Docker container using Docker Compose:

    ```bash
    docker compose up -d --build
    ```

3. Open your browser and navigate to `http://localhost:3000` to see the app running.


### Option 2: Using Docker image

1. Build the Docker image:
    ```bash
    docker build -t todo-app:latest .
    ```

2. Edit the docker-compose.yml file and replace the build section with the image field, like so:

    ```bash
    # docker-compose.yml
    version: '3'
    services:
    app:
        image: todo-app:latest
        ports:
        - "3000:3000"
        environment:
        - NODE_ENV=production
    ```

3. Now, run the Docker container using Docker Compose:

    ```bash
    docker compose up -d
    ```

   OR 

    ```bash
    docker run -p 3000:3000 todo-app:latest
    ```

4. Open your browser and navigate to http://localhost:3000 to see the app running.

## Dockerfile Overview

The `Dockerfile` in this project builds a Node.js app using the lightweight **Node Alpine** image. The `npm ci` command is used to install dependencies from the `package.json` and `package-lock.json` files. It also runs the app as a non-root user for security purposes.

## Docker Compose

The `docker-compose.yml` file simplifies the process of building and running the Docker container by exposing port `3000` and automatically using the production environment.

## Follow Me for More Tutorials!

YouTube: [SoftsWeb Channel](https://www.youtube.com/@SoftsWeb)

Website: [SoftsWeb](https://softsweb.com)


## License

This project is licensed under the MIT License.