# Cloud-Native Microservices Infrastructure

**Kubernetes | Docker | Google Cloud (GKE) | GitHub Actions | Kustomize | PostgreSQL | NATS | Node.js**

A cloud-native infrastructure project exploring the deployment, orchestration, and operation of containerized microservices using Kubernetes.

The project was developed during university coursework and evolved into a practical environment for experimenting with distributed applications, persistent storage, asynchronous messaging, automated deployments, and observability.

The main focus is on **infrastructure and service orchestration**, rather than building a feature-complete application.

## Project Overview

The repository contains several containerized applications and supporting Kubernetes infrastructure.

The main application is a distributed Todo system consisting of a frontend, backend API, PostgreSQL database, NATS message broker, and a separate event-processing service.

Additional applications are used to explore Kubernetes networking, persistent storage, service communication, deployment strategies, and operational tooling.

The project also includes configuration for deployment to Google Kubernetes Engine (GKE) and automated container image management using GitHub Actions.

## Architecture

The Todo application demonstrates a combination of synchronous and asynchronous service communication.

### Main Components

- **Frontend:** Node.js application providing the user interface.
- **Backend:** REST API responsible for Todo operations and database access.
- **PostgreSQL:** Persistent storage for application data.
- **NATS:** Message broker for asynchronous event communication.
- **Broadcaster:** Independent service consuming events and sending webhook notifications.
- **Kubernetes:** Container orchestration, service discovery, networking, and resource management.

The backend handles application requests and stores data in PostgreSQL. Application events are published through NATS and processed independently by the broadcaster service.

This architecture demonstrates the separation of application responsibilities and the use of asynchronous communication to reduce direct dependencies between services.

## Technologies and Concepts

| Area | Technologies / Concepts |
|---|---|
| Containerization | Docker |
| Orchestration | Kubernetes |
| Cloud infrastructure | Google Cloud, GKE |
| CI/CD | GitHub Actions |
| Deployment configuration | Kustomize, Kubernetes manifests |
| Application development | Node.js, JavaScript |
| Database | PostgreSQL |
| Messaging | NATS |
| Observability | Prometheus, Grafana, Loki |
| Progressive delivery | Argo Rollouts |
| Networking | Kubernetes Services, Ingress, Gateway API |

## Infrastructure and Deployment

### Kubernetes Resources

The repository includes Kubernetes configuration for:

- Deployments and StatefulSets
- Services and application routing
- Persistent Volumes and Persistent Volume Claims
- ConfigMaps and application configuration
- Scheduled workloads using CronJobs
- Container health and lifecycle management

### Google Cloud

The project includes a deployment workflow targeting Google Kubernetes Engine.

The workflow uses GitHub Actions to build container images, publish them to Google Artifact Registry, and apply Kubernetes configuration using Kustomize.

Google Cloud Workload Identity is used in the workflow configuration for authentication.

### CI/CD

GitHub Actions workflows automate parts of the build and deployment process, including container image publishing and Kubernetes configuration updates.

The repository also contains GitOps-oriented workflows for managing application image versions.

### Monitoring and Observability

Configuration files for Prometheus, Grafana, and Loki are included to explore metrics collection, visualization, and centralized logging in Kubernetes environments.

### Deployment Strategies

The repository includes examples of progressive delivery using Argo Rollouts, including canary deployment and analysis configuration.

## Repository Structure

```text
.github/workflows/   CI/CD and deployment automation
todo/                Main microservices application
log-output/          Logging and service communication examples
monitoring/          Observability configuration
storage2/            Persistent storage experiments
wikipedia/           Additional Kubernetes deployment example
screenshots/         Deployment and exercise evidence
```

## Engineering Challenges

Several aspects of the project provided practical experience with cloud-native application development.

### Service Communication

Combining REST APIs with asynchronous messaging through NATS.
