# 🌙 AI-Powered Brand Valuation Engine

**Tagline:** Determining Sports Sponsorship Media Value powered by **Twelve Labs** and **qibb**.

---

## 🚀 The Business Case

Determining the media value of sponsorship is an inexact science and extremely labor-intensive. Sponsorship auditing in sports and entertainment is traditionally a manual, post-event process that lacks real-time visibility and often relies on "best guesses" for brand value.

Our solution detects the presence of sponsorship elements within a broadcast, determines their “prominence,” and calculates the media value delivered by benchmarking its impact against the traditional :30 spot.

**Our solution automates this entire lifecycle:**
* **Instant ROI:** Attaches actual dollar values to brand appearances based on duration and prominence.
* **Customizable:** Allows marketers and sponsorship salespeople to adjust the tool to account for audience size, CPM, and level of impact.
* **Audit-Ready:** Provides deep links that jump a video player to the exact second a brand appears for 100% verification.
* **Scalable:** Handles high-density environments (NASCAR, FIFA, NBA) where dozens of brands appear simultaneously.

---

## 🏗️ System Architecture & Logic

This project is built as a native **qibb** application. The backend utilizes a high-performance orchestration layer to bridge professional media tools with cutting-edge Video AI.

### The Processing Pipeline:
1.  **Ingest & Trigger:** An **Iconik** webhook fires on `metadata_update` or `asset_creation`.
2.  **Cognitive Analysis:** The **Twelve Labs Marengo-2.6** engine performs temporal brand detection, identifying logos even in high-motion sports footage.
3.  **Valuation Engine:** * **Normalization:** Raw AI confidence scores and pixel-area data are mapped to Prominence Tiers (Dominant, Prominent, Moderate, Subtle).
    * **ROI Calculation:** A proprietary logic node applies rate-card values: `(Duration_Seconds * Tier_Rate) = Total_Media_Value`.
4.  **State Management:** Data is persisted in the **qibb Global Context** and served via an authenticated API to the frontend dashboard.

> **Note on Source Code:** Due to the proprietary nature of the enterprise orchestration layer and custom Qibb nodes, the raw backend JSON flow is not included in this public repository. Technical deep-dives are available upon request.

---

## ✨ Key Features

* **Twelve Labs Integration:** High-velocity logo detection using multimodal AI.
* **Verification Engine:** Direct deep-links to **Iconik** MAM for frame-accurate proof of performance.
* **Native Dashboard:** A custom "Tokyo Night" themed UI for stakeholders to visualize data without leaving the media environment.
* **One-Click Reporting:** Export capabilities for PDF Sponsor Reports and CSV data for financial teams.

---

## 🛠️ Technology Stack

| Component | Technology |
| :--- | :--- |
| **Orchestration** | [qibb](https://www.qibb.com/) (Enterprise Node-RED) |
| **Video AI** | [Twelve Labs](https://www.twelvelabs.io/) (Marengo Engine) |
| **Media Management** | [Iconik](https://www.iconik.io/) |
| **Frontend** | Vanilla JS, Chart.js, HTML5/CSS3 |
| **Data Storage** | qibb Global Context (High-speed native storage) |

---

## 📂 Repository Contents

* `index.html`: The interactive mock dashboard (The "Live Demo").
* `/screenshots`: Evidence of the live production environment and backend orchestration.
* `README.md`: System architecture and project documentation.

---

## 🔗 Live Demo URL

[View the Interactive Dashboard Preview here](https://DaveEuson.github.io/tl2026Dash/)
