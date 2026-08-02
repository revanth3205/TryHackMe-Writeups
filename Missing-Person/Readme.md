# Missing Person - TryHackMe Write-up

![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green)
![Category](https://img.shields.io/badge/Category-OSINT-blue)
![Platform](https://img.shields.io/badge/Platform-TryHackMe-red)

## Room Information

| Item | Details |
|------|---------|
| Room | Missing Person |
| Category | Open Source Intelligence (OSINT) |
| Platform | TryHackMe |
| Difficulty | Easy |
| Status | ✅ Completed |

---

# Objective

Investigate the disappearance of a tourist using publicly available information (OSINT).

The challenge provides only:

- Two photographs
- A short description from a concerned friend

The objective is to identify the person's movements, reconstruct their timeline, and answer investigation-related questions using open-source intelligence techniques.

---

# Skills Practiced

- Reverse Image Search
- Image Analysis
- Metadata Extraction
- Timeline Reconstruction
- Google Dorking
- Social Media Investigation
- Geolocation
- Event Correlation
- Open Source Intelligence (OSINT)

---

# Tools Used

- Google Images
- Google Search
- Exif / Metadata Viewer
- EZGif Metadata Viewer
- Facebook
- Google Maps
- Gemini AI (for search refinement)

---

# Investigation Walkthrough

## Step 1 – Reverse Image Search

The second image appeared to contain a motorcycle racing circuit.

Performed a reverse image search using Google Images.

### Result

The location was identified as:

- Pertamina Mandalika International Street Circuit
- Indonesia

This established the first major clue regarding the person's location.

---

## Step 2 – Identify the Event

Since the image showed racing motorcycles, it was reasonable to investigate MotoGP events hosted at the circuit.

Searching for:

```

Mandalika MotoGP 2025

```

revealed the event dates.

### Findings

- MotoGP Mandalika
- 03–05 October 2025

This helped establish the approximate travel timeline.

---

## Step 3 – Restaurant Identification

The first photograph contained visible text on a table.

Observed text:

```

Cantina Mexicana

```

A search confirmed it was an actual restaurant.

This provided another confirmed location visited by the missing person.

---

## Step 4 – Metadata Analysis

The original image metadata was examined.

Tool used:

- EZGif Metadata Viewer

Important information recovered:

- Original Date/Time

This helped reconstruct the sequence of events.

---

## Step 5 – Analyzing the Final Message

The second stage of the challenge introduced the final message received from the missing person.

Important clues included:

- Attended a MotoGP after-party
- Met a local DJ
- Planned to visit a cave the following day

These clues guided the remainder of the investigation.

---

## Step 6 – Finding the After-Party Location

Several targeted Google searches were performed combining:

- MotoGP
- Mandalika
- After Party
- Local DJ

After refining search terms, the after-party venue was successfully identified.

---

## Step 7 – Identifying the DJ

Using information from the party venue and related social media posts, the local DJ was identified.

This narrowed the investigation considerably.

---

## Step 8 – Determining the Cave

Instead of assuming the nearest cave, multiple searches were verified using Google and Gemini AI.

After validation, the correct destination cave was identified.

This demonstrates an important OSINT principle:

> Never assume. Always verify.

---

## Step 9 – Social Media Investigation

The final task required locating the DJ's contact number.

Methodology:

- Search social media platforms
- Review public profiles
- Identify publicly shared contact information

The required information was successfully recovered through publicly available sources.

---

# Key OSINT Techniques Learned

- Reverse image searching can instantly reveal locations.
- Small visual clues often become major breakthroughs.
- Metadata can establish accurate timelines.
- Event schedules help correlate travel dates.
- Public social media profiles often contain valuable investigative information.
- Verification is more important than assumptions.

---

# Learning Outcome

This room demonstrates that successful OSINT investigations rely more on methodology than specialized tools.

By combining:

- Image analysis
- Metadata extraction
- Search engine techniques
- Event correlation
- Social media investigation

it is possible to reconstruct a person's activities using only publicly available information.

---

# Notes

This repository is intended for educational purposes only.

The write-up focuses on the investigative methodology rather than simply revealing answers, encouraging readers to understand the OSINT process.

---

## Author

**Revanth Kengana**

Cyber Security Student | Digital Forensics | Penetration Testing | OSINT Enthusiast

---
⭐ If you found this write-up useful, consider giving the repository a star.
