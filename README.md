# Staff-Service Microservice

This is a straightforward **Staff-Service Microservice** designed to manage staff information for Best Buy. It offers REST APIs to perform CRUD operations (Create, Read, Update, Delete) on staff data, which is temporarily stored in memory for simplicity. The project follows the 12-Factor App principles to ensure it is scalable, maintainable, and portable.

## 1. Overview

The **Staff-Service Microservice** provides a RESTful API to manage staff information. The service allows for the following operations:

- **Create**: Add a new staff member.
- **Read**: Retrieve information about all staff or a specific staff member.
- **Update**: Modify the details of an existing staff member.
- **Delete**: Remove a staff member from the system.


### 2. Dependencies

The microservice relies on the following Python libraries:

- **Flask**: A minimalistic WSGI web framework for Python, ideal for building web applications.
- **python-dotenv**: A library for loading environment variables from `.env` files, making it easier to manage configuration settings.

The dependencies are listed in the `requirements.txt` file, and can be installed using the command:

```bash
pip install -r requirements.txt
```

### 2.3 Environment Configuration

The port number is configured dynamically using an `.env` file, which stores the environment variable as follows:

```
PORT=5000
```

The `python-dotenv` library loads this value into the Flask app, allowing for easy modification of the port number when deploying the service to various environments.

### 2.4 API Endpoints

The microservice provides the following CRUD operations as RESTful API endpoints:

#### Create Staff

**POST /staff**

Request Body (JSON):

```json
{
  "name": "John Doe",
  "position": "Sales Associate",
  "department": "Sales",
  "email": "john.doe@bestbuy.com",
  "phone": "555-555-5555"
}
```

#### Read All Staff

**GET /staff**

Returns a list of all staff members.

#### Read Staff by ID

**GET /staff/{id}**

Returns details of a staff member based on their ID.

#### Update Staff

**PUT /staff/{id}**

Request Body (JSON):

```json
{
  "id": "1",
  "name": "Jane Doe",
  "position": "Senior Sales Associate",
  "department": "Sales",
  "email": "jane.doe@bestbuy.com",
  "phone": "555-555-1234"
}
```

#### Delete Staff

**DELETE /staff/{id}**

Deletes the staff member with the specified ID.

### 2.5 Codebase and GitHub Repository

The source code for the microservice is tracked in a GitHub repository. The initial codebase was pushed with the following commit message:

```
Initial Commit
```

The repository is located at: [bestbuy-staff-service](https://github.com/your-username/examfinal)

### 2.6 Running the Service

To run the microservice locally:

1. Ensure that you have Python installed and the dependencies are set up using:

   ```bash
   pip install -r requirements.txt
   ```

2. Run the Flask app:

   ```bash
   flask run
   ```

   The service will be available at `http://localhost:5000`.

You can test the CRUD operations using an HTTP client like **Postman** or by using a `.http` file with a REST Client in **VS Code**.

### 2.7 Sample Data

The microservice can be tested with the following sample data for staff:

- **Staff 1**:
  - Name: Michael Scott
  - Position: Regional Manager
  - Department: Sales
  - Email: michael.scott@bestbuy.com
  - Phone: 555-555-5555

- **Staff 2**:
  - Name: Jim Halpert
  - Position: Sales Associate
  - Department: Sales
  - Email: jim.halpert@bestbuy.com
  - Phone: 555-555-1234

## 3. 12-Factor App Principles Applied

The microservice adheres to the 12-Factor App methodology:

- **Codebase**: The app uses a single GitHub repository with one codebase deployed across multiple environments.
- **Dependencies**: All dependencies are listed in `requirements.txt` to ensure isolation and easy environment setup.
- **Config**: Configuration like the port number is stored in the `.env` file, loaded at runtime via `python-dotenv`.
- **Backing Services**: No external services are used, but in a real-world scenario, backing services like databases would be configured via environment variables.

## 4. Conclusion

This simple **Staff-Service Microservice** offers a scalable, stateless way to manage staff information. By following the 12-factor app principles and storing configuration in environment variables, this service can easily be deployed and maintained in various cloud environments.


## 2. Containerize the Service (4 Marks)

### Dockerizing the Staff-Service Microservice

To enhance the portability and ease of deployment of the **Staff-Service Microservice**, I used Docker to containerize the application. Here are the steps I followed::

### 2.1 Docker Image Creation

A Dockerfile was created to containerize the **Staff-Service Microservice**. This file outlines the steps for building the Docker image, such as setting up the Python environment, installing required dependencies, and specifying the commands to launch the Flask application.

### 2.2 Build the Docker Image

After creating the Dockerfile, the following command was used to build the Docker image:

bash
docker build -t bestbuy-staff-service .


This command builds the Docker image from the current directory (.), tagging it with the name bestbuy-staff-service.

### 2.3 Push the Docker Image to Docker Hub

Once the Docker image was built, it was pushed to my personal Docker Hub account for easy access and deployment.

1. *Login to Docker Hub*:
   
   bash
   docker login
   

   Enter your Docker Hub credentials to log in.

2. *Tag the Docker Image*:

   bash
   docker tag bestbuy-staff-service <your-dockerhub-username>/bestbuy-staff-service
   

   Replace <your-dockerhub-username> with your actual Docker Hub username.

3. *Push the Docker Image*:

   bash
   docker push <your-dockerhub-username>/bestbuy-staff-service
   

   This uploads the image to Docker Hub, where it can be accessed from anywhere.

### 2.4 Docker Hub Link

After pushing the image to Docker Hub, you can access it using the following link. Please replace <your-dockerhub-username> with your actual username:

Link to docker hub image: https://hub.docker.com/repository/docker/akhiljos256/bestbuy-ls/general

### 2.5 Commit the Dockerfile

The Dockerfile was added to the repository and committed with the following message:


"Adding Dockerfile"


Certainly! Below is the markdown file with detailed technical documentation and an explanation of each part of the Kubernetes YAML file. The document also includes key comments and technical notes to guide you through the process.

---