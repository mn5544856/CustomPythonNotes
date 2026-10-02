# Chapter 2: Python Data Types

## Section 2.1 — String Data Type

Python mein **String** text/data ko represent karne ke liye use hoti hai.

Examples:

```python
name = "Muhammad"
city = "Riyadh"
country = "Saudi Arabia"
```

Yahan:

```text
"Muhammad"       → String
"Riyadh"         → String
"Saudi Arabia"   → String
```

---

# 1. String kya hoti hai?

Simple definition:

> **String characters ka sequence hoti hai.**

Characters mein:

* letters
* numbers
* spaces
* symbols

sab aa sakte hain.

Example:

```python
name = "Muhammad"
```

Is string mein characters hain:

```text
M u h a m m a d
```

---

# 2. String banane ke liye Quotes

Python mein string ko quotes ke andar likhte hain.

### Single quotes

```python
name = 'Muhammad'
```

### Double quotes

```python
name = "Muhammad"
```

Dono valid hain.

```python
name1 = 'Muhammad'
name2 = "Muhammad"

print(name1)
print(name2)
```

Output:

```text
Muhammad
Muhammad
```

---

# 3. Triple Quotes

Multiple lines ka text likhne ke liye triple quotes use kar sakte hain:

```python
message = """Hello
My name is Muhammad
I am learning Python"""
```

Print:

```python
print(message)
```

Output:

```text
Hello
My name is Muhammad
I am learning Python
```

Triple quotes documentation/docstrings ke liye bhi commonly use hoti hain.

---

# 4. String ka Type Check Karna

`type()` se check kar sakte hain:

```python
name = "Muhammad"

print(type(name))
```

Output:

```text
<class 'str'>
```

Yahan:

```text
str
↓
string
```

---

# 5. String mein Numbers

String ke andar numbers bhi ho sakte hain.

```python
age = "25"
```

Ye **number nahi**, String hai.

Check:

```python
print(type(age))
```

Output:

```text
<class 'str'>
```

Compare:

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

Is difference ko yaad rakhna bohat important hai.

---

# 6. String Concatenation

Do ya zyada strings ko `+` se join kar sakte hain.

```python
first_name = "Muhammad"
last_name = "Nouman"

full_name = first_name + " " + last_name

print(full_name)
```

Output:

```text
Muhammad Nouman
```

Yahan:

```text
first_name
    +
" "
    +
last_name
    ↓
full_name
```

Is process ko **concatenation** kehte hain.

---

# 7. String aur Number ko Directly `+` nahi kar sakte

Example:

```python
age = 25

print("Age: " + age)
```

Ye error dega kyun ke:

```text
"Age: " → str
25      → int
```

Python normally String aur Integer ko directly concatenate nahi karta.

Correct:

```python
age = 25

print("Age: " + str(age))
```

Output:

```text
Age: 25
```

Ya easier:

```python
print("Age:", age)
```

---

# 8. String Indexing

String ke har character ka ek **index** hota hai.

Example:

```python
name = "Python"
```

Index:

```text
Character:  P  y  t  h  o  n
Index:      0  1  2  3  4  5
```

Python mein indexing **0 se start** hoti hai.

---

# 9. Specific Character Access Karna

```python
name = "Python"

print(name[0])
```

Output:

```text
P
```

```python
print(name[1])
```

Output:

```text
y
```

```python
print(name[2])
```

Output:

```text
t
```

---

# 10. Negative Indexing

Python negative indexes bhi support karta hai.

```text
Character:   P   y   t   h   o   n
Positive:    0   1   2   3   4   5
Negative:   -6  -5  -4  -3  -2  -1
```

Example:

```python
name = "Python"

print(name[-1])
```

Output:

```text
n
```

Last character ke liye:

```python
name[-1]
```

bohat useful hai.

---

# 11. String Slicing

String ka ek portion nikalne ko **slicing** kehte hain.

Syntax:

```python
string[start:end]
```

Example:

```python
name = "Python"

print(name[0:3])
```

Output:

```text
Pyt
```

Important:

> `end` index include nahi hota.

`name[0:3]` ka matlab:

```text
0 → P
1 → y
2 → t
3 → stop
```

Result:

```text
Pyt
```

---

# 12. More Slicing Examples

```python
name = "Python"

print(name[2:6])
```

Output:

```text
thon
```

```python
print(name[:3])
```

Output:

```text
Pyt
```

```python
print(name[3:])
```

Output:

```text
hon
```

---

# 13. String ki Length

`len()` se String mein total characters count kar sakte hain.

```python
name = "Muhammad"

print(len(name))
```

Output:

```text
8
```

Spaces bhi character count hoti hain.

Example:

```python
name = "Muhammad Nouman"

print(len(name))
```

Space bhi count hoga.

---

# 14. String Methods

Python String ke saath bohat saare built-in methods provide karta hai.

Example:

```python
name = "muhammad"
```

### `upper()`

```python
print(name.upper())
```

Output:

```text
MUHAMMAD
```

### `lower()`

```python
name = "MUHAMMAD"

print(name.lower())
```

Output:

```text
muhammad
```

---

# 15. `strip()`

Extra spaces remove karne ke liye:

```python
name = "  Muhammad  "

print(name.strip())
```

Output:

```text
Muhammad
```

Ye **data cleaning** mein bohat useful hai.

Example CSV data:

```python
equipment = "  MEP-KHN-REF04  "

equipment = equipment.strip()

print(equipment)
```

Output:

```text
MEP-KHN-REF04
```

---

# 16. `replace()`

String ke andar text replace karne ke liye:

```python
text = "I like Python"

new_text = text.replace("Python", "Power BI")

print(new_text)
```

Output:

```text
I like Power BI
```

---

# 17. `split()`

String ko parts/list mein divide karne ke liye:

```python
text = "Python Power BI HVAC"

words = text.split()

print(words)
```

Output:

```text
['Python', 'Power', 'BI', 'HVAC']
```

Yani:

```text
String
   ↓
split()
   ↓
List
```

---

# 18. `join()`

`join()` ka use multiple strings ko ek string mein combine karne ke liye hota hai.

Example:

```python
words = ["Python", "Power", "BI"]

text = " ".join(words)

print(text)
```

Output:

```text
Python Power BI
```

Yahan:

```text
["Python", "Power", "BI"]
          ↓
      " ".join()
          ↓
"Python Power BI"
```

---

# 19. `in` Operator

Check kar sakte hain ke koi text String ke andar exist karta hai ya nahi.

```python
text = "I am learning Python"

print("Python" in text)
```

Output:

```text
True
```

Example:

```python
print("Java" in text)
```

Output:

```text
False
```

---

# 20. `not in`

Check karna ho ke text exist nahi karta:

```python
text = "I am learning Python"

print("Java" not in text)
```

Output:

```text
True
```

---

# 21. String Comparison

Strings ko compare bhi kar sakte hain.

```python
name1 = "Muhammad"
name2 = "Muhammad"

print(name1 == name2)
```

Output:

```text
True
```

Different:

```python
name1 = "Muhammad"
name2 = "Nouman"

print(name1 == name2)
```

Output:

```text
False
```

---

# 22. String Case Sensitive Hoti Hai

Python mein uppercase aur lowercase different hain.

```python
name1 = "Muhammad"
name2 = "muhammad"

print(name1 == name2)
```

Output:

```text
False
```

Kyun?

```text
Muhammad
muhammad
```

`M` aur `m` different characters hain.

Case-insensitive comparison ke liye:

```python
print(name1.lower() == name2.lower())
```

Output:

```text
True
```

---

# 23. Escape Characters

String ke andar special characters likhne ke liye **escape sequences** use hote hain.

### New line `\n`

```python
text = "Hello\nWorld"

print(text)
```

Output:

```text
Hello
World
```

### Tab `\t`

```python
text = "Name\tAge"

print(text)
```

Output:

```text
Name    Age
```

---

# 24. Quote ke Andar Quote

Suppose:

```python
text = "He said "Hello""
```

Ye problematic hai.

Single quotes use kar sakte hain:

```python
text = 'He said "Hello"'

print(text)
```

Output:

```text
He said "Hello"
```

Ya escape character:

```python
text = "He said \"Hello\""

print(text)
```

---

# 25. f-String

Variables ko String ke andar easily insert karne ke liye **f-string** bohat useful hai.

Example:

```python
name = "Muhammad"
age = 25

print(f"My name is {name} and I am {age} years old.")
```

Output:

```text
My name is Muhammad and I am 25 years old.
```

Yahan:

```text
f"..."
```

Python ko batata hai ke `{}` ke andar variables/expression evaluate karne hain.

---

# 26. Practical Example — Employee Data

```python
name = "Muhammad"
department = "Facility"
location = "Riyadh"

print(f"Name: {name}")
print(f"Department: {department}")
print(f"Location: {location}")
```

Output:

```text
Name: Muhammad
Department: Facility
Location: Riyadh
```

---

# 27. Important String Methods

Ye methods abhi remember karna useful hai:

| Method         | Purpose                     |
| -------------- | --------------------------- |
| `upper()`      | uppercase                   |
| `lower()`      | lowercase                   |
| `strip()`      | beginning/end spaces remove |
| `replace()`    | text replace                |
| `split()`      | String ko parts mein divide |
| `join()`       | Strings ko combine          |
| `startswith()` | starting text check         |
| `endswith()`   | ending text check           |
| `find()`       | text ki position find       |
| `count()`      | occurrences count           |

Example:

```python
text = "Python Python"

print(text.count("Python"))
```

Output:

```text
2
```

---

# 28. String Immutable Hoti Hai

Ye bohat important concept hai.

String **immutable** hoti hai.

Matlab existing String ke individual character ko directly change nahi kar sakte.

Example:

```python
name = "Python"

name[0] = "J"
```

Ye error dega.

Agar `"Python"` ko `"Jython"` banana hai to new String create karni hogi.

Example:

```python
name = "Python"

name = "J" + name[1:]

print(name)
```

Output:

```text
Jython
```

Ya:

```python
name = "Python"

name = name.replace("P", "J")

print(name)
```

---

# 29. String vs Integer

Ye difference strongly samjho:

```python
a = 10
b = "10"
```

```text
a → int
b → str
```

Check:

```python
print(type(a))
print(type(b))
```

Output:

```text
<class 'int'>
<class 'str'>
```

Calculation:

```python
print(a + 5)
```

Output:

```text
15
```

Lekin:

```python
print(b + 5)
```

Error dega.

Agar String `"10"` ko number banana hai:

```python
b = int(b)

print(b + 5)
```

Output:

```text
15
```

---

# 30. Real-World Data Cleaning Example

