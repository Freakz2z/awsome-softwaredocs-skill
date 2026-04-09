# Sequence Diagram Template

## Template Description

Sequence Diagram is used to describe the time-ordered message sequence between object interactions.

## Basic Syntax

```mermaid
sequenceDiagram
    participant A as Participant/Object
    participant B as Participant/Object

    A->>B: Synchronous message
    B-->>A: Response message
    A->>+B: Async message (activate B)
    B->>-A: Message end
    A-xB: Destroy message
    loop Loop description
        B->>A: Loop content
    end
    alt Condition 1
        A->>B: Condition branch 1
    else Condition 2
        A->>C: Condition branch 2
    end
    opt Optional
        A->>B: Optional content
    end
```

## Message Type Reference

| Syntax | Message Type | Description |
|--------|--------------|-------------|
| `->>` | Synchronous message | Sender waits for response |
| `-->>` | Response message | Return value |
| `->>+` | Activate+Sync | Activate target object |
| `-->>-` | Deactivate | Destroy object |
| `-x` | Async message | Sender does not wait |
| `loop` | Loop fragment | Loop execution |
| `alt/else` | Choice fragment | Conditional branch |
| `opt` | Optional fragment | Optional execution |

## Template Examples

### 1. User Login Sequence

```mermaid
sequenceDiagram
    participant U as User
    participant W as Web Frontend
    participant A as Auth Service
    participant DB as Database

    U->>W: Enter username and password
    W->>A: Submit login request
    A->>DB: Query user info
    DB-->>A: Return user data
    A->>A: Validate password
    A->>A: Generate JWT Token
    A-->>W: Return Token and user info
    W-->>U: Login successful, redirect to home
```

### 2. Order Creation Sequence

```mermaid
sequenceDiagram
    participant C as Customer
    participant S as Cart Service
    participant O as Order Service
    participant P as Payment Service
    participant I as Inventory Service
    participant M as Message Service

    C->>S: Initiate checkout
    S->>S: Calculate total price
    S-->>C: Display order confirmation

    C->>S: Confirm order
    S->>O: Create order (pending payment)
    O-->>S: Return order ID

    C->>P: Select payment method and pay
    P->>P: Call payment interface
    P-->>C: Payment in progress...

    P-->>O: Payment success callback
    O->>O: Update order status (paid)
    O->>I: Deduct inventory
    I-->>O: Inventory deducted

    O->>M: Send order notification message
    M-->>C: Notify customer order confirmed

    O-->>P: Return payment confirmation
    P-->>C: Payment successful
    C-->>S: Order created successfully
```

### 3. User Registration Sequence

```mermaid
sequenceDiagram
    participant U as User
    participant W as Web Frontend
    participant V as Verification Service
    participant M as Email/SMS Service
    participant A as Account Service
    participant DB as Database

    U->>W: Fill registration info
    W->>V: Send verification code request
    V->>M: Send verification code
    M-->>U: Receive verification code
    U->>W: Enter verification code
    W->>V: Verify code
    V-->>W: Verification passed

    W->>A: Submit registration info
    A->>DB: Check if username exists
    DB-->>A: Does not exist
    A->>DB: Create user record
    DB-->>A: User created successfully
    A->>A: Generate activation link
    A->>M: Send activation email
    M-->>U: Activation email

    U->>W: Click activation link
    W->>A: Activation request
    A->>DB: Update user status (activated)
    DB-->>A: Update successful
    A-->>W: Activation successful
    W-->>U: Registration complete
```

### 4. Concurrent Processing Sequence

```mermaid
sequenceDiagram
    participant C as Client
    participant L as Load Balancer
    participant S1 as Service Instance 1
    participant S2 as Service Instance 2
    participant Q as Message Queue
    participant W as Worker

    C->>L: HTTP Request
    L->>S1: Forward request 1
    L->>S2: Forward request 2

    par Parallel Processing
        S1->>S1: Process business logic
        S2->>S2: Process business logic
    end

    S1-->>L: Response 1
    S2-->>L: Response 2
    L-->>C: Aggregate response

    Note over L,C: If one service responds slowly,\nuse the faster response

    C->>L: Submit async task
    L->>Q: Send to message queue
    L-->>C: Task received
    Q->>W: Consume message
    W->>W: Process time-consuming task
    W-->>C: Notify task completion (optional)
```

### 5. Error Handling Sequence

```mermaid
sequenceDiagram
    participant C as Client
    participant A as API Gateway
    participant S as Business Service
    participant D as Data Service
    participant R as Degradation Service

    C->>A: Initiate request
    A->>S: Forward request
    S->>D: Query data

    alt Data Service Normal
        D-->>S: Return data
        S-->>A: Processing result
        A-->>C: Normal response
    else Data Service Timeout
        D--xS: Timeout
        S->>S: Retry attempt (1)
        S->>D: Retry request
        D--xS: Timeout again
        S->>S: Retry attempt (2)
        S->>D: Retry request
        D--xS: Third timeout
    else Data Service Failure
        D--xS: Connection refused
    end

    alt After Retry Failure
        S->>R: Request degraded data
        R-->>S: Return cache/default value
        S-->>A: Degraded response
        A-->>C: Return degraded data + friendly message
        Note over C: Show partial data\nwith retry message
    else Degradation Service Unavailable
        S-->>A: Return error
        A-->>C: 500 error + error code
        Note over C: Service temporarily unavailable
    end
```

### 6. Microservice Call Sequence

```mermaid
sequenceDiagram
    participant C as Customer
    participant G as API Gateway
    participant U as User Service
    participant O as Order Service
    participant P as Product Service
    participant I as Inventory Service
    participant M as Message Queue

    C->>G: Place order request
    G->>U: Validate user (token)
    U-->>G: User valid

    G->>O: Create order
    O->>P: Query product info
    P-->>O: Return product details
    O->>I: Query inventory
    I-->>O: Inventory sufficient

    O->>O: Create order record
    O->>I: Lock inventory
    I-->>O: Lock successful

    O->>M: Send order created event
    M-->>O: Event sent

    O-->>G: Order created successfully
    G-->>C: Return order info

    Note over M: Async processing\nPoints increase\nActual inventory deduction\nSend notification email
```

## Usage Guide

1. **Identify Participants**: Identify main objects/services in the interaction
2. **Identify Messages**: Identify information passed between participants
3. **Identify Order**: Arrange messages in time sequence
4. **Mark Activation**: Mark start and end of object lifecycle
5. **Handle Branches**: Use `alt/else` for conditional branches
6. **Handle Loops**: Use `loop` for repeated operations

## Best Practices

- Message flow top-to-bottom represents time progression
- Use clear participant naming
- Add explanatory comments to key messages
- Split complex flows into multiple sequence diagrams
- Use `Note` to mark important explanations