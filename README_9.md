# Chapter 9: Simple Mathematical Operators

Python mein mathematical calculations ke liye different operators aur functions available hain.

Basic operators:

```text
+   Addition
-   Subtraction
*   Multiplication
/   Division
//  Floor Division
**  Exponentiation
%   Modulus
```

Aur advanced mathematical calculations ke liye `math` module use kar sakte hain:

```python id="5w2q8n"
import math
```

---

# 9.1 Division

Division ke liye `/` operator use hota hai.

```python id="2xq9k8"
a = 10
b = 2

result = a / b

print(result)
```

Output:

```text id="4j5q3x"
5.0
```

Notice karo result `5.0` hai, `5` nahi.

Python mein `/` generally **float result** deta hai.

---

## Decimal division

```python id="3z8k2w"
print(10 / 4)
```

Output:

```text id="9j1n0x"
2.5
```

---

## Division with variables

```python id="8k3j4p"
quantity = 100
days = 5

average = quantity / days

print(average)
```

Output:

```text id="p6k8x1"
20.0
```

---

## Division by zero

Ye valid nahi hai:

```python id="q1h6v4"
print(10 / 0)
```

Python:

```text
ZeroDivisionError
```

dega.

---

## Floor Division `//`

Agar decimal part nahi chahiye aur floor division chahiye:

```python id="8r4m2k"
print(10 // 3)
```

Output:

```text id="z5c7v9"
3
```

Difference:

```text id="w6k2a1"
10 / 3
→ 3.333...

10 // 3
→ 3
```

**Important:** `//` simply decimal truncate karna nahi hota; ye **floor division** hai. Negative numbers mein difference nazar aata hai:

```python id="4t8m6p"
print(-10 // 3)
```

Output:

```text id="b2n7q4"
-4
```

---

# 9.2 Addition

Addition ke liye `+` use hota hai.

```python id="n8v2c5"
a = 10
b = 20

result = a + b

print(result)
```

Output:

```text id="f4s1q7"
30
```

---

## Multiple numbers

```python id="m3k9x2"
total = 10 + 20 + 30 + 40

print(total)
```

Output:

```text id="j7p2w8"
100
```

---

## Float addition

```python id="x5c1v9"
price1 = 25.50
price2 = 10.25

total = price1 + price2

print(total)
```

Output:

```text id="r4m8k2"
35.75
```

---

## Strings ke saath `+`

`+` sirf numbers ke liye nahi hai.

Strings ko concatenate bhi kar sakta hai:

```python id="q8n3v6"
first = "Muhammad"
last = "Nouman"

name = first + " " + last

print(name)
```

Output:

```text id="a5k7p2"
Muhammad Nouman
```

Lekin:

```python id="e2m9x4"
print("Age: " + 25)
```

error dega, kyun ke string aur integer directly concatenate nahi kar sakte.

Correct:

```python id="t6c4y1"
print("Age: " + str(25))
```

---

# 9.3 Exponentiation

Exponentiation ke liye `**` use hota hai.

```python id="u7p3m8"
result = 2 ** 3

print(result)
```

Output:

```text id="k9d2x5"
8
```

Matlab:

```text id="4b7nq1"
2 × 2 × 2 = 8
```

---

## Square

```python id="z4m8c2"
print(5 ** 2)
```

Output:

```text id="v6q1p9"
25
```

Matlab:

```text
5 × 5 = 25
```

---

## Cube

```python id="s2k7w4"
print(3 ** 3)
```

Output:

```text
27
```

---

## Square root

Square root ke liye exponent `0.5` use kar sakte ho:

```python id="h8p3v6"
print(25 ** 0.5)
```

Output:

```text
5.0
```

Lekin `math.sqrt()` zyada clear hai:

```python id="d4x9q1"
import math

print(math.sqrt(25))
```

Output:

```text
5.0
```

---

## Negative exponent

```python id="f6r2m8"
print(2 ** -1)
```

Output:

```text
0.5
```

Matlab:

```text
1 / 2 = 0.5
```

---

# 9.4 Trigonometric Functions

Python mein trigonometric functions `math` module mein available hain.

```python id="a7k3n5"
import math
```

Important functions:

```text id="y2p8c4"
math.sin()
math.cos()
math.tan()
```

Lekin ek **very important point**:

> Python ke `sin()`, `cos()`, `tan()` functions angle ko **radians** mein expect karte hain, degrees mein nahi.

---

## `sin()`

```python id="m5v1x8"
import math

result = math.sin(math.pi / 2)

print(result)
```

Output approximately:

```text
1.0
```

Because:

```text
π / 2 radians = 90°
sin(90°) = 1
```

---

## Degrees ko radians mein convert karna

Agar aapke paas degrees hain:

```python id="q9c4t2"
angle = 90

radians = math.radians(angle)

print(radians)
```

Output approximately:

```text
1.5707963267948966
```

Ab:

```python id="w6n2k5"
print(math.sin(radians))
```

Output:

