# Chapter 29: Basic Input and Output

Python program mein generally do basic activities hoti hain:

```text
Input  → Program data leta hai
Output → Program result deta hai
```

Example:

```python
name = input("Enter your name: ")

print("Hello", name)
```

Yahan:

```text
input()  → Input
print()  → Output
```

---

# Section 29.1: Using the `print()` Function

Python mein output display karne ke liye `print()` use hota hai.

## Basic Example

```python
print("Hello World")
```

Output:

```text
Hello World
```

Numbers:

```python
print(100)
```

Output:

```text
100
```

Expressions:

```python
print(10 + 20)
```

Output:

```text
30
```

---

## Multiple Values Print Karna

```python
name = "AHU-001"
temperature = 24

print(name, temperature)
```

Output:

```text
AHU-001 24
```

By default `print()` multiple arguments ke darmiyan **space** lagata hai.

---

## `sep` Parameter

`print()` ka `sep` parameter separator control karta hai.

```python
print("AHU-001", "Level 10", 24, sep=" | ")
```

Output:

```text
AHU-001 | Level 10 | 24
```

Default:

```python
print("A", "B", "C")
```

Output:

```text
A B C
```

Yani default:

```python
sep=" "
```

---

## `sep` ke practical examples

Comma:

```python
print("AHU-001", "Running", sep=", ")
```

Output:

```text
AHU-001, Running
```

Dash:

```python
print("2026", "10", "02", sep="-")
```

Output:

```text
2026-10-02
```

No separator:

```python
print("ABC", "123", sep="")
```

Output:

```text
ABC123
```

---

## `end` Parameter

Normally `print()` ke end par newline hoti hai.

```python
print("Hello")
print("World")
```

Output:

```text
Hello
World
```

Internally approximately:

```python
print("Hello", end="\n")
```

`\n` ka matlab newline hai.

Agar `end` change karein:

```python
print("Hello", end=" ")
print("World")
```

Output:

```text
Hello World
```

---

## `end` ke saath `|`

```python
print("AHU-001", end=" | ")
print("Running")
```

Output:

```text
AHU-001 | Running
```

---

## f-string ke saath `print()`

Modern Python mein f-string bohat useful hai:

```python
equipment_id = "AHU-001"
temperature = 24

print(f"{equipment_id} temperature is {temperature}°C")
```

Output:

```text
AHU-001 temperature is 24°C
```

---

# Section 29.2: Input from a File

Program sirf keyboard se input nahi leta. File se bhi data read kar sakta hai.

Python mein file open karne ke liye `open()` use hota hai.

Example file:

```text
equipment.txt
```

Content:

```text
AHU-001
AHU-002
VAV-001
```

Python:

```python
file = open("equipment.txt", "r")

content = file.read()

print(content)

file.close()
```

Output:

```text
AHU-001
AHU-002
VAV-001
```

Yahan:

```python
open("equipment.txt", "r")
```

mein:

```text
equipment.txt → file name
r              → read mode
```

---

# Better Way: `with open()`

Recommended approach:

```python
with open("equipment.txt", "r") as file:
    content = file.read()

print(content)
```

`with` use karne ka advantage ye hai ke Python file ko automatically close kar deta hai.

Isliye generally:

```python
with open(...) as file:
```

prefer karein.

---

## File ka complete content: `read()`

```python
with open("equipment.txt", "r") as file:
    content = file.read()

print(content)
```

`read()` poori file ko ek string ke form mein read karta hai.

---

## File ki lines: `readlines()`

```python
with open("equipment.txt", "r") as file:
    lines = file.readlines()

print(lines)
```

Agar file mein:

```text
AHU-001
AHU-002
VAV-001
```

ho to approximately:

```python
[
    "AHU-001\n",
    "AHU-002\n",
    "VAV-001\n"
]
```

`readlines()` list return karta hai.

---

## File ko line-by-line read karna

Large files ke liye:

```python
with open("equipment.txt", "r") as file:
    for line in file:
        print(line)
```

