# Smart Meeting Assistant Agent (n8n) - README

A workflow to automate meeting scheduling, agenda generation, and email notifications using Telegram, Google Calendar, and Groq LLM.

---

## 🌟 Overview
- **Trigger**: Receive meeting requests via Telegram (text as promt and PDF attachments).
- **Processing**: Extract PDF content, generate structured agendas, and schedule events in Google Calendar.
- **Output**: Send automated emails with meeting details and AI-summarized transcripts.

---

## 🛠 Prerequisites
1. **n8n Setup**: Self-hosted instance.
2. **Accounts**:
   - Telegram Bot API token ([BotFather](https://core.telegram.org/bots#6-botfather))
   - Google Workspace account (for Gmail & Calendar)
   - [Groq API Key](https://console.groq.com/)
3. **n8n Credentials**:
   - `BOT` (Telegram)
   - `Gmail account`
   - `Google Calendar account`
   - `Groq account 2`

---

## ⚙ Installation
1. **Import Workflow**:
   - In n8n, go to *Workflows* → *Import from JSON* → Upload `Lab_work_6__Smart_Meeting_Assistant_Agent__n8n_.json`.

2. **Configure Credentials**:
   - Update all nodes with red "credentials" badges:
     - **Telegram**: Add your bot token.
     - **Google Services**: Authenticate via OAuth2.
     - **Groq**: Add API key to `Groq account 2`.

3. **Set Webhooks**:
   - For the `Telegram Trigger` node, use `/rest/webhook-test/your-webhook-id` as your Telegram bot's webhook URL.

---

## 🔄 Workflow Steps
1. **Trigger**: 
   - A Telegram message (text or PDF) starts the workflow.
2. **PDF Extraction**: 
   - Extracts text from PDF attachments.
3. **Prompt Combination**: 
   - Merges user input with PDF content for LLM processing.
4. **Agenda Generation**: 
   - Uses Groq LLM to create a structured agenda.
5. **Calendar Event**: 
   - Creates a Google Calendar event with parsed details.
6. **Transcript Generation**: 
   - Simulates meeting notes with timestamps and participants.
7. **Summarization**: 
   - Condenses transcripts using Groq LLM.
8. **Email Notifications**: 
   - Sends pre-meeting invites and post-meeting summaries via Gmail.

---

## ⚠️ Configuration Notes
- **Time Zones**: Update timezone in `Extract Meeting Fields` code node (currently `Africa/Cairo`).
- **Email Templates**: Modify message templates in `Gmail1` and `Gmail2` nodes.
- **PDF Parsing**: Adjust regex patterns in `Combine Prompt & PDF Text` if PDF format changes.

---

