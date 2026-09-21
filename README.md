Traditional RAG Pipeline

A learning project that implements a Traditional Retrieval-Augmented
Generation (RAG) pipeline using LangChain, Sentence Transformers,
FAISS, and a Groq LLM.

The project demonstrates the complete RAG workflow: loading documents,
splitting them into chunks, generating embeddings, storing vectors,
retrieving relevant chunks, and generating a context-aware response.

🚀 RAG Pipeline {#rocket-rag-pipeline}

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
Relevant Context
   ↓
Groq LLM
   ↓
Generated Response

📁 Project Structure {#file_folder-project-structure}

Traditional_RAG_Pipeline/
│
├── data/
│   ├── pdf/                 # PDF documents used for the RAG pipeline
│   ├── text_files/          # Text documents
│   └── vector_store/        # Stored vector database files
│
├── notebook/
│   ├── 1-langchain-document-components.svg
│   ├── 2_pdf_loader.ipynb
│   └── document.ipynb
│
├── src/
│   ├── __init__.py
│   ├── data_loader.py       # Loads PDF, TXT, CSV, Excel, Word and JSON files
│   ├── embedding.py         # Chunking and embedding generation
│   ├── vectorstore.py       # FAISS vector store and similarity search
│   └── search.py            # Retrieval + LLM response generation
│
├── app.py                   # Main pipeline entry point
├── requirements.txt         # Python dependencies
├── pyproject.toml           # Project configuration and dependencies
├── uv.lock                  # Locked dependency versions
├── .gitignore
└── README.md

🛠️ Technologies Used {#hammer_and_wrench-technologies-used}

Python 3.13+

LangChain -- document loading and text splitting

Sentence Transformers -- text embeddings

FAISS -- vector storage and similarity search

Groq / ChatGroq -- LLM-based response generation

PyPDF / PyMuPDF -- PDF processing

ChromaDB -- included as a project dependency for vector database
experimentation

python-dotenv -- environment variable management

Jupyter Notebook -- experimentation and learning

🔄 How It Works {#arrows_counterclockwise-how-it-works}

1. Document Loading {#1-document-loading}

src/data_loader.py loads documents from the data/ directory.

Supported formats include:

PDF

TXT

CSV

Excel

Word

JSON

2. Text Chunking {#2-text-chunking}

Large documents are divided into smaller chunks using LangChain's
RecursiveCharacterTextSplitter.

Default configuration:

chunk_size = 1000
chunk_overlap = 200

3. Embedding Generation {#3-embedding-generation}

The project uses:

all-MiniLM-L6-v2

from Sentence Transformers to convert text chunks into numerical
vectors.

4. Vector Storage {#4-vector-storage}

The generated embeddings are stored using FAISS with IndexFlatL2.

This allows the system to perform similarity search and retrieve the
most relevant document chunks for a user query.

5. Retrieval {#5-retrieval}

For a query such as:

What is embeddings?

the query is converted into an embedding and compared with stored
document vectors.

The top relevant chunks are retrieved.

6. Generation {#6-generation}

The retrieved context is passed to a Groq-hosted LLM through ChatGroq,
which generates a summary/answer based on the retrieved information.

⚙️ Installation {#gear-installation}

Clone the repository

git clone <YOUR_GITHUB_REPOSITORY_URL>
cd Traditional_RAG_Pipeline

Create a virtual environment

Using Python:

python -m venv .venv

Activate it on Windows PowerShell:

.venv\Scripts\Activate.ps1

Install dependencies

pip install -r requirements.txt

Or, if using uv:

uv sync

🔑 Environment Variables {#key-environment-variables}

Create a .env file in the project root:

GROQ_API_KEY=your_groq_api_key

Do not upload .env to GitHub.

The .gitignore file already excludes .env.

Before running the LLM-based search, make sure src/search.py reads
the Groq API key from the environment rather than hard-coding a
secret.

▶️ Run the Project {#arrow_forward-run-the-project}

From the project root:

python app.py

The example pipeline loads the documents, builds/loads the FAISS vector
store, performs a similarity search, and sends retrieved context to the
LLM for summarization.

🧪 Example Query {#test_tube-example-query}

What is embeddings?

The system retrieves the most relevant document chunks and generates a
response using the retrieved context.

📚 Learning Objectives {#books-learning-objectives}

Through this project, I am learning:

Document loaders in LangChain

Recursive text splitting

Text embeddings

Vector databases / vector stores

FAISS similarity search

Retrieval-Augmented Generation

Connecting retrieved context with an LLM

Building a modular RAG pipeline with Python

🔒 GitHub Note {#lock-github-note}

The following files/folders should not be committed:

.venv/
.env
__pycache__/
*.pyc
faiss_store/

These are already included in .gitignore.

👩‍💻 Project Status {#woman_technologist-project-status}

This is a learning project focused on understanding and implementing
a traditional RAG pipeline step by step.

Future improvements can include:

Better retrieval strategies

Metadata filtering

Hybrid search

Reranking

Conversation history

Streaming responses

Evaluation of retrieval quality

Improved prompt templates

Production-ready API/UI

⭐ Author {#star-author}

Aqusa Shaikh

AI & Data Science Graduate | Learning Generative AI, RAG & Agentic AI
