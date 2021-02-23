# generic-print
Convenient generic print() for C

Other languages have nice print/log/write functions but in C you are at mercy of inconvenient `printf(format...)`. It took me an entire day reading C documentation and playing with ideas to implement this. The trick was to use builtins that check types, variadic macros and variable array initializers.

Just `#include "print.h"` and use `print()`.

#include "print.h"

```c
int main() {
	// basic usage
	print("number:", 25, "fractional number:", 1.2345, "expression:", (2.0 + 5) / 3);

	// variables can be passed
	char *s = "abc";
	void *p = main;
	long l = 1234567890123456789;
	print("string:", s, "pointer:", p, "long:", l);

	// some basic C arrays are supported
	int x[] = { 1, 2, 3 };
	char *args[] = { "gcc", "hello.c", "-o", "hello" };
	print(x, args);

	// char/byte are handled with extra love
	unsigned char byte = 222;
	char ch = 'A';
	print(byte, ch)

	// you can setup your own colors
	// arguments are: (normal, number, string, hex, fractional)
	// defaults are (-1, 4, 1, 2, 5)
	__print_setup_colors(249,236,239,244,232);

	// or disable colors completely
	__print_enable_color = 0;
}
```
