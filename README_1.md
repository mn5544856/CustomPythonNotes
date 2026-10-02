Perfect. Phir hum isko **proper Python learning book** ki tarah banayenge. Har section mein pehle concept, phir Roman Urdu explanation, examples aur practice hogi.

## Section 1.1 — Getting Started

### 1. Python kya hai?

**Python ek high-level, general-purpose programming language hai.**

Simple Roman Urdu mein:

> Python ek language hai jiske zariye hum computer ko instructions dete hain ke usay kya kaam karna hai.

Misal ke taur par agar hum computer ko bolna chahte hain:

> Screen par `Hello World` likho.

Python mein:

```python
print("Hello World")
```

Output:

```text
Hello World
```

---

### 2. Python kyun seekhein?

Python ko different types ke kaamon ke liye use kiya jata hai, jaise:

* Automation
* Web development
* Data analysis
* Artificial Intelligence
* Machine Learning
* Scripting
* Desktop applications
* Scientific computing

Example: agar aapko manually 1,000 files ke naam check karne hain, Python se ye kaam automate kiya ja sakta hai.

---

### 3. Pehla Python Program

Sabse simple program:

```python
print("Hello World")
```

Is code mein:

```text
print
```

ek **function** hai.

Aur:

```text
"Hello World"
```

ek **string** hai.

`print()` ka kaam hai value ko output mein display karna.

---

### 4. `print()` ke saath different values

Text:

```python
print("Python")
```

Output:

```text
Python
```

Number:

```python
print(100)
```

Output:

```text
100
```

Calculation:

```python
print(10 + 20)
```

Output:

```text
30
```

Multiple words:

```python
print("I am learning Python")
```

Output:

```text
I am learning Python
```

---

## 5. Python Comments

Comment wo text hota hai jo programmer ke liye hota hai aur Python usay execute nahi karta.

Python mein comment `#` se start hota hai.

```python
# This is a comment

print("Hello")
```

Python `# This is a comment` ko ignore karega aur sirf:

```text
Hello
```

display karega.

### Comment kyun use karte hain?

Comments code ko samajhne mein help karte hain.

Example:

```python
# Calculate total price
total = 100 + 50

print(total)
```

Yahan comment future mein humein batata hai ke neeche wala code kya kar raha hai.

---

## 6. Python mein Case Sensitivity

Python **case-sensitive** language hai.

Matlab:

```python
name
```

aur:

```python
Name
```

same nahi hain.

Example:

```python
name = "Muhammad"

print(name)
```

Ye correct hai.

Lekin:

```python
name = "Muhammad"

print(Name)
```

Error dega, kyun ke `Name` aur `name` different variables hain.

### Yaad rakhein:

```text
name ≠ Name
Name ≠ NAME
```

---

# Practice

Ab khud ye programs run karein:

### Practice 1

```python
print("My name is Muhammad")
```

### Practice 2

```python
print(25 + 75)
```

### Practice 3

```python
print("I am learning Python")
print("Python is interesting")
```

### Practice 4

Comment add karein:

```python
# My first Python program
print("Hello World")
```

---

## Quick Test

**Q1:** Python kya hai?

**Q2:** `print()` ka kya kaam hai?

**Q3:** Python mein comment kis symbol se start hota hai?

**Q4:** Kya `name` aur `Name` same hain?

**Q5:** Iska output kya hoga?

```python
print(20 + 30)
```

**Answers:**

1. Python ek programming language hai.
2. `print()` output display karta hai.
3. `#`
4. Nahi.
5. `50`

---

### Next: Section 1.2 — Creating Variables and Assigning Values

Is section mein hum **variable, value, assignment operator `=`, variable naming rules, multiple assignment, aur variable ki value change karna** detail mein seekhenge.
# Section 1.2 — Creating Variables and Assigning Values

Ab hum Python ke **sabse important basic concepts** mein se ek seekhenge: **Variables**.

---

## 1. Variable kya hota hai?

Simple Roman Urdu mein:

> **Variable ek naam hota hai jiske andar hum koi value store karte hain.**

Example:

```python
name = "Muhammad"
```

Yahan:

```text
name       → Variable
=          → Assignment operator
"Muhammad" → Value
```

Iska matlab:

> `"Muhammad"` value ko `name` naam ke variable mein store karo.

---

## 2. Variable ko use kaise karte hain?

Ab hum variable ko `print()` ke andar use kar sakte hain:

```python
name = "Muhammad"

print(name)
```

Output:

```text
Muhammad
```

Yahan `print(name)` mein hum `"Muhammad"` directly nahi likh rahe.

Python `name` variable ko dekhta hai aur uske andar stored value `"Muhammad"` ko output karta hai.

---

# 3. Different Types ki Values Store Karna

Variable mein sirf text hi nahi, different types ki values store kar sakte hain.

### String

```python
name = "Muhammad"
```

### Integer

```python
age = 25
```

### Float

```python
price = 99.50
```

### Boolean

```python
is_active = True
```

Example:

```python
name = "Muhammad"
age = 25
price = 99.50
is_active = True

print(name)
print(age)
print(price)
print(is_active)
```

Output:

```text
Muhammad
25
99.5
True
```

---

# 4. Assignment Operator `=`

Python mein:

```python
=
```

ko **assignment operator** kehte hain.

Example:

```python
age = 25
```

Iska matlab ye nahi hai:

> age aur 25 mathematically equal hain.

Programming mein iska matlab hai:

> `25` ko `age` variable mein assign/store karo.

---

## Example

```python
x = 10
```

Ab memory mein conceptually:

```text
x → 10
```

Agar hum likhein:

```python
print(x)
```

Output:

```text
10
```

---

# 5. Variable ki Value Change Karna

Python mein variable ki value baad mein change kar sakte hain.

```python
age = 25

print(age)

age = 26

print(age)
```

Output:

```text
25
26
```

Pehle:

```text
age → 25
```

Phir:

```text
age → 26
```

Yani variable ki purani value replace ho gayi.

---

# 6. Multiple Variables

Aap ek program mein bohat saare variables bana sakte hain.

```python
name = "Muhammad"
age = 25
country = "Saudi Arabia"
```

Phir:

```python
print(name)
print(age)
print(country)
```

Output:

```text
Muhammad
25
Saudi Arabia
```

---

# 7. Variable Naming Rules

Variable ka naam rakhte waqt kuch rules follow karne hote hain.

### Rule 1 — Letter ya underscore se start hona chahiye

Correct:

```python
name = "Ali"
_age = 25
```

Incorrect:

```python
2name = "Ali"
```

Number se variable start nahi kar sakta.

---

### Rule 2 — Variable name mein spaces nahi honi chahiye

Incorrect:

```python
first name = "Muhammad"
```

Correct:

```python
first_name = "Muhammad"
```

Space ki jagah commonly **underscore `_`** use karte hain.

---

### Rule 3 — Numbers variable name mein use kar sakte hain

Ye correct hai:

```python
user1 = "Ali"
```

Lekin:

```python
1user = "Ali"
```

incorrect hai, kyun ke variable number se start ho raha hai.

---

### Rule 4 — Python keywords ko variable name nahi bana sakte

Example:

```python
if
for
class
def
return
```

Ye Python ke reserved keywords hain.

Isliye:

```python
if = 10
```

nahi kar sakte.

---

# 8. Good Variable Names

Variable ka naam aisa rakho jo uski value ko clearly explain kare.

Bad:

```python
x = "Muhammad"
```

Better:

```python
name = "Muhammad"
```

Bad:

```python
x = 25
```

Better:

```python
age = 25
```

Bad:

```python
p = 500
```

Better:

```python
price = 500
```

**Rule of thumb:**

> Variable ka naam dekh kar ideally samajh aa jana chahiye ke uske andar kya data hai.

---

# 9. Multiple Assignment

Python mein ek hi line mein multiple variables assign kar sakte hain.

```python
name, age, country = "Muhammad", 25, "Saudi Arabia"
```

Ye conceptually same hai:

```python
name = "Muhammad"
age = 25
country = "Saudi Arabia"
```

Phir:

```python
print(name)
print(age)
print(country)
```

Output:

```text
Muhammad
25
Saudi Arabia
```

---

# 10. Same Value Multiple Variables mein

Aap ek hi value ko multiple variables mein assign kar sakte hain:

```python
x = y = z = 100
```

Ab:

```text
x → 100
y → 100
z → 100
```

Example:

```python
x = y = z = 100

print(x)
print(y)
print(z)
```

Output:

```text
100
100
100
```

---

# 11. Variable ke saath Calculation

Variables ke andar numbers hon to calculations kar sakte hain.

```python
price = 100
quantity = 5

total = price * quantity

print(total)
```

Output:

```text
500
```

Yahan:

```text
price    → 100
quantity → 5
total    → 500
```

Python ne:

```text
100 × 5 = 500
```

calculate kiya.

---

# 12. Variable ko Variable ke saath use karna

Example:

```python
a = 10
b = 20

c = a + b

print(c)
```

Output:

```text
30
```

Yahan Python ne:

```text
a = 10
b = 20

c = 10 + 20

c = 30
```

kiya.

---

# Important Concept

Isko achi tarah samajh lo:

```python
x = 10
```

ka matlab:

> **10 ko x mein store karo.**

Aur:

```python
y = x
```

ka matlab:

> **x ke andar jo value hai, usay y mein assign karo.**

Example:

```python
x = 10
y = x

print(y)
```

Output:

```text
10
```

---

# Practice Exercises

### Exercise 1

Ek variable `name` banao aur apna naam store karo.

### Exercise 2

`age` variable mein apni age store karo.

### Exercise 3

Do variables banao:

```text
price
quantity
```

Aur total calculate karo.

### Exercise 4

Ye code run karke output predict karo:

```python
x = 10
x = 20
print(x)
```

**Output kya hoga?**

### Exercise 5

Ye code samjho:

```python
a = 10
b = 20
a = b
print(a)
```

**Output kya hoga?**

---

## Section 1.2 ka Short Summary

```text
Variable
   ↓
Naam + Value
   ↓
name = "Muhammad"
   ↓
Variable ko use kar sakte hain
   ↓
print(name)
```

Sabse important cheezein:

* Variable data store karne ke liye use hota hai.
* `=` assignment operator hai.
* Variable ki value change ho sakti hai.
* Variable name space se start nahi ho sakta.
* Variable name number se start nahi ho sakta.
* `_` variable names mein use kar sakte hain.
* Meaningful variable names rakhna better practice hai.

**Next Section 1.3: Block Indentation** — ismein hum dekhenge ke Python mein spaces itni important kyun hain aur `if`, `for`, `while`, functions waghera ke **blocks** kaise work karte hain.
# Section 1.3 — Block Indentation

Ab hum Python ka ek **bohat important concept** seekhenge: **Indentation**.

Agar aap Python properly seekhna chahte ho, to indentation ko achi tarah samajhna zaroori hai, kyun ke Python mein indentation sirf code ko beautiful banane ke liye nahi hoti — **indentation code ka structure define karti hai.**

---

## 1. Indentation kya hoti hai?

**Indentation** ka matlab hai line ke start mein spaces dena.

Example:

```python
if age >= 18:
    print("You are an adult")
```

Yahan:

```python
    print("You are an adult")
```

ke start mein spaces hain.

Ye spaces batati hain ke `print()` **`if` ke block ka part hai**.

---

# 2. Block kya hota hai?

**Block** related statements ka group hota hai jo ek particular condition, loop, function etc. ke andar execute hota hai.

Example:

```python
if age >= 18:
    print("Adult")
    print("You can enter")
```

Yahan dono `print()` statements `if` block ke andar hain.

Conceptually:

```text
if condition:
    ├── statement 1
    └── statement 2
```

---

# 3. Colon `:` ka Role

Python mein jab hum `if`, `for`, `while`, function etc. ka block start karte hain, to generally line ke end par `:` lagate hain.

Example:

```python
if age >= 18:
    print("Adult")
```

Yahan:

```python
if age >= 18:
```

ke end mein `:` hai.

Colon Python ko signal deta hai:

> Ab is statement ka block start hone wala hai.

---

# 4. Correct Indentation

Example:

```python
age = 25

if age >= 18:
    print("You are an adult")
```

Output:

```text
You are an adult
```

Yahan `print()` indented hai, isliye wo `if` block ke andar hai.

---

# 5. Incorrect Indentation

Agar indentation na dein:

```python
age = 25

if age >= 18:
print("You are an adult")
```

Python error dega.

Kyun?

Kyun ke Python expect kar raha tha ke `if` ke baad ek indented block aaye.

---

# 6. Usually 4 Spaces

Python mein standard practice hai ke ek block ke liye **4 spaces** use karein.

Correct:

```python
if age >= 18:
    print("Adult")
```

Yahan `print()` ke before 4 spaces hain.

Aap 8 spaces se nested block bhi bana sakte hain:

```python
if age >= 18:
    if age >= 21:
        print("Age is 21 or above")
```

Structure:

```text
if age >= 18:
    └── if age >= 21:
            └── print()
```

---

# 7. Nested Blocks

Ek block ke andar doosra block ho to usay **nested block** kehte hain.

Example:

```python
age = 25

if age >= 18:
    print("Adult")

    if age >= 21:
        print("21 or older")
```

Output:

```text
Adult
21 or older
```

Yahan second `if` pehle `if` ke andar hai.

---

# 8. Indentation se Python Structure Samajhta Hai

Ye example dekho:

```python
age = 25

if age >= 18:
    print("Adult")
    print("Allowed")
    
print("Program finished")
```

Output:

```text
Adult
Allowed
Program finished
```

Yahan:

```python
    print("Adult")
    print("Allowed")
```

`if` block ke andar hain.

Lekin:

```python
print("Program finished")
```

indent nahi hai, isliye wo `if` block ke bahar hai.

---

# 9. Indentation Change Karne Se Result Change Ho Sakta Hai

Example:

```python
age = 15

if age >= 18:
    print("Adult")

print("Program finished")
```

Output:

```text
Program finished
```

Kyun?

`age` 15 hai, isliye `if` false hai.

Lekin last wala:

```python
print("Program finished")
```

`if` ke bahar hai, isliye wo execute hoga.

---

# 10. Multiple Statements in a Block

Ek block ke andar multiple statements ho sakti hain:

```python
age = 25

if age >= 18:
    print("You are an adult")
    print("You can continue")
    print("Access granted")
```

Teeno statements indented hain.

Isliye teeno `if` block ka part hain.

---

# 11. `if` aur `else` ke saath Indentation

Example:

```python
age = 15

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
    └── if block

else:
    └── else block
```

Notice karo:

```python
if age >= 18:
```

aur:

```python
else:
```

same indentation level par hain.

Lekin unke andar ke statements indented hain.

---

# 12. Indentation `for` Loop mein

Indentation sirf `if` ke saath nahi hoti.

Example:

