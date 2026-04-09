# Class Diagram Template

## Template Description

Class Diagram is used to show classes, interfaces, and their relationships in a system.

## Basic Syntax

```mermaid
classDiagram
    class ClassName {
        +field1: Type
        +field2: Type
        +method1(): ReturnType
        +method2(param: Type): ReturnType
    }

    class InterfaceName~T~ {
        <<interface>>
        +method1(): ReturnType
    }

    className --|> InterfaceName : implements
    className -- OtherClass : association
    className o-- OtherClass : composition
    className *-- OtherClass : aggregation
    className ..> OtherClass : dependency
```

## Symbol Reference

| Symbol | Relationship Type | Description |
|--------|------------------|-------------|
| `-->` | Association | Connection between classes |
| `*--` | Composition | Strong "has-a" relationship, parts cannot exist independently |
| `o--` | Aggregation | Weak "has-a" relationship, parts can exist independently |
| `--|>` | Generalization | Inheritance |
| `..|>` | Realization | Interface implementation |
| `..>` | Dependency | One class uses another |
| `--` | Direct Association | Bidirectional association |

## Template Examples

### 1. Basic Entity Class

```mermaid
classDiagram
    class User {
        +Long id
        +String username
        +String email
        +String password
        +String phone
        +UserStatus status
        +LocalDateTime createdAt
        +LocalDateTime updatedAt
        +createUser()
        +updateUser()
        +deleteUser()
        +findById()
        +findByUsername()
    }

    class UserStatus {
        <<enumeration>>
        ACTIVE
        INACTIVE
        DELETED
    }

    User --> UserStatus
```

### 2. Inheritance Relationship

```mermaid
classDiagram
    class Person {
        +Long id
        +String name
        +Integer age
        +String gender
    }

    class Student {
        +String studentId
        +String major
        +Double gpa
        +enroll()
        +withdraw()
    }

    class Teacher {
        +String teacherId
        +String department
        +Double salary
        +assignGrade()
        +teach()
    }

    class Employee {
        +String employeeId
        +String position
        +LocalDateTime hireDate
        +work()
        +takeLeave()
    }

    Person <|-- Student : inherits
    Person <|-- Teacher : inherits
    Person <|-- Employee : inherits
```

### 3. Interface and Implementation

```mermaid
classDiagram
    class Payable {
        <<interface>>
        +pay(amount: Double): Boolean
        +refund(amount: Double): Boolean
    }

    class CreditCardPayment {
        -String cardNumber
        -String cvv
        -LocalDateTime expiryDate
        +pay(amount: Double): Boolean
        +refund(amount: Double): Boolean
        -validateCard(): Boolean
    }

    class PayPalPayment {
        -String email
        -String transactionId
        +pay(amount: Double): Boolean
        +refund(amount: Double): Boolean
    }

    class BankTransferPayment {
        -String accountNumber
        -String routingNumber
        +pay(amount: Double): Boolean
        +refund(amount: Double): Boolean
    }

    Payable <|.. CreditCardPayment : implements
    Payable <|.. PayPalPayment : implements
    Payable <|.. BankTransferPayment : implements
```

### 4. Composition/Aggregation Relationship

```mermaid
classDiagram
    class Department {
        +Long id
        +String name
        +String location
        +hireEmployee()
        +fireEmployee()
    }

    class Employee {
        +Long id
        +String name
        +String position
        +Double salary
        +work()
        +takeVacation()
    }

    class Project {
        +Long id
        +String name
        +String description
        +ProjectStatus status
        +start()
        +complete()
        +cancel()
    }

    class Task {
        +Long id
        +String title
        +String description
        +TaskStatus status
        +assign()
        +complete()
    }

    Department "1" o-- "n" Employee : contains
    Department "1" *-- "n" Project : manages
    Project "1" o-- "n" Task : contains
    Employee "1" -- "n" Task : assigned to
```

### 5. Complete Business Class Diagram

```mermaid
classDiagram
    class Order {
        +Long id
        +String orderNumber
        +LocalDateTime orderDate
        +OrderStatus status
        +Double totalAmount
        +ShippingAddress shippingAddress
        +createOrder()
        +cancelOrder()
        +calculateTotal()
        +addItem()
        +removeItem()
    }

    class OrderItem {
        +Long id
        +Integer quantity
        +Double unitPrice
        +Double subtotal
        +getSubtotal()
    }

    class Product {
        +Long id
        +String name
        +String description
        +Double price
        +Integer stock
        +String sku
        +Category category
        +updateStock()
        +isAvailable()
    }

    class Category {
        +Long id
        +String name
        +String description
        +Category parent
        +List~Category~ children
    }

    class Customer {
        +Long id
        +String name
        +String email
        +String phone
        +List~Order~ orders
        +ShoppingCart cart
        +placeOrder()
        +viewOrderHistory()
    }

    class ShoppingCart {
        +Long id
        +List~CartItem~ items
        +addItem()
        +removeItem()
        +updateQuantity()
        +clear()
        +getTotal()
    }

    class CartItem {
        +Long id
        +Integer quantity
        +addQuantity()
        +reduceQuantity()
    }

    Customer "1" *-- "1" ShoppingCart : has
    Customer "1" o-- "n" Order : places
    ShoppingCart "1" o-- "n" CartItem : contains
    CartItem "1" -- "1" Product : references
    Order "1" *-- "n" OrderItem : contains
    OrderItem "1" -- "1" Product : references
    Product "n" -- "1" Category : belongs to
    Category "1" o-- "n" Category : parent-child
```

### 6. Design Pattern Example

```mermaid
classDiagram
    class Subject {
        <<interface>>
        +attach(observer: Observer)
        +detach(observer: Observer)
        +notify()
    }

    class ConcreteSubject {
        -String state
        -List~Observer~ observers
        +getState()
        +setState(state: String)
        +attach(observer: Observer)
        +detach(observer: Observer)
        +notify()
    }

    class Observer {
        <<interface>>
        +update(subject: Subject)
    }

    class ConcreteObserverA {
        +update(subject: Subject)
    }

    class ConcreteObserverB {
        +update(subject: Subject)
    }

    Subject <|.. ConcreteSubject : implements
    Subject <|.. Observer : implements
    ConcreteSubject o-- "n" Observer : notifies
    Observer <|.. ConcreteObserverA : implements
    Observer <|.. ConcreteObserverB : implements
```

## Usage Guide

1. **Class Names**: Capitalize first letter, use nouns
2. **Properties**: Visibility + Name + Type
   - `+` public
   - `-` private
   - `#` protected
   - `~` package
3. **Methods**: Visibility + Name + Parameters + Return Type
4. **Relationship Lines**: Label multiplicity on both ends

## Multiplicity Reference

| Notation | Meaning |
|----------|---------|
| 1 | Exactly one |
| 0..1 | Zero or one |
| n | Exactly n |
| 0..* or * | Zero or more |
| 1..* | One or more |
| m..n | At least m, at most n |