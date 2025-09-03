# Job Alert Microservices

![Java](https://img.shields.io/badge/Java-17+-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=for-the-badge&logo=spring&logoColor=white) ![GCP](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

[![CI/CD Pipeline](https://github.com/Eswar-deep/job-alert-microservices/actions/workflows/main.yml/badge.svg)](https://github.com/Eswar-deep/job-alert-microservices/actions)

This project is the evolution of the original [job-alert bot](https://github.com/Eswar-deep/job-alert). It's a complete re-architecture of a monolithic Python script into a high-performance, **event-driven system** using **Java, Spring Boot,** and a modern **microservices architecture** designed for the cloud.

The goal is to build a resilient, scalable, and maintainable platform that not only automates job alerts but also serves as a showcase of enterprise-grade software engineering practices.

## From Monolith to Microservices: The "Why"

The original Python script was effective but had limitations in scalability and fault tolerance. This new architecture is designed to overcome them.

| Aspect | 🐍 Python Monolith (Before) | ☕ Java Microservices (After) |
| :--- | :--- | :--- |
| **Architecture** | Single, monolithic script | 3+ decoupled, single-purpose services |
| **Communication** | Direct function calls | Asynchronous messaging (via GCP Pub/Sub) |
| **Scalability** | Limited; scales as one unit | High; services scale independently |
| **Fault Tolerance** | Low; one error can halt the system | High; services can fail without data loss |

## System Architecture

The system is designed around an event-driven, message-passing architecture to ensure complete decoupling between services.

```mermaid
graph TD
    A[Scraper Service] -->|1. Publishes 'new-job' event| B(GCP Pub/Sub Topic);
    B -->|2. Subscribes to events| C[Job Management Service];
    C -->|3. Publishes 'notify-user' event| B;
    B -->|4. Subscribes to events| D[Notification Service];
    D -->|5. Sends Telegram Alert| E((User));
