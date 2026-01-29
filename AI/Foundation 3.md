# Tokenization, Context window & Why prompts break? 

*LLM's read tokens within the context window*

---

**Tokenization**  
Before the model sees the text, it is break down into tokens.  
Token ! = Word  

For eg. "manageable" -> ["man","age","abl","e"]  
Models use Byte pair encoding (BPE)  
Json, codes, numbers are token heavy. 

---

Why tokens exist?   
Because if we use words vocabulary will be larger and unknown words break the system.  

---

**Context Window**  

Maximum numbers of tokens that the model can see at a once. Limits can be 8k, 16k, 200k and so on.  

---

**Why prompts break?**  
when token limit exceeds the model will silently drop the earliest token.  
so important instructions at top get ignored.  

---

**Why RAG required chunking?**  

Since we cannot feed a 200 page pdf all at once, Hence we chunk those documents, embed each chunks and retrieve the top relevant ones.  

- Chunking exist because of token limit

---
**Chunk Size**  
- If the chunk size is small then retrieval will be weak, loses meaning
- If it is too large, It will doesnt fit into windows, Waste tokens
---
*Token = Money* , More tokens higher cost, higher latency and lower reliability. 
**Efficient prompting = Token efficiency**

---

**Real Failures**
- Prompts work initially then degrade
- RAG returns irrelevant chunks
- Instructions get ignored
- Chatbots contradict earlier messages

---

```

Text → Tokens
Tokens must fit inside context window
Window is the model’s only memory
Overflow = silent forgetting
Chunking & summarization = survival techniques
```

