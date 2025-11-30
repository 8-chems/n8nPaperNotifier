# Automatic Research Update (n8n Project)

This project is an n8n workflow that collects user interests, derives search keywords using an LLM, stores subscriber data in Google Sheets, and periodically sends research paper updates via Semantic Scholar, Telegram, and Gmail.

## Architecture

![Automatic Research Update workflow](n8n.png)

The diagram (`n8n.PNG`) should illustrate the three main parts:

- **Form flow**:  
  `On form submission → Groq Chat Model + Basic LLM Chain → Search files and folders / If / Create spreadsheet → Append or update row in sheet → Form (completion with Telegram link)`

- **Telegram onboarding flow**:  
  `Telegram Trigger → Edit Fields → Get row(s) in sheet1 → If1 → (Update row in sheet | Respond to Webhook redirect to form)`

- **Scheduled research updates flow**:  
  `Schedule Trigger → Get row(s) in sheet → HTTP Request (Semantic Scholar) → Code in JavaScript (build papers_text) → (Send a text message via Telegram, Send a message via Gmail)`