```text
1.0
```

---

## `cos()`

```python id="r3x7m1"
import math

angle = math.radians(60)

print(math.cos(angle))
```

Output approximately:

```text
0.5
```

---

## `tan()`

```python id="p8k4v6"
angle = math.radians(45)

print(math.tan(angle))
```

Output approximately:

```text
1.0
```

---

## Radians → Degrees

Agar radians ko degrees mein convert karna ho:

```python id="c5y9q2"
angle = math.pi

print(math.degrees(angle))
```

Output:

```text
180.0
```

Useful functions:

```text id="x1m7b3"
math.radians()
    degrees → radians

math.degrees()
    radians → degrees
```

---

# 9.5 Inplace Operations

**In-place operation** ka matlab hai variable ki existing value ko operation ke result se update karna.

Suppose:

```python id="n4q8s2"
x = 10
x = x + 5

print(x)
```

Output:

```text
15
```

Isko short form mein:

```python id="k6w1p9"
x = 10
x += 5

print(x)
```

Output:

```text
15
```

---

## `+=`

```python id="r7m3c8"
x = 10
x += 5
```

Equivalent:

```python id="e2v9q4"
x = x + 5
```

---

## `-=`

```python id="f8k2n6"
x = 10
x -= 3

print(x)
```

Output:

```text
7
```

Equivalent:

```python
x = x - 3
```

---

## `*=`

```python id="p4y7m1"
x = 10
x *= 3

print(x)
```

Output:

```text
30
```

Equivalent:

```python
x = x * 3
```

---

## `/=`

```python id="z6c1r8"
x = 20
x /= 4

print(x)
```

Output:

```text
5.0
```

Equivalent:

```python
x = x / 4
```

---

## `//=`

```python id="h3n8q5"
x = 10
x //= 3

print(x)
```

Output:

```text
3
```

---

## `**=`

```python id="m7v2k9"
x = 2
x **= 3

print(x)
```

Output:

```text
8
```

---

## `%=`

```python id="q5x1c7"
x = 10
x %= 3

print(x)
```

Output:

```text
1
```

---

## In-place operators summary

| Operator  | Equivalent   |
| --------- | ------------ |
| `x += 5`  | `x = x + 5`  |
| `x -= 5`  | `x = x - 5`  |
| `x *= 5`  | `x = x * 5`  |
| `x /= 5`  | `x = x / 5`  |
| `x //= 5` | `x = x // 5` |
| `x **= 5` | `x = x ** 5` |
| `x %= 5`  | `x = x % 5`  |

---

# 9.6 Subtraction

Subtraction ke liye `-` operator use hota hai.

```python id="b4q8n2"
a = 20
b = 7

result = a - b

print(result)
```

Output:

```text
13
```

---

## Negative result

```python id="k7m2x5"
print(5 - 10)
```

Output:

```text
-5
```

---

## Practical work-order example

Suppose:

```python id="p3v9c6"
total_orders = 100
completed_orders = 75

pending = total_orders - completed_orders

print(pending)
```

Output:

```text
25
```

---

# 9.7 Multiplication

Multiplication ke liye `*` operator use hota hai.

```python id="w5n1r7"
price = 50
quantity = 4

total = price * quantity

print(total)
```

Output:

```text
200
```

---

## Decimal multiplication

```python id="a8k4m2"
price = 12.50
quantity = 4

total = price * quantity

print(total)
```

Output:

```text
50.0
```

---

## String multiplication

Interesting point: `*` strings ke saath bhi use ho sakta hai.

```python id="c6p2x9"
print("Hello " * 3)
```

Output:

```text
Hello Hello Hello
```

Yani string repetition.

---

## List multiplication

```python id="r1v7k4"
items = [0] * 5

print(items)
```

Output:

```text
[0, 0, 0, 0, 0]
```

---

# 9.8 Logarithms

Logarithms ke liye Python ka `math` module use hota hai.

```python id="y3m8q1"
import math
```

Important functions:

```text id="k5c2v7"
math.log()
math.log10()
math.log2()
```

---

## Natural logarithm

`math.log(x)` default mein natural logarithm, yani **base e**, calculate karta hai.

```python id="n9x4p6"
import math

print(math.log(10))
```

Output approximately:

```text
2.302585092994046
```

---

## Base 10 logarithm

```python id="t7m2c5"
print(math.log10(100))
```

Output:

```text
2.0
```

Because:

```text
10² = 100
```

---

## Base 2 logarithm

```python id="v4q8n1"
print(math.log2(8))
```

Output:

```text
3.0
```

Because:

```text
2³ = 8
```

---

## Custom base

Agar custom base chahiye:

```python id="m2x7k9"
import math

result = math.log(27, 3)

print(result)
```

Output:

```text
3.0
```

Because:

```text
3³ = 27
```

---

## `log()` ka concept

Agar:

```text
log₂(8) = 3
```

to iska matlab:

```text
2³ = 8
```

Similarly:

