# 🐍 Operation Slither — TryHackMe Walkthrough

> **Room:** Operation Slither
> **Platform:** TryHackMe
> **Category:** OSINT / Social Media Investigation / Digital Footprinting
> **Difficulty:** Easy
> **Skills:** Google Dorking, OSINT, Base64 Decoding, Social Media Analysis, Git History Analysis

---

## 📌 Overview

**Operation Slither** is an OSINT-focused TryHackMe room that simulates an investigation into a group of operators communicating across different online platforms.

The challenge requires following digital traces from one operator to another, identifying their associated accounts, and recovering information hidden within public posts, comments, and GitHub commit history.

The investigation mainly involves:

* 🔎 Google Dorking
* 🌐 Username enumeration
* 📱 Social media OSINT
* 🔐 Base64 decoding
* 🎵 Cross-platform account correlation
* 🐙 GitHub repository investigation
* 🗂️ Recovering deleted files from Git history

---

# 🎯 Objectives

During the investigation, we need to:

1. Identify the platform used by the first operator.
2. Recover the first flag.
3. Identify the second operator.
4. Investigate their other social media presence.
5. Recover the second flag.
6. Identify the third operator.
7. Discover their other platform.
8. Investigate their GitHub repository and commit history.
9. Recover the final flag.

---

# 🕵️ Task 1 — The Leader

The investigation begins with the username:

```text
v3n0mbyt3_
```

The first step is to search for this username across the internet.

### 🔎 Google Dorking

A simple search can help identify accounts associated with the username.

Example:

```text
"v3n0mbyt3_"
```

The search results reveal that the operator is also using **Threads**.

### Question

> Aside from Twitter/X, what other platform is used by `v3n0mbyt3_`?

### Answer

```text
threads
```

---

## 🔐 Finding the First Flag

After locating the Threads account, inspect the posts and replies.

A suspicious Base64-encoded string can be found in the replies.

Base64 can be decoded using a terminal:

```bash
echo "BASE64_STRING" | base64 -d
```

Or with Python:

```python
import base64

encoded = "BASE64_STRING"
print(base64.b64decode(encoded).decode())
```

The decoded value reveals the first flag.

### 🚩 Flag 1

```text
THM{sl1th3ry_tw33tz_4nd_l34ky_r3pl13s!}
```

---

# 🕵️ Task 2 — The Sidekick

The first operator's conversations provide another username:

```text
_myst1cv1x3n_
```

This appears to be another operator involved in the operation.

### Question

> What is the username of the second operator talking to `v3n0mbyt3_` from the previous platform?

### Answer

```text
_myst1cv1x3n_
```

---

## 🔎 Searching for the Second Operator

Use the username as another OSINT pivot.

Example search:

```text
"_myst1cv1x3n_"
```

Multiple accounts may appear across different platforms.

After correlating the available profiles, the **Instagram** account becomes particularly interesting.

Inspect the posts and associated content.

One of the posts contains a **SoundCloud link**, which provides another lead.

---

## 🧩 Prototype 2

Continue examining the Instagram posts.

A post titled:

```text
Prototype 2
```

contains another Base64-encoded value.

Decode it using:

```bash
echo "BASE64_STRING" | base64 -d
```

The decoded output contains the second flag.

### 🚩 Flag 2

```text
THM{s0cm1nt_00ps3c_f1ng3r_m1scl1ck}
```

---

# 🕵️ Task 3 — The Last Operator

The SoundCloud account provides another pivot point.

Inspect the account's followers and look for suspicious or relevant usernames.

One username stands out:

```text
sh4d0wF4NG
```

### Question

> What is the handle of the third operator?

### Answer

```text
sh4d0wF4NG
```

---

## 🐙 Finding the Third Operator

Search for the username:

```text
"sh4d0wF4NG"
```

The investigation leads to a **GitHub** account.

### Question

> What other platform does the third operator use?

### Answer

```text
github
```

---

# 🔍 GitHub Investigation

