# TLDR

## Like C#
- C++ is very similar to C#
- in fact, C# was derived from C++

## C++ and C
- C++ was derived from C and is fully backward-compatible
- For many problems there's two ways of solving it:
  - the "modern", object-oriented C++ way
  - the "classic", low-level C way

## Output
- C way: `printf("%d, %f, %d, %c", 3, 3.2f, true, 'a');`
- C++ way: `std::cout << 3 << ", " << 3.2f << ", " << true << ", " << a;`

## Variables & Data Types
- `bool` is basically just an `int`
  - `true`: 1
  - `false`: 0
- `int, char, float, double`: same as C#

## Operators
- same as in C#

## Input
- C way: `scanf_s("%d", &number);`
- C++ way: `cin >> number;`

## Control Structures
- Same as in C#
- For `bool`-expressions (e.g. `if(...)`):
  - everything but `0` is considered to be `true`

## Random
- initialize seed with current time: `srand(time(0));`
- get random number: `int random = rand() % max;`
- get random number 0-max: `int random = rand() % max;`
- get random number min-max: `int random = rand() % (max-min) + min;`