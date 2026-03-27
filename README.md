# 📧 AI Email Auto-Responder

This project implements an AI-powered email assistant that automatically reads, classifies, and responds to incoming emails for Dr. Mio, a university professor.

It uses an LLM (via Ollama) together with function calling (tools) to generate structured, context-aware replies.

---

## 🚀 Features

- 📥 Reads incoming emails  
- 🧠 Classifies intent (e.g. homework, exam inquiry, meeting)  
- 🛠 Uses predefined tools to generate responses  
- ✉️ Outputs clean email responses (subject + content)  
- 🔁 Iterative tool-calling loop for reliable execution  

---

## 🧩 Supported Email Categories

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
```

---

### 2. AI Processing

The LLM:
- Reads the email  
- Determines intent  
- Selects the correct tool  
- Calls the tool with the sender’s name  

---

### 3. Tool Execution

Each tool is a Python function that generates a formatted email response:

```python
def exam_review_request(student_name: str):
    return f"..."
```

---

### 4. Output

Final structured response:

```json
{
  "Email": {
    "subject": "Re: Exam Review Request",
    "content": "Dear Alien, ..."
  }
}
```

---

## 🛠️ Available Tools

### 📚 homework_submission(student_name)
Confirms homework submission.

### 📅 ask_exam_date(student_name)
Responds to exam date inquiries.

### 📝 exam_review_request(student_name)
Handles exam review requests.

### 🤝 colleague_meeting(colleague_name)
Schedules meetings.

### ⏳ be_back_soon(sender_name)
Fallback auto-reply when intent is unclear.

---

## 🔁 Tool Execution Loop

```python
while True:
  response = chat(...)

  if response.message.tool_calls:
    # Execute tool
  else:
    break
```

---

## 📦 Requirements

- Python 3.10+  
- ollama Python package  
- Local or remote LLM model (gpt-oss in this case)  

Install dependencies:

```bash
pip install ollama
```

---

## ▶️ Running the Script

```bash
python main.py
```

---

## 🧪 Example Input

```text
Dear Dr. Mio,
I would like to kindly ask for reviewing of my exam result.
```

---

## ✅ Example Output

```json
{
  "Email": {
    "subject": "Re: Exam Review Request",
    "content": "Dear Alien, Thank you for your request..."
  }
}
```

---

## ⚠️ Design Rules

- ❌ The model must NOT write responses directly  
- ✅ All responses must come from tools  
- 🎯 Closest matching tool must always be selected  
- 🔒 Ensures consistent tone and structure  

---

## 🔮 Future Improvements

- Add more email categories  
- Integrate with Gmail / Outlook APIs  
- Add database logging  
- Multi-language support  
- Fine-tuned classification  

---

## 🧠 Key Concept

This project demonstrates LLM + tool orchestration:

- The model decides what to do  
- Functions define how it's done  

---

## 📄 License
Apache 2.0 
