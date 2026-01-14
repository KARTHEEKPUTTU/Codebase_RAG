# 🤖 Codebase RAG: Intelligent Repository Question-Answering System

## 📌 Overview
This project implements a **Retrieval-Augmented Generation (RAG)** system that allows users to ask natural-language questions about a GitHub codebase and receive **context-aware answers grounded in the actual source code**.

The system ingests a repository, embeds its source files, stores them in a vector database, and uses a Large Language Model (LLM) to answer questions based strictly on retrieved code context.

---

## 🧠 Problem Statement
Large codebases are difficult to understand, especially for onboarding, debugging, or exploration.

This project solves:
- Navigating unfamiliar repositories
- Understanding how components work together
- Answering implementation-level questions without manually searching files

---

## 🏗️ Architecture

```
GitHub Repo
↓
Code Parsing & Chunking
↓
Vector Embeddings (Sentence Transformers)
↓
Pinecone Vector Database
↓
Semantic Retrieval
↓
LLM (Context-Grounded Answer)
```


---

## 🗂️ Project Structure
```
Codebase_RAG/
│
├── *.ipynb # RAG pipeline implementation & experiments
├── app.py # Streamlit chat application
├── .env # API key configuration
└── README.md
```


---

## 🔍 Repository Ingestion
- Clones a GitHub repository locally
- Recursively scans files
- Supports multiple languages:
  - Python, JavaScript, TypeScript
  - Java, C/C++, Go, Rust, Swift
  - Jupyter notebooks
- Ignores non-relevant directories:
  - `node_modules`, `.git`, `venv`, `build`, etc.

---

## 🧠 Embedding & Indexing
- Uses **Sentence-Transformers (`all-mpnet-base-v2`)**
- Converts each file into vector embeddings
- Stores vectors in **Pinecone**
- Uses namespace isolation per repository

---

## 🔎 Retrieval-Augmented Generation (RAG)
1. User submits a question
2. Question is embedded
3. Top-K relevant code snippets retrieved from Pinecone
4. Retrieved code is injected into the LLM prompt
5. LLM generates an answer strictly based on code context

This prevents hallucination and keeps answers grounded in the actual repository.

---

## 💬 LLM Integration
- Uses **Groq-hosted LLaMA models**
- Custom system prompt:
  - Enforces senior-engineer style answers
  - Requires reasoning based on retrieved code only
- Supports reusable RAG query function

---

## 🌐 Streamlit Web Application

### Features
- ChatGPT-style interface
- Conversational memory
- Real-time streaming responses
- Ask questions like:
  - *How is the Python parser used?*
  - *How are JavaScript files processed?*
  - *What does this module do?*

---

## 🚀 How to Run the Application

```bash
pip install -r requirements.txt
streamlit run app.py
```
Set environment variables in .env:  
PINECONE_API_KEY=your_key_here    
GROQ_API_KEY=your_key_here

🧪 Skills Demonstrated
- Retrieval-Augmented Generation (RAG)
- Vector databases (Pinecone)
- Sentence-Transformer embeddings
- LLM prompt engineering
- Semantic search
- GitHub repository automation
- Streamlit deployment
- End-to-end LLM system design

📌 Project Type
- Applied AI Systems
- LLM Engineering
- Retrieval-Augmented Generation

🔮 Future Enhancements
- Code chunking strategies
- File-level citations in responses
- Multi-repo indexing
- Authentication & access control
- Cloud deployment

👤 Author

**Kartheek Puttu**
