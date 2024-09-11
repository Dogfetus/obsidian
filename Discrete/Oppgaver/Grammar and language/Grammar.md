**EBNF:**
stands for extended backus-naur form

A grammar is a structure on the form (T, NT, S, R)
where T is an arbitrary set of terminal symbols,
NT is an arbitrary set of nonterminal symbols,
S is the start symbol, s is in the nonterminal symbols ($s \in NT$)
R is a set of rules (each rule is a pair (l, r) which is $\in (T \cup NT$)


apperently:
terminals is the characters you will end up with, the characters that cant be changed to something else.

non terminals are the opposite. Its the characters that are supposed to be swapped for other non terminals, or terminals. (by following the rules)

the rules tells us how we can swap out the non terminals to some new terminals/nonterminals


**grammar and language:**
all grammars define a lanugage.
some languages can be defined with a grammar

so basically wherever you find a grammar, you have a language. But just sometimes when you find a language will you actually find a grammar aswell.


here is an example from grammar to EBNF form: (from handin 3.1)
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
	expression -> term [ { ('+' | '-') term } ] 
	term -> factor [ { ('*' | '/' ) factor } ]
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
# In addition to this the expressionRest is defined recursively (by including expressionRest in itself). This means we can have more than just one expression: f.eks; 5 + 2 - 1 (not just 5 + 2). Thus we also need to include the repeating indicator {}. The same for termRest.

#also:
# we can see from the origianl gramar that:
constant -> constant digit | digit
# this means constant is devined within itself, menaing we get a recursive definition or something like that. We can therefore swap out this notation with the repeating indicator: {} like so:
constant -> digit {digit}
# {digit} itself means "" (noting) or 1, or 12 or 134 etc.
# Therefore we cant write: constant -> digit | {digit}, as this would give us an option to not write a digit at all: "", which is not allowed by the origian grammar.
```




EBNF grammar rules:
Alternatives:  
• We write s-> A|B for s->A and s->B

Kleene closure:  
• We write s->{A} for s->As and s->$\epsilon$

Positive closure:  
• We write s->{A}+ for s->As and s->A.

Optional parts:  
• We write s->\[A\] for s->A and s->$\epsilon$

like this:
![[Pasted image 20240910014102.png]]


