# Chapter 11: Boolean Operators

Python mein **Boolean Operators** ka use conditions ko combine karne aur logical decisions lene ke liye hota hai.

Python ke 3 main Boolean operators hain:

```python
and
or
not
```

Basic idea:

| Operator | Basic meaning                             |
| -------- | ----------------------------------------- |
| `and`    | Dono conditions true honi chahiye         |
| `or`     | Kam az kam ek condition true honi chahiye |
| `not`    | Result ko ulta karta hai                  |

---

# 11.1 `and` and `or` are not guaranteed to return a boolean

Ye Python ka bohat important point hai.

Beginner ko lagta hai:

```python
True and True
```

hamesha `True` return karega.

Ye true hai:

```python
print(True and True)
```

Output:

```text
True
```

Lekin Python mein `and` aur `or` **zaroori nahi ke `True` ya `False` return karein**.

Ye actual values bhi return kar sakte hain.

### Example: `and`

```python
print(10 and 20)
```

Output:

```text
20
```

Yahan result `True` nahi hai. Result `20` hai.

### Example

```python
print(0 and 20)
```

Output:

```text
0
```

### `or` example

```python
print(10 or 20)
```

Output:

```text
10
```

Aur:

```python
print(0 or 20)
```

Output:

```text
20
```

Is behavior ko samajhne ke liye **truthy/falsy** aur **short-circuit evaluation** samajhna zaroori hai.

---

## Truthy aur Falsy

Python mein kuch values ko condition mein `False` treat kiya jata hai.

Common falsy values:

```python
False
None
0
0.0
""
[]
{}
set()
```

Baaki bohat si non-empty/non-zero values truthy hoti hain:

```python
True
10
-5
"hello"
[1, 2]
{"name": "Ali"}
```

Example:

```python
if 0:
    print("True")
else:
    print("False")
```

Output:

```text
False
```

Lekin:

```python
if 10:
    print("True")
```

Output:

```text
True
```

---

# 11.2 A simple example

Sabse basic Boolean example:

```python
temperature = 22

print(temperature > 18)
```

Output:

```text
True
```

Ab do conditions combine karte hain:

```python
temperature = 22
humidity = 50

print(temperature > 18 and humidity < 60)
```

Output:

```text
True
```

Kyun?

Pehli condition:

```python
temperature > 18
```

result:

```text
True
```

Doosri:

```python
humidity < 60
```

result:

```text
True
```

So:

```text
True and True
```

result:

```text
True
```

### HVAC example

```python
fan_running = True
temperature_ok = True

if fan_running and temperature_ok:
    print("AHU condition is OK")
```

Output:

```text
AHU condition is OK
```

---

# 11.3 Short-circuit evaluation

**Short-circuit evaluation** ka matlab hai Python har condition ko zaroori nahi ke evaluate kare.

Python result determine hote hi ruk sakta hai.

## `and` mein

Agar pehli value falsy hai, to Python ko doosri value check karne ki zaroorat nahi hoti.

Example:

```python
print(0 and 100)
```

Python dekhta hai:

```text
0
```

`0` falsy hai.

`and` ko true result ke liye dono operands ki zaroorat hoti hai.

Isliye Python wahi `0` return kar deta hai.

```text
0
```

### Function se samjho

```python
def check():
    print("Function executed")
    return True

print(False and check())
```

Output:

```text
False
```

Notice:

```text
Function executed
```

print nahi hua.

Kyun?

Kyunki:

```python
False and anything
```

ka result already falsy hoga.

Isliye Python ne `check()` execute hi nahi kiya.

---

## `or` mein

Agar pehli value truthy hai, to Python doosri value evaluate nahi karta.

```python
print(10 or 100)
```

Output:

```text
10
```

Kyunki `10` truthy hai.

`or` ko already pata hai ke result truthy hoga.

### Function example

```python
def check():
    print("Function executed")
    return True

print(True or check())
```

Output:

```text
True
```

`check()` execute nahi hua.

---

# 11.4 `and`

`and` ka basic logical rule:

```text
True and True   → True
True and False  → False
False and True  → False
False and False → False
```

### Example

```python
a = True
b = True

print(a and b)
```

Output:

```text
True
```

Agar ek bhi condition false ho:

```python
a = True
b = False

print(a and b)
```

Output:

```text
False
```

### Practical example

Work order ko close karna hai agar:

1. Work complete ho
2. Technician ne comment diya ho

```python
work_complete = True
comment_added = True

if work_complete and comment_added:
    print("Close work order")
```

Output:

```text
Close work order
```

Agar:

```python
work_complete = True
comment_added = False
```

to:

```text
Close work order
```

print nahi hoga.

### Important

`and` ka logical meaning:

> **Dono conditions satisfy honi chahiye.**

---

# 11.5 `or`

`or` ka basic logical rule:

```text
True or True   → True
True or False  → True
False or True  → True
False or False → False
```

Example:

```python
alarm = False
fault = True

if alarm or fault:
    print("Attention required")
```

Output:

```text
Attention required
```

Kyunki dono mein se ek condition true hai.

### Practical HVAC example

Suppose AHU mein:

* Fan fault ho
* Ya communication fault ho

to attention chahiye:

```python
fan_fault = False
communication_fault = True

if fan_fault or communication_fault:
    print("Check AHU")
```

