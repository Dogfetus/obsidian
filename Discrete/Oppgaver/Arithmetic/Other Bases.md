we can also calculate numbers in different bases:
```c++
std::string represent(unsigned int n, b) {
	// just return 0 if that is entered
	if (n==0) 
		return char(0)

	// buffer
	std::string rep = "";

	// calculate the number in given base
	for (unsigned int h = n; h > 0; h/=b) {
		rep = rep + char(n%b);
	}

	return rep;
}
```

the way this works is by taking an initial value `n` and dividing it by the target base. this will give us a remainder. this remainder will be the first digit (the right most digit). for example:

for base 8:
```c++
(base 10): 2022 -> (base 8):

// 2022 % 8 = 6
2022 -> 252

// 252 % 8 = 4
252 -> 31

// 31 % 8 = 7
31 -> 3

// 3 % 8 = 3
3 -> 0
// since we reached 0 we stop here

// thus the final result will be these remainders written next to eachother:
(base 10): 2022 -> (base 8): 3746
```

for base 13:
```c++
(base 10): 2022 -> (base 13):

// 2022 % 13 = 7
2022 -> 155

// 155 % 13 = 12 = C
155 -> 11

// 11 % 13 = 11 = B
11 -> 0

// now we had digits which were higher than 10. Thus we had to convert them to characters
(base 10): 2022 -> (base 13): BC7
```

for base 7:
```c++ 
(base 10): 8 -> (base 7): 11

(step 1):
// 8 % 7 = 1
8 -> 1

(step 2):
// 1 % 7 = 1
1 -> 0

// since we reached 0 we stop
(result): 11
```

for base 12:
```c++
(base 10): 8 -> (base 12): 8

(step 1):
// 8 % 12 = 8
8 -> 0

//since we reached 0 we stop
(result): 8
```

