# 🌙 AI-Powered Brand Valuation Engine

**Tagline:** Determining Sports Sponsorship Media Value orchestrated by qibb and powered by Twelve Labs.

---

## 🚀 The Business Case

Determining the media value of sponsorship is an inexact science and extremely labor-intensive. Sponsorship auditing in sports and entertainment is traditionally a manual, post-event process that lacks real-time visibility and often relies on "best guesses" for brand value.

This solution is built entirely within **qibb** as the orchestration backbone. It detects the presence of sponsorship elements within a broadcast, determines their "prominence," and calculates the media value delivered by benchmarking against the traditional :30 spot.

The qibb-powered workflow automates this entire lifecycle:

- **Instant ROI:** Attaches actual dollar values to brand appearances in real-time based on duration and prominence.
- **Customizable:** Allows marketers and sponsorship salespeople to adjust the tool to account for audience size, CPM, and level of impact.
- **Audit-Ready:** Provides deep links that jump a video player to the exact second a brand appears for 100% verification.
- **Scalable:** Handles high-density environments (NASCAR, FIFA, NBA) where dozens of brands appear simultaneously, leveraging qibb's robust enterprise infrastructure.
- **MAM-Agnostic:** Works with any Media Asset Management system. Currently live with both **Iconik** and **Mimir**, feeding a single unified dashboard.

---

## 🏗️ System Architecture & Logic

### Agnostic by Design

qibb acts as a system-agnostic orchestration layer, seamlessly bridging any MAM with any Video AI engine. The same pipeline runs identically whether the source asset comes from Iconik or Mimir — both feed into a single unified Brand Exposure dashboard.

### The Processing Pipeline

```
MAM Webhook / Custom Action
        ↓
qibb Workflow Trigger
        ↓
GET Asset + Extract Proxy URL
        ↓
Check for existing Twelve Labs Video ID
    ├── Found → skip upload, reuse ID
    └── Not found → Upload via /tasks (multipart)
        ↓
Poll Task Status (uploading → pending → ready)
        ↓
POST /analyze (brand detection prompt)
        ↓
Extract: title, summary, topics, hashtags, chapters, highlights
        ↓
┌─────────────────────────────────────────────┐
│  Write back to MAM (PATCH metadata)         │
│  · tl_generated_title                       │
│  · tl_generated_summary                     │
│  · tl_video_id                              │
│  · tl_generated_hashtags / topics           │
│  · TwelveLabs_status (live updates)         │
└─────────────────────────────────────────────┘
        ↓
Post timecoded Comments to MAM
    · 📖 Chapters (with summary)
    · 🏷️ Brand highlights (with prominence + screen time)
        ↓
Valuation Engine
    · Prominence tier: DOMINANT / PROMINENT / MODERATE / SUBTLE
    · ROI: Duration × Tier Rate = Media Value
        ↓
POST to Universal Dashboard DB
        ↓
Slack Notifications (job start, upload, indexing, analysis, complete)
```

### Valuation Logic

| Tier | Rate | Criteria |
|---|---|---|
| DOMINANT | $1,000/s | Logo fills large portion of frame; focal point |
| PROMINENT | $1,000/s | Clearly readable; significant screen space |
| MODERATE | $500/s | Visible but sharing attention with other elements |
| SUBTLE | $100/s | Small, background, or briefly visible |

> Rate card is fully customizable per client via qibb flow variables.

---

## ✨ Key Features

- **Universal Dashboard:** A single "Brand Exposure Tracker" UI aggregates results from both Iconik and Mimir workflows, with source-tagged badges and deep links back to the originating MAM.
- **AI Integration:** High-velocity logo detection using multimodal AI (Twelve Labs Marengo), routed natively through qibb with a custom multipart HTTP implementation.
- **Live Status Updates:** `TwelveLabs_status` field updates in real-time as the asset moves through each pipeline stage.
- **Timecoded Comments:** Chapters and brand highlights are written back to the MAM as timecoded comments — click any entry to jump the video player to that exact moment.
- **Verification Engine:** Direct deep-links to the MAM (Iconik or Mimir) for frame-accurate proof of performance.
- **Duplicate Prevention:** Checks for an existing `tl_video_id` before uploading — assets are only indexed once regardless of how many times the workflow triggers.
- **Slack Notifications:** Real-time Slack updates at every pipeline stage — job start, upload, indexing, analysis, and completion with full brand report.
- **One-Click Reporting:** PDF export and CSV data for financial teams, driven by qibb automation.

---

## 🛠️ Technology Stack

| Component | Technology |
|---|---|
| Orchestration | **qibb** (Enterprise Node-RED Engine) |
| Video AI | **Twelve Labs** Marengo (qibb is AI-agnostic) |
| Media Management | **Iconik** + **Mimir** (qibb is MAM-agnostic) |
| Frontend UI | Vanilla JS, Chart.js, HTML5/CSS3 (hosted via qibb) |
| Data Storage | qibb Global Context (high-speed native storage) |
| Notifications | Slack Web API |
| Auth | Keycloak (dashboard SSO) |

---

## 🔌 Supported MAM Integrations

| MAM | Status | Notes |
|---|---|---|
| Iconik | ✅ Live | Custom Action webhook trigger |
| Mimir | ✅ Live | Webhook + manual inject trigger |

Both sources feed the same universal dashboard. Mimir and Iconik assets appear side-by-side with source badges and MAM-specific deep links.

---

## 📂 Repository Contents

- `index.html` — Interactive brand exposure dashboard (live demo)
- `README.md` — System architecture and project documentation
- `/screenshots` — Evidence of the live production environment and qibb orchestration

---

## 🔗 Live Demo

**[View the Interactive Brand Exposure Dashboard →](https://daveeuson.github.io/tl2026Dash/)**

---

## 📬 Contact

Built by **Dave Euson**, Solutions Architect @ Qibb  
Technical deep-dives into the workflow and qibb architecture available on request.
