# 📧 AI Email Auto-Responder

This project implements an AI-powered email assistant that automatically reads, classifies, and responds to incoming emails for **Dr. Mio**, a university professor.

It uses an LLM (via Ollama) together with function calling (tools) to generate **structured, context-aware replies**.

---

## 🚀 Features

- 📥 Reads incoming emails
- 🧠 Classifies intent (e.g. homework, exam inquiry, meeting)
- 🛠 Uses predefined tools to generate responses
- ✉️ Outputs clean email responses (subject + content)
- 🔁 Iterative tool-calling loop for reliable execution

---

## 🧩 Supported Email Categories

The system can currently handle:

| Category | Description |
|--------|------------|
| Homework Submission | Confirms receipt of homework |
| Exam Date Inquiry | Responds to exam schedule questions |
| Exam Review Request | Handles requests to review exam results |
| Meeting Request | Schedules meetings with colleagues |
| Fallback | Generic auto-reply if unclear |

---

## ⚙️ How It Works

### 1. Input
An incoming email is provided as a message:

```python
{
  "role": "user",
  "content": "Dear Dr. Mio, I would like to ask about..."
}