```text
log₁₀(1000) = 3
```

because:

```text
10³ = 1000
```

---

# 9.9 Modulus

Modulus ke liye `%` operator use hota hai.

Ye **remainder** return karta hai.

```python id="q8v3m1"
result = 10 % 3

print(result)
```

Output:

```text
1
```

Because:

```text
10 ÷ 3

3 × 3 = 9
remainder = 1
```

---

## Even/Odd check

Modulus ka bohat common use even/odd check karna hai.

```python id="c5n9x2"
number = 10

if number % 2 == 0:
    print("Even")
else:
    print("Odd")
```

Output:

```text
Even
```

For:

```python
number = 7
```

Output:

```text
Odd
```

Kyun ke:

```text
10 % 2 = 0
7 % 2 = 1
```

---

# Modulus ka practical use

Suppose work orders ko groups mein divide karna hai:

```python id="f7k2m4"
work_orders = 23
group_size = 5

remainder = work_orders % group_size

print(remainder)
```

Output:

```text
3
```

Yani 23 ko groups of 5 mein divide karne par 3 items remainder mein bachenge.

---

# Division aur Modulus together

Ye combination bohat useful hai.

```python id="s4p8y1"
number = 17

quotient = number // 5
remainder = number % 5

print("Quotient:", quotient)
print("Remainder:", remainder)
```

Output:

```text
Quotient: 3
Remainder: 2
```

Because:

```text
17 = (5 × 3) + 2
```

---

# Operator Precedence

Python mathematical expressions mein precedence follow karta hai.

Example:

```python id="n6x2c8"
result = 2 + 3 * 4

print(result)
```

Output:

```text
14
```

Kyun?

Pehle multiplication:

```text
3 × 4 = 12
```

Phir:

```text
2 + 12 = 14
```

---

## Parentheses

Agar addition pehle karni ho:

```python id="u9m4k1"
result = (2 + 3) * 4

print(result)
```

Output:

```text
20
```

Rule:

```text
Parentheses
    ↓
Exponentiation
    ↓
Multiplication / Division / Floor Division / Modulus
    ↓
Addition / Subtraction
```

---

# Complete Mathematical Operator Table

| Operator | Meaning        |   Example |     Result |
| -------- | -------------- | --------: | ---------: |
| `+`      | Addition       |  `10 + 3` |       `13` |
| `-`      | Subtraction    |  `10 - 3` |        `7` |
| `*`      | Multiplication |  `10 * 3` |       `30` |
| `/`      | Division       |  `10 / 3` | `3.333...` |
| `//`     | Floor division | `10 // 3` |        `3` |
| `%`      | Remainder      |  `10 % 3` |        `1` |
| `**`     | Exponentiation | `10 ** 2` |      `100` |

---

# Practical HVAC Calculation

Suppose AHU fan ka airflow:

```python id="b7q2m5"
airflow = 1200
fans = 4

average_airflow = airflow / fans

print(average_airflow)
```

Output:

```text
300.0
```

Suppose operating hours calculate karni hain:

```python id="x3k8n1"
start_hour = 8
end_hour = 17

operating_hours = end_hour - start_hour

print(operating_hours)
```

Output:

```text
9
```

Aur agar total energy rate se calculate karna ho:

```python id="m6v1c9"
power = 5
hours = 9

energy = power * hours

print(energy)
```

Output:

```text
45
```

---

# Chapter 9 ka Mental Model

```text
Mathematical Operators
        │
        ├── +   Addition
        ├── -   Subtraction
        ├── *   Multiplication
        ├── /   Division
        ├── //  Floor Division
        ├── %   Remainder
        └── **  Exponentiation
```

Advanced mathematics:

```text
math
 │
 ├── sqrt()
 ├── sin()
 ├── cos()
 ├── tan()
 ├── log()
 ├── log10()
 └── log2()
```

In-place:

```text
x += 5
x -= 5
x *= 5
x /= 5
x //= 5
x %= 5
x **= 5
```

---

# Quick Revision

### Division

```python
10 / 3
```

→ `3.333...`

### Floor Division

```python
10 // 3
```

→ `3`

### Addition

```python
10 + 3
```

→ `13`

### Subtraction

```python
10 - 3
```

→ `7`

### Multiplication

```python
10 * 3
```

→ `30`

### Exponentiation

```python
10 ** 2
```

→ `100`

### Modulus

```python
10 % 3
```

→ `1`

### Trigonometry

```python
import math

math.sin(math.radians(90))
```

→ approximately `1`

### Logarithm

```python
math.log10(100)
```

→ `2`

### In-place

```python
x += 5
```

same basic idea as:

```python
x = x + 5
```

## Sabse important difference

```text
/   → normal division
//  → floor division
%   → remainder
**  → power
```

Example:

```text
17 / 5   → 3.4
17 // 5  → 3
17 % 5   → 2
2 ** 3   → 8
```

Ye 4 operators especially strong kar lo, kyun ke aage programming mein bohat frequently use honge.
