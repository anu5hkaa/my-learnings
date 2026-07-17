
# ChromaDB – My Learning Notes

This notebook is part of my journey to understand **Retrieval-Augmented Generation (RAG)** from scratch.

The goal of this notebook wasn't just to use ChromaDB, but to understand **why vector databases are needed** and how they fit into the retrieval pipeline of a RAG system.

---

## What I explored

- Creating a ChromaDB client and collection
- Using Sentence Transformers to generate embeddings
- Storing documents, IDs and embeddings
- Performing semantic similarity search
- Retrieving the most relevant documents using `collection.query()`

I first experimented with a single document to understand the workflow, and then extended it to multiple documents.

---

## My Understanding

From what I've learned so far:

- A RAG system stores external knowledge in a **Knowledge Base**.
- A **Vector Database** (such as ChromaDB, FAISS or Pinecone) stores embeddings along with the original documents.
- User queries are converted into embeddings using the same embedding model.
- ChromaDB performs semantic similarity search and returns the **Top-K most relevant documents**.
- These retrieved documents are then passed to an LLM to generate the final response.

---

## Workflow

```text
Documents
    │
    ▼
Embedding Model
    │
    ▼
ChromaDB
(Store Documents + Embeddings)
    │
    ▼
User Query
    │
    ▼
Query Embedding
    │
    ▼
Semantic Search
    │
    ▼
Top-K Retrieved Documents
```

---

## Tech Stack

- Python
- ChromaDB
- Sentence Transformers
- Pandas
- Google Colab

---

## Note

These are my personal learning notes while exploring RAG systems. As I continue learning, I'll keep refining this implementation and adding more components such as hybrid retrieval, re-ranking, and LLM integration.
