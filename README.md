# Auth API

This is the authentication microservice (`ms-auth-api`) of a distributed TODO application. It is responsible for verifying user credentials and generating JWT access tokens used by other services for secure communication.

---

## 🔗 Project Links

- 📋 [Trello Board](https://trello.com/invite/b/680296aa17864e87fc6c7fed/ATTI82505e108ae3e7a005ede0081ec437f87CDDDEF1/microservice)
- 📄 [Project Documentation](https://docs.google.com/document/d/1FER2lpkZJk2eI5tpMnMy8mFhd42g3f4jioasHwZ0klo/edit?usp=sharing)

---

## Architecture & Deployment

This service is containerized with Docker and deployed to Azure Kubernetes Service (AKS). The image is built and published automatically via GitHub Actions and deployed using Kubernetes manifests.

The following environment variables are required:

- `AUTH_API_PORT` – The port on which the service runs.
- `USERS_API_ADDRESS` – Base URL of the Users API microservice.
- `JWT_SECRET` – Secret used to sign JWT tokens (must be shared with other services).

---

## 📦 Dependencies

| Dependency | Version |
|------------|---------|
| Go         | 1.18.2  |

---

# 🛠️ What Was Added – `ms-auth-api` Microservice

## 🐳 Containerization

A Dockerfile was created to containerize the authentication service using a lightweight Go image. It compiles the Go code, defines runtime environment variables, and exposes the API endpoint.

Hardcoded users were added for authentication testing:

| Username | Password |
|----------|----------|
| admin    | admin    |
| johnd    | foo      |
| janed    | ddd      |

---

## ☸️ Kubernetes Deployment

Two Kubernetes manifests were included:

- **Deployment:** Defines how the auth service is deployed in the cluster using the image from Azure Container Registry.
- **Service:** Exposes the microservice within the cluster using a `ClusterIP`.

---

## 🔁 CI/CD Automation with GitHub Actions

A GitHub Actions workflow automates the build and deployment process when code is pushed to the `main` branch. The workflow performs the following steps:

1. Logs into Azure and the container registry.
2. Builds the Docker image for the auth service.
3. Pushes the image to Azure Container Registry with `latest` and commit hash tags.
4. Applies the Kubernetes manifests.
5. Updates the deployment with the new image version.

This provides consistent and traceable deployments.

---

## 📣 Slack Notification

An additional GitHub Actions workflow was created to send Slack notifications to the `#notificaciones` channel upon pushes to the `main` branch, improving team awareness of changes in the repository.

---

## <b> Made by </b>

+ [Fabiana Valderruten](https://github.com/FFabianna "FFabianna")
+ [Gloria Vicuña](https://github.com/Vanesa155 "Vanesa V.")

[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)
