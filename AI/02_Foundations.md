# Probability and Next Token

*An LLM is a probability engine that predicts the most likely next token.*
---
1. **LLM'S do not generate sentences , they generate the next token**
   They generate one token at a time. For ex: "The forest fire is ____", the llm will asks for what token is most likely to come next?
   For eg: If the probability distribution is like the below,
   - dangerous -- 0.52
   - spreading -- 0.31
   - movie -- 0.0001
   then the llm will choose from this probability distribution.
It chooses based on the probability not on facts.
---
2. **Where do these probability comes from?**
   From Training. They see different sentences stating "The forest fire is spreading","The forest fire is dangerous" often.
   High probability means they often appeared in the training
   `Probability!=Truth`
---
3. **Why LLM always outputs something?**
   The model always output something even if it is,
   - Question is wrong
   - Data is missing
   - Answer does not exist
   Because the softmax forces the probability to 1. So one token must win.
  Softmax forces a choice among tokens, not among truth values.
  Lets see an example,
  Que: `Is 2027 is in the future?`
  Now the model is not choosing between true or false instead it is choosing between the tokens like "yes", "no", "it", "will", "cannot" so the probability space is what is the best next word?
  the softmax will make the probabilityn sums to 1.
  for eg in this case -> future -- 0.91, past -> 0.08, present -> 0.01
  why "future" wins the probability?
  In training it might see that year>present year then it is future and also like  "2027 is in future", "2030 will be the future".
---
4. **Hallucinations**
   Hallucination is not a bug — it’s a consequence of probability.
   Hallucination happens when:
   - The training data is sparse
   - Or the pattern is weak
   - Or multiple completions are equally plausible
---
5. **What is softmax?**
   - Takes raw scores
   - Converts them into probabilities
   - Makes them sum to 1
---
6. **Temperature controls randomness**
   Temperature | Behaviour
   ------------|----------
   Low (0-.03) | Safe,Det
   Medium (.7) | Balanced
   High (1+) | Creative, Risky
---
**CONNECTING TO RAG**
Without RAG:
Model guesses from training data

With RAG:
Model predicts tokens conditioned on retrieved facts

So hallucination drops.
---

  
    




    
