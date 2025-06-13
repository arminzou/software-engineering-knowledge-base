---
title: Server Infrastructure
description: This document covers fundamental concepts of Server Infrastructure
---

# Server Infrastructure

We often categorize servers by their primary function rather than their underlying technology.

## Infrastructure Components

### Web Server

A server with a specialized software that **handles HTTP requests** from clients (typically browsers). It directly **serves static content** (HTML, CSS, JavaScript, images), **forwards requests** for dynamic content to backend servers for processing, and **returns appropriate responses** to the client.

!!! info "Primary Function"

    - Focus on **serving web content**, **handling HTTP protocols**, and **routing requests**

!!! example "Examples"

    - IIS, Nginx, Apache HTTP Server

### Reverse Proxy

A server with a specialized software that sits between client devices and backend servers, **intercepting client requests** and **forwarding them to appropriate backend servers** while providing security, SSL termination, and caching.

!!! info "Primary Function"

    - Focus on request **forwarding**, **content caching**, and **security**

!!! example "Examples"

    - Nginx, IIS with Application Request Routing (ARR), Apache with mod_proxy

### Load Balancer

A server with a specialized software that **distributes incoming client requests across multiple servers** to ensure high availability, avoid traffic overload, prevent single points of failure, and enable horizontal scaling.

!!! info "Primary Function"

    - Focus on **traffic distribution** and **high availability**

!!! example "Examples"

    - **Load Balancing Software**: Microsoft Network Load Balancing (NLB), Nginx, HAProxy
    - **Cloud-based Services**: AWS Elastic Load Balancing, Azure Load Balancer

### API Gateway

A server with a specialized software that **acts as a single entry point** for client applications to access multiple backend services and APIs. It **serves as a reverse proxy for API requests** while providing additional functionality such as request routing, authentication, and monitoring.

!!! info "Primary Function"

    - Focus on **API traffic management**, **security**, and **request coordination** across multiple services

!!! example "Examples"

    - **Cloud-based Services**: Azure API Management, Amazon API Gateway
    - **Software**: Kong, Apigee, Tyk

### CDN (Content Delivery Network)

**A distributed network of servers** that caches and delivers web content from the server closest to users, improving performance and user experience.

!!! note "Key Characteristic"

    - Distributed globally to optimize content delivery

!!! example "Examples"

    - CloudFlare, Akamai, Fastly

## Server Deployment Models

### Physical Servers

Traditional deployment using dedicated hardware.

!!! info "Characteristics"

    - Full control over hardware and infrastructure
    - Higher upfront costs and maintenance overhead
    - Fixed capacity with manual scaling
    - Requires physical maintenance and datacenter management

### Virtual Machines (VMs)

Indenpendent computer environments created using software (1) on a single physical machine, allowing multiple "virtual computers" to run separately while sharing the same hardware resources. Each VM has its own operating system and appears to applications as a standalone computer.
{ .annotate }

1. **Hypervisor**: A virtualization software

!!! info "Characteristics"

    - Resource isolation through hypervisors
    - Support for multiple operating systems
    - Better resource utilization than physical servers
    - More flexible scaling and provisioning

### Containers

Lightweight, standalone executable packages including application code and dependencies.

!!! info "Characteristics"

    - Process-level isolation (shares OS kernel)
    - Consistent environments across development and production
    - Fast startup and deployment times
    - Highly efficient resource utilization
    - Orchestration through tools like Kubernetes

### Cloud-based Services

Infrastructure hosted and managed by cloud service providers with various abstraction levels (Cloud computing models).

!!! info "Characteristics"

    - Remote infrastructure management
    - Pay-as-you-go or subscription-based pricing
    - Elastic scaling capabilities
    - Managed services reducing operational overhead
    - Global availability and region-specific deployments
    - Shared responsibility security model

#### IaaS (Infrastructure as a Service)

A cloud computing model where cloud provider offers virtual infrastucture resources (servers, VMs, storage, networking) over the internet on a pay-as-you-go basis.

!!! info "Characteristics"

    - You manage the operating systems, middleware, and applications
    - The provider manages the hardware infrastructure
    - Requires the most management from your side
    - Virtualized computing resources
    - Self-service provisioning

    !!! example

        - AWS EC2
        - Azure Virtual Machines
        - Google Compute Engine

#### PaaS (Platform as a Service)

A cloud computing model that provides a platform enviroment allowing customers to develop, run, and manage applications.

!!! info "Characteristics"

    - You focus on application development
    - The provider manages the runtime, operating system, and underlying infrastructure
    - Simplifies development and deployment
    - Built-in scalability and high availability
    - Reduced operational management

    !!! example

        - Azure App Service
        - Google App Engine
        - Heroku

#### Serverless/FaaS (Function as a Service)

A cloud computing model that allows developers to build, deploy, and execute individual functions (or microservices) without managing the underlying infrastructure.

!!! info "Characteristics"

    - You pay only for execution time (not idle capacity)
    - The provider fully manages starting and stopping virtual machines (No server management required)
    - Automatic scaling based on demand
    - Event-driven architecture
    - Stateless execution model

    !!! example

        - AWS Lambda
        - Azure Functions
        - Google Cloud Functions
        - Cloudflare Workers

#### SaaS (Software as a Service)

A computing model where cloud providers host, manage, and deliver applications to customers over the internet.

!!! info "Characteristics"

    - Complete application delivered as a service
    - No local installation or maintenance required
    - Typically subscription-based pricing
    - Provider manages everything (infrastructure, platform, application)

    !!! example

        - Microsoft 365
        - Salesforce
        - Google Workspace
