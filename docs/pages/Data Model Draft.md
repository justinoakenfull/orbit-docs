# Data Model Draft

# 📊 Orbit – Data Model Cheat-Sheet

*A living reference for every database/table we’ll need to power Orbit’s features.*

---

## 🧑‍🚀 1 · Profiles (core to all features)

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Profile ID** | UUID | ✅ | Primary Key |
| **Display Name** | Text | ✅ | “Mum”, “Mia”, “Zeus (the dog)” |
| **Profile Type** | Select | ✅ | Adult / Child / Pet / Guest |
| **Color Code** | Color | ✅ | Used in calendars & lists |
| **Avatar / Photo** | File |  | Optional profile picture |
| **DOB / Age** | Date |  | Enables age-based restrictions |
| **Permissions** | Multi-select |  | CRUD flags per feature |
| **Stars Earned** | Number |  | Gamification tally |
| **Created At** | Created time | ✅ | — |

---

## 📝 2 · Customisable Lists

### Entity A – List

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **List ID** | UUID | ✅ | — |
| **Name** | Text | ✅ | “Groceries”, “Camping gear” |
| **Category** | Select |  | Shopping / To-Do / Custom |
| **Created By → Profile** | Relation | ✅ | Author |
| **Shared With → Profiles** | Relation |  | Multi-person ownership |
| **Is Archived** | Checkbox |  | Hide old lists |
| **Created At** | Created time | ✅ | — |
| **Updated At** | Last edited time | ✅ | — |

### Entity B – List Item

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Item ID** | UUID | ✅ | — |
| **List → List** | Relation | ✅ | Parent list |
| **Name** | Text | ✅ | “Milk”, “Pack tent” |
| **Quantity** | Number |  | e.g. 4 |
| **Is Completed** | Checkbox | ✅ | — |
| **Assigned To → Profile** | Relation |  | Who will do/buy it |
| **Due Date** | Date |  | Optional reminder |
| **Notes** | Text |  | Extra info |
| **Created At** | Created time | ✅ | — |

---

## 🧹 3 · Chore Chart & Gamification

### Entity A – Chore Template

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Chore ID** | UUID | ✅ | — |
| **Name** | Text | ✅ | “Wash dishes” |
| **Chore Type** | Select | ✅ | Permanent / Rotating / Routine |
| **Frequency** | Select |  | Daily, Weekly… |
| **Default Points** | Number |  | Stars awarded |
| **Routine Slot** | Select |  | Morning / Evening / Night |
| **Is Active** | Checkbox | ✅ | Toggle visibility |

### Entity B – Chore Instance

(One row per day/assignment)

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Instance ID** | UUID | ✅ | — |
| **Template → Chore Template** | Relation | ✅ | — |
| **Assigned To → Profile** | Relation | ✅ | — |
| **Scheduled Date** | Date | ✅ | — |
| **Status** | Select | ✅ | Pending / Done / Missed |
| **Points Earned** | Number |  | Overwrite default if needed |
| **Completed At** | Date |  | Timestamp |

### Entity C – Reward / Family Piggy Bank

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Reward ID** | UUID | ✅ | — |
| **Name** | Text | ✅ | “Movie night” |
| **Threshold Stars** | Number | ✅ | Stars needed |
| **Is Unlocked** | Checkbox |  | — |

---

## 📅 4 · Calendar

### Entity – Event

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Event ID** | UUID | ✅ | — |
| **Title** | Text | ✅ | “Dentist” |
| **Start Time** | Date/Time | ✅ | — |
| **End Time** | Date/Time | ✅ | — |
| **All-Day** | Checkbox |  | — |
| **Recurring** | Text |  | iCal RRULE |
| **Location** | Text |  | Optional |
| **Created By → Profile** | Relation | ✅ | — |
| **Attendees → Profiles** | Relation |  | Multi-select |
| **Color Override** | Color |  | Defaults to profile color |
| **Reminder Minutes** | Number |  | e.g. 30 |
| **Notes** | Text |  | — |

---

## 🍽️ 5 · Meal Planner

### Entity A – Meal

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Meal ID** | UUID | ✅ | — |
| **Date** | Date | ✅ | Day scheduled |
| **Meal Type** | Select | ✅ | Breakfast / Lunch / Dinner |
| **Name** | Text | ✅ | “Spaghetti Bolognese” |
| **Prepared By → Profile** | Relation |  | Chef |
| **Recipe URL / Doc** | URL |  | Link to recipe |
| **Is Favourite** | Checkbox |  | For quick adds |

