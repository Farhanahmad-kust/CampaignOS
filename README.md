# 🚀 CampaignOS | AI Sales Command Center

![Version](https://img.shields.io/badge/version-1.0.0-blue) ![Status](https://img.shields.io/badge/status-active-success) ![License](https://img.shields.io/badge/license-MIT-purple)

**CampaignOS** is a fully automated, end-to-end sales orchestration platform. It replaces manual lead management with an AI-powered ecosystem that ingests data, cleans records, and launches personalized **Email** and **Voice** campaigns autonomously.

> **Problem Solved:** Sales teams spend 80% of their time on data entry and manual dialing. CampaignOS automates the "robot work" so humans can focus on closing deals.

---

## 📺 Project Demo

[![Watch the Demo]https://youtu.be/oquJ2EhGAiw
*(Click above to watch the 4-minute walkthrough)*

---

## ✨ Key Features

### 1. 📂 Intelligent Data Ingestion
* **Drag-and-Drop Upload:** Instantly process raw CSV lead files.
* **Auto-Analysis:** Backend workflows analyze data quality in real-time.
* **Stats Dashboard:** Immediate visualization of actionable vs. incomplete leads.

### 2. 🧹 Data Cleaning Workspace
* **Interactive Grid:** Edit missing fields (Phone, Email, Job Title) directly in the UI.
* **Instant Sync:** Updates are pushed to the Supabase database via webhooks immediately upon saving.

### 3. ✉️ AI Email Agent
* **Personalization Engine:** Uses **GPT-4o** to generate unique, context-aware emails for each lead.
* **Bulk Orchestrator:** Send single emails or trigger batch campaigns (e.g., 50 leads at once).
* **Live Tracking:** Dashboard updates instantly when emails are sent.

### 4. 📞 Neural Voice Agent
* **Vapi Integration:** Triggers ultra-realistic AI voice calls that handle objections in real-time.
* **Smart Queuing:** Bulk dialer manages call pacing to prevent spam flagging.
* **Instant Intelligence:** Call transcripts and AI summaries sync back to the dashboard immediately after the call ends.

---

## 🛠️ Technical Architecture

This project utilizes a **Serverless / Low-Code** architecture for maximum scalability and low maintenance.

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Frontend** | HTML5, CSS3, JS | Custom dashboard with **Chart.js** for real-time analytics. |
| **Backend Logic** | **n8n** | 6 complex workflows handling routing, logic, and API calls. |
| **Database** | **Supabase** | PostgreSQL database for storing leads and campaign state. |
| **Voice AI** | **Vapi.ai** | Orchestrates the conversational AI for phone calls. |
| **LLM** | **OpenAI GPT-4o** | Generates email copy and conversation logic. |
| **Telephony** | **Twilio** | SIP trunking for outbound dialing. |

### 🔄 The 6 Core Workflows
1.  **Ingestion:** CSV parsing & DB insertion.
2.  **Update Loop:** Handling user edits from the dashboard.
3.  **Get Leads:** Fetching filtered lists (Email vs. Phone) for the UI.
4.  **Email Dispatch:** GPT-4 generation & Gmail/SMTP sending.
5.  **Voice Dispatch:** Vapi trigger & Bulk batching.
6.  **Result Sync:** Webhook listener for call transcripts/summaries.

---

## 👥 The Team

This project was a collaborative effort combining technical implementation with industry insights.

* **Farhan Ahmad (Lead Developer):**
    * Role: Full Stack Development, Architecture, & Deployment.
    * Contribution: Built all 6 n8n workflows, designed the Supabase schema, coded the frontend dashboard, and integrated the AI agents (Vapi/OpenAI).
* **Nahida Ali:**
    * Role: Freelance Associate.
    * Contribution: Project strategy and use-case definition.
* **Engr. Rizwan:**
    * Role: Freelance Associate.
    * Contribution: Sales workflow insights.

---

## 💰 Cost Analysis

We have prepared a detailed breakdown of the Operational Costs (OpEx) and Development Value (CapEx) for this system.

📄 **[View Full Cost Estimation Document](./COST_ESTIMATION.md)**

**Quick Summary:**
* **Fixed Monthly Cost:** ~$31.15 (n8n + Twilio)
* **Voice Cost:** ~$0.12 per minute (90% cheaper than human SDRs)
* **Email Cost:** ~$0.0002 per email

---

## 🚀 Getting Started

### Prerequisites
* [n8n](https://n8n.io/) (Self-hosted or Cloud)
* [Supabase](https://supabase.com/) Account
* [Vapi.ai](https://vapi.ai/) Account
* [OpenAI](https://openai.com/) API Key

### Installation
1.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/yourusername/CampaignOS.git](https://github.com/yourusername/CampaignOS.git)
    ```
2.  **Import Workflows:**
    * Import the `.json` workflow files located in the `/workflows` folder into your n8n instance.
3.  **Setup Database:**
    * Run the SQL script in `/database/schema.sql` in your Supabase SQL editor.
4.  **Configure Environment:**
    * Update the `index.html` file to point to your specific n8n Webhook URLs.
5.  **Run:**
    * Open `index.html` in any browser. No build step required!

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
