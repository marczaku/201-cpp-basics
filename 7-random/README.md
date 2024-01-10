# 7 Random

```cpp
#include <stdlib.h>

int main(){
  int i = rand();
  printf(i);
}
```

## Pseudo-Random

The number is pseudo-random
- mathematical function displaying "chaotic" behavior
- close to ideal distribution
- this is a useful feature. It allows us to have "random numbers"
  - that appear random to the user
  - but are predictable by the computer
- use cases for that predictability:
  - deterministic games, e.g. reproduce bugs that happen after certain "random" events
  - network games, e.g. make sure that every player's client simulates the same "random" events

## Random 0..RAND_MAX

Random Number between `0` and `RAND_MAX`

```cpp
int random = rand();
```

## Random 0..max

Random Number between `0` and `max` (exclusive)
- Use the Modulo-Operator!

```cpp
int random = rand()%max;
```

```
rand() -> rand()%5:
 0 -> 0
 1 -> 1
 2 -> 2
 3 -> 3
 4 -> 4
 5 -> 0
 6 -> 1
 7 -> 2
 8 -> 3
 9 -> 4 
10 -> 0
  ...
```

## Random min..max

Random Number between `min` (inclusive) and `max` (exclusive)

```cpp
int random = rand()%(max-min) + min;
```

```
rand() -> rand()%(5-2)+2:
 0 -> 0+2 -> 2
 1 -> 1+2 -> 3
 2 -> 2+2 -> 4
 3 -> 0+2 -> 2
 4 -> 1+2 -> 3
 5 -> 2+2 -> 4
 6 -> 0+2 -> 2
 7 -> 1+2 -> 3
 8 -> 2+2 -> 4
     ...
```

## Seed

Run this program multiple times:

```cpp
#include <stdlib.h>
#include <iostream>

int main(){
  for(int i = 0; i < 5; i++){
    std::cout << rand()%100 << std::endl;
  }
}
```

You always get the same numbers?
- successive calls of `rand()` return a deterministic sequence of numbers
- you get the same "random" numbers every time!
- very useful for debugging

## Changing the Seed

Assign a different seed, if you want a different set of "random" numbers:

```cpp
srand(50);
```

After changing the seed, all consecutive calls to `rand()` will use that seed:

```cpp
    std::cout << "First two random numbers of seed 50:" << std::endl;
    srand(50);
    std::cout << rand() % 100 << std::endl;
    std::cout << rand() % 100 << std::endl;
    std::cout << "First two random numbers of seed 51:" << std::endl;
    srand(51);
    std::cout << rand() % 100 << std::endl;
    std::cout << rand() % 100 << std::endl;
    std::cout << "First two random numbers of seed 50:" << std::endl;
    srand(50);
    std::cout << rand() % 100 << std::endl;
    std::cout << rand() % 100 << std::endl;
```

## Completely Random

If you want your Seed to be "random" every time you start your program, just use the current time:

```cpp
#include <time.h>

// ...

srand(time(0));
```

Good enough in most cases! :)

## EXERCISE: Nim
- Port your C# Code to C++
  - Shouldn't be too difficult!
