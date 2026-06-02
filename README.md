# Self-Correcting RAG Framework[cite: 1]

A production-ready implementation of a **Corrective Retrieval-Augmented Generation (CRAG)** engine built to eliminate LLM hallucinations[cite: 1]. This framework replaces traditional linear RAG workflows with an evaluative, self-correcting loop that dynamically assesses and refines context quality before generation[cite: 1].

## 📐 System Architecture

Below is the design workflow of the evaluation and fallback pipeline implemented in this repository:

![System Architecture](Screenshot%202026-06-01%20174403.png)

---

## 🚀 Key Features

* **Self-Correction Loop:** Active document grading ensures only highly relevant context reaches the LLM[cite: 1]. Unaligned or ambiguous documents trigger automated fallback mechanisms[cite: 1].
* **Two-Stage Retrieval:** Leverages **HuggingFace BGE Embeddings** (`BAAI/bge-base-en-v1.5`) and **ChromaDB** to extract the top 10 raw document chunks, which are immediately compressed and optimized using **Cohere Rerank v3.5**[cite: 1].
* **LLM-as-Judge Evaluation:** Uses **Llama 3.3 (via Groq)** with structured outputs to grade query-to-document alignment[cite: 1].
* **Dynamic Query Rewriter:** Automatically reformulates search strings and runs an iterative recovery retrieval loop up to a fixed threshold if initial contexts fail validation[cite: 1].
* **Enterprise Observability:** Features native integration with **Langfuse** for execution tracing and the **Ragas Framework** for metric benchmarking[cite: 1].

---

## 🛠️ Tech Stack

* **Notebook Implementation:** `selfrag.ipynb`
* **LLM API:** Groq Cloud (`Llama-3.3-70b-versatile`)[cite: 1]
* **Vector DB & Embeddings:** ChromaDB & BGE-Base-v1.5[cite: 1]
* **Reranker:** Cohere Rerank API v3.5[cite: 1]
* **Observability & Eval:** Langfuse & Ragas Framework[cite: 1]

---

## 🔧 Quick Setup

1. **Configure Environment Variables:**
   Create a `.env` file in the root directory:
```env
   GROQ_API_KEY=your_groq_key
   COHERE_API_KEY=your_cohere_key
   LANGFUSE_PUBLIC_KEY=your_public_key
   LANGFUSE_SECRET_KEY=your_secret_key
