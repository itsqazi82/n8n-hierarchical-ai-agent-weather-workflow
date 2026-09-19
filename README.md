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
