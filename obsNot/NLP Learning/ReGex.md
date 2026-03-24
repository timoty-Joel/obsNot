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

**To search range of character and numbers**  
To find all character in a text data that included in a certain range → Use \[char1 - char2]  
For an example, finding character from a to r → `/[a-r]/g`  

To find a certain range of number → Use `/[num1 - num2]/g`  
Example, finding a range of 4 to 12 → `/[4-12]/g`  

## Quantifiers 
**To find an instance that match patterns in any number of times, including zero** → Use `/char*/g`  
For instance, we wanna look for character e that occurs any number of times → `/de*r/g`, so it would be dr, der, deer  
  
**To find an instance that match patterns in one times or more** → Use `/char+/g`  
Finding words that has one or more 'e' between 'b' and 'r' → `/be+r/g`, the result will be 'ber', 'beer', 'beeer'

**To indicate a character is optional** → Use `/char?/g`  
Searching words with or without 'u' inside → `/colou?r/g`, the result will be color and colour  
  
**To indicate a specific limit** → Use `/{}/g`  
	To indicate only exactly a certain time appearance → Use `/{x}/g`, where x is an integer (1, 2, 3, ...)  
	To indicate only a certain time appearance with no upper limit of appearance → Use `/{x, }/g`  
	To indicate only a certain time appearance with upper limit of appearance → Use `/{x, y}/g`  

## Grouping 

