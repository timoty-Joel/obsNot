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
Use square bracket `[]` with the characters inside the bracket. For an example, we wanna find 'far', 'fir', 'fur', so we can write `/f[aiu]r/g`  

**To negate a character set (we want to do exception for some character)**  
Use `^` inside the square bracket, before the character set we want to except. For an example, instead of looking for 'far', 'fir', 'fur', we wanna negate them. So, we write `/f[^aiu]r/g`  

**To search range of character and numbers**  
To find all character in a text data that included in a certain range → Use `[char1 - char2]`  
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
Grouping can be used when we have to search for multiple parts of strings or text data that have different requirements. To do grouping, we can use `/()/g` (parentheses symbol). Parentheses can be used for grouping, matched text, referencing a group, or non-group capturing.  

**Parentheses for Grouping**  
We can use parentheses for grouping then use the group result to reference or apply some rules.  
For an example:  
	Text ⇒ ha-ha, haa-haa  
	Target: haa-haa  
	We can use `/(haa)/g` → To select the matching pattern ( in this case is 'haa' )

**Referencing a Group**  
Beside for grouping, we can utilize parentheses for referencing a group or some groups in a text data. By using parentheses to reference grouping, we can select a group or groups that match with the pattern we set.  
For an example:  
	Text ⇒ ha-ha, haa-haa ha ha-, haa-haa ha-ha, haa-haa  
	Target ⇒ ha-ha, haa-haa  
	We can use `/(ha)-\1, (haa)-\2/g` to reference 'ha' as group 1 and 'haa' as group 2. When we use that regex, we capture 'ha' as group 1 and 'haa' as group 2. So the selected string must be 'ha' with dash(-) and reference for group 1 that is 'ha', same thing for group 2. 'ha ha-' will not be selected because the first 'ha' is without dash and the next one doesn't has 'ha' at the end  

**Not Capturing Group**  
Besides using it for grouping, we can also utilize parentheses to express pattern that is not captured by references.  
For an example:  
	Text ⇒ ha, haa-haa ha ha-, haa-haa ha-ha, haa-haa  
	Target ⇒ ha, haa-haa  
	For this case, we can type `/(?:ha), (haa)-\1/g` to get the matches string. `(?;...)` this parentheses implementation indicates that it's a group without memory, while `(...)\` is group with memory so we can use it as references. Part `(?:ha)` means that we group 'ha' but we won't use it as reference. Part `(haa)-\1` means that we use 'haa' as group 1 and use it again after dash sign (it would be haa-haa(\1)).

## Alternation  
Alternation allows to specify an expression that can be different expressions. It is works similar with brackets '\[ ]'. What differs it from bracket is bracket usage works on character level while alternation works on expression level.  
For an example:  
	Text ⇒ cat rat dog mouse chicken leg  
	Target ⇒ cat rat dog leg  
	To get specified target,  we can use `/(c|r)at | dog | leg/g`. The expression allows us to select all the specified text such as cat, rat, dog, and leg.  

## Escape Character  
Escape character can be used when we wanna write some special character(**metacharacter**) in regex. Escape character tells the engine to treat those metacharacter as a literal character.  
**Metacharacter in Regex**: 