# Chapter 21: List Comprehensions

List comprehension Python mein ek concise tareeqa hai jis se hum existing iterable, jaise list, se new list create kar sakte hain.

Normal `for` loop se bhi list bana sakte hain, lekin list comprehension aksar code ko chhota aur readable bana deti hai.

## Section 21.1: List Comprehensions

Sab se pehle normal `for` loop dekhte hain.

```python
numbers = [1, 2, 3, 4, 5]

squares = []

for number in numbers:
    squares.append(number ** 2)

print(squares)
```

Output:

```text
[1, 4, 9, 16, 25]
```

Ab isi kaam ko list comprehension se karte hain:

```python
numbers = [1, 2, 3, 4, 5]

squares = [number ** 2 for number in numbers]

print(squares)
```

Output:

```text
[1, 4, 9, 16, 25]
```

Dono ka result same hai.

### List comprehension ka structure

```python
new_list = [expression for item in iterable]
```

Isko parts mein samjhein:

| Part          | Meaning                                 |
| ------------- | --------------------------------------- |
| `expression`  | Har item se kya value banani hai        |
| `for item`    | Har item ko ek ek karke lena            |
| `in iterable` | Kis list ya iterable se items lene hain |

Example:

```python
numbers = [2, 4, 6]

doubled = [number * 2 for number in numbers]

print(doubled)
```

Output:

```text
[4, 8, 12]
```

Step-by-step:

1. Pehle `number = 2`, expression `2 * 2` → `4`
2. Phir `number = 4`, expression `4 * 2` → `8`
3. Phir `number = 6`, expression `6 * 2` → `12`

Final list:

```python
[4, 8, 12]
```

### HVAC example

Suppose equipment IDs ki list hai:

```python
equipment = [
    "AHU-001",
    "AHU-002",
    "VAV-001"
]
```

Har ID ke saath `MEP-` prefix add karna hai:

```python
new_ids = [f"MEP-{item}" for item in equipment]

print(new_ids)
```

Output:

```text
['MEP-AHU-001', 'MEP-AHU-002', 'MEP-VAV-001']
```

**Yaad rakhein:** List comprehension mein expression har item ke liye evaluate hota hai aur result new list mein add hota hai.

---

## Section 21.2: Conditional List Comprehensions

List comprehension mein `if` condition bhi use kar sakte hain.

Syntax:

```python
new_list = [expression for item in iterable if condition]
```

Example:

```python
numbers = [1, 2, 3, 4, 5, 6]

even_numbers = [
    number
    for number in numbers
    if number % 2 == 0
]

print(even_numbers)
```

Output:

```text
[2, 4, 6]
```

Yahan sirf woh numbers new list mein add honge jin par condition `True` hogi.

### Normal loop ke saath comparison

Normal loop:

```python
numbers = [1, 2, 3, 4, 5, 6]

even_numbers = []

for number in numbers:
    if number % 2 == 0:
        even_numbers.append(number)
```

List comprehension:

```python
even_numbers = [
    number
    for number in numbers
    if number % 2 == 0
]
```

Dono ka result same hai.

### Condition ke saath transformation

Sirf even numbers select nahi karne, balki unka square bhi banana hai.

```python
numbers = [1, 2, 3, 4, 5, 6]

squares = [
    number ** 2
    for number in numbers
    if number % 2 == 0
]

print(squares)
```

Output:

```text
[4, 16, 36]
```

Yahan:

* `if number % 2 == 0` even numbers select karta hai.
* `number ** 2` selected numbers ka square banata hai.

### HVAC example: High temperature

```python
temperatures = [22, 25, 28, 23, 31]

high_temperatures = [
    temp
    for temp in temperatures
    if temp > 27
]

print(high_temperatures)
```

Output:

```text
[28, 31]
```

### `if-else` ke saath value choose karna

Ek important difference hai.

Agar `if` expression ke baad aaye, to items filter hote hain:

```python
result = [
    number
    for number in numbers
    if number > 3
]
```

Lekin agar `if-else` expression se pehle aaye, to har item ke liye value choose hoti hai:

```python
numbers = [1, 2, 3, 4, 5]

labels = [
    "High" if number > 3 else "Low"
    for number in numbers
]

print(labels)
```

Output:

```text
['Low', 'Low', 'Low', 'High', 'High']
```

Is example mein koi number remove nahi hua. Har number ke liye `"High"` ya `"Low"` generate hua.

**Difference:**

```python
[value for item in items if condition]
```

Condition false ho to item skip hota hai.

