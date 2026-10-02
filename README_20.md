# Chapter 20: List

Python mein `list` ek **ordered, mutable collection** hai.

Example:

```python
equipment = ["AHU-001", "AHU-002", "VAV-001"]
```

List ki important properties:

* Ordered hoti hai
* Indexing support karti hai
* Mutable hoti hai
* Duplicate values allow karti hai
* Different data types rakh sakti hai

```python
data = ["AHU-001", 10, 22.5, True]
```

---

# Section 20.1: List Methods and Supported Operators

List ke bohat saare built-in methods hain.

## `append()`

End mein **one item** add karta hai.

```python
equipment = ["AHU-001", "AHU-002"]

equipment.append("AHU-003")

print(equipment)
```

Output:

```text
['AHU-001', 'AHU-002', 'AHU-003']
```

Important:

```python
equipment.append(["VAV-001", "VAV-002"])
```

ye dono items separately add nahi karega.

Result:

```text
['AHU-001', 'AHU-002', ['VAV-001', 'VAV-002']]
```

---

## `extend()`

Multiple items add karne ke liye:

```python
equipment = ["AHU-001", "AHU-002"]

equipment.extend(["VAV-001", "VAV-002"])

print(equipment)
```

Output:

```text
['AHU-001', 'AHU-002', 'VAV-001', 'VAV-002']
```

### `append()` vs `extend()`

```python
a = [1, 2]

a.append([3, 4])
```

Result:

```text
[1, 2, [3, 4]]
```

Lekin:

```python
a = [1, 2]

a.extend([3, 4])
```

Result:

```text
[1, 2, 3, 4]
```

---

## `insert()`

Specific index par item insert karta hai.

```python
equipment = ["AHU-001", "AHU-003"]

equipment.insert(1, "AHU-002")

print(equipment)
```

Output:

```text
['AHU-001', 'AHU-002', 'AHU-003']
```

Syntax:

```python
list.insert(index, value)
```

---

## `remove()`

Value ke basis par first matching item remove karta hai.

```python
equipment = ["AHU-001", "AHU-002", "AHU-003"]

equipment.remove("AHU-002")

print(equipment)
```

Output:

```text
['AHU-001', 'AHU-003']
```

Agar value exist nahi karti:

```python
equipment.remove("AHU-999")
```

to:

```text
ValueError
```

---

## `pop()`

`pop()` index se item remove karta hai aur removed item return bhi karta hai.

```python
equipment = ["AHU-001", "AHU-002", "AHU-003"]

removed = equipment.pop(1)

print(removed)
print(equipment)
```

Output:

```text
AHU-002
['AHU-001', 'AHU-003']
```

Without index:

```python
equipment.pop()
```

last item remove karta hai.

---

## `clear()`

Puri list empty:

```python
equipment = ["AHU-001", "AHU-002"]

equipment.clear()

print(equipment)
```

Output:

```text
[]
```

---

## `index()`

Item ka first index find karta hai.

```python
equipment = ["AHU-001", "AHU-002", "AHU-003"]

print(equipment.index("AHU-002"))
```

Output:

```text
1
```

---

## `count()`

Value kitni baar appear hui hai:

```python
statuses = [
    "Running",
    "Stopped",
    "Running",
    "Running"
]

print(statuses.count("Running"))
```

Output:

```text
3
```

---

## `sort()`

List ko ascending order mein sort karta hai.

```python
numbers = [5, 2, 8, 1, 3]

numbers.sort()

print(numbers)
```

Output:

```text
[1, 2, 3, 5, 8]
```

Descending:

```python
numbers.sort(reverse=True)
```

---

## `sorted()`

`sorted()` new list return karta hai.

```python
numbers = [5, 2, 8, 1]

new_numbers = sorted(numbers)

print(numbers)
print(new_numbers)
```

Output:

```text
[5, 2, 8, 1]
[1, 2, 5, 8]
```

