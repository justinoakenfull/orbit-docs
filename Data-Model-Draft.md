---
title: Data Model Draft
description: Initial entity–relationship draft for Orbit’s data layer.
published: true
date: 2025-06-24T11:11:48.839Z
tags: architecture, data
editor: markdown
dateCreated: 2025-06-24T08:06:32.716Z
---

# Data Model Draft

> **📊 Orbit – Data Model Cheat-Sheet**  
> *A living reference for every database/table we'll need to power Orbit's features.*

---

## 🧑‍🚀 1 · Profiles (core to all features)

> **Primary Entity**: Core user profiles that drive all system functionality

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Profile ID** | UUID | :white_check_mark: | Primary Key |
| **Display Name** | Text | :white_check_mark: | "Mum", "Mia", "Zeus (the dog)" |
| **Profile Type** | Select | :white_check_mark: | Adult / Child / Pet / Guest |
| **Color Code** | Color | :white_check_mark: | Used in calendars & lists |
| **Avatar / Photo** | File | :x: | Optional profile picture |
| **DOB / Age** | Date | :x: | Enables age-based restrictions |
| **Permissions** | Multi-select | :x: | CRUD flags per feature |
| **Stars Earned** | Number | :x: | Gamification tally |
| **Created At** | Created time | :white_check_mark: | — |

---

## 📝 2 · Customisable Lists

### Entity A – List

> **Purpose**: Container for organized list items across different categories

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **List ID** | UUID | :white_check_mark: | — |
| **Name** | Text | :white_check_mark: | "Groceries", "Camping gear" |
| **Category** | Select | :x: | Shopping / To-Do / Custom |
| **Created By → Profile** | Relation | :white_check_mark: | Author |
| **Shared With → Profiles** | Relation | :x: | Multi-person ownership |
| **Is Archived** | Checkbox | :x: | Hide old lists |
| **Created At** | Created time | :white_check_mark: | — |
| **Updated At** | Last edited time | :white_check_mark: | — |

### Entity B – List Item

> **Purpose**: Individual items within lists with assignment and completion tracking

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Item ID** | UUID | :white_check_mark: | — |
| **List → List** | Relation | :white_check_mark: | Parent list |
| **Name** | Text | :white_check_mark: | "Milk", "Pack tent" |
| **Quantity** | Number | :x: | e.g. 4 |
| **Is Completed** | Checkbox | :white_check_mark: | — |
| **Assigned To → Profile** | Relation | :x: | Who will do/buy it |
| **Due Date** | Date | :x: | Optional reminder |
| **Notes** | Text | :x: | Extra info |
| **Created At** | Created time | :white_check_mark: | — |

---

## 🧹 3 · Chore Chart & Gamification

### Entity A – Chore Template

> **Purpose**: Define reusable chore types with scheduling and point systems

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Chore ID** | UUID | :white_check_mark: | — |
| **Name** | Text | :white_check_mark: | "Wash dishes" |
| **Chore Type** | Select | :white_check_mark: | Permanent / Rotating / Routine |
| **Frequency** | Select | :x: | Daily, Weekly… |
| **Default Points** | Number | :x: | Stars awarded |
| **Routine Slot** | Select | :x: | Morning / Evening / Night |
| **Is Active** | Checkbox | :white_check_mark: | Toggle visibility |

### Entity B – Chore Instance

> **Purpose**: Individual chore assignments per day/person (One row per day/assignment)

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Instance ID** | UUID | :white_check_mark: | — |
| **Template → Chore Template** | Relation | :white_check_mark: | — |
| **Assigned To → Profile** | Relation | :white_check_mark: | — |
| **Scheduled Date** | Date | :white_check_mark: | — |
| **Status** | Select | :white_check_mark: | Pending / Done / Missed |
| **Points Earned** | Number | :x: | Overwrite default if needed |
| **Completed At** | Date | :x: | Timestamp |

### Entity C – Reward / Family Piggy Bank

> **Purpose**: Manage family rewards and gamification incentives

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Reward ID** | UUID | :white_check_mark: | — |
| **Name** | Text | :white_check_mark: | "Movie night" |
| **Threshold Stars** | Number | :white_check_mark: | Stars needed |
| **Is Unlocked** | Checkbox | :x: | — |

---

## 📅 4 · Calendar

### Entity – Event

> **Purpose**: Manage family events, appointments, and scheduling

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Event ID** | UUID | :white_check_mark: | — |
| **Title** | Text | :white_check_mark: | "Dentist" |
| **Start Time** | Date/Time | :white_check_mark: | — |
| **End Time** | Date/Time | :white_check_mark: | — |
| **All-Day** | Checkbox | :x: | — |
| **Recurring** | Text | :x: | iCal RRULE |
| **Location** | Text | :x: | Optional |
| **Created By → Profile** | Relation | :white_check_mark: | — |
| **Attendees → Profiles** | Relation | :x: | Multi-select |
| **Color Override** | Color | :x: | Defaults to profile color |
| **Reminder Minutes** | Number | :x: | e.g. 30 |
| **Notes** | Text | :x: | — |

---

## 🍽️ 5 · Meal Planner

### Entity A – Meal

> **Purpose**: Plan and track family meals with preparation assignments

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Meal ID** | UUID | :white_check_mark: | — |
| **Date** | Date | :white_check_mark: | Day scheduled |
| **Meal Type** | Select | :white_check_mark: | Breakfast / Lunch / Dinner |
| **Name** | Text | :white_check_mark: | "Spaghetti Bolognese" |
| **Prepared By → Profile** | Relation | :x: | Chef |
| **Recipe URL / Doc** | URL | :x: | Link to recipe |
| **Is Favourite** | Checkbox | :x: | For quick adds |

