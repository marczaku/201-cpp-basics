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

## Variables

> In terms of programming language, a variable is a location in the computer's memory where we can store data. The value of this data can be changed during the execution of a program. Each variable has a unique and meaningful name which is known as an identifier.

### Declaration

```cpp
int health;
int x, y, z;
```

#### Global

```cpp
int health;
int main() {

}
```

#### Local

```cpp
int main() {
	int health;
}
```

#### Naming Rules
- uppercase alphabets (A to Z), lowercase alphabets (a to z), numbers (0 to 9), and underscore (_)
- first letter of an identifier must be an alphabet or an underscore. (not a number)
- case-sensitive
- cannot contain white spaces or special characters
- cannot use keywords as identifiers

### Assignment Operator
```cpp
int a;
a = 5;
```
- right-associative (executes right to left)

Can be sequenced:
```cpp
int a, b, c;
c = b = a = 30;
```


### Initialization

Assigning a value to a variable for the first time.

```cpp
int health = 100;
int minHealth = 0, maxHealth = 100;
```

### Scope

Within File

```cpp
// A.cpp
int a;
```

```cpp
// main.cpp
int main() {
  // a = 5; NOT VALID
}
```
Below the line where it was declared

```cpp
// a = 5; NOT VALID
int a;
a = 5; // OK
```

Within enclosing Curly Braces

```cpp
{
  int a;
  a = 5; // OK
}
// a = 5; NOT VALID
```

Must be unique within Scope

```cpp
int a; // OK
{
  int a; // OK

  // int a; NOT VALID
}
```

### Constants

```cpp
const int the_answer = 42;
```

## Data Types

### Primitive or fundamental data types
Primitive data types are predefined data types. These are:

- `int` (and other numeric integer data-types)
- `float` (and other numeric floating point data-types)
- `bool`
- `char`
- `void`

### Derived data types
Data types that are derived from primitive data types are known as derived data types. These are:

- Function
- Arrays
- Pointers
- Reference

### User-defined data types
Data types that are defined by the user are known as user-defined data types. These are:

- `struct`
- `union`
- `enum`
- `class`
- `typedef`

## Fundamental Data Types

### Integers

```cpp
// integers can store positive numbers:
int number = 50;
printf("%d", number); // 50
// as well as negative numbers:
number = -1000;
printf("%d", number); // -1000
// rational numbers are truncated:
number = 10.5;
printf("%d", number); // 10
// the limit is at around positive and negative 2.1bln (it overflows):
number = 2'300'000'000;
printf("%d", number); // ca. -2bln
```

#### Different Sizes
- `int`: 4 bytes
- `short`: 2 bytes
- `char`: 1 byte
- `long long`: 8 bytes

The more bytes, the larger the numbers that can be stored:
- 4 bytes: -2.1bln to +2.1bln
- 2 bytes: -65k to +65k
- 1 byte: -128 to +127
- 8 bytes: 2.3e-18 to 2.3e+18

| Type | Signed | Win32 | Unix32 | Win64 | Unix64 | Printf |
|------|--------|-------|--------|-------|--------|--------|
| short | Yes | 2 | 2 | 2 | 2 | %hd |
| int | Yes | 4 | 4 | 4 | 4 | %d |
| long | Yes | 4 | 4 | 4 | 8 | %ld |
| long long | Yes | 8 | 8 | 8 | 8 | %lld |

- The sizes of numeric types depend on the OS and the Compiler
- Your application can behave inconsistent

#### Unsigned
By using the unsigned keyword, you define that your integer can only store positive numbers.
- This allows for twice as large positive numbers using the same amount of bytes

```cpp
char max_char = 127;
unsigned char max_unsigned_char = 255;
```

But if you assign negative numbers, you will end up with really large positive numbers instead:
```cpp
unsigned char max_unsigned_char = -1; // 255
```

