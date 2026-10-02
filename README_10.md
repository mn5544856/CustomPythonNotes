# Chapter 10: Bitwise Operators

Sab se pehle ek important concept samjho:

Normal mathematical operators:

```text
+   -   *   /   %
```

numbers ki mathematical calculation karte hain.

**Bitwise operators** number ke individual **bits** par kaam karte hain.

Example:

```text
Decimal 5

Binary:
0101
```

Aur:

```text
Decimal 3

Binary:
0011
```

Yahan:

```text
0 1 0 1
│ │ │ │
│ │ │ └── bit
│ │ └──── bit
│ └────── bit
└──────── bit
```

Python mein bitwise operators:

| Operator | Name        |            |
| -------- | ----------- | ---------- |
| `~`      | Bitwise NOT |            |
| `&`      | Bitwise AND |            |
| `        | `           | Bitwise OR |
| `^`      | Bitwise XOR |            |
| `<<`     | Left Shift  |            |
| `>>`     | Right Shift |            |

---

# Binary samajhna

Bitwise operators samajhne ke liye binary ka basic idea zaroori hai.

Decimal `5` ko binary mein:

```text
5 = 0101
```

Decimal `6`:

```text
6 = 0110
```

Decimal `10`:

```text
10 = 1010
```

Har position ki value:

```text
8   4   2   1
│   │   │   │
1   0   1   0
```

Example:

```text
1010

= 1×8
+ 0×4
+ 1×2
+ 0×1

= 10
```

Python mein binary representation dekhne ke liye:

```python
print(bin(5))
```

Output:

```text
0b101
```

`0b` ka matlab hai **binary number**.

---

# 10.1 Bitwise NOT

Bitwise NOT operator:

```text
~
```

Ye bits ko invert karta hai:

```text
0 → 1
1 → 0
```

Example concept:

```text
Original:
0101

NOT:
1010
```

Python:

```python
x = 5

print(~x)
```

Output:

```text
-6
```

Yahan beginner ko usually confusion hoti hai:

> "Agar `0101` ka NOT `1010` hai to answer 10 kyun nahi?"

Reason ye hai ke Python integers **signed integer representation** aur two's complement semantics use karte hain.

Python mein:

```python
~x == -(x + 1)
```

Isliye:

```python
~5
```

becomes:

```text
-(5 + 1)
= -6
```

Aur:

```python
~10
```

→

```text
-11
```

### Simple rule

```text
~5  → -6
~10 → -11
~20 → -21
```

Formula yaad rakho:

```text
~x = -(x + 1)
```

---

# 10.2 Bitwise XOR — Exclusive OR

Operator:

```text
^
```

XOR ka rule:

```text
Same bits    → 0
Different    → 1
```

Truth table:

| A | B | A ^ B |
| - | - | ----- |
| 0 | 0 | 0     |
| 0 | 1 | 1     |
| 1 | 0 | 1     |
| 1 | 1 | 0     |

Example:

```text
5 = 0101
3 = 0011
```

XOR:

```text
  0101
^ 0011
------
  0110
```

`0110` = `6`

Python:

```python
a = 5
b = 3

print(a ^ b)
```

Output:

```text
6
```

---

## XOR ka simple rule

**Different = 1**

```text
0 ^ 0 = 0
0 ^ 1 = 1
1 ^ 0 = 1
1 ^ 1 = 0
```

Ek interesting property:

```python
print(5 ^ 5)
```

Output:

```text
0
```

Kyun ke same bits XOR karne par sab `0` ho jate hain.

---

# 10.3 Bitwise AND

Operator:

```text
&
```

AND ka rule:

> Result `1` tab hota hai jab **dono bits `1`** hon.

Truth table:

| A | B | A & B |
| - | - | ----- |
| 0 | 0 | 0     |
| 0 | 1 | 0     |
| 1 | 0 | 0     |
| 1 | 1 | 1     |

Example:

```text
5 = 0101
3 = 0011
```

AND:

```text
  0101
& 0011
------
  0001
```

`0001` = `1`

Python:

```python
a = 5
b = 3

print(a & b)
```

Output:

```text
1
```

---