Lekin yahan ek issue hai.

File ki line mein already `\n` hota hai aur `print()` bhi newline add karta hai.

Isliye extra blank lines aa sakti hain.

Better:

```python
with open("equipment.txt", "r") as file:
    for line in file:
        print(line.strip())
```

`strip()` line ke beginning/end ke unwanted whitespace aur newline ko remove karta hai.

---

## Practical Work-Order Example

Suppose file:

```text
WO1001
WO1002
WO1003
```

Code:

```python
with open("work_orders.txt", "r") as file:
    for work_order in file:
        work_order = work_order.strip()
        print(f"Processing {work_order}")
```

Output:

```text
Processing WO1001
Processing WO1002
Processing WO1003
```

Ye pattern automation scripts mein bohat common hai.

---

# Section 29.3: Read from `stdin`

`stdin` ka matlab:

> Standard Input

Normally keyboard input `stdin` se aata hai.

Python mein:

```python
import sys

data = sys.stdin.read()

print(data)
```

Agar input provide kiya jaye:

```text
AHU-001
AHU-002
VAV-001
```

to:

```python
sys.stdin.read()
```

poora input read karega.

---

## `sys.stdin.readline()`

Ek line read karne ke liye:

```python
import sys

line = sys.stdin.readline()

print(line)
```

`input()` bhi normally standard input se line read karta hai, lekin user prompt ke liye zyada convenient hai.

---

## `sys.stdin` ko loop karna

Multiple lines:

```python
import sys

for line in sys.stdin:
    print(line.strip())
```

Ye useful hai jab program ko piped input ya redirected file se data mil raha ho.

Example command-line concept:

```text
some_command | python program.py
```

Yahan previous command ka output Python program ke `stdin` mein aa sakta hai.

---

# `stdin`, `stdout`, `stderr`

Python mein standard streams commonly:

```text
stdin   → input
stdout  → normal output
stderr  → error output
```

Python:

```python
import sys
```

ke baad:

```python
sys.stdin
sys.stdout
sys.stderr
```

available hote hain.

Normal:

```python
print("Hello")
```

normally `stdout` par output karta hai.

---

# Section 29.4: Using `input()` and `raw_input()`

## `input()` in Python 3

Modern Python mein:

```python
name = input("Enter your name: ")

print(f"Hello {name}")
```

Agar user enter kare:

```text
Muhammad
```

to:

```python
name
```

mein string milegi:

```python
"Muhammad"
```

### Important

Python 3 mein `input()` **string return karta hai**.

Example:

```python
age = input("Enter your age: ")

print(type(age))
```

Agar user:

```text
30
```

enter kare, output:

```text
<class 'str'>
```

Yani `"30"` string hai, integer `30` nahi.

---

## Number Input

Integer chahiye:

```python
age = int(input("Enter your age: "))
```

Float:

```python
temperature = float(input("Enter temperature: "))
```

Example:

```python
temperature = float(input("Enter temperature: "))

print(temperature + 1)
```

Agar user:

```text
24.5
```

enter kare:

```text
25.5
```

---

# `raw_input()` — Python 2

Book mein agar:

```python
raw_input()
```

mentioned hai to ye **Python 2** ka function hai.

Python 2 mein:

```python
raw_input()
```

user input ko string ke form mein return karta tha.

Python 3 mein:

```python
raw_input()
```

exist nahi karta.

Python 3 mein equivalent:

```python
input()
```

hai.

### Important mapping

```text
Python 2:
raw_input() → string input

Python 3:
input() → string input
```

Python 2 ka `input()` different behavior rakhta tha aur user-entered expression ko evaluate kar sakta tha, isliye modern Python 3 code mein `input()` ka behavior usse different samjhein.

Aaj agar aap Python 3 use kar rahe hain:

```python
input()
```

use karein.

---

# Section 29.5: Function to Prompt User for a Number

Kabhi user se number lena ho aur ensure karna ho ke input actually number ho.

Simple version:

