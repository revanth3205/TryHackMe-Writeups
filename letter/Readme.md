# 🕵️ Letter — TryHackMe OSINT Walkthrough

> **Room:** Letter
> **Platform:** TryHackMe
> **Category:** OSINT
> **Difficulty:** Easy/Medium
> **Focus:** Open-Source Intelligence, Historical Research, Image Analysis, Postal Barcode Decoding

---

## 📌 Overview

**Letter** is an OSINT-focused TryHackMe room that combines image analysis, historical newspaper research, French archives, and logical clue correlation.

The investigation begins with an old envelope containing a **French postal barcode**. After decoding the barcode, the investigation moves toward a historical newspaper clipping and a handwritten note. These clues eventually lead to a **maritime disaster in Brittany in 1925**, where the objective is to identify the youngest member of the crew.

This room demonstrates how seemingly unrelated pieces of information can be connected to identify a specific person using publicly available sources.

---

## 🎯 Objectives

The main objectives of this room were to:

* Decode a French postal barcode.
* Identify the location associated with the barcode.
* Analyze a historical newspaper clipping.
* Determine the approximate date of the newspaper.
* Research the historical event mentioned in the documents.
* Locate additional French historical records.
* Identify the youngest crew member involved in the incident.
* Construct the final TryHackMe flag.

---

# 🔎 Investigation

## 1. Decoding the French Postal Barcode

One of the provided assets contains an old envelope with a sequence of orange bars:

```text
..||||| |.||.| ||..|| |||..| .||.||
```

The pattern corresponds to a **French postal barcode**.

The digit mapping is:

```text
0 ..||||
1 .|.|||
2 .||.||
3 .|||.|
4 |..|||
5 |.|.||
6 |.||.|
7 ||..||
8 ||.|.|
9 |||..|
```

Breaking the barcode into its components:

```text
..|||||  → Start bar
|.||.|   → 6
||..||   → 7
|||..|   → 9
.||.||   → 2
```

This produces:

```text
06792
```

French postal barcode digits are represented in reverse order, giving:

```text
29760
```

### 📍 Result

**Postal Code: `29760`**

This points the investigation toward the Brittany region of France.

---

# 📝 2. Analyzing the Note

The provided `note.txt` contains another important clue.

The note describes the person's great-grandfather as:

* The **youngest member of a team**
* Extremely courageous
* Too young to have a driver's license
* Someone who was involved in an important event

The key clue is:

> The youngest member of the team.

This suggests that we need to find an incident involving a group or crew where the ages of the members are documented.

---

# 📰 3. Identifying the Newspaper

The newspaper clipping contains a French headline referring to **Amundsen and the North Pole**.

The headline provides an important historical timestamp.

Researching the event points toward **1925**, when Roald Amundsen's expedition attempted to reach the North Pole.

The newspaper was identified as:

**L'Ouest-Éclair**

This was a French regional newspaper serving Brittany.

The combination of:

```text
L'Ouest-Éclair
+
1925
+
Amundsen
```

provided a useful starting point for searching historical newspaper archives.

---

# 📅 4. Finding the Correct Newspaper Date

Searching the historical archives around the relevant period narrowed the investigation to:

```text
22–24 May 1925
```

The provided newspaper clipping was eventually identified as the **24 May 1925** edition of *L'Ouest-Éclair*.

However, another article from **23 May 1925** provided the crucial lead.

---

# 🚢 5. The Maritime Disaster

The newspaper reported an incident involving the fishing launch:

**Sainte-Barbe**

The incident occurred on:

**23 May 1925**

The vessel had a crew of **17 men** and encountered severe weather while returning to port.

Heavy waves overwhelmed the boat near the end of the pier, throwing the crew into the sea.

Most of the crew survived, but **one crew member drowned**.

This was the event described by the clues in the note.

---

# 🌊 6. Investigating the Crew

The newspaper article provided the basic details but not enough information to identify the youngest crew member.

