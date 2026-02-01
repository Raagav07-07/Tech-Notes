# Transformers & Attention

*Transformers exists to make a token aware of every other token*

**The original problem** before was the previous models like RNN, LSTM read the text fom left to right and can forgot in the meanwhile when long context. Also it is slow. 

Eg. The animal did'nt cross the road since it was tired.  
RNN struggles to link 'it' -> animal 

Transformer solves this by making every word to look for other words. This is called *self-attention*.

**What happens to a token inside a transformer?**  
Token → Embedding → Self-Attention → Contextual embedding → Prediction  

**Self-Attention**   
Every token asks for which are the tokens that are necessary for me? This is done by using the dot product [[01_Foundations.md]]. 

**Query, Key & Value**   
- Query (Q): what I’m looking for
- Key (K): what I contain
- Value (V): my information  

Attention score= Q.K  

For eg. The animal didnt cross the road since it was tired.  
Here the Q_it is compared with K_animal and K_animal and the dot product between those in which K_animal is higher hence it is mapped to animal.  

**Why this creates contextual embeddings?**  
Earlier we have for a word like fire we have fixed vector but after this we have contextual embeddings that is,  
fire(employee context) -> vector A  
fire(forest context) -> vector B  
Same word different meaning

**Multi-Head Attention**  
One attention focus on grammar other on meaning other on position. Multiple heads=Multiple perspective.  

**Positional encoding**  
Attention doesn't know the order hence we add positional info to the embeddings. This tells model what comes first and the next.  

**Full transformer block**  
Each layer has Multi-head attention, Add & Normalise, Feed Forward neural network, Add & normalise. Repeated many times.  

**Why transformers are perfect for LLM'S?**  
* Handles long context  
* Parallel CPU usage
* Creates contextual embeddings

```
Embeddings give meaning
Attention gives context
Layers refine meaning
Softmax predicts next token
```

---

