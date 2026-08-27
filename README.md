📄 DocuMind AI
Multimodal Document Intelligence RAG System

An end-to-end Retrieval-Augmented Generation (RAG) system that enables users to upload PDF documents, retrieve relevant information using hybrid search, and generate grounded answers with source references using Google Gemini.

🚀 Project Overview

DocuMind AI is a Multimodal Document Intelligence system designed to make large and complex PDF documents easier to explore and understand.

Instead of manually reading through long documents, users can upload a PDF and ask natural-language questions. The system processes the document, converts its content into searchable chunks, retrieves the most relevant information using a combination of semantic and keyword search, and generates context-grounded answers.

The project combines LLMs, embeddings, vector databases, hybrid retrieval, and document processing into a complete RAG pipeline.

✨ Key Features
📄 Upload and process PDF documents
✂️ Intelligent document chunking with overlap
🧠 Semantic search using Gemini embeddings
🔎 Keyword search using BM25
⚡ Hybrid retrieval combining semantic + keyword search
🤖 Context-grounded answer generation using Gemini
📚 Source document and page references
🖼️ Multimodal document processing architecture
🔄 Reset functionality for processing new documents
⚠️ Graceful Gemini API quota and error handling
🖥️ Interactive Gradio interface
🆓 Designed with free-tier tools and deployment in mind


🧠 How the RAG Pipeline Works
1️⃣ Document Ingestion

The user uploads a PDF document.

The system extracts:

Text content
Page information
Document metadata
Visual/page information for multimodal processing
2️⃣ Document Chunking

Large documents cannot be sent directly to an LLM efficiently.

Therefore, the extracted text is divided into smaller overlapping chunks.

Each chunk contains metadata such as:

{
    "chunk_id": "unique-id",
    "content": "Revenue increased by 25%...",
    "content_type": "text",
    "document_name": "annual_report.pdf",
    "page_number": 12,
    "chunk_index": 0
}

Chunk overlap helps preserve context between adjacent chunks.

3️⃣ Semantic Search

Each document chunk is converted into a vector representation using:

Gemini Embedding Model

The embeddings are stored in ChromaDB.

When a user asks a question:

User Query
     ↓
Gemini Embedding
     ↓
Vector Similarity Search
     ↓
Relevant Document Chunks
4️⃣ BM25 Keyword Search

Semantic search can sometimes miss exact keywords, names, numbers, or specific terminology.

To improve retrieval, DocuMind AI also uses BM25 keyword retrieval.

This allows the system to retrieve documents based on lexical similarity.

5️⃣ Hybrid Retrieval

The final retrieval strategy combines:

Semantic Search
       +
BM25 Keyword Search
       ↓
Hybrid Ranking
       ↓
Most Relevant Context

This improves retrieval quality compared with relying on only vector similarity search.

6️⃣ Grounded Answer Generation

The retrieved document chunks are passed to Gemini along with the user's question.

The model is instructed to answer using only the retrieved context.

Retrieved Context
        +
User Question
        ↓
Gemini
        ↓
Grounded Answer

If the answer cannot be found in the retrieved context, the system is designed to indicate that the information was not found.


🛠️ Tech Stack
Technology	Purpose
Python	Core development
Google Gemini	LLM and embeddings
ChromaDB	Vector database
BM25	Keyword retrieval
PyMuPDF	PDF processing
Gradio	Interactive user interface
NumPy	Data processing
Kaggle	Development environment

📂 Project Structure
DocuMind-AI/
│
├── notebooks/
│   └── documind_ai.ipynb
│
├── app/
│   └── app.py
│
├── requirements.txt
├── .gitignore
└── README.md

⚙️ Installation

Clone the repository:

git clone <your-repository-url>
cd DocuMind-AI

Install dependencies:

pip install -r requirements.txt


🔐 Environment Setup

Create an environment variable:

GEMINI_API_KEY

Example:

export GEMINI_API_KEY="your_api_key"

On Windows PowerShell:

$env:GEMINI_API_KEY="your_api_key"


▶️ Running the Project

For the notebook version:

jupyter notebook

Open:

notebooks/documind_ai.ipynb

For the future application version:

python app/app.py


💬 Example Questions

Users can ask questions such as:

What was the revenue growth mentioned in the document?

Summarize the key financial performance.

What are the major risks discussed?

What were the key findings of the report?

Compare the results mentioned in different sections.


⚠️ API Quota Handling

The project includes handling for Gemini API limitations.

The system detects errors such as:

429 RESOURCE_EXHAUSTED

and returns a user-friendly message instead of crashing the application.

This makes the application more robust when working with free-tier API limits.


🎯 Key Technical Concepts Demonstrated

This project demonstrates practical experience with:

Retrieval-Augmented Generation
Large Language Models
Embeddings
Vector Databases
ChromaDB
Hybrid Search
BM25
Semantic Search
Document Processing
PDF Parsing
Metadata Management
Context Engineering
Prompt Engineering
API Error Handling
Rate Limit Handling
Gradio Applications
AI Application Development


🔮 Future Improvements

Planned improvements include:

 Support for tables and charts
 Image-based question answering
 OCR for scanned PDFs
 Multi-document RAG
 Conversation memory
 Query rewriting
 Reranking
 Evaluation pipeline for RAG performance
 Response caching
 Persistent vector database
 Cloud deployment
 Authentication and user sessions


📊 Why This Project Matters

DocuMind AI goes beyond a basic chatbot by implementing a complete document intelligence pipeline.

The project demonstrates how modern AI applications combine:

LLMs
+
Embeddings
+
Vector Search
+
Keyword Retrieval
+
Document Processing
+
Context Engineering
+
Error Handling

to build reliable Retrieval-Augmented Generation systems.

👨‍💻 Author

Pranay Soni

Aspiring Data Scientist / AI Engineer

If you find this project useful, consider giving the repository a ⭐.