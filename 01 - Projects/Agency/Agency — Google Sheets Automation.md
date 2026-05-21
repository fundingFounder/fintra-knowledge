---
type: project
status: active
stack: Python, gspread, Google Sheets API
tags: [agency, google-sheets, instagram, automation]
---

# Agency — Google Sheets Automation

> Lightweight Python tool that adds rows to a Google Sheet (Instagram content calendar for FinTra).

---

## 🔗 Connections

- **Used for:** [[FinTra — Marketing]]
- **Sheet:** Instagram content calendar (post_type, caption, image URLs, video URL, scheduled_time, status)

---

## 📊 Tech Stack

| | |
|---|---|
| **Language** | Python |
| **Library** | gspread (Google Sheets API wrapper) |
| **Auth** | google.oauth2 (OAuth2) |
| **Size** | 51 lines, single file |

## 📐 Row Schema

| Field | Purpose |
|-------|---------|
| `post_type` | Image, video, carousel, etc. |
| `caption` | Post caption + hashtags |
| `image_url_1–3` | Up to 3 image URLs |
| `video_url` | Video URL |
| `scheduled_time` | When to post |
| `status` | "ready" workflow state |

## 📄 Source

- **Path:** `/Users/dibyendumondal/Unicorns/agency/tools/add_sheet_row.py`

---

## 📋 Related

- [[FinTra — Marketing]]
- [[FinTra - Landing Page]]