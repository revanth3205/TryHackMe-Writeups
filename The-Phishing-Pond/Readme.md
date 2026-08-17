# 🎣 TryHackMe: The Phishing Pond — Walkthrough

> **Room:** The Phishing Pond
> **Platform:** TryHackMe
> **Category:** Phishing / Social Engineering / Email Security
> **Difficulty:** Beginner
> **Status:** Completed ✅

## 📌 Introduction

Phishing remains one of the most common techniques used by attackers to steal credentials, financial information, and sensitive data.

**The Phishing Pond** is a TryHackMe room designed to build practical skills in identifying phishing emails. The challenge presents a series of realistic email scenarios and requires us to determine whether each message is **legitimate or malicious**.

The room focuses on recognizing common phishing indicators such as:

* Urgency and pressure tactics
* Executive impersonation
* Suspicious links
* Malicious attachments
* Macro-enabled documents
* Look-alike domains
* Credential harvesting
* Requests for financial information
* Fake password-reset pages
* Suspicious third-party websites

---

## 🎯 Objectives

The main objectives of this room are to:

1. Analyze suspicious emails.
2. Identify phishing indicators.
3. Distinguish legitimate emails from malicious ones.
4. Understand common social-engineering techniques.
5. Recognize credential-harvesting attempts.
6. Identify potentially malicious attachments and links.
7. Complete the email-classification challenge and obtain the flag.

---

# 🔎 Phishing Analysis

The room provides multiple email scenarios. Each email must be analyzed based on its sender, content, links, attachments, and requested actions.

A useful approach is to ask:

> **Who sent the email? What do they want me to do? Where does the link go? Is the request unusual or urgent?**

---

## 🧪 Level 1

### Verdict: 🚨 Phishing

**Reason:**

The email impersonates an executive and requests an urgent wire transfer.

This is a classic example of **Business Email Compromise (BEC)** or executive impersonation.

### Red Flags

* Executive impersonation
* Financial request
* Urgency
* Wire-transfer request

---

## 🧪 Level 2

### Verdict: ✅ Legitimate

This email does not exhibit the typical phishing indicators required to classify it as malicious.

When analyzing legitimate-looking messages, it is still important to verify the sender and ensure that links and requests match the expected context.

---

## 🧪 Level 3

### Verdict: ✅ Legitimate

The email was classified as legitimate.

No significant phishing indicators were identified that would justify marking the message as malicious.

---

## 🧪 Level 4

### Verdict: ✅ Legitimate

This email was also classified as legitimate.

The message did not contain the suspicious characteristics associated with the phishing examples in the room.

---

## 🧪 Level 5

### Verdict: 🚨 Phishing

**Reason:**

The email contains an attachment and asks the recipient to enable macros.

### Red Flags

* Unexpected attachment
* Macro-enabled document
* Request to enable macros

Malicious Office documents can abuse macros to execute attacker-controlled code after a victim enables them.

> **Security tip:** Never enable macros in an unexpected document simply because an email instructs you to do so.

---

## 🧪 Level 6

### Verdict: 🚨 Phishing

**Reason:**

The email contains a suspicious third-party survey link.

### Red Flags

* Unexpected survey
* External/third-party link
* Suspicious destination

Attackers frequently use surveys, competitions, and rewards as social-engineering lures.

---

## 🧪 Level 7

### Verdict: 🚨 Phishing

**Reason:**

The offer requests sensitive personal or banking information.

### Red Flags

* Request for sensitive information
* Financial information
* Suspicious offer

Legitimate organizations generally should not require users to submit sensitive banking information through an unsolicited promotional email.

---

## 🧪 Level 8

### Verdict: 🚨 Phishing

**Reason:**

The email redirects the recipient to a malicious password-reset page.

Password-reset lures are extremely common phishing techniques because users are accustomed to responding quickly to account-security notifications.

### Red Flags

* Password-reset theme
* Suspicious link
* Credential-harvesting potential
* Account-security urgency

---

## 🧪 Level 9

