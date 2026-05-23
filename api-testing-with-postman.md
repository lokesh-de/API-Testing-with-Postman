
# API Testing with Postman — Complete Guide (0 to 100)

---

# Table of Contents

1. Introduction to APIs
2. What is API Testing?
3. Advantages & Disadvantages
4. What is Postman?
5. Features of Postman
6. HTTP Basics
7. HTTP Methods
8. Status Codes
9. API Request & Response
10. GET Request
11. POST Request
12. PUT Request
13. PATCH Request
14. DELETE Request
15. Headers
16. Query Parameters
17. Path Parameters
18. Authentication
19. JSON Basics
20. Collections
21. Variables
22. Tests in Postman
23. Pre-request Scripts
24. Chaining APIs
25. Collection Runner
26. Data-Driven Testing
27. Newman CLI
28. Mock Servers
29. API Monitoring
30. CRUD Operations
31. REST API Basics
32. SOAP vs REST
33. GraphQL Basics
34. Security Testing
35. Performance Testing
36. CI/CD Integration
37. Best Practices
38. Interview Questions
39. Learning Roadmap
40. Final Summary

---

# 1. Introduction to APIs

## What is an API?

API stands for **Application Programming Interface**.

It allows communication between two applications.

Example:

- Mobile App ↔ Server
- Frontend ↔ Backend
- Website ↔ Database

---

## Real-Time Example

When you login to Instagram:

1. App sends username/password to server
2. Server validates credentials
3. Server returns response

This communication happens using APIs.

---

# 2. What is API Testing?

API Testing is the process of testing APIs directly without using the frontend UI.

We verify:

- Functionality
- Reliability
- Security
- Performance

---

# 3. Advantages & Disadvantages

## Advantages

- Faster than UI testing
- Easy automation
- Detects bugs early
- Better backend validation
- Supports CI/CD

## Disadvantages

- Requires technical knowledge
- Difficult for beginners
- Complex authentication handling
- Debugging can be challenging

---

# 4. What is Postman?

Postman is a popular API testing tool used for:

- Sending requests
- Testing APIs
- Automation
- Documentation
- Monitoring

Official Website:
https://www.postman.com

---

# 5. Features of Postman

- User-friendly interface
- Supports all HTTP methods
- API automation
- Environment variables
- Collection runner
- Newman CLI support
- Mock servers
- Authentication support

---

# 6. HTTP Basics

HTTP stands for HyperText Transfer Protocol.

Used for communication between client and server.

---

# 7. HTTP Methods

| Method | Purpose |
|--------|---------|
| GET | Retrieve data |
| POST | Create data |
| PUT | Update complete data |
| PATCH | Update partial data |
| DELETE | Delete data |

---

# 8. HTTP Status Codes

| Status Code | Meaning |
|-------------|---------|
| 200 | Success |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

---

# 9. API Request & Response

## Request Contains

- URL
- Method
- Headers
- Body
- Authorization

## Response Contains

- Status Code
- Response Body
- Headers
- Response Time

---

# 10. GET Request

## Example

```http
GET https://jsonplaceholder.typicode.com/posts
```

## Steps

1. Open Postman
2. Select GET
3. Enter URL
4. Click Send

---

# 11. POST Request

## Example

```http
POST https://jsonplaceholder.typicode.com/posts
```

## Request Body

```json
{
  "title": "API Testing",
  "body": "Learning Postman",
  "userId": 1
}
```

---

# 12. PUT Request

```http
PUT https://jsonplaceholder.typicode.com/posts/1
```

```json
{
  "id": 1,
  "title": "Updated Title",
  "body": "Updated Body",
  "userId": 1
}
```

---

# 13. PATCH Request

```http
PATCH https://jsonplaceholder.typicode.com/posts/1
```

```json
{
  "title": "Updated Partial Data"
}
```

---

# 14. DELETE Request

```http
DELETE https://jsonplaceholder.typicode.com/posts/1
```

---

# 15. Headers

Headers provide metadata.

## Common Headers

```http
Content-Type: application/json
Authorization: Bearer token
Accept: application/json
```

---

# 16. Query Parameters

Example:

```http
GET /users?id=1
```

---

# 17. Path Parameters

Example:

```http
GET /users/1
```

---

# 18. Authentication

## Types of Authentication

- Basic Auth
- Bearer Token
- OAuth 2.0
- API Key

---

## Bearer Token Example

```http
Authorization: Bearer your_token_here
```

---

## API Key Example

```http
x-api-key: abc123
```

---

# 19. JSON Basics

JSON stands for JavaScript Object Notation.

Example:

```json
{
  "name": "John",
  "age": 25
}
```