```python
for number in [1, 2, 3]:
    print(number)
```

Output:

```text
1
2
3
```

`print(number)` loop ke block ke andar hai.

---

# 13. Indentation Function mein

Functions mein bhi indentation use hoti hai:

```python
def greet():
    print("Hello")
```

Yahan:

```python
    print("Hello")
```

function ke block ke andar hai.

Function call:

```python
greet()
```

Output:

```text
Hello
```

---

# 14. Same Block = Same Indentation

Ye correct hai:

```python
if age >= 18:
    print("Adult")
    print("Allowed")
```

Dono statements ki indentation same hai.

Lekin ye avoid karein:

```python
if age >= 18:
    print("Adult")
        print("Allowed")
```

Yahan unnecessary extra indentation hai aur Python error de sakta hai.

---

# 15. Tabs aur Spaces

Python code mein indentation ke liye **spaces** use karna recommended hai.

Common convention:

> **4 spaces per indentation level**

Modern Python editors usually indentation automatically manage karte hain.

Example:

```python
if True:
    print("Hello")
```

Editor mein `Enter` press karne par next line automatically indented ho sakti hai.

---

# Important Concept

Indentation ko sirf:

> "Line ke start mein spaces"

mat samjho.

Python ke context mein iska important meaning hai:

> **Indentation Python ko batati hai ke kaunsa code kis block ka part hai.**

Example:

```python
if condition:
    statement
```

Iska structure hai:

```text
if
└── statement
```

Aur:

```python
if condition:
    statement1
    statement2

statement3
```

ka structure hai:

```text
if
├── statement1
└── statement2

statement3
```

---

# Practice

### Exercise 1

Is code ka output kya hoga?

```python
age = 20

if age >= 18:
    print("Adult")
```

---

### Exercise 2

Is code ka output kya hoga?

```python
age = 15

if age >= 18:
    print("Adult")

print("Done")
```

---

### Exercise 3

Correct indentation lagao:

```python
if 10 > 5:
print("10 is greater")
```

Correct answer:

```python
if 10 > 5:
    print("10 is greater")
```

---

### Exercise 4

Nested block identify karo:

```python
age = 25

if age >= 18:
    print("Adult")

    if age >= 21:
        print("21 or older")
```

Yahan **second `if` pehle `if` ke andar nested hai**.

---

# Section 1.3 — Quick Summary

Yaad rakhne ke liye:

```text
Indentation
     ↓
Spaces at beginning of line
     ↓
Defines code block
     ↓
Usually 4 spaces
     ↓
Used with if / else / for / while / functions
```

### Golden Rule

```python
if condition:
    # 4 spaces
    statement
```

**Colon `:` block start karta hai, aur indentation batati hai ke block ke andar kya hai.**

**Next Section 1.4 — Datatypes:** hum `int`, `float`, `str`, `bool`, `None`, `type()` aur type conversion (`int()`, `float()`, `str()`) ko detail mein samjhenge.
# Section 1.4 — Datatypes

Ab hum Python ke ek aur **fundamental concept** par aate hain: **Datatypes**.

Simple Roman Urdu mein:

> **Datatype batata hai ke kisi variable ke andar kis type ka data stored hai.**

Example:

```python
age = 25
```

Yahan `25` ek **integer (`int`)** hai.

Aur:

```python
name = "Muhammad"
```

Yahan `"Muhammad"` ek **string (`str`)** hai.

---

# 1. Datatype ki zaroorat kyun hai?

Computer ke liye ye samajhna important hai ke data kis type ka hai.

Example:

```python
age = 25
```

Yahan hum `25` ko number samajhte hain.

Lekin:

```python
age = "25"
```

Yahan `25` quotation marks ke andar hai, isliye Python isay **text/string** samjhega.

Dono dekhne mein similar hain:

```text
25
"25"
```

Lekin Python ke liye dono different hain.

```python
age1 = 25
age2 = "25"

print(type(age1))
print(type(age2))
```

Output:

```text
<class 'int'>
<class 'str'>
```

---

# 2. Python ke Common Datatypes

Is chapter mein sabse pehle ye datatypes samajhna important hai:

| Datatype   | Example          | Meaning        |
| ---------- | ---------------- | -------------- |
| `int`      | `25`             | Whole number   |
| `float`    | `25.5`           | Decimal number |
| `str`      | `"Hello"`        | Text           |
| `bool`     | `True` / `False` | True or False  |
| `NoneType` | `None`           | No value       |

Baad mein hum collection datatypes jaise `list`, `tuple`, `set`, aur `dict` detail mein dekhenge.

---

# 3. Integer — `int`

Integer ka matlab hai **whole number**.

Example:

```python
age = 25
```

`25` ka datatype `int` hai.

Aur:

```python
temperature = -10
```

Ye bhi `int` hai.

Examples:

```text
10
0
-5
100
1000
```

Sab integers hain.

### Check karna

```python
age = 25

print(type(age))
```

Output:

```text
<class 'int'>
```

---

# 4. Float — `float`

Float decimal number ko represent karta hai.

Example:

```python
price = 99.50
```

Yahan `99.50` ka datatype `float` hai.

Aur:

```python
temperature = 36.5
```

Ye bhi float hai.

Examples:

```text
10.5
99.99
0.5
-12.75
```

Check:

```python
price = 99.50

print(type(price))
```

Output:

```text
<class 'float'>
```

---

# 5. String — `str`

String ka matlab hai **text**.

String ko quotes ke andar likhte hain.

Double quotes:

```python
name = "Muhammad"
```

Single quotes:

```python
name = 'Muhammad'
```

Dono valid hain.

Example:

```python
city = "Riyadh"
country = "Saudi Arabia"
```

Dono strings hain.

Check:

```python
city = "Riyadh"

print(type(city))
```

Output:

```text
<class 'str'>
```

---

# 6. String aur Number mein Difference

Ye concept bohat important hai.

```python
x = 10
```

`x` ke andar integer hai.

Lekin:

```python
x = "10"
```

`x` ke andar string hai.

Check:

```python
x = 10
print(type(x))

x = "10"
print(type(x))
```

Output:

```text
<class 'int'>
<class 'str'>
```

### Important

```text
10   → number
"10" → text
```

---

# 7. Boolean — `bool`

Boolean datatype mein sirf do basic values hoti hain:

```python
True
False
```

Example:

```python
is_active = True
```

Aur:

```python
is_logged_in = False
```

Check:

```python
is_active = True

print(type(is_active))
```

Output:

```text
<class 'bool'>
```

---

## Boolean ka real-life example

Socho ek employee active hai ya nahi:

```python
employee_active = True
```

Ya koi user logged in hai:

```python
user_logged_in = True
```

Agar user logged in nahi hai:

```python
user_logged_in = False
```

Boolean mostly conditions ke saath bohat use hota hai.

---

# 8. `None`

Python mein `None` ka matlab generally:

> **Abhi koi value nahi hai.**

Example:

```python
result = None
```

Check:

```python
print(type(result))
```

Output:

```text
<class 'NoneType'>
```

`None` ko `0` ya empty string samajhna nahi chahiye.

```text
None → no value
0    → number zero
""   → empty string
```

Ye teen different concepts hain.

---

# 9. `type()` Function

Kisi value ya variable ka datatype check karne ke liye:

```python
type()
```

use karte hain.

Example:

```python
x = 100

print(type(x))
```

Output:

```text
<class 'int'>
```

Example:

```python
name = "Ali"

print(type(name))
```

Output:

```text
<class 'str'>
```

Example:

```python
price = 50.5

print(type(price))
```

Output:

```text
<class 'float'>
```

---

# 10. Type Conversion

Kabhi humein ek datatype ko doosre datatype mein convert karna hota hai.

Isay **type conversion** kehte hain.

Common functions:

```text
int()
float()
str()
bool()
```

---

## String → Integer

Example:

```python
age = "25"

age = int(age)

print(age)
print(type(age))
```

Output:

```text
25
<class 'int'>
```

Pehle:

```text
"25" → str
```

Conversion ke baad:

```text
25 → int
```

---

# 11. Integer → String

```python
age = 25

age = str(age)

print(type(age))
```

Output:

```text
<class 'str'>
```

Yani:

```text
25 → "25"
```

---

# 12. Integer → Float

```python
number = 10

number = float(number)

print(number)
print(type(number))
```

Output:

```text
10.0
<class 'float'>
```

---

# 13. Float → Integer

```python
price = 99.99

price = int(price)

print(price)
```

Output:

```text
99
```

Yahan decimal portion remove ho gaya.

```text
99.99 → 99
```

Ye rounding nahi karta; decimal part ko truncate karta hai.

---

# 14. String mein Number aur Actual Number

Ye difference dobara important hai.

```python
x = "10"
y = 20
```

Agar hum:

```python
print(x + y)
```

karne ki koshish karein to error aayega, kyun ke:

```text
x → string
y → integer
```

Agar string ko integer mein convert karein:

```python
x = "10"
y = 20

print(int(x) + y)
```

Output:

```text
30
```

---

# 15. String Concatenation

Strings ko `+` se join kar sakte hain.

```python
first_name = "Muhammad"
last_name = "Ali"

full_name = first_name + " " + last_name

print(full_name)
```

Output:

```text
Muhammad Ali
```

Yahan:

```text
"Muhammad" + " " + "Ali"
```

combine hokar:

```text
"Muhammad Ali"
```

ban gaya.

---

# 16. Number Addition vs String Concatenation

Ye difference yaad rakho:

### Numbers

```python
print(10 + 20)
```

Output:

```text
30
```

### Strings

```python
print("10" + "20")
```

Output:

```text
1020
```

Kyun?

Pehle example mein numbers add hue.

Doosre mein strings combine hui.

```text
10 + 20     → 30

"10" + "20" → "1020"
```

---

# 17. `bool()` Conversion

Values ko Boolean mein bhi convert kar sakte hain.

Example:

```python
print(bool(1))
```

Output:

```text
True
```

Aur:

```python
print(bool(0))
```

Output:

```text
False
```

Empty string:

```python
print(bool(""))
```

Output:

```text
False
```

Non-empty string:

```python
print(bool("Hello"))
```

Output:

```text
True
```

Is concept ko hum conditions ke chapter mein aur deeply use karenge.

---

# 18. Ek Practical Example

Suppose ek product ka data hai:

```python
product_name = "Laptop"
price = 2500.50
quantity = 2
available = True
```

Yahan:

```text
product_name → str
price        → float
quantity     → int
available    → bool
```

Total calculate:

```python
total = price * quantity

print(total)
```

Output:

```text
5001.0
```

Ye real-world programming mein bohat common pattern hai.

---

# Practice Exercises

### Exercise 1

Datatype identify karo:

```python
x = 100
```

### Exercise 2

Datatype identify karo:

```python
x = 100.5
```

### Exercise 3

Datatype identify karo:

```python
x = "100"
```

### Exercise 4

Datatype identify karo:

```python
x = False
```

### Exercise 5

Output predict karo:

```python
x = "10"
y = "20"

print(x + y)
```

### Exercise 6

Output predict karo:

```python
x = "10"
y = 20

print(int(x) + y)
```

### Exercise 7

Iska datatype kya hoga?

```python
x = None
```

---

# Section 1.4 — Quick Summary

```text
int
 ↓
Whole numbers
25

float
 ↓
Decimal numbers
25.5

str
 ↓
Text
"Python"

bool
 ↓
True / False

None
 ↓
No value
None
```

Aur sabse important:

```python
type(value)
```

se datatype check karte hain.

Aur:

```python
int()
float()
str()
bool()
```

se values ko commonly convert kar sakte hain.

**Next Section 1.5 — Collection Types:** ismein hum `list`, `tuple`, `set`, aur `dictionary` ko detail mein samjhenge, including **indexing, mutable vs immutable, adding/removing items, aur practical examples**.
# Section 1.5 — Collection Types

Ab hum Python ke **Collection Types** seekhenge.

Simple Roman Urdu mein:

> Collection ka matlab hai **multiple values ko ek jagah store karna**.

Agar sirf ek value ho:

```python
name = "Muhammad"
```

Lekin agar multiple names store karne hon:

```python
names = ["Ali", "Ahmed", "Muhammad"]
```

To hum collection use kar sakte hain.

Python mein important collection types hain:

1. **List**
2. **Tuple**
3. **Set**
4. **Dictionary**

---

# 1. List

## List kya hai?

List ek collection hai jisme hum **multiple values** store kar sakte hain.

List square brackets `[]` mein banayi jati hai.

```python
fruits = ["Apple", "Banana", "Orange"]
```

Yahan `fruits` ek list hai.

Conceptually:

```text
fruits
  ↓
["Apple", "Banana", "Orange"]
```

List mein different types ka data bhi ho sakta hai:

```python
data = ["Muhammad", 25, 99.5, True]
```

---

# 2. List Indexing

List mein har item ka ek **index number** hota hai.

Important:

> Python mein indexing **0 se start hoti hai**.

Example:

```python
fruits = ["Apple", "Banana", "Orange"]
```

Index:

```text
Index       Value

  0       Apple
  1       Banana
  2       Orange
```

Isliye:

```python
print(fruits[0])
```

Output:

```text
Apple
```

Aur:

```python
print(fruits[1])
```

Output:

```text
Banana
```

```python
print(fruits[2])
```

Output:

```text
Orange
```

---

# 3. Negative Indexing

Python mein negative indexing bhi hoti hai.

```text
Index:       0        1         2
           Apple    Banana    Orange

Negative:   -3       -2        -1
```

Isliye:

```python
print(fruits[-1])
```

Output:

```text
Orange
```

Aur:

```python
print(fruits[-2])
```

Output:

```text
Banana
```

`-1` ka matlab hai **last item**.

---

# 4. List Item Change Karna

List **mutable** hoti hai.

### Mutable ka matlab?

> Collection banne ke baad uske andar ki values ko change kar sakte hain.

Example:

```python
fruits = ["Apple", "Banana", "Orange"]

fruits[1] = "Mango"

print(fruits)
```

Output:

```text
['Apple', 'Mango', 'Orange']
```

Pehle:

```text
Banana
```

tha.

Humne usay:

```text
Mango
```

se replace kar diya.

---

# 5. List mein Item Add Karna

## `append()`

List ke end mein item add karne ke liye `append()` use karte hain.

```python
fruits = ["Apple", "Banana"]

fruits.append("Orange")

print(fruits)
```

Output:

```text
['Apple', 'Banana', 'Orange']
```

---

## `insert()`

Specific position par item add karna ho to `insert()` use karte hain.

```python
fruits = ["Apple", "Orange"]

fruits.insert(1, "Banana")

print(fruits)
```

Output:

```text
['Apple', 'Banana', 'Orange']
```

Yahan:

```python
insert(1, "Banana")
```

ka matlab:

> Index `1` par `"Banana"` insert karo.

---

# 6. List se Item Remove Karna

## `remove()`

