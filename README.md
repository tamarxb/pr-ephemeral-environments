# PR Pipeline – FastAPI on Kubernetes (kind) with GitHub Actions

This project demonstrates a **Pull Request (PR) pipeline** that validates a FastAPI application by building a Docker image, deploying it to a temporary Kubernetes cluster (using **kind**), and running health checks - all automatically via **GitHub Actions**.

The goal is to simulate a real-world CI/CD flow where code is verified in a production-like environment **before merge**.

What This Project Demonstrates

- Building a Docker image for a FastAPI application
- Running Kubernetes locally using **kind (Kubernetes in Docker)**
- Deploying an application to Kubernetes using a **Deployment**
- Verifying application health via HTTP endpoint
- Automating the entire flow using **GitHub Actions**
- Simulating a real PR validation pipeline used in DevOps teams
