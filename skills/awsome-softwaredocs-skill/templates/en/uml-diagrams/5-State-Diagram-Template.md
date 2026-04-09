# State Diagram Template

## Template Description

State Diagram is used to describe the state changes of objects or systems, and events that trigger state transitions.

## Basic Syntax

```mermaid
stateDiagram
    [*] --> State1: Initial transition
    State1 --> State2: Event
    State2 --> [*]: Final transition

    state State3 {
        [*] --> SubState1
        SubState1 --> SubState2: Event
        SubState2 --> [*]: Complete
    }
```

## State Diagram Elements

| Syntax | Element Type | Description |
|--------|--------------|-------------|
| `[*]` | Initial State | Black dot, represents state machine start |
| `[*] --> State` | Transition Arrow | Transition with event |
| `State1 --> State2: Event` | State Transition | Trigger condition and result |
| `state Name { }` | Composite State | State containing substates |

## Template Examples

### 1. Order State Diagram

```mermaid
stateDiagram-v2
    [*] --> PendingPayment

    PendingPayment --> Paid: Payment Success
    Paid --> Cancelled: User Cancel/Timeout
    Paid --> Shipped: Merchant Ships

    Shipped --> InTransit: Logistics Picked Up
    InTransit --> Delivered: Arrived at Destination
    Delivered --> OutForDelivery: Start Delivery

    OutForDelivery --> Signed: Customer Signed
    Signed --> Completed: Complete Review
    Signed --> ReturnExchange: Apply for Return

    ReturnExchange --> Refunded: Review Passed
    ReturnExchange --> Returned: Merchant Received
    Returned --> Refunded: Refund Complete

    Cancelled --> [*]
    Refunded --> [*]
    Completed --> [*]
```

### 2. User Account State Diagram

```mermaid
stateDiagram-v2
    [*] --> Activating

    Activating --> Active: Email Verified
    Activating --> Expired: Verification Timeout

    Status --> Active: Admin Activates
    Status --> Frozen: Abnormal Login/Violation
    Status --> PendingReview: Profile Update
    PendingReview --> Active: Review Passed
    PendingReview --> Abnormal: Review Rejected

    Frozen --> Active: Unfreeze Request
    Frozen --> Banned: Serious Violation

    Active --> Frozen: Risk Control Triggered
    Active --> PendingReview: Modify Key Info

    Banned --> [*]
    Expired --> [*]
```

### 3. Thread State Diagram

```mermaid
stateDiagram-v2
    [*] --> New: new Thread()

    New --> Runnable: start()
    Runnable --> Running: Acquire CPU

    Running --> Runnable: Time Slice Expired
    Running --> Blocked: wait()/sleep()/IO
    Running --> WaitingLock: synchronized

    Blocked --> Runnable: Condition Met
    WaitingLock --> Runnable: Lock Acquired

    Running --> Terminated: run() ends
    WaitingLock --> Terminated: uncaughtException
```

### 4. Composite State Diagram (Order Lifecycle)

```mermaid
stateDiagram-v2
    [*] --> PendingPayment

    state PendingPayment {
        [*] --> Initialized
        Initialized --> Calculating: Calculate Fees
        Calculating --> WaitingPayment: Generate Order
        WaitingPayment --> Timeout: 30 min No Payment
        Initialized --> Cancelled: User Cancels
        Timeout --> [*]: Auto Cancel
        Cancelled --> [*]
    }

    PendingPayment --> Paid: Payment Success

    state Paid {
        [*] --> PaymentConfirmed
        PaymentConfirmed --> Preparing: Confirm Payment
        Preparing --> WaitingShipment: Goods Prepared
    }

    Paid --> TransactionClosed: Refund Cancel

    Paid --> Shipped: Merchant Ships

    state Shipped {
        [*] --> ShippedFromWarehouse
        ShippedFromWarehouse --> InTransit: Logistics Picked Up
        InTransit --> OutForDelivery: Arrived at Destination
        OutForDelivery --> WaitingSignature: Courier Delivering
    }

    Shipped --> ReturnExchange: Apply for After-sales
    OutForDelivery --> Signed: Customer Signed

    state ReturnExchange {
        [*] --> Applying
        Applying --> Reviewing: Submit Application
        Reviewing --> Passed: Review Passed
        Reviewing --> Rejected: Review Rejected
        Passed --> Returning: Customer Returns
        Rejected --> [*]
        Returning --> Received: Merchant Received
        Received --> Refunding: Inspection Complete
        Refunding --> Refunded: Refund Complete
    }

    Signed --> Completed: Complete Transaction
    Signed --> ReturnExchange: Apply for After-sales
    Completed --> [*]
    Refunded --> [*]
```

### 5. Document State Diagram (Workflow)

```mermaid
stateDiagram-v2
    [*] --> Draft

    Draft --> UnderReview: Submit for Review
    UnderReview --> ReviewPassed: Reviewer Approved
    ReviewPassed --> Publishing: Waiting to Publish
    Publishing --> Published: Execute Publish
    Published --> Archived: Exceeded Retention Period

    UnderReview --> ReviewRejected: Reviewer Rejected
    ReviewRejected --> Draft: Modify and Resubmit

    Draft --> Discarded: Author Discarded
    ReviewRejected --> Discarded: Author Confirmed Discard

    Published --> Discarded: Emergency Unpublish
    Published --> Updating: Initiate Revision
    Updating --> Published: Republish

    Discarded --> [*]
    Archived --> [*]
```

### 6. HTTP Request State Diagram

```mermaid
stateDiagram-v2
    [*] --> Idle

    Idle --> Requesting: Initiate Request

    Requesting --> Success: 2xx Response
    Requesting --> ClientError: 4xx Response
    Requesting --> ServerError: 5xx Response
    Requesting --> NetworkError: Connection Failed/Timeout
    Requesting --> Cancelled: abort()

    ClientError --> Retrying: Auto Retry
    ClientError --> Ended: Manual Handling

    ServerError --> Retrying: Auto Retry
    ServerError --> Ended: Exceeded Retry Count

    Retrying --> Requesting: Retry Count < 3
    Retrying --> Ended: Retry Count >= 3

    NetworkError --> Retrying: Auto Retry
    NetworkError --> Ended: Exceeded Retry Count

    Success --> Ended: Process Response
    Cancelled --> Ended

    Ended --> [*]
```

## Usage Guide

1. **Identify States**: Determine all possible states an object may be in
2. **Identify Transitions**: Determine conditions and events between states
3. **Initial and Final States**: Clarify start and end points
4. **Composite States**: For complex objects, use nested substates
5. **Action Labels**: Label actions next to transition arrows (guard conditions)

## Difference Between State Diagram and Activity Diagram

| Feature | State Diagram | Activity Diagram |
|---------|--------------|------------------|
| Focus | Object state changes | Activity execution flow |
| Nodes | States | Activities |
| Transitions | Event-triggered | Sequential execution |
| Parallel | Generally not supported | Supports parallel activities |
| Applicable Scenario | State machines, lifecycles | Business processes, workflows |