Difference:

```text
sort()    → original list modify
sorted()  → new sorted list
```

---

## `reverse()`

List ke elements ka order reverse karta hai.

```python
numbers = [1, 2, 3, 4]

numbers.reverse()

print(numbers)
```

Output:

```text
[4, 3, 2, 1]
```

---

## List operators

### `+`

Lists concatenate:

```python
a = [1, 2]
b = [3, 4]

result = a + b
```

Result:

```text
[1, 2, 3, 4]
```

### `*`

List repetition:

```python
result = [0] * 5
```

Result:

```text
[0, 0, 0, 0, 0]
```

### `in`

```python
"AHU-001" in equipment
```

### `not in`

```python
"AHU-999" not in equipment
```

---

# Section 20.2: Accessing List Values

List indexing **zero-based** hoti hai.

```python
equipment = [
    "AHU-001",
    "AHU-002",
    "AHU-003"
]
```

Indexes:

```text
AHU-001 → 0
AHU-002 → 1
AHU-003 → 2
```

Access:

```python
print(equipment[0])
```

Output:

```text
AHU-001
```

---

## Negative indexing

```python
print(equipment[-1])
```

Output:

```text
AHU-003
```

```text
-1 → last
-2 → second last
```

---

## Slicing

```python
equipment[0:2]
```

Output:

```text
['AHU-001', 'AHU-002']
```

Remember:

```text
start included
stop excluded
```

---

## Step size

```python
numbers = [0, 1, 2, 3, 4, 5]

print(numbers[::2])
```

Output:

```text
[0, 2, 4]
```

Reverse:

```python
print(numbers[::-1])
```

Output:

```text
[5, 4, 3, 2, 1, 0]
```

---

# Section 20.3: Checking if List is Empty

Python mein empty list `False` hoti hai.

```python
equipment = []

if not equipment:
    print("List is empty")
```

Output:

```text
List is empty
```

Ye common aur Pythonic approach hai.

---

## `len()` se bhi check kar sakte hain

```python
if len(equipment) == 0:
    print("List is empty")
```

Dono correct hain.

Lekin generally:

```python
if not equipment:
```

short aur Pythonic hai.

---

## Non-empty list

```python
equipment = ["AHU-001"]

if equipment:
    print("List has data")
```

---

# Section 20.4: Iterating Over a List

Basic `for` loop:

```python
equipment = [
    "AHU-001",
    "AHU-002",
    "VAV-001"
]

for item in equipment:
    print(item)
```

Output:

```text
AHU-001
AHU-002
VAV-001
```

---

## Index ke saath iterate

```python
for index, item in enumerate(equipment):
    print(index, item)
```

Output:

```text
0 AHU-001
1 AHU-002
2 VAV-001
```

---

## `start` parameter

```python
for index, item in enumerate(equipment, start=1):
    print(index, item)
```

Output:

```text
1 AHU-001
2 AHU-002
3 VAV-001
```

---

## List modify karte waqt caution

Ye avoid karna chahiye:

```python
numbers = [1, 2, 3, 4, 5]

for number in numbers:
    if number % 2 == 0:
        numbers.remove(number)
```

Loop ke dauran same list modify karne se unexpected behavior aa sakta hai.

Better:

```python
numbers = [1, 2, 3, 4, 5]

numbers = [
    number
    for number in numbers
    if number % 2 != 0
]
```

Result:

```text
[1, 3, 5]
```

---

# Section 20.5: Checking Whether an Item Is in a List

`in` operator use hota hai.

```python
equipment = [
    "AHU-001",
    "AHU-002",
    "VAV-001"
]

if "AHU-002" in equipment:
    print("Equipment found")
```

Output:

```text
Equipment found
```

---

## `not in`

```python
if "AHU-999" not in equipment:
    print("Equipment not found")
```

---

## String ke saath bhi

