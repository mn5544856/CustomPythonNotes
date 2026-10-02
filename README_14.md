# Chapter 14: Conditionals

**Conditional statements** ka use program mein decision lene ke liye hota hai.

Misal ke taur par:

* Agar temperature 25 se zyada ho, to warning show karo.
* Agar work order complete ho, to usko close karo.
* Agar equipment mein fault ho, to maintenance required show karo.

Python mein conditions ke liye ye keywords aur expressions use hote hain:

```python
if
elif
else
```

---

# 14.1 Conditional Expression (or "The Ternary Operator")

Conditional expression ek short way hai `if-else` likhne ka.

Isko **ternary operator** bhi kaha jata hai.

### Normal if-else

```python
temperature = 30

if temperature > 25:
    status = "High"
else:
    status = "Normal"

print(status)
```

Output:

```text
High
```

### Conditional expression

Wahi code short form mein:

```python
temperature = 30

status = "High" if temperature > 25 else "Normal"

print(status)
```

Output:

```text
High
```

Syntax:

```python
value_if_true if condition else value_if_false
```

Iska matlab:

* Agar condition `True` hai, to `value_if_true` select hogi.
* Agar condition `False` hai, to `value_if_false` select hogi.

### Example 2

```python
age = 20

result = "Adult" if age >= 18 else "Minor"

print(result)
```

Output:

```text
Adult
```

Agar `age = 15` ho:

```python
age = 15

result = "Adult" if age >= 18 else "Minor"

print(result)
```

Output:

```text
Minor
```

### HVAC example

```python
temperature = 28

status = "High Temperature" if temperature > 25 else "Normal Temperature"

print(status)
```

Output:

```text
High Temperature
```

### Conditional expression kab use karein?

Jab condition simple ho aur sirf ek value select karni ho, tab conditional expression useful hai.

Complex conditions ke liye normal `if-else` zyada readable hota hai.

---

# 14.2 `if`, `elif`, and `else`

Python mein multiple conditions check karne ke liye `if`, `elif` aur `else` use hote hain.

## `if`

`if` condition check karta hai.

```python
temperature = 30

if temperature > 25:
    print("Temperature is high")
```

Output:

```text
Temperature is high
```

Agar condition `False` ho, to `if` ke andar ka code execute nahi hoga.

## `else`

`else` tab execute hota hai jab `if` condition false ho.

```python
temperature = 20

if temperature > 25:
    print("High")
else:
    print("Normal")
```

Output:

```text
Normal
```

## `elif`

`elif` ka matlab hai **else if**.

Jab pehli condition false ho, Python `elif` ki condition check karta hai.

```python
temperature = 22

if temperature > 30:
    print("Very High")
elif temperature > 25:
    print("High")
elif temperature > 18:
    print("Normal")
else:
    print("Low")
```

Output:

```text
Normal
```

### Step-by-step execution

Temperature `22` hai.

1. `temperature > 30` → `False`
2. `temperature > 25` → `False`
3. `temperature > 18` → `True`

Python `Normal` print karta hai aur baqi conditions check nahi karta.

### Important rule

Python `if-elif-else` chain mein pehli true condition ka block execute karta hai. Uske baad chain se bahar aa jata hai.

### Multiple conditions

```python
temperature = 22

if temperature < 18:
    print("Low")
elif temperature <= 25:
    print("Normal")
else:
    print("High")
```

Output:

```text
Normal
```

### Work-order priority example

```python
priority = "High"

if priority == "Critical":
    print("Immediate response")
elif priority == "High":
    print("Urgent response")
elif priority == "Medium":
    print("Normal response")
else:
    print("Low priority")
```

Output:

```text
Urgent response
```

### Nested `if`

Ek `if` ke andar doosra `if` bhi likh sakte hain.

```python
fan_running = True
temperature = 30

if fan_running:
    if temperature > 25:
        print("Fan is running, but temperature is high")
```

Output:

```text
Fan is running, but temperature is high
```

Nested conditions mein indentation bohat important hai.

---

# 14.3 Truth Values

Python mein condition evaluate hone par truth value milti hai:

```python
True
False
```

Lekin har condition mein zaroori nahi ke actual Boolean value ho. Python doosri values ko bhi truthy ya falsy treat karta hai.

## Truthy values

Aisi values jo condition mein `True` ki tarah behave karti hain.

Examples:

```python
if 10:
    print("Truthy")

if "Python":
    print("Truthy")

if [1, 2, 3]:
    print("Truthy")
```

Output:

```text
Truthy
Truthy
Truthy
```

## Falsy values

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

Example:

```python
if 0:
    print("Truthy")
else:
    print("Falsy")
```

Output:

```text
Falsy
```

Empty string:

```python
name = ""

if name:
    print("Name available")
else:
    print("Name is empty")
```

Output:

```text
Name is empty
```

Non-empty string:

```python
name = "Muhammad"

if name:
    print("Name available")
else:
    print("Name is empty")
```

Output:

```text
Name available
```