Value ke naam se item remove karna:

```python
fruits = ["Apple", "Banana", "Orange"]

fruits.remove("Banana")

print(fruits)
```

Output:

```text
['Apple', 'Orange']
```

---

## `pop()`

`pop()` index ke basis par item remove kar sakta hai.

```python
fruits = ["Apple", "Banana", "Orange"]

fruits.pop(1)

print(fruits)
```

Output:

```text
['Apple', 'Orange']
```

Agar index na dein:

```python
fruits.pop()
```

to last item remove hota hai.

---

# 7. List ki Length

List mein kitne items hain, ye check karne ke liye:

```python
len()
```

use karte hain.

```python
fruits = ["Apple", "Banana", "Orange"]

print(len(fruits))
```

Output:

```text
3
```

---

# 8. Practical List Example

Suppose aapke paas equipment list hai:

```python
equipment = [
    "AHU-01",
    "AHU-02",
    "FCU-01",
    "VAV-01"
]
```

Kisi specific equipment ko access karna:

```python
print(equipment[0])
```

Output:

```text
AHU-01
```

Naya equipment add:

```python
equipment.append("AHU-03")
```

Equipment remove:

```python
equipment.remove("FCU-01")
```

Ye real-world automation mein bohat useful hai.

---

# 9. Tuple

Ab second collection type:

## Tuple kya hai?

Tuple bhi multiple values store karta hai.

Tuple parentheses `()` mein banayi jati hai.

```python
fruits = ("Apple", "Banana", "Orange")
```

---

# 10. Tuple Indexing

Tuple mein bhi indexing **0 se start** hoti hai.

```python
fruits = ("Apple", "Banana", "Orange")

print(fruits[0])
```

Output:

```text
Apple
```

Aur:

```python
print(fruits[-1])
```

Output:

```text
Orange
```

Yani indexing ka concept list aur tuple dono mein similar hai.

---

# 11. Tuple Immutable Hai

Ye bohat important difference hai.

**Tuple immutable hoti hai.**

Immutable ka matlab:

> Tuple create hone ke baad uske existing items ko directly change nahi kar sakte.

Example:

```python
fruits = ("Apple", "Banana", "Orange")

fruits[1] = "Mango"
```

Ye error dega.

Kyun?

Kyun ke tuple immutable hai.

---

# 12. List vs Tuple

| Feature     | List | Tuple |
| ----------- | ---- | ----- |
| Brackets    | `[]` | `()`  |
| Ordered     | Yes  | Yes   |
| Indexing    | Yes  | Yes   |
| Mutable     | Yes  | No    |
| Item change | Yes  | No    |
| `append()`  | Yes  | No    |
| `remove()`  | Yes  | No    |

Simple rule:

```text
List  → change kar sakte ho
Tuple → change nahi kar sakte
```

---

# 13. Tuple Practical Example

Suppose kisi location ke fixed coordinates hain:

```python
location = (24.7136, 46.6753)
```

Aap coordinates access kar sakte hain:

```python
print(location[0])
print(location[1])
```

Lekin normally existing tuple items ko change nahi karte.

Tuple useful hai jab data ko **fixed/unchangeable collection** ki tarah represent karna ho.

---

# 14. Set

Ab third collection:

## Set kya hai?

Set multiple values store karta hai, lekin iska important feature hai:

> **Set duplicate values ko store nahi rakhta.**

Set curly braces `{}` se banaya ja sakta hai.

```python
numbers = {10, 20, 30}
```

---

# 15. Set Duplicate Values

Example:

```python
numbers = {10, 20, 20, 30, 30}
```

Set duplicates ko remove kar deta hai.

Result conceptually:

```text
{10, 20, 30}
```

Isliye set unique values ke liye useful hai.

---

# 16. Set mein Indexing Nahi Hoti

List:

```python
fruits = ["Apple", "Banana", "Orange"]

print(fruits[0])
```

possible hai.

Lekin set:

```python
fruits = {"Apple", "Banana", "Orange"}

print(fruits[0])
```

nahi kar sakte.

Kyun?

> Set ko index-based sequence ki tarah use nahi karte.

Isliye set ke items ko list ki tarah `set[0]` se access nahi karte.

---

# 17. Set mein Item Add Karna

Set mein item add karne ke liye:

```python
add()
```

use karte hain.

```python
numbers = {10, 20, 30}

numbers.add(40)

print(numbers)
```

Result:

```text
{10, 20, 30, 40}
```

---

# 18. Set se Item Remove Karna

`remove()`:

```python
numbers = {10, 20, 30}

numbers.remove(20)

print(numbers)
```

Result:

```text
{10, 30}
```

Set mein `discard()` bhi use hota hai:

```python
numbers.discard(100)
```

Agar `100` set mein na ho, `discard()` error nahi deta.

---

# 19. Dictionary

Ab fourth aur bohat important collection:

## Dictionary kya hai?

Dictionary data ko **key-value pairs** mein store karti hai.

Example:

```python
person = {
    "name": "Muhammad",
    "age": 25,
    "country": "Saudi Arabia"
}
```

Isko aise samjho:

```text
Key       Value

name      Muhammad
age       25
country   Saudi Arabia
```

---

# 20. Dictionary se Value Access Karna

Dictionary mein key use karke value access karte hain.

```python
person = {
    "name": "Muhammad",
    "age": 25
}

print(person["name"])
```

Output:

```text
Muhammad
```

Aur:

```python
print(person["age"])
```

Output:

```text
25
```

Yahan `name` aur `age` **keys** hain.

---

# 21. Dictionary mein New Item Add Karna

Example:

```python
person = {
    "name": "Muhammad",
    "age": 25
}

person["country"] = "Saudi Arabia"
```

Ab dictionary:

```text
name     → Muhammad
age      → 25
country  → Saudi Arabia
```

---

# 22. Dictionary mein Existing Value Change Karna

Dictionary mutable hoti hai.

```python
person = {
    "name": "Muhammad",
    "age": 25
}

person["age"] = 26

print(person)
```

Result:

```text
{'name': 'Muhammad', 'age': 26}
```

---

# 23. Dictionary se Item Remove Karna

`pop()`:

```python
person = {
    "name": "Muhammad",
    "age": 25,
    "country": "Saudi Arabia"
}

person.pop("age")

print(person)
```

Result:

```text
{'name': 'Muhammad', 'country': 'Saudi Arabia'}
```

`del` bhi use kar sakte hain:

```python
del person["country"]
```

---

# 24. Dictionary mein Key Check Karna

```python
person = {
    "name": "Muhammad",
    "age": 25
}

print("name" in person)
```

Output:

```text
True
```

Aur:

```python
print("salary" in person)
```

Output:

```text
False
```

---

# 25. Dictionary Practical Example

Equipment information store karte hain:

```python
equipment = {
    "id": "MEP-KHN-REF04",
    "type": "Refrigerator",
    "area": "Kitchen",
    "floor": "Thirty Four Floor"
}
```

Ab:

```python
print(equipment["id"])
```

Output:

```text
MEP-KHN-REF04
```

Type:

```python
print(equipment["type"])
```

Output:

```text
Refrigerator
```

Area:

```python
print(equipment["area"])
```

Output:

```text
Kitchen
```

Ye real-world Python data processing mein bohat common structure hai.

---

# 26. Mutable vs Immutable

Ab is concept ko properly samjho.

### Mutable

Mutable ka matlab:

> Object create hone ke baad uske contents ko modify kar sakte hain.

Common examples:

```text
list
dict
set
```

Example:

```python
fruits = ["Apple", "Banana"]

fruits[0] = "Mango"

print(fruits)
```

List change ho gayi.

---

### Immutable

Immutable ka matlab:

> Object create hone ke baad uske existing contents ko directly modify nahi kar sakte.

Example:

```python
fruits = ("Apple", "Banana")
```

Ye tuple hai.

```python
fruits[0] = "Mango"
```

allowed nahi hai.

Common immutable examples:

```text
tuple
str
int
float
bool
```

---

# 27. Collection Types — Quick Comparison

| Type       | Syntax         |               Ordered | Mutable |  Duplicates |  Indexing |
| ---------- | -------------- | --------------------: | ------: | ----------: | --------: |
| List       | `[]`           |                   Yes |     Yes |         Yes |       Yes |
| Tuple      | `()`           |                   Yes |      No |         Yes |       Yes |
| Set        | `{}`           | No index-based access |     Yes |          No |        No |
| Dictionary | `{key: value}` |                  Yes* |     Yes | Keys unique | Key-based |

`*` Modern Python dictionaries preserve insertion order, lekin dictionary ko primarily **key-value mapping** samajhna chahiye, index-based collection nahi.

---

# 28. Ek Simple Real-World Example

Suppose aap ek employee ka data manage kar rahe hain:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "skills": ["Python", "Power BI", "HVAC"],
    "location": ("Riyadh", "Saudi Arabia"),
    "active": True
}
```

Notice karo yahan **different collection types ek doosre ke andar** bhi use ho rahe hain.

```text
employee → dictionary
             │
             ├── name → string
             ├── age → integer
             ├── skills → list
             ├── location → tuple
             └── active → boolean
```

Skills access:

```python
print(employee["skills"])
```

Output:

```text
['Python', 'Power BI', 'HVAC']
```

Specific skill:

```python
print(employee["skills"][0])
```

Output:

```text
Python
```

Yahan do concepts combine hue:

```text
employee["skills"]
        ↓
      list
        ↓
     [0]
        ↓
    Python
```

Ye nested data structures Python mein bohat important hain.

---

# 29. Practice Exercises

### Exercise 1 — List

```python
fruits = ["Apple", "Banana", "Orange"]
```

`Banana` ko `Mango` se replace karo.

---

### Exercise 2 — List

List mein `"Grapes"` add karo.

```python
fruits = ["Apple", "Banana"]
```

---

### Exercise 3 — List

Last item remove karo:

```python
numbers = [10, 20, 30, 40]
```

---

### Exercise 4 — Tuple

Predict karo:

```python
data = ("A", "B", "C")

print(data[1])
```

Output kya hoga?

---

### Exercise 5 — Set

Duplicate values ka result batao:

```python
numbers = {1, 2, 2, 3, 3, 3}
```

---

### Exercise 6 — Dictionary

Is dictionary mein `country` add karo:

```python
person = {
    "name": "Muhammad",
    "age": 25
}
```

---

### Exercise 7 — Dictionary

`age` ko `26` mein change karo.

---

### Exercise 8 — Mutable vs Immutable

Batayo kaun mutable hai aur kaun immutable:

```text
List
Tuple
Set
Dictionary
```

---

# Section 1.5 — Final Summary

Collection types ko simple tareeqe se yaad rakho:

```text
LIST
↓
Multiple values
Change kar sakte hain
Index hoti hai

TUPLE
↓
Multiple values
Change nahi kar sakte
Index hoti hai

SET
↓
Unique values
Duplicates nahi
Indexing nahi

DICTIONARY
↓
Key → Value
Data ko naam ke through access karte hain
Change kar sakte hain
```

### Sabse important distinction

```text
List       → [ ]
Tuple      → ( )
Set        → { }
Dictionary → {key: value}
```

Aur:

```text
Mutable:
List, Set, Dictionary

Immutable:
Tuple
```

**Next Section 1.6 — IDLE (Python GUI):** ismein hum Python **Shell vs Editor**, new file banana, code likhna, save karna, run karna, errors dekhna, aur IDLE mein basic debugging ko step-by-step samjhenge.
# Section 1.6 — IDLE — Python GUI

Ab Chapter 1 ka last section hai: **IDLE**.

Agar aap Python beginner ho, to IDLE ko samajhna useful hai kyun ke ismein aap Python code **likh, run aur test** kar sakte ho.

---

## 1. IDLE kya hai?

**IDLE** ka full form hai:

> **Integrated Development and Learning Environment**

Simple Roman Urdu mein:

> IDLE Python ke saath milne wala ek basic programming environment hai jahan hum Python code likh aur execute kar sakte hain.

IDLE ke andar mainly do important cheezein hoti hain:

```text
Python Shell
     +
Code Editor
```

---

# 2. Python Shell kya hai?

Python Shell mein hum Python commands ko **directly execute** kar sakte hain.

Example:

```python
>>> 10 + 20
30
```

Yahan:

```text
>>> 
```

Python ka prompt hai.

Aap directly likh sakte ho:

```python
>>> print("Hello")
Hello
```

Phir:

```python
>>> 5 * 10
50
```

Python immediately result show kar deta hai.

---

# 3. Shell ka use kab karte hain?

Shell useful hai jab aap kisi choti cheez ko quickly test karna chahte ho.

Example:

```python
>>> 100 / 4
25.0
```

Ya:

```python
>>> type(100)
<class 'int'>
```

Ya:

```python
>>> "Python".upper()
'PYTHON'
```

Aapko har baar complete program banane ki zaroorat nahi hoti.

---

# 4. IDLE Editor

Agar aap proper Python program likhna chahte ho, to **Editor** use karte ho.

IDLE mein:

**File → New File**

select karne se ek new editor window open hoti hai.

Example:

```python
name = "Muhammad"
age = 25

print(name)
print(age)
```

Is file ko save karke run kiya ja sakta hai.

---

# 5. Python File ka Extension

Python files ka extension:

```text
.py
```

hota hai.

Example:

```text
hello.py
```

Ya:

```text
calculator.py
```

Ya:

```text
my_program.py
```

`.py` Python file ko identify karta hai.

---

# 6. Program Save Karna

Editor mein code likhne ke baad:

**File → Save**

ya keyboard shortcut:

```text
Ctrl + S
```

use kar sakte ho.

Example filename:

```text
first_program.py
```

---

# 7. Program Run Karna

IDLE Editor mein Python program run karne ke liye:

**Run → Run Module**

ya commonly:

```text
F5
```

press kar sakte ho.

Example code:

```python
print("Hello Python")
```

F5 press karne ke baad Shell mein:

```text
Hello Python
```

show hoga.

---

# 8. Shell vs Editor

Ye difference bohat important hai.

| Python Shell              | Editor                   |
| ------------------------- | ------------------------ |
| Quick testing             | Complete programs        |
| Immediate result          | Code save kar sakte hain |
| Small commands            | Multiple lines           |
| Temporary experimentation | `.py` file               |
| Interactive               | Program development      |

Simple example:

### Shell

```python
>>> 10 + 20
30
```

### Editor

```python
x = 10
y = 20

result = x + y

