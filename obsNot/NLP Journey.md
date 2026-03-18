# NLP Journey
This note documents my NLP learning journey starting from fundamental concepts then move to more advanced knowledge such as complex models and real-world application. The purpose of this notebook is not only to record theory or formula i learnt, but also share the insights i gained during the learning process.  

Before start to learn NLP, we should discuss about the question below about NLP:

---

**What are the things in NLP?**  
[[Text Data](C:\Users\timot\OneDrive\Dokumen\Obsidian Vault\obsNot\NLP Learning\Text Data.md)]  
Before hopping into NLP, we have to know that data is more abundant than before in today's digital age. From articles to social media posts, vast amounts of information are generated in very short time. Text data is one of those information, plays a certain role in machine learning implementation. 

Vocab size
 - Number of unique words in a corpus
 - Example:
	> Document:  
		"I like eggs  
		I hate cats  
		I like eggs and I hate cats"  
		
	  There are 6 unique words ⇒ Vocab size = 6  
	  **Addition**: If we do vectorization by counting → There are 3 rows and 6 unique words, so there will be 6 vector with 3 as the length.
		
Normalization
- Needed because text document can contain many words. In a corpus, there are many **long** or **short** text document. 
- Normalization:  
	1. L2 Norm - 1  
		$\hat{x} = \frac{x}{| | x| |_{2}}$ → $||x||_{2} = \sqrt{\sum_{i=1}^{v} x^{2}}$   
	2. Divided by Sum  
		$\hat{x} = \frac{x}{\sum_{i=1}^{v} x_{{i}}}$ , $\sum_{i=1}^v x_{i} = \sum_{i=1}^v |x_{i}| = ||x||_{1}$ 

Why we need vector for NLP?
- Computer needs numerical representations to understand and process data → Text data is converted into numeric values in form of vector
- Vector in NLP, capture semantic (meaning), syntactic structure, and contextual relation of the text. 

## Tokenization
![Tokenization]

