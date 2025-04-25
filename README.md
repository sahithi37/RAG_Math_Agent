# 🧠 Math Tutor Agent – Agentic RAG with Feedback Loop

This project implements an **Agentic-RAG architecture** to simulate a math professor that solves **JEE-level math questions** with step-by-step explanations. The system smartly routes queries between a vector database and web search, applies input/output guardrails, and incorporates human feedback for continuous learning.

---

## 📌 Features

- ✅ **Input Guardrails** (DSPy): Accepts only academic math questions.
- 📚 **Knowledge Base Search**: Uses **Qdrant Vector DB** with OpenAI Embeddings to match known questions.
- 🌐 **Web Fallback**: Integrates **Tavily API** when no good match is found.
- ✍️ **GPT-3.5 Turbo Explanations**: Generates step-by-step math solutions.
- 🛡️ **Output Guardrails**: Filters for correctness and safety.
- 👍 **Human-in-the-Loop Feedback**: Users rate answers (Yes/No), logged for future learning.
- 📊 **Benchmarking**: Evaluated on **JEEBench** dataset with adjustable question limits.
- 💻 **Streamlit UI**: Interactive dashboard with multiple tabs.

---

## 🚀 Architecture Flow

graph TD
    A[User Query] --> B[Input Guardrail]
    B --> C[Check KB in Qdrant]
    C -->|Match Found| D[Use GPT to explain KB content]
    C -->|No Match| E[Use Tavily Web Search]
    E --> F[Use GPT to explain Web content]
    D --> G[Output Guardrail]
    F --> G
    G --> H[Answer + Feedback Logging]


