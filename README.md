
# 🔬 ResearchMind — Multi-Agent AI Research System

ResearchMind is a **multi-agent AI research system** that automates the process of researching a topic, collecting information, extracting useful content, generating a research report, and reviewing the final output.

The application is built with **Streamlit** and uses a LangChain-based multi-agent pipeline.

---

## ✨ Features

- 🔎 **Search Agent** — finds recent and relevant information about the research topic.
- 📄 **Reader Agent** — selects a relevant source and extracts deeper content.
- ✍️ **Writer Chain** — combines the collected information and generates a structured research report.
- 🧐 **Critic Chain** — reviews the generated report and provides feedback.
- 🎨 **Modern Streamlit UI** — dark navy/violet interface with pipeline status cards.
- 📥 **Report Download** — download the generated research report as a Markdown file.
- ⚡ **Multi-Agent Workflow** — different components handle different stages of the research process.

---

## 🏗️ System Architecture

```text
                    ┌───────────────────┐
                    │   Research Topic  │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │    Search Agent   │
                    │   Web Research    │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │    Reader Agent   │
                    │ Scrape & Extract  │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │    Writer Chain   │
                    │ Generate Report   │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │    Critic Chain   │
                    │ Review & Feedback │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │  Final Research  │
                    │      Report      │
                    └───────────────────┘
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Streamlit | Web interface |
| LangChain | LLM and agent orchestration |
| LangGraph | Agent workflow/orchestration |
| Mistral AI | Large Language Model |
| Tavily | Web search |
| BeautifulSoup | Web scraping and content extraction |
| Requests | HTTP requests |
| python-dotenv | Environment variable management |
| Rich | Terminal output/formatting |

---

## 📁 Project Structure

```text
multiagentsystem/
│
├── app.py                  # Streamlit application
├── agents.py               # Agent and chain definitions
├── tools.py                # Search/scraping tools
├── .env                    # API keys (do not commit)
├── .gitignore
├── pyproject.toml
├── uv.lock
└── README.md
```

> Rename `app.py` in this structure if your Streamlit file has a different filename.

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/multiagentsystem.git
cd multiagentsystem
```

### 2. Create the environment

If you are using **uv**:

```bash
uv init
```

Then install the required dependencies:

```bash
uv add streamlit langchain langchain-core langchain-community langchain-mistralai langgraph tavily-python beautifulsoup4 requests python-dotenv rich
```

Alternatively, if you have a `requirements.txt` file:

```bash
pip install -r requirements.txt
```

---

## 🔑 Environment Variables

Create a `.env` file in the project root:

```env
MISTRAL_API_KEY=your_mistral_api_key
TAVILY_API_KEY=your_tavily_api_key
```

### ⚠️ Important

Never upload your `.env` file to GitHub.

Add this to `.gitignore`:

```gitignore
.env
.venv/
__pycache__/
*.pyc
```

---

## 🤖 Mistral Model

The project uses **Mistral AI** as the language model provider.

Example:

```python
from langchain_mistralai import ChatMistralAI

llm = ChatMistralAI(
    model="open-mistral-7b",
    temperature=0
)
```

If the model name is changed in your `agents.py`, update the README accordingly.

---

## 🔎 Research Workflow

### Step 1 — Search Agent

The user enters a research topic such as:

```text
Quantum computing breakthroughs in 2025
```

The Search Agent searches for recent and detailed information.

### Step 2 — Reader Agent

The Reader Agent receives the search results, selects a relevant URL, and extracts deeper information from the source.

### Step 3 — Writer Chain

The Writer Chain receives:

```text
Search Results
+
Detailed Scraped Content
```

and generates the final research report.

### Step 4 — Critic Chain

The Critic Chain reviews the generated report and produces feedback about the report.

---

## 🖥️ Running the Application

Run the Streamlit application with:

```bash
streamlit run app.py
```

Or, if your main file has another name:

```bash
streamlit run <your_file_name>.py
```

The application will open in your browser.

---

## 💡 Example Topics

You can research topics such as:

```text
LLM agents in 2025
```

```text
CRISPR gene editing
```

```text
Fusion energy progress
```

```text
Quantum computing breakthroughs
```

```text
Generative AI applications
```

---

## 📊 Application Pipeline

The interface displays four pipeline stages:

```text
01  Search Agent
    ↓
02  Reader Agent
    ↓
03  Writer Chain
    ↓
04  Critic Chain
```

Each stage displays its current status:

- `WAITING`
- `● RUNNING`
- `✓ DONE`

This makes it easy to understand what the research system is doing.

---

## 📥 Output

After the pipeline finishes, ResearchMind displays:

### Search Results
Raw information collected by the Search Agent.

### Scraped Content
Detailed content extracted by the Reader Agent.

### Final Research Report
A structured report generated by the Writer Chain.

### Critic Feedback
Review and feedback generated by the Critic Chain.

The final report can also be downloaded as:

```text
research_report_<timestamp>.md
```

---

## 🔐 Security

Do not commit API keys or secrets to GitHub.

Recommended `.gitignore`:

```gitignore
.env
.venv/
__pycache__/
*.pyc
.streamlit/secrets.toml
```

If an API key is accidentally pushed to GitHub, revoke it and generate a new key.

---

## 🎯 Future Improvements

Possible future improvements include:

- 🌐 Support for multiple research sources
- 🧠 Better source ranking
- 📚 Citation and reference generation
- 📄 PDF report generation
- 💾 Research history
- 🔄 Parallel agent execution
- 🗃️ Vector database integration
- 💬 Conversational research assistant
- 📊 Research analytics dashboard
- 🚀 Deployment using Streamlit Cloud or another hosting platform

---

## 👩‍💻 Author

**Moksha S**

Computer Science Engineering Student

---

## ⭐ Project Summary

**ResearchMind** demonstrates how multiple specialized AI agents can collaborate to automate a complete research workflow.

Instead of relying on a single LLM call, the system divides the task into specialized stages:

> **Search → Read → Write → Critique**

This makes the project a practical example of **multi-agent AI, LLM orchestration, web research, web scraping, and automated report generation**.
