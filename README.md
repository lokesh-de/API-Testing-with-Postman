# API Testing with Postman

Complete beginner to advanced notes for API Testing using Postman.

This repository contains:

- API Testing basics
- HTTP methods
- Status codes
- Postman concepts
- JavaScript test cases
- Response validations
- Authentication
- Collection Runner
- Newman CLI
- Mock Servers
- Monitor Setup
- Forking Collections
- Dry Run concepts
- API Automation basics

---

# Topics Covered

## API Basics

- What is API?
- API Testing Introduction
- Advantages & Disadvantages
- REST API Basics
- SOAP vs REST
- GraphQL Basics

---

## HTTP Concepts

- HTTP Methods
- GET
- POST
- PUT
- PATCH
- DELETE
- Headers
- Query Parameters
- Path Parameters
- Status Codes

---

## Postman Basics

- Installing Postman
- Collections
- Environment Variables
- Global Variables
- Local Variables
- Collection Variables

---

## Authentication

- Basic Auth
- Bearer Token
- OAuth 2.0
- API Key

---

## JavaScript Test Cases

- Status code validation
- Response body validation
- Header validation
- JSON validation
- Array validation
- forEach loop validations
- Schema validation
- Response time validation

---

## Advanced Postman Concepts

- Collection Runner
- API Chaining
- Mock Servers
- Monitor Setup
- Dry Run Concept
- Forking Collections
- Newman CLI
- CI/CD Integration

---

# Project Structure

```text
postman-api-testing/
│
├── README.md
├── api-testing-with-postman.md
├── postman-testcases.md
├── advanced-postman-concepts.md
└── collections/
```

---

# Sample Postman Test Script

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

---

# Sample Array Validation

```javascript
pm.test("Validate all users", function () {

    let jsonData = pm.response.json();

    jsonData.forEach((user) => {

        pm.expect(user).to.have.property("id");

        pm.expect(user).to.have.property("name");

    });

});
```

---

# Tools Used

| Tool | Purpose |
|------|---------|
| Postman | API Testing |
| Newman | CLI Runner |
| VS Code | Notes & Development |
| JSONPlaceholder | Practice APIs |

---

# Practice APIs

## JSONPlaceholder

https://jsonplaceholder.typicode.com

## ReqRes

https://reqres.in

## DummyJSON

https://dummyjson.com

---

# Install Newman

```bash
npm install -g newman
```

---

# Run Collection using Newman

```bash
newman run collection.json
```

---

# Learning Roadmap

## Beginner

- Learn HTTP
- Learn JSON
- Learn Postman Basics

## Intermediate

- JavaScript Test Cases
- Variables
- Collection Runner
- API Chaining

## Advanced

- Newman
- CI/CD
- Security Testing
- Performance Testing
- Monitoring

---

# Best Practices

- Organize collections properly
- Use environment variables
- Write reusable test scripts
- Validate all responses
- Store tokens securely
- Automate repetitive tests

---

# Interview Topics

- Difference between PUT & PATCH
- Status Codes
- Authentication
- API Chaining
- Mock Servers
- Collection Runner
- Newman CLI
- Monitor Setup
- Forking Collections

---

# Useful Resources

## Postman Official

https://www.postman.com

## Postman Learning Center

https://learning.postman.com

## Newman GitHub

https://github.com/postmanlabs/newman

## REST API Tutorial

https://restfulapi.net

---

# Author

API Testing Notes created for learning and practice using Postman and JavaScript.

---

# License

Free to use for learning purposes.

---
````
