# Component and Deployment Diagram Template

## Component Diagram

### Template Description

Component Diagram is used to show software components and their dependencies in a system.

### Basic Syntax

```mermaid
graph LR
    component1[Component 1]
    component2[Component 2]

    component1 --> component2
```

### Mermaid Component Diagram Syntax

```mermaid
classDiagram
    class Component1 {
        <<component>>
    }
    class Component2 {
        <<component>>
    }

    Component1 ..> Component2 : depends on
```

### Component Diagram Example

```mermaid
graph TB
    subgraph FrontendLayer["Frontend Layer"]
        UI["User Interface Component\n(Component)"]
        CTRL["Controller Component\n(Component)"]
    end

    subgraph BusinessLogicLayer["Business Logic Layer"]
        SVC["Business Service Component\n(Component)"]
        VAL["Validation Component\n(Component)"]
    end

    subgraph DataAccessLayer["Data Access Layer"]
        DAO["Data Access Component\n(Component)"]
        ORM["ORM Component\n(Component)"]
    end

    subgraph ExternalServices["External Services"]
        EXT["Third-party Service\n(External)"]
    end

    UI --> CTRL
    CTRL --> SVC
    SVC --> VAL
    SVC --> DAO
    DAO --> ORM
    ORM --> EXT
    VAL --> ORM
```

## Deployment Diagram

### Template Description

Deployment Diagram is used to show the hardware and software deployment structure of a system.

### Basic Syntax

```mermaid
graph TB
    node1["Node 1"]
    artifact1["Artifact"]

    node1 --- artifact1
```

### Mermaid C4 Deployment Diagram Syntax (Alternative)

```mermaid
C4Deployment
    Deployment_Node(loc, alias, "label", "description")
```

### Deployment Diagram Example

```mermaid
graph TB
    subgraph UserLayer["User Layer"]
        C1["User Device"]
        B1["Browser"]
        M1["Mobile App"]
    end

    subgraph LoadBalancingLayer["Load Balancing Layer"]
        LB["Load Balancer\n(Nginx/HAProxy)"]
    end

    subgraph ApplicationLayer["Application Service Layer"]
        subgraph K8S["Kubernetes Cluster"]
            POD1["Web Service Pod\n×3 Replicas"]
            POD2["API Service Pod\n×3 Replicas"]
            POD3["Background Task Pod\n×2 Replicas"]
        end
    end

    subgraph DataLayer["Data Storage Layer"]
        DB1["MySQL Primary\n(Master-Slave)"]
        DB2["MySQL Replica"]
        RD["Redis Cluster\n(Cache/Session)"]
        ES["Elasticsearch\n(Search)"]
        MQ["RabbitMQ\n(Message Queue)"]
        OSS["Object Storage\n(Files/Images)"]
    end

    C1 --> B1
    C1 --> M1
    B1 --> LB
    M1 --> LB
    LB --> POD1
    POD1 --> POD2
    POD2 --> POD3
    POD2 --> DB1
    POD2 --> DB2
    POD2 --> RD
    POD2 --> ES
    POD2 --> MQ
    POD3 --> MQ
    POD3 --> OSS
```

## Combined Deployment Diagram

```mermaid
graph TB
    subgraph ProductionEnvironment["Production Environment"]
        subgraph PublicNetwork["Public Network"]
            CDN["CDN\n(Content Delivery)"]
            DNS["DNS Service"]
            Users["Users"]
        end

        subgraph LoadBalancingLayer["Load Balancing Layer"]
            SLB["SLB\n(Alibaba/Tencent Cloud)"]
        end

        subgraph ApplicationCluster["Application Cluster"]
            subgraph WebTier["Web Layer (Stateless)"]
                W1["Web Pod 1"]
                W2["Web Pod 2"]
                W3["Web Pod 3"]
            end

            subgraph ApiTier["API Layer (Stateless)"]
                A1["API Pod 1"]
                A2["API Pod 2"]
                A3["API Pod 3"]
            end

            subgraph WorkerTier["Worker Layer"]
                WK1["Worker Pod 1"]
                WK2["Worker Pod 2"]
            end
        end

        subgraph MiddlewareLayer["Middleware Layer"]
            Redis["Redis Cluster"]
            RabbitMQ["RabbitMQ"]
            ES["Elasticsearch"]
        end

        subgraph DatabaseLayer["Database Layer"]
            subgraph Primary["Primary"]
                MySQL_M["MySQL Primary"]
            end
            subgraph Replica["Replica"]
                MySQL_S1["MySQL Replica 1"]
                MySQL_S2["MySQL Replica 2"]
            end
        end

        subgraph StorageLayer["Object Storage"]
            OSS["OSS / S3"]
        end
    end

    Users --> DNS
    DNS --> CDN
    CDN --> SLB
    Users --> SLB
    SLB --> W1
    SLB --> W2
    SLB --> W3

    W1 --> A1
    W2 --> A2
    W3 --> A3

    A1 --> Redis
    A2 --> Redis
    A3 --> Redis

    A1 --> MySQL_M
    A2 --> MySQL_M
    A3 --> MySQL_M

    MySQL_M --> MySQL_S1
    MySQL_M --> MySQL_S2

    A1 --> RabbitMQ
    A2 --> RabbitMQ
    A3 --> RabbitMQ

    WK1 --> RabbitMQ
    WK2 --> RabbitMQ

    WK1 --> OSS
    WK2 --> OSS

    WK1 --> ES
    WK2 --> ES
```

