# Chapter 12: Operator Precedence

**Operator precedence** ka matlab hai:

> Jab ek expression mein multiple operators hon, Python kis operator ko pehle execute karega.

Bilkul mathematics ki tarah Python mein bhi har operator ka ek **priority/order** hota hai.

Example:

```python
result = 2 + 3 * 4
```

Agar left-to-right simple calculation hoti to:

```text
2 + 3 = 5
5 * 4 = 20
```

Lekin Python aisa nahi karega.

Python pehle `*` karega:

```text
3 * 4 = 12
```

phir:

```text
2 + 12 = 14
```

Result:

```python
print(2 + 3 * 4)
```

Output:

```text
14
```

Isko **operator precedence** kehte hain.

---

# 12.1 Simple Operator Precedence Examples in Python

## Example 1: Multiplication before Addition

```python
result = 10 + 5 * 2

print(result)
```

Python pehle:

```text
5 * 2 = 10
```

phir:

```text
10 + 10 = 20
```

Output:

```text
20
```

---

## Example 2: Parentheses change the order

Agar humein addition pehle karni ho:

```python
result = (10 + 5) * 2

print(result)
```

Ab Python pehle parentheses:

```text
10 + 5 = 15
```

phir:

```text
15 * 2 = 30
```

Output:

```text
30
```

Compare:

```python
10 + 5 * 2
```

→ `20`

Aur:

```python
(10 + 5) * 2
```

→ `30`

**Isliye parentheses bohat important hain.**

---

# Basic Operator Precedence Order

Beginner ke liye commonly used order:

| Priority | Operator             | Meaning                 |
| -------: | -------------------- | ----------------------- |
|        1 | `()`                 | Parentheses             |
|        2 | `**`                 | Exponentiation          |
|        3 | `+x`, `-x`, `~x`     | Unary operators         |
|        4 | `*`, `/`, `//`, `%`  | Multiplication/division |
|        5 | `+`, `-`             | Addition/subtraction    |
|        6 | `<`, `<=`, `>`, `>=` | Comparisons             |
|        7 | `==`, `!=`           | Equality                |
|        8 | `not`                | Logical NOT             |
|        9 | `and`                | Logical AND             |
|       10 | `or`                 | Logical OR              |

Is table ko abhi complete Python grammar ki tarah memorize karne ki zaroorat nahi hai. Pehle common operators ka order samjho.

---

# 1. Parentheses `()`

Parentheses sabse pehle evaluate hote hain.

```python
result = (5 + 3) * 2
```

Pehle:

```text
5 + 3 = 8
```

Phir:

```text
8 * 2 = 16
```

Output:

```text
16
```

Without parentheses:

```python
result = 5 + 3 * 2
```

Pehle:

```text
3 * 2 = 6
```

Phir:

```text
5 + 6 = 11
```

Output:

```text
11
```

---

# 2. Exponentiation `**`

Exponentiation multiplication se pehle hoti hai.

```python
result = 2 + 3 ** 2
print(result)
```

Pehle:

```text
3 ** 2 = 9
```

Phir:

```text
2 + 9 = 11
```

Output:

```text
11
```

---

# 3. Multiplication, Division, Floor Division, Modulus

Ye operators same precedence level par hote hain:

```text
*
/
//
%
```

Example:

```python
result = 10 + 20 / 5
```

Pehle:

```text
20 / 5 = 4
```

Phir:

```text
10 + 4 = 14
```

Output:

```text
14.0
```

Notice `/` ka result Python mein `float` hota hai.

---

# Same precedence: left to right

Agar operators same precedence ke hon, normally Python unhein **left-to-right** evaluate karta hai.

Example:

```python
result = 20 / 5 * 2
```

Pehle:

```text
20 / 5 = 4
```

Phir:

```text
4 * 2 = 8
```

Output:

```text
8.0
```

Ye:

```text
20 / (5 * 2)
```

nahi hai.

Agar tum multiplication pehle chahte ho:

```python
result = 20 / (5 * 2)
```

Result:

```text
2.0
```

---

# 4. Addition aur Subtraction

`+` aur `-` multiplication/division ke baad aate hain.

Example:

```python
result = 10 + 5 * 2 - 3
print(result)
```

Python pehle:

```text
5 * 2 = 10
```

Expression ban gaya:

```text
10 + 10 - 3
```

Phir left-to-right:

```text
10 + 10 = 20
20 - 3 = 17
```

Output:

```text
17
```

---

# 5. Comparison Operators

Comparison operators arithmetic calculation ke baad evaluate hote hain.

Example:

```python
result = 10 + 5 > 12

print(result)
```

Pehle:

```text
10 + 5 = 15
```

Phir:

```text
15 > 12
```

Result:

```text
True
```

---

# 6. `not`, `and`, `or`

Boolean operators mein precedence:

```text
not
  ↓
and
  ↓
or
```

