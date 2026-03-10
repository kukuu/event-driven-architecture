# Event Driven Architecture

**Event-driven architecture (EDA)** is a software design pattern where services communicate by producing, detecting, consuming, and reacting to events—significant changes in state or occurrences asynchronously, enabling loose coupling, scalability, and real-time responsiveness.

## Types of Architecture :

- **Apache Kafka**
- **RabbitMQ**,
- **Amazon SNS/SQS**,
- **Google Pub/Sub**
- **Azure Event Grid**
- **Apache Pulsar**
- **ActiveMQ**
- **NATS**,
- **Redis Pub/Sub**
- **AWS Kinesis**

## Event-driven frameworks: 
- **Spring Cloud Stream**
- **Akka**
- **Vert.x**.

**Benefits**:

Event-driven architecture enables:

- Real-time processing of alerts as they arrive
- Scalable correlation across millions of events
- Decoupled components that can evolve independently
- Fault tolerance through event persistence and replay
- Multiple consumers of the same event streams

## Core Pillars : Systems Design Architecture 
- Design for Failure
- Loose Coupling
- Self Healing
- Multiple Avalability Zones
- Scalability


## Principles of Software Design

<img width="1055" height="514" alt="image" src="https://github.com/user-attachments/assets/ddc171fb-22a4-4e57-a95e-b5b0db24b0d0" />

## Software Integration Tasks:

https://github.com/kukuu/integration/blob/main/README.md

## Microservice

- Implementation: https://github.com/kukuu/integration/blob/main/1-microservice-architecture.png
- Architecture : https://github.com/kukuu/integration/blob/main/1-microservice-architecture.png

## Infrastructure as Code (Iac)


<img width="1406" height="474" alt="image" src="https://github.com/user-attachments/assets/9dcd86c7-f530-4b21-8bf9-7cb3dd65d5b4" />


## Practical Solution For Fault-Tolerant Distributed System

_Solution Steps_

### Step 1: Load Balancing and Replication

- Goal: Distribute traffic evenly across backend services and ensure redundancy to avoid single points of failure.

- Use Load Balancers such as AWS Elastic Load Balancer (ELB) or NGINX to distribute traffic across backend services.

- Deploy services across multiple availability zones (AZs) or regions to ensure redundancy.

- Enable horizontal and auto scaling(with help of cloud watch) using container orchestration tools like Kubernetes (K8s) or AWS ECS.

### Step 2: Circuit Breaker Patterns

- Goal: Prevent cascading failures across services.
  
- Implement circuit breaker patterns using libraries like Hystrix (Java) or Resilience4j (Java/Spring Boot).

- Create fallback mechanisms for degraded service operation.

- Monitor service health and allow for retry logic with exponential backoff.

### Step 3: Disaster Recovery and Backup

- Goal: Ensure continuity during large-scale outages.

- Use multi-region deployments with real-time data replication for disaster recovery.

- Store backups in object storage (e.g., AWS S3, Azure Blob Storage) with versioning.

- Set up a disaster recovery plan to quickly restore critical services and data.

### Step 4: Eventual Consistency

- Goal: Allow distributed systems to achieve data consistency over time.

- Use event-driven architecture with messaging systems like Apache Kafka or RabbitMQ.

- Design idempotent APIs to ensure that repeated requests do not cause duplication.

- Implement saga patterns to manage distributed transactions.

### Step 5: Observability

- Goal: Provide visibility into system health and performance.

- Use Prometheus for metrics collection and Grafana for visualizing system health.

- Set up distributed logging with the ELK stack (Elasticsearch, Logstash, Kibana).

- Configure alerts for anomalies and system failures using tools like PagerDuty.

## Systems
- Systems Design - https://github.com/kukuu/systems-design
- Cloud Eco-systems - https://github.com/kukuu/cloud-eco-systems
- System Design Architecture - https://github.com/kukuu/system-design-architecture | https://github.com/kukuu/scalable-platforms-system-architecture
- Recommendation Systems - https://github.com/kukuu/recommendation-systems
- RAG Systems - https://github.com/kukuu/RAG-system
- RAG Systems for regulated environments -  https://github.com/kukuu/RAG-system-for-regulated-environment
- Spyder Navigation System - https://github.com/kukuu/spider-navigation-system
- High volume AWS cloud mailing service architecture - https://github.com/kukuu/high-volume-aws-cloud-mailingl-service-system
