# 🤖 AI-Powered Content Automation Engine (n8n + Gemini AI)

A robust, production-ready automation workflow that manages end-to-end social media content scheduling. It fetches data from **Google Sheets**, generates context-aware captions using **Google Gemini 1.5 Flash**, and distributes posts to **Telegram** and **Discord** based on pre-defined schedules.

---

## 🌟 Key Features
* **Intelligent Filtering:** Automatically identifies rows with `Pending` status to avoid duplicate postings.
* **AI Caption Generation:** Uses **Gemini AI** to create engaging, platform-specific captions for every post.
* **Multi-Channel Routing:** Implements **Switch Logic** to direct content to Telegram, Discord, or both simultaneously.
* **Smart Scheduling:** A custom **Date/Time Logic** ensures posts are only published when the scheduled time is reached (Time-zone aware: `Asia/Kolkata`).
* **Fail-Safe Error Handling:** Integrated **Error Branches** that trigger an automated Telegram alert if an API fails (e.g., invalid image URLs or character limits), ensuring the workflow doesn't stop.

---

## 🛠️ Technical Stack
* **Automation:** n8n (Workflow Orchestration)
* **AI:** Google Gemini 1.5 Flash API
* **Database:** Google Sheets
* **Integrations:** Telegram Bot API, Discord Webhooks
* **Logic:** JSON Data Mapping, Ternary Operators, Time-zone normalization.

---

## 📋 Database Schema (Google Sheets)
The workflow expects the following columns in the source Google Sheet:

| ID | Content | Media Url | Platform | Post-time | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Benefit of AI | https://image.url | Both | 2026-04-03 10:00 | Pending |

---

## 🚀 How to Setup
1. **Clone the Repo:** Download the `workflow.json` file.
2. **Import to n8n:** Open n8n, click on the menu, and select **Import from File**.
3. **Configure Credentials:**
   * Connect your **Google Sheets** account.
   * Input your **Gemini API Key**.
   * Set up your **Telegram Bot Token** and **Discord Webhook URL**.
4. **Activate:** Set the `Schedule Trigger` to your desired interval (e.g., every 1 minute) and flip the workflow to **Active**.

---

## 🧠 Major Learnings & Challenges
* **Data Validation:** Handled "Empty String to DateTime" conversion errors by implementing `is not empty` checks and default value logic.
* **API Constraints:** Managed Telegram's 1024-character caption limit by optimizing AI prompts to keep captions concise.
* **State Management:** Built a feedback loop that updates the Google Sheet status to `Published` only after a confirmed successful API response.

---

## 📂 Project Structure
* `/workflow.json`: The full n8n workflow export.
* `/README.md`: Documentation.
* `/assets/`: Screenshots of the workflow and successful posts.

---

## ⚠️ Security Note
**Important:** Do not share your API keys or Bot Tokens publicly. Ensure that the `workflow.json` file you upload has all sensitive credentials removed or replaced with placeholders.

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/yourusername/repo-name/issues).
