can be done in two ways:
standard Euclidean algorithm:
```c++
unsigned gcd(unsigned a, b) {
	// swap them
	if (a > b) {
		a = a ^ b
		b = a ^ b
		a = a ^ b
	}

	while (a!=0) {
		h = b % a;
		b = a;
		a = h;
	}
	return b;
}

//recursive version:
unsigned gcd_rec(unsigned a, b) {  
	if (a>b) 
		return gcd_rec(b, a);  
		
	if (a==0) 
		return b;  
		
	return gcd_rec(b%a, a);  
}
```

This works by deviding the largest number by the lower number, then doing the same for the new number (the rest), and so on.


Subtraction-based euclidean algorithm:
```c++
unsigned gcd(unsigned a, b) {
	// swap them
	if (a > b){
		a = a + b 
		b = a - b
		a = a - b
	}
	
	while (a!=0) {
		h = b - a;
		b = a;
		a = h;
	}
	return b;
}

// recursive version:
unsigned gcd_rec(unsigned a, b) {  
	if (a>b) 
		return gcd_rec(b, a);  
		
	if (a==0) 
		return b;  
		
	return gcd_rec(a, b-a);  
}
```