Suppose equipment data se value aayi:

```python
equipment_id = "  MEP-KHN-REF04  "
```

Clean:

```python
equipment_id = equipment_id.strip()
```

Uppercase:

```python
equipment_id = equipment_id.upper()
```

Final:

```python
print(equipment_id)
```

Output:

```text
MEP-KHN-REF04
```

Ye type ka String manipulation CSV/data-processing projects mein bohat common hai.

---

# Practice Exercises

## Exercise 1

Create:

```python
name = "Muhammad"
```

Print:

* name
* type
* length

---

## Exercise 2

Is String ko uppercase karo:

```python
city = "riyadh"
```

Expected:

```text
RIYADH
```

---

## Exercise 3

Extra spaces remove karo:

```python
text = "   Python   "
```

---

## Exercise 4

Is String mein `"Python"` exist karta hai ya nahi check karo:

```python
text = "I am learning Python"
```

---

## Exercise 5

Ye output generate karo:

```text
Name: Muhammad
Age: 25
City: Riyadh
```

f-string use karke.

---

## Exercise 6

Is String ko split karo:

```python
skills = "Python,Power BI,HVAC"
```

Hint:

```python
skills.split(",")
```

Expected result:

```python
['Python', 'Power BI', 'HVAC']
```

---

# Quick Revision

### String create:

```python
name = "Muhammad"
```

### Type:

```python
type(name)
```

### Length:

```python
len(name)
```

### Index:

```python
name[0]
```

### Last character:

```python
name[-1]
```

### Slice:

```python
name[0:3]
```

### Uppercase:

```python
name.upper()
```

### Lowercase:

```python
name.lower()
```

### Spaces remove:

```python
name.strip()
```

### Replace:

```python
name.replace("old", "new")
```

### Split:

```python
name.split()
```

### Search:

```python
"Python" in text
```

### f-string:

```python
f"Hello {name}"
```

---

## Sabse Important Points

```text
String
  ↓
Text/characters ka sequence

Index
  ↓
0 se start

Negative index
  ↓
-1 se last character

Slicing
  ↓
[start:end]

len()
  ↓
characters count

upper/lower
  ↓
case change

strip()
  ↓
extra beginning/end spaces remove

split()
  ↓
String → List

join()
  ↓
multiple Strings → one String

String
  ↓
Immutable
```

**Next section: 2.2 — Set Data Types.**
# Chapter 2: Python Data Types

## Section 2.2 — Set Data Types

Python mein **Set** ek collection data type hai jo **unique values** store karta hai.

Sabse important rule:

> **Set mein duplicate values nahi hoti.**

Example:

```python
numbers = {10, 20, 30, 20, 10}

print(numbers)
```

Result mein duplicate values remove ho jayengi:

```text
{10, 20, 30}
```

---

# 1. Set kya hai?

Set ko curly braces `{}` se create kar sakte hain:

```python
numbers = {10, 20, 30}
```

Yahan:

```text
10
20
30
```

teen unique values hain.

Type check:

```python
print(type(numbers))
```

Output:

```text
<class 'set'>
```

---

# 2. Set ki Main Properties

Set ki important properties:

* **Unique values**
* Mutable
* Unordered
* Indexing nahi hoti
* Duplicate values automatically remove hoti hain

Example:

```python
skills = {"Python", "Power BI", "HVAC", "Python"}

print(skills)
```

`Python` do baar diya gaya tha, lekin Set mein ek hi baar rahega.

---

# 3. Duplicate Values

Example:

```python
numbers = {1, 2, 3, 2, 4, 1, 5}

print(numbers)
```

Conceptually result:

```text
{1, 2, 3, 4, 5}
```

Set automatically duplicate values ko eliminate karta hai.

---

# 4. Set Unordered Hai

List mein order/index hota hai:

```python
numbers = [10, 20, 30]
```

Aap:

```python
print(numbers[0])
```

kar sakte ho.

Lekin Set mein:

```python
numbers = {10, 20, 30}
```

ye nahi karna:

```python
print(numbers[0])
```

Kyun ke Set **index-based collection nahi hai**.

---

# 5. Set mein Indexing Nahi Hoti

Example:

```python
skills = {"Python", "Power BI", "HVAC"}
```

Ye incorrect approach hai:

```python
print(skills[0])
```

Set mein specific position se value access nahi karte.

Agar aapko har value dekhni hai, loop use kar sakte ho:

```python
for skill in skills:
    print(skill)
```

---

# 6. Set Create Karna

Simple:

```python
fruits = {"apple", "banana", "orange"}
```

Numbers:

```python
numbers = {10, 20, 30}
```

Mixed types:

```python
data = {"Muhammad", 25, True}
```

Lekin real projects mein Set ko usually logically related values ke liye use karna better hota hai.

---

# 7. Empty Set

Yahan beginner mistake hoti hai.

Agar aap likho:

```python
empty = {}
```

to ye **empty dictionary** hoti hai, Set nahi.

Check:

```python
print(type(empty))
```

Output:

```text
<class 'dict'>
```

Empty Set banane ke liye:

```python
empty = set()
```

Check:

```python
print(type(empty))
```

Output:

```text
<class 'set'>
```

Important:

```text
{}       → Dictionary
set()    → Empty Set
```

---

# 8. `set()` Function

List ya Tuple ko Set mein convert kar sakte hain.

Example:

```python
numbers = [10, 20, 30, 20, 10]

unique_numbers = set(numbers)

print(unique_numbers)
```

Result:

```text
{10, 20, 30}
```

Yahan:

```text
List
  ↓
set()
  ↓
Set
  ↓
Duplicates removed
```

---

# 9. Set mein Value Add Karna

Set mein ek new value add karne ke liye:

```python
add()
```

Example:

```python
skills = {"Python", "Power BI"}

skills.add("HVAC")

print(skills)
```

Ab Set mein `HVAC` bhi aa jayega.

---

# 10. Existing Value Add Karna

Agar value already exist karti hai:

```python
skills = {"Python", "Power BI"}

skills.add("Python")

print(skills)
```

Duplicate create nahi hoga.

Set mein:

```text
Python
Power BI
```

hi rahenge.

---

# 11. Multiple Values Add Karna — `update()`

Agar multiple values add karni hain:

```python
skills = {"Python", "Power BI"}

skills.update(["HVAC", "CNC", "Java"])

print(skills)
```

Ab Set mein additional values aa jayengi.

`update()` iterable values ko Set mein add karta hai.

---

# 12. Value Remove Karna — `remove()`

Example:

```python
skills = {"Python", "Power BI", "HVAC"}

skills.remove("HVAC")

print(skills)
```

`HVAC` remove ho jayega.

Lekin agar value Set mein exist nahi karti:

```python
skills.remove("Java")
```

to error aa sakta hai.

---

# 13. `discard()`

Agar aap value remove karna chahte ho lekin value missing hone par error nahi chahiye:

```python
discard()
```

Example:

```python
skills = {"Python", "Power BI"}

skills.discard("Java")

print(skills)
```

`Java` exist nahi karta, lekin `discard()` error nahi deta.

---

# 14. `remove()` vs `discard()`

| Method      | Value exist karti hai | Value exist nahi karti |
| ----------- | --------------------- | ---------------------- |
| `remove()`  | Remove                | Error                  |
| `discard()` | Remove                | No error               |

Simple rule:

```text
remove()
↓
Missing value → error

discard()
↓
Missing value → safe
```

---

# 15. `pop()`

Set mein `pop()` ek element remove karta hai.

```python
numbers = {10, 20, 30}

value = numbers.pop()

print(value)
print(numbers)
```

Important:

> Set unordered hai, isliye `pop()` se kaunsi value remove hogi, us par rely nahi karna chahiye.

List mein `pop()` usually index/last-position behavior ke context mein use hota hai, lekin Set mein ye concept different hai.

---

# 16. Set ki Length

`len()` use kar sakte ho:

```python
skills = {"Python", "Power BI", "HVAC"}

print(len(skills))
```

Output:

```text
3
```

Duplicates count nahi hote.

Example:

```python
skills = {"Python", "Python", "HVAC"}

print(len(skills))
```

Result:

```text
2
```

---

# 17. `in` Operator

Set mein check karna bohat easy hai:

```python
skills = {"Python", "Power BI", "HVAC"}

print("Python" in skills)
```

Output:

```text
True
```

Example:

```python
print("Java" in skills)
```

Output:

```text
False
```

---

# 18. `not in`

```python
skills = {"Python", "Power BI", "HVAC"}

print("Java" not in skills)
```

Output:

```text
True
```

Meaning:

> Java Set ke andar nahi hai.

---

# 19. Set Operations

Sets ki sabse powerful features mein se ek **Set Operations** hain.

Important operations:

1. Union
2. Intersection
3. Difference
4. Symmetric Difference

---

# 20. Union

Union ka matlab:

> Dono Sets ki **all unique values** combine karna.

Example:

```python
a = {1, 2, 3}
b = {3, 4, 5}

result = a | b

print(result)
```

Result:

```text
{1, 2, 3, 4, 5}
```

Method form bhi:

```python
result = a.union(b)
```

---

# 21. Union ka Visual Concept

```text
A = {1, 2, 3}

B = {3, 4, 5}

A UNION B

= {1, 2, 3, 4, 5}
```

`3` dono mein tha, lekin result mein ek hi baar hai.

---

# 22. Intersection

Intersection ka matlab:

> Dono Sets mein jo values **common** hain.

Example:

```python
a = {1, 2, 3}
b = {3, 4, 5}

result = a & b

print(result)
```

Output:

```text
{3}
```

Method:

```python
result = a.intersection(b)
```

---

# 23. Difference

Difference:

> Pehle Set mein jo values hain, lekin doosre Set mein nahi.

Example:

```python
a = {1, 2, 3}
b = {3, 4, 5}

result = a - b

print(result)
```

Output:

```text
{1, 2}
```

Lekin:

```python
print(b - a)
```

Output:

```text
{4, 5}
```

Order important hai.

---

# 24. Symmetric Difference

Iska matlab:

> Dono Sets ki values jo **sirf ek Set mein** hain; common values nahi.

Example:

```python
a = {1, 2, 3}
b = {3, 4, 5}

result = a ^ b

print(result)
```

Output:

```text
{1, 2, 4, 5}
```

Common `3` remove ho gaya.

---

# 25. Set Operations Summary

```text
A = {1, 2, 3}
B = {3, 4, 5}
```

### Union

```python
A | B
```

Result:

```text
{1, 2, 3, 4, 5}
```

### Intersection

```python
A & B
```

Result:

```text
{3}
```

### Difference

