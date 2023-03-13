
## 3.1 Variables

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

## 3.2 Data Types

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

## 3.3 Fundamental Data Types

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

| Type | Signed | Win32 | Unix32 | Win64 | Unix64 | Printf | Value Range |
|------|--------|-------|--------|-------|--------|--------|-------------|
| int | Yes | 4 | 4 | 4 | 4 | %d | -2.1bln to 2.1bln |
| short | Yes | 2 | 2 | 2 | 2 | %hd | -32,768 to 32,767 |
| char | Yes | 1 | 1 | 1 | 1 | %hhd | -127 to 128 |
| long | Yes | 4 | 4 | 4 | 8 | %ld | -2.1bln to 2.1bln |
| long long | Yes | 8 | 8 | 8 | 8 | %lld | 9e-18 to 9e+18 |

- The sizes of numeric types depend on the OS and the Compiler
- Your application can behave inconsistent
- Choose the right size for your needs

#### Unsigned
By using the unsigned keyword, you define that your integer can only store positive numbers.
- This allows for twice as large positive numbers using the same amount of bytes

```cpp
char max_char = 127;
char min_char = -128;
unsigned char max_unsigned_char = 255;
unsigned char min_unsigned_char = 0;
```

But if you assign negative numbers, you will end up with really large positive numbers instead:
```cpp
unsigned char max_unsigned_char = -1; // 255
```

| Type | Signed | Win32 | Unix32 | Win64 | Unix64 | Printf | Value Range |
|------|--------|-------|--------|-------|--------|--------|-------------|
| unsigned int | No | 4 | 4 | 4 | 4 | %u | 0 to 4.2bln |
| unsigned short | No | 2 | 2 | 2 | 2 | %hu | 0 to 65535 |
| unsigned char | No | 1 | 1 | 1 | 1 | %hhu | 0 to 255 |
| unsigned long | No | 4 | 4 | 4 | 8 | %lu | 0 to 4.2bln |
| unsigned long long | No | 8 | 8 | 8 | 8 | %llu | 0 to 18e+18 |

#### Guaranteed sizes

```cpp
#include <cstdint>
int8_t a; // 8 bit - 1 byte
int16_t b; // 16 bit - 2 bytes
int32_t c; // 32 bit - 4 bytes
int64_t d; // 64 bit - 8 bytes
uint8_t e; // 8 bit - 1 byte - unsigned
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

## 3.4 User-Defined Data Types

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

### Union
All members of a union share the same address in memory.
- if you change one member
- it also affects the others
- sometimes used for some low-level optimizations
- generally considered "evil"

```cpp
union {
  bool b;
  char c;
}

int main() {
  b = true;
  printf("%d", c); // 1
  c = 0;
  printf("%d", b); // 0
}
```