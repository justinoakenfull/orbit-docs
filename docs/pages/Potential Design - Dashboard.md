# Potential Design - Dashboard

# Orbit - **Dashboard Layout**

> Everything below is intentionally in a code-block so you can paste it straight into Notion.
> 

## 1 · Top Status Bar (persistent, 56 px-ish)

| Element | Purpose |
| --- | --- |
| **Date & time** (big, left-aligned) | Immediate orientation |
| **Quiet-Time toggle** | One-tap household mute |
| **Sync indicator** | Shows calendar/cloud sync status |
| **Profile avatar switcher** | Changes colour-coding + access level |

---

## 2 · Primary Quick-Glance Row (large cards, swipeable if overflow)

| Card | Contents | Tap action |
| --- | --- | --- |
| **Today’s Schedule** | • Next 3 events (colour-coded) <br>• “+” to add event | Opens **Calendar** page, day view |
| **Weather Now / Dress For Today** | • Icon + temp <br>• Rain alert badge | Opens **Weather** page |
| **Chores Due** | • 3 highest-priority chores for this profile<br>• Stars earned today | Opens **Chores** page |
| **Shopping List Snapshot** | • First unchecked items on default list | Opens **Lists** page (shopping view) |

*Rationale:* These four cover the highest-frequency “what’s next” checks for most households (events, weather, chores, lists). ➜ All data points come from your existing feature set :contentReference[oaicite:0]{index=0}.

---

## 3 · Secondary Widgets Grid (two-column, scrollable)

| Widget | Details |
| --- | --- |
| **Meal Planner Tonight** | Dish name, “Favourite” tag, quick-edit icon |
| **Family Alerts Banner** | Stacked chips for unread alerts; tap to expand history |
| **Sticky Notes Board** | Up to three most-recent notes; long-press to delete |
| **Gamification Snapshot** | Star balance, piggy-bank progress bar, this week’s leaderboard top 3 |
| **Upcoming Celebrations** | Next birthday/anniversary + confetti icon |

---

## 4 · Quick-Actions Dock (bottom, chunky buttons)

| Button | Icon | Visible to |
| --- | --- | --- |
| **+ Event** | calendar-plus | Adults, Teens (if permitted) |
| **+ List Item** | checklist | All profiles |
| **+ Chore** | broom | Adults |
| **Voice Command** | mic | All profiles (press-and-hold PTT) |
| **Emergency** | phone-alert | Always visible, opens **Emergency** page instantly |

---

## 5 · Contextual Photo Screensaver

*When idle for n minutes*, the dashboard fades into the rotating family photo gallery. A tap returns to the dashboard.

---

### Interaction Notes

- All cards/buttons are ≥ 64 px tall for easy touch targets on a wall-mounted 27″ tablet.
- Colour palette matches profile colour-coding to reinforce whose data is shown.
- Dashboard respects **Profile Restrictions**: e.g., a Child profile hides Quiet-Time toggle and Gamification leaderboard totals for other users.
- Quiet-Time state subtly tints the status bar (e.g., dark slate) so adults can see at a glance that notifications are muted.
- Voice Command button triggers on-device STT; fallback to offline intent library if no Internet.
- Widgets should lazy-refresh to keep the page lightweight; heavy lists (full chores grid, deep list views) live on their dedicated pages.

---

### Navigation Model

The *pages* list you already sketched stays: **Dashboard · Calendar · Lists · Chores · Weather · Address · Profile · Settings · Emergency**.

The Dashboard simply mirrors a *summary* slice of each, giving everyone one-tap depth where needed.