```python
A - B
```

Result:

```text
{1, 2}
```

### Symmetric Difference

```python
A ^ B
```

Result:

```text
{1, 2, 4, 5}
```

---

# 26. Practical Example — Employee Skills

Suppose do employees ke skills:

```python
employee1 = {"Python", "Power BI", "Excel"}
employee2 = {"Python", "HVAC", "Excel"}
```

### Common skills

```python
common = employee1 & employee2

print(common)
```

Result:

```text
{"Python", "Excel"}
```

### Dono employees ki total unique skills

```python
all_skills = employee1 | employee2

print(all_skills)
```

Result conceptually:

```text
{"Python", "Power BI", "Excel", "HVAC"}
```

### Employee 1 ke unique skills

```python
unique1 = employee1 - employee2

print(unique1)
```

Result:

```text
{"Power BI"}
```

Ye real-world data comparison mein useful ho sakta hai.

---

# 27. Practical Example — Equipment IDs

Suppose ek system se IDs:

```python
system_a = {
    "MEP-KHN-REF04",
    "MEP-KHN-REF45",
    "MEP-KHN-REF44"
}
```

Doosre system se:

```python
system_b = {
    "MEP-KHN-REF45",
    "MEP-KHN-REF44",
    "MEP-KHN-REF50"
}
```

Common equipment:

```python
common = system_a & system_b

print(common)
```

Result:

```text
{
    "MEP-KHN-REF45",
    "MEP-KHN-REF44"
}
```

System A mein hain lekin System B mein nahi:

```python
missing_from_b = system_a - system_b

print(missing_from_b)
```

Result:

```text
{"MEP-KHN-REF04"}
```

Ye type ka comparison data cleaning/reconciliation mein useful hai.

---

# 28. Set aur List ka Difference

| Feature        | List    | Set         |
| -------------- | ------- | ----------- |
| Syntax         | `[]`    | `{}`        |
| Ordered        | Yes     | No          |
| Duplicate      | Allowed | Not allowed |
| Indexing       | Yes     | No          |
| Mutable        | Yes     | Yes         |
| `in` search    | Yes     | Yes         |
| Set operations | No      | Yes         |

Example:

```python
my_list = [10, 20, 20, 30]

my_set = {10, 20, 20, 30}
```

List:

```text
[10, 20, 20, 30]
```

Set:

```text
{10, 20, 30}
```

---

# 29. Set aur Tuple ka Difference

| Feature   | Set  | Tuple |
| --------- | ---- | ----- |
| Syntax    | `{}` | `()`  |
| Ordered   | No   | Yes   |
| Duplicate | No   | Yes   |
| Indexing  | No   | Yes   |
| Mutable   | Yes  | No    |

Example:

```python
my_set = {10, 20, 30}
my_tuple = (10, 20, 30)
```

---

# 30. Set Mutable Hai

Set ko create karne ke baad change kar sakte ho.

```python
skills = {"Python", "Power BI"}

skills.add("HVAC")

print(skills)
```

Set change ho gaya.

Isliye:

```text
Set → Mutable
```

---

# 31. Set ke Elements ke Baare Mein Important Rule

Set ke elements generally **hashable** hone chahiye.

Beginner level par iska simple meaning:

Set mein normally immutable/hashable values use hoti hain, jaise:

```python
numbers = {1, 2, 3}
```

```python
names = {"Ali", "Ahmed", "Muhammad"}
```

Lekin list ko directly Set ke andar nahi rakh sakte:

```python
data = {[1, 2], [3, 4]}
```

Ye error dega.

Is concept ko hum baad mein **hashing / hashable objects** ke topic mein detail se samajh sakte hain.

---

# 32. Important Beginner Mistake

Ye:

```python
data = {}
```

Set nahi hai.

Ye:

```python
data = set()
```

Empty Set hai.

Ya values ke saath:

```python
data = {1, 2, 3}
```

Set hai.

Yaad rakho:

```text
{}       → empty dictionary
set()    → empty set
{1, 2}   → set
```

---

# Practice Exercises

## Exercise 1 — Duplicates Remove

```python
numbers = [10, 20, 20, 30, 30, 40]
```

Is List ko Set mein convert karo.

Expected:

```text
{10, 20, 30, 40}
```

---

## Exercise 2 — Add

```python
skills = {"Python", "Power BI"}
```

`HVAC` add karo.

---

## Exercise 3 — Common Skills

```python
a = {"Python", "Excel", "Power BI"}
b = {"Python", "HVAC", "Excel"}
```

Common skills find karo.

Hint:

```python
a & b
```

---

## Exercise 4 — Difference

Find karo ke `a` mein kya hai jo `b` mein nahi:

```python
a - b
```

---

## Exercise 5 — Membership

```python
skills = {"Python", "Power BI", "HVAC"}
```

Check karo:

```python
"Python" in skills
```

aur:

```python
"Java" in skills
```

---

# Quick Revision

### Set create:

```python
skills = {"Python", "Power BI", "HVAC"}
```

### Duplicate remove:

```python
unique = set([1, 2, 2, 3])
```

### Add:

```python
skills.add("CNC")
```

### Multiple values:

```python
skills.update(["Java", "Excel"])
```

### Remove:

```python
skills.remove("Java")
```

### Safe remove:

```python
skills.discard("Java")
```

### Length:

```python
len(skills)
```

### Membership:

```python
"Python" in skills
```

### Union:

```python
a | b
```

### Intersection:

```python
a & b
```

### Difference:

```python
a - b
```

### Symmetric Difference:

```python
a ^ b
```

---

# Sabse Important Concept

Set ko ek simple example se yaad rakho:

```text
List
[Python, Python, HVAC, Excel]
       ↓
      set()
       ↓
{Python, HVAC, Excel}
```

**Set ka main purpose: unique values aur Set operations.**

Agar aapko **duplicates remove karne**, **common values find karne**, ya
# Chapter 2: Python Data Types

## Section 2.3 — Numbers Data Type

Python mein **Numbers** ko represent karne ke liye mainly 3 numeric data types use hote hain:

1. `int`
2. `float`
3. `complex`

Sabse zyada aap `int` aur `float` use karoge.

---

# 1. `int` — Integer

Integer ka matlab **whole number**.

Examples:

```python id="w7n2fy"
age = 25
quantity = 10
floor = 41
temperature = 60
```

In sab ka type `int` hai.

Check:

```python id="qg45bs"
print(type(age))
```

Output:

```text id="vkn8qk"
<class 'int'>
```

---

# 2. Negative Integers

Integer sirf positive numbers nahi hote.

Negative numbers bhi `int` ho sakte hain:

```python id="f0d5tq"
temperature = -5
balance = -100
```

Aur:

```python id="1t9p1j"
print(type(temperature))
```

Output:

```text id="4w3o4e"
<class 'int'>
```

---

# 3. Zero bhi Integer Hai

```python id="g8wz3b"
quantity = 0

print(type(quantity))
```

Output:

```text id="2lhj8m"
<class 'int'>
```

Yani:

```text id="jzlh1d"
10    → int
0     → int
-10   → int
```

---

# 4. `float` — Decimal Number

`float` decimal/fractional numbers ko represent karta hai.

Example:

```python id="p5d4js"
price = 25.50
temperature = 60.5
height = 1.75
```

Check:

```python id="t9e0l3"
print(type(price))
```

Output:

```text id="j11i5s"
<class 'float'>
```

---

# 5. Integer vs Float

```python id="xqj2os"
a = 10
b = 10.0
```

Dono numerically same value represent kar sakte hain, lekin data type different hai:

```python id="k9e7q3"
print(type(a))
print(type(b))
```

Output:

```text id="j1u9x0"
<class 'int'>
<class 'float'>
```

Simple:

```text id="4h8m0b"
10      → int
10.0    → float
10.5    → float
```

---

# 6. Arithmetic Operators

Numbers ke saath calculations karne ke liye operators use hote hain.

Important operators:

```text id="ttr6tg"
+    Addition
-    Subtraction
*    Multiplication
/    Division
//   Floor Division
%    Modulus
**   Exponentiation
```

---

# 7. Addition `+`

```python id="q0d3ng"
a = 10
b = 5

print(a + b)
```

Output:

```text id="9k5ohv"
15
```

---

# 8. Subtraction `-`

```python id="xq1c8e"
a = 10
b = 5

print(a - b)
```

Output:

```text id="5d5yqa"
5
```

---

# 9. Multiplication `*`

```python id="7a0w0x"
price = 25
quantity = 4

total = price * quantity

print(total)
```

Output:

```text id="2rjv1v"
100
```

Ye business/data calculations mein bohat common hai.

---

# 10. Division `/`

```python id="c1o7fc"
a = 10
b = 2

print(a / b)
```

Output:

```text id="0b6p9u"
5.0
```

Important:

> `/` ka result Python mein normally `float` hota hai.

Even:

```python id="t8k2kz"
10 / 2
```

result:

```text id="jyf6v6"
5.0
```

---

# 11. Floor Division `//`

`//` division karta hai aur result ko **floor** karta hai.

Example:

```python id="v7o8bw"
print(10 // 3)
```

Output:

```text id="qj4jv0"
3
```

Normal division:

```python id="h8d0s5"
print(10 / 3)
```

Output approximately:

```text id="q8x9jh"
3.3333333333333335
```

Floor division:

```text id="z6hj7j"
10 // 3
↓
3
```

---

# 12. Modulus `%`

`%` division ka **remainder** deta hai.

Example:

```python id="x1c1kq"
print(10 % 3)
```

Output:

```text id="t8t4cy"
1
```

Kyun?

```text id="z3zj3m"
10 ÷ 3

3 × 3 = 9
remainder = 1
```

Isliye:

```text id="zj1p3j"
10 % 3 = 1
```

---

# 13. Modulus ka Practical Use

Check karna ho number even hai ya odd:

```python id="8r6kyo"
number = 10

print(number % 2)
```

Output:

```text id="d9e7ah"
0
```

Agar:

```python id="8upnms"
number = 7

print(number % 2)
```

Output:

```text id="1m7jqa"
1
```

Rule:

```text id="b9qv1h"
number % 2 == 0
↓
Even

number % 2 != 0
↓
Odd
```

---

# 14. Exponentiation `**`

Power calculate karne ke liye:

```python id="u4f9h1"
print(2 ** 3)
```

Output:

```text id="u1s9o3"
8
```

Kyun?

```text id="4r4m1p"
2 × 2 × 2 = 8
```

Another example:

```python id="2r4jsf"
print(5 ** 2)
```

Output:

```text id="7v6y1j"
25
```

---

# 15. Operator Precedence

