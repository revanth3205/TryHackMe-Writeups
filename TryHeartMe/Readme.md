# TryHeartMe — JWT Privilege Escalation

> TryHackMe — Love at First Breach 2026

## Overview

**TryHeartMe** is a web exploitation challenge involving a fictional Valentine’s gift shop. The application uses **JSON Web Tokens (JWTs)** for authentication and authorization.

The challenge demonstrates how an improperly protected JWT signing secret can allow an authenticated user to modify their token and escalate privileges from `user` to `admin`.

---

## Objective

Access the hidden **ValenFlag** item in the shop and retrieve the flag by exploiting the JWT-based authentication mechanism.

---

## Reconnaissance

After accessing the web application on the target machine, I navigated to the Valentine’s gift shop running on the web service.

The application allows users to create an account and browse products.

After registering and logging in, I inspected the available products and noticed that the application references the user's role:

```text
role:user
```

This suggested that the application may use the user's role for authorization.

---

## JWT Cookie Analysis

I inspected the website's cookies using the browser's developer tools.

A cookie containing a **JWT (JSON Web Token)** was present.

A JWT normally consists of three parts:

```text
HEADER.PAYLOAD.SIGNATURE
```

The payload contained claims similar to:

```json
{
  "email": "you@gmail.com",
  "role": "user",
  "credits": 0,
  "iat": 1786959649,
  "theme": "valentine"
}
```

The interesting claim was:

```json
"role": "user"
```

Since the application appeared to rely on this value for authorization, I investigated whether the JWT could be modified.

---

## JWT Tampering

I decoded the JWT and modified the role claim from:

```json
"role": "user"
```

to:

```json
"role": "admin"
```

The modified payload became:

```json
{
  "email": "you@gmail.com",
  "role": "admin",
  "credits": 0,
  "iat": 1786959649,
  "theme": "valentine"
}
```

The challenge uses **HS256** for JWT signing and the signing secret was:

```text
secret
```

The modified payload was then re-signed to generate a new valid JWT.

---

## Replacing the Session Cookie

I copied the newly generated JWT and replaced the original JWT value in the browser's cookie/session storage.

After refreshing the website, the application accepted the modified token and treated my account as an administrator.

This resulted in successful **privilege escalation from `user` to `admin`**.

---

## Accessing the Hidden Item

After gaining administrator privileges, I navigated to the **Admin** section of the website.

From there:

1. Opened the **ValenFlag** item.
2. Selected **Buy**.
3. The hidden flag was revealed.

---

## Flag

```text
THM{v4l3nt1n3_jwt_c00k13_t4mp3r_4dm1n_sh0p}
```

---

## Vulnerability

The primary vulnerability was **JWT privilege escalation through token tampering**.

The application trusted authorization information contained in the JWT while using a weak/exposed signing secret. Because the secret was known, an attacker could:

1. Obtain a legitimate JWT.
2. Decode its payload.
3. Change the `role` claim.
4. Re-sign the modified payload.
5. Replace the original session token.
6. Gain administrator privileges.

### Impact

An attacker able to obtain the signing secret could potentially modify authentication or authorization claims and gain unauthorized access to privileged functionality.

---

## Key Takeaways

* Never use weak JWT signing secrets such as `secret`.
* JWT claims such as `role` should not be blindly trusted.
* JWT signatures must always be properly validated.
* Sensitive authorization decisions should have appropriate server-side controls.
* Exposing or leaking JWT signing secrets can lead to privilege escalation and account compromise.

---

## Tools Used

* Browser Developer Tools
* JWT.io
* CyberChef
* TryHackMe

---

## Conclusion

The TryHeartMe challenge demonstrates a practical JWT security issue where a weak signing secret allows an authenticated user to tamper with their authorization claims.

By changing the JWT role from `user` to `admin`, generating a valid signed token, and replacing the session cookie, administrative functionality became accessible and the hidden **ValenFlag** could be purchased.

**Flag:** `THM{v4l3nt1n3_jwt_c00k13_t4mp3r_4dm1n_sh0p}`