## `bool()` function

Kisi value ki Boolean interpretation check karne ke liye `bool()` use kar sakte hain.

```python
print(bool(0))
print(bool(10))
print(bool(""))
print(bool("Hello"))
print(bool(None))
```

Output:

```text
False
True
False
True
False
```

### Practical example: work-order comment

```python
comment = ""

if comment:
    print("Comment available")
else:
    print("Comment missing")
```

Output:

```text
Comment missing
```

Yahan empty string falsy hai, isliye `else` execute hua.

**Yaad rakho:** `if` condition mein Python value ki truthiness check karta hai. Zaroori nahi ke condition ka result explicitly `True` ya `False` ho.

---

# 14.4 Boolean Logic Expressions

Boolean logic expressions mein conditions ko combine kiya jata hai.

Python ke three main logical operators hain:

| Operator | Meaning                         |
| -------- | ------------------------------- |
| `and`    | Dono conditions true hon        |
| `or`     | Kam az kam ek condition true ho |
| `not`    | Boolean result ko reverse kare  |

## `and`

```python
temperature = 30
fan_running = True

if temperature > 25 and fan_running:
    print("High temperature while fan is running")
```

Output:

```text
High temperature while fan is running
```

Dono conditions true hain.

Agar ek bhi false ho, to complete `and` expression false hoga.

## `or`

```python
fan_fault = False
communication_fault = True

if fan_fault or communication_fault:
    print("Fault detected")
```

Output:

```text
Fault detected
```

Ek condition true hai, isliye `or` expression true hai.

## `not`

```python
fan_running = False

if not fan_running:
    print("Fan is stopped")
```

Output:

```text
Fan is stopped
```

`not False` ka result `True` hai.

## Combined Boolean expression

```python
temperature = 30
fan_running = True
fault = False

if temperature > 25 and fan_running and not fault:
    print("Check temperature")
```

Output:

```text
Check temperature
```

Breakdown:

```text
temperature > 25  → True
fan_running       → True
not fault         → True
```

Final expression:

```python
True and True and True
```

Result:

```text
True
```

## Parentheses ka use

Complex Boolean expressions mein parentheses se logic clear hota hai.

```python
fan_fault = False
communication_fault = True
temperature = 30

if (fan_fault or communication_fault) and temperature > 25:
    print("Maintenance required")
```

Output:

```text
Maintenance required
```

Pehle fault conditions ka `or` evaluate hota hai, phir temperature condition ke saath `and` hota hai.

### Short-circuit evaluation

`and` aur `or` short-circuit kar sakte hain.

```python
def check():
    print("Checking...")
    return True

print(False and check())
```

Output:

```text
False
```

`check()` execute nahi hua, kyunki `False and ...` ka result pehle se falsy hota hai.

Isi tarah:

```python
print(True or check())
```

Output:

```text
True
```

Is baar bhi `check()` execute nahi hota.

---

# 14.5 Using the `cmp` function to get the comparison result of two objects

`cmp()` Python 2 ka built-in function tha. Python 3 mein ise remove kar diya gaya hai.

Python 2 mein:

```python
cmp(a, b)
```

ka result hota tha:

| Comparison | Result |
| ---------- | -----: |
| `a < b`    |   `-1` |
| `a == b`   |    `0` |
| `a > b`    |    `1` |

### Python 2 ka example

```python
print(cmp(10, 20))
print(cmp(20, 20))
print(cmp(30, 20))
```

Python 2 output:

```text
-1
0
1
```

### Python 3 mein kya karein?

Python 3 mein comparison operators use karo:

```python
a = 10
b = 20

print(a < b)
print(a == b)
print(a > b)
```

Output:

```text
True
False
False
```

Agar tumhein `-1`, `0`, `1` jaisa result chahiye, to khud condition likh sakte ho:

```python
a = 10
b = 20

if a < b:
    result = -1
elif a > b:
    result = 1
else:
    result = 0

print(result)
```

Output:

```text
-1
```

Ye simple numeric comparison ke liye kaam karta hai.

### Important

`cmp()` Python 3 mein available nahi hai. Modern Python code mein `==`, `<`, `>`, `<=` aur `>=` use karo.

---

# 14.6 Else statement

`else` ek alternate block hai. Ye tab execute hota hai jab uske corresponding `if` ya `if-elif` chain ki koi condition true nahi hoti.

Example:

```python
temperature = 20

if temperature > 25:
    print("High")
else:
    print("Normal")
```

Output:

```text
Normal
```

## `else` ke saath `elif`

```python
temperature = 15

if temperature > 30:
    print("Very High")
elif temperature > 25:
    print("High")
elif temperature >= 18:
    print("Normal")
else:
    print("Low")
```

Output:

```text
Low
```

Sab conditions false hain, isliye `else` execute hua.

## `else` optional hai

Har `if` ke saath `else` likhna zaroori nahi.

```python
temperature = 30

if temperature > 25:
    print("High")
```

Output:

```text
High
```