```python
def get_number():
    return int(input("Enter a number: "))
```

Use:

```python
number = get_number()

print(number)
```

Agar user:

```text
25
```

enter kare:

```text
25
```

mil jayega.

Lekin agar user:

```text
abc
```

enter kare:

```text
ValueError
```

aa jayega.

Isliye better version validation ke saath banate hain.

---

## `try/except` ke saath

```python
def get_number():
    while True:
        try:
            return int(input("Enter a number: "))
        except ValueError:
            print("Please enter a valid number.")
```

Ab:

```text
Enter a number: abc
Please enter a valid number.
Enter a number: hello
Please enter a valid number.
Enter a number: 25
```

Function `25` return karega.

---

## Float number ke liye

Agar decimal values allow karni hon:

```python
def get_number():
    while True:
        try:
            return float(input("Enter a number: "))
        except ValueError:
            print("Please enter a valid number.")
```

Ab:

```text
Enter a number: 24.5
```

return:

```python
24.5
```

---

## HVAC Example

Temperature input:

```python
def get_temperature():
    while True:
        try:
            return float(input("Enter temperature °C: "))
        except ValueError:
            print("Invalid temperature. Please enter a number.")
```

Use:

```python
temperature = get_temperature()

print(f"Temperature = {temperature}°C")
```

Example:

```text
Enter temperature °C: abc
Invalid temperature. Please enter a number.
Enter temperature °C: 24.5
Temperature = 24.5°C
```

---

## Minimum/Maximum Validation

Sirf number hona enough nahi. Range bhi validate kar sakte hain.

Example:

```python
def get_temperature():
    while True:
        try:
            temperature = float(input("Enter temperature °C: "))

            if 0 <= temperature <= 50:
                return temperature

            print("Temperature must be between 0 and 50.")

        except ValueError:
            print("Please enter a valid number.")
```

Ab:

```text
Enter temperature °C: 100
Temperature must be between 0 and 50.

Enter temperature °C: 24.5
```

Function:

```python
24.5
```

return karega.

---

# Section 29.6: Printing a String Without a Newline at the End

Normally:

```python
print("Hello")
print("World")
```

Output:

```text
Hello
World
```

Kyun?

Kyuki `print()` ka default:

```python
end="\n"
```

hota hai.

---

## Newline remove karna

```python
print("Hello", end="")
print("World")
```

Output:

```text
HelloWorld
```

---

## Space ke saath

```python
print("Hello", end=" ")
print("World")
```

Output:

```text
Hello World
```

---

## Same line par multiple prints

```python
print("Processing", end="...")
print("Done")
```

Output:

```text
Processing...Done
```

---

# Progress Display Example

```python
for i in range(1, 6):
    print(i, end=" ")
```

Output:

```text
1 2 3 4 5
```

Agar normal `print()` hota:

```python
for i in range(1, 6):
    print(i)
```

Output:

```text
1
2
3
4
5
```

---

# `print()` ka Important Mental Model

`print()` ka basic structure:

```python
print(*objects, sep=" ", end="\n")
```

Example:

```python
print("A", "B", "C", sep="-", end="!")
```

Output:

```text
A-B-C!
```

Yahan:

```text
objects → "A", "B", "C"
sep     → "-"
end     → "!"
```

---

# Input aur Output ka Complete Flow

Ek simple program:

```python
name = input("Enter equipment ID: ")

print(f"Equipment: {name}")
```

Flow:

```text
User
 ↓
input()
 ↓
String
 ↓
Variable
 ↓
print()
 ↓
Screen
```

Number ke saath:

```python
temperature = float(input("Enter temperature: "))

if temperature > 25:
    print("High temperature")
else:
    print("Normal temperature")
```

Flow:

```text
User enters "26.5"
        ↓
input()
        ↓
"26.5"  ← string
        ↓
float()
        ↓
26.5    ← float
        ↓
comparison
        ↓
print()
```

---

# File Input ka Flow

