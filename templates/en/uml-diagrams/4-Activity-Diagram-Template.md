# Activity Diagram Template

## Template Description

Activity Diagram is used to describe business processes, workflows, or algorithm execution steps, supporting parallel activities.

## Basic Syntax

```mermaid
graph TD
    A[Start] --> B[Activity Node]
    B --> C{Decision Node}
    C -->|Condition 1| D[Activity 1]
    C -->|Condition 2| E[Activity 2]
    D --> F[End]
    E --> F

    subgraph Subgraph Name
        G --> H
    end
```

## Node Types

| Syntax | Node Type | Description |
|--------|-----------|-------------|
| `[Text]` | Activity | Rounded rectangle, represents action/operation |
| `{Text}` | Decision | Diamond, represents conditional judgment |
| `([[Text]])` | Start/End | Circle, represents process start or end |
| `((Text))` | Circle | Large dot, represents start (vertical) |
| `([Text])` | Stadium | Rounded rectangle with semicircles on both ends, represents subprocess |

## Branch and Loop

```mermaid
graph TD
    A --> B{Condition Check}
    B -->|Yes| C[Execute Activity]
    B -->|No| D[Other Activity]
    C --> D

    subgraph Loop Example
        E --> F{Continue Loop?}
        F -->|Yes| G[Loop Body]
        G --> E
        F -->|No| H[Exit Loop]
    end
```

## Template Examples

### 1. User Registration Process

```mermaid
graph TD
    A([Start Registration]) --> B[Fill Registration Info]
    B --> C{Info Validation}
    C -->|Fail| D[Show Error Message]
    D --> B
    C -->|Success| E[Send Verification Code]
    E --> F[Enter Verification Code]
    F --> G{Code Correct?}
    G -->|No| H[Show Code Error]
    H --> F
    G -->|Yes| I[Create Account]
    I --> J[Send Welcome Email]
    J --> K([Registration Success])
```

### 2. Order Processing Flow

```mermaid
graph TD
    A([New Order]) --> B[Validate Order Info]
    B --> C{Info Valid?}
    C -->|No| D[Notify User to Correct]
    D --> B
    C -->|Yes| E[Check Inventory]

    E --> F{Inventory Sufficient?}
    F -->|No| G[Reserve Inventory/Wait Restock]
    G --> H{Inventory Met?}
    H -->|Yes| E
    H -->|Timeout| I[Cancel Order]
    I --> J([Order Cancelled])
    F -->|Yes| K[Lock Inventory]

    K --> L[Calculate Fees]
    L --> M[Initiate Payment]

    M --> N{Payment Success?}
    N -->|No| O[Order Pending Payment]
    O --> P[Wait for User Payment]
    P --> M
    N -->|Yes| Q[Confirm Order]

    Q --> R[Send Order Confirmation]
    R --> S[Arrange Shipping]
    S --> T([Order Complete])
```

### 3. Parallel Activity Processing

```mermaid
graph TD
    A([Start]) --> B[Receive Order]

    subgraph Parallel Processing
        B --> C[Query Inventory]
        B --> D[Calculate Price]
        B --> E[Prepare Packaging Materials]
    end

    C --> F{Inventory Sufficient?}
    D --> G[Fee Calculation Complete]
    E --> H[Packaging Ready]

    F -->|No| I[Notify Customer Out of Stock]
    I --> J([Process End])
    F -->|Yes| K[Continue Processing]

    G --> K
    H --> K
    K --> L[Pack Products]
    L --> M[Arrange Shipping]
    M --> N([Shipping Complete])
```

### 4. Approval Process (With Roles)

```mermaid
graph TD
    A([Submit Application]) --> B[Submit to Dept Manager]

    subgraph Dept Manager Approval
        B --> C{Manager Approved?}
        C -->|No| D[Return Modification Suggestions]
        D --> E[Modify Application]
        E --> B
        C -->|Yes| F[Submit to Director]
    end

    subgraph Director Approval
        F --> G{Director Approved?}
        G -->|No| H[Return Modification Suggestions]
        H --> E
        G -->|Yes| I[Submit to Finance]
    end

    subgraph Finance Approval
        I --> J{Finance Approved?}
        J -->|No| K[Return Modification Suggestions]
        K --> E
        J -->|Yes| L[Process Payment]
    end

    L --> M[Update Application Status]
    M --> N[Notify Applicant]
    N --> O([Approval Complete])
```

### 5. Member Level Calculation

```mermaid
graph TD
    A([Start]) --> B[Calculate Annual Spending]
    B --> C[Calculate Annual Order Count]
    C --> D[Calculate Points]

    D --> E{Amount >= 10000?}
    E -->|Yes| F[Promote to Gold Member]
    E -->|No| G{Amount >= 5000?}

    G -->|Yes| H[Maintain Silver Member]
    G -->|No| I[Maintain Regular Member]

    F --> J[Apply Gold Member Benefits]
    H --> K[Apply Silver Member Benefits]
    I --> L[Apply Regular Member Benefits]

    J --> M[Send Upgrade Notification]
    K --> M
    L --> M

    M --> N([Calculation Complete])
```

### 6. Login and Permission Verification

```mermaid
graph TD
    A([User Access]) --> B[Show Login Page]
    B --> C[Enter Username Password]

    C --> D[Submit Login Request]

    D --> E{Account Exists?}
    E -->|No| F[Prompt Account Not Found]
    F --> B
    E -->|Yes| G[Verify Password]

    G --> H{Password Correct?}
    H -->|No| I[Prompt Password Error]
    I --> J[Error Count +1]
    J --> K{Continuous Errors>=5?}
    K -->|Yes| L[Lock Account]
    L --> M[Prompt Account Locked]
    M --> N([Login Failed])
    K -->|No| B
    H -->|Yes| O[Verification Success]

    O --> P{Need Two-Factor?}
    P -->|Yes| Q[Send Verification Code]
    Q --> R[User Enters Code]
    R --> S{Code Correct?}
    S -->|No| T[Prompt Code Error]
    T --> Q
    S -->|Yes| U[Verification Passed]
    P -->|No| U

    U --> V[Generate Token]
    V --> W[Record Login Log]
    W --> X([Login Success])
```

## Usage Guide

1. **Clear Start and End**: Each process has exactly one start, multiple ends possible
2. **Activity Naming**: Use verb-object phrases (e.g., "Submit Order", "Validate Info")
3. **Decision Nodes**: Use diamonds, label clear branch conditions
4. **Parallel Processing**: Use `subgraph` to group parallel activities
5. **Swimlane Activity Diagram**: For different roles' activities, use Swimlanes

## Mermaid Activity Diagram Limitations

Mermaid's `graph TD` syntax supports:
- Start/End nodes: `([Text])` or `[[Text]]`
- Activity nodes: `[Text]`
- Decision nodes: `{Text}`
- Subgraph: `subgraph`

Does not support true parallel activity diagrams (Fork/Join), but can represent parallel concepts through visual grouping.