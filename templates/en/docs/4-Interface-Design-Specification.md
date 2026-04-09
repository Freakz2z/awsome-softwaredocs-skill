# Interface Design Specification (ID)

## Document Information

| Item | Content |
|------|---------|
| Document Name | Interface Design Specification |
| Document Number | ID-{{projectCode}}-V1.0 |
| Version | V1.0 |
| Date | {{createdDate}} |
| Author | {{author}} |

---

## 1. Introduction

### 1.1 Purpose

This document defines the detailed specifications for all interfaces of **{{projectName}}**, including internal and external interfaces.

### 1.2 Interface Overview

| Interface Type | Quantity | Description |
|----------------|----------|-------------|
| REST API | X | Frontend-backend interaction interfaces |
| Internal Interfaces | X | Inter-service calls |
| Third-party Interfaces | X | External system integration |

---

## 2. REST API Design

### 2.1 API Specification

#### 2.1.1 Basic Specification

- **Base URL**: `https://api.example.com/v1`
- **Authentication**: Bearer Token (JWT)
- **Request Format**: JSON (`Content-Type: application/json`)
- **Response Format**: JSON
- **Character Encoding**: UTF-8

#### 2.1.2 Common Response Format

```json
{
    "code": 200,
    "message": "success",
    "data": {},
    "timestamp": "2024-01-01T12:00:00Z",
    "requestId": "uuid"
}
```

#### 2.1.3 Error Response Format

```json
{
    "code": 400,
    "message": "Parameter error",
    "errors": [
        {
            "field": "username",
            "message": "Username cannot be empty"
        }
    ],
    "timestamp": "2024-01-01T12:00:00Z",
    "requestId": "uuid"
}
```

#### 2.1.4 HTTP Status Codes

| Status Code | Description |
|-------------|-------------|
| 200 | Success |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

### 2.2 User Management Module

#### 2.2.1 User-Related Interfaces

##### Get User List

```
GET /users
```

**Request Parameters**:
| Parameter | Type | Location | Required | Description |
|-----------|------|----------|----------|-------------|
| page | int | query | No | Page number, default 1 |
| pageSize | int | query | No | Page size, default 20 |
| keyword | string | query | No | Search keyword |

**Response Example**:
```json
{
    "code": 200,
    "data": {
        "list": [
            {
                "id": "uuid",
                "username": "johndoe",
                "email": "johndoe@example.com",
                "status": "ACTIVE",
                "createdAt": "2024-01-01T12:00:00Z"
            }
        ],
        "pagination": {
            "page": 1,
            "pageSize": 20,
            "total": 100,
            "totalPages": 5
        }
    }
}
```

##### Get User Details

```
GET /users/{id}
```

**Path Parameters**:
| Parameter | Type | Description |
|-----------|------|-------------|
| id | string | User ID |

**Response Example**:
```json
{
    "code": 200,
    "data": {
        "id": "uuid",
        "username": "johndoe",
        "email": "johndoe@example.com",
        "phone": "13800138000",
        "status": "ACTIVE",
        "roles": ["ADMIN", "USER"],
        "createdAt": "2024-01-01T12:00:00Z",
        "updatedAt": "2024-01-01T12:00:00Z"
    }
}
```

##### Create User

```
POST /users
```

**Request Body**:
```json
{
    "username": "johndoe",
    "password": "Password123!",
    "email": "johndoe@example.com",
    "phone": "13800138000",
    "roleIds": ["role-1", "role-2"]
}
```

**Response Example**:
```json
{
    "code": 201,
    "data": {
        "id": "uuid",
        "username": "johndoe"
    }
}
```

##### Update User

```
PUT /users/{id}
```

##### Delete User

```
DELETE /users/{id}
```

### 2.3 Authentication Module

#### 2.3.1 User Login

```
POST /auth/login
```

**Request Body**:
```json
{
    "username": "johndoe",
    "password": "Password123!"
}
```

