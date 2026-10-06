# Retrieval-Augmented Generation (RAG)

RAG connects private, domain-specific data to an LLM, reducing hallucinations and allowing the model to cite its sources.

## 1. The RAG Pipeline

### Phase A: Data Ingestion (Offline)
1.  **Extract:** Load documents (PDFs, Confluence, databases).
2.  **Chunk:** Split documents into smaller tokens (e.g., 500-token chunks with 50-token overlap). 
    *   *Tip: Preserve semantic boundaries (paragraphs, markdown headers).*
3.  **Embed:** Convert chunks into dense vector embeddings using models like OpenAI `text-embedding-3-small` or HuggingFace sentence transformers.
4.  **Store:** Save vectors and metadata in a Vector Database (ChromaDB, Pinecone, FAISS).

### Phase B: Retrieval & Generation (Runtime)
1.  **Query Embedding:** Convert user query into a vector using the same embedding model.
2.  **Similarity Search:** Perform a cosine similarity search in the Vector DB to find the top $K$ most relevant chunks.
    $$\text{Cosine Similarity} = \frac{A \cdot B}{\vert{}\vert{}A\vert{}\vert{} \vert{}\vert{}B\vert{}\vert{}}$$
3.  **Prompt Injection:** Insert the retrieved chunks into the LLM context window.
4.  **Synthesis:** The LLM generates an answer strictly based on the provided context.

## 2. Advanced RAG Techniques

| Technique | Purpose | Mechanism |
|---|---|---|
| **Query Reformulation** | Fixes poor user prompts. | Uses a smaller LLM to rewrite the user's query for better retrieval before searching the database. |
| **Hybrid Search** | Improves retrieval recall. | Combines semantic vector search with keyword-based search (BM25). |
| **Re-ranking** | Improves precision of top results. | Uses a cross-encoder model to score and re-order the retrieved chunks before passing them to the LLM. |
| **Parent-Child Retrieval** | Balances search granularity with LLM context. | Embeds small chunks for precise searching, but retrieves the larger parent document for the LLM to read. |


*©️ Created by Wecncode Developer Community!*
