Kubernetes Orchestration on Google Cloud Platform (GCP) with IP Addresses

This guide explains how to deploy and manage containerized applications using Kubernetes on Google Cloud Platform (GCP). It focuses on understanding IP address usage and the reasoning behind specific configuration choices. 

Prerequisites:

    Google Cloud SDK (gcloud): Ensure you have gcloud installed and configured on your local machine.
    Kubernetes Engine API: Verify the Kubernetes Engine API is enabled in your GCP project.

Deployment Steps:

    Create a Cluster:

    Run the following command in your Cloud Shell to create a Kubernetes cluster named yolo-project in the us-central1 region with 2 nodes:

    gcloud container clusters create yolo-project --region us-central1 --num-nodes 2

    Authenticate with GKE Cluster:

    Authenticate your local machine with the newly created cluster using:

    gcloud container clusters get-credentials yolo-project --region us-central1

    Create Namespaces:

    Create separate namespaces for the backend and client applications using kubectl:

    kubectl create namespace backend
    kubectl create namespace client

    Deploy Applications:

    Apply the deployment manifests (backend-deployment.yaml and client-deployment.yaml) to deploy the applications to their respective namespaces:

    kubectl apply -f backend-deployment.yaml -n backend
    kubectl apply -f client-deployment.yaml -n client

    Expose Applications (Services):

    Apply the service manifests (backend-service.yaml and client-service.yaml) to expose the deployed applications:

    kubectl apply -f backend-service.yaml -n backend
    kubectl apply -f client-service.yaml -n client

    Verify Deployment:

        Deployment Status:

        Use kubectl get deployments -n <namespace> (replace <namespace> with the desired namespace) to check if deployments are running with the expected number of replicas.

        Pod Status:

        Use kubectl get pods -n <namespace> to view the status of individual pods within each deployment.