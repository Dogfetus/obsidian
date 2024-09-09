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