## AND ka simple rule

**Dono 1 hon → 1**

```text
1 & 1 = 1
1 & 0 = 0
0 & 1 = 0
0 & 0 = 0
```

---

# 10.4 Bitwise OR

Operator:

```text
|
```

OR ka rule:

> Agar **kam az kam ek bit `1`** ho to result `1`.

Truth table:

| A | B | A | B |
| - | - | ----- |
| 0 | 0 | 0     |
| 0 | 1 | 1     |
| 1 | 0 | 1     |
| 1 | 1 | 1     |

Example:

```text
5 = 0101
3 = 0011
```

OR:

```text
  0101
| 0011
------
  0111
```

`0111` = `7`

Python:

```python
a = 5
b = 3

print(a | b)
```

Output:

```text
7
```

---

# AND vs OR vs XOR

Ye teen bohat important hain:

```text
AND (&)
→ dono 1 hon to 1

OR (|)
→ koi ek bhi 1 ho to 1

XOR (^)
→ different hon to 1
```

Example:

```text
A = 1
B = 1

AND → 1
OR  → 1
XOR → 0
```

Aur:

```text
A = 1
B = 0

AND → 0
OR  → 1
XOR → 1
```

### Memory trick

```text
AND → All/Dono
OR  → One/Koi ek
XOR → Different
```

---

# 10.5 Bitwise Left Shift

Operator:

```text
<<
```

Left shift bits ko left side move karta hai.

Example:

```text
5 = 0101
```

Agar 1 position left shift:

```text
0101 << 1

1010
```

`1010` = `10`

Python:

```python
x = 5

print(x << 1)
```

Output:

```text
10
```

---

## Left shift ka shortcut

Positive integer ke liye:

```text
x << 1
```

approximately:

```text
x × 2
```

Aur:

```text
x << 2
```

approximately:

```text
x × 4
```

Example:

```python
print(5 << 1)
print(5 << 2)
print(5 << 3)
```

Output:

```text
10
20
40
```

Because:

```text
5 × 2 = 10
5 × 4 = 20
5 × 8 = 40
```

General rule:

```text
x << n

= x × 2ⁿ
```

Positive integers ke liye.

---

# 10.6 Bitwise Right Shift

Operator:

```text
>>
```

Right shift bits ko right side move karta hai.

Example:

```text
20 = 10100
```

One position right:

```text
10100 >> 1

01010
```

`01010` = `10`

Python:

```python
x = 20

print(x >> 1)
```

Output:

```text
10
```

---

## Right shift ka shortcut

Positive integer ke liye:

```text
x >> 1
```

approximately integer floor division by 2 ke equivalent hota hai.

Example:

```python
print(20 >> 1)
```

→

```text
10
```

Aur:

```python
print(20 >> 2)
```

→

```text
5
```

Because:

```text
20 ÷ 2 = 10

20 ÷ 4 = 5
```

General rule:

```text
x >> n
```

positive integers ke liye roughly:

```text
x // 2ⁿ
```

---

# Left Shift vs Right Shift

| Operator | Meaning     |   Example | Result |
| -------- | ----------- | --------: | -----: |
| `<<`     | Left shift  |  `5 << 1` |   `10` |
| `>>`     | Right shift | `20 >> 1` |   `10` |

Mental picture:

```text
<<
LEFT

>> 
RIGHT
```

Example:

```text
5 = 0101

5 << 1
= 1010
= 10
```

Aur:

```text
20 = 10100

20 >> 1
= 01010
= 10
```

---

# 10.7 Inplace Operations

Chapter 9 mein humne arithmetic in-place operators dekhe thay:

```python
x += 5
x -= 5
x *= 5
```

Bitwise operators ke bhi in-place versions hote hain.

---

## `&=`

```python
x = 5
x &= 3

print(x)
```

Equivalent:

```python
x = x & 3
```

Output:

```text
1
```

---

## `|=`

```python
x = 5
x |= 3

print(x)
```

Equivalent:

```python
x = x | 3
```

Output:

```text
7
```

---

## `^=`

```python
x = 5
x ^= 3

print(x)
```

Equivalent:

```python
x = x ^ 3
```

