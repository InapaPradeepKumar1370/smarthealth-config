# SmartHealth+ Configuration Repository

This repository holds centralized configuration files for all microservices in the **SmartHealth+** healthcare management platform.

## 📌 Purpose

This repository is used by the `configserver` (Spring Cloud Config Server) to serve configuration to microservices dynamically.  
It supports both **shared configurations** and **service-specific configurations**, enabling externalization of properties.

---

## 🗂️ Folder Structure

smarthealth-config/
├── application.yml # Global default config for all services
├── patient-service.yml # Config specific to patient-service
├── doctor-service.yml # Config specific to doctor-service
├── appointment-service.yml # Config for appointment-service
├── prescription-service.yml # Config for prescription-service
├── billing-service.yml # Config for billing-service
├── auth-service.yml # Config for auth-service
├── notification-service.yml # Config for notification-service
├── reporting-service.yml # Config for reporting-service
├── feedback-service.yml # Config for feedback-service
├── file-service.yml # Config for file-service
├── audit-service.yml # Config for audit-service
├── inventory-service.yml # Config for inventory-service
├── payment-gateway-service.yml # Config for payment gateway

yaml
Copy
Edit

---

## ⚙️ Sample `application.yml`

```yaml
server:
  port: 8888

spring:
  application:
    name: configserver
  cloud:
    config:
      server:
        git:
          uri: https://github.com/your-username/smarthealth-config
          default-label: main
          search-paths: .
📢 Best Practices
Use meaningful profiles (e.g., application-dev.yml, patient-service-prod.yml) for environment separation.

Never commit sensitive data (like passwords or secrets). Use placeholders or secret vault integration.

Ensure all services are configured to use the correct spring.cloud.config.uri.

🚀 How It Works
The configserver reads this repo at startup.

Each microservice makes an HTTP call to configserver like:

bash
Copy
Edit
http://localhost:8888/patient-service/default
Config server serves the appropriate config (e.g., patient-service.yml).

🧑‍💻 Author
Pradeep Kumar Inapa
Java Developer | Spring Boot | Microservices | Cloud-Native Apps
