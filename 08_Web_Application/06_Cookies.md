<br>

# Cookies
Cookies are **small pieces of data stored by a web browser on behalf of a website, typically used for session management, user preferences, and tracking**. To enhance security, cookies come with attributes that control their behavior and access.

## 1. Key Cookie Attributes

| Attribute | Purpose |
| --------- | ------- |
| HttpOnly | Prevents client-side JavaScript from accessing the cookie. |
| Secure | Ensures the cookie is sent only over HTTPS connections. |
| SameSite | Restricts cross-site requests, mitigating CSRF attacks. |
| Domain | Specifies the domain for which the cookie is valid. |
| Path | Limits the scope of the cookie to a specific URL path. |
| Expires / Max-Age | Defines the lifetime of the cookie before it expires. |  
<br>

## 2. HttpOnly Attribute
### a. What It Does
  - The HttpOnly attribute **makes a cookie inaccessible to JavaScript running in the browser**.
  - This **mitigates Cross-Site Scripting (XSS) attacks**, as malicious scripts cannot steal session cookies or sensitive data.

### b. Example
  - Setting an HttpOnly cookie in HTTP headers  

```
Set-Cookie: sessionId=abc123; HttpOnly
```  

  - JavaScript trying to access the cookie  

```
console.log(document.cookie); // HttpOnly cookies are not visible here.
``` 

### c. Use Case
  - Protecting session cookies or authentication tokens to prevent them from being accessed or stolen by malicious scripts.  
<br>

## 3. Secure Attribute

### a. What It Does
  - The Secure attribute **ensures that a cookie is sent only over HTTPS connections**, preventing exposure over unencrypted HTTP.

### b. Example
  - Setting a Secure cookie  

```
Set-Cookie: sessionId=abc123; Secure
```

### c. Use Case
  - Essential for cookies containing sensitive data, such as authentication tokens, in production environments.  
<br>

## 4. SameSite Attribute
### a. What It Does
  - Controls whether cookies are sent with cross-site requests.
  - Modes
    - Strict: Cookies are sent **only for requests originating from the same site**.
    - Lax: Cookies are sent for top-level navigation requests but not for other cross-site requests (e.g., iframes).
    - None: Cookies are sent for all requests but require the Secure attribute.

### b. Example
  - Setting a SameSite cookie  

```
Set-Cookie: sessionId=abc123; SameSite=Strict
```

### c. Use Case
  - **Mitigates Cross-Site Request Forgery (CSRF)** by preventing cookies from being sent with malicious cross-site requests.  
<br>

## 5. Domain and Path Attributes
### a. What They Do
  - Domain
    - Specifies which domain can access the cookie.
    - Example  

```
Set-Cookie: sessionId=abc123; Domain=example.com
```

The cookie is accessible to example.com and all its subdomains (e.g., sub.example.com).

  - Path
    - Restricts cookie access to specific URL paths.
    - Example  

```
Set-Cookie: sessionId=abc123; Path=/admin
```

The cookie is accessible only for URLs under /admin.

### b. Use Case
  - Limit the scope of cookies to relevant parts of the site to reduce exposure.  
<br>

## 6. Expires and Max-Age Attributes

### a. What They Do
  - Expires
    - Specifies an expiration date and time.
    - Example  

```
Set-Cookie: sessionId=abc123; Expires=Fri, 31 Dec 2024 23:59:59 GMT
```

  - Max-Age
    - Specifies the number of seconds until the cookie expires.
    - Example  

```
Set-Cookie: sessionId=abc123; Max-Age=3600
```

The cookie will expire in 1 hour.

### b. Use Case
  - Control the duration for which cookies remain valid, such as session cookies expiring when the browser closes.  
<br>

## 7. Combining Attributes for Security
A robust cookie configuration includes multiple attributes to enhance security.  

```
Set-Cookie: sessionId=abc123; HttpOnly; Secure; SameSite=Strict; Path=/; Max-Age=3600
```  
<br>

## 8. Common Security Threats and Mitigations

| Threat | Description | Mitigation |
| ------ | ----------- | ---------- |
| XSS (Cross-Site Scripting) | Malicious scripts stealing cookies. | Use HttpOnly to protect sensitive cookies. |
| CSRF (Cross-Site Request Forgery) | Attacker forces the browser to send authenticated requests to another site. | Use SameSite=Strict or Lax. |
| Session | Hijacking | Intercepting cookies over unencrypted HTTP connections.	| Use Secure to send cookies only over HTTPS. |  
<br>

## 9. Practical Examples
### a. Setting Cookies in HTTP Headers
  - Response from Server  

```
Set-Cookie: userId=12345; HttpOnly; Secure; SameSite=Lax; Max-Age=3600
```

### b. Setting Cookies in JavaScript
  - Note: HttpOnly cookies cannot be set via JavaScript, but others can.  

```
document.cookie = "theme=dark; Max-Age=3600; Secure; SameSite=Lax";
```  
<br>

## 10. Best Practices
1. Always Use **HttpOnly** for Sensitive Cookies
  - Prevents exposure to JavaScript, reducing XSS risks.
2. Enforce **Secure** Attribute
  - Ensure cookies are sent only over encrypted HTTPS connections.
3. Adopt **SameSite=Strict** Where Possible
  - Prevents cookies from being sent with cross-site requests, mitigating CSRF risks.
4. Regularly **Audit** Cookie Configurations
  - Ensure attributes align with the security needs of the application.  
<br>

## 11. Summary

| Attribute | Purpose | Example |
| --------- | ------- | ------- |
| HttpOnly | Prevents access via JavaScript. | Set-Cookie: sessionId=abc123; HttpOnly |
| Secure | Sends cookies only over HTTPS. | Set-Cookie: sessionId=abc123; Secure |
| SameSite | Restricts cross-site requests. | Set-Cookie: sessionId=abc123; SameSite=Lax |
| Domain | Defines cookie domain scope. | Set-Cookie: sessionId=abc123; Domain=example.com |
| Path | Limits cookies to specific paths. | Set-Cookie: sessionId=abc123; Path=/admin |

Proper cookie configuration is essential for securing web applications against common threats like XSS and CSRF. **By leveraging attributes like HttpOnly, Secure, and SameSite, developers can significantly enhance the security of their applications while maintaining functionality**.  
<br>