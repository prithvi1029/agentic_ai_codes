# 🧩 FDS-to-TDS Generator Agentic System

A multi-agent system powered by LangGraph, Streamlit, and Together.ai for automatic generation of **TDS (Technical Design Specification)** from **FDS (Functional Design Specification)** documents in SAP. It uses Retrieval-Augmented Generation (RAG), role-specialized agents, scoring, feedback loops, and retry logic to ensure high-quality TDS outputs.

---

## 📦 Features

- ✅ PDF Upload & Vectorization of FDS
- 🔍 RAG-based Internal Retrieval
- 🌐 External Web Context using Tavily
- 🤖 Agentic Generation using Mixtral LLM
- 🧠 Explanation Generator
- 📊 Scoring Agent with Retry if Score < 7
- 📝 MongoDB Logging

---

## 🧠 Multi-Agent Graph Structure

```text
+----------+
| retrieve |  <-- extract internal context from PDF
+----------+
     |
+-----v----+
|   web    |  <-- get external info using Tavily
+----------+
     |
+-----v----+
|  answer  |  <-- generate TDS using context + web
+----------+
     |
+-----v----+
| explain  |  <-- generate explanation for reasoning
+----------+
     |
+-----v----+
|  score   |  <-- give score and retry if score < 7
+----------+
     |
  [  END  ]
```

---

## 🚀 How to Run

```bash
git clone https://github.com/YOUR_USERNAME/agentic_ai_codes.git
cd agentic_ai_codes

# Create virtual environment
python -m venv venv
venv\Scripts\activate   # or source venv/bin/activate

# Install requirements
pip install -r requirements.txt

# Run the Streamlit app
streamlit run fds_to_tds_agent.py
```

---

## 📁 Folder Structure

```text
.
├── fds_to_tds_agent.py         # Streamlit + Agent Graph
├── utils/
│   └── mongo_helper.py         # MongoDB handler
├── requirements.txt
└── README.md
```

---

## 🔐 API Keys Required

- `TOGETHER_API_KEY`: for Mixtral-8x7B via Together.ai
- `TAVILY_API_KEY`: for web search augmentation

You can set them via:

```python
os.environ["TOGETHER_API_KEY"] = "your-api-key"
os.environ["TAVILY_API_KEY"] = "your-api-key"
```

---

## 🙌 Acknowledgements

- **LangGraph** for multi-agent orchestration
- **Mixtral-8x7B** via Together.ai for LLM capabilities
- **Tavily API** for live web data
- **Streamlit** for the UI
- **MongoDB** for logging and feedback capture

---

## 📬 Contact

Raise an issue or connect for feature requests, contributions, or collaborations.