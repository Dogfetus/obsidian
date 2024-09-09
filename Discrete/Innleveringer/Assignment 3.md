Oppgave 1:
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


Oppgave 2:

make a grammar of the following: $a^n b^m c^o d^m e^n$

we know that a grammar is defined by (terminals, non terminals, starting point, rules)
thus we first find the terminals and non terminals:
we realize that there are as many a's as e's since both are to the nth power, so we first get A -> aAe | $\epsilon$. then we realize the same for b and d to the mth power, so we get B -> bBd | $\epsilon$. Then we to the same for the last one (c to the oth power). C -> cC | $\epsilon$. Then we define the starting point:
we call this S:
S -> A B C ; where :
A -> aAe | $\epsilon$
B -> bBd | $\epsilon$
C -> cC | $\epsilon$
These are the rules that define the grammar. Now we can create as many instances of a's b's c's d's and e's, as we want.