Output:

```text
Check AHU
```

### Important

`or` ka logical meaning:

> **Kam az kam ek condition true honi chahiye.**

---

# 11.6 `not`

`not` result ko opposite kar deta hai.

```python
not True
```

result:

```text
False
```

Aur:

```python
not False
```

result:

```text
True
```

### Truth table

| Input   | `not`       | Result  |
| ------- | ----------- | ------- |
| `True`  | `not True`  | `False` |
| `False` | `not False` | `True`  |

### Example

```python
fan_running = False

if not fan_running:
    print("Fan is OFF")
```

Output:

```text
Fan is OFF
```

Kyunki:

```python
fan_running
```

ki value `False` hai.

Aur:

```python
not fan_running
```

ban gaya:

```python
True
```

---

# `not` with other values

`not` sirf `True` aur `False` ke saath nahi hota.

Python pehle value ko truthy/falsy samajhta hai.

Example:

```python
print(not 0)
```

Output:

```text
True
```

Kyunki `0` falsy hai.

```python
print(not 10)
```

Output:

```text
False
```

Kyunki `10` truthy hai.

Example:

```python
print(not "")
```

Output:

```text
True
```

Empty string falsy hai.

```python
print(not "Python")
```

Output:

```text
False
```

Non-empty string truthy hai.

---

# `and`, `or`, `not` ka comparison

| Operator | Basic rule         |
| -------- | ------------------ |
| `and`    | Dono true → true   |
| `or`     | Ek bhi true → true |
| `not`    | Opposite result    |

Example:

```python
a = True
b = False

print(a and b)
print(a or b)
print(not a)
print(not b)
```

Output:

```text
False
True
False
True
```

---

# Sabse important: `and` / `or` actual values return kar sakte hain

Ye point specially yaad rakho.

```python
print("Hello" and "Python")
```

Output:

```text
Python
```

Aur:

```python
print("" and "Python")
```

Output:

```text
```

Empty string falsy hai.

### `or`

```python
print("" or "Python")
```

Output:

```text
Python
```

Aur:

```python
print("Hello" or "Python")
```

Output:

```text
Hello
```

Isliye:

```python
and
```

aur:

```python
or
```

ko sirf `True/False` operators samajhna incomplete hai.

Python mein ye **operands ki actual value** bhi return kar sakte hain.

---

# Practical example: default value

`or` ka common practical use:

```python
name = ""

display_name = name or "Unknown"

print(display_name)
```

Output:

```text
Unknown
```

Kyunki:

```python
name
```

empty string hai, jo falsy hai.

Isliye `or` next value:

```python
"Unknown"
```

return karta hai.

Agar:

```python
name = "Muhammad"
```

ho:

```python
display_name = name or "Unknown"
```

to:

```text
Muhammad
```

milega.

---

# Practical example: work-order data

Suppose work-order mein comment kabhi empty ho sakta hai:

```python
comment = ""

final_comment = comment or "No comment provided"

print(final_comment)
```

Output:

```text
No comment provided
```

Agar comment available ho:

```python
comment = "Filter cleaned"

final_comment = comment or "No comment provided"

print(final_comment)
```

Output:

```text
Filter cleaned
```

---

# Boolean Operators ki precedence

Jab ek expression mein multiple Boolean operators hon, order important hai.

Generally:

```text
not
```

pehle evaluate hota hai, phir:

```text
and
```

phir:

```text
or
```

Example:

```python
True or False and False
```

Python pehle:

```python
False and False
```

evaluate karega:

```python
False
```

Phir:

```python
True or False
```

result:

```text
True
```

Clear code ke liye parentheses use karna better hai:

```python
True or (False and False)
```

---

# Real-world condition example

Suppose equipment ko maintenance ke liye select karna hai:

```python
temperature = 30
fan_fault = False
communication_fault = True

if temperature > 25 and (fan_fault or communication_fault):
    print("Maintenance required")
```

Breakdown:

```python
temperature > 25
```

→ `True`

```python
fan_fault or communication_fault
```

→ `True`

Then:

```python
True and True
```

→ `True`

Output:

```text
Maintenance required
```

---

# Common mistakes

### Mistake 1

```python
if temperature > 20 and < 30:
```

❌ Invalid syntax.

Correct:

```python
if temperature > 20 and temperature < 30:
```

Ya Python ka cleaner chained comparison:

```python
if 20 < temperature < 30:
```

---

### Mistake 2

```python
if x == 10 or 20:
```

Ye beginners ki common mistake hai.

Iska matlab ye nahi:

```text
x == 10 OR x == 20
```

Correct:

```python
if x == 10 or x == 20:
```

Ya:

```python
if x in (10, 20):
```

---

# Final Mental Model

```text
and
↓
Dono conditions/value chain mein pehli falsy value tak jaata hai;
agar sab truthy hon to last value return hoti hai.

or
↓
Pehli truthy value return karta hai;
agar sab falsy hon to last value return hoti hai.

not
↓
Truthy → False
Falsy  → True
```

Simple beginner memory:

```text
AND = dono chahiye
OR  = koi ek chalega
NOT = ulta
```

Aur Python ka important advanced point:

```python
and / or
```

**sirf `True` / `False` return karna guaranteed nahi karte; ye actual operand values return kar sakte hain.**
