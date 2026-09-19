# Hierarchical Multi-Agent AI Workflow in n8n

A modular, multi-agent automation pipeline built in **n8n** that demonstrates the **Parent-Child workflow pattern**, agentic memory retention, multi-LLM model integration (OpenAI & Google Gemini), and dynamic external tool execution.

---

## 🌟 Key Features

- **Parent-Child Workflow Architecture:** Implements a decoupled design where a primary orchestrator delegates specialized execution steps to dedicated sub-workflows.
- **Multi-LLM Integration:** Combines **OpenAI Chat Model** (for conversation orchestration) and **Google Gemini Chat Model** (for sub-task data synthesis and formatting).
- **Conversational Memory:** Employs **Simple Memory** within the parent agent to retain context across multi-turn user sessions.
- **Real-Time Data Retrieval:** Integrates with the **OpenWeatherMap API** to extract live atmospheric metrics (temperature, humidity, wind speed, conditions).
- **Modular Tool Calling:** Encapsulates sub-workflows into callable n8n custom tools.

---

## 🏗️ System Architecture
<img width="506" height="669" alt="image" src="https://github.com/user-attachments/assets/a6c10f0c-e694-4fa6-bb56-34d7c69006e3" />

<img width="1024" height="481" alt="image" src="https://github.com/user-attachments/assets/7956ac8c-458e-4fa2-b5a1-dd6a505d6902" />

<img width="1690" height="852" alt="image" src="https://github.com/user-attachments/assets/125fefc0-0192-4365-afbe-a38453805f7b" />

---

## 🛠️ Tech Stack & Nodes Used

- **Automation Engine:** [n8n](https://n8n.io/)
- **AI Models:** OpenAI GPT Models (`@n8n/n8n-nodes-langchain.lmChatOpenAi`), Google Gemini (`@n8n/n8n-nodes-langchain.lmChatGoogleGemini`)
- **Memory Management:** Simple Memory (`@n8n/n8n-nodes-langchain.memorySimple`)
- **Integrations:** OpenWeatherMap API

---

## ⚙️ How It Works

### 1. Parent Workflow (`Process Weather Data`)
- Listens for incoming chat messages via the **Chat Trigger** node.
- Passes the user prompt to the primary **AI Agent**.
- Evaluates if external weather data is required. If needed, invokes the **Weather Tool** sub-workflow.
- Integrates the returned sub-workflow data into the final user prompt response.

### 2. Child Workflow (`Child Weather API`)
- Triggered dynamically by the parent workflow (**When Executed by Another Workflow**).
- Fetches real-time weather metrics from **OpenWeatherMap** based on target coordinates or location parameters.
- Runs the raw API output through a second **AI Agent** equipped with **Google Gemini** to produce a concise, structured response.
- Sends the structured output back to the parent workflow tool caller.

---

## 🚀 Setup & Installation

### Prerequisites
- An active instance of **n8n** (Self-hosted or n8n Cloud).
- API Keys for:
  - **OpenAI API**
  - **Google Gemini API**
  - **OpenWeatherMap API**

