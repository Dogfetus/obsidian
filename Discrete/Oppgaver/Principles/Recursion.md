As with [induction](Discrete/Oppgaver/Principles/Induction), we have two steps for recursion:
- Define the function initially for 0 (or the star value)
- Define the function for the successor based on the value of the previous number(s)

A recursive definition has two parts: 
- initial definition
- and recursion.

we use [induction](Discrete/Oppgaver/Principles/Induction) when we want to compare an explicit and a recursive definition. 

Recursive example:

(part 1):
Initial: 
id(0) = 0

(part 2):
recursive:
id(k+1) = id(k) + 1

We recognize the function it defines: 
id(n) = n

This is the recursive definition.
Recursive definition (as i understand it), is about finding the formula for finding the next element using the previous element. F.eks:

we start with the function : $s_n = 42^n$
as a recursive definition we do it like this:

initial would be $s_0 = 42^0$ (this would not have any effect so we continue)
initial(2) would be $s_1 = 42^1 = 42$ if we try more we get:
$s_2 = 42^2 = 42 \cdot s_1$
$s_3 = 42^3 = 42 \cdot s_2$
$s_2 = 42^4 = 42 \cdot s_3$



Then we can use [inductiive](Discrete/Oppgaver/Principles/Induction) proof ???:
- prove for inital value (0): id(0) = 0 (definition)
- assume for k: id(k) = k (recognized function)
- prove for k+1: id(k+1) = id(k) + 1 = k+1 

This proves the id(n) = n

