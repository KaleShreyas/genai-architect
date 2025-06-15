# 📚 Course Recommendation Engine

This project implements a **Course Recommendation Engine** that returns the top-5 most relevant courses from a catalog of course offerings, based on a user query (completed courses + interest blurb).  

✅ **Tech Highlights**:
- Uses **Azure OpenAI Embeddings** for semantic representation.
- Uses **vector similarity search** (e.g. FAISS or cloud vector DB) for fast retrieval.
- Uses **LangChain** to structure embedding + search operations (optional).

---

## 🚀 How it works

### 🔹 User Input  
The user provides:
- A list of completed courses
- A short text describing their interests  

👉 Example:

---

### 🔹 Embedding the data  
- All **course descriptions** are converted into embeddings (high-dimensional vectors).
- The **user query** (completed courses + interests) is also converted into an embedding.

---

### 🔹 Semantic Search  
- Vectors are stored in a **vector database** (e.g. FAISS, Pinecone, Azure Cognitive Search).
- The user query vector is compared to the course vectors using **cosine similarity**.
- Top 5 most similar courses are returned.

---

## 🛠 Setup

### Requirements
- Python 3.8+
- `langchain`
- `openai` / `azure-openai`
- `faiss-cpu` (or another vector DB client)
- `numpy`

Install dependencies:
```bash
pip install langchain azure-openai faiss-cpu numpy
