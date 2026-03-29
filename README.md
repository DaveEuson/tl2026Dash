# 🌙 AI-Powered Brand Valuation Engine

**Tagline:** Determining Sports Sponsorship Media Value orchestrated by qibb and powered by Twelve Labs.

---

## 🚀 The Business Case

Determining the media value of sponsorship is an inexact science and extremely labor-intensive. Sponsorship auditing in sports and entertainment is traditionally a manual, post-event process that lacks real-time visibility and often relies on "best guesses" for brand value.

This solution is designed entirely within qibb as the backbone to solve this industry bottleneck. It detects the presence of sponsorship elements within a broadcast, determines their “prominence,” and calculates the media value delivered by benchmarking its impact against the traditional :30 spot.

**Our qibb-powered workflow automates this entire lifecycle:**
* **Instant ROI:** Attaches actual dollar values to brand appearances in real-time based on duration and prominence.
* **Customizable:** Allows marketers and sponsorship salespeople to adjust the qibb tool to account for audience size, CPM, and level of impact.
* **Audit-Ready:** Provides deep links that jump a video player to the exact second a brand appears for 100% verification.
* **Scalable:** Handles high-density environments (NASCAR, FIFA, NBA) where dozens of brands appear simultaneously, leveraging qibb's robust enterprise infrastructure.

---

## 🏗️ System Architecture & Logic

**Agnostic by Design:** This project is built as a qibb workflow. qibb acts as a system-agnostic orchestration layer, meaning it can seamlessly bridge *any* Media Asset Management (MAM) system with *any* Language Model or Video AI. 

*Note: For the purposes of this demo, the workflow utilizes Iconik as the MAM and Twelve Labs as the AI engine.*

### The Processing Pipeline:
1. **Ingest & Trigger:** A webhook from the connected MAM (e.g., Iconik) fires on `metadata_update` or `asset_creation`, instantly triggering a qibb flow.
2. **Cognitive Analysis:** The qibb orchestration passes the media payload to the Video AI engine (e.g., Twelve Labs Marengo-2.6), which performs temporal brand detection to identify logos even in high-motion sports footage.
3. **Valuation Engine:** * **Normalization:** Raw AI confidence scores and pixel-area data are mapped to Prominence Tiers (Dominant, Prominent, Moderate, Subtle) within qibb.
   * **ROI Calculation:** A custom qibb logic node applies rate-card values: `(Duration_Seconds * Tier_Rate) = Total_Media_Value`.
4. **State Management:** Data is persisted in the qibb dashboard and served via an authenticated API directly to the frontend dashboard and back to the connected MAM.

*Technical deep-dives into the workflow and qibb architecture are available upon request.*

---

## ✨ Key Features

* **AI Integration:** High-velocity logo detection using multimodal AI (demonstrated with Twelve Labs), routed natively through qibb.
* **Verification Engine:** Direct deep-links to the MAM, generated seamlessly by qibb for frame-accurate proof of performance.
* **Native Dashboard:** A custom "Tokyo Night" themed UI built directly on qibb's interface layer for stakeholders to visualize data without leaving the media environment.
* **One-Click Reporting:** Automated export capabilities for PDF Sponsor Reports and CSV data for financial teams, driven by qibb automation.

---

## 🛠️ Technology Stack

| Component | Technology |
| :--- | :--- |
| **Orchestration** | [qibb](https://www.qibb.com/) (Enterprise Node-RED Engine) |
| **Video AI** | [Twelve Labs](https://www.twelvelabs.io/) *(Demo solution; qibb is AI-agnostic)* |
| **Media Management** | [Iconik](https://www.iconik.io/) *(Demo solution; qibb is MAM-agnostic)* |
| **Frontend UI** | Vanilla JS, Chart.js, HTML5/CSS3 (Hosted via qibb) |
| **Data Storage** | qibb Global Context (High-speed native storage) |

---

## 📂 Repository Contents

* `index.html`: The interactive mock dashboard (The "Live Demo").
* `/screenshots`: Evidence of the live production environment and backend qibb orchestration.
* `README.md`: System architecture and project documentation.

---

## 🔗 Live Demo URL

[View the Interactive Dashboard Preview of qibb dashboard here](https://DaveEuson.github.io/tl2026Dash/)
