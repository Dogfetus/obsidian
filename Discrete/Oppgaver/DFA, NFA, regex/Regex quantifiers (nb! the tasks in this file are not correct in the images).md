For these kind of questions:
# Lecture 4:
### task:
![[Pasted image 20241015223519.png]]
### answer:
![[Pasted image 20241015234319.png]]
{H, Q}, {V}, {N}, {F}, {C}
You should continue the equivalence checks until you get two identical equivalences, but i realized i would get this here, since the only option i had to change something, would be to split the {H, Q}, which would not work, and result in a duplicate equivalence check.






## task:
![[Pasted image 20241015223715.png]]
### asnwer:
In this task you need to look at the picture and determine the different terminals and nonterminalsa swell as startingpiont and rules. 
terminals => all the labels on the arrows
non-terminals => all the lables on the nodes
startingpoint => the node with the empty arrow pointing to it
rules => provided by the arrow pointing out from each node with its corresponding terminal and ending non-terminal. For double lines they can also just stop as $\epsilon$.










### Task:
![[Pasted image 20241015223331.png]]

### answer:
![[Pasted image 20241015220222.png]]





# Lecture 5:
### Task:
![[Pasted image 20241015235020.png]]
### answer:







### Task:
![[Pasted image 20241015234527.png]]
### answer:






### Task:
![[Pasted image 20241015223449.png]]
![[Pasted image 20241015223504.png]]
### answer:










### Task:
![[Pasted image 20241015224032.png]]
### answer:
For this task the weaker an equation is, is determined by how many possible solutions it has. This means that x = x would be the weakest, since it holds true for every single possible value for x. This is followed by x $\neq$ 1, since this holds true for every single value for x except 1. Then at medium is the same as shown in the picture, since x can be three different values. Thereafter, the quadratic polinomial equation is placed correct at strong since it has two different values for x. Then we top it all of with 6x = 24 as the strongset, since x can only be one value: 4. 
Final result would look like this:
- strongest: 6x = 24                       : 1 solution
- strong: $x^2-12x+32 = 0$           : 2 solutions
- medium: $x\in \{4,8,12\}$                : 3 solutions
- weak: $x\neq1$                                 : infinite - 1 solutions
- weakest: x = x                             : infinite solutions









# Lecture 6:
### task:
![[Pasted image 20241015221722.png]]
### answer: 
here (7, 5) means essentially (x, y) so if xRy ((x, y) in R) then (y, x) must also be in R (since symmetric) but this is antisymmetric, so we know that this is only true when y = x, such that we only get (x, x) in R.


### task:
![[Pasted image 20241015225028.png]]
### answer:
**false**: reflexive: if x $\cdot$ x $\neq 0$ for ***ALL*** values of x                                                
**true**: symmetric: if $x \cdot y \neq 0$ then this should also be true for: $y \cdot x \neq 0$         
**false**: antisymmetric: if $x \cdot y \neq 0$  and $y \cdot x \neq 0$, then $x = y$.
**true**: transitive: if $x \cdot y \neq 0$ and $y \cdot z \neq 0$, then $x \cdot z \neq 0$






### Task:
![[Pasted image 20241015225902.png]]
### answer:
In this task we take modulo 12(given) of each number in S:

- −14≡10(mod12)
- −11≡1(mod12)
- −10≡2(mod12)
- −9≡3(mod12)
- −4≡8(mod12)
- −1≡11(mod12)
- 0≡0(mod12) 
- 2≡2(mod12) 
- 3≡3(mod12) 
- 4≡4(mod12) 
- 6≡6(mod12) 
- 8≡8(mod12) 
- 9≡9(mod12) 
- 10≡10(mod12)
- 12≡0(mod12)
- 14≡2(mod12)
- 15≡3(mod12)
- 18≡6(mod12)
- 19≡7(mod12)
- 20≡8(mod12)

Then we group the numbers by their reminder:
- **Remainder 0**: {0,12}
- **Remainder 1**: {−11}
- **Remainder 2**: {−10,2,14}\
- **Remainder 3**: {−9,3,15}
- **Remainder 4**: {4}
- **Remainder 6**: {6,18}
- **Remainder 7**: {19}\
- **Remainder 8**: {−4,8,20}
- **Remainder 9**: {9}
- **Remainder 10**: {−14,10}
- **Remainder 11**: {−1}

then we get the final answer:
{{0,12},{−11},{−10,2,14},{−9,3,15},{4},{6,18},{19},{−4,8,20},{9},{−14,10},{−1}}


code for this:
```python
import sys
import ast

def compute_equivalence_classes(S, modulo):
    equivalence_classes = {}
    
    # Compute the equivalence classes
    for element in S:
        remainder = element % modulo
        if remainder not in equivalence_classes:
            equivalence_classes[remainder] = []
        equivalence_classes[remainder].append(element)
    
    # Sort the values in each equivalence class and return as set of sets
    return {tuple(sorted(equivalence_classes[key])) for key in equivalence_classes}

if __name__ == "__main__":
    # Get the arguments from the command line
    input_set = sys.argv[1]
    S = ast.literal_eval(input_set)  # Convert the string input to a set
    modulo = int(sys.argv[2])

    # Compute the equivalence classes
    equivalence_classes = compute_equivalence_classes(S, modulo)
    
    # Print the result
    print(equivalence_classes)

```

Works like this:
```bash
python Equivalence_class.py "{-14, -11, -10, -9, -4, -1, 0, 2, 3, 4, 6, 8, 9, 10, 12, 14, 15, 18, 19, 20}" 12

script : Equivalence_class.py 
S : "{-14, -11, -10, -9, -4, -1, 0, 2, 3, 4, 6, 8, 9, 10, 12, 14, 15, 18, 19, 20}"
Modulo : 12
```