```python
[value_if_true if condition else value_if_false for item in items]
```

Har item ke liye ek value generate hoti hai.

---

## Section 21.3: Avoid Repetitive and Expensive Operations Using Conditional Clause

Kabhi condition check karne ke liye expensive function call karna padta hai. Agar woh function baar baar call ho, to program slow ho sakta hai.

Example:

```python
def get_status(equipment_id):
    print("Checking:", equipment_id)
    return "Running"
```

Ab list comprehension:

```python
equipment = ["AHU-001", "AHU-002", "VAV-001"]

running = [
    item
    for item in equipment
    if get_status(item) == "Running"
]
```

Yahan har item ke liye `get_status()` call hoga.

Agar function database ya API se data la raha ho, to ye operation expensive ho sakta hai.

### Repeated calculation se bachna

Maan lein humein temperature ko convert karke check karna hai.

```python
temperatures = [20, 25, 30, 35]

result = [
    temp * 1.8 + 32
    for temp in temperatures
    if temp * 1.8 + 32 > 80
]
```

Yahan selected temperature ke liye conversion do baar ho sakti hai: ek condition mein aur ek expression mein.

Agar calculation expensive ho, to pehle calculate karke store karna behtar hai.

```python
temperatures_f = [
    temp * 1.8 + 32
    for temp in temperatures
]

result = [
    temp
    for temp in temperatures_f
    if temp > 80
]
```

Ab conversion sirf ek baar hui.

### Walrus operator `:=`

Python 3.8+ mein assignment expression, jise walrus operator kehte hain, use kar sakte hain.

```python
temperatures = [20, 25, 30, 35]

result = [
    fahrenheit
    for temp in temperatures
    if (fahrenheit := temp * 1.8 + 32) > 80
]

print(result)
```

Output:

```text
[86.0, 95.0]
```

Yahan:

```python
(fahrenheit := temp * 1.8 + 32)
```

calculation karta hai aur result `fahrenheit` variable mein assign bhi karta hai.

Phir wahi value condition mein check hoti hai aur expression mein use hoti hai.

**Important:** Walrus operator har situation mein zaroori nahi. Agar code complex ho raha ho, to normal `for` loop zyada readable ho sakta hai.

---

## Section 21.4: Dictionary Comprehensions

List comprehension ki tarah dictionary comprehension bhi hoti hai.

Syntax:

```python
new_dict = {
    key_expression: value_expression
    for item in iterable
}
```

Example:

```python
numbers = [1, 2, 3, 4]

squares = {
    number: number ** 2
    for number in numbers
}

print(squares)
```

Output:

```text
{1: 1, 2: 4, 3: 9, 4: 16}
```

Yahan:

* Number dictionary ki key ban raha hai.
* Uska square value ban raha hai.

### Condition ke saath dictionary comprehension

```python
numbers = [1, 2, 3, 4, 5, 6]

squares = {
    number: number ** 2
    for number in numbers
    if number % 2 == 0
}

print(squares)
```

Output:

```text
{2: 4, 4: 16, 6: 36}
```

### HVAC example

Equipment IDs aur temperatures ko dictionary mein convert karte hain:

```python
equipment = [
    ("AHU-001", 22),
    ("AHU-002", 25),
    ("VAV-001", 23)
]

temperatures = {
    equipment_id: temp
    for equipment_id, temp in equipment
}

print(temperatures)
```

Output:

```text
{'AHU-001': 22, 'AHU-002': 25, 'VAV-001': 23}
```

Agar sirf high temperature equipment chahiye:

```python
high_temp = {
    equipment_id: temp
    for equipment_id, temp in equipment
    if temp > 23
}

print(high_temp)
```

Output:

```text
{'AHU-002': 25}
```

---

## Section 21.5: List Comprehensions with Nested Loops

List comprehension mein ek se zyada `for` loops use kar sakte hain.

Normal nested loops:

```python
pairs = []

for x in [1, 2]:
    for y in [10, 20]:
        pairs.append((x, y))

print(pairs)
```

Output:

```text
[(1, 10), (1, 20), (2, 10), (2, 20)]
```

List comprehension:

```python
pairs = [
    (x, y)
    for x in [1, 2]
    for y in [10, 20]
]

print(pairs)
```

Output same hai:

```text
[(1, 10), (1, 20), (2, 10), (2, 20)]
```

### Loops ka order

Is comprehension mein:

```python
[
    (x, y)
    for x in [1, 2]
    for y in [10, 20]
]
```

