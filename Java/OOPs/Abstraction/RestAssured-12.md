# Java Abstraction Master Guide – Part 13

## REST Assured Framework Usage (API Abstraction in Automation)

---

# Table of Contents

1. Why REST Assured Uses Abstraction
2. RequestSpecification Abstraction
3. ResponseSpecification Abstraction
4. Given-When-Then Model
5. API Framework Architecture
6. Serialization & Deserialization Abstraction
7. JSON Parsing Abstraction
8. Real Project API Framework Design
9. Logging & Reporting in API Framework
10. Reusable Utility Layer
11. Hybrid API + UI Framework Concept
12. Interview Questions
13. Tricky Questions
14. Revision Notes
15. Cheat Sheet

---

# 1. Why REST Assured Uses Abstraction

REST Assured hides:

* HTTP request complexity
* Serialization logic
* Response parsing
* Header handling

---

## Developer sees:

```java id="r1"
given()
.when()
.get("/users")
.then()
.statusCode(200);
```

---

## Internally:

```text id="r2"
HTTP Client → Request Builder → Response Parser → Validator
```

---

✔ Everything is abstracted using fluent APIs

---

# 2. RequestSpecification Abstraction

Represents reusable request configuration.

---

## Example:

```java id="r3"
RequestSpecification req =
    given()
    .baseUri("https://api.example.com")
    .header("Content-Type", "application/json");
```

---

## Benefit:

```text id="r4"
No need to repeat base URL, headers, auth
```

---

# 3. ResponseSpecification Abstraction

Used for reusable response validation.

---

## Example:

```java id="r5"
ResponseSpecification resSpec =
    new ResponseSpecBuilder()
    .expectStatusCode(200)
    .build();
```

---

## Usage:

```java id="r6"
then()
.spec(resSpec);
```

---

✔ Centralized validation logic

---

# 4. Given-When-Then Model

REST Assured uses BDD style abstraction.

---

## Structure:

```text id="r7"
given() → Setup
when() → Action
then() → Validation
```

---

## Example:

```java id="r8"
given()
    .baseUri("https://api.com")
.when()
    .get("/users")
.then()
    .statusCode(200);
```

---

✔ Improves readability
✔ Acts like natural language

---

# 5. API Framework Architecture

---

## Standard Layered Design:

```text id="r9"
Test Layer (TestNG)
    ↓
Service Layer (API logic)
    ↓
Request Builder Layer
    ↓
Utility Layer
    ↓
Config Layer
```

---

✔ Fully abstraction-based architecture

---

# 6. Serialization & Deserialization Abstraction

---

## Serialization:

Java Object → JSON

```java id="r10"
given()
.body(userObject)
.post("/users");
```

---

## Deserialization:

JSON → Java Object

```java id="r11"
User user =
    response.as(User.class);
```

---

✔ No manual parsing required

---

# 7. JSON Parsing Abstraction

---

## Using JsonPath:

```java id="r12"
String name =
    response.jsonPath()
    .getString("name");
```

---

## Abstraction benefit:

* No manual JSON traversal
* Structured data access

---

# 8. Real Project API Framework Design

---

## Architecture:

```text id="r13"
Test Layer
   ↓
API Service Layer
   ↓
Request Builder
   ↓
Config Manager
   ↓
Utils (Auth, JSON, Logging)
```

---

## Example:

```java id="r14"
Response res =
    ApiClient.get("/users");
```

---

✔ Clean separation of concerns

---

# 9. Logging & Reporting in API Framework

---

## Logging:

```java id="r15"
log().all();
```

---

## Reporting Tools:

* Extent Reports
* Allure Reports

---

✔ Abstracts test execution details

---

# 10. Reusable Utility Layer

---

## Example:

```java id="r16"
class ApiUtils {

    public static String getBaseUrl() {
        return "https://api.com";
    }
}
```

---

✔ Prevents duplication
✔ Central configuration management

---

# 11. Hybrid API + UI Framework Concept

---

## Flow:

```text id="r17"
API → Create Data
UI → Validate Data
```

---

## Example:

1. Create user via API
2. Login via UI
3. Validate UI data

---

✔ Real enterprise testing approach

---

# 12. Interview Questions

---

## Q1: What is RequestSpecification?

Answer:
It is a reusable configuration for API requests.

---

## Q2: What is ResponseSpecification?

Answer:
Reusable validation rules for responses.

---

## Q3: What is given-when-then?

Answer:
BDD style API testing structure.

---

## Q4: Why REST Assured is abstraction-based?

Answer:
It hides HTTP complexity using fluent APIs.

---

## Q5: What is serialization?

Answer:
Java object → JSON conversion.

---

# 13. Tricky Questions

---

## Q1: Can REST Assured work without given()?

Answer:
No, it is core abstraction.

---

## Q2: Is JSON parsing manual?

Answer:
No, JsonPath abstracts it.

---

## Q3: Can we reuse RequestSpecification?

Answer:
Yes, it improves maintainability.

---

## Q4: Is REST Assured synchronous?

Answer:
Yes, by default.

---

# 14. Revision Notes

```text id="r18"
REST Assured Abstraction:
-------------------------
given() → setup
when() → action
then() → validation

RequestSpecification → request abstraction
ResponseSpecification → response abstraction
JsonPath → parsing abstraction
Serialization → object mapping abstraction
```

---

# 15. Cheat Sheet

```text id="r19"
given() → request setup
when() → API call
then() → validation

RequestSpec → reusable request config
ResponseSpec → reusable response checks
JsonPath → JSON reader
```

---

# 🚀 NEXT PART (Part 14 Preview)

## Advanced Interview Questions

* Abstraction deep questions
* Real scenario-based design questions
* Tricky output-based Java questions
* Coding challenges (core + framework)
* Design-based interview rounds
* Selenium + API + Spring combined scenarios

---

If you say **“next part”**, I’ll continue with:

👉 **PART 14 – Advanced Interview Questions + Tricky + Coding + Design Scenarios**