| Type | Signed | Win32 | Unix32 | Win64 | Unix64 | Printf |
|------|--------|-------|--------|-------|--------|--------|
| unsigned short | No | 2 | 2 | 2 | 2 | %hu |
| unsigned int | No | 4 | 4 | 4 | 4 | %u |
| unsigned long | No | 4 | 4 | 4 | 8 | %lu |
| unsigned long long | No | 8 | 8 | 8 | 8 | %llu |

#### Guaranteed sizes

```cpp
#include <cstdint>
int8_t a;
int16_t b;
int32_t c;
int64_t d;
uint8_t e;
```

- provides guaranteed sizes

#### Literals

```cpp
int a = 0b11; // binary
int b = 011; // octal
int c = 11; // decimal
int d = 0x11; // hexadecimal
int e = 1'000'000; // improve readability
```

What's the output?
```cpp
printf("%d", 011);
```

Numeric literals per default have the smallest fitting type
  - e.g. 111111 can be stored in `int`

Unless you specify the type explicitly:

```cpp
int a = 1234;
unsigned int a = 1234u;
long a = 1234l;
unsigned long a = 1234ul;
long long a = 1234ll;
unsigned long long a = 1234ull;
```

#### Printf
You can print your integers as:
- `c`haracters
- `o`ctals
- he`x`adecimal
- `d`ecimal

```cpp
	unsigned int a = 65;
	printf("%c, %o, %d, %x", a, a, a, a);
```

### Floating-Point Types

```cpp
float f = .3f;
double d = .3;
long double ld = .3l;
```

- `float` usually 4 bytes
- `double` usually 8 bytes
- `long double` usually same size as `double`

#### Literals

```cpp
float d = 10.3f;
float e = .3f;
float f = 6.3e+12;
float g = 6.3e-12;
```

#### Printf

```cpp
float f = .0003f;
printf("%f, %e, %g", f, f, f);
```

- `%f`: decimal digits
- `%e`: scientific notation
- `%g`: shorter of either above

```cpp
double d = 0.003d;
long double ld = 0.0003l;
printf("%lf, %Lf", d, ld);
```

### Characters

```cpp
char ascii = 'a';
char16_t utf16 = u'a';
char32_t utf32 = U'a';
wchar_t unicode = L'a';
```

#### Escaping

- Newline: '\n'
- Horizontal Tab: '\t'
- Vertical Tab: '\v'
- Backspace: '\b'
- Carriage Return: '\r'
- Alert: '\a'
- Backslash: '\\'
- Single Quote: '\''
- Double Quote: '\"'
- Null Character: '\0'

#### Unicode

```cpp
wchar_t a = '\u0041'; // 4-digit unicode
wchar_t beer = U'\U0001F37A'; // 8-digit unicode
```

But beware! Your Console might not be capable of displaying Unicode Characters with its Default Font!
- still needed for your games, though!
- e.g. in-game chat

#### Printf

```cpp
#include <cstdio>

int main() {
  char x = 'M';
  wchar_t y = L'Z';
  printf("Windows binaries start with %c%lc.\n", x, y);
}
```

### Boolean
Booleans are just integers with two possible values!
- `1` (`true`)
- `0` (`false`)

```cpp
bool b = false; // 0
bool c = true; // 1
```

#### Printf

```cpp
#include <cstdio>

int main() {
  bool b1 = true;  ➊ // b1 is true
  bool b2 = false; ➋ // b2 is false
  printf("%d %d\n", b1, b2); ➌
}
```

### std::byte

Later

### size_t

```cpp
size_t floatSize = sizeof(float);
```

- can store the maximum size of a theoretically possible object of any type (including array)
- which can technically be more than 2.1bln (max value of `int`)
- should be used whenever dealing with sizes of types or arrays

#### Printf

```cpp
printf("float: %zu", sizeof(float));
```

### void

```cpp
void sayHello() {
	printf("Hello!");
}
```

### Eumeration Types

#### Scoped Enum (Modern, C++ Style)

