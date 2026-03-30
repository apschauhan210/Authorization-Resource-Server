This is much better — now we can make a **high-quality, accurate README** that actually reflects your codebase structure and will impress in interviews.
# Authorization & Resource Server (Spring Security OAuth2)

A complete **OAuth2-based authentication and authorization system** built using Spring Boot and Spring Security.

This repository demonstrates a **progressive implementation** of OAuth2:

* 🔐 Authorization Server (In-Memory)
* 🛡️ Resource Server (JWT Protected APIs)
* 🗄️ Authorization Server with Database (Production-ready)

---

## 🚀 Projects Overview

### 1️⃣ Authorization Server (In-Memory)

📁 `1. AuthorizationServer`

* Implements OAuth2 Authorization Server
* Issues JWT tokens
* Uses **in-memory client & user configuration**
* Contains:

  * `config/` → Security & OAuth configuration

---

### 2️⃣ Resource Server

📁 `2. ResourceServer`

* Secures REST APIs using JWT tokens
* Validates tokens issued by Authorization Server
* Implements role-based access

**Key Packages:**

* `config/` → Security configuration (JWT validation)
* `controllers/` → Protected REST APIs

---

### 3️⃣ Authorization Server with Database

📁 `3. AuthorizationServerWithDB`

A **production-style Authorization Server** with full layered architecture.

**Key Packages:**

* `config/` → OAuth2 & security configuration
* `security/` → Custom security logic / filters
* `controllers/` → API endpoints (auth-related)
* `services/` → Business logic
* `repositories/` → Database access (JPA)
* `entities/` → DB models
* `dtos/` → Request/response objects
* `PrimaryKeys/` → Composite keys (if used)

---

## 🧠 System Architecture

```text
Client
   ↓
Authorization Server (JWT Issuer)
   ↓
Access Token (JWT)
   ↓
Resource Server (JWT Validator)
   ↓
Protected APIs
```

---

## 🔄 OAuth2 Flow

1. Client sends authentication request
2. Authorization Server validates credentials
3. JWT Access Token is issued
4. Client calls Resource Server APIs with token
5. Resource Server:

   * Validates JWT signature
   * Extracts claims/roles
   * Grants or denies access

---

## 🛠️ Tech Stack

* Java 17+
* Spring Boot
* Spring Security 6
* Spring Authorization Server
* OAuth2 & JWT
* Spring Data JPA (DB module)
* Maven

---

## 📂 Detailed Project Structure

```text
.
├── 1. AuthorizationServer
│   └── src/main/java/com/springsecurity/authorizationserver
│       └── config/
│
├── 2. ResourceServer
│   └── src/main/java/com/springsecurity/resourceserver
│       ├── config/
│       └── controllers/
│
├── 3. AuthorizationServerWithDB
│   └── src/main/java/com/springsecurity/authorizationserverwithdb
│       ├── config/
│       ├── security/
│       ├── controllers/
│       ├── services/
│       ├── repositories/
│       ├── entities/
│       ├── dtos/
│       └── PrimaryKeys/
```

---

## ⚙️ Running the Applications

### 1. Start Authorization Server (In-Memory)

```bash
cd "1. AuthorizationServer"
./mvnw spring-boot:run
```

---

### 2. Start Resource Server

```bash
cd "2. ResourceServer"
./mvnw spring-boot:run
```

---

### 3. Start DB-based Authorization Server

```bash
cd "3. AuthorizationServerWithDB"
./mvnw spring-boot:run
```

---

## 🔐 API Access

### Resource Server Endpoints

| Method | Endpoint  | Description   | Authorization |
| ------ | --------- | ------------- | ------------- |
| GET    | `/public` | Public API    | No            |
| GET    | `/secure` | Protected API | JWT Required  |
| GET    | `/admin`  | Admin API     | Admin Role    |

---

## 🧪 Testing the Flow

### 1. Get Access Token

```bash
curl -X POST http://localhost:9000/oauth2/token \
  -d "grant_type=client_credentials" \
  -u client:secret
```

---

### 2. Call Protected API

```bash
curl -H "Authorization: Bearer <ACCESS_TOKEN>" \
http://localhost:8080/secure
```

---

## 🔑 Key Concepts Demonstrated

* OAuth2 Authorization Server setup
* JWT token generation & validation
* Spring Security filter chain
* Role-based access control
* In-memory vs database-backed authentication
* Layered architecture (Controller → Service → Repository → Entity)

---

## ⭐ Why This Project Stands Out

* Covers **end-to-end OAuth2 flow**
* Shows **evolution from basic → production-ready system**
* Demonstrates **real-world backend architecture**
* Includes **secure API design patterns**

---

## 🧑‍💻 Author

**Anuj Pratap Singh**
GitHub: [https://github.com/apschauhan210](https://github.com/apschauhan210)


