# .NET Microservices Application

This project demonstrates a microservices-based architecture using .NET and C#. The application leverages RabbitMQ for service communication, MongoDB for data storage, Docker for containerization, and Postman for API testing.

## Table of Contents
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Architecture Overview](#architecture-overview)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Step 1: Clone the Repository](#step-1-clone-the-repository)
  - [Step 2: Set Up MongoDB](#step-2-set-up-mongodb)
  - [Step 3: Set Up RabbitMQ](#step-3-set-up-rabbitmq)
- [Running the Services](#running-the-services)
  - [Step 4: Build and Run with Docker](#step-4-build-and-run-with-docker)
  - [Step 5: Verify Services are Running](#step-5-verify-services-are-running)
- [Testing the APIs](#testing-the-apis)
  - [Step 6: Use Postman for API Testing](#step-6-use-postman-for-api-testing)
---

## Features
- **Service Communication:** RabbitMQ for inter-service communication.
- **Data Storage:** MongoDB used as the NoSQL database for storing data.
- **Containerization:** Docker for packaging services into containers.
- **API Testing:** Postman for testing RESTful APIs.

## Technologies Used
- **.NET Core**
- **C#**
- **RabbitMQ**
- **MongoDB**
- **Docker**
- **Postman**

## Architecture Overview
The application is designed with the following microservices:
1. **Service A:** Handles user management and authentication.
2. **Service B:** Manages products and inventory.
3. **Service C:** Handles orders and payments.

Each service is deployed independently in a Docker container and communicates using RabbitMQ.

## Prerequisites
To run this project, ensure that you have the following installed on your machine:
- [.NET SDK](https://dotnet.microsoft.com/download)
- [Docker](https://www.docker.com/get-started)
- [MongoDB](https://www.mongodb.com/try/download/community)
- [RabbitMQ](https://www.rabbitmq.com/download.html)
- [Postman](https://www.postman.com/downloads/)

## Getting Started

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
```

### Step 2: Set Up MongoDB
1. Install MongoDB if not already installed.
2. Start MongoDB service.
3. Update the MongoDB connection string in the `appsettings.json` file of each service.

### Step 3: Set Up RabbitMQ
1. Install RabbitMQ.
2. Run RabbitMQ using Docker:
   ```bash
   docker run -d --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management
   ```
3. Access the RabbitMQ management UI at `http://localhost:15672` (default credentials: guest/guest).

## Running the Services

### Step 4: Build and Run with Docker
1. Ensure Docker is running.
2. Navigate to each microservice directory and build Docker images:
   ```bash
   docker build -t service-a .
   docker build -t service-b .
   docker build -t service-c .
   ```
3. Run the services:
   ```bash
   docker-compose up
   ```
   
   This will start all services as defined in the `docker-compose.yml` file.

### Step 5: Verify Services are Running
- Visit the API endpoints of each service:
  - **Service A:** `http://localhost:5000/api/users`
  - **Service B:** `http://localhost:5001/api/products`
  - **Service C:** `http://localhost:5002/api/orders`

## Testing the APIs

### Step 6: Use Postman for API Testing
- Import the provided Postman collection from the repository.
- Test the endpoints for each service:
  - **Service A (User Management):**
    - GET/POST/PUT/DELETE operations for users.
  - **Service B (Product Management):**
    - CRUD operations for products.
  - **Service C (Order Management):**
    - Placing and retrieving orders.
