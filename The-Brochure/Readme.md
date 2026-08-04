# The Brochure - TryHackMe Write-up

## Overview

**Room:** The Brochure
**Platform:** TryHackMe
**Category:** OSINT (Open Source Intelligence)

This room focuses on basic OSINT techniques by following publicly available information across social media platforms. The objective is to investigate a hotel brochure, identify hidden clues, and recover the final flag.

---

## Objective

A promotional brochure for **Byte Lotus Hotel** contains an image that may reveal more than intended. The task is to investigate the available information and uncover the hidden connection that leads to the flag.

---

## Tools Used

* ExifTool
* Web Browser
* Base64 Decoder

---

## Methodology

### 1. Metadata Analysis

The investigation began by examining the brochure image using **ExifTool** to check for embedded metadata such as GPS coordinates, device information, or author details.

**Result:** No useful metadata was present.

---

### 2. Visual Inspection

Since the metadata did not provide any leads, the image itself was inspected carefully.

During this process, two important clues were identified:

* An Instagram username
* A reference to **Vera**, who appeared to be associated with the hotel

---

### 3. Social Media Investigation

The Instagram account for **Byte Lotus Resort** was located.

Observations:

* The account contained only a few posts.
* It followed a single account named **Vera**.

This suggested that Vera was the next point of investigation.

---

### 4. Inspecting Vera's Profile

The Vera account contained three posts.

Each post included part of a **Base64-encoded string** within its caption.

The encoded text was split across all three posts.

---

### 5. Reconstructing the Encoded String

The three Base64 fragments were collected in the correct order and combined into a single string.

Example:

```text
VEhNe1YzckBzX2FDQzB1bnRfaDRzX2IzM25fZjB1bmQhfQ==
```

---

### 6. Decoding

After decoding the reconstructed Base64 string, the final flag was obtained.

**Flag**

```text
THM{V3r@s_aCC0unt_h4s_b33n_f0und!}
```

---

## Key Takeaways

* Always inspect both **metadata** and the **visual contents** of an image.
* Social media relationships (followers/following) can reveal valuable investigative leads.
* Read every available post or caption—important information may be distributed across multiple sources.
* Simple encoding methods like Base64 are commonly used to hide challenge flags.

---

## Skills Practiced

* OSINT Investigation
* Image Analysis
* Social Media Enumeration
* Information Correlation
* Base64 Decoding

---

## Status

✅ Room Completed
