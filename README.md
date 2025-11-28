

![AI Agent Node](images/n8n.JPG)

# Automated AI Email Assistant Workflow (n8n)

This n8n workflow automates sending professional emails. Provide a **sender name** and a **message**, and the system will:

- Generate a professional **email subject** and **body** using AI.
- Look up the recipient's email from **Google Sheets**.
- Send the email directly via **Gmail** automatically.

---

## Features

- Accepts **name** and **message** as input.
- AI generates polished, professional emails.
- Automatic recipient lookup from Google Sheets.
- Fully automated sending via Gmail.

---

## Workflow Components

1. **Chat Trigger / Webhook** – Receives `name` and `message`.  
2. **AI Agent (LangChain / OpenAI)** – Generates `Subject` and `Message`.  
3. **Google Sheets Node** – Finds recipient email based on name.  
4. **Gmail Node** – Sends email automatically.  
5. **Optional Memory Node** – Maintains short-term AI context.

---

## Setup

1. Configure **OpenAI API** in n8n.  
2. Configure **Gmail OAuth2** credentials.  
3. Prepare **Google Sheets** with `Name` and `Email` columns.  
4. Import the workflow JSON and verify node connections.  
5. Gmail node expressions:
```json
"to": "={{ $node['Google Sheets'].json['Email'] }}",
"subject": "={{ $json['Subject'] }}",
"message": "={{ $json['Message'] }}"