Agar condition false hoti, to kuch bhi print nahi hota.

## `else` ki indentation

Correct:

```python
if temperature > 25:
    print("High")
else:
    print("Normal")
```

`else` ko `if` ke same indentation level par likhna hota hai.

Incorrect indentation se `IndentationError` ya `SyntaxError` aa sakta hai.

---

# 14.7 Testing if an object is None and assigning it

Python mein `None` ka matlab hai ke kisi variable mein abhi koi meaningful value nahi hai, ya value intentionally absent hai.

Example:

```python
comment = None
```

`None` check karne ka recommended tareeqa:

```python
if comment is None:
    print("No comment")
```

Output:

```text
No comment
```

## `is None` kyun use karte hain?

Python mein `is` identity operator hai. `is None` specifically check karta hai ke object `None` hi hai.

Recommended:

```python
if comment is None:
    print("Missing")
```

`None` check karne ke liye `== None` ke bajaye `is None` use karo.

## `is not None`

Agar check karna ho ke value `None` nahi hai:

```python
comment = "Filter cleaned"

if comment is not None:
    print(comment)
```

Output:

```text
Filter cleaned
```

## `None` ke liye default value assign karna

Example:

```python
comment = None

if comment is None:
    comment = "No comment provided"

print(comment)
```

Output:

```text
No comment provided
```

Agar comment pehle se maujood ho:

```python
comment = "Filter cleaned"

if comment is None:
    comment = "No comment provided"

print(comment)
```

Output:

```text
Filter cleaned
```

Yahan existing value overwrite nahi hui.

## Short form: conditional expression

Isi ka short version:

```python
comment = None

comment = "No comment provided" if comment is None else comment

print(comment)
```

Output:

```text
No comment provided
```

## Short form: `or` ka use

Agar tum `None` ke saath empty string ko bhi missing treat karna chahte ho, to `or` use kar sakte ho:

```python
comment = ""

comment = comment or "No comment provided"

print(comment)
```

Output:

```text
No comment provided
```

Lekin dhyan do:

```python
comment = 0
comment = comment or 100
print(comment)
```

Output:

```text
100
```

`or` har falsy value ko replace kar sakta hai, sirf `None` ko nahi.

Agar sirf `None` replace karna hai, to explicit check behtar hai:

```python
value = 0

if value is None:
    value = 100

print(value)
```

Output:

```text
0
```

## Practical work-order example

```python
def process_work_order(work_order, comment=None):
    if comment is None:
        comment = "No comment provided"

    print("Work Order:", work_order)
    print("Comment:", comment)


process_work_order("WO-1001")
process_work_order("WO-1002", "AHU filter cleaned")
```

Output:

```text
Work Order: WO-1001
Comment: No comment provided
Work Order: WO-1002
Comment: AHU filter cleaned
```

Yahan function parameter `comment` ki default value `None` hai. Agar caller comment nahi deta, to function default message assign karta hai.

---

# Chapter 14: Practice Exercises

In questions ko khud solve karne ki koshish karo.

## Exercise 1: Conditional expression

```python
temperature = 32

status = "High" if temperature > 30 else "Normal"

print(status)
```

Output kya hoga?

## Exercise 2: `if-elif-else`

```python
temperature = 22

if temperature > 30:
    print("High")
elif temperature > 20:
    print("Normal")
else:
    print("Low")
```

Output kya hoga?

## Exercise 3: Truth values

```python
value = []

if value:
    print("Available")
else:
    print("Empty")
```

Output kya hoga?

## Exercise 4: Boolean logic

```python
fan_running = True
fault = False

if fan_running and not fault:
    print("Running normally")
else:
    print("Check equipment")
```

Output kya hoga?

## Exercise 5: `None`

```python
comment = None

if comment is None:
    comment = "No comment"

print(comment)
```

Output kya hoga?

---

# Chapter 14: Final Summary

| Concept                | Purpose                                                            |
| ---------------------- | ------------------------------------------------------------------ |
| `if`                   | Condition true ho to code execute karta hai                        |
| `elif`                 | Pehli condition false ho to doosri condition check karta hai       |
| `else`                 | Jab koi previous condition true na ho                              |
| Conditional expression | Short `if-else` expression                                         |
| Truthy                 | Condition mein true ki tarah behave karne wali value               |
| Falsy                  | Condition mein false ki tarah behave karne wali value              |
| `and`                  | Dono conditions true hon                                           |
| `or`                   | Kam az kam ek condition true ho                                    |
| `not`                  | Truth value reverse karta hai                                      |
| `cmp()`                | Python 2 ka comparison function; Python 3 mein remove ho chuka hai |
| `is None`              | Check karta hai ke value `None` hai                                |
| `is not None`          | Check karta hai ke value `None` nahi hai                           |

**Mental model:**

```text
Condition
    ↓
True or False?
    ↓
if / elif / else
    ↓
Selected code block executes
```

Python mein conditions ka sahi use automation aur decision-making programs ke liye fundamental hai.