### Verdict: 🚨 Phishing

**Reason:**

The link uses a deceptive destination designed to resemble a payment portal.

### Red Flags

* Fake payment portal
* Deceptive URL
* Financial context
* Potential credential/payment theft

Always inspect the actual destination of a hyperlink rather than trusting the displayed text.

---

## 🧪 Level 10

### Verdict: 🚨 Phishing

**Reason:**

The email contains an attachment and asks the recipient to enable macros.

### Red Flags

* Suspicious attachment
* Macro execution
* Social-engineering instructions

This follows the same malicious-document technique seen earlier in the room.

---

# 📊 Final Classification

| Level | Classification | Primary Indicator                       |
| ----- | -------------- | --------------------------------------- |
| 1     | 🚨 Phishing    | Executive impersonation + wire transfer |
| 2     | ✅ Legitimate   | No significant phishing indicators      |
| 3     | ✅ Legitimate   | No significant phishing indicators      |
| 4     | ✅ Legitimate   | No significant phishing indicators      |
| 5     | 🚨 Phishing    | Attachment + macros                     |
| 6     | 🚨 Phishing    | Suspicious survey link                  |
| 7     | 🚨 Phishing    | Requests sensitive information          |
| 8     | 🚨 Phishing    | Fake password-reset page                |
| 9     | 🚨 Phishing    | Deceptive payment portal                |
| 10    | 🚨 Phishing    | Attachment + macros                     |

---

# 🚩 Common Phishing Indicators

The room demonstrates several indicators that can be used during real-world email analysis.

### 1. Urgency

Attackers often pressure victims to act immediately.

Examples:

```text
URGENT: Immediate action required
Your account will be suspended today
Final warning
```

### 2. Impersonation

An attacker may pretend to be:

* A manager
* CEO
* Bank
* IT administrator
* Delivery company
* Government organization

### 3. Suspicious Links

Always inspect the actual destination rather than trusting the visible text.

### 4. Malicious Attachments

Unexpected documents, especially those requesting macros or other active content, should be treated cautiously.

### 5. Credential Requests

Requests for passwords, banking information, OTPs, or other sensitive information are major warning signs.

### 6. Fake Account Notifications

Password resets, account suspension warnings, and security alerts are commonly used as phishing lures.

---

# 🛡️ How to Defend Against Phishing

A strong phishing-defense process should include:

* Verify the sender independently.
* Hover over links before opening them.
* Inspect suspicious domains carefully.
* Avoid unexpected attachments.
* Never enable macros in untrusted documents.
* Never provide passwords through unsolicited links.
* Verify financial requests through another communication channel.
* Report suspicious emails to the security team.
* Use MFA to reduce the impact of stolen credentials.
* Deploy email security and anti-phishing controls.

---

# 🧠 What I Learned

This room helped reinforce several practical cybersecurity concepts:

* Phishing detection
* Email analysis
* Social engineering
* Business Email Compromise
* Executive impersonation
* Malicious attachments
* Macro-based attacks
* Credential phishing
* URL analysis
* Financial fraud
* Security awareness

The biggest takeaway is that **phishing is primarily a social-engineering attack**. Technical indicators are important, but understanding the attacker's attempt to manipulate the victim is equally important.

---

# 🏆 Flag

After correctly classifying the emails, the room provides the final flag:

```text
THM{i_phish_you_not}
```

---

## 🎣 Conclusion

**The Phishing Pond** is a useful introductory room for developing the ability to identify malicious emails.

The challenge demonstrates that phishing messages don't always look obviously malicious. Attackers can use authority, urgency, curiosity, financial incentives, and account-security warnings to convince users to perform dangerous actions.

Learning to stop and verify before clicking is one of the most effective defenses against phishing.

> **Think before you click — catch the phish before the phish catches you.**

---

### 🏷️ Tags

`TryHackMe` `Phishing` `Cybersecurity` `Social Engineering` `Email Security` `OSINT` `Security Awareness` `Blue Team` `Incident Response` `Cybersecurity Fundamentals`