```python
if "AHU" in "MEP-AHU-001":
    print("AHU equipment")
```

`in` ka behavior data type ke context par depend karta hai.

List mein:

```python
"AHU-001" in equipment
```

whole element check karta hai.

---

# Section 20.6: Any and All

Python mein:

```python
any()
```

aur:

```python
all()
```

bohat useful built-in functions hain.

---

## `any()`

Agar iterable mein **kam az kam ek truthy value** ho to `True`.

```python
values = [False, False, True, False]

print(any(values))
```

Output:

```text
True
```

Agar sab false:

```python
values = [False, False, False]

print(any(values))
```

Output:

```text
False
```

---

## Practical example

```python
temperatures = [22, 23, 25, 28]

if any(temp > 27 for temp in temperatures):
    print("High temperature detected")
```

Output:

```text
High temperature detected
```

Yahan `any()` check kar raha hai:

> Kya koi bhi temperature 27 se greater hai?

---

## `all()`

`all()` tab `True` return karta hai jab **sab values truthy** hon.

```python
values = [True, True, True]

print(all(values))
```

Output:

```text
True
```

Agar ek bhi false:

```python
values = [True, True, False]

print(all(values))
```

Output:

```text
False
```

---

## Practical HVAC example

```python
temperatures = [22, 23, 24, 25]

if all(temp < 30 for temp in temperatures):
    print("All temperatures are below 30")
```

Output:

```text
All temperatures are below 30
```

---

## Important difference

```text
any() → kam az kam ek condition True
all() → har condition True
```

Example:

```python
numbers = [2, 4, 6, 7]
```

```python
any(n % 2 == 1 for n in numbers)
```

→ `True`

kyun ke `7` odd hai.

Lekin:

```python
all(n % 2 == 0 for n in numbers)
```

→ `False`

kyun ke `7` even nahi hai.

---

# Section 20.7: Reversing List Elements

Method:

```python
numbers = [1, 2, 3, 4]

numbers.reverse()

print(numbers)
```

Output:

```text
[4, 3, 2, 1]
```

---

## Slicing se reverse

```python
numbers = [1, 2, 3, 4]

reversed_numbers = numbers[::-1]
```

Result:

```text
[4, 3, 2, 1]
```

Difference:

```text
reverse() → original list modify
[::-1]    → new list
```

---

## `reversed()`

Python ka built-in:

```python
numbers = [1, 2, 3, 4]

result = reversed(numbers)

print(list(result))
```

Output:

```text
[4, 3, 2, 1]
```

`reversed()` ek iterator return karta hai, is liye commonly:

```python
list(reversed(numbers))
```

use karte hain.

---

# Section 20.8: Concatenate and Merge Lists

Do lists combine karne ke liye `+`:

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

## `extend()`

```python
a = [1, 2, 3]
b = [4, 5, 6]

a.extend(b)

print(a)
```

Output:

```text
[1, 2, 3, 4, 5, 6]
```

Difference:

```text
a + b
```

new list banata hai.

```text
a.extend(b)
```

`a` ko modify karta hai.

---

## Multiple lists

```python
list1 = [1, 2]
list2 = [3, 4]
list3 = [5, 6]

result = list1 + list2 + list3
```

Result:

```text
[1, 2, 3, 4, 5, 6]
```

---

# Section 20.9: Length of a List

`len()` list mein total elements batata hai.

```python
equipment = [
    "AHU-001",
    "AHU-002",
    "VAV-001"
]

print(len(equipment))
```

Output:

```text
3
```

---

## Empty list

```python
data = []

print(len(data))
```

Output:

```text
0
```

---

## Nested list

```python
data = [
    [1, 2],
    [3, 4],
    [5, 6]
]

print(len(data))
```

Output:

```text
3
```

Important:

`len()` outer list ke elements count karega, total inner values nahi.

Total values:

```text
3 rows × 2 values = 6
```

---

