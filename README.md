# ⚓ The Brand Anchor: AI-Driven Engagement Suite

**The Brand Anchor** is a high-impact automation ecosystem designed to build authority and maintain a daily connection with your audience. By combining the "thinking" power of **Gemini 1.5 Flash** with the "orchestration" of **n8n**, this system delivers hyper-personalized daily insights while tracking exactly where your growth is coming from via Source Tracking.

It transforms a passive spreadsheet into a proactive brand ambassador that handles everything from first impressions to legal compliance and performance analytics.

---

## 📋 Overview

The Brand Anchor eliminates generic mass-mailing and replaces it with high-frequency, high-value personal connections. It serves as a persistent, positive brand presence that builds trust and authority on autopilot.

* **Hyper-Personalization**: Uses AI to generate unique content for every single subscriber based on their name and niche.
* **Omnichannel Logic**: Centralizes data in Google Sheets while distributing via branded HTML emails.
* **Compliance First**: Includes a dedicated "Listener" loop for instant, one-click unsubscribes.
* **Growth Intelligence**: Automatically tracks and reports on sign-up sources (e.g., LinkedIn, Instagram).

---

## 🚀 Workflow Architecture

The ecosystem consists of four specialized "Loops" that share a single **Google Sheet** database:

1. **The Welcome Loop (Instant)**
   * **Trigger**: A new row is added to the Google Sheet.
   * **Action**: Greets the user instantly, acknowledges their specific sign-up source, and sets expectations for daily anchors.

2. **The Delivery Loop (Daily 9 AM)**
   * **Trigger**: A time-based schedule "wakes" the workflow.
   * **Intelligence**: Reads "Pending" subscribers and passes data to Gemini AI.
   * **Dispatch**: Sends a branded HTML email and updates status to "Sent".

3. **The Compliance Loop (Instant)**
   * **Trigger**: A user clicks "Unsubscribe" in an email footer.
   * **Action**: A Webhook instantly updates the database to "Unsubscribed".

4. **The Analytics Loop (Weekly Friday 5 PM)**
   * **Trigger**: A Friday afternoon schedule.
   * **Action**: Aggregates "Sent" data and delivers a performance summary to the administrator.

---

## 🛠️ Tech Stack

* **Automation**: [n8n](https://n8n.io/) (Self-hosted or Cloud)
* **LLM**: [Google Gemini 1.5 Flash](https://aistudio.google.com/)
* **Database**: [Google Sheets](https://www.google.com/sheets/about/)
* **Communication**: SMTP / Email Node

---

## ⚙️ Installation & Setup

### Phase 1: The Database
1. Create a Google Sheet named `The Brand Anchor Database`.
2. Add these headers to Row 1: `Email`, `First Name`, `Status`, `Source`, and `Last Sent`.

### Phase 2: The Compliance Loop
1. Import the **Unsubscribe Webhook** JSON into a new n8n workflow.
2. Copy the **Production Webhook URL** from the Webhook node.
3. Toggle the workflow to **Active**.

### Phase 3: The Welcome Loop
1. Import the **Welcome Greeter** JSON into a new n8n workflow.
2. Point the trigger to your Google Sheet and set the event to `Row Added`.
3. Toggle the workflow to **Active**.

### Phase 4: The Delivery Loop
1. Import the **Daily Delivery** JSON into a new n8n workflow.
2. Configure the Google Sheets node: `Resource: Row` | `Operation: Get Many` | `Filter: Status = Pending`.
3. Paste your HTML email template and update the unsubscribe link with the URL from Phase 2.
4. Toggle the workflow to **Active**.

### Phase 5: The Analytics Loop
1. Import the **Weekly Performance Report** JSON into a new n8n workflow.
2. Point the data source to your database and set the recipient email.
3. Toggle the workflow to **Active**.

---


## 📬 Contact
👩‍💻 Created by: **Charlote Araneta**

🔗 LinkedIn: https://www.linkedin.com/in/charlotearaneta

🌐 Portfolio: https://charlotearaneta.github.io

---