### Entity B – Ingredient

> **Purpose**: Optional granular tracking of meal ingredients

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Ingredient ID** | UUID | :white_check_mark: | — |
| **Meal → Meal** | Relation | :white_check_mark: | Parent |
| **Name** | Text | :white_check_mark: | — |
| **Quantity** | Text | :x: | "500 g" |

---

## ⏰ 6 · Routine Manager

> **Purpose**: Automate recurring family routines and linked chores

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Routine ID** | UUID | :white_check_mark: | — |
| **Name** | Text | :white_check_mark: | "Bedtime" |
| **Start Time** | Time | :white_check_mark: | Auto-trigger |
| **End Time** | Time | :x: | — |
| **Days Of Week** | Multi-select | :white_check_mark: | Mon – Sun |
| **Steps / Linked Chores → Chore Templates** | Relation | :x: | — |
| **Created By → Profile** | Relation | :white_check_mark: | — |
| **Is Enabled** | Checkbox | :white_check_mark: | Toggle |

---

## 🗒️ 7 · Sticky Notes & Guest Tab

### Sticky Note

> **Purpose**: Quick family notes and reminders with visual positioning

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Note ID** | UUID | :white_check_mark: | — |
| **Content** | Text | :white_check_mark: | Rich text ok |
| **Color** | Color | :x: | Yellow, pink… |
| **Position** | Text | :x: | Canvas X,Y or column order |
| **Created By → Profile** | Relation | :white_check_mark: | — |
| **Created At** | Created time | :white_check_mark: | — |
| **Expiry Date** | Date | :x: | Auto-purge |

### Guest Info

> **Purpose**: Store guest access information and instructions

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **SSID** | Text | :white_check_mark: | Wi-Fi name |
| **Password** | Text | :white_check_mark: | — |
| **QR Code Image** | File | :x: | Stored PNG/SVG |
| **Guest Notes** | Text | :x: | Checkout instructions |

---

## ☎️ 8 · Address Book & Emergency Contacts

> **Purpose**: Centralized contact management with emergency flagging

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Contact ID** | UUID | :white_check_mark: | — |
| **Name** | Text | :white_check_mark: | — |
| **Phone** | Phone | :x: | — |
| **Email** | Email | :x: | — |
| **Address** | Text | :x: | — |
| **Birthday** | Date | :x: | Enables celebrations |
| **Is Emergency** | Checkbox | :x: | Flag |
| **Notes** | Text | :x: | Relationship, allergies… |

---

## 🚨 9 · Family Alerts

> **Purpose**: Internal family communication system with priority levels

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Alert ID** | UUID | :white_check_mark: | — |
| **Message** | Text | :white_check_mark: | — |
| **Sent By → Profile** | Relation | :white_check_mark: | — |
| **Sent At** | Created time | :white_check_mark: | — |
| **Recipients → Profiles** | Relation | :x: | All or subset |
| **Priority** | Select | :x: | Info / Warning / Critical |
| **Requires Ack** | Checkbox | :x: | Track read receipts |

---

## 🖼️ 10 · Photo Screensaver

> **Purpose**: Configure family photo display settings

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Folder Path** | Text | :white_check_mark: | Local or NAS |
| **Shuffle** | Checkbox | :x: | Randomise order |
| **Display Duration (sec)** | Number | :white_check_mark: | Per image |
| **Last Updated** | Last edited time | :white_check_mark: | — |

---

## 🔕 11 · Quiet Time Toggle

> **Purpose**: System-wide notification management

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Is Enabled** | Checkbox | :white_check_mark: | Global mute |
| **Start Time** | Time | :x: | — |
| **End Time** | Time | :x: | — |
| **Days** | Multi-select | :x: | — |

---

## ☁️ 12 · Calendar Sync Accounts

> **Purpose**: External calendar integration and synchronization

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Account ID** | UUID | :white_check_mark: | — |
| **Provider** | Select | :white_check_mark: | Google / iCloud / Outlook |
| **Email / Username** | Email | :white_check_mark: | — |
| **Auth Token** | Text | :white_check_mark: | Encrypted |
| **Last Sync At** | Date/Time | :x: | — |
| **Sync Prefs** | Text | :x: | One-way / Two-way etc. |

---

## ⛈️ 13 · Weather Widget Settings

> **Purpose**: Weather display configuration and alerts

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Location** | Text | :white_check_mark: | "Brisbane, AU" |
| **Units** | Select | :white_check_mark: | °C / °F |
| **Show Dress Tips** | Checkbox | :x: | "Bring umbrella" |
| **Alert Threshold (mm rain)** | Number | :x: | — |

---

## 🎙️ 14 · Voice Command Preferences

> **Purpose**: Voice interaction configuration and security

| Property | Type | Required | Notes |
|----------|------|----------|-------|
| **Enabled** | Checkbox | :white_check_mark: | — |
| **Language** | Select | :white_check_mark: | en-AU, etc. |
| **Hotword** | Text | :x: | "Hey Orbit" |
| **Allowed Profiles → Profiles** | Relation | :x: | Security |

---

> **📅 Last updated**: 24 June 2025

## Navigation

- [Profiles](#1--profiles-core-to-all-features)
- [Lists](#2--customisable-lists)
- [Chores](#3--chore-chart--gamification)
- [Calendar](#4--calendar)
- [Meals](#5--meal-planner)
- [Routines](#6--routine-manager)
- [Notes](#7--sticky-notes--guest-tab)
- [Contacts](#8--address-book--emergency-contacts)
- [Alerts](#9--family-alerts)
- [Settings](#10--photo-screensaver)