# n8n-job-alert-automation
Automated daily Wellfound job alerts to Gmail using n8n and AI
# 🎯 Automated Daily Job Alert Workflow (n8n + AI)

An automated workflow built with **n8n** that fetches job listings from **Wellfound** via RSS feeds, processes and formats the key details using **AI**, and sends structured daily email alerts directly to **Gmail**.

---

## 📌 Features

- **Automated Daily Trigger**: Runs on a set schedule without manual intervention.
- **RSS Parsing**: Extracts real-time job listings directly from Wellfound's RSS feed.
- **AI-Powered Summarization**: Uses an LLM to extract key details (Role, Company, Work Mode, Tech Stack, and Apply Links) and format them into a clean template.
- **Filtering Logic**: Evaluates processed data using conditional checks to ensure quality emails.
- **Direct Email Delivery**: Dispatches organized summary emails via Gmail integration.

---

## 🛠️ Architecture & Workflow
[ Schedule Trigger ] ──► [ RSS Read ] ──► [ Limit ] ──► [ AI Model ] ──► [ If Condition ] ──► [ Gmail Node ]


### Node Breakdown:
1. **Schedule Trigger**: Triggers the workflow daily on a predefined schedule.
2. **RSS Read**: Pulls raw feed data from Wellfound.
3. **Limit**: Restricts the maximum number of job listings fetched per execution.
4. **Message a Model (AI)**: Summarizes raw listings into clean fields:
   - 📌 **Role**
   - 🏢 **Company / Source**
   - 📍 **Work Mode / Location**
   - 💰 **Stipend / Salary**
   - 🛠️ **Key Tech Stack**
   - 📝 **Brief Summary**
   - 🔗 **Link to Apply**
5. **If Condition**: Validates that valid job output exists before attempting to send.
6. **Send a Message (Gmail)**: Emails the structured job alert directly to your inbox.

---

## 🚀 Setup & Installation

### Prerequisites
- An active [n8n](https://n8n.io/) instance (Cloud or Self-Hosted).
- A Gmail account with OAuth2 credentials configured in n8n.
- An API key for your preferred AI provider (e.g., OpenAI, Anthropic, or Google Gemini).

### Steps
1. **Import Workflow**:
   - Copy the workflow JSON file from this repository (`workflow.json`).
   - Open n8n, navigate to **Workflows**, click **Import from File** (or paste the JSON).
2. **Configure Credentials**:
   - Link your **Gmail** account in the Gmail node.
   - Attach your API key credential to the **AI Model** node.
3. **Adjust Settings**:
   - Update the **RSS Read** URL with your custom Wellfound RSS feed search URL.
   - Adjust the **Schedule Trigger** time to your preferred daily delivery slot.
4. **Activate**:
   - Toggle the workflow status to **Active** (Published).

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
