
# 🧾 Receipto AI: End-to-End Expense Automation & RAG Assistant

**Receipto AI** is an end-to-end financial automation system and interactive dashboard. It leverages Google's `gemini-3.6-flash` model via structured Pydantic schemas to extract precise JSON data from messy receipts, automatically indexing the structured records across a dual-database architecture for seamless retrieval-augmented generation (RAG) and financial querying.

---

## 🚀 Key Features

* **Structured LLM Parsing:** Parses unstructured receipt text into validated JSON schema fields (`merchant`, `date`, `total_amount`, `category`, `tax_amount`) using `gemini-3.6-flash` and Pydantic.
* **Dual-Database Pipeline:**
  * **Relational Storage (SQLite):** In-memory structured SQL database (`expenses` table) for fast tabular storage and numerical aggregations.
  * **Vector Storage (ChromaDB):** Generates semantic summaries and indexes them in a vector collection (`expense_vectors`) for similarity search.
* **RAG-Powered Financial QA:** Performs semantic vector search over stored expense summaries to synthesize concise natural-language answers to spending queries.
* **Interactive Frontend Options:** Includes both a Python Gradio web interface and an ultra-modern React + Tailwind CSS dashboard template.

---

## 🛠️ Tech Stack

* **LLM Engine:** Google Gemini API (`gemini-3.6-flash`)
* **SDKs & Libraries:** `google-genai`, `pydantic`
* **Vector & Relational Storage:** `chromadb`, `sqlite3`
* **User Interface:** `gradio` (Python UI) / React + Tailwind CSS (Dashboard)

---

## 📋 Installation & Setup

### 1. Clone the Repository
2. Install Required Packages
Bash
pip install google-genai pydantic chromadb gradio
3. Set Up API Key
Ensure you have a Gemini API key. Set it as an environment variable in your terminal:

Bash
export GEMINI_API_KEY="your_gemini_api_key_here"
⚡ Quick Start
Execute the main python script to initialize the databases, process sample receipts, and launch the Gradio web interface:

Bash
python app.py
Core Architecture Workflow
Extraction: parse_receipt_text(raw_text) sends raw text to gemini-3.6-flash with response_mime_type="application/json" and ReceiptData schema.

Dual-Storage: store_expense(parsed_json) executes SQL INSERT into SQLite while adding embedded summaries into ChromaDB.

RAG Queries: answer_expense_question(query) queries top matching vector contexts from ChromaDB and prompts Gemini for a natural summary answer.

https://receipto-vision-ai.lovable.app
```bash
git clone [https://github.com/your-username/receipto-ai.git](https://github.com/your-username/receipto-ai.git)
cd receipto-ai