Agar ek expression mein multiple operators hain, Python specific order follow karta hai.

Example:

```python id="5d7npx"
result = 10 + 5 * 2

print(result)
```

Output:

```text id="6h3qv9"
20
```

Pehle:

```text id="9l9q2p"
5 * 2 = 10
```

phir:

```text id="8uj5oz"
10 + 10 = 20
```

---

# 16. Parentheses `()`

Calculation ka order control karne ke liye parentheses use karo.

```python id="db0wjr"
result = (10 + 5) * 2

print(result)
```

Output:

```text id="n88h7h"
30
```

Pehle:

```text id="19om7h"
10 + 5 = 15
```

phir:

```text id="8ysqg0"
15 * 2 = 30
```

---

# 17. Numeric Conversion

String ko Integer mein convert:

```python id="ynz4ta"
number = int("25")

print(number)
print(type(number))
```

Output:

```text id="xps6kz"
25
<class 'int'>
```

String ko Float mein:

```python id="4l3j9c"
price = float("25.50")

print(price)
```

Output:

```text id="t3zqjm"
25.5
```

---

# 18. Float ko Integer

```python id="8f3yde"
price = 25.75

number = int(price)

print(number)
```

Output:

```text id="o3n2j8"
25
```

Important:

`int()` yahan simply decimal part ko remove karta hai; ye normal mathematical rounding nahi karta.

Example:

```python id="0b7zqv"
print(int(25.99))
```

Output:

```text id="pqu0aw"
25
```

---

# 19. Rounding

Rounding ke liye `round()` use kar sakte ho.

```python id="c6zqjy"
number = 25.75

print(round(number))
```

Output:

```text id="spm7sn"
26
```

Specific decimal places:

```python id="6d8z6h"
number = 25.7567

print(round(number, 2))
```

Output:

```text id="q3j0ab"
25.76
```

---

# 20. `abs()`

Absolute value ke liye:

```python id="ck1s4q"
number = -25

print(abs(number))
```

Output:

```text id="f3u8a7"
25
```

Negative sign remove ho jata hai.

---

# 21. `min()` aur `max()`

Minimum:

```python id="z9v2iw"
numbers = [10, 20, 5, 40]

print(min(numbers))
```

Output:

```text id="b5b4eh"
5
```

Maximum:

```python id="2u5bby"
print(max(numbers))
```

Output:

```text id="xj93fe"
40
```

---

# 22. `sum()`

Numbers ka total:

```python id="r2e4p5"
numbers = [10, 20, 30]

print(sum(numbers))
```

Output:

```text id="yq8k2m"
60
```

---

# 23. Complex Numbers

Python ka third numeric type hai:

```text id="jzv5b7"
complex
```

Example:

```python id="gr2f1s"
number = 2 + 3j

print(type(number))
```

Output:

```text id="9j5b3x"
<class 'complex'>
```

Yahan:

```text id="j4j8k0"
2 → real part
3j → imaginary part
```

Complex numbers scientific/engineering aur mathematical applications mein use hote hain.

Beginner Python programming mein `int` aur `float` zyada commonly encounter honge.

---

# 24. Numeric Comparison

Numbers ko compare kar sakte ho:

```python id="3i7w8v"
a = 10
b = 20

print(a == b)
print(a != b)
print(a > b)
print(a < b)
```

Output:

```text id="x0ps3y"
False
True
False
True
```

Operators:

```text id="y8m9cw"
==    Equal
!=    Not equal
>     Greater than
<     Less than
>=    Greater than or equal
<=    Less than or equal
```

---

# 25. Numeric Boolean Result

Comparison ka result Boolean hota hai.

Example:

```python id="8a1v6h"
age = 25

print(age >= 18)
```

Output:

```text id="1d7l4p"
True
```

Type:

```python id="3r4l5v"
print(type(age >= 18))
```

Output:

```text id="x9j7s0"
<class 'bool'>
```

Yani:

```text id="o8s9p1"
Number comparison
       ↓
True / False
       ↓
bool
```

---

# 26. Integer aur Float Calculation

```python id="g1b2op"
a = 10
b = 2.5

result = a * b

print(result)
print(type(result))
```

Output:

```text id="1f6z9w"
25.0
<class 'float'>
```

Integer aur Float ko calculation mein combine karne par result aksar `float` ho sakta hai.

---

# 27. Augmented Assignment

Numbers ke saath short assignment operators bhi use hote hain.

Instead of:

```python id="j1b7q2"
total = 10
total = total + 5
```

likh sakte ho:

```python id="h7o1rx"
total = 10
total += 5
```

Result:

```text id="b0r6a1"
15
```

Similarly:

```python id="l0l6jk"
total -= 2
```

```python id="f3o8y4"
total *= 3
```

```python id="3v0t0w"
total /= 2
```

---

# 28. Practical Example — Sales

Suppose:

```python id="8x7l2q"
price = 25.50
quantity = 4
```

Total:

```python id="4v7w1n"
sales = price * quantity

print(sales)
```

Output:

```text id="2n3q4b"
102.0
```

Yahan:

```text id="y0x8md"
25.50 × 4 = 102.00
```

---

# 29. Practical Example — Temperature

```python id="v8p7s2"
temperature = 60

if temperature > 50:
    print("High temperature")
else:
    print("Normal temperature")
```

Output:

```text id="7t2j4f"
High temperature
```

Yahan numeric data ko condition ke saath use kiya gaya.

---

# 30. Practical Example — Quantity

```python id="f5m8k2"
quantity = 15

if quantity > 10:
    print("Large quantity")
else:
    print("Small quantity")
```

Output:

```text id="v4s7n1"
Large quantity
```

---

# 31. Floating-Point Precision

`float` ke saath ek important concept hai.

Computer floating-point numbers ko binary representation mein store karta hai, isliye kuch calculations mein tiny precision differences aa sakte hain.

Example:

```python id="u6v3r8"
print(0.1 + 0.2)
```

Output kuch systems/Python versions mein:

```text id="x9b2k1"
0.30000000000000004
```

Mathematical expectation:

```text id="y6n3s8"
0.1 + 0.2 = 0.3
```

Lekin floating-point representation ki wajah se tiny difference aa sakta hai.

Financial applications mein exact decimal arithmetic ke liye Python ka `decimal` module useful ho sakta hai.

---

# 32. Numbers Data Types Summary

| Data Type | Example | Meaning        |
| --------- | ------- | -------------- |
| `int`     | `25`    | Whole number   |
| `float`   | `25.5`  | Decimal number |
| `complex` | `2+3j`  | Complex number |

---

# 33. Operators Summary

| Operator | Meaning        | Example   | Result |
| -------- | -------------- | --------- | ------ |
| `+`      | Addition       | `10 + 5`  | `15`   |
| `-`      | Subtraction    | `10 - 5`  | `5`    |
| `*`      | Multiplication | `10 * 5`  | `50`   |
| `/`      | Division       | `10 / 5`  | `2.0`  |
| `//`     | Floor division | `10 // 3` | `3`    |
| `%`      | Remainder      | `10 % 3`  | `1`    |
| `**`     | Power          | `2 ** 3`  | `8`    |

---

# Practice Exercises

## Exercise 1

Create three variables:

```python id="v4h6z8"
age = 25
price = 50.5
temperature = -5
```

Har variable ka `type()` print karo.

---

## Exercise 2

Calculate:

```text id="j5x8p0"
Price = 25
Quantity = 8
```

Total sales find karo.

---

## Exercise 3

Find remainder:

```python id="m7q2c9"
print(25 % 4)
```

Pehle khud answer predict karo.

---

## Exercise 4

Check karo `50` even hai ya odd.

Hint:

```python id="x5d8s2"
50 % 2
```

---

## Exercise 5

Calculate:

```python id="a7k3m1"
print(2 ** 5)
```

---

## Exercise 6

Is expression ka result predict karo:

```python id="r8n4q6"
10 + 5 * 2
```

Phir:

```python id="c1v7p9"
(10 + 5) * 2
```

Dono ke difference ko samjho.

---

# Final Revision

```text id="k8s4n2"
Numbers
   │
   ├── int
   │     └── 10, 25, -5
   │
   ├── float
   │     └── 10.5, 25.75
   │
   └── complex
         └── 2 + 3j
```

Sabse important:

```text id="w4p7z1"
int
↓
Whole number

float
↓
Decimal number

complex
↓
Real + imaginary number
```

Aur calculations:

```text id="s2d6k8"
+     Addition
-     Subtraction
*     Multiplication
/     Division
//    Floor Division
%     Remainder
**    Power
```

**Next: Section 2.4 — List Data Type.**
# Chapter 2: Python Data Types

## Section 2.4 — List Data Type

Python mein **List** ek collection data type hai jo multiple values ko ek variable mein store karne ke liye use hoti hai.

Example:

```python
numbers = [10, 20, 30, 40]
```

Yahan ek hi variable `numbers` ke andar 4 values hain.

---

# 1. List kya hai?

Simple definition:

> **List ek ordered aur mutable collection hai jo multiple values store kar sakti hai.**

Example:

```python
skills = ["Python", "Power BI", "HVAC"]
```

Is List mein 3 items hain:

```text
Python
Power BI
HVAC
```

---

# 2. List banane ke liye `[]`

List normally square brackets `[]` se create hoti hai.

```python
fruits = ["Apple", "Banana", "Orange"]
```

Numbers:

```python
numbers = [10, 20, 30, 40]
```

Strings:

```python
names = ["Ali", "Ahmed", "Muhammad"]
```

---

# 3. List ka Type

`type()` se check kar sakte ho:

```python
skills = ["Python", "Power BI", "HVAC"]

print(type(skills))
```

Output:

```text
<class 'list'>
```

---

# 4. List Ordered Hoti Hai

List mein items ka order preserve hota hai.

```python
skills = ["Python", "Power BI", "HVAC"]
```

Order:

```text
Python
Power BI
HVAC
```

Aap indexing se specific item access kar sakte ho.

---

# 5. List Indexing

Python mein index `0` se start hota hai.

```python
skills = ["Python", "Power BI", "HVAC"]
```

Index:

```text
Item:      Python    Power BI    HVAC
Index:        0          1          2
```

First item:

```python
print(skills[0])
```

Output:

```text
Python
```

Second:

```python
print(skills[1])
```

Output:

```text
Power BI
```

Third:

```python
print(skills[2])
```

Output:

```text
HVAC
```

---

# 6. Negative Indexing

List mein negative indexing bhi hoti hai.

```text
Item:        Python   Power BI   HVAC
Positive:       0         1         2
Negative:      -3        -2        -1
```

Last item:

```python
print(skills[-1])
```

Output:

```text
HVAC
```

Second-last:

```python
print(skills[-2])
```

Output:

```text
Power BI
```

---

# 7. List Slicing

List ka portion nikalne ke liye slicing use karte hain.

Syntax:

```python
list[start:end]
```

Example:

```python
numbers = [10, 20, 30, 40, 50]

print(numbers[1:4])
```

Output:

```text
[20, 30, 40]
```

Yaad rakho:

> `end` index include nahi hota.

---

# 8. Slicing Examples

```python
numbers = [10, 20, 30, 40, 50]
```

First 3:

```python
print(numbers[:3])
```

Output:

```text
[10, 20, 30]
```

Last items:

```python
print(numbers[2:])
```

Output:

```text
[30, 40, 50]
```

Copy-like full slice:

```python
print(numbers[:])
```

---

# 9. List Mutable Hoti Hai

Ye List ka bohat important feature hai.

**Mutable** ka matlab:

> List create hone ke baad uske items ko change kar sakte ho.

Example:

```python
numbers = [10, 20, 30]

numbers[0] = 100

print(numbers)
```

Output:

```text
[100, 20, 30]
```

Pehle:

```text
[10, 20, 30]
```

Baad mein:

```text
[100, 20, 30]
```

---

# 10. List mein New Item Add Karna

Sabse common method:

```python
append()
```

Example:

```python
skills = ["Python", "Power BI"]

skills.append("HVAC")

print(skills)
```

Output:

```text
['Python', 'Power BI', 'HVAC']
```

`append()` item ko List ke **end** mein add karta hai.

---

# 11. `insert()`

Specific position par item add karna ho to `insert()` use karte hain.

Syntax:

```python
list.insert(index, value)
```

Example:

```python
skills = ["Python", "HVAC"]

skills.insert(1, "Power BI")

print(skills)
```

Output:

```text
['Python', 'Power BI', 'HVAC']
```

Yahan `"Power BI"` index `1` par insert hua.

---

# 12. `extend()`

Multiple items add karne ke liye `extend()` useful hai.

```python
skills = ["Python", "Power BI"]

skills.extend(["HVAC", "CNC"])

print(skills)
```

Output:

```text
['Python', 'Power BI', 'HVAC', 'CNC']
```

---

# 13. `append()` vs `extend()`

Ye difference important hai.

### `append()`

```python
numbers = [1, 2]

numbers.append([3, 4])

print(numbers)
```

Result:

```text
[1, 2, [3, 4]]
```

Puri List ek single item ke taur par add hui.

### `extend()`

```python
numbers = [1, 2]

numbers.extend([3, 4])

print(numbers)
```

Result:

```text
[1, 2, 3, 4]
```

Difference:

```text
append()
→ ek item add

extend()
→ multiple items add
```

---

# 14. List se Item Remove Karna — `remove()`

Value ke basis par remove:

```python
skills = ["Python", "Power BI", "HVAC"]

skills.remove("HVAC")

print(skills)
```

Output:

```text
['Python', 'Power BI']
```

Agar value List mein nahi hai to `remove()` error de sakta hai.

---

# 15. `pop()`

`pop()` index ke basis par item remove kar sakta hai.

```python
numbers = [10, 20, 30, 40]

value = numbers.pop(1)

print(value)
print(numbers)
```

Output:

```text
20
[10, 30, 40]
```

Yahan index `1` ka item remove hua.

---

# 16. `pop()` Without Index

Agar index nahi do:

```python
numbers = [10, 20, 30]

value = numbers.pop()

print(value)
print(numbers)
```

Output:

```text
30
[10, 20]
```

Normally last item remove hota hai.

---

# 17. `del`

Index ke basis par item delete karne ke liye `del` bhi use kar sakte ho.

```python
numbers = [10, 20, 30, 40]

del numbers[1]

print(numbers)
```

Output:

```text
[10, 30, 40]
```

---

# 18. `clear()`

List ke saare items remove karne ke liye:

```python
numbers = [10, 20, 30]

numbers.clear()

print(numbers)
```

Output:

```text
[]
```

List ab empty hai.

---

# 19. List ki Length

`len()` use karo:

```python
skills = ["Python", "Power BI", "HVAC"]

print(len(skills))
```

Output:

```text
3
```

---

# 20. List mein Search — `in`

Check karo item exist karta hai ya nahi:

```python
skills = ["Python", "Power BI", "HVAC"]

print("Python" in skills)
```

Output:

```text
True
```

```python
print("Java" in skills)
```

Output:

```text
False
```

---

# 21. `not in`

```python
skills = ["Python", "Power BI", "HVAC"]

print("Java" not in skills)
```

Output:

```text
True
```

---

# 22. List ko Loop Karna

List ko iterate karne ke liye `for` loop use karte hain.

```python
skills = ["Python", "Power BI", "HVAC"]

for skill in skills:
    print(skill)
```

Output:

```text
Python
Power BI
HVAC
```

Yahan loop ek-ek item ko `skill` variable mein rakhta hai.

---

# 23. List with Numbers

```python
numbers = [10, 20, 30, 40]

for number in numbers:
    print(number)
```

Output:

```text
10
20
30
40
```

---

# 24. List mein Different Data Types

Python List mein different types ke items bhi ho sakte hain.

```python
data = ["Muhammad", 25, 60.5, True]
```

Yahan:

```text
"Muhammad" → str
25         → int
60.5       → float
True       → bool
```

Ye technically valid hai.

Lekin practical applications mein List ko logically consistent rakhna aksar easier hota hai.

---

# 25. Nested List

List ke andar List bhi ho sakti hai.

```python
data = [
    ["Muhammad", 25],
    ["Ali", 30],
    ["Ahmed", 28]
]
```

Ye **nested list** hai.

Access:

```python
print(data[0])
```

Output:

```text
['Muhammad', 25]
```

Specific value:

```python
print(data[0][0])
```

Output:

```text
Muhammad
```

Yahan:

```text
data[0]
↓
first inner list

data[0][0]
↓
first inner list ka first item
```

---

# 26. List of Dictionaries

Real-world data mein ye structure bohat common hai.

```python
employees = [
    {"name": "Muhammad", "age": 25},
    {"name": "Ali", "age": 30},
    {"name": "Ahmed", "age": 28}
]
```

First employee:

```python
print(employees[0])
```

Output:

```text
{'name': 'Muhammad', 'age': 25}
```

First employee ka name:

```python
print(employees[0]["name"])
```

Output:

```text
Muhammad
```

Is tarah:

```text
List
 ↓
Multiple records

Dictionary
 ↓
Record ke fields
```

---

# 27. List Sorting

Numbers ko sort karne ke liye:

```python
numbers = [40, 10, 30, 20]

numbers.sort()

print(numbers)
```

Output:

```text
[10, 20, 30, 40]
```

Default ascending order hota hai.

---

# 28. Descending Sort

```python
numbers = [40, 10, 30, 20]

numbers.sort(reverse=True)

print(numbers)
```

Output:

```text
[40, 30, 20, 10]
```

---

# 29. `sorted()` vs `sort()`

`sort()` original List ko modify karta hai:

```python
numbers = [30, 10, 20]

numbers.sort()

print(numbers)
```

List change ho gayi.

`sorted()` ek new sorted List return karta hai:

```python
numbers = [30, 10, 20]

new_numbers = sorted(numbers)

print(numbers)
print(new_numbers)
```

Conceptually:

```text
numbers
→ [30, 10, 20]

new_numbers
→ [10, 20, 30]
```

Original List preserve reh sakti hai.

---

# 30. `count()`

List mein kisi value ki occurrences count karne ke liye:

```python
numbers = [10, 20, 10, 30, 10]

print(numbers.count(10))
```

Output:

```text
3
```

---

# 31. `index()`

Value ki first matching position find karne ke liye:

```python
skills = ["Python", "Power BI", "HVAC"]

print(skills.index("Power BI"))
```

Output:

```text
1
```

Agar value nahi milti, `index()` error de sakta hai.

---

# 32. List Copy

List copy karte waqt ek important concept hai.

```python
numbers = [10, 20, 30]

copy_numbers = numbers.copy()

print(copy_numbers)
```

Output:

```text
[10, 20, 30]
```

Ab `copy_numbers` separate List object hai.

---

# 33. Simple Assignment vs Copy

Ye:

```python
numbers = [10, 20, 30]

other = numbers
```

traditional independent copy nahi banata.

Dono same List object ko reference kar sakte hain.

Example:

```python
numbers = [10, 20, 30]

other = numbers

other[0] = 100

print(numbers)
```

Output:

```text
[100, 20, 30]
```

`other` mein change karne se `numbers` bhi affect hua.

Independent copy ke liye:

```python
other = numbers.copy()
```

---

# 34. List Concatenation

Do Lists ko `+` se combine kar sakte ho:

```python
a = [1, 2, 3]
b = [4, 5, 6]

result = a + b

print(result)
```

Output:

```text
[1, 2, 3, 4, 5, 6]
```

---

# 35. List Repetition

`*` se List repeat kar sakte ho:

```python
numbers = [1, 2]

print(numbers * 3)
```

Output:

```text
[1, 2, 1, 2, 1, 2]
```

---

# 36. List Comprehension — Basic Introduction

Python mein List create karne ka ek powerful short syntax hai:

**List Comprehension**

Example:

```python
numbers = [1, 2, 3, 4, 5]

squares = [number ** 2 for number in numbers]

print(squares)
```

Output:

```text
[1, 4, 9, 16, 25]
```

Iska basic structure:

```text
[expression for item in collection]
```

Is concept ko later detail mein practice karna useful hoga.

---

# 37. Practical Example — Equipment IDs

Suppose:

```python
equipment_ids = [
    "MEP-KHN-REF04",
    "MEP-KHN-REF45",
    "MEP-KHN-REF44"
]
```

Total equipment:

```python
print(len(equipment_ids))
```

Output:

```text
3
```

Check:

```python
print("MEP-KHN-REF45" in equipment_ids)
```

Output:

```text
True
```

Loop:

```python
for equipment_id in equipment_ids:
    print(equipment_id)
```

---

# 38. Practical Example — Work Orders

```python
work_orders = [
    "WO-1001",
    "WO-1002",
    "WO-1003"
]
```

New work order:

```python
work_orders.append("WO-1004")
```

Check:

```python
print(work_orders)
```

Output:

```text
['WO-1001', 'WO-1002', 'WO-1003', 'WO-1004']
```

Agar `WO-1002` complete/remove karna ho:

```python
work_orders.remove("WO-1002")
```

---

# 39. List vs Set

Ye difference important hai:

| Feature        | List    | Set         |
| -------------- | ------- | ----------- |
| Syntax         | `[]`    | `{}`        |
| Ordered        | Yes     | No          |
| Duplicate      | Allowed | Not allowed |
| Indexing       | Yes     | No          |
| Mutable        | Yes     | Yes         |
| Slicing        | Yes     | No          |
| Set operations | No      | Yes         |

Example:

```python
data = [10, 20, 20, 30]
```

duplicates remain:

```text
[10, 20, 20, 30]
```

Set:

```python
data = {10, 20, 20, 30}
```

duplicates remove:

```text
{10, 20, 30}
```

---

# 40. List vs Tuple

| Feature   | List    | Tuple   |
| --------- | ------- | ------- |
| Syntax    | `[]`    | `()`    |
| Ordered   | Yes     | Yes     |
| Duplicate | Allowed | Allowed |
| Indexing  | Yes     | Yes     |
| Mutable   | Yes     | No      |
| Slicing   | Yes     | Yes     |

Main difference:

```text
List
↓
Mutable

Tuple
↓
Immutable
```

---

# 41. Important List Methods

Ye methods yaad rakhna useful hai:

```text
append()
insert()
extend()
remove()
pop()
clear()
sort()
reverse()
count()
index()
copy()
```

---

# Practice Exercises

## Exercise 1

Create:

```python
skills = ["Python", "Power BI", "HVAC"]
```

First aur last item print karo.

---

## Exercise 2

Is List mein `"CNC"` add karo:

```python
skills = ["Python", "Power BI"]
```

---

## Exercise 3

Value `"HVAC"` remove karo:

```python
skills = ["Python", "Power BI", "HVAC"]
```

---

## Exercise 4

List ko reverse order mein karo:

```python
numbers = [10, 20, 30, 40]
```

Hint:

```python
numbers.reverse()
```

---

## Exercise 5

Find karo `30` ka index:

```python
numbers = [10, 20, 30, 40]
```

---

## Exercise 6

Duplicates ko remove karne ke liye:

```python
numbers = [10, 20, 20, 30, 30, 40]
```

Hint:

```python
set(numbers)
```

---

## Exercise 7

Nested List se `"Muhammad"` print karo:

```python
employees = [
    ["Muhammad", 25],
    ["Ali", 30]
]
```

Hint:

```python
employees[0][0]
```

---

# Quick Revision

### Create:

```python
numbers = [10, 20, 30]
```

### Index:

```python
numbers[0]
```

### Last:

```python
numbers[-1]
```

### Slice:

```python
numbers[0:2]
```

### Change:

```python
numbers[0] = 100
```

### Add:

```python
numbers.append(40)
```

### Insert:

```python
numbers.insert(1, 15)
```

### Multiple add:

```python
numbers.extend([50, 60])
```

### Remove by value:

```python
numbers.remove(20)
```

### Remove by index:

```python
numbers.pop(1)
```

### Length:

```python
len(numbers)
```

### Search:

```python
20 in numbers
```

### Sort:

```python
numbers.sort()
```

### Reverse:

```python
numbers.reverse()
```

### Loop:

```python
for number in numbers:
    print(number)
```

---

# Sabse Important Concept

List ko is tarah yaad rakho:

```text
List
 ↓
Multiple values
 ↓
Ordered
 ↓
Index available
 ↓
Duplicates allowed
 ↓
Mutable
```

Example:

```python
equipment = [
    "REF04",
    "REF45",
    "REF44"
]
```

Aap:

```python
equipment[0]
```

se item access kar sakte ho,

```python
equipment.append("REF50")
```

se add kar sakte ho,

```python
equipment.remove("REF45")
```

se remove kar sakte ho,

aur:

```python
for item in equipment:
    print(item)
```

se har item par loop chala sakte ho.

**Next: Section 2.5 — Dictionary Data Type.**
# Chapter 2: Python Data Types

## Section 2.5 — Dictionary Data Type

## 1. Dictionary kya hai?

Python mein **Dictionary** ek collection data type hai jo data ko **key-value pairs** ki form mein store karta hai.

Example:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "department": "Maintenance"
}
```

Yahan:

```text
"name"       → key
"Muhammad"   → value

"age"        → key
25           → value

"department" → key
"Maintenance"→ value
```

Simple concept:

```text
Dictionary
    ↓
Key → Value
```

---

# 2. Dictionary ka Syntax

Dictionary curly brackets `{}` use karta hai:

```python
person = {
    "name": "Ali",
    "age": 30
}
```

General syntax:

```python
{
    key: value,
    key: value
}
```

Har key aur value ke beech:

```text
:
```

colon use hota hai.

---

# 3. Dictionary ka Type

`type()` se check kar sakte ho:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

print(type(employee))
```

Output:

```text
<class 'dict'>
```

`dict` ka matlab Dictionary hai.

---

# 4. Key kya hoti hai?

Key ek **identifier/name** hoti hai jiske through value ko access karte hain.

Example:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}
```

Yahan:

```text
"name" → key
"age"  → key
```

Values:

```text
"Muhammad" → value
25         → value
```

---

# 5. Value kya hoti hai?

Value actual data hota hai.

Example:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}
```

`"Muhammad"` name ki value hai.

`25` age ki value hai.

---

# 6. Dictionary se Value Access Karna

Sabse common method:

```python
dictionary[key]
```

Example:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

print(employee["name"])
```

Output:

```text
Muhammad
```

Age:

```python
print(employee["age"])
```

Output:

```text
25
```

---

# 7. Dictionary mein Indexing nahi hoti

List mein:

```python
numbers = [10, 20, 30]

print(numbers[0])
```

Yahan index `0` use hua.

Dictionary mein normally index ki jagah **key** use hoti hai:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

print(employee["name"])
```

Isliye:

```text
List
↓
Index

Dictionary
↓
Key
```

---

# 8. Dictionary Mutable Hoti Hai

Dictionary **mutable** hai.

Matlab create hone ke baad values change kar sakte ho.

Example:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

employee["age"] = 26

print(employee)
```

Output:

```text
{'name': 'Muhammad', 'age': 26}
```

---

# 9. Dictionary mein New Key Add Karna

Agar key pehle exist nahi karti, assignment se new key create ho jati hai.

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

employee["department"] = "Maintenance"

print(employee)
```

Output:

```text
{
    'name': 'Muhammad',
    'age': 25,
    'department': 'Maintenance'
}
```

Yani:

```python
employee["department"] = "Maintenance"
```

ne new key-value pair add kar diya.

---

# 10. Existing Value Change Karna

Agar key already exist karti hai, assignment value ko update karta hai.

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

employee["age"] = 26
```

Yahan new key nahi bani.

Existing `"age"` ki value change hui.

---

# 11. `len()` with Dictionary

Dictionary mein kitne key-value pairs hain:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "department": "Maintenance"
}

print(len(employee))
```

Output:

```text
3
```

Yahan 3 keys hain.

---

# 12. Check Key — `in`

Check karne ke liye ke key exist karti hai:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

print("name" in employee)
```

Output:

```text
True
```

```python
print("salary" in employee)
```

Output:

```text
False
```

Important:

```python
"name" in employee
```

normally **keys** check karta hai, values nahi.

---

# 13. `not in`

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

print("salary" not in employee)
```

Output:

```text
True
```

---

# 14. `get()` Method

Dictionary se value safely retrieve karne ke liye `get()` bohat useful hai.

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

print(employee.get("name"))
```

Output:

```text
Muhammad
```

---

# 15. `[]` vs `get()`

Ye important difference hai.

Agar key exist karti hai:

```python
employee["name"]
```

aur:

```python
employee.get("name")
```

dono value return karenge.

Lekin agar key exist nahi karti:

```python
employee = {
    "name": "Muhammad"
}

print(employee["salary"])
```

To `KeyError` aa sakta hai.

Lekin:

```python
print(employee.get("salary"))
```

Output:

```text
None
```

Isliye uncertain/missing keys ke liye `get()` useful hai.

---

# 16. `get()` mein Default Value

Aap default value bhi de sakte ho:

```python
employee = {
    "name": "Muhammad"
}

salary = employee.get("salary", 0)

print(salary)
```

Output:

```text
0
```

Matlab:

```text
salary key hai
↓
value return karo

salary key nahi hai
↓
0 return karo
```

Data processing mein ye bohat useful hai.

---

# 17. Dictionary se Item Remove — `pop()`

Specific key remove karne ke liye:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "department": "Maintenance"
}

employee.pop("age")

print(employee)
```

Output:

```text
{'name': 'Muhammad', 'department': 'Maintenance'}
```

---

# 18. `del`

Key delete karne ke liye `del` bhi use kar sakte ho:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

del employee["age"]

print(employee)
```

Output:

```text
{'name': 'Muhammad'}
```

---

# 19. `clear()`

Dictionary ke saare items remove:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

employee.clear()

print(employee)
```

Output:

```text
{}
```

Dictionary empty ho gayi.

---

# 20. `keys()`

Dictionary ki keys dekhne ke liye:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "department": "Maintenance"
}

print(employee.keys())
```

Output approximately:

```text
dict_keys(['name', 'age', 'department'])
```

---

# 21. `values()`

Sirf values:

```python
print(employee.values())
```

Output:

```text
dict_values(['Muhammad', 25, 'Maintenance'])
```

---

# 22. `items()`

Key aur value dono ek saath:

```python
print(employee.items())
```

Output approximately:

```text
dict_items([
    ('name', 'Muhammad'),
    ('age', 25),
    ('department', 'Maintenance')
])
```

---

# 23. Dictionary ke Through Loop

Keys par loop:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "department": "Maintenance"
}

for key in employee:
    print(key)
```

Output:

```text
name
age
department
```

---

# 24. Values par Loop

```python
for value in employee.values():
    print(value)
```

Output:

```text
Muhammad
25
Maintenance
```

---

# 25. Key aur Value Dono par Loop

Sabse useful pattern:

```python
for key, value in employee.items():
    print(key, ":", value)
```

Output:

```text
name : Muhammad
age : 25
department : Maintenance
```

Is pattern ko yaad rakhna useful hai:

```python
for key, value in dictionary.items():
    ...
```

---

# 26. Duplicate Keys

Dictionary mein same key ko repeatedly rakhna useful nahi hota.

Example:

```python
data = {
    "name": "Ali",
    "name": "Ahmed"
}
```

Final value effectively last assignment wali hogi:

```text
Ahmed
```

Isliye Dictionary mein keys **unique** honi chahiye.

---

# 27. Dictionary Keys