print(result)
```

Editor wala code save karke dobara run kiya ja sakta hai.

---

# 9. IDLE mein `print()` Test Karna

Shell open karo aur:

```python
>>> print("Hello World")
```

Output:

```text
Hello World
```

Ab:

```python
>>> print(10 + 20)
```

Output:

```text
30
```

Ab variable:

```python
>>> name = "Muhammad"
>>> print(name)
```

Output:

```text
Muhammad
```

---

# 10. IDLE mein Datatype Check Karna

Shell:

```python
>>> age = 25
>>> type(age)
<class 'int'>
```

String:

```python
>>> name = "Muhammad"
>>> type(name)
<class 'str'>
```

List:

```python
>>> fruits = ["Apple", "Banana"]
>>> type(fruits)
<class 'list'>
```

Is tarah IDLE ko learning ke liye interactive testing environment ki tarah use kar sakte ho.

---

# 11. IDLE mein Error

Programming mein errors normal hain.

Example:

```python
print(name)
```

Agar `name` variable pehle define nahi kiya, to Python error dega:

```text
NameError
```

Example:

```python
>>> print(name)

Traceback ...
NameError: name 'name' is not defined
```

Iska simple matlab:

> Python ko `name` naam ka variable nahi mila.

---

# 12. Syntax Error

Agar Python ka syntax galat ho:

```python
if age >= 18
    print("Adult")
```

Yahan `if` condition ke baad `:` missing hai.

Python syntax error report karega.

Correct:

```python
if age >= 18:
    print("Adult")
```

---

# 13. Indentation Error

Agar indentation galat ho:

```python
if age >= 18:
print("Adult")
```

Python ko pata nahi chalega ke `print()` `if` block ka part kaise hai.

Correct:

```python
if age >= 18:
    print("Adult")
```

Isliye jo humne **Section 1.3 mein Indentation** seekhi thi, wo IDLE mein bhi bohat important hai.

---

# 14. IDLE mein Error ko Kaise Read Karein?

Error dekh kar panic nahi karna.

Error message ko **neeche se upar** read karna useful hota hai.

Example:

```text
Traceback ...
File "test.py", line 3
    print(name)

NameError: name 'name' is not defined
```

Sabse important part usually last line hoti hai:

```text
NameError: name 'name' is not defined
```

Yani:

> `name` variable define nahi hua.

---

# 15. IDLE ka Interactive Learning Example

Chalo ek complete mini exercise karte hain.

Shell mein:

```python
>>> name = "Muhammad"
>>> age = 25
>>> age + 5
30
>>> print(name)
Muhammad
>>> type(age)
<class 'int'>
```

Yahan humne ek hi Shell session mein:

1. Variable create kiya
2. Value assign ki
3. Calculation ki
4. `print()` use kiya
5. Datatype check kiya

---

# 16. Editor mein Complete Program

Ab same concepts ko ek proper program mein likhte hain:

```python
name = "Muhammad"
age = 25

print("Name:", name)
print("Age:", age)
```

Output:

```text
Name: Muhammad
Age: 25
```

Yahan:

```text
name → string
age  → integer
```

---

# 17. IDLE aur Python Learning

Beginner ke liye ek simple workflow ye ho sakta hai:

```text
Concept seekho
     ↓
IDLE Shell mein test karo
     ↓
Code Editor mein program likho
     ↓
.py file save karo
     ↓
F5 se run karo
     ↓
Output check karo
     ↓
Error aaye to error read karo
```

Ye approach Python seekhne mein kaafi useful hai.

---

# Chapter 1 — Complete Revision

Ab humne poora Chapter 1 cover kar liya:

### 1.1 Getting Started

Python kya hai, `print()`, comments aur basic execution.

### 1.2 Variables

```python
name = "Muhammad"
age = 25
```

Variable mein values store karna.

### 1.3 Block Indentation

```python
if age >= 18:
    print("Adult")
```

Indentation se code blocks define karna.

### 1.4 Datatypes

```text
int
float
str
bool
None
```

Aur:

```python
type()
int()
float()
str()
bool()
```

### 1.5 Collection Types

```text
List
Tuple
Set
Dictionary
```

### 1.6 IDLE

```text
Shell → Quick testing
Editor → Complete programs
.py → Python source file
F5 → Run program
```

---
# Section 1.7 — User Input

Ab tak hum program ke andar values khud define kar rahe thay:

```python
name = "Muhammad"
age = 25
```

Lekin real programs mein aksar humein **user se information leni hoti hai**.

Example:

```text
Enter your name:
Enter your age:
Enter your city:
```

Python mein user se input lene ke liye hum **`input()` function** use karte hain.

---

## 1. `input()` kya hai?

`input()` user se keyboard ke through information leta hai.

Basic syntax:

```python
input()
```

Example:

```python
name = input()
print(name)
```

Program run karne par:

```text
Muhammad
Muhammad
```

Yahan user ne `Muhammad` enter kiya.

---

# 2. `input()` ke andar Message dena

Hum user ko bata sakte hain ke usse kya enter karna hai.

```python
name = input("Enter your name: ")

print(name)
```

Output:

```text
Enter your name: Muhammad
Muhammad
```

Yahan:

```python
"Enter your name: "
```

prompt/message hai.

---

# 3. User Input ko Variable mein Store Karna

Sabse common pattern:

```python
variable = input("Message: ")
```

Example:

```python
name = input("Enter your name: ")
```

Ab user jo value enter karega wo `name` variable mein store ho jayegi.

Example:

```text
Enter your name: Muhammad
```

Ab:

```python
print(name)
```

Output:

```text
Muhammad
```

---

# 4. Ek se Zyada Inputs

Hum multiple inputs bhi le sakte hain.

```python
name = input("Enter your name: ")
city = input("Enter your city: ")

print(name)
print(city)
```

Example:

```text
Enter your name: Muhammad
Enter your city: Riyadh
Muhammad
Riyadh
```

---

# 5. Important: `input()` Normally String Return Karta Hai

Ye beginner ke liye **bohat important point** hai.

Agar user enter kare:

```text
25
```

to Python normally usko:

```python
str
```

samajhta hai, `int` nahi.

Example:

```python
age = input("Enter your age: ")

print(type(age))
```

User:

```text
25
```

Output:

```text
<class 'str'>
```

Yani:

```python
age
```

mein number jaisa dikhne wala data hai, lekin datatype **string** hai.

---

# 6. `input()` aur Calculation

Agar hum directly ye karein:

```python
age = input("Enter your age: ")

print(age + 5)
```

aur user:

```text
25
```

enter kare, to error aayega.

Kyun?

Kyun ke:

```text
age = "25"
```

hai.

Python string aur integer ko directly `+` nahi kar sakta.

---

# 7. `int()` ke Saath Input

Agar user se integer lena ho to:

```python
age = int(input("Enter your age: "))
```

Yahan process:

```text
input()
   ↓
String
   ↓
int()
   ↓
Integer
```

Example:

```python
age = int(input("Enter your age: "))

print(age + 5)
```

User:

```text
Enter your age: 25
```

Output:

```text
30
```

---

# 8. `float()` ke Saath Input

Decimal number ke liye `float()` use kar sakte hain.

```python
price = float(input("Enter price: "))

print(price)
```

User:

```text
Enter price: 125.50
```

Output:

```text
125.5
```

Datatype:

```python
print(type(price))
```

Output:

```text
<class 'float'>
```

---

# 9. Different Types ka Input

### String

```python
name = input("Name: ")
```

### Integer

```python
age = int(input("Age: "))
```

### Float

```python
price = float(input("Price: "))
```

Ye pattern yaad rakhna useful hai:

```python
str_value = input("Enter text: ")

int_value = int(input("Enter integer: "))

float_value = float(input("Enter decimal: "))
```

---

# 10. Practical Example — Simple Calculator

User se do numbers lete hain:

```python
num1 = int(input("Enter first number: "))
num2 = int(input("Enter second number: "))

result = num1 + num2

print("Result:", result)
```

Example:

```text
Enter first number: 20
Enter second number: 30
Result: 50
```

---

# 11. Multiplication Example

```python
price = float(input("Enter price: "))
quantity = int(input("Enter quantity: "))

total = price * quantity

print("Total:", total)
```

Example:

```text
Enter price: 25.50
Enter quantity: 4
Total: 102.0
```

Ye real-world programs mein bohat common pattern hai:

```text
User Input
    ↓
Convert datatype
    ↓
Calculation
    ↓
Output
```

---

# 12. User ka Naam aur Age

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))

print("Name:", name)
print("Age:", age)
```

Example:

```text
Enter your name: Muhammad
Enter your age: 25

Name: Muhammad
Age: 25
```

---

# 13. Input ke Saath `type()`

Input ka datatype check karna ho:

```python
name = input("Enter name: ")
age = int(input("Enter age: "))

print(type(name))
print(type(age))
```

Output:

```text
<class 'str'>
<class 'int'>
```

---

# 14. User Input ko Calculation mein Use Karna

Example salary calculation:

```python
salary = float(input("Enter monthly salary: "))
months = int(input("Enter number of months: "))

total = salary * months

print("Total:", total)
```

Agar:

```text
salary = 5000
months = 12
```

to:

```text
Total: 60000.0
```

---

# 15. Input mein Invalid Data

Ye bhi samajhna important hai.

Agar code hai:

```python
age = int(input("Enter age: "))
```

aur user enter kare:

```text
abc
```

to Python `abc` ko integer mein convert nahi kar sakta.

Isliye error aayega:

```text
ValueError
```

Abhi hum error handling detail mein nahi ja rahe. Baad mein `try` / `except` ke through is situation ko properly handle karenge.

---

# 16. `input()` ka Basic Formula

Is formula ko yaad rakho:

```python
variable = input("Question: ")
```

Agar integer chahiye:

```python
variable = int(input("Question: "))
```

Agar decimal chahiye:

```python
variable = float(input("Question: "))
```

---

# 17. Mini Exercise

Ye program khud likho:

```text
Enter your name:
Enter your age:
Enter your city:

Name: ...
Age: ...
City: ...
```

Expected structure:

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))
city = input("Enter your city: ")

print("Name:", name)
print("Age:", age)
print("City:", city)
```

---

# 18. Important Points

### Point 1

`input()` user se data leta hai.

### Point 2

`input()` normally **string** return karta hai.

### Point 3

Integer ke liye:

```python
int(input(...))
```

### Point 4

Decimal ke liye:

```python
float(input(...))
```

### Point 5

User input ko variable mein store kar sakte hain:

```python
name = input("Name: ")
```

### Point 6

Input ko calculation mein use karne se pehle datatype ka khayal rakho.

---

## Section 1.7 ka Short Summary

```text
input()
   ↓
User se value
   ↓
Normally String
   ↓
int() / float() agar conversion required ho
   ↓
Calculation / Processing
   ↓
print() se result
```

Example:

```python
price = float(input("Enter price: "))
quantity = int(input("Enter quantity: "))

total = price * quantity

print("Total:", total)
```

Ye **User Input ka fundamental pattern** hai aur aage ke Python programs mein baar-baar use hoga.
# Section 1.8 — Built-in Modules and Functions

Python mein bohat saara useful functionality pehle se available hota hai. Humein har cheez khud se create nahi karni padti.

Python mein do important concepts hain:

1. **Built-in Functions**
2. **Modules**

---

# 1. Built-in Function kya hota hai?

**Function** code ka ek reusable block hota hai jo koi specific kaam karta hai.

Python mein kuch functions pehle se available hote hain. Inko **Built-in Functions** kehte hain.

Example:

```python
print("Hello")
```

Yahan:

```python
print()
```

ek built-in function hai.

Isi tarah:

```python
len()
type()
input()
int()
float()
str()
```

bhi commonly used built-in functions hain.

---

# 2. `print()` Function

`print()` ka kaam output screen par display karna hai.

```python
print("Hello Python")
```

Output:

```text
Hello Python
```

Multiple values:

```python
name = "Muhammad"
age = 25

print(name, age)
```

Output:

```text
Muhammad 25
```

---

# 3. `input()` Function

`input()` user se information leta hai.

```python
name = input("Enter your name: ")
```

Example:

```text
Enter your name: Muhammad
```

Ab value `name` mein store ho gayi.

---

# 4. `len()` Function

`len()` kisi object ki length/count return karta hai.

String:

```python
name = "Muhammad"

print(len(name))
```

Output:

```text
8
```

List:

```python
fruits = ["Apple", "Banana", "Orange"]

print(len(fruits))
```

Output:

```text
3
```

Yani `len()` context ke according length ya number of items batata hai.

---

# 5. `type()` Function

`type()` kisi value ka datatype batata hai.

```python
age = 25
print(type(age))
```

Output:

```text
<class 'int'>
```

Example:

```python
name = "Muhammad"
price = 25.50
active = True

print(type(name))
print(type(price))
print(type(active))
```

Output:

```text
<class 'str'>
<class 'float'>
<class 'bool'>
```

---

# 6. `int()`, `float()` aur `str()`

Ye functions conversion ke liye use hote hain.

### String → Integer

```python
age = int("25")

print(age)
print(type(age))
```

Output:

```text
25
<class 'int'>
```

### String → Float

```python
price = float("25.50")

print(price)
```

### Number → String

```python
age = 25

text = str(age)

print(type(text))
```

Output:

```text
<class 'str'>
```

---

# 7. `max()` aur `min()`

`max()` largest value return karta hai.

```python
numbers = [10, 25, 5, 40, 15]

print(max(numbers))
```

Output:

```text
40
```

`min()` smallest value return karta hai.

```python
print(min(numbers))
```

Output:

```text
5
```

---

# 8. `sum()`

`sum()` numbers ka total calculate karta hai.

```python
numbers = [10, 20, 30, 40]

print(sum(numbers))
```

Output:

```text
100
```

Ye data processing mein bohat useful hai.

---

# 9. `abs()`

`abs()` absolute value return karta hai.

```python
print(abs(-25))
```

Output:

```text
25
```

Example:

```python
temperature_difference = -10

print(abs(temperature_difference))
```

Output:

```text
10
```

---

# 10. `round()`

`round()` number ko round karta hai.

```python
price = 25.6789

print(round(price))
```

Output:

```text
26
```

Decimal places specify bhi kar sakte hain:

```python
print(round(price, 2))
```

Output:

```text
25.68
```

---

# 11. Function ka General Structure

Built-in function ko generally is tarah call karte hain:

```python
function_name(arguments)
```

Example:

```python
len("Python")
```

Yahan:

```text
len      → function
"Python" → argument
```

Aur:

```python
max(10, 20, 30)
```

mein numbers arguments hain.

---

# 12. Built-in Function aur Module mein Difference

Ab important part:

### Function

Ek specific kaam karta hai.

Example:

```python
len()
```

### Module

Related functions, classes aur other Python code ka collection hota hai.

Simple example:

```text
Module
 ├── Function
 ├── Function
 ├── Function
 └── Other code
```

Isko aap ek **toolbox** ki tarah samajh sakte ho.

---

# 13. Module kya hai?

Python module generally ek `.py` file hoti hai jisme reusable Python code hota hai.

Example:

```text
math
random
datetime
os
```

Python ke saath bohat se modules available hote hain.

Inko generally **Python Standard Library** ka part kaha jata hai.

---

# 14. `math` Module

Mathematical operations ke liye `math` module useful hai.

Pehle module import karte hain:

```python
import math
```

Ab `math` ke functions use kar sakte hain.

Example:

```python
import math