Pehle `x` loop chalta hai. Har `x` ke liye `y` loop complete hota hai.

Isliye combinations ka order:

```text
(1, 10)
(1, 20)
(2, 10)
(2, 20)
```

### Teen loops

```python
combinations = [
    (x, y, z)
    for x in [1, 2]
    for y in [10, 20]
    for z in ["A", "B"]
]

print(combinations)
```

Output:

```text
[
    (1, 10, 'A'),
    (1, 10, 'B'),
    (1, 20, 'A'),
    (1, 20, 'B'),
    (2, 10, 'A'),
    (2, 10, 'B'),
    (2, 20, 'A'),
    (2, 20, 'B')
]
```

Total combinations:

```text
2 × 2 × 2 = 8
```

### HVAC example

```python
floors = [10, 11]
equipment_types = ["AHU", "VAV"]

equipment = [
    f"{equipment_type}-Floor-{floor}"
    for floor in floors
    for equipment_type in equipment_types
]

print(equipment)
```

Output:

```text
[
    'AHU-Floor-10',
    'VAV-Floor-10',
    'AHU-Floor-11',
    'VAV-Floor-11'
]
```

---

## Section 21.6: Generator Expressions

Generator expression ka syntax list comprehension jaisa hai, lekin square brackets ki jagah parentheses use hote hain.

List comprehension:

```python
squares = [x ** 2 for x in range(5)]
```

Generator expression:

```python
squares = (x ** 2 for x in range(5))
```

Dono mein values generate karne ka logic same hai, lekin behavior different hai.

### List comprehension

```python
squares = [x ** 2 for x in range(5)]

print(squares)
```

Output:

```text
[0, 1, 4, 9, 16]
```

List saari values memory mein store karti hai.

### Generator expression

```python
squares = (x ** 2 for x in range(5))

print(squares)
```

Output kuch is tarah hoga:

```text
<generator object <genexpr> at ...>
```

Generator saari values ek saath store nahi karta. Values zaroorat ke mutabiq produce karta hai.

```python
for value in squares:
    print(value)
```

Output:

```text
0
1
4
9
16
```

### Generator ka faida

Agar bohat zyada data ho, to generator memory bachane mein madad kar sakta hai.

Example:

```python
total = sum(
    number ** 2
    for number in range(1_000_000)
)

print(total)
```

Yahan generator expression `sum()` ko values ek ek karke deta hai. Puri million values ki list create nahi hoti.

### Generator one-time iteration hota hai

```python
numbers = (x for x in range(3))

print(list(numbers))
print(list(numbers))
```

Output:

```text
[0, 1, 2]
[]
```

Pehli baar generator consume ho gaya. Doosri baar values nahi milin.

**Yaad rakhein:**

* List comprehension → values ki list create hoti hai.
* Generator expression → values demand par generate hoti hain.
* Generator ko dobara use karna ho to naya generator create karein.

---

## Section 21.7: Set Comprehensions

Set comprehension se set create hota hai.

Syntax:

```python
new_set = {
    expression
    for item in iterable
}
```

Example:

```python
numbers = [1, 2, 2, 3, 3, 4]

squares = {
    number ** 2
    for number in numbers
}

print(squares)
```

Output mein unique values hongi:

```text
{16, 1, 4, 9}
```

Set order guarantee nahi karta, isliye output ka order different ho sakta hai.

### Condition ke saath

```python
numbers = [1, 2, 3, 4, 5, 6]

even_squares = {
    number ** 2
    for number in numbers
    if number % 2 == 0
}

print(even_squares)
```

Output:

```text
{16, 4, 36}
```

### Duplicate equipment IDs remove karna

```python
equipment = [
    "AHU-001",
    "AHU-002",
    "AHU-001",
    "VAV-001"
]

unique_equipment = {
    item
    for item in equipment
}

print(unique_equipment)
```

Set duplicates remove kar dega. Lekin agar original order preserve karna hai, to:

```python
unique_equipment = list(dict.fromkeys(equipment))
```

use karein.

---

## Section 21.8: Refactoring `filter()` and `map()` to List Comprehensions

Python mein `map()` aur `filter()` built-in functions hain.

Lekin kai cases mein list comprehension unka readable alternative hoti hai.

### `map()` ka example

`map()` har item par function apply karta hai.

```python
numbers = [1, 2, 3, 4]

squares = list(map(lambda x: x ** 2, numbers))

print(squares)
```

Output:

```text
[1, 4, 9, 16]
```

Isko list comprehension se likhein:

```python
squares = [x ** 2 for x in numbers]
```

Result same hai.

### `filter()` ka example

`filter()` condition ke mutabiq items select karta hai.

```python
numbers = [1, 2, 3, 4, 5, 6]

even_numbers = list(
    filter(lambda x: x % 2 == 0, numbers)
)

print(even_numbers)
```

Output:

```text
[2, 4, 6]
```

List comprehension:

```python
even_numbers = [
    x
    for x in numbers
    if x % 2 == 0
]
```

Result same hai.

### `map()` aur `filter()` ek saath

```python
numbers = [1, 2, 3, 4, 5, 6]

result = list(
    map(
        lambda x: x ** 2,
        filter(lambda x: x % 2 == 0, numbers)
    )
)

print(result)
```

Output:

```text
[4, 16, 36]
```

List comprehension:

```python
result = [
    x ** 2
    for x in numbers
    if x % 2 == 0
]
```

Dono ka output same hai.

### Kab list comprehension use karein?

Jab transformation aur filtering simple ho, list comprehension aksar zyada readable hoti hai.

Lekin agar function complex hai ya multiple steps hain, normal `for` loop behtar ho sakta hai.

---

## Section 21.9: Comprehensions Involving Tuples

List comprehension mein tuple create kar sakte hain.

Example:

```python
numbers = [1, 2, 3]

result = [
    (number, number ** 2)
    for number in numbers
]

print(result)
```

Output:

```text
[(1, 1), (2, 4), (3, 9)]
```

Har output element ek tuple hai.

### Multiple values ko tuple mein combine karna

```python
names = ["Ali", "Ahmed", "Sara"]

result = [
    (name, len(name))
    for name in names
]

print(result)
```

Output:

```text
[('Ali', 3), ('Ahmed', 5), ('Sara', 4)]
```

### Tuple unpacking

Agar input tuples ki list ho:

```python
equipment = [
    ("AHU-001", 22),
    ("AHU-002", 25),
    ("VAV-001", 23)
]

result = [
    (equipment_id, temp * 1.8 + 32)
    for equipment_id, temp in equipment
]

print(result)
```

Output:

```text
[
    ('AHU-001', 71.6),
    ('AHU-002', 77.0),
    ('VAV-001', 73.4)
]
```

Yahan loop ke andar tuple unpack ho raha hai:

```python
for equipment_id, temp in equipment
```

---

## Section 21.10: Counting Occurrences Using Comprehension

List comprehension ko counting ke liye bhi use kar sakte hain, lekin simple counting ke liye `count()` aksar zyada direct hota hai.

Example:

```python
statuses = [
    "Running",
    "Stopped",
    "Running",
    "Running",
    "Stopped"
]
```

`Running` kitni baar hai?

```python
count = sum(
    1
    for status in statuses
    if status == "Running"
)

print(count)
```

Output:

```text
3
```

### Ye kaise kaam karta hai?

```python
1 for status in statuses if status == "Running"
```

Har matching item ke liye `1` generate hota hai.

Phir `sum()` in ones ko add karta hai.

Example:

```text
Running → 1
Stopped → skip
Running → 1
Running → 1
Stopped → skip
```

Total:

```text
1 + 1 + 1 = 3
```

### `count()` se comparison

```python
count = statuses.count("Running")
```

Ye bhi `3` return karega.

### Multiple status counts

```python
statuses = [
    "Running",
    "Stopped",
    "Running",
    "Maintenance"
]

counts = {
    status: statuses.count(status)
    for status in set(statuses)
}

print(counts)
```

Possible output:

```text
{
    'Running': 2,
    'Stopped': 1,
    'Maintenance': 1
}
```

Set ka order fixed nahi hota.

Agar large list ho, to har unique status ke liye baar baar `.count()` chalana inefficient ho sakta hai. Aise case mein `collections.Counter` behtar hai:

```python
from collections import Counter

counts = Counter(statuses)

print(counts)
```

---

## Section 21.11: Changing Types in a List

List comprehension se list ke elements ka data type convert kar sakte hain.

### String se integer

```python
numbers = ["10", "20", "30", "40"]

converted = [
    int(number)
    for number in numbers
]

print(converted)
```

Output:

```text
[10, 20, 30, 40]
```

Ab values `str` nahi, `int` hain.

```python
print(type(converted[0]))
```

Output:

```text
<class 'int'>
```

### Integer se string

```python
numbers = [10, 20, 30]

converted = [
    str(number)
    for number in numbers
]

print(converted)
```

Output:

```text
['10', '20', '30']
```

### String se float

```python
readings = ["22.5", "23.0", "24.7"]

temperatures = [
    float(value)
    for value in readings
]

print(temperatures)
```

Output:

```text
[22.5, 23.0, 24.7]
```

### Important: invalid conversion

```python
values = ["10", "20", "abc"]

numbers = [
    int(value)
    for value in values
]
```

Is code se `ValueError` aayega, kyun ke `"abc"` integer mein convert nahi ho sakta.

Agar data unreliable ho, to pehle validation karein ya `try/except` use karein.

---

## Section 21.12: Nested List Comprehensions

Nested list comprehension se list ke andar lists create kar sakte hain.

Example:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

Isko comprehension se create karein:

```python
matrix = [
    [0 for column in range(3)]
    for row in range(3)
]

print(matrix)
```

Output:

```text
[
    [0, 0, 0],
    [0, 0, 0],
    [0, 0, 0]
]
```

Yahan outer comprehension rows create karti hai, aur inner comprehension har row ke columns create karti hai.

### Values generate karna

```python
matrix = [
    [row * 3 + column for column in range(3)]
    for row in range(3)
]

print(matrix)
```

Output:

```text
[
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8]
]
```

### Existing nested list ko flatten karna

Suppose:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

Humein ek single list chahiye:

```python
flat = [
    value
    for row in matrix
    for value in row
]

print(flat)
```

Output:

```text
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Loop order normal nested loop jaisa hai:

```python
flat = []

for row in matrix:
    for value in row:
        flat.append(value)
```

### Nested comprehension ka order

```python
[
    value
    for row in matrix
    for value in row
]
```

Pehle outer `row` select hoti hai. Phir us row ke har `value` par inner loop chalta hai.

### HVAC example

```python
floor_equipment = [
    ["AHU-001", "AHU-002"],
    ["AHU-003", "AHU-004"],
    ["VAV-001", "VAV-002"]
]

all_equipment = [
    item
    for floor in floor_equipment
    for item in floor
]

print(all_equipment)
```

Output:

```text
[
    'AHU-001',
    'AHU-002',
    'AHU-003',
    'AHU-004',
    'VAV-001',
    'VAV-002'
]
```

---

## Section 21.13: Iterate Two or More Lists Simultaneously Within List Comprehension

Agar do lists ke elements ko same index par process karna ho, to `zip()` use kar sakte hain.

Example:

```python
names = ["Ali", "Ahmed", "Sara"]
ages = [25, 30, 28]

result = [
    (name, age)
    for name, age in zip(names, ages)
]

print(result)
```

Output:

```text
[('Ali', 25), ('Ahmed', 30), ('Sara', 28)]
```

`zip()` dono lists ke matching elements ko pair karta hai.

### HVAC example

```python
equipment_ids = [
    "AHU-001",
    "AHU-002",
    "VAV-001"
]

temperatures = [22, 25, 23]

result = [
    f"{equipment_id}: {temperature}°C"
    for equipment_id, temperature
    in zip(equipment_ids, temperatures)
]

print(result)
```

Output:

```text
[
    'AHU-001: 22°C',
    'AHU-002: 25°C',
    'VAV-001: 23°C'
]
```

### Different length wali lists

```python
a = [1, 2, 3]
b = ["A", "B"]

result = [
    (x, y)
    for x, y in zip(a, b)
]

print(result)
```

Output:

```text
[(1, 'A'), (2, 'B')]
```

Normal `zip()` shortest iterable par ruk jata hai.

Python 3.10+ mein agar lengths equal honi zaroori hain, to:

```python
result = list(zip(a, b, strict=True))
```

Different lengths par `ValueError` raise hota hai.

### Teen lists ek saath

```python
equipment_ids = ["AHU-001", "AHU-002"]
floors = [10, 11]
statuses = ["Running", "Stopped"]

result = [
    (equipment_id, floor, status)
    for equipment_id, floor, status
    in zip(equipment_ids, floors, statuses)
]

