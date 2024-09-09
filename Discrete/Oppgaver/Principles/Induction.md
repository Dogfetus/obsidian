we use three steps for inductive proofs:
- prove the property initially for 0 (or the starting value)
- assume the implication condition
- prove the implication consequence

for example:
statement: for all numbers greater or equal to 3, the sum of the previous natural numbers is greater or equal to the number itself
This becomes :

Ɐx ≥ 3 \[ $\sum_{i=1}^{x-1}{i}$ ≥ x\]
or:
Ɐx ≥ 3 \[ $\sum_{i=1}^{x}{i}$ ≥ s(x)\]


1. **First we prove the property initially for the starting value (3):**
$$ 1 + 2 = 3 \geq 3 $$
as we can see this holds true:



2. **Then we assume for x >2:** $$S_{x-1} \geq x$$Which essentially is the same as:
$$Ɐx \geq 3 \,:\,\,\,\,\sum_{i=1}^{x-1}{i} \geq x $$

3. **Then we prove for x+1:**$$\begin{align}
\sum_{i=1}^{(x+1)-1}{i} &= \sum_{i=1}^{x}{i}\\
\sum_{i=1}^{x}{i} &= \sum_{i=1}^{x-1}{i} + x\\
\\ 
\text{We know this from the assumption}&\text{ that: }\\
\sum_{i=1}^{x-1}{i} &\geq x\\
\\
\text{this means we can write it like this:}\\
\sum_{i=1}^{x-1}{i} + x &\geq x + x\\
\\
\text{this means that we know this has t} &\text{o be bigger or equal to the same with 3:}
\\
x + x &\geq x + 3\\
\\
\text{which again have to be bigger than} &\text{ a 1:}\\
x + 3 &\geq x + 1
\end{align}
$$
thus we know that :
	$$\begin{align}
	\sum_{i=1}^{x}{i} &\geq x + 1\\
	&\textbf{Or:}\\
	\\
	S_{x+1} &\geq x + 1
	\end{align}$$



tips:
when working with k + 1 (x + 1 in this case) we are activly trying to find the equation stated in the assumption with just k. And calculating the rest based off of this.