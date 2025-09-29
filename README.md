# aiops-The-Alphabet-Alchemist

A microservice for performing various text transformations.

## Description

The Alphabet Alchemist is a whimsical microservice that provides a RESTful API for various text-based transformations and analyses. Whether you need to reverse a string, count its vowels, or check if it's a palindrome, the Alchemist has a spell for it. This project is containerized using Docker for easy setup and deployment.

## Features

*   Reverse a given string.
*   Check if a string is a palindrome.
*   Count the number of vowels in a string.
*   Convert a string to uppercase.
*   Convert a string to lowercase.

## API Endpoints

The service exposes the following endpoints, typically running on port 5000:

*   `POST /api/reverse`: Reverses the input string.
*   `POST /api/palindrome`: Checks if the input string is a palindrome.
*   `POST /api/vowel_count`: Counts vowels in the input string.
*   `POST /api/uppercase`: Converts the input string to uppercase.
*   `POST /api/lowercase`: Converts the input string to lowercase.

All endpoints expect a JSON payload with a `text` key: `{"text": "your string here"}`.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

You need to have Docker and Docker Compose installed on your machine.

*   [Docker Desktop](https://www.docker.com/products/docker-desktop)

### Running with Docker Compose

This project is designed to be run with Docker Compose, which simplifies the process of setting up and running the application and its dependencies.

1.  **Clone the repository (if you haven't already):**

    ```bash
    git clone https://github.com/your-username/aiops-The-Alphabet-Alchemist.git
    cd aiops-The-Alphabet-Alchemist
    ```

2.  **Create a `docker-compose.yml` file:**

    Create a file named `docker-compose.yml` in the root of the project with the following content. This assumes you have a `Dockerfile` in the project root that builds the application image.

    ```yaml
    version: '3.8'
    services:
      alphabet-alchemist:
        build: .
        image: alphabet-alchemist-app
        container_name: alphabet-alchemist
        ports:
          - "5000:5000"
        restart: unless-stopped
    ```

3.  **Build and run the application:**

    Open a terminal in the project's root directory and run the following command:

    ```bash
    docker-compose up --build -d
    ```

    This command will build the Docker image for the application (if it doesn't exist) and start the service in detached mode.

4.  **Verify the application is running:**

    You can check the status of the running containers with:

    ```bash
    docker-compose ps
    ```

    You should see the `alphabet-alchemist` container in an "up" state.

## Usage

Once the application is running, you can interact with it by sending requests to the API endpoints. Here are some examples using `curl`.

### Reverse a string

```bash
curl -X POST -H "Content-Type: application/json" -d '{"text": "hello world"}' http://localhost:5000/api/reverse
```
Expected response:
```json
{
  "result": "dlrow olleh"
}
```

### Check for a palindrome

```bash
curl -X POST -H "Content-Type: application/json" -d '{"text": "madam"}' http://localhost:5000/api/palindrome
```
Expected response:
```json
{
  "is_palindrome": true
}
```

## Stopping the application

To stop the application, run the following command in the project's root directory:

```bash
docker-compose down
```