```cpp
enum class ChessPiece {
	Rook,
	Pawn,
	Queen,
	...
};
```

```cpp
ChessPiece rook = ChessPiece::Rook
```

#### Unscoped Enum (Old, C-Style)

```cpp
enum ChessPiece {
	Rook,
	Pawn,
	Queen,
	...
};
```

```cpp
ChessPiece rook = Rook;
```

- Less safe to use, because values can be accessed without preceding type name `ChessPiece::`
- Use for backwards-compatibility with C applications

## Operators

### Operator Types
- Unary `-a`, `+a`, `a++`
- Binary `a+b`, `a*b`, `a<b`
- Ternary `a ? b : c`

### Arithmetic Operators
- `+`, `-`, `/`, `*`, `%`, `++`, `--`
- Post-Increment: `a++`
- Pre-Increment: `a--`

### Comparison Operators
- Two arguments
- Return Type `bool`
- `==`, `!=`, `<`, `<=`, `>`, `>=`

### Logical Operators

- `!`, `&&`, `||`

### Bitwise Operators
- `~`, `&`, `|`, `^`, `>>`, `<<`

```cpp
#include <cstdio>
#include <array>
#include <stdexcept>



enum class AttackFlags : uint8_t
{
    None = 0,
    Stun = 1 << 0,     //  1 0b00000001
    Freeze = 1 << 1,   //  2 0b00000010
    Poison = 1 << 2,   //  4 0b00000100
    Magic = 1 << 3,    //  8 0b00001000
    Physical = 1 << 4, // 16 0b00010000
    Despell = 1 << 5,  // 32 0b00100000
};

int main()
{
    AttackFlags flags{ AttackFlags::None };

    // setting bits:
    flags = static_cast<AttackFlags>(static_cast<uint8_t>(flags) | static_cast<uint8_t>(AttackFlags::Stun));
    flags = static_cast<AttackFlags>(static_cast<uint8_t>(flags) | static_cast<uint8_t>(AttackFlags::Poison));

    // unsetting bits:
    flags = static_cast<AttackFlags>(static_cast<uint8_t>(flags) & ~static_cast<uint8_t>(AttackFlags::Stun));

    // testing for bits:
    if (static_cast<uint8_t>(flags) & static_cast<uint8_t>(AttackFlags::Poison)) {
        // true
        printf("You will see this, since the Poison-Bit is set.");
    }
    if (static_cast<uint8_t>(flags) & static_cast<uint8_t>(AttackFlags::Stun)) {
        // false
        printf("You will not see this, since the Stun-Bit is not set.");
    }
}
```

### Compound Assignment Operators

- `+=`, `-=`, `*=`, `/=`, `%=`, `|=`, `&=`, `^=`, `<<=`, `>>=`

## Input

### Read Character: getchar

```cpp
printf("Do you want to continue? y/n");
char c = getchar();
{ // clear unparsed characters from the buffer
	char _c;
	while ((_c = getchar()) != '\n' && _c != EOF);
}
switch(c){
	/*...*/
}
```

### Read String: fgets

Later

### Read Format: scanf

```cpp
// required to allow using scanf on Windows
#define _CRT_SECURE_NO_WARNINGS
#include <cstdio>

int main() {
    for(int i = 0; i < 5; i++)
    {
        AskAgain:
        // ask for input
        printf("Give me two numbers. e.g. 3, 7\n");
        // declare variable to store the information in
        int num1, num2;
        // read input from the console. Returns the number of successfully parsed arguments 
        int result = scanf("%d, %d", &num1, &num2);
        
        { // clear unparsed characters from the buffer
            char c;
            while ((c = getchar()) != '\n' && c != EOF);
        }

        // if not both numbers were provided, we go back to asking again
        if(result != 2) goto AskAgain;
        // else, we can print the average of both provided numbers:
        printf("The average is %d.\n", (num1+num2)/2);
    }
}
```

## Control Structures

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