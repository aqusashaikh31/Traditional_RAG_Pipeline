# 🚀 Traditional RAG Pipeline

A learning project focused on understanding and implementing a **Traditional Retrieval-Augmented Generation (RAG) pipeline** using **LangChain, Sentence Transformers, FAISS, and Groq**.

This project demonstrates the complete RAG workflow, including document loading, text splitting, embedding generation, vector storage, similarity-based retrieval, and context-aware response generation.

---

## 🔄 RAG Pipeline

```text
Documents
    ↓
Document Loading
    ↓
Text Chunking
    ↓
Embedding Generation
    ↓
FAISS Vector Store
    ↓
Similarity Search
    ↓
Relevant Context Retrieval
    ↓
Groq LLM
    ↓
Generated Response
```

---

## 📁 Project Structure

```text
Traditional_RAG_Pipeline/
│
├── data/
│   ├── pdf/                    # PDF documents
│   ├── text_files/             # Text documents
│   └── vector_store/           # Stored vector database files
│
├── notebook/
│   ├── 1-langchain-document-components.svg
│   ├── 2_pdf_loader.ipynb
│   └── document.ipynb
│
├── src/
│   ├── __init__.py
│   ├── data_loader.py          # Loads different document formats
│   ├── embedding.py            # Text chunking and embedding generation
│   ├── vectorstore.py          # FAISS vector store and similarity search
│   └── search.py               # Retrieval and LLM response generation
│
├── app.py                      # Main application entry point
├── requirements.txt            # Project dependencies
├── pyproject.toml              # Project configuration
├── uv.lock                     # Locked dependency versions
├── .gitignore
└── README.md
```

---

## 🛠️ Technologies Used

- **Python 3.13+**
- **LangChain** – document loading and text splitting
- **Sentence Transformers** – text embedding generation
- **FAISS** – vector storage and similarity search
- **Groq / ChatGroq** – LLM-based response generation
- **PyPDF / PyMuPDF** – PDF document processing
- **ChromaDB** – vector database experimentation
- **python-dotenv** – environment variable management
- **Jupyter Notebook** – experimentation and learning

---

## ⚙️ How the RAG Pipeline Works

### 1. 📄 Document Loading

The `data_loader.py` module loads documents from the `data/` directory.

The project supports multiple document formats:

- PDF
- TXT
- CSV
- Excel
- Word
- JSON

---

### 2. ✂️ Text Chunking

Large documents are divided into smaller and more manageable chunks using LangChain's `RecursiveCharacterTextSplitter`.

The current configuration is:

```python
chunk_size = 1000
chunk_overlap = 200
```

Chunking helps the retrieval system work with relevant portions of the document instead of processing the entire document at once.

---

### 3. 🧠 Embedding Generation

The project uses the following Sentence Transformer model:

```text
all-MiniLM-L6-v2
```

The text chunks are converted into numerical vector representations called **embeddings**.

These embeddings allow the system to compare the semantic similarity between the user query and the stored document chunks.

---

### 4. 🗄️ Vector Storage

The generated embeddings are stored using **FAISS** with:

```text
IndexFlatL2
```

FAISS enables efficient similarity search over the generated vector embeddings.

---

### 5. 🔍 Similarity Search & Retrieval

When the user asks a question, the query is converted into an embedding and compared with the stored document vectors.

For example:

```text
What is embeddings?
```

The system retrieves the most relevant document chunks based on vector similarity.

---

### 6. 🤖 Response Generation

The retrieved document context is then passed to a **Groq-hosted LLM through ChatGroq**.

The LLM uses the retrieved context to generate a relevant and context-aware answer.

---

## 📦 Installation

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd Traditional_RAG_Pipeline
```

---

### 2. Create a Virtual Environment

Using Python:

```bash
python -m venv .venv
```

Activate the virtual environment on Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

---

### 3. Install Dependencies

Using `pip`:

```powershell
pip install -r requirements.txt
```

Or using `uv`:

```powershell
uv sync
```

---

## 🔑 Environment Variables

Create a `.env` file in the root directory of the project:

```env
GROQ_API_KEY=your_groq_api_key
```

> **Important:** Never upload your `.env` file or API keys to GitHub.

---

## ▶️ Run the Project

From the project root directory, run:

```powershell
python app.py
```

The application loads the documents, works with the FAISS vector store, performs similarity-based retrieval, and sends the retrieved context to the LLM for response generation.

---

## 🧪 Example Query

```text
What is embeddings?
```

The RAG pipeline retrieves the most relevant document chunks and uses the retrieved context to generate the final response.

---

## 📚 Learning Objectives

Through this project, I am learning and practicing:

- Document loaders in LangChain
- Recursive text splitting
- Text embeddings
- Vector stores
- FAISS similarity search
- Retrieval-Augmented Generation (RAG)
- Context retrieval
- Connecting retrieved context with an LLM
- Building a modular RAG pipeline using Python

---

## 🔒 GitHub Note

The following files and folders should **not** be committed to GitHub:

```text
.venv/
.env
__pycache__/
*.pyc
faiss_store/
```

These are excluded through `.gitignore`.

---

## 🚧 Project Status

This is a **learning project** created to understand and implement a traditional RAG pipeline step by step.

The project currently focuses on the core RAG workflow:

```text
Document → Chunking → Embeddings → Vector Store → Retrieval → LLM Response
```

---

## 🔮 Future Improvements

Some possible improvements for this project include:

- Better retrieval strategies
- Metadata filtering
- Hybrid search
- Reranking
- Conversation history
- Streaming responses
- Retrieval quality evaluation
- Improved prompt templates
- Production-ready API/UI

---

## 👩‍💻 Author

**Aqusa Shaikh**

AI & Data Science Graduate  
Learning **Generative AI, RAG & Agentic AI**