Further OSINT research led to **KBC Penmarc'h**, a French historical website containing information about events and disasters around Penmarc'h.

The relevant section was:

```text
DISASTER OF MAY 23, 1925
```

The page contained detailed information about the incident and listed the members of the crew.

The note specifically tells us to look for:

> The youngest member of the team.

---

# 👤 7. Identifying the Youngest Crew Member

After examining the crew list, one person stood out:

```text
GOURLAOUEN (Yves-Marie) — 15 years old
```

This perfectly matches the clues from the note.

### Identified Person

| Field      | Result                |
| ---------- | --------------------- |
| First Name | Yves-Marie            |
| Surname    | Gourlaouen            |
| Age        | 15                    |
| Incident   | Sainte-Barbe disaster |
| Date       | 23 May 1925           |
| Location   | Brittany, France      |

Yves-Marie Gourlaouen was the **youngest member of the crew**, and historical records indicate that he was later awarded the **Silver Medal, 2nd Class**, by the French government.

---

# 🚩 8. Flag Construction

The room specifies the flag format:

```text
THM{Name_Surname_age}
```

Our information:

```text
Name: Yves-Marie
Surname: Gourlaouen
Age: 15
```

Therefore:

```text
THM{Yves-Marie_Gourlaouen_15}
```

### 🏁 Final Flag

```text
THM{Yves-Marie_Gourlaouen_15}
```

---

# 🧠 OSINT Techniques Used

This room demonstrates several useful OSINT techniques:

### 🔹 Image Analysis

Examining old documents and identifying useful visual clues.

### 🔹 Barcode Analysis

Recognizing and decoding a French postal barcode.

### 🔹 Historical Research

Using historical events to establish a timeline.

### 🔹 Newspaper Archive Research

Searching historical editions of *L'Ouest-Éclair*.

### 🔹 Geographic Pivoting

Using the postal code to narrow the investigation to Brittany.

### 🔹 Cross-Referencing

Connecting information from newspapers, notes, and historical websites.

### 🔹 Identity Resolution

Using age and crew information to identify the correct individual.

---

# 🛠️ Tools & Resources

| Tool / Resource    | Purpose                            |
| ------------------ | ---------------------------------- |
| Google             | General OSINT research             |
| Wikipedia          | French postal barcode reference    |
| Newspaper Archives | Historical newspaper investigation |
| KBC Penmarc'h      | Historical maritime records        |
| Translation tools  | Understanding French sources       |
| Image Viewer       | Examining provided assets          |

---

# 💡 Key Takeaways

The most important lesson from this room is **not to focus on a single clue**.

The investigation becomes possible by connecting multiple weak signals:

```text
Old Envelope
      ↓
French Postal Barcode
      ↓
Postal Code 29760
      ↓
Brittany, France
      ↓
Historical Newspaper
      ↓
L'Ouest-Éclair
      ↓
23 May 1925
      ↓
Sainte-Barbe Disaster
      ↓
Crew of 17
      ↓
Youngest Crew Member
      ↓
Yves-Marie Gourlaouen
      ↓
THM{Yves-Marie_Gourlaouen_15}
```

This is a good example of how **OSINT investigations are often about correlation rather than finding the answer directly**.

---

## 🏁 Conclusion

The **Letter** room demonstrates a realistic OSINT workflow where an investigator starts with a seemingly insignificant artifact and progressively extracts more information from it.

By combining barcode decoding, historical newspapers, geographic information, archival research, and identity correlation, the investigation ultimately reveals the identity of the youngest crew member involved in the 1925 *Sainte-Barbe* disaster.

**Final Flag:**

```text
THM{Yves-Marie_Gourlaouen_15}
```

---

### 📚 Skills Practiced

`OSINT` `Reconnaissance` `Image Analysis` `Historical Research` `Archive Research` `Information Correlation` `Identity Resolution` `Geolocation`
