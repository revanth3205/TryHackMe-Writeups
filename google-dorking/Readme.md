# 🔎 Google Dorking — TryHackMe Walkthrough

> A practical walkthrough of the **Google Dorking** room on TryHackMe, covering search-engine reconnaissance, web crawlers, `robots.txt`, sitemaps, and advanced search operators.

![TryHackMe](https://img.shields.io/badge/TryHackMe-Google%20Dorking-red?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-OSINT-blue?style=for-the-badge)
![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green?style=for-the-badge)

---

## 📌 Room Information

* **Platform:** TryHackMe
* **Room:** Google Dorking
* **Category:** OSINT / Reconnaissance
* **Focus:** Search Engine Reconnaissance
* **Room Link:** https://tryhackme.com/room/googledorking

---

## 🎯 Objectives

This room introduces the fundamentals of using search engines for reconnaissance.

The main concepts covered are:

* Web crawlers
* Search engine indexing
* `robots.txt`
* Sitemaps
* Google Dorking
* Search operators
* Discovering publicly exposed information

---

# 🧠 Task 2 — Let's Learn About Crawlers

### 1. What is a “Crawler” used to do?

**Answer:**

```text
Index
```

### Explanation

A crawler, also known as a **spider** or **bot**, automatically discovers web pages and resources.

The information discovered by crawlers is organized into an **index**, allowing search engines to retrieve relevant information quickly.

---

### 2. What technique do Search Engines use to retrieve information about websites?

**Answer:**

```text
Crawling
```

### Explanation

**Crawling** is the automated process of visiting websites, following links, and collecting information from web pages.

The collected information is then processed and stored in a search engine's index.

---

### 3. What type of content could be gathered from a website?

**Answer:**

```text
Keywords
```

### Explanation

Search engine crawlers can collect information such as:

* Page text
* Keywords
* Headings
* Metadata
* URLs
* Links
* Page structure

This information helps search engines understand and index web pages.

---

# 🤖 Task 4 — Beepboop: robots.txt

## 1. Where would `robots.txt` be located?

For:

```text
ablog.com
```

**Answer:**

```text
ablog.com/robots.txt
```

### Explanation

The `robots.txt` file is normally placed at the **root directory of a website**.

Example:

```text
https://example.com/robots.txt
```

It provides instructions to compliant web crawlers about which parts of a website they should or should not crawl.

> ⚠️ `robots.txt` should not be treated as a security mechanism. Anyone can access it, and malicious crawlers can ignore its rules.

---

## 2. Where would a sitemap normally be located?

**Answer:**

```text
/sitemap.xml
```

### Explanation

A sitemap is commonly available at:

```text
https://example.com/sitemap.xml
```

It can also be referenced from the website's `robots.txt` file.

---

## 3. How would we only allow Bingbot to index the website?

**Answer:**

```text
User-agent: Bingbot
```

Example:

```text
User-agent: Bingbot
Allow: /
```

### Explanation

The `User-agent` directive identifies which crawler the following rules apply to.

Here, the rules specifically target:

```text
Bingbot
```

---

## 4. How would we prevent a crawler from indexing `/dont-index-me/`?

**Answer:**

```text
Disallow: /dont-index-me/
```

Example:

```text
User-agent: *
Disallow: /dont-index-me/
```

### Explanation

This tells compliant crawlers not to crawl URLs under that directory.

However, `robots.txt` does **not** provide access control or prevent someone from manually accessing the directory.

---

## 5. What extension might a Unix/Linux configuration file have?

**Answer:**

```text
.conf
```

### Explanation

Unix/Linux systems commonly use `.conf` files for configuration.

Examples include:

```text
apache.conf
nginx.conf
service.conf
```

Sensitive configuration files should **never be publicly accessible**. Proper authentication, authorization, server configuration, and access controls should be used instead of relying on `robots.txt`.

---

# 🗺️ Task 5 — Sitemaps

## 1. What is the typical file structure of a sitemap?

**Answer:**

```text
XML
```

### Explanation

Sitemaps are commonly written using **XML**.

Example:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset>
    <url>
        <loc>https://example.com/</loc>
    </url>
</urlset>
```

---

## 2. What real-life example can a sitemap be compared to?

**Answer:**

```text
Map
```

### Explanation

A sitemap can be thought of as a **map of a website**.

It provides a structured list of URLs that helps search engines discover content.

---

## 3. What keyword describes the path taken for content on a website?

**Answer:**

```text
Route
```

### Explanation

A route represents the path used to access content on a website.

For example:

```text
https://example.com/blog/security
```

The route is:

```text
/blog/security
```

---

# 🔍 Task 6 — What is Google Dorking?

## What is Google Dorking?

**Google Dorking** is the use of advanced search-engine operators to find specific information or content on the web.

Security professionals can use it during reconnaissance to identify publicly exposed information.

Common operators include:

| Operator    | Purpose                                 |
| ----------- | --------------------------------------- |
| `site:`     | Search within a specific website/domain |
| `filetype:` | Search for specific file types          |
| `intitle:`  | Search for words in page titles         |
| `inurl:`    | Search for words in URLs                |
| `" "`       | Search for an exact phrase              |

---

## 1. Search BBC for information about flood defences

**Answer:**

```text
site:bbc.co.uk flood defences
```

A more precise version can use quotation marks:

```text
site:bbc.co.uk "flood defences"
```

### Explanation

The `site:` operator restricts results to a particular domain.

---

## 2. What operator is used to search by file type?

**Answer:**

```text
filetype:
```

Example:

```text
site:gov.uk filetype:pdf "flood defences"
```

This searches for PDF documents associated with the specified domain and search terms.

---

## 3. What operator can be used to look for login pages?

**Answer:**

```text
intitle:
```

Example:

```text
intitle:"login" site:example.com
```

### Explanation

The `intitle:` operator searches for specific terms appearing in the title of indexed web pages.

---

# 🛡️ Security Considerations

Google Dorking itself is not inherently malicious.

It can be used legitimately for:

* Security assessments
* OSINT investigations
* Attack-surface discovery
* Finding accidentally exposed documents
* Identifying information leaks
* Reconnaissance during penetration testing

However, searches should only be performed against systems and information that you are **authorized to assess**.

### Important Principle

> **Publicly accessible does not automatically mean authorized to exploit.**

Finding exposed information is one thing; accessing, downloading, modifying, or exploiting systems without permission is another.

---

# 🧰 Key Commands & Operators

```text
site:
filetype:
intitle:
inurl:
"exact phrase"
```

Example:

```text
site:example.com filetype:pdf
```

Example:

```text
site:example.com intitle:"login"
```

Example:

```text
site:example.com inurl:admin
```

---

# 📚 Key Takeaways

After completing this room, I learned:

* How search-engine crawlers discover websites
* How indexing works
* The purpose and limitations of `robots.txt`
* How websites use sitemaps
* How XML sitemaps are structured
* How Google search operators work
* How `site:` restricts searches to a domain
* How `filetype:` searches for specific file types
* How `intitle:` searches page titles
* How Google Dorking can support OSINT and reconnaissance

---

# 🚀 Practical Security Applications

Google Dorking can be useful during the reconnaissance phase of a security assessment.

A security professional might use search operators to identify:

```text
Public documents
↓
Exposed directories
↓
Old pages
↓
Forgotten subdomains
↓
Technology information
↓
Potentially exposed information
```

The goal is to understand the **public attack surface** and help organizations remove information that should not be exposed.

---

# 📝 Conclusion

The Google Dorking room provides a strong introduction to search-engine-based reconnaissance.

Understanding how crawlers, indexes, `robots.txt`, sitemaps, and advanced search operators work is useful for anyone entering **OSINT, penetration testing, vulnerability assessment, or web security**.

The biggest takeaway is that search engines can reveal a surprising amount of information about an organization's public-facing presence—making search-engine reconnaissance an important part of security assessments.

---

## 🔗 TryHackMe Room

https://tryhackme.com/room/googledorking

---

### 👨‍💻 Author

**Revanth Kengana**

Cybersecurity Student | Penetration Testing | Web Security | OSINT

```
#CyberSecurity #TryHackMe #OSINT #GoogleDorking
#Reconnaissance #WebSecurity #PenetrationTesting
```
