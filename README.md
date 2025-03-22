# Nooritalk WhatsApp API Backend

This is a **Spring Boot-based** backend for integrating the **WhatsApp Business API (Interakt)**. It allows sending messages, handling authentication, and managing communication via Interakt.

## 🚀 Features
- WhatsApp Business API Integration using Interakt
- Authentication with JWT
- Logging & Exception Handling
- RESTful API endpoints for message communication
- Error handling with proper HTTP responses

## 📌 Tech Stack
- **Java 11/17**
- **Spring Boot 2.7+**
- **Spring Security (JWT Authentication)**
- **Spring Data JPA (MySQL)**
- **Lombok**
- **Log4j (Logging)**
- **Postman (API Testing)**

---

## 📂 Project Structure
```
Nooritalk-WhatsApp-Backend/
│── src/
│   ├── main/
│   │   ├── java/com/nooritalk/
│   │   │   ├── controller/
│   │   │   │   ├── WhatsAppController.java
│   │   │   ├── service/
│   │   │   │   ├── WhatsAppService.java
│   │   │   ├── entity/
│   │   │   │   ├── Admin.java
│   │   │   ├── repository/
│   │   │   │   ├── AdminRepository.java
│   │   │   ├── security/
│   │   │   │   ├── JwtUtil.java
│   │   │   ├── config/
│   │   │   │   ├── SecurityConfig.java
│   │   │   ├── exception/
│   │   │   │   ├── GlobalExceptionHandler.java
│   │   │   ├── NooritalkApplication.java
│   ├── resources/
│   │   ├── application.yml
│── pom.xml (For Maven) OR build.gradle (For Gradle)
│── README.md
```

---

## ⚙️ Setup Instructions

### **1️⃣ Clone the Repository**
```sh
git clone https://github.com/ParagSneh/nooritalk-whatsapp-backend.git
cd nooritalk-whatsapp-backend
```

### **2️⃣ Configure `application.yml`**
Create `src/main/resources/application.yml` and configure it as follows:

```yaml
server:
  port: 8080

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/nooritalk
    username: root
    password: password
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true

interakt:
  api:
    base-url: "https://api.interakt.ai/v1/public/message/"
    auth-token: "Bearer YOUR_AUTH_TOKEN"
```

### **3️⃣ Build & Run the Project**
#### **For Maven**
```sh
mvn clean install
mvn spring-boot:run
```
#### **For Gradle**
```sh
./gradlew build
./gradlew bootRun
```

---

## 📌 API Endpoints
### **1️⃣ Send WhatsApp Message**
**Request:**
```http
POST /api/whatsapp/send
Content-Type: application/json
Authorization: Bearer YOUR_AUTH_TOKEN
```
**Body:**
```json
{
  "fullPhoneNumber": "+919876543210",
  "callbackData": "some_callback_data",
  "type": "Text",
  "data": {
    "message": "Hello, this is a test message!"
  }
}
```
**Response:**
```json
{
  "result": true,
  "message": "Message queued for sending via Interakt. Check webhook for delivery status",
  "id": "d58aeff7-a81c-47a7-9b67-f381e13f6c4e"
}
```

---

## 🛑 Error Handling
| **Error** | **HTTP Code** | **Message** |
|-----------|-------------|-------------|
| Invalid Request | 400 | `Bad Request` |
| Unauthorized | 401 | `Invalid Token` |
| Not Found | 404 | `Resource Not Found` |
| Internal Server Error | 500 | `Something Went Wrong` |

---

## 📜 Logging & Debugging
- Uses **Log4j** for structured logging
- Logs stored in `logs/nooritalk.log`

### Example Logging Configuration (`log4j2.xml`):
```xml
<Configuration status="WARN">
    <Appenders>
        <Console name="Console" target="SYSTEM_OUT">
            <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss} [%t] %-5level %logger{36} - %msg%n" />
        </Console>
        <File name="File" fileName="logs/nooritalk.log">
            <PatternLayout>
                <pattern>%d %p %c{1.} [%t] %m%n</pattern>
            </PatternLayout>
        </File>
    </Appenders>
    <Loggers>
        <Root level="info">
            <AppenderRef ref="Console" />
            <AppenderRef ref="File" />
        </Root>
    </Loggers>
</Configuration>
```

---

## 🛠️ Future Enhancements
- Webhook Handling for Message Delivery
- AI-powered WhatsApp Chatbot
- Admin Panel for Message Logs

---

## 👨‍💻 Author
**Parag Girdhari Khot**  
📧 [paragkhot07@gmail.com](mailto:paragkhot07@gmail.com)  
🔗 [GitHub](https://github.com/ParagSneh)  

---

## 📜 License
This project is licensed under the **MIT License**.

