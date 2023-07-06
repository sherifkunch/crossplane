# Platform Engineering Project

This project aims to create a robust platform using various tools and technologies such as Crossplane, Kubernetes (k8s) cluster, Argo CD, Getport.io, and more. The platform will enable teams to efficiently manage and deploy their applications with ease.

## Project Overview

The main goal of this project is to build a platform that provides a streamlined and standardized approach to deploying applications on Kubernetes. By utilizing Crossplane, we can abstract the underlying infrastructure and create a self-service model for teams to provision and manage their resources.

## Tools and Technologies

The project utilizes the following tools and technologies:

1. **Crossplane**: Crossplane is an open-source Kubernetes add-on that extends the capabilities of Kubernetes, enabling teams to provision and manage cloud resources through the Kubernetes API. It provides a declarative API for defining and managing infrastructure resources.

2. **Kubernetes Cluster**: A Kubernetes cluster will be set up to provide the underlying infrastructure for hosting applications. Kubernetes provides scalable and resilient infrastructure management, ensuring high availability and fault tolerance.

3. **Argo CD**: Argo CD is a continuous delivery tool that automates the deployment of applications on Kubernetes. It allows teams to manage and track changes in their applications and ensures that the deployed applications match the desired state defined in Git repositories.

4. **Getport.io**: Getport.io is a tool that simplifies the process of exposing applications running on Kubernetes clusters. It provides a secure and customizable domain for accessing applications, making it easier to share and access deployed services.

## Project Setup

To set up and deploy the platform, follow these steps:

1. Clone the repository:

   ```bash
   git clone <repository-url>
   ```

2. Install and configure the required tools:

   - Install Crossplane by following the installation instructions provided in their documentation.
   - Set up a Kubernetes cluster using a cloud provider or a local cluster like Minikube.
   - Install Argo CD by following the installation instructions provided in their documentation.
   - Register an account on Getport.io and configure the necessary DNS settings for your domain.

3. Configure Crossplane:

   - Define the required infrastructure resources (e.g., virtual machines, databases, storage) using Crossplane's declarative API. Store these definitions in a Git repository for version control.

4. Configure Argo CD:

   - Define the application deployment manifests using GitOps principles. Store these manifests in a Git repository.

5. Deploy the platform:

   - Use Argo CD to deploy the platform by pointing it to the Git repository containing the application deployment manifests.
   - Argo CD will automatically synchronize the deployed applications with the desired state defined in the Git repository.

6. Expose the applications:

   - Use Getport.io to expose the deployed applications securely.
   - Configure the necessary domain settings in Getport.io to map the applications to custom domains.

