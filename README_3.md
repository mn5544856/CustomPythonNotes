# Chapter 3: Indentation

Python mein **Indentation** ka matlab hai line ke beginning mein spaces ya tabs dena.

Example:

```python
if age >= 18:
    print("Adult")
```

Yahan:

```text
if age >= 18:
```

ke baad wali line:

```python
    print("Adult")
```

4 spaces andar hai.

Ye indentation Python ko batati hai ke `print()` kis **block** ka part hai.

---

# Section 3.1 — Simple Example

## 1. Sabse Simple Example

```python
age = 25

if age >= 18:
    print("You are an adult")
```

Output:

```text
You are an adult
```

Yahan `if` ek condition check kar raha hai.

```text
if age >= 18:
        ↓
condition True
        ↓
print() execute
```

---

# 2. Indentation Kahan Hai?

Code dekho:

```python
if age >= 18:
    print("You are an adult")
```

`print()` ke before 4 spaces hain.

Visual:

```text
if age >= 18:
    print("You are an adult")
↑
4 spaces
```

Python samajhta hai:

```text
if condition:
    ↓
    ye line IF ke andar hai
```

---

# 3. Colon `:` ka Role

Python mein block start karne se pehle normally colon `:` lagta hai.

Example:

```python
if age >= 18:
    print("Adult")
```

Yahan:

```python
if age >= 18:
```

ke end par `:` hai.

Colon ka matlab samjho:

> Ab ek block start hone wala hai.

Phir indentation se Python ko batate hain ke block ke andar ka code kya hai.

---

# 4. Multiple Lines in One Block

Sirf ek line hi nahi, multiple lines bhi same block mein ho sakti hain.

```python
age = 25

if age >= 18:
    print("Adult")
    print("You can vote")
    print("You are eligible")
```

Yahan teeno `print()` same indentation level par hain.

Structure:

```text
if condition:
    ├── print()
    ├── print()
    └── print()
```

---

# 5. Indentation Change Karne Se Structure Change Ho Sakta Hai

Example:

```python
if age >= 18:
    print("Adult")

print("Program finished")
```

Yahan:

```python
print("Adult")
```

`if` ke andar hai.

Lekin:

```python
print("Program finished")
```

indent nahi hai, isliye ye `if` ke bahar hai.

Structure:

```text
if
└── print("Adult")

print("Program finished")
```

---

# 6. Compare Karo

### Code 1

```python
if age >= 18:
    print("Adult")
    print("Eligible")
```

Dono lines `if` ke andar hain.

### Code 2

```python
if age >= 18:
    print("Adult")

print("Eligible")
```

Sirf pehli line `if` ke andar hai.

`Eligible` wali line har situation mein execute hogi.

---

# 7. Indentation Python mein Important Kyun Hai?

Kuch programming languages block ke liye `{}` use karti hain.

Python indentation use karta hai.

Example Python:

```python
if temperature > 30:
    print("Temperature is high")
    print("Check HVAC")
```

Python indentation se samajhta hai ke dono lines `if` block ka part hain.

Isliye indentation Python syntax ka important part hai.

---

# 8. `if` aur `else`

Example:

```python
age = 16

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

Output:

```text
Minor
```

Structure:

```text
if condition:
    └── IF block

else:
    └── ELSE block
```

Notice:

```python
if age >= 18:
```

aur:

```python
else:
```

same indentation level par hain.

Andar wali lines 4 spaces indent hain.

---

# 9. Correct Structure

```python
if age >= 18:
    print("Adult")
else:
    print("Minor")
```

Isko visually:

```text
if
    print
else
    print
```

samjho.

---

# 10. Incorrect Structure

Example:

```python
if age >= 18:
print("Adult")
```

Ye incorrect hai.

Python ko pata nahi chalega ke `print()` `if` block ka part hai.

Usually error:

```text
IndentationError
```

aayega.

Correct:

```python
if age >= 18:
    print("Adult")
