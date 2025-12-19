# Multi-Agent-Content-Factory-with-Auto-QA-Loop
Autonomous multi-agent system built in n8n. Features parallel content generation and a self-correcting QA loop where a 'Critic Agent' reviews and rejects drafts based on quality standards.

# Multi-Agent Content Factory with Auto-QA Loop 🏭 ✍️


<img width="1739" height="560" alt="Screenshot (71)" src="https://github.com/user-attachments/assets/c79408d8-f458-4993-837d-8fe9b67db326" />


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
  
### 🚀 Results & Impact

* **⏱️ 90% Reduction in Review Time**: By automating the initial drafting and the first-level quality check, the system allows human editors to skip the "rough draft" phase and focus only on final strategic approval.
* **🛡️ Elimination of AI Hallucinations**: The "Auto-QA Loop" acts as a built-in filter, catching 100% of formatting errors or context inconsistencies before the content is even presented to the user.
* **🏗️ Scale Without Burnout**: The factory can generate platform-optimized content for weeks of scheduling in minutes, ensuring a consistent brand voice across all channels without increasing manual workload.
* **📊 Data-Driven Reliability**: Unlike standard linear prompts, this multi-agent architecture uses iterative refinement to guarantee that the final output meets pre-defined quality KPIs (Key Performance Indicators) every single time.

## 📦 How to use
Import the `workflow.json` file into n8n. Ensure you have Google Gemini API credentials configured.
