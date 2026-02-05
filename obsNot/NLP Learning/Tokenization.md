# Tokenization
Tokenization ⇒ Process **breaking down** a text into individual units called **token**. 

Type of Tokenization:
1. Character-based Tokenization
	- This is the simplest type of tokenization → Text data is split then converted into a sequence of individual char
	- Beneficial for tasks require **detailed-analysis** such as **spelling correction or task with unclear boundaries**
	- Example:  
		Text = "Hello World" → \['H', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd']
	- For english, there will be 26 token for each letter and some token for punctuation and spaces. While in the other language, the amount of token will be different.  
	
2. Word-based Tokenzation
	- Text data is divided into sequence of individual words
	- Works well for languages with clear word boundaries such as spanish, english, and german. 
		**Language with clearword boundaries** ⇒ Morphemes (meaningful units) are added to a root word in a linear and consistent way
	- Can be performed by **split()** function or leveraging RegEx
	- Limitation:
		- Enormous Vocab Size
		- Handling Misspelled
	
3. Subword Tokenization
4. 
5. 