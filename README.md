# Multi-Agent-Content-Factory-with-Auto-QA-Loop
Autonomous multi-agent system built in n8n. Features parallel content generation and a self-correcting QA loop where a 'Critic Agent' reviews and rejects drafts based on quality standards.

# Multi-Agent Content Factory with Auto-QA Loop 🏭 ✍️

<img width="1749" height="587" alt="Screenshot (70)" src="https://github.com/user-attachments/assets/93b1e930-2b3b-4974-8d1b-3cc7557eba4a" />


## 🧠 Overview
This isn't just a content generator. It is an **Agentic System** designed to mimic a real-world editorial team. It orchestrates multiple AI Agents to plan, draft, and —crucially— **review and critique** social media content based on strict brand guidelines.

## 🔄 The Self-Correction Loop (Key Feature)
Unlike standard automations that output whatever the LLM generates, this workflow implements a **Quality Assurance Loop**:
1.  **Drafting:** Three parallel agents generate content for different funnel stages (Engagement, Hype, Pre-Launch).
2.  **The Critic Agent:** A specialized "Senior Editor" agent evaluates the drafts giving a score (0-10) based on brand tone, coherence, and CTA effectiveness.
3.  **Feedback Loop:** If the score is below threshold (< 7/10), the system **rejects the draft**, sends specific feedback back to the drafting agents, and forces a rewrite.
4.  **Approval:** Only high-quality content passes through to the final document.

## 🛠️ Tech Stack
* **Orchestration:** n8n
* **AI Models:** Google Gemini (via LangChain nodes)
* **Logic:** Javascript (Custom parsing for robust JSON handling)
* **Integration:** Google Drive, Google Docs

## ⚙️ Workflow Logic
1.  **Trigger:** Detects a new "Brand Brief" uploaded to Google Drive.
2.  **Analysis:** Parses the brief to extract Brand Tone and Phase Goals.
3.  **Parallel Execution:** Activates 3 distinct AI Agents to draft content simultaneously.
4.  **Evaluation:** The Critic Agent reviews the combined output.
    * *Pass:* Generates a formatted Google Doc report.
    * *Fail:* Triggers the **Correction Loop** (Max 3 retries).

## 📦 How to use
Import the `workflow.json` file into n8n. Ensure you have Google Gemini API credentials configured.
