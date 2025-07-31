Calculator App with Kubernetes (Kind)
This project demonstrates a simple calculator web application built using HTML, CSS, JavaScript, and Node.js, packaged with Docker, and deployed on a local Kubernetes cluster using Kind (Kubernetes in Docker).

The application features a clean, responsive UI accessible from the browser, showcasing a complete workflow of containerization and Kubernetes deployment.

Prerequisites
Ensure the following are installed on your system:

Node.js (v16+ recommended)

Docker

Kind

kubectl

Setup Instructions

**1. Clone the Repository**

bash
Copy
Edit
git clone <your-repo-url>
cd calculator-app

**2. Install Dependencies**

bash
Copy
Edit
npm install
This installs all required Node.js packages for the calculator app.

**3. Build the Docker Image**

bash
Copy
Edit
docker build -t calculator-app:latest .
This command creates a Docker image tagged as calculator-app:latest.

**4. Create a Kind Cluster**

bash
Copy
Edit
kind create cluster --config kind-config.yaml
kind-config.yaml defines the cluster configuration (e.g., ports mapping for browser access).

Verify the cluster is running:

bash
Copy
Edit
kubectl cluster-info

**5. Load Docker Image into Kind**

bash
Copy
Edit
kind load docker-image calculator-app:latest
This makes the locally built image available to the Kind cluster without pushing it to a remote registry.

**6. Deploy to Kubernetes**

Apply the deployment and service YAMLs to launch the app:

bash
Copy
Edit
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
Check if pods are running:

bash
Copy
Edit
kubectl get pods
Check services and assigned NodePort:

bash
Copy
Edit
kubectl get svc

**7. Access the Application**
   
Open your browser and navigate to:

arduino
Copy
Edit
http://localhost:30080
(Port 30080 comes from the NodePort service configuration.)

**8. Clean Up**
When done, delete the Kind cluster to free resources:

bash
Copy
Edit
kind delete cluster

**Project Highlights**

Node.js Backend for handling calculator operations.

Dockerized Application for consistent containerized deployment.

Kubernetes Deployment with Kind for local cluster testing.

NodePort Service to access the application via a browser.

Clean & Responsive UI built with HTML, CSS, and vanilla JavaScript.
