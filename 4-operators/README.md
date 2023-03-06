
## 4 Operators

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