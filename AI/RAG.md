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
----------------|------------
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

---

# RAG Tuning - Metadata, Chunking, Re-ranking 

*90% of the RAG failures are due to chunking and retrieval not the model*

**Chunking strategies**  
Naive chunking is the wrong way of chunking like fixing the chunk size to 200-500 tokens or something like this. The problems can be meaning can be broken, sentences can be cut, embedding becomes weak. 

*Semantic chunking is the right way to do it*

Split by, 
- Paragraphs
- Headings
- Sections
- Meaning boundaries

Chunk should answer , Can this chunk answer independently?  

**Overlapping chunks**

We add overlaps like, 
Chunk 1: 200-350 token
Chunk 2: 300-350 token

Because info may sit at boundaries. 

---
**Metadata**
Each chunk should store metadata. 
Eg. 
```
{
  source: "HR_policy.pdf",
  section: "Leave Policy",
  page: 12,
  date: "2024"
}
```
Before vector search we can filter. It improves retrieval. 

---

**WHY Similarity search is not enough?**

Cosine similarity gives top-k chunks where some are loosely relevant and some are very relevant. 

So we need **re-ranking**.

---
**Re-Ranking** 

After retrieving top 10 chunks, 
Use a small model to answer which chunk answers the best to the question. 
This improves answer quality. 

---
**Hybrid Search** 
Sometimes embeddings miss exact terms. Hence we use keyword search + vector search. 

---

**When RAG gives wrong answers?**  

| Symptom               | Root Cause             |
| --------------------- | ---------------------- |
| Irrelevant answer     | Wrong chunks retrieved |
| Partial answer        | Chunk split badly      |
| Model ignores context | Prompt bad             |
| Too long context      | Token overflow         |
| Conflicting chunks    | Need reranking         |

---

**Ideal RAG** 

Docs
 ↓
Semantic chunking + overlap
 ↓
Embeddings
 ↓
Vector DB (+ metadata)
 ↓
User query
 ↓
Metadata filter
 ↓
Vector search (top 10)
 ↓
Reranker (top 3)
 ↓
Structured context prompt
 ↓
LLM answer

---

**RAG Prompt Design**  

When a model uses its memory instead of using the chunks retrieved then the probability of choosing the answer from the memory is higher than the probability of choosing from retrieved chunks. So we must have to shift probabilities. 

**A Good RAG Prompt has 4 parts**
- Roles
- Rules
- Context
- Questions

1. **Role**
It defines the role of RAG system. Eg. You are a compliance checker. You answer only from the retrieved policy chunks.

2. **Rules**
Example rules,
- Answer only from the context
- If answer not present, say "Not found in document"
- Do not use prior knowledge
- Quote relevant lines

3. **Context**

Bad
``` [big text blob] ```

Good
```
Document: HR Leave Policy
Section: Intern Leave Rules
Content:
"...text..."
```

4. **Always keep question after the context** - LLM's give more weight to the recent tokens.

----

### Sample RAG Prompt

```
You are an assistant that answers strictly from the given document.

Rules:
- Use only the provided context
- If not present, say "Not found in document"
- Cite the relevant sentence

Context:
[Chunk 1 with title]
[Chunk 2 with title]
[Chunk 3 with title]

Question:
...
```
---









