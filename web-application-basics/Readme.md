# Web Application Basics - TryHackMe Walkthrough

## Overview

This repository contains my walkthrough and notes for the **Web Application Basics** room on TryHackMe.

The room introduces the fundamental concepts of web applications, HTTP communication, URLs, request methods, response codes, HTTP headers, cookies, security headers, and practical API interactions. It serves as an excellent foundation before moving on to web application penetration testing and OWASP Top 10 vulnerabilities.

---

## Learning Objectives

After completing this room, I learned about:

- Web application architecture
- Client-server communication
- Web browsers and web servers
- Web Application Firewall (WAF)
- URL structure
- HTTP protocol
- HTTP request methods
- HTTP responses and status codes
- HTTP request and response headers
- Cookies and cookie security
- Common security headers
- Making GET, POST, and DELETE requests to APIs

---

## Topics Covered

### Web Application Overview

- Web Browser
- Web Server
- Web Application Firewall (WAF)
- Client-Server Architecture

---

### Uniform Resource Locator (URL)

Understanding the different parts of a URL:

- Protocol (HTTP/HTTPS)
- Domain Name
- Port
- Path
- Query String
- Fragment

Also covered:

- HTTPS
- Typosquatting
- URL Parameters

---

### HTTP Messages

Learned the structure of HTTP communication:

#### HTTP Request

- Request Line
- Headers
- Empty Line
- Body

#### HTTP Response

- Status Line
- Headers
- Empty Line
- Body

---

### HTTP Request Methods

Studied commonly used HTTP methods:

| Method | Purpose |
|---------|----------|
| GET | Retrieve data |
| POST | Submit data |
| PUT | Replace existing data |
| PATCH | Modify existing data |
| DELETE | Remove data |
| OPTIONS | Discover supported methods |
| HEAD | Retrieve headers only |

---

### HTTP Request Headers

Important headers learned:

- Host
- User-Agent
- Accept
- Authorization
- Content-Type
- Cookie

Common Content-Type:

```
application/x-www-form-urlencoded
```

---

### HTTP Response Status Codes

Learned the five categories of status codes:

| Code | Meaning |
|------|----------|
| 1xx | Informational |
| 2xx | Success |
| 3xx | Redirection |
| 4xx | Client Error |
| 5xx | Server Error |

Examples:

- 200 OK
- 301 Moved Permanently
- 403 Forbidden
- 404 Not Found
- 500 Internal Server Error

---

### HTTP Response Headers

Common response headers:

- Server
- Content-Type
- Content-Length
- Set-Cookie
- Cache-Control

---

### Cookie Security

Learned the importance of cookie flags:

- Secure
- HttpOnly
- SameSite

These flags help mitigate attacks such as:

- Session Hijacking
- Cross-Site Scripting (XSS)
- Cross-Site Request Forgery (CSRF)

---

### Security Headers

Security headers explored:

- Content-Security-Policy (CSP)
- Strict-Transport-Security (HSTS)
- X-Content-Type-Options
- X-Frame-Options
- Referrer-Policy

Important directives:

```
script-src
includeSubDomains
nosniff
```

---

## Practical Exercises

Performed several HTTP API requests:

### GET Request

Retrieved the user list.

**Flag**

```
THM{YOU_HAVE_JUST_FOUND_THE_USER_LIST}
```

---

### POST Request

Modified Bob's country from **UK** to **US**.

**Flag**

```
THM{YOU_HAVE_MODIFIED_THE_USER_DATA}
```

---

### DELETE Request

Deleted a user through the API.

**Flag**

```
THM{YOU_HAVE_JUST_DELETED_A_USER}
```

---

## Key Takeaways

- Learned how web applications communicate over HTTP.
- Understood the structure of URLs and HTTP messages.
- Practiced different HTTP request methods.
- Identified common HTTP status codes.
- Learned the role of cookies and secure cookie flags.
- Explored essential HTTP security headers.
- Gained hands-on experience interacting with APIs using GET, POST, and DELETE requests.

---

## Skills Gained

- Web Application Fundamentals
- HTTP Protocol
- REST APIs
- HTTP Methods
- HTTP Headers
- URL Analysis
- Cookie Security
- Security Headers
- Client-Server Architecture
- Basic Web Security Concepts

---

## Platform

- **Platform:** TryHackMe
- **Room:** Web Application Basics
- **Category:** Web Fundamentals

---

## Repository Purpose

This repository is part of my cybersecurity learning journey, where I document TryHackMe rooms, CTFs, and hands-on labs to strengthen my understanding of offensive and defensive security concepts.

---

**Author**

**Revanth Kengana**

Cyber Security Student | IIIT Kottayam

Learning • Practicing • Building • Sharing