print(math.sqrt(25))
```

Output:

```text
5.0
```

Yahan:

```text
math
```

module hai.

Aur:

```text
sqrt()
```

module ke andar function hai.

---

# 15. `math.pi`

`math` module mein useful constants bhi hain.

```python
import math

print(math.pi)
```

Output approximately:

```text
3.141592653589793
```

Circle calculation:

```python
import math

radius = 5

area = math.pi * radius ** 2

print(area)
```

---

# 16. `random` Module

Random values generate karne ke liye `random` module use hota hai.

```python
import random
```

Example:

```python
number = random.randint(1, 10)

print(number)
```

Program `1` se `10` ke beech ek random integer dega.

Example output:

```text
7
```

Agli baar:

```text
3
```

aa sakta hai.

---

# 17. `datetime` Module

Date aur time ke saath kaam karne ke liye `datetime` module useful hai.

```python
import datetime

today = datetime.date.today()

print(today)
```

Output current date ke according hoga, example:

```text
2026-10-02
```

Yahan:

```text
datetime
```

module hai.

Aur:

```text
date.today()
```

date related functionality use kar raha hai.

---

# 18. `os` Module

`os` module operating system ke saath interact karne ke liye useful hai.

Example:

```python
import os

print(os.getcwd())
```

`getcwd()` ka matlab hai:

> Get Current Working Directory

Ye batata hai ke Python ka current working folder kya hai.

Example output:

```text
C:\Users\Muhammad\Python
```

Actual path aapke computer par different hoga.

---

# 19. Module Import Karne ka Basic Syntax

Basic syntax:

```python
import module_name
```

Example:

```python
import math
```

Phir:

```python
math.sqrt(25)
```

Isi tarah:

```python
import random

random.randint(1, 100)
```

---

# 20. `from ... import ...`

Aap module ke andar se specific function bhi import kar sakte ho.

Example:

```python
from math import sqrt
```

Ab directly:

```python
print(sqrt(25))
```

likh sakte ho.

Pehle wale method mein:

```python
import math

print(math.sqrt(25))
```

Dono valid hain.

---

# 21. `import` vs `from ... import`

### Method 1

```python
import math

print(math.sqrt(25))
```

Yahan clearly pata chal raha hai ke `sqrt()` `math` module se aaya hai.

### Method 2

```python
from math import sqrt

print(sqrt(25))
```

Yahan sirf `sqrt` import kiya gaya.

Beginner ke liye pehle:

```python
import math
```

wala approach samajhna easier hota hai.

---

# 22. Module ko Alias Dena

Module ka short naam bhi bana sakte hain.

Example:

```python
import math as m

print(m.sqrt(25))
```

Yahan:

```text
math → m
```

alias ban gaya.

Ab:

```python
m.sqrt(25)
```

use kar sakte hain.

---

# 23. Built-in Function vs Module Example

Ye difference yaad rakho:

```python
print(len("Python"))
```

Yahan:

```text
len()
```

built-in function hai.

Lekin:

```python
import math

print(math.sqrt(25))
```

Yahan:

```text
math
```

module hai.

Aur:

```text
sqrt()
```

math module ki functionality hai.

---

# 24. Practical Example — Employee Data

Ab ek practical example:

```python
name = "Muhammad"
skills = ["Python", "Power BI", "HVAC"]

print("Name:", name)
print("Number of skills:", len(skills))
print("Datatype:", type(skills))
```

Output:

```text
Name: Muhammad
Number of skills: 3
Datatype: <class 'list'>
```

Yahan humne built-in functions use kiye:

```text
print()
len()
type()
```

---

# 25. Practical Example — Equipment Data

Suppose:

```python
temperatures = [22.5, 23.1, 21.8, 24.2, 22.9]
```

Hum built-in functions se analysis kar sakte hain:

```python
print("Minimum:", min(temperatures))
print("Maximum:", max(temperatures))
print("Total:", sum(temperatures))
print("Number of readings:", len(temperatures))
```

Output approximately:

```text
Minimum: 21.8
Maximum: 24.2
Total: 114.5
Number of readings: 5
```

Ye simple example batata hai ke built-in functions data processing mein kitne useful hain.

---

# 26. Important Built-in Functions

Beginner ke liye in functions ko achhi tarah samajhna useful hai:

| Function  | Kaam                     |
| --------- | ------------------------ |
| `print()` | Output display           |
| `input()` | User input               |
| `len()`   | Length / number of items |
| `type()`  | Datatype                 |
| `int()`   | Integer conversion       |
| `float()` | Float conversion         |
| `str()`   | String conversion        |
| `bool()`  | Boolean conversion       |
| `max()`   | Maximum value            |
| `min()`   | Minimum value            |
| `sum()`   | Total                    |
| `abs()`   | Absolute value           |
| `round()` | Rounding                 |

---

# 27. Important Standard Library Modules

Python ke standard library mein bohat se modules hain.

Kuch common examples:

```text
math
random
datetime
os
sys
json
csv
pathlib
```

Har module ka apna purpose hota hai.

For example:

```text
math      → Mathematics
random    → Random values
datetime  → Date and time
os        → Operating system interaction
json      → JSON data
csv       → CSV files
pathlib   → File/folder paths
```

Aage Python seekhte waqt hum in modules ko individually detail mein use karenge.

---

# 28. Function aur Module ko Ek Simple Example se Samjho

Imagine karo ek toolbox hai:

```text
Toolbox = Module
```

Toolbox ke andar different tools hain:

```text
Toolbox
 ├── Tool A
 ├── Tool B
 ├── Tool C
 └── Tool D
```

Python mein:

```text
Module
 ├── Function
 ├── Function
 ├── Function
 └── Classes / Constants / Other code
```

Example:

```python
import math
```

Ab `math` toolbox jaisa hai.

```python
math.sqrt(25)
```

mein hum `sqrt()` functionality use kar rahe hain.

---

# 29. Practice Exercise

### Exercise 1

Ek list banao:

```python
numbers = [10, 20, 5, 40, 15]
```

Phir find karo:

* Maximum
* Minimum
* Total
* Number of items

Functions:

```python
max()
min()
sum()
len()
```

---

### Exercise 2

`math` module use karke:

```python
25
```

ka square root find karo.

Expected:

```python
import math

print(math.sqrt(25))
```

---

### Exercise 3

`random` module use karke `1` se `100` ke beech random number generate karo.

Hint:

```python
import random

number = random.randint(1, 100)

print(number)
```

---

### Exercise 4

Current date display karo:

```python
import datetime

print(datetime.date.today())
```

---

# Section 1.8 — Summary

Sabse important concepts:

### Built-in Function

Python mein already available function:

```python
print()
len()
type()
input()
max()
min()
sum()
```

### Module

Reusable Python code ka collection:

```python
math
random
datetime
os
```

### Module Import

```python
import math
```

### Module ki functionality use karna

```python
math.sqrt(25)
```

### Specific functionality import karna

```python
from math import sqrt
```

Phir:

```python
sqrt(25)
```

---

## Sabse important difference

```text
Function
   ↓
Specific kaam

Module
   ↓
Related functionality ka collection
```

Example:

```python
import math

result = math.sqrt(25)
```

Yahan:

```text
math  → Module
sqrt  → Function
25    → Argument
```

Ye distinction clear hona bohat important hai, kyun ke next sections mein hum **apna khud ka module create** karenge.
# Section 1.9 — Creating a Module

Section 1.8 mein humne dekha tha ke Python mein built-in modules available hote hain, jaise:

```python
import math
```

Lekin Python mein hum **apna khud ka module bhi create** kar sakte hain.

Ye concept bohat important hai, especially jab program bada ho jaye.

---

# 1. Module kya hota hai?

Simple words mein:

> **Module ek Python file (`.py`) hoti hai jisme reusable code hota hai.**

Example:

```text
calculator.py
```

Agar is file mein functions hain:

```python
def add(a, b):
    return a + b
```

to doosri Python file mein hum is function ko import karke use kar sakte hain.

---

# 2. Module banane ka Basic Idea

Suppose humare paas do files hain:

```text
project/
│
├── calculator.py
└── main.py
```

Yahan:

```text
calculator.py → Module
main.py       → Main program
```

`calculator.py` mein reusable functions honge.

`main.py` un functions ko use karega.

---

# 3. Apna Pehla Module Create Karna

Sabse pehle ek file banao:

```text
calculator.py
```

Ismein likho:

```python
def add(a, b):
    return a + b
```

Ab `calculator.py` ek module ban gaya.

---

# 4. Module ko Import Karna

Ab same folder mein doosri file banao:

```text
main.py
```

Usmein:

```python
import calculator
```

Ab hum calculator module ke `add()` function ko use kar sakte hain:

```python
result = calculator.add(10, 20)

print(result)
```

Output:

```text
30
```

---

# 5. Ye Process Kaise Work Karta Hai?

Overall flow:

```text
calculator.py
     ↓
add() function
     ↓
main.py
     ↓
import calculator
     ↓
calculator.add()
     ↓
Result
```

Yani humne code ko ek file mein likha aur doosri file mein reuse kar liya.

---

# 6. Multiple Functions Wala Module

Module mein sirf ek function zaroori nahi.

`calculator.py`:

```python
def add(a, b):
    return a + b


def subtract(a, b):
    return a - b


def multiply(a, b):
    return a * b


def divide(a, b):
    return a / b
```

Ab `main.py`:

```python
import calculator

print(calculator.add(10, 5))
print(calculator.subtract(10, 5))
print(calculator.multiply(10, 5))
print(calculator.divide(10, 5))
```

Output:

```text
15
5
50
2.0
```

---

# 7. Module ka Fayda

Socho aapke paas 500 lines ka program hai.

Agar sab kuch ek hi file mein likhoge:

```text
main.py
```

to file difficult ho sakti hai.

Instead hum code ko logically divide kar sakte hain:

```text
main.py
calculator.py
file_utils.py
data_utils.py
```

Example:

```text
calculator.py
    → calculations

file_utils.py
    → files/folders

data_utils.py
    → data processing

main.py
    → main program
```

Isse code ko **organize aur reuse** karna easier hota hai.

---

# 8. `from module import function`

Pehle humne likha:

```python
import calculator

calculator.add(10, 20)
```

Lekin hum directly `add()` bhi import kar sakte hain:

```python
from calculator import add

result = add(10, 20)

print(result)
```

Output:

```text
30
```

Yahan:

```text
calculator → module
add        → function
```

---

# 9. Multiple Functions Import Karna

Agar humein `add` aur `multiply` dono chahiye:

```python
from calculator import add, multiply

print(add(10, 20))
print(multiply(10, 20))
```

Output:

```text
30
200
```

---

# 10. `import module` vs `from module import`

### Method 1

```python
import calculator

calculator.add(10, 20)
```

### Method 2

```python
from calculator import add

add(10, 20)
```

Dono valid hain.

Beginner ke liye pehle method ko samajhna useful hai:

```python
import calculator
```

Isse clearly pata rehta hai ke function kis module se aa raha hai.

---

# 11. Module mein Variables bhi Ho Sakte Hain

Module mein sirf functions nahi hote.

`company.py`:

```python
company_name = "ABC Company"
country = "Saudi Arabia"
```

Ab `main.py`:

```python
import company

print(company.company_name)
print(company.country)
```

Output:

```text
ABC Company
Saudi Arabia
```

Yani module mein:

* Variables
* Functions
* Classes
* Constants
* Other Python code

ho sakta hai.

---

# 12. Practical Example — Employee Module

Ek file banao:

```text
employee.py
```

Code:

```python
def calculate_salary(hours, rate):
    return hours * rate


def employee_info(name, department):
    print("Name:", name)
    print("Department:", department)
```

Ab `main.py`:

```python
import employee

salary = employee.calculate_salary(8, 50)

print("Salary:", salary)

employee.employee_info("Muhammad", "Maintenance")
```

Output:

```text
Salary: 400
Name: Muhammad
Department: Maintenance
```

---

# 13. Module ka Reuse

Suppose kal kisi aur program mein bhi salary calculate karni hai.

Humein function dobara likhne ki zaroorat nahi.

Bas:

```python
import employee
```

aur:

```python
employee.calculate_salary(10, 60)
```

use kar sakte hain.

Ye **code reuse** hai.

---

# 14. Module aur Built-in Module ka Difference

Built-in/standard module:

```python
import math
```

Ye Python ke standard library ka part hai.

Apna module:

```python
import calculator
```

Ye module humne khud create kiya.

Concept same hai:

```text
Module
   ↓
Reusable Python code
```

Difference sirf ye hai ke code kahan se aa raha hai.

---

# 15. Module ka File Location Important Hai

Beginner level par easiest setup:

```text
project/
│
├── main.py
└── calculator.py
```

Dono files **same folder** mein rakho.

Phir `main.py` mein:

```python
import calculator
```

normally kaam karega.

Example:

```text
PythonProject/
│
├── main.py
└── calculator.py
```

---

# 16. Agar Module Same Folder Mein Na Ho?

Agar:

```text
PythonProject/
│
├── main.py
│
└── modules/
    └── calculator.py
```

to simple:

```python
import calculator
```

har situation mein directly work nahi karega.

Is tarah ke cases mein Python ke **packages, imports aur module search path** samajhna padta hai.

Abhi beginner level par hum same-folder structure use karenge.

---

# 17. Module Name ka Dhyan Rakho

Module ka naam simple aur meaningful rakho.

Good examples:

```text
calculator.py
employee.py
file_utils.py
data_utils.py
temperature.py
```

Avoid confusing names.

Aur module ka naam generally Python ke built-in module ke naam ke saath conflict nahi karna chahiye.

Example ke taur par apni file ka naam:

```text
math.py
```

rakhna avoid karo agar aap standard `math` module use karna chahte ho.

---

# 18. Module Import Hone Par Code Execute Ho Sakta Hai

Ye beginner ke liye important concept hai.

Agar `calculator.py` mein:

```python
print("Calculator module loaded")

def add(a, b):
    return a + b
```

aur `main.py` mein:

```python
import calculator
```

to import karte waqt:

```text
Calculator module loaded
```

print ho sakta hai.

Kyun?

Kyun ke module load karte waqt uska top-level code execute hota hai.

Isliye modules mein normally reusable definitions ko organize karna important hota hai.

---

# 19. `if __name__ == "__main__":`

Python mein ek important pattern hai:

```python
if __name__ == "__main__":
    print("This file is running directly")
```

Isko beginner level par simple way mein samjho:

> Ye check karta hai ke file directly run ho rahi hai ya kisi doosri file ne usko import kiya hai.

Example:

`calculator.py`:

```python
def add(a, b):
    return a + b


if __name__ == "__main__":
    print(add(10, 20))