## Complete Microservices Architecture Deployment Diagram

```mermaid
graph TB
    subgraph External["External"]
        Browser["Browser"]
        MobileApp["Mobile App"]
        ThirdParty["Third-party API"]
    end

    subgraph Gateway["API Gateway Layer"]
        Kong["Kong Gateway"]
    end

    subgraph ServiceMesh["Service Mesh Layer"]
        Istio["Istio"]
    end

    subgraph Services["Microservices Layer"]
        subgraph UserService["User Service"]
            U_POD["User Service Pod"]
        end

        subgraph OrderService["Order Service"]
            O_POD["Order Service Pod"]
        end

        subgraph ProductService["Product Service"]
            P_POD["Product Service Pod"]
        end

        subgraph PaymentService["Payment Service"]
            PY_POD["Payment Service Pod"]
        end

        subgraph NotificationService["Notification Service"]
            N_POD["Notification Service Pod"]
        end
    end

    subgraph Backend["Backend Support"]
        Redis["Redis Cluster"]
        MySQL["MySQL Cluster"]
        Kafka["Kafka Cluster"]
        ES["Elasticsearch"]
        S3["Object Storage"]
    end

    Browser --> Kong
    MobileApp --> Kong
    Kong --> Istio

    Istio --> U_POD
    Istio --> O_POD
    Istio --> P_POD
    Istio --> PY_POD
    Istio --> N_POD

    U_POD --> Redis
    U_POD --> MySQL

    O_POD --> Redis
    O_POD --> MySQL
    O_POD --> Kafka

    P_POD --> Redis
    P_POD --> MySQL
    P_POD --> ES

    PY_POD --> MySQL
    PY_POD --> ThirdParty

    N_POD --> Kafka
    N_POD --> S3

    O_POD ..> P_POD : Service Call
    O_POD ..> PY_POD : Service Call
    O_POD ..> N_POD : Async Message
```

## Containerized Deployment Architecture

```mermaid
graph TB
    subgraph DevelopmentEnvironment["Development Environment"]
        DEV_PC["Developer PC"]
        REGISTRY_DEV["Private Image Registry\n(Development)"]
    end

    subgraph CI_CD["CI/CD Pipeline"]
        GitRunner["GitLab Runner"]
        Harbor["Harbor Image Registry"]
    end

    subgraph K8S_Prod["Kubernetes Production Cluster"]
        subgraph Ingress["Ingress"]
            Nginx_Ing["Nginx Ingress"]
        end

        subgraph Monitor["Monitoring Components"]
            Prometheus["Prometheus"]
            Grafana["Grafana"]
        end

        subgraph ApplicationLayer["Application Load"]
            APP_PODS["Business Pod Group"]
        end

        subgraph DataLayer["Storage Layer"]
            PVC["Persistent Volume"]
        end
    end

    DEV_PC --> GitRunner : push code
    GitRunner --> Harbor : push image
    Harbor --> K8S_Prod : pull image

    Nginx_Ing --> APP_PODS
    Prometheus --> APP_PODS
    APP_PODS --> PVC
```

## Component Diagram vs Deployment Diagram Comparison

| Feature | Component Diagram | Deployment Diagram |
|---------|------------------|-------------------|
| Focus | Software components and dependencies | Hardware and software deployment |
| Main Elements | Components, interfaces, dependencies | Nodes, devices, artifacts |
| Purpose | Code organization structure | Physical deployment structure |
| Perspective | Developer perspective | Operations perspective |
| Abstraction Level | Logical level | Physical level |

## Usage Guide

1. **Component Diagram**: Show system's modular structure, reflecting code organization
2. **Deployment Diagram**: Show system's physical architecture, reflecting hardware resources
3. **Combined Use**: Component diagram for design phase, deployment diagram for implementation phase
4. **Hierarchical Structure**: Use `subgraph` to represent system's logical layering
5. **Redundancy Design**: Production environment usually shows multi-replica and high-availability architecture