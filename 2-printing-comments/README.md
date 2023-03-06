# 2 Basics

## Comments

### C-Style Comments

```cpp
/*
 * multi-line comment
 */
```

Careful: Nesting Comments does not work!
```cpp
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
```cpp
// single-line comment
int number = 12; // span the rest of the line
```

## Output

### Write Line: Puts

Prints the given string and a newline to the console.

```cpp
puts("Hello, World.");
```

### Write: Printf

```cpp
printf("Hello, World.");
```

### Write Format: Printf

```cpp
printf("Ten %d, Twenty %d, Thirty %d", 10, 20, 30);
```