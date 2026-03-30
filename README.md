# Authorization Resource Server

A **Spring Boot OAuth2 Resource Server** that validates and protects APIs using JWT tokens issued by an Authorization Server.

This project demonstrates how to build a secure backend using **Spring Security + OAuth2 Resource Server** concepts.

---

## 🚀 Features

* 🔐 OAuth2 Resource Server using JWT
* 🛡️ Secure REST APIs with role-based access
* 📦 Spring Boot 3 + Spring Security 6
* 🔑 Token validation using public keys / JWKS
* ⚙️ Configurable security rules
* 🧪 Ready for integration with any Authorization Server (Auth Server)

---

## 🧠 Architecture Overview

```
Client → Authorization Server → Access Token (JWT)
       → Resource Server (this app) → Protected APIs
```

* The **Authorization Server** issues access tokens
* The **Resource Server** validates tokens and serves protected resources
* Tokens are typically validated using **JWKS or introspection** ([Cornucopia][1])

---

## 🛠️ Tech Stack

* Java 17+
* Spring Boot
* Spring Security
* OAuth2 Resource Server
* Maven / Gradle

---

## 📂 Project Structure

```
src/
 ├── main/
 │   ├── java/
 │   │   └── com.example.authorizationresourceserver
 │   │       ├── config/        # Security configuration
 │   │       ├── controller/    # REST endpoints
 │   │       ├── service/       # Business logic
 │   │       └── model/         # DTOs / entities
 │   └── resources/
 │       └── application.yml   # Configurations
```

---

## ⚙️ Configuration

### application.yml

```yaml
spring:
  security:
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: http://localhost:9000
```

OR using JWKS:

```yaml
spring:
  security:
    oauth2:
      resourceserver:
        jwt:
          jwk-set-uri: http://localhost:9000/.well-known/jwks.json
```

---

## 🔐 Security Configuration

Example:

```java
@Bean
SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
    http
        .authorizeHttpRequests(auth -> auth
            .requestMatchers("/public/**").permitAll()
            .anyRequest().authenticated()
        )
        .oauth2ResourceServer(OAuth2ResourceServerConfigurer::jwt);

    return http.build();
}
```

---

## 📡 API Endpoints

| Method | Endpoint  | Description         | Access       |
| ------ | --------- | ------------------- | ------------ |
| GET    | `/public` | Public API          | Public       |
| GET    | `/secure` | Protected API       | JWT required |
| GET    | `/admin`  | Admin-only endpoint | Role-based   |

---

## ▶️ Running the Application

### 1. Clone the repo

```bash
git clone https://github.com/apschauhan210/Authorization-Resource-Server.git
cd Authorization-Resource-Server
```

### 2. Run the app

```bash
./mvnw spring-boot:run
```

---

## 🧪 Testing APIs

Use tools like:

* Postman
* curl

### Example:

```bash
curl -H "Authorization: Bearer <ACCESS_TOKEN>" \
http://localhost:8080/secure
```

---

## 🔗 Integration with Authorization Server

This resource server works with any OAuth2 Authorization Server such as:

* Spring Authorization Server
* Auth0
* Keycloak

These servers issue JWT tokens that this service validates.

---

## 📌 Key Concepts

* **Resource Server**: Protects APIs and validates tokens
* **Authorization Server**: Issues access tokens
* **JWT**: Self-contained token with claims
* **Scopes & Roles**: Used for access control

---

## 🧑‍💻 Author

**Anuj Pratap Singh**

* GitHub: [https://github.com/apschauhan210](https://github.com/apschauhan210)

---

## ⭐ Contribution

Feel free to fork the repo and submit pull requests!
