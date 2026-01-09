
# URL Shortener API

A robust Spring Boot REST API that transforms long, cumbersome URLs into shortened, manageable links with expiration dates.

## 🚀 Features

* **Shorten URLs:** Generate unique, high-collision-resistant short codes for long URLs.
* **Redirection Logic:** Retrieve the original URL and check for expiration before redirecting.
* **Validation:** Ensures validity dates are set in the future.
* **Error Handling:** Custom exceptions for `UrlNotFound` and `UrlExpired` scenarios.

## 🛠️ Tech Stack

* **Java 25**
* **Spring Boot 4.0.1**
* **Spring Data JPA**
* **Gradle** (Build Tool)
* **Lombok** (For boilerplate reduction)

---

## 🏗️ Project Structure

The project follows a clean layered architecture as seen in the source tree:
* `controller`: Handles incoming REST requests.
* `service`: Contains business logic for short-code generation and expiration checks.
* `repository`: Data access layer for URL entities.
* `dto`: Data Transfer Objects for clean API request/response contracts.
* `entity`: JPA entities for database mapping.

---

## 🚦 Getting Started

### Prerequisites
* JDK 25
* A configured IDE (IntelliJ IDEA or VS Code)

### Run the Application
1. Clone the repository.
2. Navigate to the root directory.
3. Run the following command:
   ```bash
   ./gradlew bootRun

```

The server will start at `http://localhost:8080`.

---

## 📖 API Reference

### 1. Shorten a URL

**Endpoint:** `POST /api/shorten`

**Request Body:**

```json
{
   "originalUrl":"https://abusaeed2433.github.io/java-in-readme-site/",
   "validity":"2026-01-10T15:50:50"
}

```

**Success Response:**

```json
{
    "shortUrl": "http://localhost:8080/r/dnRwDnzZl",
    "originalUrl": "https://abusaeed2433.github.io/java-in-readme-site/",
    "validity": "2026-01-10T15:50:50"
}

```

### 2. Get Original URL (Redirection)

**Endpoint:** `GET /r/{shortCode}`

**Success Response:**

```json
{
    "originalUrl": "https://abusaeed2433.github.io/java-in-readme-site/",
    "validity": "2026-01-10T15:50:50"
}

```

---

## 🧪 Error Handling

The API returns specific error messages for:

* **404 Not Found:** When a short code does not exist in the database.
* **410 Gone / 400 Bad Request:** When the URL validity period has expired.
* **400 Bad Request:** When trying to create a URL with a past validity date.

```