Output:

```text
6
```

---

## `<<=`

```python
x = 5
x <<= 1

print(x)
```

Equivalent:

```python
x = x << 1
```

Output:

```text
10
```

---

## `>>=`

```python
x = 20
x >>= 1

print(x)
```

Equivalent:

```python
x = x >> 1
```

Output:

```text
10
```

---

## `~=` ?

Yahan ek important point:

Bitwise NOT ka **`~=` in-place operator nahi hota**.

Aap:

```python
x ~= 5
```

nahi likh sakte.

NOT ke liye simply:

```python
x = ~x
```

use karo.

---

# Bitwise In-place Summary

| Operator  | Equivalent   |              |
| --------- | ------------ | ------------ |
| `x &= y`  | `x = x & y`  |              |
| `x        | = y`         | `x = x \| y` |
| `x ^= y`  | `x = x ^ y`  |              |
| `x <<= y` | `x = x << y` |              |
| `x >>= y` | `x = x >> y` |              |

---

# Complete Bitwise Operator Table

| Operator | Name        | Basic idea       |
| -------- | ----------- | ---------------- |
| `~`      | NOT         | `0 ↔ 1`          |
| `&`      | AND         | dono `1` → `1`   |
| `\|`     | OR          | koi ek `1` → `1` |
| `^`      | XOR         | different → `1`  |
| `<<`     | Left Shift  | bits left move   |
| `>>`     | Right Shift | bits right move  |

---

# Ek Complete Example

Ab `5` aur `3` par sab operations dekhte hain:

```python
a = 5
b = 3

print("AND:", a & b)
print("OR:", a | b)
print("XOR:", a ^ b)
print("Left Shift:", a << 1)
print("Right Shift:", a >> 1)
print("NOT:", ~a)
```

Output:

```text
AND: 1
OR: 7
XOR: 6
Left Shift: 10
Right Shift: 2
NOT: -6
```

---

# Real-world Concept: Flags

Bitwise operations ka ek important practical use **flags/permissions/status bits** hain.

Suppose ek system mein 4 features hain:

```text
Bit 0 → Fan
Bit 1 → Cooling
Bit 2 → Heating
Bit 3 → Alarm
```

Example:

```text
0001
```

ka matlab Fan enabled.

Aur:

```text
0011
```

ka matlab:

```text
Fan + Cooling
```

Bitwise OR se flags combine kar sakte hain:

```python
FAN = 1
COOLING = 2

status = FAN | COOLING

print(status)
```

Output:

```text
3
```

Binary:

```text
0001
OR
0010
----
0011
```

Yani dono flags active.

Bitwise AND se check kar sakte hain:

```python
if status & COOLING:
    print("Cooling is ON")
```

Output:

```text
Cooling is ON
```

Ye concept HVAC controllers, permissions, hardware registers, network protocols aur embedded systems mein useful hota hai.

---

# Binary Dekhne ka Useful Tool

Aap Python mein `bin()` use karke number ka binary representation dekh sakte ho:

```python
x = 13

print(bin(x))
```

Output:

```text
0b1101
```

Aur:

```python
print(bin(5))
print(bin(3))
```

Output:

```text
0b101
0b11
```

Comparison ko same length mein likho:

```text
5 = 0101
3 = 0011
```

Phir operation samajhna easy ho jata hai.

---

# Chapter 10 — Sabse Important Examples

### AND

```python
5 & 3
```

```text
0101
0011
----
0001

= 1
```

### OR

```python
5 | 3
```

```text
0101
0011
----
0111

= 7
```

### XOR

```python
5 ^ 3
```

```text
0101
0011
----
0110

= 6
```

### Left Shift

```python
5 << 1
```

```text
0101 → 1010
```

→ `10`

### Right Shift

```python
20 >> 1
```

```text
10100 → 01010
```

→ `10`

### NOT

```python
~5
```

→ `-6`

Formula:

```text
~x = -(x + 1)
```

---

# Chapter 10 Mental Model

```text
                 Bitwise Operators
                        │
        ┌───────────────┼────────────────┐
        │               │                │
       Logic          Shift             NOT
        │               │                │
    ┌───┼───┐       ┌───┴───┐            ~
    │   │   │       │       │
    &   |   ^      <<       >>
   AND OR XOR     Left     Right
```

