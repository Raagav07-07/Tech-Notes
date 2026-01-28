# RAG

*Given the LLM the right truth before predicting*

---

## Mind Map  

Documents
  ↓
Chunking
  ↓
Embeddings
  ↓
Vector Database
  ↓
User Question → Embedding
  ↓
Cosine Similarity Search
  ↓
Top-k Chunks Retrieved
  ↓
Placed into Context Window
  ↓
LLM Generates Answer

---

1. **Document ingestion**

Inputs can be pdf, docs, policies, webpage, code and so on..
Problem : These are too large to provide as a context.  

---

2. **Chunking**

We spilt the document into chunks.  
Ideal chunk size --> 200 - 500 tokens  

**What happens if chunking is bad?**  
chunking | Result  
---------|-------
Too small | Loses context
Too big | Waste tokens

---

3. **Embeddings**
It gives the semantic meaning of that chunk in vector.

---

4. **Vector Database**
We store chunk_text+embeddings. Here we search by similarity not by keyword. We use cosine similiarity to find the similarity between the two vectors.

Eg. Pinecone, ChromaDB, FAISS, Weaviate  

---

5. **User Questions**
The user question is convertd into embeddings.

---

6. **Cosine Similarity**
We take the cosine similarity between the question vector and all chunks and retreive the relevant chunks in same vector space.

---

7. **Retrieve top-k chunks**
From the retreived chunks we will take the top-k chunks for the context based on the similarity score.

---

**When RAG can fail?**  
Problems | Cause
---------|------
Wrong chunks retreived | Bad embeddings 
Too much context | Token overflow
Model ignores context | Prompt poorly designed 
Similar chunking | Needs reranking 

---

**Retrieval Tuning**  
Ways to improve chunking  
- Better chunking
- Metadata filtering
- Reranking retrieved chunks
- Hybrid Search (keyword + vector)

---

**Why RAG > Fine-Tuning**

Fine-tuning bakes the knowledge into the weight of the model also it is expensive whereas RAG is cheap and it is an external knowledge.  

---

```
Embeddings → Find meaning
Cosine similarity → Find relevance
Chunking → Fit window
Context → Ground LLM
LLM → Fluent generator
```