Once the GitHub account is identified, inspect the available repositories.

Rather than only looking at the current files, investigate the repository's **commit history**.

This is important because information removed from a repository may still exist in previous commits.

### What to investigate

Look for:

* Deleted files
* Previous versions of files
* Suspicious commit messages
* Credentials
* Password-related information
* Configuration files
* Historical changes

---

## 🗑️ Recovering Deleted Files

One of the commits contains files that were later deleted.

The deleted file contains a value associated with:

```text
shadow-password
```

The value appears to be a hash.

However, the objective here is to investigate the historical repository state and identify the information exposed by the deleted file.

The recovered information leads to the final flag.

### 🚩 Flag 3

```text
THM{sh4rp_f4ngz_l34k3d_bl00dy_pw}
```

---

# 🏁 Final Answers

| Task   | Question                            | Answer                                    |
| ------ | ----------------------------------- | ----------------------------------------- |
| Task 1 | Other platform used by `v3n0mbyt3_` | `threads`                                 |
| Task 1 | Flag                                | `THM{sl1th3ry_tw33tz_4nd_l34ky_r3pl13s!}` |
| Task 2 | Second operator                     | `_myst1cv1x3n_`                           |
| Task 2 | Flag                                | `THM{s0cm1nt_00ps3c_f1ng3r_m1scl1ck}`     |
| Task 3 | Third operator                      | `sh4d0wF4NG`                              |
| Task 3 | Other platform                      | `github`                                  |
| Task 3 | Flag                                | `THM{sh4rp_f4ngz_l34k3d_bl00dy_pw}`       |

---

# 🧠 Key Takeaways

This room demonstrates how seemingly insignificant pieces of public information can be connected to build a larger picture.

### 1. Username reuse is valuable

People often reuse the same username across multiple platforms.

A single username can therefore become an effective starting point for OSINT investigations.

### 2. Follow the breadcrumbs

The investigation follows a chain:

```text
Operator 1
    ↓
Threads
    ↓
Operator 2
    ↓
Instagram
    ↓
SoundCloud
    ↓
Operator 3
    ↓
GitHub
    ↓
Git commit history
```

Each platform provides the next clue.

### 3. Deleted does not always mean gone

Git repositories preserve historical versions of files.

A developer may delete sensitive information from the current version, while the information remains accessible through previous commits.

### 4. Base64 is encoding, not encryption

The room uses Base64 to hide some of the flags.

Base64 can easily be decoded with tools such as:

```bash
base64 -d
```

or Python's:

```python
base64.b64decode()
```

### 5. Cross-platform OSINT

The most important skill demonstrated by this room is **correlation**.

A username found on one platform can become the pivot for finding another account, which can reveal another operator and eventually lead to the final evidence.

---

# 🛠️ Tools Used

* Google / Search Engine Dorking
* Base64 Decoder
* Python
* Threads
* Instagram
* SoundCloud
* GitHub
* Git commit history

---

# 📚 Skills Practiced

```text
OSINT
├── Username Enumeration
├── Google Dorking
├── Social Media Investigation
├── Account Correlation
├── Base64 Decoding
└── Digital Footprinting

Git Investigation
├── Repository Analysis
├── Commit History
├── Deleted File Recovery
└── Sensitive Data Discovery
```

---

# ⚠️ Disclaimer

This walkthrough is intended for **educational and authorized cybersecurity training purposes only**.

The techniques demonstrated should only be used against systems, accounts, repositories, and information that you are authorized to investigate.

---

## 🏆 Flags Collected

```text
THM{sl1th3ry_tw33tz_4nd_l34ky_r3pl13s!}

THM{s0cm1nt_00ps3c_f1ng3r_m1scl1ck}

THM{sh4rp_f4ngz_l34k3d_bl00dy_pw}
```

---

**Room:** Operation Slither
**Platform:** TryHackMe
**Focus:** OSINT • Social Engineering Awareness • Digital Footprinting • Git Investigation
