# 🚀 Marketing Agency: Client Retainer & Payment Automation

An automated workflow built in **n8n** that manages the end-to-end billing lifecycle for marketing agency retainers. It monitors a Google Sheet database, generates PayPal invoices, sends professional Gmail notifications, and updates payment tracking in real-time.

---

## 📋 Overview
Managing monthly retainers manually is prone to error and late payments. This automation ensures:
- **Proactive Billing:** Invoices are generated exactly 7 days before the due date.
- **Data Integrity:** Syncs PayPal Invoice IDs back to Google Sheets for easy tracking.
- **Professionalism:** Sends branded HTML emails to clients with direct payment links.
- **Zero Duplicates:** Built-in logic to prevent sending multiple invoices for the same period.

---

## 🚀 Workflow Architecture
1.  **Trigger:** Daily check at 9:00 AM.
2.  **Fetch:** Pulls all client data from the "Retainers" Google Sheet.
3.  **Filter:** Checks if `Due Date` is in 7 days AND `Invoice Status` is "Pending".
4.  **Action:** Generates a PayPal Invoice and extracts the hosted payment URL.
5.  **Notify:** Sends a customized Gmail to the client with the payment button.
6.  **Update:** Writes the PayPal ID and Link back to the Sheet and marks it as "Sent".

## 🛠️ Tech Stack
- **Automation:** [n8n.io]
- **Database:** Google Sheets
- **Payments:** PayPal REST API
- **Communication:** Gmail API
- **Logic:** JavaScript / Luxon

---

## ⚙️ Installation & Setup

### 1. Google Sheets Preparation
Create a sheet named `Retainers` with the following headers:
`Client Name`, `Email`, `Amount`, `Currency`, `Due Date`, `Invoice Status`, `PayPal ID`, `PayPal Link`, `Sent Date`.

### 2. PayPal Developer Setup
- Go to the [PayPal Developer Portal](https://developer.paypal.com/).
- Create an App to get your **Client ID** and **Secret**.
- *Note:* Use Sandbox mode first for testing.

### 3. n8n Configuration
1.  **Import Workflow:** Copy the JSON from this repository and import it into your n8n instance.
2.  **Credentials:** - Connect your **Google Cloud Console** (OAuth2) for Sheets and Gmail.
    - Connect your **PayPal** account using the Client ID and Secret.
3.  **Environment Variables:** Update the `Sheet ID` in the Google Sheets nodes to match your specific spreadsheet URL.

### 4. Deployment
- Set the workflow to **Active**.
- Ensure your n8n instance is running (local, Docker, or Cloud).

---


## 📬 Contact
👩‍💻 Created by: **Charlote Araneta**

🔗 LinkedIn: https://www.linkedin.com/in/charlotearaneta

🌐 Portfolio: https://charlotearaneta.github.io

---
