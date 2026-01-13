# RAG Project

> [!NOTE]
> **Work in Progress**: This project is currently under active development and is considered incomplete.

A generic Retrieval-Augmented Generation (RAG) implementation using LangChain, Ollama, and ChromaDB. This project demonstrates how to ingest text documents, create vector embeddings, and perform semantic retrieval to answer queries based on the ingested context.

## Features

- **Document Ingestion**: Load text documents from a directory.
- **Text Chunking**: Split documents into manageable chunks for embedding.
- **Vector Storage**: Store embeddings locally using ChromaDB.
- **Semantic Retrieval**: Query the vector store to find relevant context.
- **Local LLM Support**: Uses Ollama for embeddings.

## Tech Stack

- **Python 3.x**
- **[LangChain](https://python.langchain.com/docs/get_started/introduction)**: Framework for developing applications powered by language models.
- **[Ollama](https://ollama.com/)**: Run Llama 3, Mistral, Gemma, and other models locally.
- **[ChromaDB](https://www.trychroma.com/)**: The open-source embedding database.

## Prerequisites

1.  **Python 3.8+** installed.
2.  **Ollama** installed and running.
    *   Install Ollama from [ollama.com](https://ollama.com).
    *   Pull the embedding model required for this project:
        ```bash
        ollama pull nomic-embed-text:v1.5
        ```

## Installation

1.  Clone the repository:
    ```bash
    git clone <repository_url>
    cd <repository_name>
    ```

2.  Create a virtual environment (recommended):
    ```bash
    python -m venv .venv
    source .venv/bin/activate  # On Windows use `.venv\Scripts\activate`
    ```

3.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
    *(Note: If `requirements.txt` is missing, you may need to manually install `langchain-community`, `langchain-ollama`, `langchain-chroma`, `python-dotenv`)*

4.  Set up environment variables:
    *   Create a `.env` file if necessary (check `.env.example` if available).

## Usage

### 1. Ingest Documents

Place your `.txt` files in the `docs/` directory. Then run the ingestion pipeline to process the documents and create the vector store:

```bash
python ingestion_pipeline.py
```

This script will:
- Load documents from `docs/`.
- Split them into chunks.
- Generate embeddings using Ollama.
- Store them in `db/chroma_db`.

### 2. Query / Retrieval

Run the retrieval pipeline to query the vector store:

```bash
python retrieval_pipeline.py
```

Currently, the query is hardcoded in the script (`"When did Google became a public company?"`). You can modify the `query` variable in `retrieval_pipeline.py` to test different questions.

## Project Structure

```
.
├── db/                   # ChromaDB persistence directory (created after ingestion)
├── docs/                 # Directory for input text documents
├── ingestion_pipeline.py # Script to ingest and embed documents
├── retrieval_pipeline.py # Script to query the vector store
├── .gitignore            # Git ignore file
└── README.md             # Project documentation
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
