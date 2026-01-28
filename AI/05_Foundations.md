# Hallucinations, Grounding 

*An LLM hallucinates when it has to predict the next token without any reliable context*

---

**Hallucination** - Statistically plausible text without any grounded truth.  

**When it happens the most?**  

| Situation               | Why                          |
| ----------------------- | ---------------------------- |
| Asking for recent facts | Not in training data         |
| Asking for rare facts   | Weak pattern learned         |
| Long prompts            | Important context pushed out |
| No grounding documents  | Pure probability guessing    |

**Why prompt engineering cannot fix this?**

If the prompt says, "If you do know the answer, say no". This is still in the token competing step where if the answer has higher probability than this then this will be refused.  

*Prompt influence probability , they do not add knowledge*

---

**What grounding actually means?**  
Providing real, external information inside the context window before generation.  
Question → retrieve facts → model predicts using facts

---

**How RAG works?**  
- Convert documents to embeddings
- Store in vector DB
- Question → embedding
- Cosine similarity retrieves relevant chunks
- Chunks placed inside context
- Model predicts tokens using those chunks

**This is how tools and agents reduce the hallucinations.**

---

**Why embeddings are essential?**  
  Finding the relevant text even if wordings differ.  

---

```
Hallucination is a property of pure language modeling.
Grounding turns it into knowledge modeling.
```
