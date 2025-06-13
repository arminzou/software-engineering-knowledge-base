---
title: Client-Server Architecture
description: This document covers fundamental concepts of Client-Server Architecture
---

# Client-Server Architecture

A computing model where tasks are distributed between clients (requesters) and
servers (providers of resources/services).

## Core Components

### Client

**End-user (client) devices or applications** that communicates with **consumer applications** to make **requests** to servers.

!!! example "Examples"

    -   **Client devices**: Web browser, phone, computer
    -   **Consumer apps**: Web application, mobile application

### Server

**Dedicated computers or software** that **provides services, resources or data** to clients over a network to **fulfill requests**.

!!! info "Key Characteristics"

    -   Always-on availability
    -   Scalable resources
    -   Centralized management
    -   Secure access control

!!! note annotate

    Servers can be deployed in various ways depending on the requirements.(1)

1. See [Server Infrastructure](../fundamentals/server-infrastructure.md#server-deployment-models) for information about different deployment models (physical, virtual, containerized, cloud-based)

## Application Layers

### Frontend

**Web servers** that **serve static files** (HTML, CSS, JavaScript), **routes requests** to appropriate backend servers, often **acts as the entry point** for client application.

!!! info "Important Note"

    All frontend servers are [web servers](../fundamentals/server-infrastructure.md#web-server), but not all web servers that serve static files are considered frontend servers (Ex: CDN, Static File Servers).

!!! example "Examples"

    -   **Node.js with Express**: Often used to create custom frontend servers that serve React/Angular/Vue applications
    -   **Nginx as a frontend proxy**: Configured specifically to route and cache frontend resources

### Backend

**Application servers** that **host server-side applications** that process business logic, handle data operations, and interact with databases and other services.

!!! example "Examples"

    -   Application servers running Node.js, Python, Java, .NET, etc.

### Browser/Frontend App

A **client-side application** (1) running on the user's device that **provides the interface users interact** with directly in their browser.
{ .annotate }

1. client-side application: A collection of static files (HTML, CSS, and JavaScript)

!!! example "Examples"

    -   **Examples**: Web apps developed using frontend frameworks like React, Vue.js, Angular

### Backend App

**Server-side applications** (typically stateless services) that run on backend servers, **implement business logic** and **data processing** functionalities, and **expose APIs** for clients to consume.

!!! example "Examples"

    -   Applications built with ASP.NET Core, Django, Node.js

## Application Types

### Traditional Web Application

**Web applications** where **pages are fully rendered on the server** before being sent to the client.

```mermaid
sequenceDiagram
    participant U as User
    participant B as Browser
    participant S as Server

    U->>B: Initial request
    B->>S: GET /page
    S->>B: Generate and return complete HTML
    B->>U: Display page

    U->>B: Click link/submit form
    B->>S: GET/POST new request
    S->>B: Generate and return new complete HTML
    B->>U: Display new page (full reload)
```

### Single Page Application (SPA)

**Web applications** that **load a single HTML page** and dynamically update content
without full page reloads.

```mermaid
sequenceDiagram
    participant U as User
    participant B as Browser
    participant S as Server

    U->>B: Initial request
    B->>S: GET index.html
    S->>B: Return HTML, CSS, JavaScript
    Note over B: SPA loads completely

    U->>B: Interact with page
    B->>B: Update DOM

    U->>B: Request new data
    B->>S: AJAX call to API
    S->>B: Return JSON data
    B->>B: Update view without page reload
```

!!! tip

    SPAs use AJAX and JavaScript to fetch data from servers and modify the current page without requiring full page reloads.

### Progressive Web Application (PWA)

**Web applications** that use modern web technologies to **deliver app-like experiences** to users.

```mermaid
flowchart LR
    Client[Client] -->|HTTP/HTTPS| SW[Service Worker]
    SW -->|Cache| CS[Cache Storage]
    SW -->|Sync| BS[Background Sync]
    SW -->|Push| PN[Push API]

    Client -->|Install| WM[Web Manifest]
    WM -->|Metadata| App[PWA]
    App -->|Offline| SW
    App -->|Responsive| Client
```

!!! note "Key Features"

    PWAs are responsive, work offline, can be installed on home screens, support push notifications, and combine the best features of web and mobile applications.

## Deployment Architecture Patterns

### Single-Tier Architecture

A deployment strategy where **all application components (presentation, logic, data) run on a single server**. All components share the same computing resources and system environment.

```mermaid
flowchart LR
    subgraph "Web server (IIS/Nginx)"
        UI[User Interface] --> BL[Business Logic]
        BL --> DB[(Database)]
    end
    User(("User/Browser")) -->|HTTP| UI
```

### Multi-Tier Architecture

A deployment strategy that **splits application components across multiple servers** by deploying them into separate tiers for web servers, application servers, and database servers to improves scalability, enhances maintainability, and strengthens security.

```mermaid
flowchart LR
    User(("User/Browser")) -->|HTTP| LB[Load Balancer]

    subgraph "Presentation Tier"
        W1[Web Server 1]
        W2[Web Server 2]
    end

    subgraph "Application Tier"
        A1[App Server 1]
        A2[App Server 2]
    end

    subgraph "Data Tier"
        DB1[(Primary DB)]
        DB2[(Replica DB)]
    end

    LB --> W1
    LB --> W2
    W1 -->|API calls| A1
    W1 -->|API calls| A2
    W2 -->|API calls| A1
    W2 -->|API calls| A2
    A1 -->|SQL| DB1
    A2 -->|SQL| DB1
    DB1 -.->|Replication| DB2
```

### Containerized Architecture

A deployment strategy **using containerization (Docker, etc.) to package application components with their dependencies**. This enables consistent deployment across different environments and works with orchestration platforms like Kubernetes.

```mermaid
flowchart TB
    User(("User/Browser")) -->|HTTP| API[API Gateway]

    subgraph "Kubernetes Cluster"
        subgraph "Node 1"
            C1{{UI Container}}
            C2{{Auth Container}}
        end

        subgraph "Node 2"
            C3{{Payment Container}}
            C4{{Product Container}}
        end

        subgraph "Node 3"
            C5{{Notification Container}}
            C6{{Analytics Container}}
        end

        subgraph "Persistent Storage"
            DB1[(Auth DB)]
            DB2[(Product DB)]
            DB3[(Payment DB)]
        end
    end

    API -->|Routes request| C1
    API -->|Routes request| C2
    API -->|Routes request| C3
    API -->|Routes request| C4
    API -->|Routes request| C5
    API -->|Routes request| C6

    C2 -.->|Read/Write| DB1
    C3 -.->|Read/Write| DB3
    C4 -.->|Read/Write| DB2

    C1 <-->|API calls| C2
    C1 <-->|API calls| C4
    C3 <-->|API calls| C4
```

!!! tip

    Tools like Docker help create containers, while systems like Kubernetes help manage many containers.
