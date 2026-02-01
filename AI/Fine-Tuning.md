**Fine-Tuning**  

*Fine tuning doesn't add knowledge. It changes the behaviour.*  
Fine tuning = continuing training on a smaller dataset 
 
Training loop is the same but now the data is domain specific, behavious specific, style specific.  

**Why full Fine-Tuning is rare today?**  
LLM's have billions of parameter so updating all of them is expensive, takes so much GPU, overfitting, forgetting the base knowledge.  

**PEFT-Parameter Efficient Fine Tuning**  
Don't change the whole model add small trainable parts.  

**LoRa - Low Rank Adaptation**  
- Freeze model weights  
- Add small low rank matrix 
- Train only those  

So instead of changing W(huge matrix), we learn W + (AXB). Where A and B are small.  
Why this works?  
Because most knowledge is in base model i.e already in W. You only need small adjustments to tone, style,, behaviour, domain preference.  

**QLoRa**  
QloRa adds quantization(compression technique where a bigger models weight is changed from high precision values to low precision values). In result, fine tune big models on small GPU's.  

Failing of fine tuning is that people teach the model new data. This fails because small data, model forgets easily, not scalable, RAG is better.  

Real egs:  
- Make model talk like a doctor
- Make model generate SQL always
- Make model follow strict format
- Make model adopt brand voice
 
```
RAG → gives knowledge
Prompt → shapes response
LoRA/Fine-tune → shapes personality/behavior
```