```

Agar directly:

```text
calculator.py
```

run karo, to:

```text
30
```

aayega.

Lekin agar:

```python
import calculator
```

kisi doosri file mein karo, to `if __name__ == "__main__":` ke andar wala code normally execute nahi hoga.

Ye pattern future Python projects mein bohat important hoga.

---

# 20. Practical Project Structure

Aap future mein is tarah project organize kar sakte ho:

```text
my_project/
│
├── main.py
├── calculator.py
├── file_utils.py
└── data_utils.py
```

### `calculator.py`

```python
def add(a, b):
    return a + b
```

### `file_utils.py`

```python
def show_file_name(name):
    print("File:", name)
```

### `data_utils.py`

```python
def count_items(items):
    return len(items)
```

### `main.py`

```python
import calculator
import file_utils
import data_utils

print(calculator.add(10, 20))

file_utils.show_file_name("report.csv")

print(data_utils.count_items([10, 20, 30]))
```

Output:

```text
30
File: report.csv
3
```

Yahan har module ka apna responsibility hai.

---

# 21. Real-World Example

Agar aap koi work-order automation program bana rahe ho, to sab kuch `main.py` mein rakhne ke bajaye logically divide kiya ja sakta hai:

```text
work_order_project/
│
├── main.py
├── file_utils.py
├── work_order_utils.py
└── validation.py
```

Example:

```text
file_utils.py
    → folders/files handle kare

work_order_utils.py
    → work-order data process kare

validation.py
    → data validate kare

main.py
    → complete workflow run kare
```

Is approach se project maintain karna easier hota hai.

---

# 22. Important Terms

### Module

Python file containing reusable code.

```text
calculator.py
```

### Import

Module ko current program mein available karna.

```python
import calculator
```

### Function

Specific task perform karne wala reusable code.

```python
def add(a, b):
    return a + b
```

### Reuse

Same code ko multiple programs mein use karna.

---

# 23. Practice Exercise

### Exercise 1 — Calculator Module

Do files banao:

```text
calculator.py
main.py
```

`calculator.py`:

```python
def add(a, b):
    return a + b


def multiply(a, b):
    return a * b
```

`main.py`:

```python
import calculator

print(calculator.add(10, 5))
print(calculator.multiply(10, 5))
```

Expected:

```text
15
50
```

---

### Exercise 2 — Temperature Module

File:

```text
temperature.py
```

Function:

```python
def celsius_to_fahrenheit(celsius):
    return (celsius * 9 / 5) + 32
```

`main.py`:

```python
import temperature

result = temperature.celsius_to_fahrenheit(25)

print(result)
```

Expected:

```text
77.0
```

---

### Exercise 3 — Apna Module

Ek module banao:

```text
my_info.py
```

Usmein:

```python
name = "Muhammad"
profession = "Maintenance"
country = "Saudi Arabia"
```

Phir `main.py` mein:

```python
import my_info

print(my_info.name)
print(my_info.profession)
print(my_info.country)
```

---

# Section 1.9 — Quick Revision

Module ka basic concept:

```text
Python File
    ↓
.py
    ↓
Module
    ↓
Functions / Variables / Classes
    ↓
import
    ↓
Doosre program mein reuse
```

Example:

### `calculator.py`

```python
def add(a, b):
    return a + b
```

### `main.py`

```python
import calculator

result = calculator.add(10, 20)

print(result)
```

Output:

```text
30
```

### Sabse important baat

**Module ka matlab hai reusable Python code ko ek separate `.py` file mein organize karna.**

Jab projects bade hote hain, modules code ko **organized, reusable aur maintainable** banane mein help karte hain.
# Section 1.10 — Installation of Python 2.7.x and 3.x

Python code run karne ke liye computer mein **Python interpreter** installed hona zaroori hai.

Is section mein hum samjhenge:

* Python kya install karta hai
* Python version kaise check karte hain
* Python 2 aur Python 3 ka difference
* Python 3 install karne ka basic process
* Windows mein installation verify kaise karte hain

---

# 1. Python Interpreter kya hai?

Hum Python mein code likhte hain:

```python
print("Hello Python")
```

Computer directly Python code ko normally understand nahi karta.

**Python interpreter** Python code ko read karke execute karta hai.

Simple flow:

```text
Python Code
    ↓
Python Interpreter
    ↓
Computer Execution
    ↓
Output
```

---

# 2. Python 2 aur Python 3

Python ke historically do major versions thay:

```text
Python 2.x
Python 3.x
```

Example:

```text
Python 2.7
Python 3.8
Python 3.10
Python 3.11
Python 3.12
Python 3.13
```

Python 2 aur Python 3 mein kuch syntax aur behavior differences hain.

---

# 3. Python 2.7 kya hai?

Python 2.7 Python 2 series ka final major release tha.

Example Python 2 syntax:

```python
print "Hello"
```

Python 3 mein:

```python
print("Hello")
```

Yani Python 3 mein `print()` function syntax use hota hai.

---

# 4. Python 2.7 ka Status

Python 2.7 ka official support:

```text
1 January 2020
```

ko end ho gaya tha.

Iska matlab:

> Python 2.7 new projects ke liye recommended choice nahi hai.

Agar koi old application Python 2.7 par depend karti hai, to legacy compatibility ke liye Python 2.7 mil sakta hai, lekin new learning aur development ke liye **Python 3** use karna chahiye.

---

# 5. Python 3

Python 3 current Python development ka standard major version hai.

Python 3 mein:

```python
print("Hello")
```

likhte hain.

Variables:

```python
name = "Muhammad"
age = 25
```

Input:

```python
name = input("Enter your name: ")
```

Ye wahi syntax hai jo hum previous sections mein seekh rahe hain.

---

# 6. Python Install Karne Se Kya Milta Hai?

Windows par Python install karne ke baad normally aapko important tools milte hain:

```text
Python Interpreter
Python Launcher
pip
IDLE
Standard Library
```

Example:

```text
python.exe
pip
IDLE
```

Ye tools Python development mein different purposes ke liye use hote hain.

---

# 7. Python Installation Check Karna

Windows mein **Command Prompt** open karo.

Start menu mein search karo:

```text
Command Prompt
```

ya:

```text
cmd
```

Phir command:

```text
python --version
```

run karo.

Agar Python available hai to version show ho sakta hai:

```text
Python 3.x.x
```

Example:

```text
Python 3.13.7
```

Actual version aapke installed Python par depend karega.

---

# 8. `py --version`

Windows mein Python Launcher available ho to:

```text
py --version
```

bhi use kar sakte ho.

Example:

```text
Python 3.x.x
```

`py` Windows par multiple Python versions ke saath kaam karne mein useful ho sakta hai.

---

# 9. `python` Command

Command Prompt mein:

```text
python
```

likh kar Enter press karo.

Agar Python properly available hai, Python interactive shell open ho sakti hai:

```text
>>>
```

Ab test karo:

```python
print("Hello Python")
```

Output:

```text
Hello Python
```

Exit karne ke liye:

```python
exit()
```

likh sakte ho.

---

# 10. Python Install Karne ka Basic Process

Windows par Python install karne ka general process:

```text
Python installer download
        ↓
Installer run
        ↓
Python installation options
        ↓
Install
        ↓
Command Prompt open
        ↓
python --version
        ↓
Installation verify
```

---

# 11. PATH kya hai?

Installation ke waqt aapko **PATH** ka concept mil sakta hai.

PATH operating system ko batata hai ke executable programs ko kin folders mein search karna hai.

Agar Python properly PATH mein available ho, to Command Prompt se:

```text
python
```

ya:

```text
python --version
```

directly work kar sakta hai.

---

# 12. "Python was not found" Error

Agar aap command run karo:

```text
python --version
```

aur Windows Python ko find na kar sake, to issue ho sakta hai:

* Python installed nahi hai
* Python PATH mein available nahi hai
* Windows Python command ko kisi aur application ke through handle kar raha hai

Is situation mein Python installation aur PATH configuration check karni hoti hai.

---

# 13. IDLE ka Relation Python Installation se

Humne Section 1.6 mein IDLE padha tha.

Python installation ke saath IDLE commonly available hota hai.

Windows Start menu mein search karo:

```text
IDLE
```

Phir Python IDLE open karo.

Aapko Shell window mil sakti hai:

```text
>>>
```

Ab:

```python
print("Hello")
```

run karo.

Output:

```text
Hello
```

---

# 14. Python Version Check Karna — IDLE mein

IDLE Shell open karne par startup information mein Python version show ho sakta hai.

Aap Python ke andar bhi version information dekh sakte ho:

```python
import sys

print(sys.version)
```

Output example:

```text
3.x.x ...
```

Exact output installed Python version aur operating system par depend karega.

---

# 15. Python 2 vs Python 3 — Simple Difference

Basic example:

### Python 2

```python
print "Hello"
```

### Python 3

```python
print("Hello")
```

Python 3:

```python
name = input("Enter your name: ")
```

Python 2 mein input behavior different tha aur Python 2 code ko Python 3 mein blindly copy nahi karna chahiye.

---

# 16. Python 3 ko Prefer Kyun Karein?

New Python learning aur development ke liye Python 3 use karna practical hai kyun ke:

* Python 2.7 end-of-life hai
* Modern Python libraries Python 3 target karti hain
* New Python features Python 3 mein aati hain
* Modern development tools Python 3 ecosystem ke around hain
* Tutorials aur projects generally Python 3 use karte hain

---

# 17. Python Version Check Karne ke Important Commands

Windows Command Prompt:

```text
python --version
```

Alternative:

```text
py --version
```

Python ke andar:

```python
import sys

print(sys.version)
```

Ye teen methods aapko Python version identify karne mein help karte hain.

---

# 18. Multiple Python Versions

Ek computer par multiple Python versions possible hain.

Example:

```text
Python 3.11
Python 3.12
Python 3.13
```

Is situation mein Python Launcher useful ho sakta hai.

Example:

```text
py -3.12
```

specific Python 3.12 interpreter launch karne ke liye use kiya ja sakta hai, agar wo version installed ho.

Version-specific commands system configuration par depend kar sakti hain.

---

# 19. Python Installation Verify Karne ka Practical Test

Command Prompt mein:

```text
python --version
```

Phir:

```text
python
```

Python Shell mein:

```python
print("Python is working")
```

Agar output:

```text
Python is working
```

aata hai, to basic Python interpreter successfully run ho raha hai.

Exit:

```python
exit()
```

---

# 20. `pip` ka Basic Introduction

Python installation ke saath commonly **pip** bhi available hota hai.

`pip` Python packages install/manage karne ke liye use hota hai.

Example:

```text
python -m pip --version
```

Ye pip ka installed version show kar sakta hai.

Aage **Section 1.12** mein hum `pip` ko detail mein padhenge.

---

# 21. Installation ke Baad Recommended Check

Python install karne ke baad ye commands check karna useful hai:

```text
python --version
```

```text
py --version
```

```text
python -m pip --version
```

Aur Python run karke:

```python
print("Hello Python")
```

Agar ye successfully execute ho jayein, to basic installation ready hai.

---

# 22. Python Installation ka Complete Flow

```text
Install Python 3
       ↓
Python Interpreter
       ↓
PATH / Launcher configuration
       ↓
Command Prompt
       ↓
python --version
       ↓
Python Shell
       ↓
print("Hello")
       ↓
Python Ready
```

---

# 23. Important Note About Book Versions

Agar aap jis book ko follow kar rahe ho usmein:

```text
Python 2.7.x and 3.x
```

likha hua hai, to ho sakta hai book purani ho aur Python 2.7 ko bhi explain kar rahi ho.

Aapko concept samajhne ke liye dono versions ka historical difference dekhna useful hai.

Lekin **new Python projects ke liye Python 3 syntax aur Python 3 ecosystem ko follow karo**.

---

# Section 1.10 — Quick Revision

### Python Interpreter

Python code execute karta hai.

```text
Code → Interpreter → Output
```

### Python 2.7

Legacy version hai aur iska official support **2020 mein end** ho chuka hai.

### Python 3

Modern Python development ke liye use hota hai.

### Version Check

```text
python --version
```

ya:

```text
py --version
```

### Python Shell

```text
python
```

phir:

```python
>>>
```

### IDLE

Python ke saath available graphical development environment hai.

### pip

Python packages install/manage karne ke liye use hota hai.

---

## Practice

Apne Windows Command Prompt mein ye commands try karo:

```text
python --version
```

```text
py --version
```

```text
python -m pip --version
```

Phir:

```text
python
```

Aur Python Shell mein:

```python
print("Hello Python")
```

Agar sab successful hain, to aapki Python installation basic level par ready hai.
# Section 1.11 — String Functions: `str()` and `repr()`

Python mein `str()` aur `repr()` dono bohat useful functions hain.

Dono ka relation **object ki representation** se hai, lekin dono ka use-case different hai.

Simple rule:

```text
str()  → User-friendly representation
repr() → Developer/debugging representation
```

---

# 1. `str()` kya hai?

`str()` kisi object ka **readable string representation** return karta hai.

Example:

```python id="x7k5a1"
age = 25

result = str(age)

print(result)
```

Output:

```text id="d4z0r2"
25
```

Ab:

```python id="q9t3wb"
print(type(result))
```

Output:

```text id="9h6f2e"
<class 'str'>
```

Yani:

```text
25
```

originally integer tha:

```python
int
```

lekin `str()` ke baad:

```python
str
```

ban gaya.

---

# 2. `str()` ka Practical Use

Suppose:

```python id="x4j6vp"
age = 25
```

Agar humein text ke saath concatenate karna ho:

```python id="j3w8ka"
print("My age is " + str(age))
```

Output:

```text id="w8s1nf"
My age is 25
```

Kyun ke:

```text
"My age is " → string
25           → integer
```

Python directly dono ko `+` se concatenate nahi karega.

`str(age)` integer ko string bana deta hai.

---

# 3. `str()` ke Different Examples

Integer:

```python id="s0p6cz"
print(str(100))
```

Float:

```python id="x6a1we"
print(str(25.50))
```

Boolean:

```python id="z8p4qk"
print(str(True))
```

List:

```python id="w2h7nx"
print(str([10, 20, 30]))
```

Dictionary:

```python id="c1v9rm"
print(str({"name": "Muhammad", "age": 25}))
```

`str()` different Python objects ko readable text representation mein convert kar sakta hai.

---

# 4. `repr()` kya hai?

`repr()` ka matlab generally **representation** samjha ja sakta hai.

Ye object ki aisi representation return karne ki koshish karta hai jo **developer/programmer ke liye useful aur unambiguous** ho.

Example:

```python id="h4q7cs"
name = "Muhammad"

print(str(name))
print(repr(name))
```

Output:

```text id="p9d1kw"
Muhammad
'Muhammad'
```

Difference dekho:

```text
str()
→ Muhammad

