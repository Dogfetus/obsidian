can be done in two ways:
standard Euclidean algorithm:
```c++

unsigned gcd(unsigned a, b) {
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