```

---

# Section 3.2 — How Indentation is Parsed

Ab thoda deeper concept samajhte hain.

Python source code ko execute karne se pehle **parse** karta hai.

Parser code ka structure samajhta hai.

Indentation parser ko batati hai:

> Kaunsi line kis block ke andar hai?

---

# 11. Indentation Levels

Example:

```python
if temperature > 30:
    print("High temperature")
    if fan_running:
        print("Fan is running")
```

Ismein multiple levels hain.

Visual:

```text
Level 0
if temperature > 30:
    ↓
Level 1
    print("High temperature")
    if fan_running:
        ↓
Level 2
        print("Fan is running")
```

Yahan:

```text
Level 0 → 0 spaces
Level 1 → 4 spaces
Level 2 → 8 spaces
```

---

# 12. Nested Block

Jab ek block ke andar doosra block ho, usko **nested block** keh sakte hain.

Example:

```python
temperature = 35
fan_running = True

if temperature > 30:
    print("High temperature")

    if fan_running:
        print("Fan is running")
```

Structure:

```text
if temperature > 30:
    ├── print()
    │
    └── if fan_running:
            └── print()
```

---

# 13. Python Indentation ko Kaise Samajhta Hai?

Python logically indentation levels maintain karta hai.

Example:

```python
if x > 10:
    print("A")
    print("B")

print("C")
```

Python isko roughly:

```text
Block 0
│
├── if x > 10
│   ├── print("A")
│   └── print("B")
│
└── print("C")
```

ki tarah structure karta hai.

---

# 14. Same Indentation = Same Block

Example:

```python
if x > 10:
    print("A")
    print("B")
    print("C")
```

Teeno lines same indentation level par hain.

Isliye teeno same `if` block ka part hain.

```text
if
├── A
├── B
└── C
```

---

# 15. Indentation Increase = New Block

Example:

```python
if x > 10:
    print("A")
```

`if` ke baad indentation increase hui.

Matlab:

```text
new block start
```

---

# 16. Indentation Decrease = Block End

Example:

```python
if x > 10:
    print("A")

print("B")
```

`print("B")` indentation level 0 par wapas aa gaya.

Iska matlab `if` block end ho gaya.

Visual:

```text
Level 0 → if
Level 1 → print A
Level 0 → print B
```

Yani:

```text
Indent increase
↓
Block enter

Indent decrease
↓
Block exit
```

Ye Chapter ka **core concept** hai.

---

# 17. `if / elif / else`

Example:

```python
temperature = 25

if temperature > 30:
    print("Hot")
elif temperature < 15:
    print("Cold")
else:
    print("Normal")
```

Structure:

```text
if
    print

elif
    print

else
    print
```

Important:

`if`, `elif`, aur `else` same level par hain.

---

# 18. Function ke Andar Indentation

Functions mein bhi indentation use hoti hai.

```python
def greet():
    print("Hello")
    print("Welcome")
```

Yahan:

```python
def greet():
```

block start karta hai.

Andar:

```python
    print("Hello")
    print("Welcome")
```

function block ka part hain.

Call:

```python
greet()
```

Output:

```text
Hello
Welcome
```

---

# 19. Loop ke Andar Indentation

`for` loop:

```python
numbers = [10, 20, 30]

for number in numbers:
    print(number)
```

`print(number)` loop ke andar hai.

Visual:

```text
for
└── print
```

---

# 20. Nested Loop

Ek loop ke andar doosra loop:

```python
for i in range(3):
    for j in range(2):
        print(i, j)
```

Indentation:

```text
Level 0
for i:
    Level 1
    for j:
        Level 2
        print()
```

Har level clearly separate hai.

---

# 21. `try / except` mein Indentation

Error handling mein bhi:

```python
try:
    number = int(input("Enter number: "))
except ValueError:
    print("Invalid number")
```

Structure:

```text
try
└── code

except
└── error handling
```

---

# 22. `with` Statement mein Indentation

Files ke saath kaam karte waqt:

```python
with open("data.txt") as file:
    data = file.read()
    print(data)
```

`data` aur `print` dono `with` block ke andar hain.

---

# Section 3.3 — Indentation Errors

Ab sabse important practical part:

**Indentation Errors**

Python indentation mein mistake hone par different errors de sakta hai.

---

# 23. `IndentationError`

Example:

```python
if age >= 18:
print("Adult")
```

Problem:

`print()` ko indent karna chahiye tha.

Correct:

```python
if age >= 18:
    print("Adult")
