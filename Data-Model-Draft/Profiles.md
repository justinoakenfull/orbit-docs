---
title: Profiles
description: Core entity representing user and pet profiles.
published: true
date: 2025-06-24T11:04:48.515Z
tags: 
editor: markdown
dateCreated: 2025-06-24T11:04:48.515Z
---

# Profiles

> \[!ADMONITION|note]
> The Profiles entity is central to all other features and includes permissions and gamification attributes.

```mermaid
erDiagram
    PROFILES {
        UUID profile_id PK "Primary Key"
        TEXT display_name
        TEXT profile_type "Adult / Child / Pet / Guest"
        TEXT color_code "Hex or named color"
        FILE avatar "Optional profile picture"
        DATE dob
        TEXT permissions "CRUD flags per feature"
        INT stars_earned
        TIMESTAMP created_at
    }
```

<details>
<summary>Properties & Descriptions</summary>

| Property           | Type         | Required | Notes                          |
| ------------------ | ------------ | -------- | ------------------------------ |
| **Profile ID**     | UUID         | ✅        | Primary Key                    |
| **Display Name**   | Text         | ✅        | “Mum”, “Mia”, “Zeus (the dog)” |
| **Profile Type**   | Select       | ✅        | Adult / Child / Pet / Guest    |
| **Color Code**     | Color        | ✅        | Used in calendars & lists      |
| **Avatar / Photo** | File         |          | Optional profile picture       |
| **DOB / Age**      | Date         |          | Enables age-based restrictions |
| **Permissions**    | Multi-select |          | CRUD flags per feature         |
| **Stars Earned**   | Number       |          | Gamification tally             |
| **Created At**     | Created time | ✅        | Timestamp of creation          |

</details>

*Last updated: 24 June 2025*
