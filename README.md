Job Alert Microservices
![alt text](https://img.shields.io/badge/Java-17+-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![alt text](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![alt text](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)

![alt text](https://github.com/Eswar-deep/job-alert-microservices/actions/workflows/build.yml/badge.svg)
This project is the evolution of the original job-alert bot. It's a complete re-architecture of a monolithic Python script into a high-performance, event-driven system using Java, Spring Boot, and a modern microservices architecture designed for the cloud.
The goal is to build a resilient, scalable, and maintainable platform that not only automates job alerts but also serves as a showcase of enterprise-grade software engineering practices.
From Monolith to Microservices: The "Why"
The original Python script was effective but had limitations. This new architecture is designed to overcome them.
Aspect	🐍 Python Monolith (Before)	☕ Java Microservices (After)
Architecture	Single, monolithic script	3+ decoupled, single-purpose services
Communication	Direct function calls	Asynchronous messaging (via GCP Pub/Sub)
Scalability	Limited; scales as one unit	Infinite; services scale independently
Fault Tolerance	Low; one error can halt the system	High; services can fail without data loss
System Architecture
The system is designed around an event-driven, message-passing architecture to ensure complete decoupling between services.
code
Code
+------------------+      +-----------------------+      +-------------------+
|  Scraper Service |----->|  GCP Pub/Sub          |----->|  Job Management   |
| (Java, Selenium) |      |  (Topic: new-jobs)    |      |  Service (Java)   |
+------------------+      +-----------------------+      +-------------------+
                                                                   |
                                                                   | (sends message)
                                                                   v
+------------------+      +-----------------------+      +-------------------+
| Notification     |<-----|  GCP Pub/Sub          |<-----| (Apache Camel     |
| Service (Java)   |      |  (Topic: notifications)|      |  Route)           |
+------------------+      +-----------------------+      +-------------------+
Technology Stack
Backend: Java 17+, Spring Boot 3
Microservices Framework: Spring Cloud
Messaging & Integration: Apache Camel, Google Cloud Pub/Sub
Database: MongoDB (via Spring Data MongoDB)
Web Scraping: Selenium
Cloud & DevOps: Docker, GCP Cloud Run, GitHub Actions (CI/CD)
Testing: JUnit 5, Mockito
🚧 Project Status: Under Active Development 🚧
This project is being built iteratively. The current focus is on establishing the core architecture and message-driven communication.
Roadmap

Phase 1: Core business logic for each service.

Phase 2: Implement Apache Camel routes and integrate with GCP Pub/Sub.

Phase 3: Containerize all services with Docker.

Phase 4: Establish a full CI/CD pipeline with GitHub Actions to deploy to GCP Cloud Run.

Phase 5: Implement comprehensive unit and integration tests.
