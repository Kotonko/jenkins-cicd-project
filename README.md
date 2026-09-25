# Automated Jenkins CI/CD Pipeline Infrastructure 🚀

This repository contains a professional declarative pipeline configuration (`Jenkinsfile`) designed to establish continuous integration paradigms. It shifts deployment patterns away from manual execution toward a fully automated, real-time code verification lifecycle.

## 📁 Repository Structural Components
*   `Jenkinsfile`: Master script tracking declarative Pipeline-as-Code execution rules.
*   `src/app.js`: Target core service entry source code artifact.

## 🛠️ Automated CI/CD Pipeline Blueprint
The pipeline orchestrates application code verification sequentially across four operational phases:
1.  **Fetch Source Code**: Automated checkout loop verifying branch availability.
2.  **Execute Code Compilation**: Provisions workspace directories and creates a persistent compilation log build manifest.
3.  **Run Package Unit Tests**: Triggers unit test validations to enforce testing metrics, failing the pipeline if violations are detected.
4.  **Package Release Distributable**: Bundles all verified files into a compressed production release tarball archive (`.tar.gz`) for deployment consistency.

## 🧹 Post-Execution Life Cycle Guardrails
A defensive `post` engine monitors execution paths:
*   `always`: Triggers clean-up routines to scrub intermediate directories from disk storage layout.
*   `success` / `failure`: Returns status logs directly to the Jenkins build view console.
