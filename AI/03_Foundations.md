# Loss & Training

**How a model learns**  
A model learns only through minimizing the loss
---

**What is loss?**  
loss =  How wrong the model's predictions was (numerically wrong)
Eg.  
The forest fire is ___. True Next token is "dangerous".
but the probability distributions looks like the following,
"dangerous" -> 0.40
"spreading" -> 0.30
"large" -> 0.20  
Here even though "dangerously" is scored highest but it was not confident enough. Hence loss is high. So it penalises the low confident scores. 

---
**Why cross entropy loss is used?**
- High confidence + corrent answer -> low loss
- Low confidence + correct answer -> high loss
- Low confidence + wrong answer -> very high loss
---

**Training loop**
Input text -> Predicts next token -> Calculates loss -> Backpropagate -> Updates weight -> Repeat

---
**What backpropagation does?**  

It answers which parameters contributed most to the mistake and it will nudge those,in the direction that would reduce the mistake next time.

---
**Why small updates matter?**  
If we update too much,  
  - the model forget the old parameters
  - becomes unstable
If we update a little,
  - learning is slow
*This is controlled by learning rate* - Lower the learning rate, little the update takes place.
---
**How meaning emerges?**  
This is where embeddings comes to play.  
During training,  
- Tokens used in similar context
- Reduce loss in similar way
- Their vectors get nudge in similar direction
Over billions of step, Structural Meaning emerges.
---
**Generalisation**  
Generalisation means that the model performs well on unseen data.  
This happens because:
- Language patterns repeat
- Grammar and semantics are consistent
- Loss optimization compresses patterns
The model does pattern compression, not memorization (ideally).
---
**Overfitting**  
The model performs well on training data but poorly performs on new data.  
How can we reduce it? Large dataset, Regularisation, Early stopping, Validation check.  

---
## CONNECTING TO REAL SYSTEMS
In RAG:  
- Model still predicts tokens
- But loss-trained embeddings retrieve facts
- Context reduces loss during generation
In Agents:
- Tools reduce uncertainty
- Fewer hallucinations
- Lower effective loss

```
Training = Loss minimization
Learning = Weight updates
Meaning = Emergent structure
Knowledge = Statistical patterns
Behavior = Probability shaping```







