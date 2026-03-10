# Event Driven Architecture

**Event-driven architecture (EDA)** is a software design pattern where services communicate by producing, detecting, consuming, and reacting to events—significant changes in state or occurrences asynchronously, enabling loose coupling, scalability, and real-time responsiveness.

## Types of Architecture :

- Apache Kafka
- RabbitMQ
- Amazon SNS/SQS
- Google Pub/Sub
- Azure Event Grid
- Apache Pulsar
- ActiveMQ
- NATS
- Redis Pub/Sub
- AWS Kinesis

## Event-driven frameworks: 
- Spring Cloud Stream
- Akka
- Vert.x*

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

## Feature Toggling

Implementing feature toggles or feature flags allows you to control the release of new features in your application without the need for code deployments. This can help you gradually roll out features to different user groups or enable/disable features as needed. Below, I'll demonstrate how to implement feature toggles using the launchdarkly-node-server-sdk library as an example.

This is a very progressive and useful tool in optimisation, refinements, recommendation and improvements during service delivery and support in Management Consultancy.

By using LaunchDarkly, you can manage your feature toggles remotely without the need to modify the application code or redeploy it. This approach allows you to experiment with new features and safely roll them out to a subset of users/segmentation before enabling them for all users. Additionally, you can quickly disable features in case of issues or performance concerns.

https://github.com/kukuu/integration/blob/main/feature-toggle.md

## Implementing Comprehensive Incremental Deployments
Incremental deployments are an approach to deploying software updates in smaller, manageable increments rather than deploying everything at once. The goal is to reduce risks, improve feedback cycles, and deliver new features more frequently.

By implementing these practices and leveraging appropriate tools, teams can achieve comprehensive incremental deployments, allowing them to release software updates more frequently and with greater confidence in the stability and quality of the releases.

Here are some practices and tools that can be used to implement comprehensive incremental deployments:

- Feature Toggles/Flags: Use feature toggles to enable or disable specific features during deployment. This allows you to control the rollout of new functionality and easily roll back if needed. Tools like LaunchDarkly or Unleash can help manage feature toggles.

- Continuous Integration and Delivery (CI/CD): Implement automated CI/CD pipelines to build, test, and deploy code frequently and reliably. Jenkins, GitLab CI/CD, and CircleCI are popular CI/CD tools.
- Microservice: A Microservices architecture refers to an application which is constructed from a number of independent services called Microservices.  Each microservice is a self-contained module that performs a discrete group of functions.
    - Loose coupling since it decouples clients from services
    - Small individual components
    - Easy to maintain
    - Offers parallel development
    - Independent deployment
    - Rapid iteration
    - Feature additions - enrichments
    - Confidence with CI/CD
    - Improved availability since the message broker buffers messages until the consumer is able to process them
    - Supports a variety of communication patterns including request/reply, notifications, request/async response, 
       publish/subscribe, publish/async response etc
    - Agile compliant: The modular approach of Microservices architecture works well with an agile management style as it 
       supports the slicing and splitting up of smaller work increments and tasks which goes hand-in-hand with projects using 
       an agile methodology.
     - Reduced system downtime: Microservices provide the flexibility to change parts of the solution without affecting the solution as a whole which is key in providing a reliable solution without downtime for end users.

- Canary Deployment (Segmentation) : Deploy new features or updates to a small subset of users (the "canary" group) before rolling out to the entire user base. This helps identify issues early and minimize the impact of potential problems. Kubernetes and Istio can assist in canary deployments.

- Blue-Green Deployment: Maintain two identical environments, one active (blue) and the other inactive (green). Deploy updates to the inactive environment and switch traffic to the updated version once it's tested and verified. Tools like AWS Elastic Beanstalk or Docker Swarm can facilitate blue-green deployments.

- Automated Testing: Comprehensive test suites, including unit tests, integration tests, and end-to-end tests, help ensure the stability and quality of each incremental deployment.

- Monitoring and Alerts: Set up monitoring and alerting systems to quickly detect any issues in the production environment after deployment. Tools like Prometheus and Grafana can help monitor application performance.