repr()
→ 'Muhammad'
```

`repr()` ne quotes bhi show kiye.

---

# 5. String ka Important Difference

Example:

```python id="j7c2pa"
text = "Hello Python"
```

`str()`:

```python id="k8w5nz"
print(str(text))
```

Output:

```text id="4b9xq1"
Hello Python
```

`repr()`:

```python id="m3f8tv"
print(repr(text))
```

Output:

```text id="n2k6yd"
'Hello Python'
```

Yahan quotes important information de rahe hain ke value ek Python string hai.

---

# 6. Whitespace ko Samajhna

`repr()` debugging mein especially useful hota hai.

Example:

```python id="v1j8rq"
text = "Hello\nWorld"
```

Agar:

```python id="q7k2mc"
print(str(text))
```

Output:

```text id="x5d9pt"
Hello
World
```

Kyun ke `\n` newline create karta hai.

Lekin:

```python id="b4m6zs"
print(repr(text))
```

Output:

```text id="c8w2la"
'Hello\nWorld'
```

Yahan `repr()` clearly show karta hai ke string ke andar `\n` character present hai.

Ye debugging ke liye bohat useful hai.

---

# 7. Space ko Detect Karna

Suppose:

```python id="y8r4qp"
name = "Muhammad "
```

Notice:

```text
Muhammad
        ↑
      extra space
```

Agar:

```python id="m5k1td"
print(str(name))
```

to output dekh kar extra space easily notice nahi hoga.

Lekin:

```python id="p3n7vx"
print(repr(name))
```

Output:

```text id="w6c9ra"
'Muhammad '
```

Ab ending space clearly visible context mein samajh aata hai.

---

# 8. `str()` vs `repr()`

Simple comparison:

| Feature           | `str()`                | `repr()`                 |
| ----------------- | ---------------------- | ------------------------ |
| Main purpose      | User-friendly output   | Developer representation |
| Readability       | Human-friendly         | Debugging-friendly       |
| String quotes     | Usually show nahi hoti | Usually visible          |
| Escape characters | Display form           | Representation form      |
| Debugging         | Less useful            | Very useful              |

Simple rule:

```text
str()
↓
"User ko kya dikhana hai?"

repr()
↓
"Developer ko actual representation kya dikhani hai?"
```

---

# 9. Numbers ke Saath

Integer:

```python id="r8v3km"
number = 25

print(str(number))
print(repr(number))
```

Output:

```text id="d4f1qa"
25
25
```

Yahan dono same nazar aa sakte hain.

Kyun?

Kyun ke integer `25` ki representation simple hai.

---

# 10. List ke Saath

Example:

```python id="a6p2xk"
items = ["Apple", "Banana", "Orange"]

print(str(items))
print(repr(items))
```

Dono ka output generally similar hoga:

```text id="m8q4vz"
['Apple', 'Banana', 'Orange']
```

Lekin conceptually dono functions ka purpose different hai.

`str()` readable form provide karta hai.

`repr()` programmer-oriented representation provide karta hai.

---

# 11. Dictionary ke Saath

```python id="k7v2qs"
employee = {
    "name": "Muhammad",
    "age": 25
}

print(str(employee))
print(repr(employee))
```

Output dono cases mein generally similar Python-style representation ho sakta hai:

```text id="e5w9bc"
{'name': 'Muhammad', 'age': 25}
```

Phir bhi `repr()` ka focus developer/debugging representation par hai.

---

# 12. `print()` aur `repr()` ka Difference

Ek interesting example:

```python id="t6c3yj"
name = "Muhammad"

print(name)
print(repr(name))
```

Output:

```text id="f4r8kp"
Muhammad
'Muhammad'
```

`print()` internally object ki user-facing string representation use karta hai.

`repr()` explicitly developer-oriented representation deta hai.

---

# 13. Debugging Example

Suppose aapke program mein user ka naam expected tha:

```text
Muhammad
```

Lekin comparison kaam nahi kar raha.

Aap:

```python id="j9w2sf"
name = input("Enter name: ")

print(name)
```

karoge to:

```text id="5s8c2m"
Muhammad
```

dikh sakta hai.

Lekin actual value ho sakti hai:

```text
"Muhammad "
```

ya:

```text
" Muhammad"
```

Debugging ke liye:

```python id="p1x6vz"
print(repr(name))
```

karna useful hai.

Output:

```text id="q8m3dn"
'Muhammad '
```

Ab extra space identify ho sakta hai.

---

# 14. `repr()` Debugging mein Important Kyun Hai?

Imagine karo:

```python id="s2k7cf"
data = "ABC\nDEF"
```

Normal print:

```python id="m4v9qa"
print(data)
```

Output:

```text id="e1z6tp"
ABC
DEF
```

Agar aapko actual stored value inspect karni hai:

```python id="n8c3wr"
print(repr(data))
```

Output:

```text id="h5q1js"
'ABC\nDEF'
```

Ab aapko clearly pata chal raha hai:

> String mein actual newline escape sequence hai.

---

# 15. `str()` aur Type Conversion

`str()` ko hum type conversion ke liye bhi use karte hain.

Example:

```python id="u7x4kp"
quantity = 10

quantity_text = str(quantity)

print(type(quantity))
print(type(quantity_text))
```

Output:

```text id="g3r8lm"
<class 'int'>
<class 'str'>
```

Yani:

```text
int
 ↓
str()
 ↓
str
```

---

# 16. `repr()` Type Conversion Jaisa Same Concept Nahi

Ye distinction important hai.

```python id="f9k2vz"
number = 25

print(type(number))
print(type(repr(number)))
```

Output:

```text id="w3m7qa"
<class 'int'>
<class 'str'>
```

`repr()` ka result bhi string hota hai.

Lekin iska main purpose ye nahi ke aap normal user input ko text mein convert karke display karo.

Iska purpose object ki **developer-oriented representation** dena hai.

---

# 17. Custom Objects mein `str()` aur `repr()`

Python mein hum apne classes/objects ke liye `__str__()` aur `__repr__()` define kar sakte hain.

Example:

```python id="q6n1ys"
class Employee:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

Object:

```python id="a4v8kc"
employee = Employee("Muhammad", 25)
```

Baad mein hum class mein:

```python id="r7p3xm"
__str__()
```

aur:

```python id="v2k9fd"
__repr__()
```

define karke decide kar sakte hain ke object user aur developer ko kaise represent ho.

Is concept ko hum **Object-Oriented Programming** mein detail se padhenge.

---

# 18. `repr()` ka Common Use

Debugging:

```python id="x3q7la"
value = "Hello\nPython"

print("Value:", repr(value))
```

Output:

```text id="c6w1zr"
Value: 'Hello\nPython'
```

Ye debugging ke waqt useful hai kyun ke hidden characters aur escape sequences visible ho sakte hain.

---

# 19. Practical Example — CSV/Data Cleaning

Suppose CSV se data read hua:

```python id="m9f4tk"
room = "Room 101 "
```

Aap check karna chahte ho ke koi hidden spaces hain ya nahi:

```python id="j1v8pc"
print(repr(room))
```

Output:

```text id="d5k2ys"
'Room 101 '
```

Ab pata chal gaya ke ending mein extra space hai.

Phir cleaning:

```python id="n4x7qb"
room = room.strip()

print(repr(room))
```

Output:

```text id="v8c3lm"
'Room 101'
```

Ye data cleaning aur debugging mein practical use hai.

---

# 20. Simple Rule Yaad Rakho

Agar aapko user ko value dikhani hai:

```python id="e7m2qs"
str()
```

Agar aapko developer ke taur par value inspect/debug karni hai:

```python id="k5p9wd"
repr()
```

Example:

```python id="h8r3zx"
name = "Muhammad"

print(str(name))
print(repr(name))
```

Result:

```text id="c4q7vn"
Muhammad
'Muhammad'
```

---

# 21. Practice Exercise

### Exercise 1

```python id="p2x8mk"
name = "Muhammad"

print(str(name))
print(repr(name))
```

Dono outputs observe karo.

---

### Exercise 2

Is string ko test karo:

```python id="v6k1rs"
text = "Hello\nPython"
```

Run:

```python id="z4m9cq"
print(text)
print(repr(text))
```

Dono outputs ka difference observe karo.

---

### Exercise 3

Extra spaces:

```python id="n7q3bf"
room = "Room 101 "
```

Run:

```python id="t5w8ka"
print(repr(room))
```

Phir:

```python id="y2c6mp"
room = room.strip()

print(repr(room))
```

Difference observe karo.

---

# Section 1.11 — Quick Revision

### `str()`

Readable string representation.

```python id="u8j4cn"
age = 25

text = str(age)
```

Useful for:

* String conversion
* User-friendly output
* Concatenation

---

### `repr()`

Developer-oriented representation.

```python id="b3k7qp"
name = "Muhammad"

print(repr(name))
```

Useful for:

* Debugging
* Hidden spaces identify karna
* Escape characters inspect karna
* Object representation samajhna

---

## Final Difference

```text
str()
 ↓
Human/User-friendly representation
```

```text
repr()
 ↓
Developer/Debugging representation
```

Ek line mein:

> **`str()` ka focus readable output hai, jab ke `repr()` ka focus object ki useful developer representation hai.**
# Section 1.12 — Installing External Modules Using `pip`

Section 1.8 mein humne Python ke built-in aur standard modules dekhe thay:

```python
import math
import random
import datetime
```

Lekin Python ecosystem mein bohat saari additional libraries available hain jo Python ke saath by default install nahi hoti.

In external packages ko install karne ke liye commonly **`pip`** use hota hai.

---

# 1. `pip` kya hai?

`pip` Python packages ko:

* install
* update
* uninstall

karne ke liye commonly used package-management tool hai.

Simple flow:

```text
Python
   ↓
pip
   ↓
External Package
   ↓
Python Program mein Use
```

---

# 2. Package kya hota hai?

Simple beginner-level definition:

> **Package reusable Python code ka collection hota hai jo doosre Python programs mein use kiya ja sakta hai.**

Example packages:

```text
requests
pandas
numpy
openpyxl
matplotlib
```

In packages ke different purposes hain.

---

# 3. Built-in/Standard Module vs External Package

### Standard Library

Python installation ke saath commonly available:

```python
import math
import random
import datetime
```

### External Package

Usually separately install karna padta hai:

```text
pandas
requests
openpyxl
```

Phir Python code mein import:

```python
import pandas
```

---

# 4. `pip` Check Karna

Windows Command Prompt open karo.

Run:

```text
python -m pip --version
```

Example output:

```text
pip 25.x.x from ...
```

Exact version aapke system par depend karega.

Agar ye command successfully run hoti hai, to pip available hai.

---

# 5. Package Install Karna

Basic syntax:

```text
python -m pip install package_name
```

Example:

```text
python -m pip install requests
```

Yahan:

```text
python
   ↓
-m pip
   ↓
install
   ↓
requests
```

ka matlab hai ke Python ke through pip ko run karke `requests` package install karo.

---

# 6. `requests` Package Example

`requests` HTTP requests ke liye commonly used Python package hai.

Install:

```text
python -m pip install requests
```

Phir Python program mein:

```python
import requests
```

Ab package ki functionality use ki ja sakti hai.

---

# 7. `pandas` Install Karna

Data analysis ke liye Python ecosystem mein `pandas` bohat commonly used package hai.

Install:

```text
python -m pip install pandas
```

Phir:

```python
import pandas as pd
```

Example:

```python
import pandas as pd

data = [10, 20, 30]

series = pd.Series(data)

print(series)
```

Yahan:

```text
pandas → package
pd     → alias
Series → pandas functionality
```

---

# 8. `openpyxl` Install Karna

Excel `.xlsx` files ke saath kaam karne ke liye `openpyxl` useful package hai.

Install:

```text
python -m pip install openpyxl
```

Phir:

```python
import openpyxl
```

Iska use Excel workbooks ko read/write karne ke liye kiya ja sakta hai.

---

# 9. Package Install Hone ke Baad Import

Ye distinction bohat important hai.

Command Prompt mein:

```text
python -m pip install pandas
```

Package **install** karta hai.

Python code mein:

```python
import pandas
```

Package ko **program mein use** karne ke liye import karta hai.

Yani:

```text
pip install
     ↓
Package computer/environment mein available
     ↓
import
     ↓
Python program mein use
```

---

# 10. Package Uninstall Karna

Agar package remove karna ho:

```text
python -m pip uninstall requests
```

pip confirmation maang sakta hai.

Confirm karne ke baad package uninstall ho jayega.

---

# 11. Package Update Karna

Existing package ko update karne ke liye:

```text
python -m pip install --upgrade requests
```

Ye `requests` ko available newer version par update karne ki koshish karega.

---

# 12. Installed Packages Dekhna

Installed packages ki list dekhne ke liye:

```text
python -m pip list
```

Example output:

```text
Package    Version
---------- -------
pip        ...
pandas     ...
requests   ...
```

Aapke computer par list different ho sakti hai.

---

# 13. Specific Package ki Information

Kisi package ke baare mein information:

```text
python -m pip show pandas
```

Ismein package ke related information show ho sakti hai, jaise:

* Name
* Version
* Location
* Dependencies

---

# 14. Package Install Hua Ya Nahi — Test

Suppose `requests` install kiya:

```text
python -m pip install requests
```

Ab Python:

```python
import requests

print(requests.__version__)
```

Agar import successfully ho jaye, package available hai.

---

# 15. `pip` aur `python -m pip`

Aapko internet par ye command bhi mil sakti hai:

```text
pip install pandas
```

Ye commonly work kar sakti hai.

Lekin beginner ke liye ye form zyada clear aur reliable habit ho sakti hai:

```text
python -m pip install pandas
```

Kyun?

Kyun ke ye explicitly current `python` interpreter ke saath pip run karne ko kehta hai.

Multiple Python installations wale systems mein ye distinction useful ho sakta hai.

---

# 16. Multiple Python Versions ka Issue

Suppose computer mein:

```text
Python 3.11
Python 3.13
```

dono installed hain.

Aapko ensure karna hota hai ke package **usi Python environment** mein install ho raha hai jahan aap program run karoge.

Isliye:

```text
python -m pip install pandas
```

aur:

```text
python
```

ke interpreter ka relationship important hai.

Windows par Python Launcher ke saath specific version bhi target kiya ja sakta hai, for example:

```text
py -3.13 -m pip install pandas
```

agar Python 3.13 installed ho.

---

# 17. External Module Install Karne ka Complete Process

Example `pandas`:

### Step 1 — Command Prompt

```text
python -m pip install pandas
```

### Step 2 — Installation complete hone ka wait

pip package aur uski required dependencies install karega.

### Step 3 — Python open karo

```text
python
```

### Step 4 — Import karo

```python
import pandas
```

### Step 5 — Test karo

```python
print(pandas.__version__)
```

Agar version show ho jaye, basic installation successful hai.

---

# 18. Dependencies kya hoti hain?

