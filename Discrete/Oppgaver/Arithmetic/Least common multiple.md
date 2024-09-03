
To find the least common multiple, we can use the [gcd](Discrete/Oppgaver/Arithmetic/Greatest%20common%20divisor) and the multiplication of a and b by explained in [theorem](https://uia.instructure.com/courses/16240/files/2639182?module_item_id=627022) (page 47).
```c++
// simplest version:
// using gcd:
unsigned lcm(unsigned a, b) {
	if (a < 0)
		a = -a;

	if (b < 0)
		b = -b;

	return (a * b) / gcd(a, b);
}
```

we can also do this 