## 6 Control Structures

### Branches
- `if`, `switch`

Used to write code that behaves differently depending on some condition

```c++
if(age < 20) {
	printf("not allowed to enter.");
} else {
	printf("welcome in!");
}
```

#### Switch

```c++
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

Performance Benefit: Compiler can generate:
- jump table: no comparison needed
- binary decision tree: optimized if..else with binary search
- worst case: same as if..else

### Loops
`for`, `while`, `do..while`

Used to write code that repeats as many times as a certain condition commands

```c++
while(!gameOver) {
	// [...] continue game
}
```

### Jumps
- `goto`, `break`, `continue`

Used to escape from loops or jump over lines of code otherwise:

```c++
while(!gameOver) {
	// [...] check for errors
	if(errorHappened) break;
	// [...] continue game
}
```

## Expressions

Every expression is a valid C++ statement. Including:

```c++
a = b = 10 + 2;
a = 10 + 2;
10 + 2;
2;
```

### Expression Short-Cutting

```c++
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

## EXERCISE
Ask the user for two numbers. Then print the higher of both.
```
Output: Give me two numbers Separated by Comma. Like "-2,5"
Input:0,-1
Output: The higher number is: 0.
```

## EXERCISE
Ask the user for a character. Return, whether the character is a digit, a lower-case letter, an upper-case letter or a symbol.
```
Output: Give me a character.
Input:0
Output: That's a digit.
Output: Give me a character.
Input:a
Output: That's a lower-case letter.
```

## EXERCISE
Ask the user for a base and a power. Return the base to the given power. Print the full multiplication.
```
Output: Give me a base and a power separated by ^. Like "2^5"
Input:2^5
Output: 2*2*2*2*2=32
```
