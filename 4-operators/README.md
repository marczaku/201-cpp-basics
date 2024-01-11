
## 4 Operators

### Operator Types
- Unary `-a`, `+a`, `a++`
- Binary `a+b`, `a*b`, `a<b`
- Ternary `a ? b : c`

### Arithmetic Operators
- `+`, `-`, `/`, `*`, `%`, `++`, `--`
- Post-Increment: `a++`
- Pre-Increment: `++a`
  - often has better performance!

Used to express mathematical operations:

```c++
float damage = (strength + itemPower) * bonusDamage;
```

### Comparison Operators
- `==`, `!=`, `<`, `<=`, `>`, `>=`
- Two arguments
  - often of the same type
  - but not always!
- Return Type `bool`

Used to compare two values by making an assumption and receiving:
- `true`, if the assumption was true
  - e.g. `4 < 100;`
- `false`, if the assumption was false
  - e.g. `1 == 2;`

The Player has full health if
- the player's health is EQUAL TO
- the player's max health

```c++
bool playerHasFullHealth = health == maxHealth;
```

### Logical Operators
- `!`, `&&`, `||`

Used to express more complex logical conditions

The Game is over if
- either the player is dead
- or BOTH:
  - the game is NOT endless
  - AND the time is over

```c++
bool gameOver = playerIsDead || (!gameIsEndless && timeIsOver);
```

### Bitwise Operators
- `~`, `&`, `|`, `^`, `>>`, `<<`

Used to do logical operations on bit-level
- can be used for very low-level optimizations
- often used for generating hashes
- can be used for very simple encryption
- most common use case: Enum Flags:

```c++
#include <cstdio>
#include <Windows.h>

enum AttackFlags : uint8_t
{
    None = 0,
    Stun = 1 << 0,     //  1 0b00000001
    Freeze = 1 << 1,   //  2 0b00000010
    Poison = 1 << 2,   //  4 0b00000100
    Magic = 1 << 3,    //  8 0b00001000
    Physical = 1 << 4, // 16 0b00010000
    Despell = 1 << 5,  // 32 0b00100000
};

DEFINE_ENUM_FLAG_OPERATORS(AttackFlags)

int main()
{
    AttackFlags flags{ AttackFlags::None };

    // setting bits:
    flags |= AttackFlags::Stun | AttackFlags::Poison;

    // unsetting bits:
    flags &= ~AttackFlags::Stun;

    // testing for bits:
    if (flags & AttackFlags::Poison) {
        // true
        printf("You will see this, since the Poison-Bit is set.");
    }
    if (flags & AttackFlags::Stun) {
        // false
        printf("You will not see this, since the Stun-Bit is not set.");
    }
}
```

### Compound Assignment Operators

Exist to reduce our code from:
```c++
health = health + 5;
```

to:

```c++
health += 5;
```

In C++, they even bring performance benefits!
- More on the reason why later!

- `+=`, `-=`, `*=`, `/=`, `%=`, `|=`, `&=`, `^=`, `<<=`, `>>=`