# Section 20.10: Remove Duplicate Values in List

List duplicates allow karti hai:

```python
equipment = [
    "AHU-001",
    "AHU-002",
    "AHU-001",
    "VAV-001",
    "AHU-002"
]
```

Duplicates remove karne ka simple method:

```python
unique = list(set(equipment))
```

Lekin `set` order preserve karne ke liye ideal nahi hai.

---

## Order preserve karna

Modern Python mein simple method:

```python
unique = list(dict.fromkeys(equipment))
```

Result:

```text
[
    'AHU-001',
    'AHU-002',
    'VAV-001'
]
```

Original order preserve hota hai.

---

## Manual method

```python
unique = []

for item in equipment:
    if item not in unique:
        unique.append(item)
```

Ye beginner ke liye concept samajhne ke liye useful hai.

---

# Section 20.11: Comparison of Lists

Python lists ko compare kar sakta hai.

```python
a = [1, 2, 3]
b = [1, 2, 3]

print(a == b)
```

Output:

```text
True
```

List comparison **contents aur order** ko consider karti hai.

---

## Order different

```python
a = [1, 2, 3]
b = [3, 2, 1]

print(a == b)
```

Output:

```text
False
```

Values same hain lekin order different hai.

---

## Different values

```python
a = [1, 2, 3]
b = [1, 2, 4]

print(a == b)
```

Output:

```text
False
```

---

## `<`, `>`

Lists lexicographically compare ho sakti hain.

```python
a = [1, 2]
b = [1, 3]

print(a < b)
```

Output:

```text
True
```

Python pehle first elements compare karta hai:

```text
1 == 1
```

Phir next:

```text
2 < 3
```

Isliye:

```text
a < b
```

`True`.

---

# Section 20.12: Accessing Values in Nested List

Nested list ka matlab list ke andar list.

```python
data = [
    ["AHU-001", 10, "Running"],
    ["AHU-002", 11, "Stopped"],
    ["VAV-001", 10, "Running"]
]
```

First row:

```python
print(data[0])
```

Output:

```text
['AHU-001', 10, 'Running']
```

---

## Specific value

```python
print(data[0][0])
```

Output:

```text
AHU-001
```

Yahan:

```text
data[0]
```

first row.

Phir:

```text
[0]
```

first column.

---

## Temperature example

```python
data = [
    ["AHU-001", 10, 22],
    ["AHU-002", 11, 25],
    ["VAV-001", 10, 23]
]
```

Second equipment ka temperature:

```python
print(data[1][2])
```

Output:

```text
25
```

---

## Nested list iterate karna

```python
for row in data:
    print(row)
```

Agar columns separately chahiye:

```python
for equipment_id, floor, temperature in data:
    print(equipment_id, floor, temperature)
```

Output:

```text
AHU-001 10 22
AHU-002 11 25
VAV-001 10 23
```

Ye **unpacking** hai.

---

## Nested list modify karna

```python
data[0][2] = 24
```

Ab:

```python
print(data[0])
```

Output:

```text
['AHU-001', 10, 24]
```

---

# Section 20.13: Initializing a List to a Fixed Number of Elements

Kabhi humein specific size ki list banani hoti hai.

Example: 5 zeros.

```python
numbers = [0] * 5

print(numbers)
```

Output:

```text
[0, 0, 0, 0, 0]
```

---

## 10 empty strings

```python
names = [""] * 10
```

Result:

```text
['', '', '', '', '', '', '', '', '', '']
```

---

## 5 `None` values

```python
data = [None] * 5
```

Result:

```text
[None, None, None, None, None]
```

---

## Important: nested lists ka common trap

Ye dangerous ho sakta hai:

```python
matrix = [[0] * 3] * 3
```

Dekhne mein:

```text
[
    [0, 0, 0],
    [0, 0, 0],
    [0, 0, 0]
]
```

lagta hai.

