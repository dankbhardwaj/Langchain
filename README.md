# 🦜🔗 LangChain Tutorial

<div align="center">

![LangChain](https://img.shields.io/badge/LangChain-🦜🔗-green?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![AWS Lambda](https://img.shields.io/badge/AWS_Lambda-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

**A structured, hands-on LangChain tutorial series — from basic LLM calls to intelligent agents with database integration, powered by AWS Lambda.**

[📖 Chapters](#-chapter-overview) • [🚀 Getting Started](#-getting-started) • [💡 Usage](#-usage) • [📁 Structure](#-project-structure)

</div>

---

## 📖 About This Repository

This tutorial is a step-by-step guide to building real-world LLM applications using the [LangChain](https://python.langchain.com/) framework with **AWS Lambda** as the LLM backend. It is organized into chapters that progressively build your knowledge — starting from raw LLM calls and working all the way up to autonomous agents connected to live databases.

### What You'll Learn

| Chapter | Topic | Skills Gained |
|---|---|---|
| **CH-1** | LLM Fundamentals | LLM calls, messages, structured outputs |
| **CH-2** | Chains | LCEL chains, custom runnables, parallel & conditional logic |
| **CH-3** | Agents | ReAct agents, tool usage, SQLite DB integration |

---

## 📁 Project Structure

```
Langchain_Tutorial/
│
├── main.py                               # 🚀 Entry point — prints project welcome message
├── pyproject.toml                        # 📦 Project metadata and dependencies
├── README.md                             # 📄 You are here!
│
├── CH-1/                                 # 📘 Getting Started with LLMs
│   ├── 1_LLM_Call.ipynb                  #   Basic LLM calls via AWS Lambda
│   ├── 2_Messages.ipynb                  #   Working with message objects
│   └── 3_Structured_Outputs.ipynb       #   Structured outputs from LLMs
│
├── CH-2/                                 # 📗 Building Chains with LCEL
│   ├── 1_first_chain.ipynb               #   Your first LangChain chain
│   ├── 2_chain_with_customRunnable.ipynb #   Custom runnables in chains
│   ├── 3_parallel_chains.ipynb           #   Parallel chain execution
│   └── 4_conditional_chains.ipynb       #   Conditional / branching logic
│
└── CH-3/                                 # 📕 Agents & Database Integration
    ├── 1_ReAct_Agent_Intro.ipynb         #   Introduction to ReAct agents
    ├── 2_React_DB_Agent.ipynb            #   Agent connected to a database
    ├── init_db.py                        #   Script to initialize the SalesDB
    └── SalesDB/                          #   SQLite database files live here
```

---

## 🚀 Getting Started

### Prerequisites

- Python **3.9+**
- An **AWS account** with Lambda configured as your LLM backend
- Jupyter Notebook or JupyterLab

### 1. Clone the Repository

```bash
git clone https://github.com/dankbhardwaj/Langchain.git
cd Langchain
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv

# macOS / Linux
source .venv/bin/activate

# Windows
.venv\Scripts\activate
```

### 3. Install Dependencies

```bash
# Using pyproject.toml (recommended)
pip install -e .

# Or install directly
pip install -r requirements.txt
```

### 4. Configure AWS Credentials

This project uses **AWS Lambda** as the LLM provider. Set up your credentials:

```bash
aws configure
```

Or export them as environment variables:

```bash
export AWS_ACCESS_KEY_ID=your_access_key_id
export AWS_SECRET_ACCESS_KEY=your_secret_access_key
export AWS_DEFAULT_REGION=us-east-1
export AWS_LAMBDA_FUNCTION_NAME=your_lambda_function_name
```

Or create a `.env` file in the project root:

```env
AWS_ACCESS_KEY_ID=your_access_key_id
AWS_SECRET_ACCESS_KEY=your_secret_access_key
AWS_DEFAULT_REGION=us-east-1
AWS_LAMBDA_FUNCTION_NAME=your_lambda_function_name
```

---

## 💡 Usage

### Run the Entry Point

```bash
python main.py
```

### Explore the Notebooks

Launch Jupyter and open any chapter in order:

```bash
jupyter notebook
# or
jupyter lab
```

Navigate to `CH-1`, `CH-2`, or `CH-3` and run notebooks sequentially for the best learning experience.

### Initialize the Sales Database (CH-3)

Before running the database agent notebooks, bootstrap the SQLite database:

```bash
python CH-3/init_db.py
```

This creates `SalesDB/sales.db` populated with sample sales data ready for agent querying.

---

## 📚 Chapter Overview

### 📘 CH-1 — Getting Started with LLMs

> Master the foundations: calling LLMs, handling messages, and parsing structured outputs via AWS Lambda.

| Notebook | Description |
|---|---|
| `1_LLM_Call.ipynb` | Make your first LLM call using AWS Lambda as the inference backend |
| `2_Messages.ipynb` | Work with `HumanMessage`, `AIMessage`, `SystemMessage` and multi-turn chat history |
| `3_Structured_Outputs.ipynb` | Parse raw LLM responses into typed Python objects using output parsers |

---

### 📗 CH-2 — Building Chains

> Compose powerful, reusable pipelines using LangChain Expression Language (LCEL).

| Notebook | Description |
|---|---|
| `1_first_chain.ipynb` | Build a simple `prompt → llm → parser` pipeline |
| `2_chain_with_customRunnable.ipynb` | Extend chains with custom `Runnable` components |
| `3_parallel_chains.ipynb` | Run multiple chains simultaneously with `RunnableParallel` |
| `4_conditional_chains.ipynb` | Add dynamic branching logic using `RunnableBranch` |

**LCEL Quick Reference:**

```python
# Basic chain
chain = prompt | llm | output_parser

# Parallel chains
chain = RunnableParallel(branch_a=chain_a, branch_b=chain_b)

# Conditional chain
chain = RunnableBranch(
    (condition_fn, chain_a),
    default_chain          # fallback
)
```

---

### 📕 CH-3 — Agents & Database Integration

> Build autonomous ReAct agents that reason, select tools, and query real databases.

| File | Description |
|---|---|
| `1_ReAct_Agent_Intro.ipynb` | Understand the ReAct (Reason + Act) loop and build your first agent |
| `2_React_DB_Agent.ipynb` | A fully working agent that answers questions by querying SQLite |
| `init_db.py` | Seeds `SalesDB/sales.db` with sample sales records |
| `SalesDB/` | Contains the SQLite database after `init_db.py` is run |

**How the DB Agent Works:**

```
User Query  ──▶  ReAct Agent (Reason)
                      │
                      ▼
               Selects SQL Tool (Act)
                      │
                      ▼
               Queries SalesDB (SQLite)
                      │
                      ▼
               Observes the Result
                      │
                      ▼
               Generates Final Answer  ──▶  User
```

---

## 🛠️ Tech Stack

| Technology | Role |
|---|---|
| [LangChain](https://python.langchain.com/) | Core LLM orchestration framework |
| [AWS Lambda](https://aws.amazon.com/lambda/) | Serverless LLM backend / inference provider |
| [LCEL](https://python.langchain.com/docs/concepts/lcel/) | LangChain Expression Language for composable chains |
| [SQLite](https://www.sqlite.org/) | Lightweight embedded database for agent tool use |
| [Jupyter](https://jupyter.org/) | Interactive notebook environment for step-by-step learning |
| [pyproject.toml](https://pip.pypa.io/en/stable/reference/build-system/pyproject-toml/) | Modern Python project and dependency management |

---

## 🗺️ Learning Path

```
START
  │
  ▼
📘 CH-1: LLM Basics
  ├── Make raw LLM calls via AWS Lambda
  ├── Handle Human / AI / System messages
  └── Parse responses into structured objects
  │
  ▼
📗 CH-2: Chains (LCEL)
  ├── Build your first chain
  ├── Add custom Runnables
  ├── Run chains in parallel
  └── Add conditional branching
  │
  ▼
📕 CH-3: Agents
  ├── Understand the ReAct reasoning loop
  ├── Connect agent to a live SQLite database
  └── Query data using natural language
  │
  ▼
🎓 Ready to build production LLM applications!
```

---

## 📦 Dependencies Overview

Managed via `pyproject.toml`. Key packages include:

```toml
[tool.poetry.dependencies]
python = "^3.9"
langchain = "*"
langchain-aws = "*"       # AWS Lambda LLM integration
boto3 = "*"               # AWS SDK
jupyter = "*"
python-dotenv = "*"
```

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. **Fork** the repo
2. **Create** your branch: `git checkout -b feature/ch-4-rag`
3. **Commit** your changes: `git commit -m 'Add CH-4: RAG Pipeline'`
4. **Push** to your branch: `git push origin feature/ch-4-rag`
5. **Open** a Pull Request

---

## 📝 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Dank Bhardwaj**

- GitHub: [@dankbhardwaj](https://github.com/dankbhardwaj)

---

<div align="center">

⭐ **Found this helpful? Give it a star — it helps others discover this tutorial!** ⭐

*Built with ❤️ using LangChain + AWS Lambda*

</div>
