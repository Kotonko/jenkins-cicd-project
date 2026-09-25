# Automated Jenkins CI/CD Pipeline Architecture 🚀

This repository houses an enterprise-grade Declarative Pipeline (`Jenkinsfile`) integrated with Node.js unit testing matrices and Docker containerization stages.

---

## 🛠️ Jenkins Server Setup & Configuration Guide

### 1️⃣ Core System Prerequisites
*   Ensure **Java Runtime Environment (JRE/JDK 11 or 17)** is provisioned on the host.
*   Install the native **Docker Engine** and ensure the `jenkins` user is added to the docker system group (`sudo usermod -aG docker jenkins`).

### 2️⃣ Required Plugin Footprint
Install the following core plugins via the Jenkins Plugin Dashboard Management panel:
*   `Pipeline` / `Git Plugin`
*   `Credentials Binding Plugin` (Secures access tokens natively)
*   `Docker Pipeline`

### 3️⃣ Pipeline Triggers & Webhook Automation
To enable real-time continuous integration code integration execution, configure an automated trigger under your Jenkins Job dashboard settings:
*   Check **Build Triggers** -> **GitHub hook trigger for GITScm polling**.
*   In your GitHub repository settings, configure a webhook pointing to: `http://YOUR_JENKINS_IP:8080/github-webhook/` with the payload event type set to `application/json`.

---

## 🔐 Cryptographic Credentials Security Model
Secrets are never hardcoded inside source arrays. The pipeline binds tokens securely using Jenkins' native context framework:
```groovy
environment {
    DOCKER_CREDS = credentials('docker-hub-credentials')
}
```
This isolates username and password fields into protected, hidden system memory strings (`$DOCKER_CREDS_USR` and `$DOCKER_CREDS_PSW`) to block logging leaks.
