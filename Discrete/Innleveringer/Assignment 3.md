Oppgave 1:
![[Pasted image 20240910141042.png]]

Answer: 
This task is also done in [[Discrete/Oppgaver/Grammar and language/Grammar|Grammar]]. and looks like this:

```python
G= (

	# this would be the terminals
	{
		‘0’, ‘1’, ‘2’, ‘3’, ‘4’, ‘5’, ‘6’, ‘7’, ‘8’, ‘9’, ‘x’, ‘y’, ‘z’, ‘+’, ‘-’, ‘*’, ‘/’, ‘(’, ‘)’
	},

	# this would be the non terminals
	{
		expression, expressionRest, term, termRest, factor, variable, constant,          digit
	},

	# this would be the starting point
	expression,

	# this would be the rules:
	{
	
		(expression, term expressionRest),
		(expressionRest, ε),
		(expressionRest, expressionRest '+' term),
		(expressionRest, expressionRest '-' term),

		(term, factor termRest),
		(termRest, ε),
		(termRest, termRest '*' factor),
		(termRest, termRest '/' factor),

		(factor, constant),
		(factor, variable),
		(factor, '(' expression ')'),

		(variable, 'x'),
		(variable, 'y'),
		(variable, 'z'),

		(constant, constant digit),
		(constant, digit),

		(digit, '0'),
		(digit, '1'),
		(digit, '2'),
		(digit, '3'),
		(digit, '4'),
		(digit, '5'),
		(digit, '6'),
		(digit, '7'),
		(digit, '8'),
		(digit, '9')
	}
)


#converting this to EBNF form we apperentlt only care about the rules? so:
EBNF:
	expression -> term  { ('+' | '-') term } 
	term -> factor { ('*' | '/' ) factor }
	factor -> constant | variable | '(' expression ')'
	variable -> 'x' | 'y' | 'z'
	constant -> digit {digit}
	digit -> '0' | '1' | '2' | '3' | '4' | '5' | '6' | '7' | '8' | '9'
```

```python
#additional explaination:
#in the original grammar we saw that:
expressionRest -> ε | expressionRest '+' term | expressionRest '-' term
termRest -> ε | '*' factor | '/' factor
#since this can be empty, we dont need them on their own? so we can collapse them into the other terms with the optional indicator: []
# However the expressionRest is defined recursively (by including expressionRest in itself). This means we can have more than just one expression: f.eks; 5 + 2 - 1 (not just 5 + 2). Thus we also need to include the repeating indicator {}. This indicator can also be empty "". so we do not need to add both indicators for optional ([]) and for repeating ({}). The same for termRest. 

#also:
# we can see from the origianl gramar that:
constant -> constant digit | digit
# this means constant is devined within itself, menaing we get a recursive definition or something like that. We can therefore swap out this notation with the repeating indicator: {} like so:
constant -> digit {digit}
# {digit} itself means "" (noting) or 1, or 12 or 134 etc.
# Therefore we cant write: constant -> digit | {digit}, as this would give us an option to not write a digit at all: "", which is not allowed by the origian grammar.
```


Oppgave 2:

make a grammar of the following: $a^n b^m c^o d^m e^n$

we know that a grammar is defined by (terminals, non terminals, starting point, rules)
thus we first find the terminals and non terminals:
we realize that there are as many a's as e's since both are to the nth power, so we first get A -> aAe | B. then we realize the same for b and d to the mth power, so we get B -> bBd | C. Then we to the same for the last one (c to the oth power). C -> cC | $\epsilon$. Then we define the starting point:
In this case, that is A.
A -> aAe | B | ε
B -> bBd | C | ε
C -> cC | $\epsilon$

