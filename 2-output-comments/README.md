# 2 Basics

## Comments

### C-Style Comments

```c++
/*
 * multi-line comment
 */
```

Careful: Nesting Comments does not work!
```c++
/*
void foo() {
	int a = 3;
	int b = 2;
	/* int c = 5; */
	return 5;
}
*/
```

### Cpp-Style Comments
```c++
// single-line comment
int number = 12; // span the rest of the line
```

## Output

### Old, C Style

```c++
#include <cstdio>
```

#### Write Line: Puts

Prints the given string and a newline to the console.

```c++
puts("Hello, World.");
```

#### Write: Printf

```c++
printf("Hello, World.");
```

#### Write Format: Printf

```c++
printf("Ten %d, Twenty %d, Thirty %d", 10, 20, 30);
```

### New, C++ Style

```c++
#include <iostream>
using namespace std;
```

```c++
cout << "Hello, World." << endl;
cout << "Ten " << 10 << " Twenty << 20 << " Thirty " << 30 << endl;
```