```

---

# 24. Expected an Indented Block

Example:

```python
if age >= 18:
```

Aur uske baad kuch nahi.

Python expect karta hai ke block ke andar code ho.

Example:

```text
IndentationError: expected an indented block
```

Correct:

```python
if age >= 18:
    print("Adult")
```

---

# 25. Unexpected Indent

Example:

```python
age = 25

    print(age)
```

Yahan unnecessary indentation hai.

Python ko Level 0 par `print()` expected tha.

Correct:

```python
age = 25

print(age)
```

---

# 26. Unindent Does Not Match Any Outer Indentation Level

Ye tab ho sakta hai jab indentation levels inconsistent hon.

Example:

```python
if x > 10:
    print("A")
      print("B")
```

Yahan second `print()` ki indentation pehli line ke indentation se match nahi karti.

Python confused ho jata hai aur error de sakta hai.

Correct:

```python
if x > 10:
    print("A")
    print("B")
```

---

# 27. Tabs vs Spaces

Python mein indentation ke liye **spaces** commonly recommended hain.

Standard convention:

```text
4 spaces = 1 indentation level
```

Example:

```python
if x > 10:
    print("A")
```

Yahan `print()` se pehle 4 spaces hain.

---

# 28. Tab aur Space Mix Karna

Ye problem create kar sakta hai.

Example concept:

```text
Line 1 → TAB
Line 2 → 4 SPACES
```

Dono visually same nazar aa sakte hain, lekin Python ke liye whitespace representation different ho sakti hai.

Isliye:

> **Tabs aur spaces ko mix mat karo.**

Modern editors usually automatically spaces insert kar dete hain.

---

# 29. VS Code mein Indentation

Agar aap VS Code use kar rahe ho, normally:

**Tab** press karne se indentation insert hoti hai.

Example:

```python
if x > 10:
    print(x)
```

Agar cursor `print()` se pehle hai:

```text
Tab
↓
indent
```

---

# 30. Indentation Remove Karna

Agar line ko ek level bahar lana ho:

**Shift + Tab**

Example:

```python
if x > 10:
    print("A")
    print("B")
```

Cursor `print("B")` par:

```text
Shift + Tab
```

se:

```python
if x > 10:
    print("A")
print("B")
```

ho jayega.

---

# 31. Real Example — HVAC

Suppose temperature check karna hai:

```python
temperature = 35

if temperature > 30:
    print("Temperature is high")
    print("Check HVAC")
```

Dono lines `if` ke andar hain.

Agar:

```python
temperature = 25
```

to dono lines execute nahi hongi.

---

# 32. Same Example with Outside Code

```python
temperature = 35

if temperature > 30:
    print("Temperature is high")
    print("Check HVAC")

print("Inspection completed")
```

Output:

```text
Temperature is high
Check HVAC
Inspection completed
```

Notice:

```text
if block
├── Temperature is high
└── Check HVAC

outside block
└── Inspection completed
```

---

# 33. Common Beginner Mistake

Galat:

```python
temperature = 35

if temperature > 30:
print("High")
print("Check HVAC")
```

Correct:

```python
temperature = 35

if temperature > 30:
    print("High")
    print("Check HVAC")
```

---

# 34. Nested HVAC Example

```python
temperature = 35
fan_status = "ON"

if temperature > 30:
    print("High temperature")

    if fan_status == "ON":
        print("Fan is running")
```

Indentation levels:

```text
if temperature > 30:          Level 0
    print(...)                 Level 1

    if fan_status == "ON":    Level 1
        print(...)             Level 2
```

Isko visually:

```text
Level 0
└── if temperature
    │
    ├── print
    │
    └── if fan_status
        │
        └── print
```

---

# 35. Important Rule — Colon + Indentation

Python blocks ko identify karne ke liye ye pattern bohat common hai:

```python
statement:
    indented code
```

Examples:

```python
if condition:
    code
```

```python
for item in items:
    code
```

```python
while condition:
    code
```

```python
def function():
    code
