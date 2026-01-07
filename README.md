# 📧 AI-Powered Smart Email Assistant (n8n + Gemini)

![License](https://img.shields.io/github/license/Sumonmialab/ai-smart-email-responder-n8n)
![n8n](https://img.shields.io/badge/Workflow-n8n-ff6e5c?style=flat&logo=n8n)
![Gemini](https://img.shields.io/badge/AI-Google%20Gemini-4285F4?style=flat&logo=google)

This project is an advanced automation workflow built with **n8n** that uses **Google Gemini AI** to manage incoming emails intelligently. It analyzes email context, categorizes priority, and automatically generates tone-appropriate draft replies directly in Gmail.

## 🚀 Key Features
* **Smart Categorization:** Automatically tags emails as `Urgent`, `Newsletter`, `Spam`, or `General`.
* **Dynamic Tone Adaptation:**
    * *Corporate/Professional emails* → Generates formal, detailed responses with "Sincerely".
    * *Casual/Informal emails* → Generates friendly, concise responses with "Best regards".
* **Zero Hallucination Policy:** The System Prompt is engineered to prevent the AI from inventing facts.
* **Robust JSON Parsing:** Includes a dedicated Javascript/Regex layer to clean AI outputs.
* **Automated Drafting:** Saves the generated reply as a **Draft** in Gmail (allows human review before sending).

## 📸 Workflow Preview

![Workflow Diagram](https://raw.githubusercontent.com/Sumonmialab/ai-smart-email-responder-n8n/refs/heads/main/Screenshot%202026-01-07%20203659.png)

## 🛠️ Workflow Architecture
The pipeline consists of the following nodes:
1.  **Gmail Trigger:** Polls for new emails every minute.
2.  **AI Agent (LangChain):** Connects to **Google Gemini Chat Model** with memory context.
3.  **Data Cleaning:** Uses Regex to strip markdown code blocks from the AI response.
4.  **Gmail Draft:** Creates the final email draft using the cleaned text.

## ⚙️ How to Use
1.  **Installation:** Download the `.json` file from this repository and import it into n8n.
2.  **Credentials:** Set up your Google (Gmail) and Gemini API credentials in n8n.
3.  **Activate:** Turn on the workflow to start processing emails.

## 🧠 AI Prompt Logic (Snippet)
The core intelligence relies on a strict prompt engineering strategy:
```json
"INSTRUCTIONS": "NO HALLUCINATIONS. Do not invent names/dates. OUTPUT FORMAT: Pure JSON only."
