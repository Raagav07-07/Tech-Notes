# Foundations
## Linear Algebra
### Why do we need linear algebra for LLM?
LLM do not understand text instead they understand only numbers arranged in vectors or matrices.
Text->Numbers->Math->Output

---
## 1. Vectors
---
Vectors are the ordered list of numbers. Eg.`[12, 32, 13]`
In Generative AI, it represents meaning. For example: cat-> `[2,3,-2]` Similar meaning words -> Similar vector
These vectors are the one's stored in the rag database.
We can do cosine similarity on the vectors for retreival in RAG.
In short: "It is the numerical representation of semantic meaning"

---
## 2.Matrices
---
A matrix is a collection of vectors.Eg.`[[1,4,3],[1,-2,-3.2]]`
Sentence -> Vector, Collection of Sentence -> Document -> Matrices.

---
## Dot Product
---

(A.B) = A1XB1 + A2XB2 + ..
Dot Product gives us how much the vectors align. If the relevance score is high then it the vectors are in same directions if not then they are unrelated.
For example: An animal is walking on the road. It needs help. Here logically the 'It' should be animal not road this should be understood by the LLM.
Here for example: It->`[1,0]`, Animal->`[1,0]`,Road->`[0,0]`. Then the dot product of 'it' with 'animal' and 'it' with 'road' are given by,
[(1x1)+(0x0)] = 1 (Animal) , [(1x0)+(0x0)] = 0 (Road). So the animal has more relevance.
This used in Attention mechanism. Token relevance is decided here.

---
## Cosine Similarity

It checks angle between the vectors.

|Cosine value|Meaning|
|------------|-------|
| 1.0 | Same |
| 0.8 | Similar |
| 0.0 | Unrelated |
| -1.0 | Opposite |

Why cosine similarity? Because vector length is not matter here. 
Why not eucleidean? Sentence length changes magnitude. Cosine does not take magnitude. It compares meaning not size.

---
# ALL TOGETHER
---

Text -> Embedding model -> Vector -> Stored in matrix -> Dot Product / Cosine Similarity -> Find Relevance


---
## How embedding models are trained ?
Embedding models are trained by predicting words from context. During training, words and sentences that appear in similar 
contexts get their vectors adjusted in similar directions. Over billions of examples, this causes semantically similar text 
to cluster together in vector space, allowing similarity to be measured geometrically using cosine similarity.








