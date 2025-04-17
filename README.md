# bestbuy-staff-service
Overview
This project involves deploying a Staff Service application on Kubernetes. The goal is to build, containerize the application using Docker, and deploy it to a Kubernetes cluster (Azure Kubernetes Service - AKS). The application is intended to manage staff data and provide services accordingly. The process also integrates CI/CD workflows to automate build, test, and deployment using Docker and Kubernetes.

Steps Completed
1. Docker Image Build and Push
Dockerfile: We created a Dockerfile for building a container image of the staff service application.

Build Docker Image: Using the docker build command, we successfully built the Docker image.

Push to Docker Hub: After building the Docker image, we pushed it to Docker Hub for storage and later use in Kubernetes.

2. Kubernetes Cluster Setup
Azure Kubernetes Service (AKS): We set up a Kubernetes cluster on Azure using the Azure CLI.

Created a resource group (cst8915).

Created a Kubernetes cluster (bestbuy-cluster).

Successfully fetched credentials to interact with the cluster using az aks get-credentials.

3. Deployment Configuration
Kubernetes Deployment: We created a Kubernetes deployment YAML (deployment.yaml) to configure how the staff service application will run in the AKS cluster. This deployment describes the desired state, including the Docker image to use, the number of replicas, environment variables, etc.

Applying Deployment: We applied the Kubernetes deployment using kubectl apply -f deployment.yaml.

4. CI/CD Pipeline Setup
GitHub Actions (CI/CD): A GitHub Actions pipeline was created to automate the build, test, and deploy process.

The pipeline is triggered on push events to the main branch.

The pipeline includes stages for:

Building the Docker image.

Running unit tests (simulated in this case).

Pushing the image to Docker Hub.

Deploying the container to AKS.

Issues Encountered
Problem: Pods Are Not Running as Expected
After deploying the application to the AKS cluster, we encountered issues with the deployment, specifically:

Pods Are Stuck in "CrashLoopBackOff" State:

The pods are not starting successfully and are stuck in the CrashLoopBackOff state. This indicates that the containers are failing to start, but Kubernetes is trying to restart them continuously.

Invalid Image Name:

There was an issue with the image name being invalid when we tried to apply the new deployment. This prevented the pod from running.

Deployment Errors:

Errors like Error from server (NotFound): pods "deployment.yaml" not found and others related to missing resources were observed.

The deployment was created successfully, but the pod is not running as expected due to image issues or potential misconfiguration in the deployment file.

Steps Taken to Debug
We checked the logs of the pods, but there were errors indicating that the staff-service pod could not be found in the default namespace.

We attempted to troubleshoot by describing the pods, but the same errors persisted, indicating that the Kubernetes deployment was not able to correctly deploy or pull the Docker image.

Current Blocker
We are currently facing a CrashLoopBackOff issue on the pods due to potential configuration problems with the Docker image or deployment setup. These are the likely causes:

Docker Image Issue: The image might be improperly tagged, or the image name may not match the one stored in Docker Hub.

Deployment Configuration Issue: There could be missing environment variables, incorrect paths, or incorrect references to the Docker image in the Kubernetes deployment file.

Pod Creation Issue: Kubernetes is unable to create pods due to the errors in the deployment process.

Next Steps
Fix the Docker Image: Verify the image name and ensure it’s correctly tagged in the deployment configuration.

Check the Kubernetes Logs: Once the pods are running, further check logs to identify the root cause of the CrashLoopBackOff.

Test Deployment Again: After addressing the issues, we will try to deploy the application again and verify that the pods run successfully.

What to Add/Modify in the README:
Details About the Issues: Clearly mention the steps you've done so far, including Docker image building, Kubernetes deployment, and CI/CD pipeline setup. Then, state where you're stuck, which is the pod crash issue.

Root Cause Analysis (Optional): You can try adding a bit more about possible causes of the issue based on what you've observed so far.

Future Steps: Add the next troubleshooting steps or actions you plan to take in order to resolve the issue and successfully deploy the pod.

This will help in tracking what has been comp![Screenshot (683)](https://github.com/user-attachments/assets/4e6b24f4-50fd-4ebb-a954-0174f089f668)
