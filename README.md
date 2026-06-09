# 🔌 API Testing Project

![Java](https://img.shields.io/badge/Java-11-orange?logo=java)
![RestAssured](https://img.shields.io/badge/RestAssured-5.4-green)
![TestNG](https://img.shields.io/badge/TestNG-7.9-blue)
![Postman](https://img.shields.io/badge/Postman-Collection-orange?logo=postman)
![CI](https://github.com/YOUR_USERNAME/api-testing-project/actions/workflows/ci.yml/badge.svg)

A complete REST API test automation project using **Java**, **RestAssured**, and **TestNG** — with a full **Postman collection** included. Tests run against [reqres.in](https://reqres.in), a free public REST API.

---

## 📁 Project Structure

```
api-testing-project/
├── src/test/java/
│   ├── models/                     # POJOs for request/response
│   │   ├── User.java
│   │   └── CreateUserRequest.java
│   ├── tests/                      # TestNG test classes
│   │   ├── GetUsersTest.java        # 7 GET endpoint tests
│   │   ├── CrudOperationsTest.java  # POST, PUT, PATCH, DELETE, Auth tests
│   │   └── ResponseValidationTest.java  # Headers, response time, pagination
│   └── utils/
│       └── ApiConfig.java           # RestAssured base configuration
├── src/test/resources/
│   └── testng.xml
├── postman/
│   └── Reqres_API_Collection.postman_collection.json
├── .github/workflows/
│   └── ci.yml                       # Runs Java tests + Newman (Postman)
└── pom.xml
```

---

## ✅ Test Coverage

### GET Endpoints (7 tests)
| Test ID | Scenario |
|---------|----------|
| TC_GET_01 | GET /users returns 200 OK |
| TC_GET_02 | Response contains all required fields |
| TC_GET_03 | User objects have id, email, first_name, last_name |
| TC_GET_04 | Pagination — page 1 and page 2 return different users |
| TC_GET_05 | GET /users/{id} returns correct single user |
| TC_GET_06 | GET /users/9999 returns 404 Not Found |
| TC_GET_07 | All email fields are valid format |

### CRUD + Auth (8 tests)
| Test ID | Scenario |
|---------|----------|
| TC_POST_01 | POST /users creates user — returns 201 |
| TC_POST_02 | POST with missing fields — still returns 201 |
| TC_PUT_01 | PUT /users/{id} full update — returns 200 |
| TC_PATCH_01 | PATCH /users/{id} partial update — returns 200 |
| TC_DELETE_01 | DELETE /users/{id} — returns 204 No Content |
| TC_AUTH_01 | POST /login valid credentials — returns token |
| TC_AUTH_02 | POST /login missing password — returns 400 |
| TC_AUTH_03 | POST /register valid data — returns token |

### Response Validation (5 tests)
| Test ID | Scenario |
|---------|----------|
| TC_RESP_01 | Response time under 5 seconds |
| TC_RESP_02 | Content-Type header is application/json |
| TC_RESP_03 | Response body is not empty |
| TC_RESP_04 | Delayed endpoint handled correctly |
| TC_RESP_05 | Pagination math is consistent |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Java 11 | Programming language |
| RestAssured 5.4 | API automation library |
| TestNG 7.9 | Test framework |
| Jackson | JSON serialization/deserialization |
| Maven | Build tool |
| Postman | Manual & exploratory API testing |
| Newman | CLI runner for Postman collections |
| GitHub Actions | CI/CD — runs both Java & Postman tests |

---

## 🚀 How to Run

### Prerequisites
- Java 11+, Maven 3.6+
- Node.js + npm (for Newman/Postman)

### Run Java automation
```bash
# Run smoke tests
mvn clean test -Dgroups=smoke

# Run full regression
mvn clean test -Dgroups=regression

# Run all tests
mvn clean test
```

### Run Postman collection via Newman
```bash
# Install Newman
npm install -g newman

# Run the collection
newman run postman/Reqres_API_Collection.postman_collection.json
```

---

## 🔄 CI/CD Pipeline

GitHub Actions runs **two parallel jobs** on every push:
1. **Java Tests** — smoke + regression via Maven
2. **Postman Tests** — full collection via Newman with HTML report

---

## 🧪 API Under Test

All tests use **[reqres.in](https://reqres.in)** — a hosted REST API for testing.

| Endpoint | Methods Tested |
|----------|---------------|
| `/users` | GET, POST |
| `/users/{id}` | GET, PUT, PATCH, DELETE |
| `/login` | POST |
| `/register` | POST |

---

## 👤 Author

Amal
QA Engineer | Java | RestAssured | Postman | API Automation  
[LinkedIn](https://www.linkedin.com/in/amal-a49244350) • [GitHub](https://github.com/am-qa-engineer))
