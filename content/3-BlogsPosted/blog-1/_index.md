---
title: "Blog 1"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Building a Multi-Tenant Configuration System with Tagged Storage Patterns

---

> [!IMPORTANT]
> ### 🎯 Article Objective
> In modern microservices architectures, managing **multi-tenant configuration** remains one of the biggest operational challenges. This article provides a step-by-step guide to designing a **high-performance, secure, event-driven configuration service** on AWS, eliminating the traditional bottlenecks of cache TTL invalidation and enabling real-time configuration synchronization.
>
> * **Original article:** [AWS Study Group](https://awsstudygroup.com/2026/05/14/xay-dung-he-thong-cau-hinh-da-doi-tuong-thue-voi-cac-mau-luu-tru-duoc-gan-the/)

---

## 1. Challenges of Multi-Tenant Configuration Systems

As organizations scale their SaaS (Software as a Service) platforms to hundreds or even thousands of tenants, traditional configuration management architectures begin to expose two major limitations:

1. **Cache Invalidation TTL**
   * Tenant metadata changes more frequently than the cache TTL allows.
   * Traditional caching strategies force a trade-off between serving stale tenant context (leading to potential data leakage or incorrect feature flags) and continuously invalidating caches, which significantly increases metadata service load.

2. **Storage Backend Mismatch**
   * Different configuration types have different access patterns.
   * Frequently updated tenant-specific configurations require the high read/write throughput provided by **Amazon DynamoDB**.
   * Shared system configurations and hierarchical settings that require versioning are better suited for **AWS Systems Manager Parameter Store**.
   * Using a single storage backend for every configuration type results in reduced performance and operational efficiency.

---

## 2. Solution: Tagged Storage Pattern

This approach uses configuration key prefixes (for example, `tenant_config_` and `param_config_`) to automatically route configuration requests to the most appropriate AWS storage service through a **Config Strategy Factory** design.

![Overall architecture of the multi-tenant configuration system on AWS](/images/multi_tenant_architecture.png)

### End-to-End Workflow

Based on the overall architecture, requests and configuration updates flow through the following 13 steps:

1. **User Authentication** – Client applications send their initial login request to **Amazon Cognito** `(1)`.
2. **JWT Token Issued** – **Amazon Cognito** authenticates the user and returns a JWT token containing the custom tenant attribute (`custom:tenantId`) `(2)`.
3. **API Request** – The client sends REST API requests with the JWT token through **AWS WAF** for protection `(3)`.
4. **API Gateway Routing** – Requests are forwarded to **AWS API Gateway (Public REST API)** `(4)`.
5. **Private Integration** – **VPC Link V2** securely routes traffic into the private VPC network `(5)`.
6. **Load Balancing** – **Application Load Balancer** distributes requests to the **REST API Controller** of the **Order Service** running on Amazon ECS Fargate `(6)`.
7. **Service Discovery** – The **Order Service** performs DNS lookup using **AWS Cloud Map** `(7)` to locate the Config Service (`config-service.local:5000`).
8. **gRPC Communication** – The internal **gRPC Client** establishes a connection and invokes the **gRPC Controller** of the **Config Service** `(8)` to minimize network overhead.
9. **Strategy Routing** – The **Config Strategy Factory** `(9)` analyzes the configuration key prefix:
   * If the prefix is `tenant_config_*` → Select the **DynamoDB Strategy**, retrieving data through a Gateway Endpoint using partition key `TENANT#{tenantId}`.
   * If the prefix is `param_config_*` → Select the **SSM Strategy**, retrieving data from **Parameter Store** through an Interface Endpoint with AWS KMS encryption.
10. **Configuration Change Detection** – When Parameter Store configurations change, an event `(10)` is published to **Amazon EventBridge**.
11. **Lambda Trigger** – **Amazon EventBridge** detects the event and invokes an **AWS Lambda** function `(11)`.
12. **DNS Lookup & Cache Refresh** – **AWS Lambda** performs service discovery through Cloud Map `(12)` and directly invokes the Config Service's `gRPC refresh()` method `(13)` to invalidate or refresh the local cache immediately without restarting any containers.

---

## 3. Core Components and Architectural Layers

The system is organized into four tightly integrated layers to maximize both performance and security.

### 💼 Layer 1: Storage Layer – Multi-Backend Strategy

* **Amazon DynamoDB (Tenant-Specific Configuration)**
  * Stores tenant-specific settings such as payment gateways and feature flags.
  * Uses a composite key schema:
    * Partition Key: `TENANT#{tenantId}`
    * Sort Key: `CONFIG#{configType}`
  * Provides complete tenant isolation at the data model level.
  * Delivers single-digit millisecond latency.

* **AWS Systems Manager Parameter Store (Shared Configuration)**
  * Stores relatively static yet hierarchical configurations such as API endpoints and connection strings.
  * Uses a path structure like:
    `/config-service/{tenantId}/{service}/{parameter}`
  * Supports batch retrieval, reducing initialization API calls from dozens to a single request.

### 🔌 Layer 2: Service Layer – gRPC with the Strategy Pattern

* Uses **NestJS** together with the high-performance **gRPC** protocol for east-west communication between microservices.
* The **Strategy Pattern** separates business logic from storage implementations, making it easy to extend additional storage backends (such as Amazon S3 for large configuration files) without restructuring the application's core code.

### 🔐 Layer 3: Authentication Layer – Tenant Context from Cognito JWT Claims

Amazon Cognito defines the following required custom attributes:

* `custom:tenantId` (immutable) – Tenant identifier.
* `custom:role` (mutable) – User role.

**Secure Design**

The Configuration Service never accepts `tenantId` directly from API request parameters. Instead, it extracts `custom:tenantId` from the JWT token forwarded by API Gateway, completely eliminating **IDOR (Insecure Direct Object Reference)** vulnerabilities and preventing cross-tenant data leakage.

### ⚡ Layer 4: Event-Driven Cache Refresh

This architecture eliminates the traditional cache TTL bottleneck using an event-driven synchronization mechanism.

Benefits include:

* Eliminates continuous polling, reducing API costs and synchronization delays.
* Eliminates service restarts, providing zero-downtime configuration updates.
* Uses **Amazon EventBridge** together with **AWS Lambda** to capture Parameter Store change events and immediately push cache invalidation signals to the Config Service gRPC API, allowing cache synchronization across the ECS cluster within seconds.

---

> [!TIP]
> ### 💡 Architectural Benefits
>
> * **Complete tenant isolation** through Cognito JWT claims and DynamoDB partitioning.
> * **High performance** by combining gRPC with intelligent strategy-based backend routing.
> * **Zero downtime** through event-driven cache refresh using Amazon EventBridge and AWS Lambda, eliminating service restarts after configuration updates.
```