### Entity B – Ingredient (optional granular tracking)

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Ingredient ID** | UUID | ✅ | — |
| **Meal → Meal** | Relation | ✅ | Parent |
| **Name** | Text | ✅ | — |
| **Quantity** | Text |  | “500 g” |

---

## ⏰ 6 · Routine Manager

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Routine ID** | UUID | ✅ | — |
| **Name** | Text | ✅ | “Bedtime” |
| **Start Time** | Time | ✅ | Auto-trigger |
| **End Time** | Time |  | — |
| **Days Of Week** | Multi-select | ✅ | Mon – Sun |
| **Steps / Linked Chores → Chore Templates** | Relation |  | — |
| **Created By → Profile** | Relation | ✅ | — |
| **Is Enabled** | Checkbox | ✅ | Toggle |

---

## 🗒️ 7 · Sticky Notes & Guest Tab

### Sticky Note

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Note ID** | UUID | ✅ | — |
| **Content** | Text | ✅ | Rich text ok |
| **Color** | Color |  | Yellow, pink… |
| **Position** | Text |  | Canvas X,Y or column order |
| **Created By → Profile** | Relation | ✅ | — |
| **Created At** | Created time | ✅ | — |
| **Expiry Date** | Date |  | Auto-purge |

### Guest Info

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **SSID** | Text | ✅ | Wi-Fi name |
| **Password** | Text | ✅ | — |
| **QR Code Image** | File |  | Stored PNG/SVG |
| **Guest Notes** | Text |  | Checkout instructions |

---

## ☎️ 8 · Address Book & Emergency Contacts

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Contact ID** | UUID | ✅ | — |
| **Name** | Text | ✅ | — |
| **Phone** | Phone |  | — |
| **Email** | Email |  | — |
| **Address** | Text |  | — |
| **Birthday** | Date |  | Enables celebrations |
| **Is Emergency** | Checkbox |  | Flag |
| **Notes** | Text |  | Relationship, allergies… |

---

## 🚨 9 · Family Alerts

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Alert ID** | UUID | ✅ | — |
| **Message** | Text | ✅ | — |
| **Sent By → Profile** | Relation | ✅ | — |
| **Sent At** | Created time | ✅ | — |
| **Recipients → Profiles** | Relation |  | All or subset |
| **Priority** | Select |  | Info / Warning / Critical |
| **Requires Ack** | Checkbox |  | Track read receipts |

---

## 🖼️ 10 · Photo Screensaver

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Folder Path** | Text | ✅ | Local or NAS |
| **Shuffle** | Checkbox |  | Randomise order |
| **Display Duration (sec)** | Number | ✅ | Per image |
| **Last Updated** | Last edited time | ✅ | — |

---

## 🔕 11 · Quiet Time Toggle

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Is Enabled** | Checkbox | ✅ | Global mute |
| **Start Time** | Time |  | — |
| **End Time** | Time |  | — |
| **Days** | Multi-select |  | — |

---

## ☁️ 12 · Calendar Sync Accounts

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Account ID** | UUID | ✅ | — |
| **Provider** | Select | ✅ | Google / iCloud / Outlook |
| **Email / Username** | Email | ✅ | — |
| **Auth Token** | Text | ✅ | Encrypted |
| **Last Sync At** | Date/Time |  | — |
| **Sync Prefs** | Text |  | One-way / Two-way etc. |

---

## ⛈️ 13 · Weather Widget Settings

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Location** | Text | ✅ | “Brisbane, AU” |
| **Units** | Select | ✅ | °C / °F |
| **Show Dress Tips** | Checkbox |  | “Bring umbrella” |
| **Alert Threshold (mm rain)** | Number |  | — |

---

## 🎙️ 14 · Voice Command Preferences

| Property | Type | Required | Notes |
| --- | --- | --- | --- |
| **Enabled** | Checkbox | ✅ | — |
| **Language** | Select | ✅ | en-AU, etc. |
| **Hotword** | Text |  | “Hey Orbit” |
| **Allowed Profiles → Profiles** | Relation |  | Security |

---

*Last updated: 24 June 2025*