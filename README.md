# Advanced RAG Pipeline - PDF Q&A

A complete 7-stage Retrieval-Augmented Generation pipeline that answers questions from a business plan PDF with citations.

### 🚀 Live Output
> **Question:** What is monthly revenue?  
> **Answer:** The total illustrative revenue for the first year is approximately **₹18.94 lakh [page 3].**

### 🏗️ Architecture (7 Stages)

1.  **PDF Parsing:** `PyMuPDF` - Extracts text with page numbers
2.  **Chunking:** 500-word chunks with overlap
3.  **Embedding & Indexing:** ChromaDB + `all-MiniLM-L6-v2` (384-dim vectors)
4.  **Query Planning:** Query decomposition into sub-queries
5.  **HyDE:** Hypothetical Document Embedding for better retrieval
6.  **Reranking:** Cross-encoder reranking for relevance
7.  **Generation:** `gpt-4o-mini` with page citations `[page X]`

### 📁 Files
- `pipeline.py` - Main RAG pipeline code
- `Execution.txt` - Full execution log (5 pages, 11 chunks)
- `Businnes_plan.pdf` - Source document

### ⚙️ How to Run
```bash
# Install dependencies
pip install chromadb pymupdf openai python-dotenv

# Set API key in .env file
OPENAI_API_KEY=your_key_here

# Run
python pipeline.py