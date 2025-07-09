
# 📑 Document Quality Analyzer Agent (FDS/TDS)

An AI-powered document quality evaluator built using LangGraph, Streamlit, and Together.ai’s Mixtral model. This tool compares FDS/TDS technical documents section-wise, scores them based on quality, and suggests improvements. It’s ideal for SAP automation pipelines to ensure document compliance, completeness, and clarity using LLM-powered multi-agent reasoning.

---

## 📦 Features

### ✅ DOCX Upload and Section Matching
- Upload **reference** and **candidate** `.docx` documents.
- Sections are extracted using heading-based splitting logic.
- Only common sections between both documents are compared.

### 🧠 Multi-Agent Workflow (LangGraph)
- **Compare Agent**: Compares candidate section to reference and provides feedback.
- **Score Agent**: Rates the section from 1 to 10 and explains the score.
- **Retry Agent**: Suggests rewritten or improved section if score is low (< 7).

### 🔁 Feedback & Retry Loops
- If section quality is low, a **corrective retry** agent rewrites the section.
- Ensures continuous improvement before finalizing the feedback.

### 📝 MongoDB Logging
- Each section’s:
  - Reference and candidate text
  - Feedback
  - Score
  - Suggested rewrite (if needed)
  - Timestamp  
  is logged to MongoDB (`doc_quality.section_logs`).

---

### 📝 Graph structure:

           +-----------+
           | __start__ |
           +-----------+
                  |
            +-----v------+
            |  compare   | 🔍 Compare content
            +-----+------+
                  |
            +-----v------+
            |   score    | 🧮 Score the quality
            +-----+------+
                  |
            +-----v------+
            |   retry    | 🔁 Retry suggestion if needed
            +-----+------+
                  |
           +------v------+
           |   __end__   |
           +-------------+

---

## 🚀 How to Run

1. Clone this repository or save the script:

```bash
git clone https://github.com/YOUR_USERNAME/agentic_ai_codes.git
cd agentic_ai_codes
````

2. Create and activate a virtual environment:

```bash
python -m venv venv
venv\Scripts\activate  # Windows
# or
source venv/bin/activate  # macOS/Linux
```

3. Install required packages:

```bash
pip install -r requirements.txt
```

4. Launch the Streamlit app:

```bash
streamlit run document_quality_analyser.py
```

---

## 🧪 Example Run

> Upload your Reference and Candidate FDS/TDS `.docx` files

### Output:

* ✍️ **Feedback** on completeness, clarity, correctness.
* 📊 **Score** out of 10 with explanation.
* 🔁 **Suggested rewrite** (if score < 7).
* 🗃️ **Logged** in MongoDB with timestamp.

---

## 📚 Techniques Used

* **LangGraph**: For orchestrating multi-agent flows.
* **Corrective RAG**: Retry logic based on section scoring.
* **Self-RAG**: Feedback + scoring agent loop to drive improvement.
* **Streamlit UI**: For document upload and result viewing.
* **MongoDB**: For persistence of logs and audit trails.
* **Mixtral-8x7B (Together.ai)**: Used for all LLM reasoning.

---

## 📁 Folder Structure

```
.
├── document_quality_analyser.py       # Streamlit UI + agent graph
├── utils/
│   └── mongo_helper.py                # MongoDB connector
├── requirements.txt
└── README.md
```

---

## 🔐 API Keys

Set these in your environment:

* `TOGETHER_API_KEY`: For calling Mixtral via Together.ai
* `TAVILY_API_KEY`: For optional web-enhanced capabilities

Example:

```python
os.environ["TOGETHER_API_KEY"] = "your-together-api-key"
os.environ["TAVILY_API_KEY"] = "your-tavily-api-key"
```

---

## 🙌 Acknowledgements

* **LangGraph** for agent orchestration
* **Together.ai** for inference via Mixtral-8x7B
* **Streamlit** for the frontend
* **MongoDB** for backend storage and logging

---

## 📬 Contact

For collaborations, improvements, or support, feel free to raise an issue or connect directly.

```

---

Let me know if you want me to:
- Save this file as `README.md` in your current VS Code project
- Add project badges (e.g. Python version, license)
- Push this to a GitHub repository

Would you like any of these next?
```
