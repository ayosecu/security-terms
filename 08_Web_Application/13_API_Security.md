<br>

# API (Application Programming Interfaces) Security
APIs (Application Programming Interfaces) **allow communication between clients (like web or mobile applications) and servers**. While APIs streamline data exchange and functionality, they can expose vulnerabilities if not properly secured. Understanding what information APIs return and what can be sent is critical for ensuring their security.

## 1. Key Areas to Consider for API Security

### a. Information Returned by APIs
#### APIs may unintentionally expose sensitive information to users or attackers.
#### Common Risks:
  1. **Excessive Data Exposure**
    - Returning more data than needed, such as user details, internal IDs, or debug information.  
    - Example  

```
{
  "username": "johndoe",
  "password": "plaintext",
  "session_token": "abc123",
  "debug_info": "stack_trace_here"
}
```

  2. **Error Messages**  
    - Detailed error messages can leak information about the backend, such as database names, server configurations, or stack traces.  
    - Example of a bad error message  

```
{
  "error": "SQL Error: SELECT * FROM users WHERE id=1"
}
```

  3. **Information Disclosure in Responses**  
    - APIs may expose fields like internal server IPs, timestamps, or PII (personally identifiable information).  
    - Example  

```
{
  "user": {
    "id": 123,
    "email": "john@example.com",
    "internal_ip": "192.168.1.10"
  }
}
```

### b. What Can Be Sent to APIs
#### APIs may accept user input as parameters, which can be exploited if not validated.
#### Common Risks
  1. **Injection Attacks**  
    - Input like SQL queries, NoSQL commands, or scripts can compromise the database or application.  
    - Example  

```
GET /api/user?id=1;DROP TABLE users;
```

  2. **Unvalidated Input**  
    - Accepting any input without validation allows malicious payloads.  
    - Example  

```
{
  "username": "<script>alert('XSS')</script>"
}
```

  3. **Excessive Input**  
    - Large inputs (like oversized payloads) **can cause Denial of Service (DoS)**.  
    - Example  
      - Uploading a massive JSON payload to crash the server.  
  4. **Insecure Authentication**  
    - Sending invalid or missing credentials may allow unauthorized access.  
    - Example  

```
POST /api/login
{"username": "admin", "password": "wrongpass"}
```

  5. **Improper Access Control**
    - APIs may expose endpoints that allow users to access or modify data they shouldn’t.
    - If not validated, a regular user might delete another user’s account.  
    - Example  

```
DELETE /api/user/123
```


## 2. API Security Best Practices

### a. Validate and Sanitize Inputs
  - Ensure all incoming parameters are properly validated.
  - Reject dangerous inputs that could cause SQL Injection, XSS, or command injection.

### b. Control API Responses
1. Minimize Data Exposure
  - Return only what is necessary.
  - Example of better practice  

```
{
  "user": {
    "username": "johndoe"
  }
}
```

2. Standardize Error Messages
  - Avoid leaking implementation details.
  - Use generic error responses like  

```
{
  "error": "Invalid request."
}
```

### c. Implement Strong Authentication
- Use secure authentication methods such as:
  - OAuth 2.0 for token-based authentication.
  - API keys or JSON Web Tokens (JWTs).
- Example (Bearer Token)  

```
Authorization: Bearer <your_token_here>
```

### d. Enforce Rate Limiting
- Prevent abuse with **rate limiting** (e.g., 100 requests per minute per user).
- Example response when exceeding limits  

```
HTTP/1.1 429 Too Many Requests
```

### e. Use Proper Access Control
- Implement **Role-Based Access Control (RBAC) or Attribute-Based Access Control (ABAC)**.
- Restrict what users can access based on their roles or permissions.

### f. Monitor and Log API Activity
- Track API usage to detect anomalies (e.g., unusual access patterns).
- Log errors and failed authentication attempts.

### g. Secure Data Transmission
- Always **use HTTPS** to encrypt API communication and protect data in transit.

### h. Version Your APIs
- Use API versioning (e.g., /v1/users) to prevent breaking changes when updates occur.


## 3. Tools to Test and Secure APIs
1. **Burp Suite**
  - Intercepts and tests API requests for vulnerabilities like SQLi or XSS.
2. **Postman**
  - Used for testing and debugging API endpoints.
3. **OWASP ZAP**
  - Automated vulnerability scanning for APIs.
4. **Insomnia**
  - Lightweight tool for API testing.
5. **Tools for Rate Limiting**
  - Libraries like Express Rate Limit in Node.js or NGINX throttling.


## 4. Example of a Secure API Request and Response

### Request  

```
POST /api/login HTTP/1.1
Host: example.com
Content-Type: application/json
Authorization: Bearer <token>

{
  "username": "john_doe",
  "password": "securepassword123"
}
```

### Response  

```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "message": "Login successful",
  "user": {
    "id": 123,
    "username": "john_doe"
  }
}
```


## 5. Summary

| Aspect | Details |
| ------ | ------- |
| Returned Information | Avoid excessive data exposure, detailed error messages, or sensitive fields. |
| What Can Be Sent | Validate input to prevent SQLi, XSS, and command injections. |
| Authentication | Use OAuth2, JWT, or API keys for secure access. |
| Best Practices | Input validation, rate limiting, HTTPS, access controls, and logging. |
| Common Tools | Burp Suite, Postman, OWASP ZAP, Insomnia. |

APIs are critical components of modern web applications but **can expose sensitive data and become attack vectors if not secured**. **Developers must carefully control what APIs return and validate what is sent to prevent common vulnerabilities like data exposure, injection attacks, and unauthorized access**. Following API security best practices ensures robust protection and reliability.  
<br>