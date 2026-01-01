##### Problem Statement

Medical students rely on large reference textbooks such as **SRS Surgery**, which contain extensive and unstructured information.  
Finding precise answers (definitions, procedures, indications, complications, classifications) by manually searching through hundreds of pages is **time-consuming and inefficient**.

Traditional keyword search is limited because:
- medical terms may appear in different contexts,
- exact keyword matches may not exist,
- relevant information may be scattered across multiple sections.

**Objective:**  
To build an **educational Retrieval-Augmented Generation (RAG) system** that:
- converts unstructured medical textbook content into structured, searchable knowledge,
- retrieves the most relevant textbook sections for a student’s question,
- and generates **accurate, book-grounded answers** using a language model,
- through a simple and accessible web interface.

The system is designed **only for learning and academic revision**, not for clinical diagnosis or medical decision-making.

---

### 🐍 Python
- Acts as the **core programming language**
- Used to glue all components together:
  - text processing
  - model inference
  - retrieval logic
  - UI integration

---

### 📄 PDF / Text Processing Libraries
- Used to extract raw text from the **SRS Surgery book (PDF)**
- Convert book content into plain text so it can be processed by NLP tools

📌 Without this step, the book cannot be used by machine learning models.

---

### ✂️ Regex & Basic NLP
- Used to clean and structure unstructured medical text
- Helps in:
  - removing page numbers, headers, footers
  - fixing broken sentences and spacing
  - identifying section headings and content blocks

📌 This step converts **messy textbook text into clean, usable data**.

---

### 🧩 Text Chunking Logic
- Splits cleaned text into **small, overlapping chunks**
- Prevents loss of context during retrieval
- Ensures the LLM gets only relevant portions of the book

📌 Chunking is critical for accurate RAG systems.

---

### 🤗 Hugging Face Transformers
- Used to load **Transformer-based models**
- Provides:
  - embedding models (sentence transformers)
  - tokenization support
- Converts text into **dense numerical vectors** that capture semantic meaning

📌 These models are used for **embedding generation**, not for training new models.

---

### 🔢 Embeddings
- Each text chunk is converted into a numerical vector (embedding)
- Similar text produces similar vectors
- Enables **semantic search** instead of keyword-based search

📌 Embeddings allow the system to understand **meaning**, not just exact words.

---

### 📦 FAISS (Facebook AI Similarity Search)
- Stores all embeddings in a **vector database**
- Performs fast similarity search for user queries
- Retrieves the most relevant textbook sections

📌 FAISS is the **retrieval engine** of the RAG system.

---

### 🔗 LangChain
- Acts as the **orchestration framework** for the RAG pipeline
- Connects:
  - user query
  - embedding model
  - FAISS retriever
  - language model
- Ensures responses are generated **only from retrieved textbook content**

📌 LangChain controls the end-to-end RAG workflow.

---

### 🧠 Transformer-based Language Model (LLM – via OpenAI API)
- Used to generate **human-readable answers**
- Accessed using a secure **OpenAI API key**
- Receives:
  - the user’s question
  - only the retrieved textbook content
- Generates answers strictly based on this retrieved data

📌 The OpenAI model is used **only for answer generation**, not for storage or retrieval.

---

### 🔑 OpenAI API Key (Secure Usage)
- Required to access the transformer-based language model
- Stored securely using:
  - environment variables
- Never hard-coded in the source code

📌 This prevents API key exposure on GitHub and ensures secure usage.

---

###(🖥️ To be deployed in Streamlit )
- Used to build a simple and interactive **web interface**
- Allows users to:
  - type medical questions
  - view chatbot responses
- Makes the system usable by **non-technical medical students**

📌 Streamlit turns the backend RAG pipeline into a usable application.

---

### 📊 Pandas
- Used for handling structured data (if required)
- Helpful for inspection, debugging, or exporting intermediate results

---

## How Everything Works Together (One-Line Summary)

PDF Text → Regex Cleaning → Chunking → Transformer Embeddings → FAISS Retrieval → LangChain RAG → OpenAI LLM Answer → ( To be deployed in Streamlit UI )