These are the rules that define the grammar. Now we can create as many instances of a's b's c's d's and e's, as we want.
What we did here is a CFG grammar: [Context-Free Grammar](https://brilliant.org/wiki/context-free-grammars/). 


If we want to write this as a EBNF grammar, we can do it like this:
A -> { 'a' } B { 'e' } | $\epsilon$ ;
B -> { 'b' } C { 'd' } | $\epsilon$;
C -> { 'c' } | $\epsilon$;



Task 3:
This one was actually pretty simple:
we need to go from $1 + 2*3^4 + 5^6*7$ to a tree using the rules:
expression = term { ( '+' | '-' ) term }
term       = factor  { ( '\*' | '\/' ) factor }
factor     = { number '^' } number

We can do it like this:
![[Pasted image 20240910140908.png]]
or like this:
![[Pasted image 20240910140929.png]]
(they are the same).


Task 4:
Find the derivation for the syntax tree:

```txt
	          x  
           /  | \  
        /     |   \  
     /        |     \
  x           |       t  
 /| \         |     / |\  
x |   t       |   t   | f  
| |  /| \     |   |   | |  
t | t |   f   |   f   | |  
| | | |  /|\  |  /|\  | |  
f | f | f | | | f | | | |  
| | | | | | | | | | | | |  
1 + 2 * 3 ^ 4 + 5 ^ 6 * 7
```

To do this we start with the x at the top:
x -> x + t
then we do the same for these values:
x -> x + t
t -> t \* f
thus we get x -> x + t ----> (x + t) + (t \* f)
then we continue:
(x + t) -> (t) + (t * f)
(t * f) -> (f) \* (f)
This means we currently have:
x -> x + t -> (x + t) + (t * f) -----> (t) + (t \* f) + (f) \* (f)
Then we continue:
(t) -> f
(t \* f) -> (f) \* (f^f)
(f) -> (f^f)
(f) -> f
Now we have:
x -> x + t -> (x + t) + (t * f) -> (t) + (t \* f) + (f) \* (f) -----> f + (f \* ( f ^ f ) ) + (f ^ f) \* f
now finally we turn this into numbers and we get:
 f + (f \* ( f ^ f ) ) + (f ^ f) \* f 
 ----> 
 $1 + 2 * 3^4 + 5^6 * 7$
All in all, it should look something like this:
x -> x + t
-> x + t + t \* f
-> t + t \* f + f \* f
->f + f \* f^f + f^f \* f
->1 + 2 \* 3^4 + 5^6 \* 7



Task 5:
find a textual language that does not have any grammar:
easy answer: no such language exists. HOWEVER, is such a language exists, there would potentially exist an infinite amount of languages which had no grammar. But none of these languages would be able to be defined, since they lack the grammar to define such languages. Thus we cannot describe such a language that lacks grammar.


task 6:
![[Pasted image 20240910153224.png]]

To define an EBNF grammar we need to define the following:
terminals, non terminals, starting point and the rules.
We can define this (from the text) as:
terminals:
- string (startingpiont)
- name
- role
- department
- office
- email
- phonenumber

Non terminal: this would be the individual information per terminal

starting point: this would be the starting string?

the rules: 
From the information above we gathered this:
string -> firstname lastname, role, department, office, email, phonenumber
firstname -> Andreas Prinz | Arne Wiklund | Sverre Lunøe-Nielsen
lastname -> Prinz | Wiklund | Lunøe-Nielsen
role -> professor | Universitetslektor | førsteamanuensis
department -> Department of ICT | Department of engineering sciences
office -> A3-082 | A3-067 | C5-085
email ->firstname.lastname@uia.no
phonenumber -> +47 ( 37 23 32 20 | 37 23 34 24 | 984 47 348 | 37 23 37 46 | 469 66 063 )




Extra tasks:

![[Pasted image 20240910154652.png]]

We write 4-tuple grammar like this:
G = 
(
	{ terminals sepparated by comma},
	{ nonterminals separated by comma},
	starting point,
	{
		(rule 1 separated by comma), 
		{rule 2 separated by comma},
		..., 
		{rule n separated by comma}
	}
)

Thus we get the following for this 
G = 