```

```python
try:
    code
except:
    code
```

---

# 36. Indentation ko Braces ki Jagah Samjho

Conceptually comparison:

Some languages:

```text
if (condition) {
    code
}
```

Python:

```python
if condition:
    code
```

Python mein `{}` ki jagah indentation block define karti hai.

Ye exact language syntax comparison nahi hai, lekin beginner ke liye concept samajhne ka useful tareeqa hai.

---

# 37. Indentation ka Golden Rule

Ye 4 rules yaad kar lo:

### Rule 1

Block start karne ke liye normally `:`:

```python
if condition:
```

### Rule 2

Block ke andar indentation:

```python
if condition:
    print("Hello")
```

### Rule 3

Same block = same indentation:

```python
if condition:
    print("A")
    print("B")
```

### Rule 4

Block se bahar = indentation reduce:

```python
if condition:
    print("A")

print("B")
```

---

# 38. Practice — Identify the Error

### Question 1

```python
if x > 10:
print("Greater")
```

Problem kya hai?

**Answer:** `print()` indented nahi hai.

Correct:

```python
if x > 10:
    print("Greater")
```

---

### Question 2

```python
x = 10

    print(x)
```

Problem?

**Answer:** unnecessary indentation.

Correct:

```python
x = 10

print(x)
```

---

### Question 3

```python
if x > 10:
    print("A")
      print("B")
```

Problem?

**Answer:** indentation levels match nahi kar rahe.

Correct:

```python
if x > 10:
    print("A")
    print("B")
```

---

# 39. Practice — Predict the Output

```python
x = 20

if x > 10:
    print("A")
    print("B")

print("C")
```

Output:

```text
A
B
C
```

Kyun?

`A` aur `B` `if` ke andar hain.

`C` bahar hai.

---

# 40. Another Example

```python
x = 5

if x > 10:
    print("A")

print("B")
```

Output:

```text
B
```

Kyun?

`x > 10` False hai, isliye `A` nahi chalega.

Lekin `B` `if` ke bahar hai, isliye execute hoga.

---

# 41. Nested Example

```python
x = 20
y = 5

if x > 10:
    print("A")

    if y < 10:
        print("B")

print("C")
```

Output:

```text
A
B
C
```

Structure:

```text
if x > 10
│
├── A
│
└── if y < 10
    └── B

C
```

---

# 42. Indentation ko Tree Structure ki Tarah Socho

Python code ko tree ki tarah visualize karna bohat helpful hai.

Example:

```python
if temperature > 30:
    print("High")
    if fan == "ON":
        print("Fan ON")
    print("Check system")

print("Done")
```

Tree:

```text
if temperature > 30
│
├── print("High")
│
├── if fan == "ON"
│   └── print("Fan ON")
│
└── print("Check system")

print("Done")
```

Agar indentation samajh aa gayi, Python ke `if`, `for`, `while`, functions aur nested structures samajhna bohat easy ho jata hai.

---

# Chapter 3 — Quick Revision

## Indentation

```python
if x > 10:
    print(x)
```

`print()` indented hai.

## Same Block

```python
if x > 10:
    print("A")
    print("B")
```

## Block End

```python
if x > 10:
    print("A")

print("B")
```

## Nested Block

```python
if x > 10:
    if y > 5:
        print("Yes")
```

## Function

```python
def greet():
    print("Hello")
```

## Loop

```python
for item in items:
    print(item)
```

---

# Final Mental Model

Python indentation ko is formula se yaad rakho:

```text
: 
↓
Block start

Indent increase
↓
Block ke andar

Same indentation
↓
Same block

Indent decrease
↓
Block end
```

Example:

```python
if condition:
    statement_1
    statement_2

statement_3
```

Iska meaning:

```text
IF BLOCK
├── statement_1
└── statement_2

OUTSIDE BLOCK
└── statement_3
```

### Sabse important baat

Python mein indentation **sirf decoration/formatting nahi hai**.

Ye Python program ki **structure aur scope of blocks** define karne mein directly involved hai.

Isliye indentation mistake se program ka behavior bhi change ho sakta hai aur syntax error bhi aa sakta hai.
