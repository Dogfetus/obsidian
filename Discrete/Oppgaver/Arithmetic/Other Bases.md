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

