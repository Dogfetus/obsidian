
To find the least common multiple, we can use the [gcd](Discrete/Oppgaver/Arithmetic/Greatest%20common%20divisor) and the multiplication of a and b by explained in [theorem](https://uia.instructure.com/courses/16240/files/2639182?module_item_id=627022) (page 47).
```c++
// simplest version:
// using gcd:
unsigned int lcm(unsigned a, b) {
	if (a < 0)
		a = -a;

	if (b < 0)
		b = -b;

	return (a * b) / gcd(a, b);
}
```


we can also do this by finding all the prime numbers that make up the two different numbers, and multiply all of them together:
```c++
unsigned int lcm(unsigned a, b) { 
	std::vector<unsigned int> prime_a = find_prime_numbers(a);
	std::vector<unsigned int> prime_b = find_prime_numbers(b);

	unsigned int _lcm_ = 1;

	for (unsigned int prime : prime_a)
		_lcm_ *= prime;
		
	for (unsigned int prime : prime_b)
		_lcm_ *= prime;

	return _lcm_;
}
```
