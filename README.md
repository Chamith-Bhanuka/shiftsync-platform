# ShiftSync — Platform Infrastructure Services

**Student Name:** Chamith Bhanuka Widanapathirana  
**Student ID / Number:** 241711051  
**Slack Handle:** Chamith Bhanuka  
**GCP Project ID:** project-a58ee7a4-4913-4af2-a6d  
**Course:** ITS 2130 — Enterprise Cloud Architecture  

---

## Description

Parent platform repository housing core infrastructure services for the ShiftSync enterprise platform:

1. **[api-gateway](./api-gateway)**: Central API Gateway built with Spring Cloud Gateway MVC, routing incoming traffic, enforcing CORS, and responding to GCP load balancer health checks.
2. **[config-server](./config-server)**: Spring Cloud Config Server managing centralized configuration repository for all platform services and domain microservices.
3. **[eureka-server](./eureka-server)**: Netflix Eureka registry enabling dynamic service discovery and client-side load balancing.

---

## Architecture Overview

```
Client / Frontend
       │
       ▼ (Port 80 / 7000)
┌─────────────────────────────────┐
│       API Gateway (MVC)         │
└────────────────┬────────────────┘
                 │ (Eureka Service Discovery)
   ┌─────────────┼─────────────┐
   ▼             ▼             ▼
Scheduling  Notification  Credential
 Service      Service      Service
```

---

## Deployment Architecture

Platform services run on Google Cloud Platform (GCP) Compute Engine Managed Instance Groups (`mig-platform`) behind External Classic Application Load Balancer (`lb-api-gateway`) and Internal Application Load Balancer (`lb-platform-config-server`).
