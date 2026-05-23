# Advanced Postman Concepts

---

# 1. Postman Monitor Setup

## What is a Monitor?

A Monitor in Postman is used to run API collections automatically at scheduled intervals.

It helps check:

- API uptime
- API health
- Response failures
- Performance issues

---

## Advantages of Monitors

- Automated API health checks
- Detect failures quickly
- Continuous monitoring
- Email notifications
- Useful in production systems

---

## Steps to Create a Monitor

### Step 1: Open Collection

Select the collection you want to monitor.

---

### Step 2: Click on Collection Options

Click the `...` (three dots) beside the collection name.

---

### Step 3: Select Monitor Collection

Click:

```text
Monitor Collection
```

---

### Step 4: Configure Monitor

Provide:

- Monitor Name
- Environment
- Region
- Frequency

Example:

```text
Run every 5 minutes
Run every 1 hour
Run daily
```

---

### Step 5: Save Monitor

Click:

```text
Create Monitor
```

---

## Monitor Execution Flow

```text
Monitor Trigger
      ↓
Collection Executes
      ↓
Requests Sent
      ↓
Tests Validated
      ↓
Reports Generated
```

---

## Example Monitor Use Cases

- Login API health check
- Payment API monitoring
- Authentication service uptime
- Production API validation

---

# 2. Dry Run Concept in Postman

## What is a Dry Run?

A Dry Run means executing requests or collections for validation purposes without affecting actual production data.

Used for:

- Validation testing
- Debugging
- Safe execution
- Pre-check verification

---

## Purpose of Dry Run

- Verify request flow
- Validate test scripts
- Check variable values
- Ensure APIs work correctly

---

## Real-Time Example

Before executing APIs in Production:

```text
DEV → QA → UAT → DRY RUN → PROD
```

Dry run helps avoid production failures.

---

## Dry Run in Collection Runner

You can perform dry runs by:

- Using test environments
- Using mock servers
- Using dummy test data
- Running APIs in staging environment

---

## Example Dry Run Scenario

### Login API

```http
POST /login
```

### Dry Run Goal

- Check token generation
- Validate response structure
- Ensure authentication works

without impacting real users.

---

# 3. Forking Collections in Postman

## What is Forking?

Forking means creating your own copy of an existing Postman collection.

Similar to GitHub fork concept.

---

## Why Fork Collections?

- Team collaboration
- Independent testing
- Experiment safely
- Modify APIs without affecting original collection

---

## Advantages of Forking

- Safe editing
- Parallel development
- Better collaboration
- Version control support

---

# Steps to Fork a Collection

## Step 1: Open Collection

Select the collection.

---

## Step 2: Click Three Dots

```text
...
```

---

## Step 3: Click Fork Collection

Select:

```text
Fork Collection
```

---

## Step 4: Enter Fork Name

Example:

```text
User API Testing - My Copy
```

---

## Step 5: Select Workspace

Choose your workspace.

---

## Step 6: Create Fork

Click:

```text
Fork Collection
```

---

# Fork vs Export

| Fork | Export |
|------|--------|
| Creates editable copy in Postman | Downloads JSON file |
| Supports sync | Static file |
| Collaboration friendly | Manual sharing |
| Live updates possible | No updates |

---

# Forking Use Cases

## Team Collaboration

Developer creates collection → QA forks collection → QA adds tests

---

## Safe Experimentation

Original collection remains unchanged while testing new scripts.

---

# Pull Changes in Forked Collections

If original collection updates:

```text
Pull Changes
```

helps sync latest updates into your fork.

---

# Merge Changes

If you modify your fork:

```text
Create Pull Request
```

can be used to merge updates.

---

# 4. Mock Servers in Postman

## What is a Mock Server?

Mock Server simulates API responses without backend implementation.

---

## Advantages

- Frontend testing before backend ready
- Faster development
- Independent testing

---

# Steps to Create Mock Server

1. Create Collection
2. Add Example Responses
3. Click Mock Collection
4. Generate Mock URL

---

## Example Mock URL

```text
https://mock.postman-api.com/users
```

---

# 5. Workspace Concept

## What is a Workspace?

Workspace is a shared area where teams collaborate.

---

## Types of Workspaces

| Type | Purpose |
|------|---------|
| Personal | Individual work |
| Team | Team collaboration |
| Public | Public sharing |
| Partner | External collaboration |

---

# 6. Environment Setup

## What is an Environment?

Environment stores reusable variables.

---

## Example Variables

```text
base_url
token
user_id
```

---

## Example Usage

```text
{{base_url}}/users
```

---

# 7. Global Variables

Global variables are accessible across all collections.

---

## Set Global Variable

```javascript
pm.globals.set("token", "abc123");
```

---

## Get Global Variable

```javascript
pm.globals.get("token");
```

---

# 8. Collection Variables

Used only inside specific collections.

---

## Set Collection Variable

```javascript
pm.collectionVariables.set("userId", 101);
```

---

# 9. Local Variables

Temporary variables used during request execution.

---

## Example

```javascript
pm.variables.set("tempId", 500);
```

---

# 10. Pre-request Script Concept

## What is Pre-request Script?

Runs before request execution.

Used for:

- Generate tokens
- Set variables
- Create timestamps
- Encrypt data

---

## Example

```javascript
console.log("Request Started");
```

---

# 11. Test Script Concept

## What is Test Script?

Runs after API response.

Used for:

- Validate status codes
- Validate response body
- Store dynamic values

---

## Example

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

---

# 12. Collection Runner Concept

## What is Collection Runner?

Executes multiple requests automatically.

---

## Benefits

- Automation
- Regression testing
- Data-driven testing
- Batch execution

---

# 13. API Chaining Concept

## What is API Chaining?

Using response data from one API into another API.

---

## Example Flow

```text
Login API
    ↓
Get Token
    ↓
Use Token in User API
```

---

## Example Script

```javascript
let jsonData = pm.response.json();

pm.environment.set("token", jsonData.token);
```

---

# 14. Newman CLI Concept

## What is Newman?

Command-line runner for Postman collections.

---

## Install

```bash
npm install -g newman
```

---

## Run Collection

```bash
newman run collection.json
```

---

# 15. Real-Time Project Workflow

```text
Requirement Analysis
        ↓
API Development
        ↓
Postman Collection Creation
        ↓
Environment Setup
        ↓
Test Script Writing
        ↓
Collection Runner Execution
        ↓
Dry Run Validation
        ↓
Monitor Setup
        ↓
CI/CD Integration
        ↓
Production Deployment
```

---

# Final Notes

Important Advanced Concepts in Real Projects:

- Monitor Setup
- Dry Run Testing
- Forking Collections
- Mock Servers
- Environment Variables
- Collection Runner
- API Chaining
- Newman CLI
- CI/CD Integration

These concepts are commonly asked in interviews and used in real-time API automation projects.

---
````
