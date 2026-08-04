<!-- BANNER_START -->
<p align="center">
  <img src="./.banner/banner.svg" width="100%" alt="Project Banner">
</p>
<!-- BANNER_END -->

# DevOps Project 6: Cloud Native Infrastructure

## Cloud Native Infrastructure with EKS, Istio, and GitOps

A production-grade demonstration of Cloud Native architecture on AWS, showcasing Infrastructure as Code, GitOps, and Service Mesh technologies for building scalable and observable microservices applications.

## Table of Contents

1. [About This Project](#about-this-project)
2. [Technologies Used](#technologies-used)
3. [Techniques & Concepts](#techniques--concepts)
4. [Architecture](#architecture)
5. [Prerequisites](#prerequisites)
6. [Getting Started](#getting-started)
7. [Setup Instructions](#setup-instructions)
8. [Observability](#observability)
9. [Verification](#verification)
10. [Screenshots/Visual Reference](#screenshotsvisual-reference)
11. [License](#license)
12. [Author](#author)

## About This Project

This project is built for **learning DevOps, Kubernetes, and Service Mesh** technologies through hands-on implementation. It demonstrates how to build, deploy, and manage a microservices application using industry-standard tools and best practices.

The project orchestrates a sample microservices application (Next.js frontend and Node.js backend) on Amazon EKS, with infrastructure managed via Terraform, continuous deployment via ArgoCD, and traffic management and observability powered by Istio and Kiali.

**Key Learning Objectives:**
- Automate infrastructure provisioning using Infrastructure as Code (IaC)
- Implement GitOps workflows for continuous delivery
- Configure and manage a service mesh for traffic control and security
- Set up observability and monitoring for microservices
- Apply real-world DevOps practices with production-grade tools

> [!NOTE]
> **Live Demo:** A frontend-only deployment is available at [https://devops6.himanm.com](https://devops6.himanm.com) for demonstration purposes. The backend EKS cluster is not connected to this specific instance.

## Technologies Used

![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Amazon EKS](https://img.shields.io/badge/Amazon%20EKS-FF9900?style=for-the-badge&logo=amazon-eks&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![Istio](https://img.shields.io/badge/Istio-466BB0?style=for-the-badge&logo=istio&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)
![Kiali](https://img.shields.io/badge/Kiali-003D4F?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAA7AAAAOwBeShxvQAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAADeSURBVCiRY2CgEPj//z8DlI2NjY0JxgZxgQQDAwMDEwMDAwOQABJgQhYEYhBbGKoYyAZyGRgYGBhANjIwMDAwgAQYQAyoJJANYoO4QDYDAwMDAwMDAwPIRqgkyEagJAgDxSA2iA3iArVhALoApAkkALLRNAK5IDaIzQDSjE0jUBJkI4gN4jJgA8gaoJpAbBAb5CWoRpBGkI1ANggDtUDFsAEGkABUDARowM5lYGBgYIBqRtcIAmgagWyQOFQciIEYqpGBgYGBgQGH72A2gm2EsuFiODQyMDAAgZSKfwBTcz0F9QQAAAAASUVORK5CYII=&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)

**Technology Descriptions:**

- **AWS EKS (Elastic Kubernetes Service)**: Managed Kubernetes service that simplifies running Kubernetes on AWS without needing to install and operate your own Kubernetes control plane
- **Terraform**: Infrastructure as Code tool for building, changing, and versioning infrastructure safely and efficiently across multiple cloud providers
- **Istio**: Open-source service mesh that provides traffic management, security, and observability for microservices with minimal code changes
- **ArgoCD**: Declarative GitOps continuous delivery tool for Kubernetes that automates application deployment and lifecycle management
- **Kiali**: Management console for Istio service mesh that provides visibility into the structure and health of your service mesh
- **GitHub Actions**: CI/CD platform that automates build, test, and deployment pipelines directly from GitHub repositories
- **Next.js**: React framework for building server-side rendered and static web applications
- **Node.js**: JavaScript runtime for building scalable network applications and microservices

## Techniques & Concepts

This project demonstrates the following DevOps techniques and concepts:

- **Infrastructure as Code (IaC)**: Automated provisioning of AWS infrastructure (VPC, subnets, EKS cluster, IAM roles, security groups) using Terraform for reproducible and version-controlled infrastructure
- **GitOps**: Declarative application management where Git serves as the single source of truth, with ArgoCD automatically syncing cluster state to match the desired state in the repository
- **Service Mesh**: Implementation of Istio for advanced traffic management, load balancing, service-to-service authentication, and authorization without modifying application code
- **Traffic Management**: Fine-grained control over traffic routing, retries, failovers, and circuit breaking using Istio VirtualServices and DestinationRules
- **Observability**: Comprehensive monitoring and visualization of service mesh topology, traffic flow, and application metrics using Kiali dashboards
- **Continuous Integration/Continuous Deployment (CI/CD)**: Automated build and deployment pipelines using GitHub Actions to build Docker images and push them to container registries
- **Container Orchestration**: Managing containerized microservices at scale using Kubernetes for automated deployment, scaling, and management
- **Security Best Practices**: Network segmentation, security groups, IAM roles, and service mesh security policies for defense-in-depth
- **High Availability**: Auto-scaling groups, load balancing, and multi-AZ deployment for resilient infrastructure
- **Cloud Native Architecture**: Microservices design patterns following 12-factor app principles for building cloud-native applications

## Architecture

The system follows a modern cloud-native architecture with multiple layers of abstraction and security.

### System Architecture Overview

The application is deployed on Amazon EKS (Elastic Kubernetes Service) with the following components:
- **VPC and Networking**: Custom VPC with public and private subnets across multiple availability zones
- **EKS Cluster**: Managed Kubernetes control plane with worker nodes running on EC2 instances
- **Service Mesh**: Istio deployed for traffic management, security, and observability
- **GitOps**: ArgoCD monitoring the Git repository and automatically syncing changes to the cluster
- **CI/CD**: GitHub Actions building Docker images and updating Kubernetes manifests
- **Load Balancing**: AWS Application Load Balancer (ALB) distributing traffic to Istio Ingress Gateway

### Request Flow

1. **User Request**: A user sends an HTTP request which enters the AWS infrastructure via an Application Load Balancer (ALB) that provides external access and TLS termination
2. **Ingress Gateway**: The ALB forwards the request to the Istio Ingress Gateway running in the `istio-system` namespace, which acts as the entry point to the service mesh
3. **Traffic Routing**: Istio VirtualServices evaluate the request path and headers, then route the traffic to the appropriate Kubernetes Service (frontend or backend) based on configured rules
4. **Service Mesh Proxy**: Each microservice pod has an Envoy sidecar proxy injected by Istio that intercepts all inbound and outbound traffic, enforcing security policies and collecting telemetry data
5. **Pod Execution**: The request reaches the application container (Next.js frontend or Node.js backend) running inside a Kubernetes Pod on an EKS worker node (EC2 instance)
6. **Inter-service Communication**: When the frontend needs to call the backend, the request flows through the Envoy sidecars, which handle load balancing, retries, circuit breaking, and mutual TLS authentication
7. **Response Path**: The response travels back through the same layers (pod → sidecar → service → ingress gateway → ALB) to the user
8. **Observability**: Throughout this flow, Istio collects metrics, traces, and logs that are visualized in Kiali for real-time monitoring of service mesh health and performance

## Prerequisites

Before you begin, ensure you have the following tools installed and configured on your local machine:

- **[AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)**: Command-line tool for interacting with AWS services. Configure it with `aws configure` using your AWS credentials, default region, and output format.
- **[Terraform](https://developer.hashicorp.com/terraform/downloads)**: Infrastructure as Code tool (version 1.0 or later) for provisioning AWS resources. Download and add to your system PATH.
- **[kubectl](https://kubernetes.io/docs/tasks/tools/)**: Kubernetes command-line tool for managing cluster resources. Must match or be within one minor version of your cluster version.
- **[Docker](https://docs.docker.com/get-docker/)**: Container platform for building and running containerized applications (required for manual image builds).
- **[ArgoCD CLI](https://argo-cd.readthedocs.io/en/stable/cli_installation/)**: Command-line tool for managing ArgoCD applications (required if using GitOps deployment).

**AWS Account Requirements:**
- An active AWS account with appropriate IAM permissions
- IAM user or role with permissions to create EKS clusters, VPCs, EC2 instances, and related resources (see `IAM_POLICY.json` for detailed permissions)
- AWS credentials configured locally via `aws configure` or environment variables

> [!IMPORTANT]
> For AWS IAM configuration, you can use the provided `IAM_POLICY.json` file to create a custom policy with the minimum required permissions. Alternatively, for testing purposes, you may use `AdministratorAccess` managed policy, though this is not recommended for production environments.

## Getting Started

To replicate this project locally, follow these steps:

### Clone the Repository

```bash
# Clone the repository to your local machine
git clone https://github.com/HimanM/kubernetes-gitops-servicemesh-demo.git

# Navigate into the project directory
cd kubernetes-gitops-servicemesh-demo
```

### Repository Structure

```
.
├── terraform/          # Infrastructure as Code definitions
│   ├── main.tf        # Main Terraform configuration
│   ├── variables.tf   # Variable definitions
│   └── outputs.tf     # Output values
├── manifests/         # Kubernetes manifests for application deployment
│   ├── namespace.yaml
│   ├── deployment.yaml
│   ├── service.yaml
│   └── istio-*.yaml
├── frontend/          # Next.js frontend application source code
├── backend/           # Node.js backend application source code
├── .github/workflows/ # CI/CD pipeline definitions
├── .docs/            # Documentation and screenshots
└── README.md         # Project documentation
```

## Setup Instructions

Follow these step-by-step instructions to deploy the entire infrastructure and application.

### Step 1: AWS IAM Configuration

Configure the necessary AWS IAM permissions for Terraform to provision resources.

**Option A: Custom Policy (Recommended)**
```bash
# Create an IAM policy using the provided policy document
aws iam create-policy \
  --policy-name EKS-Terraform-Policy \
  --policy-document file://IAM_POLICY.json

# Attach the policy to your IAM user
aws iam attach-user-policy \
  --user-name YOUR_IAM_USERNAME \
  --policy-arn arn:aws:iam::YOUR_ACCOUNT_ID:policy/EKS-Terraform-Policy
```

**What this does:** Creates a least-privilege IAM policy that grants only the permissions needed for Terraform to create EKS clusters, VPCs, security groups, and related AWS resources.

**Option B: Administrator Access (Testing Only)**
```bash
# Attach AdministratorAccess for full AWS permissions
aws iam attach-user-policy \
  --user-name YOUR_IAM_USERNAME \
  --policy-arn arn:aws:iam::aws:policy/AdministratorAccess
```

**What this does:** Grants full administrative access to your AWS account. Use only for testing/development environments.

### Step 2: Build and Push Docker Images

The application uses GitHub Actions for automated CI/CD. When you push code changes, images are automatically built and pushed to GitHub Container Registry (GHCR).

**Automated Build (Recommended)**
```bash
# Make any change to trigger the CI/CD pipeline
git add .
git commit -m "Trigger CI/CD pipeline"
git push origin main
```

**What this does:** Triggers the GitHub Actions workflow defined in `.github/workflows/ci-cd.yml`, which builds Docker images for both frontend and backend, tags them with the commit SHA, pushes them to GHCR, and updates the Kubernetes manifests with the new image tags.

**Manual Build (Optional)**

If you need to build and push images manually:

```bash
# Build frontend Docker image
docker build -t ghcr.io/YOUR_USERNAME/kubernetes-gitops-servicemesh-demo/frontend:latest ./frontend

# Push frontend image to registry
docker push ghcr.io/YOUR_USERNAME/kubernetes-gitops-servicemesh-demo/frontend:latest

# Build backend Docker image
docker build -t ghcr.io/YOUR_USERNAME/kubernetes-gitops-servicemesh-demo/backend:latest ./backend

# Push backend image to registry
docker push ghcr.io/YOUR_USERNAME/kubernetes-gitops-servicemesh-demo/backend:latest
```

**What this does:** Builds Docker images locally from the Dockerfiles in the frontend and backend directories, tags them with your username and version, and pushes them to GitHub Container Registry for deployment.

### Step 3: Provision Infrastructure with Terraform

Use Terraform to create all AWS infrastructure including VPC, subnets, EKS cluster, and node groups.

```bash
# Navigate to the terraform directory
cd terraform

# Initialize Terraform and download required providers
terraform init

# Review the planned changes before applying
terraform plan

# Apply the Terraform configuration to create infrastructure
terraform apply
```

**What this does:** 
- `terraform init`: Downloads the AWS provider plugin and initializes the backend for state storage
- `terraform plan`: Shows a preview of all resources that will be created, modified, or destroyed
- `terraform apply`: Creates the VPC with public/private subnets, EKS cluster with managed node groups, IAM roles, security groups, and installs Istio and Kiali using Helm

> [!NOTE]
> The infrastructure provisioning process takes approximately 15-20 minutes to complete. You will be prompted to type 'yes' to confirm the apply operation.

### Step 4: Configure kubectl

After Terraform completes, configure kubectl to communicate with your new EKS cluster.

```bash
# Update kubeconfig to add the new EKS cluster context
aws eks update-kubeconfig --region us-west-2 --name learn-eks-sm-cluster
```

**What this does:** Adds the EKS cluster credentials to your `~/.kube/config` file, allowing kubectl commands to authenticate and interact with the cluster. Replace `us-west-2` with your region and `learn-eks-sm-cluster` with your cluster name if different.

**Verify cluster access:**
```bash
# Check cluster connection
kubectl cluster-info

# List all nodes in the cluster
kubectl get nodes
```

### Step 5: Deploy Applications

Deploy the application manifests to the Kubernetes cluster.

```bash
# Return to the project root directory
cd ../

# Create the application namespace
kubectl apply -f manifests/namespace.yaml

# Deploy all application resources
kubectl apply -f manifests/
```

**What this does:**
- Creates a dedicated Kubernetes namespace for the application resources
- Deploys the frontend and backend Deployments with specified container images
- Creates Services for internal communication between pods
- Configures Istio Gateway and VirtualServices for external traffic routing
- Sets up DestinationRules for traffic policies

### Step 6: Configure ArgoCD for GitOps (Optional)

If you want to use ArgoCD for continuous delivery, add your EKS cluster to ArgoCD.

```bash
# Login to ArgoCD (if not already logged in)
argocd login YOUR_ARGOCD_SERVER

# Add the EKS cluster to ArgoCD
argocd cluster add arn:aws:eks:us-west-2:YOUR_ACCOUNT_ID:cluster/learn-eks-sm-cluster

# Create an ArgoCD application
argocd app create kubernetes-gitops-servicemesh-demo \
  --repo https://github.com/HimanM/kubernetes-gitops-servicemesh-demo.git \
  --path manifests \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace default
```

**What this does:** Registers your EKS cluster with ArgoCD and creates an Application that monitors the `manifests/` directory in your Git repository. When you push changes to manifests, ArgoCD automatically detects the drift and syncs the cluster state to match the desired state in Git.

### Step 7: Access the Application

Retrieve the external load balancer URL to access your application.

```bash
# Get the external IP/hostname of the Istio Ingress Gateway
kubectl get svc -n istio-system istio-ingressgateway

# Watch for the EXTERNAL-IP to be assigned (may take a few minutes)
kubectl get svc -n istio-system istio-ingressgateway -w
```

**What this does:** Retrieves the AWS Application Load Balancer DNS name that serves as the entry point to your application. Copy the `EXTERNAL-IP` value and open it in your web browser to access the frontend application.

> [!TIP]
> If the EXTERNAL-IP shows `<pending>`, wait a few minutes for AWS to provision the load balancer. The `-w` flag watches for changes in real-time.

## Observability

Kiali provides a powerful web-based console for visualizing and managing the Istio service mesh.

### Accessing Kiali Dashboard

To access the Kiali dashboard, use kubectl port-forwarding:

```bash
# Forward local port 20001 to the Kiali service
kubectl port-forward svc/kiali -n istio-system 20001:20001 --address 0.0.0.0
```

**What this does:** Creates a secure tunnel from your local machine to the Kiali service running in the cluster, making the dashboard accessible at `http://localhost:20001` in your web browser.

### Kiali Features

**Service Mesh Topology**: Visualize the graph of all services, including traffic flow, request rates, error rates, and latency between services

**Traffic Management**: Monitor how Istio routes traffic between service versions, view load balancing algorithms, and observe traffic splitting for canary deployments

**Health Monitoring**: Check the health status of services, workloads, and applications with real-time metrics and alerts

**Configuration Validation**: Validate Istio configuration objects (VirtualServices, DestinationRules, Gateways) for syntax errors and best practices

**Distributed Tracing**: View request traces across microservices to identify performance bottlenecks and debug issues

> [!NOTE]
> Keep the port-forward command running while you use the Kiali dashboard. Press Ctrl+C to stop the tunnel when finished.

### Monitoring Setup

The project includes Istio's telemetry components that collect:
- **Metrics**: Request rates, error rates, and latency (P50, P95, P99)
- **Traces**: Distributed traces showing request paths across services
- **Logs**: Application and proxy logs for debugging

These metrics are visualized in Kiali and can be exported to external monitoring systems like Prometheus and Grafana for long-term storage and alerting.

## Verification

Verify that your deployment is working correctly by checking the status of Kubernetes resources.

### Check Cluster Resources

```bash
# View all namespaces in the cluster
kubectl get namespaces

# Check pods in the default namespace
kubectl get pods

# Check all pods in the istio-system namespace
kubectl get pods -n istio-system

# View services and their endpoints
kubectl get svc --all-namespaces

# Check deployment status
kubectl get deployments
```

**What to verify:**
- All pods should be in `Running` state
- Istio control plane pods (istiod, istio-ingressgateway) should be healthy
- Application pods should show 2/2 containers (app + Envoy sidecar)
- Services should have valid ClusterIP and/or LoadBalancer addresses

### Check Application Health

```bash
# Describe a specific pod for detailed information
kubectl describe pod POD_NAME

# View logs from the frontend application
kubectl logs -l app=frontend -c frontend

# View logs from the backend application
kubectl logs -l app=backend -c backend

# Check Istio sidecar injection
kubectl get pod POD_NAME -o jsonpath='{.spec.containers[*].name}'
```

### Test Application Endpoints

```bash
# Get the load balancer URL
INGRESS_HOST=$(kubectl get svc istio-ingressgateway -n istio-system -o jsonpath='{.status.loadBalancer.ingress[0].hostname}')

# Test frontend endpoint
curl http://$INGRESS_HOST

# Test backend endpoint
curl http://$INGRESS_HOST/api/health
```

## Screenshots/Visual Reference

This section includes all visual documentation and screenshots demonstrating the deployed infrastructure and application.

### Infrastructure Provisioning

**Terraform Apply Outputs:**
![Terraform Apply Outputs](.docs/tf_apply_outputs.png)
*Output from Terraform showing successfully created resources including VPC, subnets, EKS cluster, and node groups*

**EKS Cluster:**
![EKS Cluster](.docs/eks_cluster.png)
*AWS EKS console showing the active Kubernetes cluster with version, status, and endpoint information*

**EC2 Instances for EKS Cluster:**
![EC2 Instances](.docs/ec2_instances_of_eks_cluster.png)
*EC2 console displaying the worker nodes running as part of the EKS managed node group*

**EKS Cluster Networking:**
![EKS Networking](.docs/eks_cluster_networking.png)
*VPC and subnet configuration showing public and private subnets across availability zones*

**Security Groups:**
![Security Groups](.docs/sequiry_groups_for_project.png)
*AWS security groups configured for the EKS cluster controlling inbound and outbound traffic rules*

**Auto Scaling Groups:**
![Auto Scaling Groups](.docs/auto_scaling_groups.png)
*Auto Scaling Group configuration managing the desired, minimum, and maximum number of worker nodes*

### CI/CD Pipeline

**GitHub Actions Pipeline:**
![CI CD Pipeline](.docs/ci_cd_pipeline.png)
*GitHub Actions workflow executing the CI/CD pipeline for building and pushing Docker images*

**GitHub Container Registry:**
![GitHub Packages](.docs/github_packages_images.png)
*GitHub Packages showing the published Docker images for frontend and backend with version tags*

### GitOps with ArgoCD

**ArgoCD Application Overview:**
![ArgoCD Overview](.docs/argocd_application_overview.png)
*ArgoCD dashboard showing all applications and their sync status with the Git repository*

**ArgoCD Application Details:**
![ArgoCD Details](.docs/argocd_application_details.png)
*Detailed view of a specific application including health status, sync status, and deployed resources*

**ArgoCD Sync Status:**
![ArgoCD Sync Status](.docs/argocd_application_application_sync_status.png)
*Application sync status showing Git revision, commit message, and synchronized Kubernetes resources*

### Traffic Management

**Load Balancer for Istio:**
![Load Balancer](.docs/load_balancer_for_Istio.png)
*AWS Application Load Balancer providing external access to the Istio Ingress Gateway*

**Target Groups:**
![Target Groups](.docs/target_groups.png)
*ALB target groups showing registered instances and health check configuration*

**Istio Status:**
![Istio Status](.docs/istio.png)
*Istio control plane status showing the service mesh components and their health*

**Running Application Frontend:**
![Running Frontend](.docs/running_application_frontend.png)
*Live frontend application accessible through the load balancer demonstrating successful deployment*

### Observability with Kiali

**Kiali Service Mesh Graph:**
![Kiali Mesh](.docs/kiali_mesh.png)
*Kiali's graph visualization showing service-to-service communication patterns and traffic flow*

**Kiali Overview:**
![Kiali Overview](.docs/kiali_overview.png)
*Kiali dashboard overview displaying applications, workloads, services, and their health status*

### Verification

**Namespace Details (CLI):**
![CLI Output](.docs/namespace_details_cli.png)
*Command-line output showing Kubernetes resources deployed in the namespace including pods, services, and deployments*

## License

This project is open source and available for educational purposes. Feel free to use, modify, and distribute this project for learning and non-commercial purposes.

## Author

**Himan Manduja**

- GitHub: [@HimanM](https://github.com/HimanM)
- Website: [himanm.com](https://himanm.com)
- Project Demo: [devops6.himanm.com](https://devops6.himanm.com)

For questions, suggestions, or collaboration opportunities, please open an issue in this repository or reach out through the contact information above.
