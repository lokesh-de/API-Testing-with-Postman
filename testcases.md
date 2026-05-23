# Postman Test Cases Using JavaScript

---

# 1. Basic Status Code Validation

## GET Request

```javascript
pm.test("GET Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

---

## POST Request

```javascript
pm.test("POST Status code is 201", function () {
    pm.response.to.have.status(201);
});
```

---

## PUT Request

```javascript
pm.test("PUT Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

---

## PATCH Request

```javascript
pm.test("PATCH Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

---

## DELETE Request

```javascript
pm.test("DELETE Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

---

# 2. Validate Response Time

```javascript
pm.test("Response time is less than 500ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});
```

---

# 3. Validate Response Body is Not Empty

```javascript
pm.test("Response body is not empty", function () {
    pm.expect(pm.response.text()).not.empty;
});
```

---

# 4. Validate JSON Response

```javascript
pm.test("Response is JSON", function () {
    pm.response.to.be.json;
});
```

---

# 5. Validate Specific Field Value

```javascript
pm.test("Validate username", function () {

    let jsonData = pm.response.json();

    pm.expect(jsonData.username).to.eql("john");
});
```

---

# 6. Validate Field Exists

```javascript
pm.test("Validate email field exists", function () {

    let jsonData = pm.response.json();

    pm.expect(jsonData).to.have.property("email");
});
```

---

# 7. Validate Header

```javascript
pm.test("Content-Type is application/json", function () {

    pm.expect(
        pm.response.headers.get("Content-Type")
    ).to.include("application/json");
});
```

---

# 8. Validate Array Length

```javascript
pm.test("Users array should not be empty", function () {

    let jsonData = pm.response.json();

    pm.expect(jsonData.length).to.be.above(0);
});
```

---

# 9. Validate Multiple Responses Using forEach()

## Example Response

```json
[
  {
    "id": 1,
    "name": "John"
  },
  {
    "id": 2,
    "name": "David"
  }
]
```

---

## Validate Every Object in Array

```javascript
pm.test("Validate all users", function () {

    let jsonData = pm.response.json();

    jsonData.forEach((user) => {

        pm.expect(user).to.have.property("id");

        pm.expect(user).to.have.property("name");

        pm.expect(user.id).to.not.be.null;

        pm.expect(user.name).to.not.be.empty;
    });

});
```

---

# 10. Validate Status Code and Response Together

```javascript
pm.test("Validate status and response", function () {

    pm.response.to.have.status(200);

    let jsonData = pm.response.json();

    pm.expect(jsonData.id).to.eql(1);

});
```

---

# 11. Validate Response Contains Text

```javascript
pm.test("Response contains success message", function () {

    pm.expect(pm.response.text()).to.include("success");

});
```

---

# 12. Validate Response Object Type

```javascript
pm.test("Response is an object", function () {

    let jsonData = pm.response.json();

    pm.expect(jsonData).to.be.an("object");

});
```

---

# 13. Validate Response Array Type

```javascript
pm.test("Response is an array", function () {

    let jsonData = pm.response.json();

    pm.expect(jsonData).to.be.an("array");

});
```

---

# 14. Validate Nested JSON Response

## Example JSON

```json
{
  "user": {
    "name": "John",
    "email": "john@test.com"
  }
}
```

---

## Validation

```javascript
pm.test("Validate nested JSON", function () {

    let jsonData = pm.response.json();

    pm.expect(jsonData.user.name).to.eql("John");

    pm.expect(jsonData.user.email).to.include("@");

});
```

---

# 15. Validate Response Schema

```javascript
pm.test("Validate schema", function () {

    let schema = {
        "type": "object",
        "properties": {
            "id": { "type": "number" },
            "name": { "type": "string" },
            "email": { "type": "string" }
        },
        "required": ["id", "name", "email"]
    };

    pm.response.to.have.jsonSchema(schema);

});
```

---

# 16. Validate Dynamic Values

```javascript
pm.test("User ID should be greater than 0", function () {

    let jsonData = pm.response.json();

    pm.expect(jsonData.id).to.be.above(0);

});
```

---

# 17. Save Response Value into Variable

```javascript
let jsonData = pm.response.json();

pm.environment.set("userId", jsonData.id);
```

---

# 18. Get Variable Value

```javascript
let userId = pm.environment.get("userId");

console.log(userId);
```

---

# 19. Loop Through Array and Validate IDs

```javascript
pm.test("Validate all IDs", function () {

    let jsonData = pm.response.json();

    jsonData.forEach((item) => {

        pm.expect(item.id).to.be.a("number");

    });

});
```

---

# 20. Loop Through Array and Validate Emails

```javascript
pm.test("Validate all emails", function () {

    let jsonData = pm.response.json();

    jsonData.forEach((user) => {

        pm.expect(user.email).to.include("@");

    });

});
```

---

# 21. Validate Response Count

```javascript
pm.test("Validate total response count", function () {

    let jsonData = pm.response.json();

    pm.expect(jsonData.length).to.eql(10);

});
```

---

# 22. Validate Response Has Required Keys

```javascript
pm.test("Validate required keys", function () {

    let jsonData = pm.response.json();

    jsonData.forEach((item) => {

        pm.expect(item).to.have.all.keys(
            "id",
            "name",
            "email"
        );

    });

});
```

---

# 23. Validate Status Code Using OneOf

```javascript
pm.test("Status code is valid", function () {

    pm.expect(pm.response.code).to.be.oneOf([200, 201]);

});
```

---

# 24. Validate Error Response

```javascript
pm.test("Validate error message", function () {

    pm.response.to.have.status(400);

    let jsonData = pm.response.json();

    pm.expect(jsonData.message).to.eql("Invalid Request");

});
```

---

# 25. Commonly Used Postman Assertions

| Assertion | Purpose |
|-----------|---------|
| eql() | Exact match |
| include() | Contains value |
| above() | Greater than |
| below() | Less than |
| empty | Empty validation |
| property() | Check field exists |
| oneOf() | Match one value |

---

# Final Notes

Most Commonly Used in Real Projects:

- Status code validation
- Response body validation
- Schema validation
- Header validation
- Array validation
- forEach loop validations
- Token extraction
- Dynamic variables
- Response time validation

---
````