- Rollback Mechanism: Plan for a rollback strategy in case of unexpected issues or failures during deployment. This could involve automatically rolling back to a previous version or fixing the problem and redeploying.
  Use version control systems like Git to keep track of code changes and easily revert or switch between different versions.

- Infrastructure as Code (IaC): Adopt IaC tools like Terraform or CloudFormation to manage and version infrastructure changes, ensuring consistent and reproducible deployments.

## Addressing Technical Debt and Scaling Legacy Systems
This solution provides a comprehensive roadmap to address technical debt and scale legacy systems. The gradual migration approach minimizes risks and ensures system availability, while observability and refactoring practices ensure long-term maintainability. By communicating trade-offs and balancing feature development with technical debt reduction, you ensure stakeholder buy-in and deliver measurable results.

#### Architecture

_High-Level Overview:_

- API Gateway: Acts as a single entry point, routing traffic to legacy systems or refactored microservices.

- Microservices: Gradually replace legacy system functionality with scalable, loosely coupled services.

- Caching Layer: Introduce Redis or Memcached for frequently accessed data.

- Data Layer: Use database sharding/partitioning and replication to ensure performance.

- Monitoring Tools: Implement tools like Prometheus and Grafana to track system performance and technical debt.

#### Solution Steps

 ##### Refactoring Strategies: Strangler Pattern

- Identify business-critical components in the legacy system.

- Implement the Strangler Pattern: incrementally refactor and replace legacy components with modern, modular microservices.

- Route traffic through an API gateway to gradually transition functionality from legacy systems to new microservices, minimizing disruptions.

- Start with non-critical services (e.g., reporting systems) and progress to core services (e.g., billing or real-time energy consumption).

##### Scalability Improvements

- Implement horizontal scaling by deploying services on cloud platforms like AWS, using tools such as AWS Auto Scaling Groups or Kubernetes.

- Add a caching layer with Redis or Memcached to handle frequently accessed data and reduce database load.

- Use database sharding or partitioning for large-scale data distribution and faster query performance.

##### Tools and Techniques to Measure and Reduce Technical Debt

- Use SonarQube or Code Climate to measure and visualize technical debt (code complexity, duplication, and maintainability).

- Refactor high-complexity code and implement unit tests to ensure functional correctness.

- Use static code analysis tools to enforce coding standards.

- Perform periodic code reviews and architecture assessments to keep technical debt in check.

##### Balancing Between New Features and Technical Debt

- Use the 70/30 rule: allocate 70% of development resources to new features and 30% to technical debt reduction.

- Schedule sprints dedicated to technical debt reduction within Agile workflows (e.g., every 3rd sprint).

- Identify low-effort, high-impact debt reduction tasks (e.g., replacing outdated libraries or removing redundant code).

##### Communication Strategies with Stakeholders

- Clearly document technical debt items, their impact on business performance, and proposed solutions.

- Use simple language to explain trade-offs between fixing technical debt and delivering new features (e.g., reduced downtime, improved scalability).

- Develop a prioritized roadmap, balancing technical improvements and business needs.
Demonstrate ROI by showing how debt reduction improves key metrics (e.g., latency, scalability).


## AI, ML, LLM / NLP Integration

https://github.com/kukuu/AI-ML-LLM-NLP-integration

## Systems
- Systems Design - https://github.com/kukuu/systems-design
- Cloud Eco-systems - https://github.com/kukuu/cloud-eco-systems
- System Design Architecture - https://github.com/kukuu/system-design-architecture | https://github.com/kukuu/scalable-platforms-system-architecture
- Recommendation Systems - https://github.com/kukuu/recommendation-systems
- RAG Systems - https://github.com/kukuu/RAG-system
- RAG Systems for regulated environments -  https://github.com/kukuu/RAG-system-for-regulated-environment
- Spyder Navigation System - https://github.com/kukuu/spider-navigation-system
- High volume AWS cloud mailing service architecture - https://github.com/kukuu/high-volume-aws-cloud-mailingl-service-system