---

# 20. Collections in Postman

Collections help organize APIs.

Example:

```text
User APIs
Product APIs
Auth APIs
```

---

# 21. Variables in Postman

## Types

- Global Variables
- Collection Variables
- Environment Variables
- Local Variables

## Example

```text
{{base_url}}
{{token}}
```

---

# 22. Writing Tests in Postman

Postman uses JavaScript for testing.

## Status Code Validation

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

---

## Response Time Validation

```javascript
pm.test("Response time is less than 500ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});
```

---

## Response Body Validation

```javascript
pm.test("Check username", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.username).to.eql("john");
});
```

---

# 23. Pre-request Scripts

Runs before request execution.

Example:

```javascript
console.log("Before request");
```

---

# 24. Chaining APIs

Use response data from one API in another.

Example:

```javascript
pm.environment.set("token", jsonData.token);
```

---

# 25. Collection Runner

Used to run multiple APIs together.

Benefits:

- Automation
- Batch execution
- Regression testing

---

# 26. Data-Driven Testing

Use CSV or JSON files.

## CSV Example

```csv
username,password
admin,1234
test,abcd
```

---

# 27. Newman CLI

Newman is Postman’s command-line runner.

## Install Newman

```bash
npm install -g newman
```

## Run Collection

```bash
newman run collection.json
```

---

# 28. Mock Servers

Mock servers simulate APIs before backend development is completed.

Benefits:

- Frontend testing
- Early integration

---

# 29. API Monitoring

Used to monitor:

- Uptime
- Response time
- Failures

---

# 30. CRUD Operations

CRUD means:

| Operation | Method |
|-----------|--------|
| Create | POST |
| Read | GET |
| Update | PUT/PATCH |
| Delete | DELETE |

---

# 31. REST API Basics

REST stands for Representational State Transfer.

## Characteristics

- Stateless
- Client-server architecture
- Cacheable
- Uniform interface

---

# 32. SOAP vs REST

| SOAP | REST |
|------|------|
| XML only | JSON/XML |
| Heavy | Lightweight |
| Slower | Faster |
| Complex | Simple |

---

# 33. GraphQL Basics

GraphQL allows clients to request only required data.

## Advantages

- Flexible
- Efficient
- Avoids over-fetching

---

# 34. Security Testing

Check for:

- Unauthorized access
- Token validation
- SQL Injection
- Data exposure

---

# 35. Performance Testing

Measure:

- Response time
- Throughput
- Concurrency

## Popular Tools

- JMeter
- k6
- LoadRunner

---

# 36. CI/CD Integration

Postman + Newman can integrate with:

- Jenkins
- GitHub Actions
- GitLab CI
- Azure DevOps

---

# 37. Best Practices

- Use proper naming conventions
- Organize collections properly
- Use environment variables
- Validate responses
- Store secrets securely
- Automate repetitive tests

---

# 38. Common Interview Questions

## What is API testing?

Testing APIs directly without UI.

---

## Difference between PUT and PATCH?

- PUT updates entire resource
- PATCH updates partial resource

---

## What is status code 404?

Resource not found.

---

## What is Bearer Token?

Authentication token sent in Authorization header.

---

# 39. Learning Roadmap

## Beginner Level

- Learn HTTP
- Learn JSON
- Learn Postman basics

## Intermediate Level

- Automation
- Variables
- Scripting

## Advanced Level

- Newman
- CI/CD
- Security testing
- Performance testing

---

# 40. Final Summary

API Testing with Postman is one of the most important skills for:

- QA Engineers
- Automation Testers
- Backend Developers
- DevOps Engineers

Master these topics:

- HTTP methods
- Status codes
- Authentication
- Collections
- Variables
- Scripts
- Automation
- Newman
- CI/CD

to become highly skilled in API Testing.

---

# Bonus Tips

## Tips for Beginners

- Practice daily
- Learn JSON deeply
- Understand APIs conceptually
- Create collections
- Automate simple tests first

---

# Cheat Sheet

## HTTP Methods

```text
GET    → Read
POST   → Create
PUT    → Update
PATCH  → Partial Update
DELETE → Delete
```

---

## Common Status Codes

```text
200 OK
201 Created
400 Bad Request
401 Unauthorized
404 Not Found
500 Server Error
```

---

# Practice APIs

## JSONPlaceholder

https://jsonplaceholder.typicode.com

## ReqRes

https://reqres.in

## DummyJSON

https://dummyjson.com

---

# Useful Resources

## Postman Documentation

https://learning.postman.com

## Newman Documentation

https://github.com/postmanlabs/newman

## REST API Tutorial

https://restfulapi.net

---
````
