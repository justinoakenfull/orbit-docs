---
title: Minimal Viable Product (MVP)
description: Scope, rationale, and exclusions for Orbit’s MVP release.
published: true
date: 2025-06-24T10:46:19.898Z
tags: design, ui, architecture, data, features, scope
editor: markdown
dateCreated: 2025-06-24T07:53:45.387Z
---

# Minimum Viable Product

# **Introduction & Goal**

Orbit’s MVP aims to deliver a streamlined yet highly functional touchscreen-based family hub. The objective is to clearly demonstrate core usability, facilitate household management tasks, and verify the primary value proposition. Simplifying and organising family life through a central, intuitive interface.

# **Included Features**

**1. Calendar**

- Views: Week & Month
- Functionality:
    - Create, edit, delete events (Adults only)
    - View events (All profiles)
- Justification: Essential for family scheduling, ensuring visibility of appointments and events, foundational feature for household management.

**2. Customisable Lists**

- Functionality:
    - Users create custom lists (e.g., shopping, to-do)
    - Add, edit, remove items
- Justification: Provides flexibility and addresses various household needs efficiently without predetermined constraints.

**3. Chore Chart**

- Functionality:
    - Assign and track chores
    - Simple gamification (star/points)
    - Mark chores as completed (All profiles)
- Justification: Centralizes household responsibilities, introduces motivation through gamification, and ensures clarity about household tasks.

**4. Sticky Notes**

- Functionality:
    - Quick, easily accessible notes pinned to the main dashboard
    - Adults create, edit, delete notes; children view notes only
- Justification: Fast, simple communication method, replacing physical notes and reducing clutter.

**5. User Profiles & Restrictions**

| **Feature / Action** | **Adult (18 +)** | **Teen (13-17)** | **Child (≤12)** |
| --- | --- | --- | --- |
| **Create events** | ✅ (anyone) | ⚠️ (self + opt. shared) | ❌ |
| **Edit / delete events** | ✅ (anyone) | ⚠️ (self-created only) | ❌ |
| **View calendar events** | ✅ | ✅ | ✅ |
| **Create personal lists** | ✅ | ⚠️ (own lists only) | ❌ |
| **Edit / delete personal lists** | ✅ | ⚠️ (own lists only) | ❌ |
| **View family lists** | ✅ | ✅ | ✅ |
| **Assign chores** | ✅ | ❌ | ❌ |
| **Mark chores as completed** | ✅ | ✅ | ✅ |
| **Create sticky notes** | ✅ | ✅  | ❌ |
| **Edit / delete sticky notes** | ✅ | ⚠️ (own notes) | ❌ |
| **Broadcast family-wide alerts** | ✅ | ❌ | ❌ |
| **Receive family-wide alerts** | ✅ | ✅ | ✅ |
| **Change profile photos / colours** | ✅ (anyone) | ⚠️ (own profile) | ❌ |
| **Gamification (earn stars)** | Optional | ✅ | ✅ |
| **Access settings / integrations** | ✅ (anyone) | ⚠️ (own profile) | ❌ |
- Justification: Clearly defined user roles ensure both functionality and appropriate restrictions, maintaining system integrity and usability for all family members.

**6. Family-wide Alerts**

- Functionality:
    - Broadcast urgent or important notifications instantly to all connected devices
- Justification: Critical communication tool for timely, effective notifications within a household.

# **Out-of-Scope Features (MVP Exclusions)**

| **Feature** | **Reason for Exclusion** |
| --- | --- |
| Advanced Gamification | Requires extensive development; foundational system validation first |
| Guest Tab (Wi-Fi QR codes) | Convenience-oriented; secondary to initial family coordination |
| Voice Command Integration | Complexity and licensing challenges; deferring to post-MVP |
| Weather Widgets | External integrations and recurring costs; not essential initially |
| Photo Screensaver & Event Animations | Aesthetic and engagement features; secondary priority |
| Cloud Sync | Technical complexity, undefined scope, potential licensing, and costs |

**Partial Inclusion (Post-MVP Priority)**

- Emergency Contacts & Detailed Address Book:
    - Recognized importance but prioritizing immediate usability features. Will become an early post-MVP addition due to practical household benefit.

This document clearly outlines Orbit’s initial MVP scope, ensuring focus on fundamental functionality, efficient development, and a solid foundation for future expansions.

---

*Last updated: 28 May 2025*