Sabse pehle ye yaad rakho:

```text
&   → AND  → dono 1
|   → OR   → koi ek 1
^   → XOR  → different
~   → NOT  → opposite
<<  → left shift
>>  → right shift
```

Aur:

```text
<< 1 → × 2
<< 2 → × 4

>> 1 → ÷ 2
>> 2 → ÷ 4
```

**Note:** Ye multiplication/division shortcut positive integers ke context mein samajhna easiest hai; negative integers ke liye Python ka signed/two's-complement behavior alag details rakhta hai.

## Practice

Inko khud predict karo, phir Python mein run karke check karo:

```python
print(6 & 3)
print(6 | 3)
print(6 ^ 3)
print(6 << 1)
print(6 >> 1)
print(~6)
```

Phir binary mein verify karo:

```python
print(bin(6))
print(bin(3))
```

Is chapter mein sabse important skill **binary conversion ratna nahi**, balki bits ko line-by-line compare karna hai.
# 10.1 Bitwise NOT `~`

Python mein **Bitwise NOT** operator:

```python
~
```

hota hai.

Ye integer ke bits ko conceptually **invert** karta hai:

```text
0 → 1
1 → 0
```

Lekin Python mein integers fixed 4-bit ya 8-bit numbers nahi hote. Python signed integers ko **two's-complement semantics** ke saath treat karta hai. Is wajah se `~5` ka result `10` nahi, balki `-6` hota hai.

---

## Example

```python
x = 5

print(~x)
```

Output:

```text
-6
```

Is result ko samajhne ka sabse reliable mathematical rule hai:

```text
~x = -(x + 1)
```

Isliye:

```text
~5
= -(5 + 1)
= -6
```

---

## Ye rule kyun kaam karta hai?

Positive integer `5` ka binary:

```text
5 = 0101
```

Agar hum simplified fixed-width example mein bits invert karein:

```text
0101
↓ NOT
1010
```

Lekin `1010` ko **ordinary positive binary 10** samajhna Python ke `~5` ko explain nahi karta.

Python ke signed/two's-complement interpretation mein:

```text
~5 = -6
```

Aur two's-complement relationship ki wajah se:

```text
~5 + 5 = -1
```

ya:

```text
~5 = -5 - 1
    = -6
```

---

## Kuch aur examples

```python
print(~0)
print(~1)
print(~2)
print(~5)
print(~10)
```

Output:

```text
-1
-2
-3
-6
-11
```

Pattern dekho:

```text
~0  = -(0 + 1)  = -1
~1  = -(1 + 1)  = -2
~2  = -(2 + 1)  = -3
~5  = -(5 + 1)  = -6
~10 = -(10 + 1) = -11
```

---

## Negative numbers par bhi

Formula negative integers ke liye bhi work karta hai.

Example:

```python
print(~(-6))
```

Output:

```text
5
```

Calculation:

```text
~(-6)
= -((-6) + 1)
= -(-5)
= 5
```

Isliye ye relationship yaad rakhna useful hai:

```text
~x = -(x + 1)
```

---

## `~` ko `-` se confuse mat karo

Ye:

```python
x = 5

print(-x)
print(~x)
```

Output:

```text
-5
-6
```

Difference:

```text
-x
```

**Arithmetic negation** hai.

Jab ke:

```text
~x
```

**Bitwise NOT** hai.

---

## Important mental model

```text
-x
→ number ko negate karta hai

~x
→ bits ko invert karta hai
→ Python integer result: -(x + 1)
```

Example:

```text
x = 5

-x → -5
~x → -6
```

### Short rule

```text
Bitwise NOT:

~x = -(x + 1)
```

Isliye:

```text
~5  → -6
~10 → -11
~20 → -21
```

**Important:** `~5` ko simply `0101 → 1010 → 10` kehna Python ke actual result ko explain nahi karta. `0101 → 1010` sirf ek fixed-width bit illustration hai; Python ke actual integer semantics mein `~5` ka result `-6` hai.
