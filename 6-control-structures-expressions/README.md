## 6 Control Structures

### Jumps
- `goto`, `break`, `continue`

### Branches
- `if`, `switch`

#### Switch

```cpp
int number = 1;
switch(number) {
	case 0: {
		// option a 
	} break;
	case 1: {
		// option b
	} break;
	default: {
		printf("Error!");
	}
}
```

Performance: Compiler can generate:
- jump table: no comparison needed
- binary decision tree: optimized if..else with binary search
- worst case: same as if..else

### Loops
`for`, `while`, `do..while`

## Expressions

Every expression is a valid C++ statement. Including:

```cpp
a = b = 10 + 2;
a = 10 + 2;
10 + 2;
2;
```

### Expression Short-Cutting

```cpp
int a = 0, b = 0;
if(++a || ++b){
	printf("True!");
}
printf("a: %d, b: %d", a, b);
```

- first sub-expression is already true
- so second sub-expression of `||` doesn't have to be executed
- can be very useful e.g. `if(player && player.canAttack)`
- can also be unintended

## EXERCISE: Triangle
- Print this Triangle to the Screen:

```
& & & & & &
& & & & &
& & & &
& & &
& &
&
```

## EXERCISE: Swap Values of Two Variables
- Assign 50 to variable named `a`
- Assign 25 to variable named `b`
- Swap the values of `a` and `b`

## EXERCISE: Nim
- Port your C# Code to C++
  - Shouldn't be too difficult!