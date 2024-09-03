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

then we use inductive proof:
- prove for inital value (0): id(0) = 0 (definition)
- assume for k: id(k) = k (recognized function)
- prove for k+1: id(k+1) = id(k) + 1 = k+1 

This proves the id(n) = n

