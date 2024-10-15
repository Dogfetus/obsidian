For all the tasks:

![[Pasted image 20240924234512.png]]

1. Find regular expressions to define the following tokens: string constants (such as _"hallo"_ or _'123%#@'_, boolean constants (such as _true_), hexadecimal numbers (such as 0x12ab or 0xABC).

	answer:
	We want to find the regular expressions to define tokens:
	**Strings:**
		For the string constants we are aiming to find all strings and characters which are not 
		wtf:
		`"([^"\\]|\\.)*"|'([^'\\]|\\.)*'`
	**Booleans:**
		For the booleans they can only be of two values, either true or false. Also we want to compare them as a whole word / byte instead of each character as one by themselves. Thats why we also add \\b (word boundary) at the front and back. Then we get the regex for booleans: $\b(true|false)\b$
	**Hexadecimals**:
		For hexadecimals we have to include the 0x at the start, since all the hexadecimal numbers start with 0x. Also every hexadecimal number can be a combination of the numbers 0 - 9, and any character a - f / A - F. Since all the hexadecimal numbers needs to have a digit after the 0c, we add a + indicating that we need at least one digit. We therefore get the following regex for hexadecimals: $0x[0-9A-Fa-F]+$



2. Translate the following regular expressions into one NFA: keywords: 0(12)*, special: 121?, number: [0123]+.


3. Translate your NFA from task 2 to a DFA. Show all important steps.


4. When you translate a regular expression to an NFA, and then to a DFA, and then minimize it - do you get a unique result at the end?


5. Translate the following grammar to an NFA:    A -> aB | bA | b,    B -> aC | bB,    C -> aA | bC | a


6. Translate the following grammar to an NFA: E -> E O E | id, O -> + | - | * | /  
Hint: Check the Chomsky grammar hierarchy.