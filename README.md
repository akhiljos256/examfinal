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

 3 Deploy to Azure Kubernetes Service (AKS)




## Steps to Deploy the Service

To create an Azure Kubernetes Service (AKS) cluster via the Azure Portal, first, log in to the Azure Portal using your Azure credentials. Navigate to [https://portal.azure.com](https://portal.azure.com) and sign in. Next, create a Resource Group to hold your AKS cluster and related resources by selecting *Create a resource* from the left sidebar, searching for *Resource group*, and clicking *Create*. Fill in the required details like *Subscription*, *Resource group name*, and *Region*, then click *Review + Create* and *Create*. After the resource group is created, proceed to create the AKS cluster by selecting *Create a resource* again, typing *Kubernetes Service*, and clicking *Create*. On the *Create Kubernetes Cluster* page, choose your subscription, select the resource group, provide a name for your AKS cluster, select the region, and the desired Kubernetes version. In the *Node pools* section, configure your worker nodes by providing a name, selecting the node size, entering the number of nodes, and setting the disk size. Finally, review all settings and click *Create* to initiate the deployment. The process may take a few minutes to complete. Once the cluster is created, you can access it using the Azure CLI with the `az aks get-credentials` command to retrieve the Kubeconfig and connect to your AKS cluster.

### *Access Your AKS Cluster*

Once your AKS cluster is successfully created, you can access it via the Azure CLI by opening your terminal or command prompt and running the command `az aks get-credentials --resource-group finalexam --name <cluster name> --overwrite-existing`, replacing `finalexam` with your resource group name and `<cluster name>` with your AKS cluster's name. The `--overwrite-existing` flag ensures any previous configurations are replaced. To verify the connection, use `kubectl get nodes`, which will display the nodes in your AKS cluster. You can also verify the cluster in the Azure Portal by navigating to your AKS cluster page and clicking on **Nodes** under *Settings*, where you should see your active node(s). This setup allows you to manage your AKS cluster via the Azure CLI.

### 2. *Write the Kubernetes Deployment YAML*

The *Deployment* YAML file specifies the configuration for deploying the microservice in Kubernetes, including the container image, the number of replicas (with a single replica used for simplicity), and the port configuration, while the *Service* YAML defines how the service is exposed externally. The *Deployment* section includes a *Selector* to identify the correct pods using labels and a *Template* to define pod metadata and container specifications. The *Service* section uses the label from the deployment (app: staff-service) to route traffic to the pods, exposes port 80 externally, and forwards traffic to port 5000 inside the container, with the service type set to LoadBalancer to provision an external IP for public access.

### 3. *Deploy the YAML File to AKS*

Once the YAML file is ready, apply it to the AKS cluster using the command `kubectl apply -f staff-service-deployment.yaml`, which will create the necessary resources (Deployment and Service) on the AKS cluster. After deployment, retrieve the external IP assigned by the LoadBalancer by running `kubectl get services` and look for the EXTERNAL-IP column under your staff-service-service. It may take a few minutes for the IP to be assigned, after which you can use it to access the service publicly. The YAML file is composed of two main sections: *Deployment* and *Service*. The *Deployment* section specifies the API version, resource kind, and metadata like deployment name, the number of replicas (set to 1), and the label selector for identifying the pods. The *Service* section is configured to expose the application externally via a LoadBalancer, routing traffic to the service's port 5000. The *Deployment* section also defines the container image, which is the Docker image from DockerHub, and the container's port configuration.



## Testing the Service

After deploying the service and obtaining the *external IP*, you can test the service using **Send HTTP** or any HTTP client. To do this, first, retrieve the public IP by running `kubectl get services`. Once you have the external IP (e.g., http://<external-ip>:80), you can test the CRUD operations exposed by the microservice by making requests to the service using the appropriate HTTP methods (GET, POST, PUT, DELETE) based on the operations you want to perform.

## Conclusion

By following these steps, you have successfully deployed the *Staff-Service Microservice* to *Azure Kubernetes Service (AKS)*. The service is now publicly accessible via a **LoadBalancer**, enabling external access for testing and interaction through HTTP requests..


# Set Up CI/CD Pipeline (3 Marks)

### Objective:
The goal is to set up a CI/CD pipeline using *GitHub Actions* to automate the build, test, and deployment processes for the *Staff-Service Microservice*. This will streamline the workflow, ensuring that every change to the codebase triggers an automated process for building the Docker image, running tests, and deploying the application to *Azure Kubernetes Service (AKS)*, making the deployment process more efficient and consistent..


To configure a CI/CD pipeline using GitHub Actions for the *Staff-Service Microservice*, create a `.github/workflows` directory in your repository and add a `ci_cd.yaml` file that defines the steps to build, test, push the Docker image to Docker Hub, and deploy the application to Azure Kubernetes Service (AKS). Then, add necessary secrets to your GitHub repository, such as **DOCKER_USERNAME**, **DOCKER_PASSWORD**, and **KUBE_CONFIG_DATA** (base64-encoded Kubernetes config), to enable secure access to Docker Hub and Kubernetes. Finally, set up environment variables like **DOCKER_IMAGE_NAME**, **DEPLOYMENT_NAME**, and **CONTAINER_NAME** to configure the deployment process. After pushing the `ci_cd.yaml` file and setting the secrets and variables, your CI/CD pipeline will automate the entire build, test, push, and deploy workflow for the staff-service application.

### Technical Overview of CI/CD Pipeline (ci_cd.yaml):

The `ci_cd.yaml` file for GitHub Actions will contain multiple stages to automate the build, test, push, and deploy processes for the *Staff-Service Microservice*. The **Build Stage** will pull the Dockerfile, build the Docker image using `docker build`, and tag the image with a version number. In the **Test Stage**, tests will be run using a framework like `pytest` to ensure the application's functionality. The **Push Stage** will log in to Docker Hub using credentials stored in GitHub Secrets and push the built Docker image to the repository. Finally, the **Deploy Stage** will use the Kubernetes CLI (`kubectl`) to deploy the updated image to the AKS cluster, update the Kubernetes deployment, and expose the application to the internet via a LoadBalancer service. This structure ensures a smooth and automated workflow for continuous integration and deployment.

### Conclusion:

By following the above steps, you will have a fully automated CI/CD pipeline that builds, tests, pushes, and deploys the *Staff-Service Microservice* using GitHub Actions and Azure Kubernetes Service (AKS). This setup ensures that every change made to the application code is automatically tested and deployed, providing a seamless process for managing updates and ensuring consistency across environments. With this pipeline in place, you can focus on development while the automation takes care of the building, testing, and deployment tasks..



## Test the CI/CD Pipeline (2 Marks)

### Objective:
To trigger and verify the CI/CD workflow, push the changes (including the `ci_cd.yaml` file) to your GitHub repository, and GitHub Actions will automatically trigger the workflow based on the events defined in the file. Navigate to the **Actions** tab in your GitHub repository to see the progress of the workflow jobs (Build, Test, Push, Deploy). Each job will indicate its status—whether it's in progress, succeeded, or failed—and you can view detailed logs for troubleshooting. If any step fails, address the issues (such as incorrect environment variables or authentication problems) and push the changes again to re-trigger the workflow. Once successful, your staff-service application will be automatically built, tested, pushed to Docker Hub, and deployed to Azure Kubernetes Service (AKS).

### Steps:

To test and trigger the CI/CD pipeline, first, add a new user to the `app.py` file as an example to test the trigger, then commit and push the changes to your GitHub repository. After pushing, GitHub Actions will automatically trigger the pipeline, and you can monitor its progress by going to the **Actions** tab in your GitHub repository to verify the success of the build, test, push, and deploy stages. Once the pipeline completes successfully, check the live service to ensure that the new user data is available through the exposed endpoint, confirming the proper functioning of the CI/CD pipeline.