Commonly keys ke liye strings use hoti hain:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}
```

Numbers bhi key ho sakte hain:

```python
data = {
    1: "Apple",
    2: "Banana",
    3: "Orange"
}
```

Access:

```python
print(data[1])
```

Output:

```text
Apple
```

---

# 28. Dictionary Values Different Types ki Ho Sakti Hain

Example:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "salary": 5000.50,
    "active": True
}
```

Values:

```text
str
int
float
bool
```

sab ho sakti hain.

---

# 29. Dictionary ke Andar List

Ye real-world programming mein bohat common hai.

```python
employee = {
    "name": "Muhammad",
    "skills": ["Python", "Power BI", "HVAC"]
}
```

Skills access:

```python
print(employee["skills"])
```

Output:

```text
['Python', 'Power BI', 'HVAC']
```

First skill:

```python
print(employee["skills"][0])
```

Output:

```text
Python
```

Yahan do levels hain:

```text
employee
   ↓
"skills"
   ↓
List
   ↓
index [0]
```

---

# 30. Dictionary ke Andar Dictionary

Dictionary nested bhi ho sakti hai.

```python
company = {
    "employee": {
        "name": "Muhammad",
        "age": 25
    }
}
```

Name access:

```python
print(company["employee"]["name"])
```

Output:

```text
Muhammad
```

---

# 31. Practical Equipment Example

Facility/equipment data ko Dictionary mein represent karna:

```python
equipment = {
    "equipment_id": "MEP-KHN-REF04",
    "description": "Refrigerator",
    "area": "Kitchen",
    "floor": "Thirty Four Floor"
}
```

Equipment ID:

```python
print(equipment["equipment_id"])
```

Output:

```text
MEP-KHN-REF04
```

Description:

```python
print(equipment["description"])
```

Output:

```text
Refrigerator
```

---

# 32. Equipment Data Update

Agar equipment floor change ho:

```python
equipment["floor"] = "Thirty Five Floor"
```

New value:

```python
print(equipment["floor"])
```

Output:

```text
Thirty Five Floor
```

---

# 33. Multiple Equipment Records

Real-world mein ek equipment ki jagah multiple equipment honge.

Iske liye:

**List of Dictionaries**

bohat useful structure hai.

```python
equipment_list = [
    {
        "equipment_id": "MEP-KHN-REF04",
        "description": "Refrigerator",
        "area": "Kitchen"
    },
    {
        "equipment_id": "MEP-KHN-REF45",
        "description": "Refrigerator",
        "area": "Food Preparation Area"
    },
    {
        "equipment_id": "MEP-KHN-REF44",
        "description": "Refrigerator",
        "area": "VIP Pantry"
    }
]
```

Ye structure data processing mein bohat common hai.

---

# 34. First Equipment Access

```python
print(equipment_list[0])
```

First Dictionary milegi.

Specific equipment ID:

```python
print(equipment_list[0]["equipment_id"])
```

Output:

```text
MEP-KHN-REF04
```

---

# 35. Multiple Equipment par Loop

```python
for equipment in equipment_list:
    print(equipment["equipment_id"])
```

Output:

```text
MEP-KHN-REF04
MEP-KHN-REF45
MEP-KHN-REF44
```

Ye pattern bohat important hai:

```python
for equipment in equipment_list:
    print(equipment["equipment_id"])
```

Matlab:

```text
List
 ↓
one Dictionary
 ↓
Dictionary ki key
 ↓
value
```

---

# 36. Dictionary vs List

| Feature          | List                | Dictionary                     |
| ---------------- | ------------------- | ------------------------------ |
| Syntax           | `[]`                | `{}`                           |
| Data access      | Index               | Key                            |
| Ordered          | Yes                 | Yes, insertion order preserved |
| Mutable          | Yes                 | Yes                            |
| Duplicate values | Allowed             | Allowed                        |
| Unique keys      | N/A                 | Yes                            |
| Best use         | Collection of items | Named/structured data          |

Example List:

```python
skills = ["Python", "Power BI", "HVAC"]
```

Example Dictionary:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "department": "Maintenance"
}
```

---

# 37. Dictionary vs Set

Dono curly braces use karte hain, lekin structure different hai.

Set:

```python
skills = {"Python", "Power BI", "HVAC"}
```

Dictionary:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}
```

Difference:

```text
Set
↓
value, value, value

Dictionary
↓
key: value
key: value
```

Important:

```python
{}
```

empty Dictionary hoti hai.

Empty Set:

```python
set()
```

---

# 38. Real-World JSON Connection

Python Dictionary ka JSON ke saath strong relationship hai.

Example Python:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "active": True
}
```

JSON mein similar structure:

```json
{
    "name": "Muhammad",
    "age": 25,
    "active": true
}
```

APIs se data receive karte waqt aapko frequently Dictionary/List structures milenge.

---

# 39. Important Dictionary Methods

Ye methods yaad rakhna:

```text
get()
keys()
values()
items()
pop()
clear()
update()
```

Aur operations:

```text
dictionary[key]
dictionary[key] = value
key in dictionary
```

---

# 40. `update()`

Existing Dictionary mein multiple values update/add karne ke liye:

```python
employee = {
    "name": "Muhammad",
    "age": 25
}

employee.update({
    "age": 26,
    "department": "Maintenance"
})

print(employee)
```

Result:

```text
{
    'name': 'Muhammad',
    'age': 26,
    'department': 'Maintenance'
}
```

Yahan `"age"` update hua aur `"department"` add hua.

---

# Practice Exercises

## Exercise 1

Ye Dictionary create karo:

```python
student = {
    "name": "Ali",
    "age": 22,
    "course": "Python"
}
```

`name` print karo.

---

## Exercise 2

`student` ki age `23` kar do.

---

## Exercise 3

Is Dictionary mein `"city": "Riyadh"` add karo.

---

## Exercise 4

Check karo `"course"` key exist karti hai ya nahi.

Hint:

```python
"course" in student
```

---

## Exercise 5

`get()` use karke `"salary"` retrieve karo. Agar key missing ho to `0` return hona chahiye.

Hint:

```python
student.get("salary", 0)
```

---

## Exercise 6

Ye equipment Dictionary banao:

```python
equipment = {
    "id": "MEP-KHN-REF04",
    "type": "Refrigerator",
    "floor": "34"
}
```

Phir:

1. ID print karo
2. floor change karke `"35"` karo
3. `"area"` add karo
4. `for` loop se key/value print karo

---

# Final Concept

Dictionary ko simple formula se yaad rakho:

```text
Dictionary
     ↓
Key → Value
```

Example:

```python
employee = {
    "name": "Muhammad",
    "age": 25,
    "department": "Maintenance"
}
```

Access:

```python
employee["name"]
```

Add:

```python
employee["salary"] = 5000
```

Update:

```python
employee["age"] = 26
```

Safe access:

```python
employee.get("salary")
```

Remove:

```python
employee.pop("age")
```

Loop:

```python
for key, value in employee.items():
    print(key, value)
```

Sabse important difference:

```text
List
↓
Index se data access

Dictionary
↓
Key se data access
```

Aur real-world structured data mein:

```text
List of Dictionaries
        ↓
multiple records
        ↓
har record = Dictionary
```

Example:

```python
employees = [
    {"name": "Muhammad", "age": 25},
    {"name": "Ali", "age": 30}
]
```

Ye structure Python mein data processing, APIs, JSON aur automation mein bohat frequently milega.

**Next: Section 2.6 — Tuple Data Type.**
# Chapter 2: Python Data Types

## Section 2.6 — Tuple Data Type

## 1. Tuple kya hai?

**Tuple** Python ka ek collection data type hai jo multiple values ko ek sequence mein store karta hai.

Example:

```python
coordinates = (10, 20, 30)
```

Tuple ki important properties:

```text
Tuple
 ↓
Ordered
 ↓
Index-based
 ↓
Duplicates allowed
 ↓
Immutable
```

Sabse important:

> **Tuple ko create karne ke baad uske existing items ko directly change nahi kar sakte.**

---

# 2. Tuple ka Syntax

Tuple normally parentheses `()` se create hoti hai.

```python
numbers = (10, 20, 30)
```

Strings:

```python
skills = ("Python", "Power BI", "HVAC")
```

Mixed values:

```python
data = ("Muhammad", 25, True)
```

---

# 3. Tuple ka Type

`type()` se check:

```python
numbers = (10, 20, 30)

print(type(numbers))
```

Output:

```text
<class 'tuple'>
```

---

# 4. Tuple Ordered Hoti Hai

Tuple mein items ka order preserve hota hai.

```python
skills = ("Python", "Power BI", "HVAC")
```

Order:

```text
Python
Power BI
HVAC
```

Isliye indexing possible hai.

---

# 5. Tuple Indexing

Python mein index `0` se start hota hai.

```python
skills = ("Python", "Power BI", "HVAC")
```

```python
print(skills[0])
```

Output:

```text
Python
```

```python
print(skills[1])
```

Output:

```text
Power BI
```

```python
print(skills[2])
```

Output:

```text
HVAC
```

---

# 6. Negative Indexing

Tuple mein negative indexing bhi hoti hai.

```python
skills = ("Python", "Power BI", "HVAC")
```

Last item:

```python
print(skills[-1])
```

Output:

```text
HVAC
```

Second-last:

```python
print(skills[-2])
```

Output:

```text
Power BI
```

---

# 7. Tuple Slicing

Tuple mein slicing bhi possible hai.

```python
numbers = (10, 20, 30, 40, 50)

print(numbers[1:4])
```

Output:

```text
(20, 30, 40)
```

Same slicing rule:

> `end` index include nahi hota.

---

# 8. Tuple Immutable Hoti Hai

Ye Tuple ka **sabse important concept** hai.

Immutable ka matlab:

> Create hone ke baad Tuple ke existing elements ko change nahi kar sakte.

Example:

```python
numbers = (10, 20, 30)

numbers[0] = 100
```

Ye error dega:

```text
TypeError
```

Kyun?

Kyun ke Tuple immutable hai.

Compare:

```python
numbers = [10, 20, 30]

numbers[0] = 100
```

List mein ye allowed hai.

Lekin:

```python
numbers = (10, 20, 30)

numbers[0] = 100
```

Tuple mein allowed nahi.

---

# 9. List vs Tuple

Ye difference achi tarah samajhna zaroori hai.

### List

```python
numbers = [10, 20, 30]
```

Mutable:

```python
numbers[0] = 100
```

Allowed.

### Tuple

```python
numbers = (10, 20, 30)
```

Immutable:

```python
numbers[0] = 100
```

Not allowed.

Simple rule:

```text
List
↓
Change kar sakte ho