**Response Example**:
```json
{
    "code": 200,
    "data": {
        "accessToken": "eyJhbGciOiJIUzI1NiIs...",
        "refreshToken": "eyJhbGciOiJIUzI1NiIs...",
        "expiresIn": 7200,
        "tokenType": "Bearer"
    }
}
```

#### 2.3.2 Refresh Token

```
POST /auth/refresh
```

### 2.4 Business Module

#### [Module Name]

##### [Interface Name]

```
[GET/POST/PUT/DELETE] /[module]/[resource]
```

**Description**: [Description]

**Request Parameters**: [Parameter table]

**Request Body**:
```json
{}
```

**Response Example**:
```json
{}
```

---

## 3. Internal Interfaces

### 3.1 Inter-Service Communication Protocol

| Communication Mode | Protocol | Description |
|-------------------|----------|-------------|
| Synchronous Call | HTTP/gRPC | Real-time response |
| Asynchronous Message | RabbitMQ/Kafka | Message queue |

### 3.2 Internal Interface List

| Interface Name | Caller | Receiver | Protocol | Description |
|----------------|--------|---------|----------|-------------|
| [Interface 1] | [Service A] | [Service B] | HTTP | [Description] |

### 3.3 Internal Interface Detailed Definition

#### 3.3.1 [Interface Name]

**Service**: [Service name]
**Protocol**: HTTP
**Method**: POST
**Path**: `/internal/[module]/[action]`

**Request Headers**:
| Header Name | Value | Description |
|-------------|-------|-------------|
| X-Service-Id | string | Service identifier |
| X-Request-Id | string | Request tracking ID |

**Request Body**:
```json
{}
```

**Response Body**:
```json
{}
```

---

## 4. Third-Party Interfaces

### 4.1 Third-Party Service List

| Provider | Interface Type | Purpose | Status |
|----------|---------------|---------|--------|
| [Provider 1] | [SMS/Payment/Map/etc.] | [Purpose] | [Integrated/Pending] |

### 4.2 Interface Detailed Definition

#### 4.2.1 [Third-Party Service] - [Interface Name]

**Provider**: {{author}}
**Interface URL**: [URL]
**Authentication**: [Method]

**Request Parameters**:
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|

**Request Example**:
```json
{}
```

**Response Example**:
```json
{}
```

---

## 5. Message Queue Design

### 5.1 Queue List

| Queue Name | Type | Description | Consumer |
|------------|------|-------------|----------|
| [Queue 1] | [Queue/Topic] | [Description] | [Consumer service] |

### 5.2 Message Format

```json
{
    "messageId": "uuid",
    "topic": "topic-name",
    "action": "action-name",
    "payload": {},
    "metadata": {
        "timestamp": 1704067200,
        "source": "service-name"
    }
}
```

### 5.3 Message Examples

#### 5.3.1 [Message Name]

**Topic**: [topic name]
**Routing Key**: [key]

```json
{
    "messageId": "uuid",
    "action": "user.created",
    "payload": {
        "userId": "uuid",
        "username": "johndoe",
        "email": "johndoe@example.com"
    }
}
```

---

## 6. Interface Security

### 6.1 Authentication Mechanism

| Interface Type | Authentication | Description |
|---------------|----------------|-------------|
| External API | JWT Token | Bearer Token |
| Internal API | Service Auth | Inter-service authentication |
| Third-party API | OAuth2/API Key | Per provider |

### 6.2 Rate Limiting Strategy

| Rate Limit Dimension | Limit Value | Time Window |
|---------------------|-------------|------------|
| IP Dimension | 1000 requests | 1 minute |
| User Dimension | 100 requests | 1 minute |
| Interface Dimension | [Value] | [Window] |

### 6.3 Sensitive Data Handling

- Password: Encrypted storage, not returned in interfaces
- Phone: Masked (138****8000)
- ID Card: Masked
- Bank Card: Masked

---

**Document Approval**:

| Role | Name | Date | Signature |
|------|------|------|-----------|
| API Designer | | | |
| Technical Lead | | | |