Yani `not` pehle, phir `and`, phir `or`.

Example:

```python
result = True or False and False

print(result)
```

Python pehle:

```text
False and False
```

→ `False`

Phir:

```text
True or False
```

→ `True`

Output:

```text
True
```

---

# Parentheses se Boolean expression clear karo

Ye:

```python
result = True or False and False
```

ki jagah explicitly likh sakte ho:

```python
result = True or (False and False)
```

Isse code read karna easy ho jata hai.

---

# Practical HVAC Example

Suppose:

```python
temperature = 30
fan_running = True
fault = False
```

Condition:

```python
if temperature > 25 and fan_running and not fault:
    print("AHU running normally")
```

Python logically evaluate karega:

```text
temperature > 25
        ↓
      True

fan_running
        ↓
      True

not fault
        ↓
      True
```

Then:

```text
True and True and True
```

Result:

```text
True
```

Output:

```text
AHU running normally
```

---

# Practical Work Order Example

Suppose:

```python
hours = 1.5
priority = "High"
completed = True
```

Condition:

```python
if hours < 2 and priority == "High" and completed:
    print("Work order completed within target")
```

Yahan comparisons pehle values produce karte hain:

```text
hours < 2
```

→ `True`

```text
priority == "High"
```

→ `True`

```text
completed
```

→ `True`

Then:

```text
True and True and True
```

→ `True`

Output:

```text
Work order completed within target
```

---

# A complex example

```python
result = 10 + 2 * 3 > 15 and 5 < 10
```

Isko step-by-step solve karte hain.

### Step 1: Multiplication

```text
2 * 3 = 6
```

Expression:

```text
10 + 6 > 15 and 5 < 10
```

### Step 2: Addition

```text
10 + 6 = 16
```

Expression:

```text
16 > 15 and 5 < 10
```

### Step 3: Comparisons

```text
16 > 15
```

→ `True`

Aur:

```text
5 < 10
```

→ `True`

Ab:

```text
True and True
```

→ `True`

Final result:

```python
True
```

---

# Parentheses: Best Practice

Agar expression complicated ho, parentheses use karna **good practice** hai.

Instead of:

```python
if temperature > 25 and fan_running or communication_ok:
```

clear version:

```python
if (temperature > 25 and fan_running) or communication_ok:
```

Ab reader ko immediately samajh aata hai ke logic ka grouping kya hai.

---

# Important: Precedence aur Evaluation Order same cheez nahi

Ye distinction important hai.

**Operator precedence** batati hai:

> Kaunsa operator expression mein higher priority rakhta hai?

**Evaluation order** batata hai:

> Python actual expression ko kis sequence mein evaluate karta hai?

Boolean expressions mein **short-circuit evaluation** bhi involved hoti hai.

Example:

```python
False and some_function()
```

Yahan `and` ki precedence se zyada important practical behavior ye hai ke Python `False` dekh kar `some_function()` ko evaluate hi nahi karega.

---

# Common Beginner Mistake

### Mistake

```python
result = 10 + 5 * 2
```

Sochna:

```text
10 + 5 = 15
15 * 2 = 30
```

❌ Wrong.

Python multiplication pehle karega:

```text
5 * 2 = 10
10 + 10 = 20
```

✅ Correct result:

```text
20
```

---

# Correct way to force your order

Agar addition pehle chahiye:

```python
result = (10 + 5) * 2
```

Result:

```text
30
```

**Rule:**

> Jis calculation ko pehle karwana hai, usko parentheses mein rakho.

---

# Quick Practice

### Question 1

```python
print(2 + 3 * 4)
```

Answer:

```text
14
```

---

### Question 2

```python
print((2 + 3) * 4)
```

Answer:

```text
20
```

---

### Question 3

```python
print(20 / 5 * 2)
```

Answer:

```text
8.0
```

---

### Question 4

```python
print(2 ** 3 + 1)
```

Pehle:

```text
2 ** 3 = 8
```

Then:

```text
8 + 1 = 9
```

Answer:

```text
9
```

---

### Question 5

```python
print(True or False and False)
```

Pehle:

```text
False and False = False
```

Then:

```text
True or False = True
```

Answer:

```text
True
```

---

# Chapter 12 Summary

Sabse important precedence order ko abhi is tarah yaad rakho:

```text
()
 ↓
**
 ↓
*, /, //, %
 ↓
+, -
 ↓
comparisons
 ↓
not
 ↓
and
 ↓
or
```

### Simple memory trick

```text
Parentheses
→ Power
→ Multiply/Divide
→ Add/Subtract
→ Compare
→ NOT
→ AND
→ OR
```

Aur sabse important rule:

> **Parentheses expression ka order explicitly control karne ka easiest tareeqa hain.**

Agar doubt ho ke Python expression ko kis order mein calculate karega, parentheses use karo.
