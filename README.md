# DocuMind — I read it so you don't have to

A local RAG (Retrieval-Augmented Generation) chatbot that lets you chat with any PDF using AI. Upload any document and ask questions in plain English — DocuMind finds the relevant sections and answers accurately.

## Features

- **Multi-PDF support** — index multiple PDFs and search across all at once
- **Smart chunking** — automatically detects document type and picks the best chunking strategy (recursive, semantic)
- **Balanced retrieval** — prevents large documents from drowning out smaller ones
- **Conversation memory** — follow-up questions work naturally
- **Source transparency** — every answer shows exactly which chunks were used
- **No hallucination** — answers only from your documents, never made up

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Streamlit |
| LLM | Groq API (llama3-8b-8192) |
| Embeddings | sentence-transformers (all-MiniLM-L6-v2) |
| Vector DB | ChromaDB |
| Chunking | LangChain RecursiveCharacterTextSplitter + SemanticChunker |
| PDF parsing | pypdf |

## How It Works

```
PDF → Extract text → Detect strategy → Chunk → Embed → ChromaDB
                                                              ↓
User question → Embed → Similarity search → Top-k chunks → LLM → Answer
```

## Setup

### 1. Clone the repo
```bash
git clone https://github.com/yourusername/documind.git
cd documind
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Set up environment variables
Create a `.env` file:
```
GROQ_API_KEY=your_groq_api_key_here
```
Get a free Groq API key at [console.groq.com](https://console.groq.com)

### 4. Run the app
```bash
streamlit run app.py
```

## Project Structure

```
documind/
├── app.py              # Streamlit UI
├── ingest.py           # PDF processing and indexing
├── rag.py              # Query engine and retrieval
├── requirements.txt    # Dependencies
├── pdficon.png         # App icon
└── .gitignore
```

## Key Concepts Implemented

- **RAG pipeline** — retrieval-augmented generation from scratch
- **Hybrid chunking** — auto-detects document type, picks recursive or semantic splitting
- **Balanced multi-doc retrieval** — equal representation across documents of different sizes
- **Conversation history** — multi-turn chat with context window management
- **Groq inference** — fast LLM responses via Groq's free API

## Live Demo

[DocuMind on Streamlit Cloud](https://docu-mind-ai-chatbot.streamlit.app/)
