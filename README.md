
# 🚀 Vendor Onboarding Microservice

A Spring Boot-based microservice designed to automate and streamline the vendor onboarding process. This service provides secure file uploads, SFTP integration, database interactions, and is fully containerized and cloud-ready with CI/CD support on Azure.

---

## 📌 Features

- RESTful APIs for vendor onboarding and file handling
- File upload handling using Spring Multipart
- Secure SFTP communication using JSch
- Tracks onboarding process using external tracking URLs
- Configurable via environment-specific Helm charts
- Dockerized and deployed via Azure Pipelines

---

## 🏗️ Tech Stack

| Layer               | Tech Used                                |
|--------------------|-------------------------------------------|
| Language           | Java 21                                   |
| Framework          | Spring Boot, Spring Web, Spring Config    |
| File Upload        | Spring Multipart                          |
| SFTP Integration   | JSch (Java Secure Channel)                |
| CI/CD              | Azure DevOps + Helm + Docker              |
| Deployment         | Kubernetes on Azure (AKS)                 |
| Monitoring         | Prometheus PodMonitor (Helm)              |
| Logging            | Logback                                    |
| Config Management  | YAML-based, env-specific Helm overrides   |

---

## 📂 Project Structure

```

vendor-onboarding/
│
├── src/main/java/                    # Core Java logic (controllers, services)
│
├── src/main/resources/
│   ├── application.yml              # Global Spring Boot config
│   ├── logback.xml                  # Log configuration
│   └── scripts/
│       └── voa\_bulk\_upload.ksh      # Shell script for bulk onboarding
│
├── charts/vendoronboarding/
│   ├── configFiles/env/             # Env-specific Helm override files
│   ├── templates/                   # Helm templates for K8s manifests
│   ├── Chart.yaml                   # Helm metadata
│   └── values.yaml                  # Helm default values
│
├── qualitygate/
│   ├── pr-qualitygate.properties    # PR-specific quality rules
│   └── qualitygate.properties       # Code quality configs (for SonarQube, Veracode, etc)
│
├── azure-pipeline.yml               # Azure DevOps CI/CD pipeline
├── Dockerfile                       # Builds microservice Docker image
├── pom.xml                          # Maven build config
├── README.md                        # You're reading it 😊
└── ...

```

---

## 🔄 Data Flow (See Diagram)

1. Vendor uploads data via REST API (HTTP/HTTPS)
2. Data is validated and stored in DB
3. Files are pushed to an SFTP server (via JSch)
4. Tracking URLs monitor onboarding progress
5. Service is deployed to Azure using Helm & Azure DevOps

---

## 🚢 Deployment (CI/CD Overview)

- CI: Automated build, test & sonar checks via Azure Pipeline
- CD: Docker image pushed to Azure Container Registry
- Deployed to Azure Kubernetes Service (AKS) using Helm
- Each environment (dev, uat, prod) has a separate YAML override in Helm

---

## 🛡️ Security

- Secrets and credentials are passed via environment variables or Azure Key Vault (best practice)
- SFTP credentials securely handled using `JSchConfig.java`

---

## 🧪 Testing

- JUnit + Mockito for unit testing
- YAML config for test-specific profiles
- Test coverage enforced via qualitygate rules

---

## 📈 Monitoring & Logging

- Logback for application logs (configurable via `logback.xml`)
- Prometheus integration via `podmonitor.yaml` (Helm)
- Health and readiness probes configured

---

## 🧑‍💻 Author

Deep Kushwaha  
Backend Java Developer | Spring Boot | Cloud-Native Dev  
Client: AT&T via Tech Mahindra  
📍 Pune, India 

---

## 📎 License

This is a proprietary project developed under AT&T. Code shown here is for **demonstration purposes only**.

```
