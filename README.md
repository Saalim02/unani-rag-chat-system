### Problem Statement : 
-Large surgery textbooks are difficult to search efficiently during exam preparation. 
This project uses a RAG-based LLM system to retrieve accurate, textbook-grounded answers for medical students.

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
  - tokenizer support
  - LLM inference (depending on setup)

📌 Transformers convert text into **dense numerical vectors** that capture meaning.

---

### 🔢 Embeddings
- Each text chunk is converted into a numerical vector (embedding)
- Similar text produces similar vectors
- Enables semantic search instead of keyword search

📌 Embeddings allow the system to “understand meaning”, not just words.

---

### 📦 FAISS (Facebook AI Similarity Search)
- Stores all embeddings in a **vector database**
- Performs fast similarity search when a user asks a question
- Retrieves the most relevant textbook sections

📌 FAISS is the **retrieval engine** of the RAG system.

---

### 🔗 LangChain
- Acts as the **orchestration framework**
- Connects:
  - user query
  - embedding model
  - FAISS retriever
  - transformer-based language model
- Ensures answers are generated **only from retrieved content**

📌 LangChain controls the RAG workflow end-to-end.

---

### 🧠 Transformer-based Language Model (LLM)
- Generates human-readable answers
- Uses **only the retrieved textbook content**
- Does not invent or hallucinate new medical facts

📌 The LLM is responsible for **answer formulation**, not knowledge storage.

---

### {(🖥️ TO be deployed in Streamlit )}
- Used to build a simple and interactive **web interface**
- Allows users to:
  - type medical questions
  - view chatbot responses
- Makes the system usable by **non-technical medical students**

📌 Streamlit turns the backend RAG system into a usable application.

## How Everything Works Together (One-Line Summary)
PDF Text → Regex Cleaning → Chunking → Transformer Embeddings → FAISS Retrieval → LangChain RAG → LLM Answer →  ( to be deployed in Streamlit UI )