Tuple
↓
Existing items change nahi kar sakte
```

---

# 10. Empty Tuple

Empty Tuple:

```python
data = ()
```

Check:

```python
print(type(data))
```

Output:

```text
<class 'tuple'>
```

---

# 11. Single-Item Tuple

Yahan beginner mistake bohat common hai.

Ye:

```python
data = ("Python")
```

Tuple nahi hai.

Ye actually `str` hai:

```python
print(type(data))
```

Output:

```text
<class 'str'>
```

Single-item Tuple ke liye **comma** zaroori hai:

```python
data = ("Python",)
```

Ab:

```python
print(type(data))
```

Output:

```text
<class 'tuple'>
```

Important rule:

```text
("Python")
↓
String

("Python",)
↓
Tuple
```

Yahan comma important hai.

---

# 12. Tuple Packing

Multiple values ko automatically Tuple mein pack kar sakte ho:

```python
data = 10, 20, 30
```

Python isko Tuple samajhta hai:

```python
print(data)
```

Output:

```text
(10, 20, 30)
```

Type:

```python
print(type(data))
```

Output:

```text
<class 'tuple'>
```

Parentheses technically har situation mein required nahi hain.

Lekin beginner code mein parentheses use karna readability ke liye better hai:

```python
data = (10, 20, 30)
```

---

# 13. Tuple Unpacking

Tuple ke values ko multiple variables mein assign kar sakte ho.

```python
data = ("Muhammad", 25, "Maintenance")

name, age, department = data

print(name)
print(age)
print(department)
```

Output:

```text
Muhammad
25
Maintenance
```

Yahan:

```text
data
 ↓
("Muhammad", 25, "Maintenance")

name
 ↓
"Muhammad"

age
 ↓
25

department
 ↓
"Maintenance"
```

Isko **Tuple Unpacking** kehte hain.

---

# 14. Unpacking mein Number Match Hona Chahiye

Example:

```python
data = (10, 20, 30)

a, b, c = data
```

Correct.

Lekin:

```python
a, b = data
```

Error aayega, kyun ke 3 values hain lekin variables 2.

Isi tarah:

```python
a, b, c, d = data
```

bhi error dega.

Basic rule:

```text
Number of values
=
Number of variables
```

---

# 15. `len()` with Tuple

Tuple ke items count karne ke liye:

```python
skills = ("Python", "Power BI", "HVAC")

print(len(skills))
```

Output:

```text
3
```

---

# 16. `in` Operator

Check karo item exist karta hai:

```python
skills = ("Python", "Power BI", "HVAC")

print("Python" in skills)
```

Output:

```text
True
```

```python
print("Java" in skills)
```

Output:

```text
False
```

---

# 17. `not in`

```python
skills = ("Python", "Power BI", "HVAC")

print("Java" not in skills)
```

Output:

```text
True
```

---

# 18. Tuple mein Duplicates Allowed Hain

Tuple duplicate values rakh sakti hai.

```python
numbers = (10, 20, 20, 30, 30)
```

Ye valid hai.

Check:

```python
print(numbers)
```

Output:

```text
(10, 20, 20, 30, 30)
```

---

# 19. `count()`

Tuple mein kisi value ki occurrences count karne ke liye:

```python
numbers = (10, 20, 20, 30, 20)

print(numbers.count(20))
```

Output:

```text
3
```

---

# 20. `index()`

Value ka first index:

```python
numbers = (10, 20, 30, 40)

print(numbers.index(30))
```

Output:

```text
2
```

---

# 21. Tuple mein `append()` nahi hota

List:

```python
numbers = [10, 20, 30]

numbers.append(40)
```

Allowed.

Tuple:

```python
numbers = (10, 20, 30)

numbers.append(40)
```

Error aayega.

Kyun?

Kyun ke Tuple immutable hai.

Isi tarah Tuple mein normally:

```text
append()
insert()
remove()
pop()
clear()
```

jaise List mutation methods nahi hote.

---

# 22. Tuple ko Loop Karna

Tuple ko `for` loop se iterate kar sakte ho.

```python
skills = ("Python", "Power BI", "HVAC")

for skill in skills:
    print(skill)
```

Output:

```text
Python
Power BI
HVAC
```

---

# 23. Tuple Concatenation

Do Tuples ko `+` se combine kar sakte ho.

```python
a = (1, 2, 3)
b = (4, 5, 6)

result = a + b

print(result)
```

Output:

```text
(1, 2, 3, 4, 5, 6)
```

Yahan original Tuples modify nahi huin; ek new Tuple bani.

---

# 24. Tuple Repetition

`*` use karke Tuple repeat:

```python
numbers = (1, 2)

print(numbers * 3)
```

Output:

```text
(1, 2, 1, 2, 1, 2)
```

---

# 25. Tuple ke Andar List

Ek interesting point:

Tuple immutable hai, lekin uske andar agar **mutable object** ho, to us object ko modify kiya ja sakta hai.

Example:

```python
data = ("Muhammad", [10, 20, 30])
```

Tuple ka second item ek List hai.

Aap ye nahi kar sakte:

```python
data[0] = "Ali"
```

Lekin List ke andar change kar sakte ho:

```python
data[1].append(40)
```

Ab:

```python
print(data)
```

Output:

```text
('Muhammad', [10, 20, 30, 40])
```

Yahan Tuple ka reference structure change nahi hua; andar wali List mutate hui.

Beginner level par is rule ko yaad rakho:

> **Tuple khud immutable hai, lekin uske andar mutable object ho to woh object apne rules ke mutabiq change ho sakta hai.**

---

# 26. Practical Example — Location

Suppose equipment ki location fixed hai:

```python
location = ("Riyadh", "Saudi Arabia")
```

Access:

```python
print(location[0])
```

Output:

```text
Riyadh
```

```python
print(location[1])
```

Output:

```text
Saudi Arabia
```

Agar ye data logically fixed hai, Tuple useful ho sakti hai.

---

# 27. Practical Equipment Example

```python
equipment = {
    "id": "MEP-KHN-REF04",
    "location": ("Kitchen", "Thirty Four Floor")
}
```

Yahan Dictionary equipment ki properties store kar rahi hai aur Tuple location ke fixed components store kar rahi hai.

Access:

```python
print(equipment["location"])
```

Output:

```text
("Kitchen", "Thirty Four Floor")
```

Floor:

```python
print(equipment["location"][1])
```

Output:

```text
Thirty Four Floor
```

Structure:

```text
Dictionary
   ↓
"location"
   ↓
Tuple
   ↓
index [1]
```

---

# 28. Tuple vs List vs Set vs Dictionary

Ab Chapter 2 ke collection types ko compare karte hain:

| Feature    | List                  | Tuple            | Set           | Dictionary     |
| ---------- | --------------------- | ---------------- | ------------- | -------------- |
| Syntax     | `[]`                  | `()`             | `{}`          | `{key: value}` |
| Ordered    | Yes                   | Yes              | No indexing   | Yes            |
| Mutable    | Yes                   | No               | Yes           | Yes            |
| Duplicates | Allowed               | Allowed          | No            | Keys unique    |
| Indexing   | Yes                   | Yes              | No            | Key-based      |
| Main use   | Changeable collection | Fixed collection | Unique values | Key-value data |

---

# 29. Kab List Use Karein?

Jab data ko change karna ho:

```python
work_orders = [
    "WO-1001",
    "WO-1002",
    "WO-1003"
]
```

New work order add:

```python
work_orders.append("WO-1004")
```

List suitable hai.

---

# 30. Kab Tuple Use Karein?

Jab values ko sequence ki form mein rakhna ho aur normally unko change nahi karna.

Example:

```python
coordinates = (24.7136, 46.6753)
```

Ya:

```python
dimensions = (100, 200, 50)
```

Ya:

```python
location = ("Kitchen", "34th Floor")
```

---

# 31. Kab Set Use Karein?

Jab uniqueness important ho.

Example:

```python
equipment_types = {
    "Refrigerator",
    "AHU",
    "VAV",
    "Pump"
}
```

Duplicate automatically remove ho jata hai.

---

# 32. Kab Dictionary Use Karein?

Jab data fields ke naam ke saath store karna ho.

Example:

```python
equipment = {
    "id": "MEP-KHN-REF04",
    "type": "Refrigerator",
    "area": "Kitchen",
    "floor": "34"
}
```

Yahan Dictionary best structure hai because har value ka clear field name hai.

---

# 33. Quick Decision Rule

Isko yaad kar lo:

```text
Multiple changeable items?
        ↓
      List

Fixed sequence?
        ↓
      Tuple

Unique values?
        ↓
       Set

Key → Value data?
        ↓
   Dictionary
```

---

# 34. Important Tuple Functions/Methods

Commonly useful:

```text
len()
in
not in
count()
index()
```

Aur indexing/slicing:

```python
data[0]
data[-1]
data[1:3]
```

---

# Practice Exercises

## Exercise 1

Ye Tuple create karo:

```python
skills = ("Python", "Power BI", "HVAC")
```

First aur last skill print karo.

---

## Exercise 2

Check karo `"Python"` Tuple mein hai ya nahi.

---

## Exercise 3

Tuple ki length find karo:

```python
numbers = (10, 20, 30, 40, 50)
```

---

## Exercise 4

`20` kitni baar hai?

```python
numbers = (10, 20, 20, 30, 20)
```

---

## Exercise 5

`30` ka index find karo:

```python
numbers = (10, 20, 30, 40)
```

---

## Exercise 6 — Unpacking

```python
employee = ("Muhammad", 25, "Maintenance")
```

Isko:

```text
name
age
department
```

mein unpack karo.

---

## Exercise 7 — Important

Ye code dekho:

```python
data = ("Python")
```

Iska type kya hoga?

Aur:

```python
data = ("Python",)
```

iska type kya hoga?

---

# Chapter 2 Complete Revision

Ab humne Chapter 2 mein ye 6 data types cover kiye:

```text
2.1 String
2.2 Set
2.3 Numbers
2.4 List
2.5 Dictionary
2.6 Tuple
```

## String

```python
name = "Muhammad"
```

Characters/text ke liye.

## Set

```python
skills = {"Python", "HVAC", "Power BI"}
```

Unique values ke liye.

## Numbers

```python
age = 25
temperature = 24.5
```

Numeric calculations ke liye.

## List

```python
skills = ["Python", "HVAC", "Power BI"]
```

Changeable ordered collection ke liye.

## Dictionary

```python
employee = {
    "name": "Muhammad",
    "age": 25
}
```

Key-value structured data ke liye.

## Tuple

```python
location = ("Riyadh", "Saudi Arabia")
```

Fixed/