print(result)
```

Output:

```text
[
    ('AHU-001', 10, 'Running'),
    ('AHU-002', 11, 'Stopped')
]
```

### Cartesian combinations aur `zip()` ka difference

`zip()` matching positions ko pair karta hai:

```python
[(x, y) for x, y in zip([1, 2], ["A", "B"])]
```

Output:

```text
[(1, 'A'), (2, 'B')]
```

Lekin nested loops har possible combination banate hain:

```python
[
    (x, y)
    for x in [1, 2]
    for y in ["A", "B"]
]
```

Output:

```text
[(1, 'A'), (1, 'B'), (2, 'A'), (2, 'B')]
```

`zip()` matching items ke liye hai; nested loops all combinations ke liye.

---

# Chapter 21: Quick Revision

| Concept                  | Syntax                                   |
| ------------------------ | ---------------------------------------- |
| Basic list comprehension | `[x for x in items]`                     |
| Transformation           | `[x * 2 for x in items]`                 |
| Filtering                | `[x for x in items if condition]`        |
| Conditional value        | `[a if condition else b for x in items]` |
| Dictionary comprehension | `{k: v for x in items}`                  |
| Set comprehension        | `{x for x in items}`                     |
| Generator expression     | `(x for x in items)`                     |
| Nested loops             | `[... for x in a for y in b]`            |
| Flatten nested list      | `[v for row in matrix for v in row]`     |
| Pair two lists           | `[... for x, y in zip(a, b)]`            |
| Count matches            | `sum(1 for x in items if condition)`     |
| Convert types            | `[int(x) for x in items]`                |

## List comprehension ka basic structure

```python
[
    expression
    for item in iterable
    if condition
]
```

Yaad rakhein:

* `expression` batata hai kya value generate hogi.
* `for` batata hai kis iterable se values leni hain.
* `if` optional hai aur items filter karta hai.

## List comprehension kab use karni chahiye?

Use karein jab:

* Simple transformation karni ho.
* Simple filtering karni ho.
* Ek iterable se new list banani ho.
* Code ek line ya chhote block mein clearly samajh aa raha ho.

Normal `for` loop use karein jab:

* Multiple complex operations hon.
* Error handling ya logging chahiye.
* Nested logic bohat complicated ho.
* Readability comprehension se kam ho rahi ho.

**Important:** Short code hamesha better code nahi hota. Readability aur maintainability bhi zaroori hain.

---

# Practice Exercises

In exercises ko khud solve karne ki koshish karein.

### Exercise 1: Squares

```python
numbers = [2, 3, 4, 5, 6]
```

List comprehension se har number ka square banayein.

Expected output:

```text
[4, 9, 16, 25, 36]
```

### Exercise 2: Even numbers

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8]
```

Sirf even numbers ki list banayein.

Expected output:

```text
[2, 4, 6, 8]
```

### Exercise 3: High temperature

```python
temperatures = [21, 25, 29, 23, 31, 27]
```

Sirf 27 se zyada temperatures ki list banayein.

Expected output:

```text
[29, 31]
```

### Exercise 4: Dictionary comprehension

```python
equipment = ["AHU-001", "AHU-002", "VAV-001"]
```

Aisi dictionary banayein jisme har equipment ID ki value uski length ho.

Expected output:

```text
{
    'AHU-001': 7,
    'AHU-002': 7,
    'VAV-001': 7
}
```

### Exercise 5: Flatten nested list

```python
data = [
    [1, 2],
    [3, 4],
    [5, 6]
]
```

Ek single list banayein.

Expected output:

```text
[1, 2, 3, 4, 5, 6]
```

### Exercise 6: Count running equipment

```python
statuses = [
    "Running",
    "Stopped",
    "Running",
    "Maintenance",
    "Running"
]
```

Comprehension aur `sum()` use karke `"Running"` ki count nikalein.

Expected output:

```text
3
```

### Exercise 7: Two lists with `zip()`

```python
equipment_ids = ["AHU-001", "AHU-002"]
statuses = ["Running", "Stopped"]
```

Har equipment ID aur status ka tuple banayein.

Expected output:

```text
[('AHU-001', 'Running'), ('AHU-002', 'Stopped')]
```

---

# Final Mental Model

```text
COMPREHENSIONS
      |
      |-- List:       [expression for item in iterable]
      |
      |-- Conditional: [expression for item in iterable if condition]
      |
      |-- Dictionary: {key: value for item in iterable}
      |
      |-- Set:        {expression for item in iterable}
      |
      |-- Generator:  (expression for item in iterable)
      |
      |-- Nested:     [expression for x in a for y in b]
      |
      |-- Zip:        [expression for x, y in zip(a, b)]
```

Chapter 21 ka main concept ye hai ke comprehensions se hum iterable ke items ko **transform, filter, combine aur count** kar sakte hain.

Sab se pehle simple list comprehension achhi tarah samjhein. Phir conditions, nested loops aur generators ki taraf jayein. Is tarah advanced syntax ko samajhna asaan rahega.
