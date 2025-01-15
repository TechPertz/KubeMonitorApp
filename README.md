# KubeMonitorApp  
A Flask-MongoDB-based web application deployed using Docker and Kubernetes, showcasing advanced features like replication, rolling updates, health probes, and real-time alerting with Prometheus and Slack.

## Table of Contents  
1. [Introduction](#introduction)  
2. [Features](#features)  
3. [Technologies Used](#technologies-used)  
4. [Setup Instructions](#setup-instructions)  
5. [Deployment](#deployment)  
    - [Local Deployment with Minikube](#local-deployment-with-minikube)  
    - [Cloud Deployment with AWS EKS](#cloud-deployment-with-aws-eks)  
6. [Monitoring and Alerting](#monitoring-and-alerting)  
7. [Results](#results)  
8. [Contributing](#contributing)  
9. [License](#license)  

## Introduction  
**KubeMonitorApp** demonstrates the power of containerized deployments with Docker and Kubernetes. The project involves a Flask-based backend connected to MongoDB for persistent data storage. It showcases modern cloud-native practices like scaling, health monitoring, rolling updates, and real-time alerting.

## Features  
- **Containerization**: Flask-MongoDB app containerized using Docker.  
- **Kubernetes Deployment**: Configured with replication, rolling updates, and health monitoring.  
- **Local Deployment**: Deployed locally using Minikube for development and testing.  
- **Cloud Deployment**: Scaled and hosted on AWS EKS for production-grade infrastructure.  
- **Monitoring and Alerting**: Integrated Prometheus for health checks and Slack for real-time alerts.  

## Technologies Used  
- **Backend**: Flask  
- **Database**: MongoDB  
- **Containerization**: Docker  
- **Orchestration**: Kubernetes (Minikube, AWS EKS)  
- **Monitoring**: Prometheus, Slack  
- **Version Control**: Git  

## Setup Instructions  

### Prerequisites  
- Docker and Docker Compose installed  
- Minikube and kubectl installed  
- AWS account with CLI configured  
- Docker Hub account  

### 1. Clone the Repository  
```bash  
git clone https://github.com/yourusername/KubeMonitorApp.git  
cd KubeMonitorApp  
```  

### 2. Containerize the Application  
- Build the Flask app Docker image:  
```bash  
docker build -t yourdockerhubusername/kubemonitorapp:latest .  
```  
- Test locally with Docker Compose:  
```bash  
docker-compose up  
```  
- Push the Docker image to Docker Hub:  
```bash  
docker push yourdockerhubusername/kubemonitorapp:latest  
```  

## Deployment  

### Local Deployment with Minikube  
1. Start Minikube:  
```bash  
minikube start  
```  
2. Apply Kubernetes configurations:  
```bash  
kubectl apply -f kubernetes/deployment.yaml  
kubectl apply -f kubernetes/service.yaml  
```  
3. Access the application:  
```bash  
minikube service flask-service  
```  

### Cloud Deployment with AWS EKS  
1. Create an EKS cluster via AWS Console or CLI.  
2. Configure kubectl for EKS:  
```bash  
aws eks update-kubeconfig --region your-region --name your-cluster-name  
```  
3. Deploy the application:  
```bash  
kubectl apply -f kubernetes/deployment.yaml  
kubectl apply -f kubernetes/service.yaml  
```  
4. Verify the deployment:  
```bash  
kubectl get pods  
kubectl get services  
```  

## Monitoring and Alerting  
1. **Prometheus Setup**:  
- Deploy Prometheus:  
```bash  
kubectl apply -f monitoring/prometheus-deployment.yaml  
```  
- Access Prometheus Dashboard:  
```bash  
kubectl port-forward prometheus-pod-name 9090:9090  
```  

2. **Slack Alerts**:  
- Configure Slack Webhook in Prometheus Alert Manager.  
- Test alerts by simulating a failure (e.g., deleting a pod):  
```bash  
kubectl delete pod pod-name  
```  

## Results  
- Application deployed with replication, rolling updates, and health monitoring.  
- Real-time alerts sent via Slack for pod failures or health probe issues.  
- Seamless scaling from local Minikube to AWS EKS.  

## Contributing  
Contributions are welcome! Please open an issue or submit a pull request for any improvements.  

## License  
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.