```text
File
 ↓
open()
 ↓
read() / readline() / iteration
 ↓
Python variable
 ↓
process
 ↓
print()
```

Example:

```python
with open("equipment.txt") as file:
    for line in file:
        equipment_id = line.strip()
        print(equipment_id)
```

---

# Important Differences

| Function/Concept   | Purpose                                                         |
| ------------------ | --------------------------------------------------------------- |
| `print()`          | Output display karna                                            |
| `input()`          | User se ek line input lena                                      |
| `open()`           | File open karna                                                 |
| `file.read()`      | Complete file read karna                                        |
| `file.readline()`  | Ek line read karna                                              |
| `file.readlines()` | Lines ki list lena                                              |
| `sys.stdin`        | Standard input stream                                           |
| `raw_input()`      | Python 2 ka input function                                      |
| `end=`             | `print()` ke end ko control karta hai                           |
| `sep=`             | Multiple printed values ke darmiyan separator control karta hai |

---

# Important Beginner Mistakes

## Mistake 1: `input()` ko number samajhna

```python
age = input("Age: ")

print(age + 5)
```

Agar `30` enter kiya to error aa sakta hai, kyun ke `age` string hai.

Correct:

```python
age = int(input("Age: "))

print(age + 5)
```

---

## Mistake 2: File close karna bhoolna

Manual:

```python
file = open("data.txt")
data = file.read()
file.close()
```

Better:

```python
with open("data.txt") as file:
    data = file.read()
```

---

## Mistake 3: `raw_input()` ko Python 3 mein use karna

```python
raw_input("Enter value: ")
```

Python 3 mein use na karein.

Use:

```python
input("Enter value: ")
```

---

## Mistake 4: `print()` mein extra newline

```python
for i in range(5):
    print(i)
```

Agar same line chahiye:

```python
for i in range(5):
    print(i, end=" ")
```

---

# Practical Work-Order Example

Suppose user se Work Order Number aur temperature lena hai:

```python
work_order = input("Enter Work Order Number: ")

while True:
    try:
        temperature = float(input("Enter temperature °C: "))
        break
    except ValueError:
        print("Please enter a valid number.")

print()
print("Work Order:", work_order)
print("Temperature:", temperature)
```

Example:

```text
Enter Work Order Number: WO10025
Enter temperature °C: abc
Please enter a valid number.
Enter temperature °C: 24.5

Work Order: WO10025
Temperature: 24.5
```

---

# Chapter 29 Summary

Sabse important concepts:

### 1. Output

```python
print("Hello")
```

### 2. Separator

```python
print("A", "B", sep="-")
```

Output:

```text
A-B
```

### 3. Newline control

```python
print("A", end=" ")
print("B")
```

Output:

```text
A B
```

### 4. User input

```python
name = input("Name: ")
```

`input()` Python 3 mein string return karta hai.

### 5. Integer input

```python
number = int(input("Number: "))
```

### 6. Float input

```python
temperature = float(input("Temperature: "))
```

### 7. File input

```python
with open("data.txt") as file:
    data = file.read()
```

### 8. Standard input

```python
import sys

data = sys.stdin.read()
```

### 9. Python 2 vs Python 3

```text
Python 2 → raw_input()
Python 3 → input()
```

### 10. Number validation

```python
try:
    number = int(input("Number: "))
except ValueError:
    print("Invalid number")
```

## Final Mental Model

```text
                 INPUT
                   ↓
        ┌──────────────────┐
        │  input()         │
        │  sys.stdin       │
        │  File            │
        └────────┬─────────┘
                 ↓
             Python Data
                 ↓
              Process
                 ↓
        ┌────────┴─────────┐
        │     OUTPUT       │
        │     print()      │
        └──────────────────┘
```

**Core idea:** Python mein input different sources se aa sakta hai — user, file, ya `stdin` — aur output commonly `print()` ke through diya jata hai. `input()` se milne wali value ko number ke taur par use karna ho to `int()` ya `float()` conversion zaroori hoti hai.