Kabhi package ko doosre packages ki bhi zaroorat hoti hai.

Example:

```text
Your Package
    ↓
Dependency A
    ↓
Dependency B
```

`pip` package install karte waqt required dependencies ko bhi install kar sakta hai.

Isliye ek command:

```text
python -m pip install some_package
```

se multiple related packages install ho sakte hain.

---

# 19. Version Specify Karna

Kabhi humein package ka specific version install karna hota hai.

General syntax:

```text
python -m pip install package_name==version
```

Example:

```text
python -m pip install requests==2.32.0
```

Yahan:

```text
requests
   ↓
package

==
   ↓
exact version

2.32.0
   ↓
version
```

Real projects mein package compatibility ke liye version control important ho sakta hai.

---

# 20. `requirements.txt`

Python projects mein commonly ek file hoti hai:

```text
requirements.txt
```

Is file mein project ki dependencies list ki ja sakti hain.

Example:

```text
pandas
requests
openpyxl
```

Ya versions ke saath:

```text
pandas==...
requests==...
openpyxl==...
```

Phir requirements file se packages install kiye ja sakte hain:

```text
python -m pip install -r requirements.txt
```

Iska benefit ye hai ke project ki required dependencies ko ek jagah define kiya ja sakta hai.

---

# 21. Virtual Environment ka Basic Concept

External packages ke saath kaam karte waqt **virtual environment** bohat important concept hai.

Virtual environment project ke liye isolated Python environment provide karta hai.

Example:

```text
Project A
   ↓
Environment A
   ↓
pandas version A

Project B
   ↓
Environment B
   ↓
pandas version B
```

Isse different projects ki dependencies ko separate rakhna easier hota hai.

Is topic ko hum baad mein detail mein kar sakte hain.

---

# 22. `pip` Error ka Example

Agar aap run karo:

```text
python -m pip install abcxyz
```

aur `abcxyz` valid package available nahi hai, to pip error de sakta hai.

Isi tarah:

```text
python -m pip install pandas
```

network, permissions, Python version compatibility, ya environment issues ki wajah se fail ho sakta hai.

Error message ko carefully read karna important hai.

---

# 23. Permission Problem

Kabhi Windows mein package install karte waqt permission issue aa sakta hai.

Especially agar Python system-wide install hua ho aur current user ko installation directory mein write permission na ho.

Aise cases mein **virtual environment** use karna generally better development approach hai.

`--user` installation bhi kuch situations mein available hoti hai:

```text
python -m pip install --user package_name
```

Lekin project-based development ke liye virtual environments ko samajhna zyada useful hai.

---

# 24. Practical Example — Data Analysis

Aap Python mein CSV data analyze karna chahte ho.

Pehle:

```text
python -m pip install pandas
```

Phir:

```python
import pandas as pd

data = pd.read_csv("data.csv")

print(data.head())
```

Flow:

```text
CSV File
   ↓
pandas
   ↓
DataFrame
   ↓
Analysis
```

Ye real-world data analysis mein common workflow hai.

---

# 25. Practical Example — Excel

Excel file ke saath kaam karna ho:

```text
python -m pip install openpyxl
```

Phir:

```python
import openpyxl

workbook = openpyxl.load_workbook("data.xlsx")

print(workbook.sheetnames)
```

Yahan:

```text
openpyxl
   ↓
Excel workbook
   ↓
Python
```

---

# 26. Standard Library vs External Package

Is difference ko yaad rakho:

### Standard Library

Usually Python ke saath available:

```python
import math
import os
import datetime
```

Usually separately pip install nahi karna padta.

### External Package

Usually separately install karna padta hai:

```text
pandas
requests
openpyxl
numpy
```

Phir code mein:

```python
import pandas
```

---

# 27. Common `pip` Commands

Ye commands important hain:

### Install

```text
python -m pip install package_name
```

### Uninstall

```text
python -m pip uninstall package_name
```

### Upgrade

```text
python -m pip install --upgrade package_name
```

### List

```text
python -m pip list
```

### Package information

```text
python -m pip show package_name
```

### Requirements install

```text
python -m pip install -r requirements.txt
```

---

# 28. Important Concept

Ye teen words confuse nahi karne:

```text
Module
Package
pip
```

### Module

Usually ek `.py` file containing reusable Python code.

Example:

```text
calculator.py
```

### Package

Related Python modules/code ka organized distribution.

Example:

```text
pandas
```

### pip

Python packages ko install/manage karne ka tool.

Example:

```text
python -m pip install pandas
```

---

# 29. Practice Exercise

### Exercise 1

Check karo pip installed hai:

```text
python -m pip --version
```

---

### Exercise 2

Installed packages dekho:

```text
python -m pip list
```

---

### Exercise 3

`requests` install karo:

```text
python -m pip install requests
```

Phir Python mein:

```python
import requests

print(requests.__version__)
```

---

### Exercise 4

`pandas` install karo:

```text
python -m pip install pandas
```

Phir:

```python
import pandas as pd

print(pd.__version__)
```

---

# Section 1.12 — Quick Revision

## `pip`

Python packages install/manage karne ka tool.

### Install:

```text
python -m pip install pandas
```

### Import:

```python
import pandas
```

### Check version:

```text
python -m pip show pandas
```

ya Python mein:

```python
import pandas

print(pandas.__version__)
```

### List packages:

```text
python -m pip list
```

### Uninstall:

```text
python -m pip uninstall pandas
```

### Upgrade:

```text
python -m pip install --upgrade pandas
```

---

## Complete Flow

```text
External Package
       ↓
pip install
       ↓
Package installed
       ↓
import package
       ↓
Use package functions/classes
```

Example:

```text
python -m pip install pandas
```

then:

```python
import pandas as pd

data = pd.read_csv("data.csv")

print(data.head())
```

**Core idea:** `pip` package ko install karta hai; `import` us installed package ko Python program ke andar available karta hai.
# Section 1.13 — Help Utility

Python mein har function ya module ka documentation yaad rakhna zaroori nahi.

Python khud humein ek built-in **`help()` function** deta hai jisse hum Python objects, functions, modules, classes aur keywords ke baare mein information dekh sakte hain.

---

# 1. `help()` kya hai?

`help()` Python ka built-in function hai.

Basic syntax:

```python
help(object)
```

Example:

```python
help(print)
```

Ye `print()` function ki documentation show karega.

---

# 2. `help()` ka simple example

Python Shell open karo:

```text
>>>
```

Phir:

```python
help(print)
```

Python `print()` ke baare mein information show karega.

Aapko arguments aur function ka purpose samajhne mein help milegi.

---

# 3. `help()` kisi module ke liye

Example:

```python
import math

help(math)
```

Ye `math` module ke baare mein documentation show karega.

Ismein module ke andar available functions/classes/constants ki information mil sakti hai.

---

# 4. Kisi Specific Function ki Help

Suppose humein `math.sqrt()` ke baare mein information chahiye.

```python
import math

help(math.sqrt)
```

Ye specifically `sqrt()` function ki documentation show karega.

---

# 5. `help()` aur `print()` mein Difference

Ye important distinction hai.

### `print()`

Kisi value ko display karta hai:

```python
print("Hello")
```

Output:

```text
Hello
```

### `help()`

Kisi Python object/function ke baare mein documentation/information provide karta hai:

```python
help(print)
```

Yani:

```text
print()
↓
Value display

help()
↓
Documentation / information
```

---

# 6. Python Shell mein `help()`

IDLE Python Shell mein:

```python
>>> help()
```

Aap Python ke interactive help system mein enter ho sakte ho.

Aksar prompt kuch is tarah appear hota hai:

```text
help>
```

Ab aap information search kar sakte ho.

Example:

```text
help> print
```

Help system `print` ke baare mein information dikhayega.

Exit karne ke liye:

```text
help> quit
```

ya generally:

```text
help> q
```

---

# 7. `help()` Function ke andar Direct Search

Aap direct keyword/function de sakte ho:

```python
help(len)
```

Example:

```python
help(str)
```

Ye `str` type ke baare mein information dega.

Similarly:

```python
help(list)
```

list ke baare mein documentation show karega.

---

# 8. Python Keywords ki Help

Python ke keywords ke liye bhi help system useful hai.

Example:

```python
help("if")
```

Ya:

```python
help("for")
```

Ya:

```python
help("while")
```

Ye Python language ke specific keyword ke baare mein information de sakta hai.

---

# 9. `help()` ke Saath String kyun?

Aapne dekha:

```python
help("if")
```

Yahan `"if"` string hai.

Python help system special language topics ko string ke through search kar sakta hai.

Examples:

```python
help("if")
help("for")
help("while")
help("class")
```

---

# 10. Module ke Function ko Search Karna

Suppose:

```python
import math
```

Math module mein kaunse functions hain, ye dekhna ho:

```python
help(math)
```

Specific function:

```python
help(math.sqrt)
```

Another example:

```python
help(math.ceil)
```

---

# 11. `dir()` — Available Names Dekhna

`help()` ke saath ek aur useful built-in function hai:

```python
dir()
```

`dir()` kisi object/module ke available attributes aur methods ke names dekhne mein help karta hai.

Example:

```python
import math

print(dir(math))
```

Isse `math` module ke andar available names ki list mil sakti hai.

---

# 12. `dir()` vs `help()`

Ye dono confuse nahi karna.

### `dir()`

Batata hai:

> "Is object/module ke paas kaunse names/methods available hain?"

Example:

```python
dir(math)
```

### `help()`

Batata hai:

> "Ye function/object kya karta hai aur isko kaise use karna hai?"

Example:

```python
help(math.sqrt)
```

Simple:

```text
dir()
↓
What is available?

help()
↓
What does it mean/how is it used?
```

---

# 13. String ke Saath `dir()`

Example:

```python
name = "Muhammad"

print(dir(name))
```

Isse string object ke available methods/names ki list mil sakti hai.

Aapko methods jaise:

```text
upper
lower
strip
replace
split
```

etc. nazar aa sakte hain.

Phir kisi specific method ki help:

```python
help(str.strip)
```

---

# 14. List ke Saath

Example:

```python
numbers = [10, 20, 30]

print(dir(numbers))
```

Aap list ke methods dekh sakte ho.

For example:

```python
help(list.append)
```

Ab `append()` ke baare mein information mil sakti hai.

---

# 15. `help()` Learning ke Liye Important Kyun Hai?

Beginner aksar har function ke liye internet search karta hai.

Lekin Python ke andar hi basic documentation explore ki ja sakti hai.

Example:

```python
help(str.replace)
```

Aapko pata chal sakta hai ke `replace()` kis purpose ke liye hai.

Similarly:

```python
help(list.append)
help(dict.get)
help(str.split)
```

---

# 16. Practical Example — CSV/Data Cleaning

Suppose aapke paas:

```python
name = " Muhammad "
```

Aur aapko extra spaces remove karne hain.

Aap `strip()` use karna jaante ho ya nahi, to:

```python
help(str.strip)
```

Phir:

```python
name = name.strip()

print(name)
```

Output:

```text
Muhammad
```

Yani documentation dekh kar method ka purpose samajh sakte ho.

---

# 17. Function ka Documentation `__doc__` se

Python objects ke paas aksar documentation string hoti hai jise:

```python
__doc__
```

se access kiya ja sakta hai.

Example:

```python
print(print.__doc__)
```

Ye `print()` function ki documentation string show kar sakta hai.

Similarly:

```python
print(str.strip.__doc__)
```

---

# 18. `help()` vs `__doc__`

### `help()`

```python
help(str.strip)
```

Readable documentation format provide karta hai.

### `__doc__`

```python
print(str.strip.__doc__)
```

Object ki documentation string directly access karta hai.

Beginner ke liye pehle:

```python
help()
```

ko master karna enough hai.

---

# 19. Practical Learning Workflow

Agar aapko koi method nahi pata:

### Step 1

Object identify karo.

```python
name = "Muhammad"
```

### Step 2

Available methods dekho:

```python
dir(name)
```

### Step 3

Suppose `upper` interesting laga:

```python
help(str.upper)
```

### Step 4

Use karo:

```python
print(name.upper())
```

Output:

```text
MUHAMMAD
```

Workflow:

```text
Object
  ↓
dir()
  ↓
Available methods
  ↓
help()
  ↓
Method samjho
  ↓
Use karo
```

---

# 20. Example — List

```python
numbers = [10, 20, 30]
```

Available methods:

```python
dir(numbers)
```

Suppose `append` use karna hai:

```python
help(list.append)
```

Phir:

```python
numbers.append(40)

print(numbers)
```

Output:

```text
[10, 20, 30, 40]
```

---

# 21. Example — Dictionary

```python
employee = {
    "name": "Muhammad",
    "age": 25
}
```

Available methods:

```python
dir(employee)
```

Suppose `get()` samajhna hai:

```python
help(dict.get)
```

Then:

```python
print(employee.get("name"))
```

Output:

```text
Muhammad
```

---

# 22. Important Built-in Functions Explore Karna

Aap in par `help()` practice kar sakte ho:

```python
help(len)
help(print)
help(input)
help(type)
help(str)
help(list)
help(tuple)
help(set)
help(dict)
```

Ye Python fundamentals strong karne ke liye useful exercise hai.

---

# 23. Important Difference: `help()` Documentation Hai, Search Engine Nahi

`help()` Python ki available documentation provide karta hai.

Agar aapko error ka complete solution chahiye, to sirf:

```python
help()
```

hamesha enough nahi hoga.

For example:

```text
ModuleNotFoundError
PermissionError
ValueError
```

jaise errors ke context mein error message ko samajhna aur documentation/reference dekhna bhi zaroori hota hai.

---

# 24. Practice Exercise

### Exercise 1

Run:

```python
help(print)
```

---

### Exercise 2

Run:

```python
help(str)
```

---

### Exercise 3

Run:

```python
help(list.append)
```

---

### Exercise 4

Run:

```python
help(dict.get)
```

---

### Exercise 5

Run:

```python
name = "python"

print(dir(name))
```

Phir:

```python
help(str.upper)
```

Aur:

```python
print(name.upper())
```

---

# 25. Quick Revision

### `help()`

Documentation/information ke liye:

```python
help(print)
```

### `dir()`

Available attributes/methods dekhne ke liye:

```python
dir("hello")
```

### `__doc__`

Documentation string access karne ke liye:

```python
print(str.strip.__doc__)
```

---

# Sabse Important Concept

Agar aapko Python mein koi object ya method samajh nahi aa raha:

```text
1. Object dekho
       ↓
2. dir() use karo
       ↓
3. Method identify karo
       ↓
4. help() use karo
       ↓
5. Method ko practice karo
```

Example:

```python
name = "Muhammad"

print(dir(name))

help(str.upper)

print(name.upper())
```

Is tarah aap Python documentation ko **khud explore karna** seekh sakte ho, jo programming seekhne mein bohat useful skill hai.
