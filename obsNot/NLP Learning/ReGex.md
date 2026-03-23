# Regex
**What is Regex?**
⇒ Basically, regex is an acronym for **Regular Expression**  
⇒ A string of characters to search a certain pattern in a text. It is especially used to find or replace words in texts.  
⇒ For example, we want to search files using .pdf extension:  
	We have to type following expression → ^\w+\\.pdf$

**Basic of Regex**  
In regex, we can find a specific word by write it directly. It is similar to normal search process.  
For instance, we want to find a word 'regex' or 'processing' → Just write `/regex/g` or `/processing/g`  
**To search or find any character in the text**  
Use → / . /g  

## Using Brackets
**To find a set character**  
Use square bracket `[]` with the characters inside the bracket. For an example, we wanna find 'far', 'fir, 'fur, so we can write `/f[aiu]r/g`  
**To negate a character set (we want to do exception for some character)**  
Use `^` inside the square bracket, before the character set we want to except. For an example, instead of looking for 'far', 'fir', 'fur', we wanna negate them. So, we write `/f[^aiu]r/g`  
**To search 
