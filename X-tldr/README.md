# TLDR

## Like C#
- C++ is very similar to C#
- in fact, C# was derived from C++

## C# Hello World

```csharp
using System;
class Program {
    static void Main() {
        Console.WriteLine("Hello, World!");
    }
}
```

## C++ Hello World

```csharp
#include <iostream>
using namespace std;
void Main() {
    cout << "Hello, World!";
}
```

## C++ and C
- C++ was derived from C and is fully backward-compatible
- For many problems there's two ways of solving it:
  - the "modern", object-oriented C++ way
  - the "classic", low-level C way

## Output
- C# way: `Console.WriteLine($"{3}, {3.2f}, {true}, {'a'}");`
- C way: `printf("%d, %f, %d, %c", 3, 3.2f, true, 'a');`
- C++ way: `std::cout << 3 << ", " << 3.2f << ", " << true << ", " << a;`

## Variables & Data Types
- `bool` is basically just an `int`
  - `true`: `1`
  - `false`: `0`
- `int, char, float, double`: same as C#

## Operators
- same as in C#

## Input
- C# way: `int number = int.Parse(Console.ReadLine());`
- C way: `scanf_s("%d", &number);`
- C++ way: `cin >> number;`

## Control Structures
- Same as in C#
- For `bool`-expressions (e.g. `if(...)`):
  - everything but `0` is considered to be `true`

## Random

### C#

```csharp
// initialize random with random seed:
Random random = new Random();
// get random number between 0 and RANDOM_MAX:
int random = random.Next();
// get random number between 0 and 10:
int random = random.Next(11);
// get random number between 10 and 20:
int random = random.Next(10, 21);
```

### C++

```c++
// initialize seed with current time (for real random numbers):
srand(time(0));
// get random number between 0 and RANDOM_MAX:
int random = rand();
// get random number between 0 and 10:
int random = rand() % 11;
// get random number between 10 and 20:
int random = rand() % (21-10) + 10;
```