Lekin inner lists actually **same object** hain.

Agar:

```python
matrix[0][0] = 99
```

to result:

```text
[
    [99, 0, 0],
    [99, 0, 0],
    [99, 0, 0]
]
```

Ye unexpected hai.

---

## Correct method

```python
matrix = [
    [0] * 3
    for _ in range(3)
]
```

Ab:

```python
matrix[0][0] = 99
```

Result:

```text
[
    [99, 0, 0],
    [0, 0, 0],
    [0, 0, 0]
]
```

Ye correct independent rows hain.

---

# Practical Work-Order Example

Suppose work orders ki list hai:

```python
work_orders = [
    "WO-1001",
    "WO-1002",
    "WO-1003",
    "WO-1002"
]
```

### Total work orders

```python
print(len(work_orders))
```

Result:

```text
4
```

### Duplicate remove

```python
unique_work_orders = list(dict.fromkeys(work_orders))
```

Result:

```text
['WO-1001', 'WO-1002', 'WO-1003']
```

### Check work order

```python
if "WO-1002" in work_orders:
    print("Work order found")
```

### Loop

```python
for wo in work_orders:
    print(wo)
```

### Reverse

```python
for wo in reversed(work_orders):
    print(wo)
```

---

# Practical Equipment Example

```python
equipment = [
    ["AHU-001", "Floor 10", "Running", 22],
    ["AHU-002", "Floor 11", "Stopped", 25],
    ["VAV-001", "Floor 10", "Running", 23]
]
```

High temperature equipment:

```python
for equipment_id, floor, status, temperature in equipment:

    if temperature > 24:
        print(
            equipment_id,
            floor,
            temperature
        )
```

Output:

```text
AHU-002 Floor 11 25
```

Running equipment count:

```python
running_count = sum(
    1
    for equipment_id, floor, status, temperature in equipment
    if status == "Running"
)

print(running_count)
```

Output:

```text
2
```

Yahan `sum()` + generator expression ka use hua hai.

---

# Chapter 20 — Quick Revision

## List access

```python
items[0]
items[-1]
items[1:4]
```

## Add

```python
append()
insert()
extend()
```

## Remove

```python
remove()
pop()
clear()
```

## Search

```python
in
not in
index()
count()
```

## Order

```python
sort()
sorted()
reverse()
reversed()
```

## Size

```python
len()
```

## Logic

```python
any()
all()
```

## Combine

```python
+
extend()
```

## Duplicate removal

```python
list(set(items))
```

Order preserve karna ho:

```python
list(dict.fromkeys(items))
```

## Nested list

```python
data[row][column]
```

## Fixed-size list

```python
[0] * 10
```

Nested independent rows:

```python
[[0] * 3 for _ in range(3)]
```

---

# Most Important Mental Model

List ko is tarah yaad rakhein:

```text
                 LIST
                   │
       ┌───────────┼───────────┐
       ↓           ↓           ↓
    Access       Modify      Search
       │           │           │
    index[]    append()       in
    slice      insert()       index()
               remove()       count()
               pop()
               sort()
```

Aur list ke important built-ins:

```text
len()   → kitne elements?
any()   → koi ek True?
all()   → sab True?
sorted() → sorted new list?
reversed() → reverse iterator?
```

Sab se important differences:

```text
append(x)
→ x ko ek single element ki tarah add karta hai

extend(x)
→ x ke elements ko individually add karta hai

remove(x)
→ value ke basis par remove

pop(i)
→ index ke basis par remove aur value return

sort()
→ original list modify

sorted()
→ new sorted list

reverse()
→ original list reverse

[::-1]
→ new reversed list
```

Chapter 20 ka core concept:

```text
LIST = Ordered + Mutable + Indexed + Duplicate-friendly
```

Aur practical Python programming mein list ka use bohat frequently hota hai — especially work orders, equipment records, CSV rows, API data aur processed datasets ke saath.
