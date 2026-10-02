# Chapter 19: Dictionary

Python mein `dictionary` ek **key-value data structure** hai.

Basic structure:

```python
equipment = {
    "id": "AHU-001",
    "location": "Floor 10",
    "status": "Running"
}
```

Yahan:

* `"id"` → key
* `"AHU-001"` → value
* `"location"` → key
* `"Floor 10"` → value

Dictionary ka basic mental model:

```text
KEY → VALUE
```

---

# Section 19.1: Introduction to Dictionary

Dictionary curly braces `{}` use karta hai.

```python
person = {
    "name": "Ali",
    "age": 30,
    "city": "Riyadh"
}
```

Value access karne ke liye key use hoti hai:

```python
print(person["name"])
```

Output:

```text
Ali
```

### New value add karna

```python
person["job"] = "Engineer"
```

Ab:

```python
print(person)
```

Output:

```text
{
    "name": "Ali",
    "age": 30,
    "city": "Riyadh",
    "job": "Engineer"
}
```

### Existing value change karna

```python
person["age"] = 31
```

### Key delete karna

```python
del person["city"]
```

---

## Dictionary mein duplicate key

```python
data = {
    "name": "Ali",
    "name": "Ahmed"
}
```

Python mein same key dobara dene par **last value** remain karti hai.

```python
print(data)
```

Output:

```text
{'name': 'Ahmed'}
```

Is liye dictionary mein keys unique honi chahiye.

---

# Section 19.2: Avoiding KeyError Exceptions

Agar hum dictionary mein aisi key access karein jo exist nahi karti:

```python
equipment = {
    "id": "AHU-001",
    "status": "Running"
}

print(equipment["temperature"])
```

Error:

```text
KeyError: 'temperature'
```

Isko `KeyError` kehte hain.

---

## Method 1: `get()`

Sab se common solution:

```python
temperature = equipment.get("temperature")

print(temperature)
```

Output:

```text
None
```

Agar key exist karti ho:

```python
print(equipment.get("status"))
```

Output:

```text
Running
```

---

## `get()` ke saath default value

```python
temperature = equipment.get("temperature", 0)

print(temperature)
```

Output:

```text
0
```

Matlab:

> Agar `"temperature"` key mile to uski value do, warna `0` do.

Example:

```python
status = equipment.get("status", "Unknown")
```

---

## Method 2: `in`

```python
if "temperature" in equipment:
    print(equipment["temperature"])
else:
    print("Temperature not available")
```

Output:

```text
Temperature not available
```

### Important

Ye:

```python
equipment["temperature"]
```

missing key par `KeyError` de sakta hai.

Lekin:

```python
equipment.get("temperature")
```

normally `None` return karta hai.

---

# Section 19.3: Iterating Over a Dictionary

Dictionary ko `for` loop se iterate kar sakte hain.

```python
equipment = {
    "id": "AHU-001",
    "status": "Running",
    "temperature": 22
}

for key in equipment:
    print(key)
```

Output:

```text
id
status
temperature
```

---

## Keys aur values dono

```python
for key, value in equipment.items():
    print(key, value)
```

Output:

```text
id AHU-001
status Running
temperature 22
```

`items()` key-value pairs provide karta hai.

---

## Sirf keys

```python
for key in equipment.keys():
    print(key)
```

---

## Sirf values

```python
for value in equipment.values():
    print(value)
```

---

## Practical HVAC example

```python
ahu = {
    "id": "AHU-001",
    "fan": "ON",
    "temperature": 22,
    "damper": 65
}

for key, value in ahu.items():
    print(f"{key}: {value}")
```

Output:

```text
id: AHU-001
fan: ON
temperature: 22
damper: 65
```

---

# Section 19.4: Dictionary with Default Values

Kabhi humein dictionary mein values ko automatically initialize karna hota hai.

Is purpose ke liye `collections.defaultdict` useful hai.

```python
from collections import defaultdict
```

Example:

```python
counts = defaultdict(int)

counts["AHU"] += 1
counts["VAV"] += 1
counts["AHU"] += 1

print(counts)
```

Output:

```text
defaultdict(<class 'int'>, {'AHU': 2, 'VAV': 1})
```

Yahan `int()` ka default value:

```python
0
```

hai.

Isliye:

```python
counts["AHU"] += 1
```

automatically:

```text
0 + 1
```

se start ho jata hai.

---

## Normal dictionary mein same kaam

Normal dictionary mein:

```python
counts = {}

if "AHU" not in counts:
    counts["AHU"] = 0

counts["AHU"] += 1
```

`defaultdict` isko simpler bana deta hai:

```python
from collections import defaultdict

counts = defaultdict(int)

counts["AHU"] += 1
```

---

## List ke saath `defaultdict`

```python
from collections import defaultdict

equipment_by_floor = defaultdict(list)

equipment_by_floor["Floor 10"].append("AHU-001")
equipment_by_floor["Floor 10"].append("AHU-002")
equipment_by_floor["Floor 11"].append("AHU-003")

print(equipment_by_floor)
```

Result:

```text
Floor 10 → ['AHU-001', 'AHU-002']
Floor 11 → ['AHU-003']
```

Ye real-world data grouping mein bohat useful hai.

---

# Section 19.5: Merging Dictionaries

Python mein dictionaries merge karne ke multiple ways hain.

## Method 1: `|` operator

Modern Python mein:

```python
a = {
    "name": "Ali",
    "age": 30
}

b = {
    "city": "Riyadh",
    "job": "Engineer"
}

result = a | b

print(result)
```

Output:

```text
{
    'name': 'Ali',
    'age': 30,
    'city': 'Riyadh',
    'job': 'Engineer'
}
```

---

## Duplicate key hone par

```python
a = {
    "status": "Running"
}

b = {
    "status": "Stopped"
}

result = a | b

print(result)
```

Output:

```text
{'status': 'Stopped'}
```

Right-hand dictionary ki value overwrite karti hai.

---

## Method 2: `update()`

```python
a = {
    "name": "Ali",
    "age": 30
}

b = {
    "city": "Riyadh"
}

a.update(b)

print(a)
```

`update()` original dictionary ko modify karta hai.

Important difference:

```python
result = a | b
```

new dictionary banata hai.

Lekin:

```python
a.update(b)
```

`a` ko modify karta hai.

---

# Section 19.6: Accessing Keys and Values

Dictionary ke keys dekhne ke liye:

```python
equipment.keys()
```

Values:

```python
equipment.values()
```

Key-value pairs:

```python
equipment.items()
```

Example:

```python
equipment = {
    "id": "AHU-001",
    "status": "Running",
    "temperature": 22
}

print(equipment.keys())
print(equipment.values())
print(equipment.items())
```

---

## List mein convert karna

```python
keys = list(equipment.keys())
values = list(equipment.values())
items = list(equipment.items())
```

Ab:

```python
print(keys)
```

Output:

```text
['id', 'status', 'temperature']
```

---

# Section 19.7: Accessing Values of a Dictionary

Sab se direct method:

```python
equipment["status"]
```

Example:

```python
print(equipment["status"])
```

Lekin agar key missing ho sakti hai:

```python
print(equipment.get("status"))
```

Better approach:

```python
status = equipment.get("status", "Unknown")
```

---

## Nested dictionary

Dictionary ke andar dictionary bhi ho sakti hai.

```python
equipment = {
    "AHU-001": {
        "floor": 10,
        "temperature": 22,
        "status": "Running"
    }
}
```

Temperature access:

```python
print(equipment["AHU-001"]["temperature"])
```

Output:

```text
22
```

Yahan do keys hain:

```text
equipment
   ↓
"AHU-001"
   ↓
"temperature"
   ↓
22
```

---

# Section 19.8: Creating a Dictionary

Dictionary directly `{}` se bana sakte hain:

```python
person = {
    "name": "Ali",
    "age": 30
}
```

Empty dictionary:

```python
data = {}
```

Phir values add:

```python
data["name"] = "Ali"
data["age"] = 30
```

---

## Dictionary comprehension

Python mein dictionary comprehension bhi hoti hai.

```python
numbers = [1, 2, 3, 4, 5]

squares = {
    number: number ** 2
    for number in numbers
}

print(squares)
```

Output:

```text
{
    1: 1,
    2: 4,
    3: 9,
    4: 16,
    5: 25
}
```

Structure:

```python
{
    key_expression: value_expression
    for item in iterable
}
```

---

## Condition ke saath

```python
numbers = [1, 2, 3, 4, 5]

squares = {
    number: number ** 2
    for number in numbers
    if number % 2 == 0
}

print(squares)
```

Output:

```text
{2: 4, 4: 16}
```

---

# Section 19.9: Creating an Ordered Dictionary

Historical Python mein `OrderedDict` kaafi important tha.

```python
from collections import OrderedDict
```

Example:

```python
data = OrderedDict()

data["first"] = 1
data["second"] = 2
data["third"] = 3

print(data)
```

Modern Python mein normal `dict` insertion order preserve karta hai.

```python
data = {}

data["first"] = 1
data["second"] = 2
data["third"] = 3
```

Python 3.7+ mein dictionary insertion order language guarantee ka part hai.

Isliye normal:

```python
dict
```

aaj kal most cases mein sufficient hai.

`OrderedDict` phir bhi kuch specialized operations provide karta hai, jaise order-oriented APIs.

---

# Section 19.10: Unpacking Dictionaries Using `**`

`**` dictionary unpacking ke liye use ho sakta hai.

Example:

```python
person = {
    "name": "Ali",
    "age": 30
}

new_person = {
    **person,
    "city": "Riyadh"
}

print(new_person)
```

Output:

```text
{
    'name': 'Ali',
    'age': 30,
    'city': 'Riyadh'
}
```

Yahan:

```python
**person
```

ka matlab hai:

> `person` ke key-value pairs ko yahan spread/unpack karo.

---

## Two dictionaries merge karna

```python
a = {
    "name": "Ali",
    "age": 30
}

b = {
    "city": "Riyadh",
    "job": "Engineer"
}

result = {
    **a,
    **b
}

print(result)
```

Output:

```text
{
    'name': 'Ali',
    'age': 30,
    'city': 'Riyadh',
    'job': 'Engineer'
}
```

---

## Duplicate keys

```python
a = {
    "status": "Running"
}

b = {
    "status": "Stopped"
}

result = {
    **a,
    **b
}
```

Result:

```text
{'status': 'Stopped'}
```

Jo dictionary baad mein unpack hoti hai, uski value win karti hai.

---

## Function mein `**`

Ye concept bohat important hai.

```python
def show_equipment(**data):
    print(data)
```

Call:

```python
show_equipment(
    id="AHU-001",
    status="Running",
    temperature=22
)
```

Output:

```text
{'id': 'AHU-001', 'status': 'Running', 'temperature': 22}
```

`**data` keyword arguments ko dictionary mein collect karta hai.

---

# Section 19.11: The Trailing Comma

Trailing comma ka matlab hai last item ke baad comma.

Example:

```python
equipment = {
    "id": "AHU-001",
    "status": "Running",
}
```

Yahan:

```python
"status": "Running",
```

ke baad comma hai.

Ye valid Python hai.

---

## Single-item tuple mein comma important hai

Dictionary ke context se related ek important concept:

```python
x = (10)
```

Ye `int` hai:

```python
type(x)
```

Output:

```text
<class 'int'>
```

Lekin:

```python
x = (10,)
```

Ye tuple hai:

```text
<class 'tuple'>
```

Yani comma kabhi-kabhi syntax ka important part hota hai.

---

## Multi-line dictionary mein trailing comma useful hai

```python
equipment = {
    "id": "AHU-001",
    "floor": 10,
    "status": "Running",
}
```

Isse future mein new item add karna easy hota hai:

```python
equipment = {
    "id": "AHU-001",
    "floor": 10,
    "status": "Running",
    "temperature": 22,
}
```

---

# Section 19.12: The `dict()` Constructor

Dictionary banane ke liye `dict()` bhi use kar sakte hain.

```python
person = dict(
    name="Ali",
    age=30,
    city="Riyadh"
)

print(person)
```

Output:

```text
{
    'name': 'Ali',
    'age': 30,
    'city': 'Riyadh'
}
```

---

## Existing pairs se dictionary

```python
data = [
    ("id", "AHU-001"),
    ("status", "Running"),
    ("temperature", 22)
]

equipment = dict(data)

print(equipment)
```

Output:

```text
{
    'id': 'AHU-001',
    'status': 'Running',
    'temperature': 22
}
```

---

## `dict()` with another dictionary

```python
original = {
    "name": "Ali",
    "age": 30
}

copy_data = dict(original)
```

Ab:

```python
copy_data["age"] = 31
```

`original` ki value automatically change nahi hogi.

---

# Section 19.13: Dictionaries Example

Ab ek practical example banate hain.

Suppose hamare paas HVAC equipment ka data hai:

```python
equipment = {
    "MEP-AHU-001": {
        "type": "AHU",
        "floor": 10,
        "status": "Running",
        "temperature": 22
    },

    "MEP-AHU-002": {
        "type": "AHU",
        "floor": 11,
        "status": "Stopped",
        "temperature": 25
    },

    "MEP-VAV-001": {
        "type": "VAV",
        "floor": 10,
        "status": "Running",
        "temperature": 23
    }
}
```

---

## Equipment ID print karna

```python
for equipment_id in equipment:
    print(equipment_id)
```

Output:

```text
MEP-AHU-001
MEP-AHU-002
MEP-VAV-001
```

---

## Complete equipment information

```python
for equipment_id, details in equipment.items():
    print(equipment_id)
    print(details)
```

---

## Sirf running equipment

```python
for equipment_id, details in equipment.items():

    if details["status"] == "Running":
        print(equipment_id)
```

Output:

```text
MEP-AHU-001
MEP-VAV-001
```

---

## Temperature check

```python
for equipment_id, details in equipment.items():

    if details["temperature"] > 24:
        print(
            equipment_id,
            "High temperature:",
            details["temperature"]
        )
```

Output:

```text
MEP-AHU-002 High temperature: 25
```

---

## Missing key se bachna

Agar kisi equipment mein temperature available na ho:

```python
temperature = details.get("temperature", "N/A")
```

Ye `KeyError` se bachata hai.

---

# Section 19.14: All Combinations of Dictionary Values

Ye section thora advanced hai.

Suppose hamare paas multiple values hain:

```python
data = {
    "color": ["red", "blue"],
    "size": ["S", "M", "L"]
}
```

Humein har possible combination chahiye.

Possible combinations:

```text
red, S
red, M
red, L
blue, S
blue, M
blue, L
```

Iske liye `itertools.product()` useful hai.

```python
from itertools import product
```

Example:

```python
colors = ["red", "blue"]
sizes = ["S", "M", "L"]

combinations = product(colors, sizes)

for combination in combinations:
    print(combination)
```

Output:

```text
('red', 'S')
('red', 'M')
('red', 'L')
('blue', 'S')
('blue', 'M')
('blue', 'L')
```

---

## Dictionary ke values se combinations

```python
from itertools import product

data = {
    "color": ["red", "blue"],
    "size": ["S", "M"],
    "material": ["cotton", "polyester"]
}

combinations = product(*data.values())

for combination in combinations:
    print(combination)
```

Output:

```text
('red', 'S', 'cotton')
('red', 'S', 'polyester')
('red', 'M', 'cotton')
('red', 'M', 'polyester')
('blue', 'S', 'cotton')
('blue', 'S', 'polyester')
('blue', 'M', 'cotton')
('blue', 'M', 'polyester')
```

Yahan sab se important concept:

```python
*data.values()
```

`data.values()` ko unpack karta hai.

Agar:

```python
data.values()
```

mein ye hai:

```text
[
    ["red", "blue"],
    ["S", "M"],
    ["cotton", "polyester"]
]
```

to:

```python
*data.values()
```

effectively arguments ko alag-alag pass karta hai:

```python
product(
    ["red", "blue"],
    ["S", "M"],
    ["cotton", "polyester"]
)
```

---

# Practical HVAC Example: Possible Configurations

Suppose hum different HVAC configuration combinations generate karna chahte hain:

```python
from itertools import product

settings = {
    "mode": ["Auto", "Manual"],
    "fan": ["Low", "High"],
    "damper": [50, 75, 100]
}

for combination in product(*settings.values()):
    print(combination)
```

Har combination ek possible configuration hai.

Total combinations:

```text
2 × 2 × 3 = 12
```

Yani:

```python
len(list(product(*settings.values())))
```

Output:

```text
12
```

---

# Important Dictionary Concepts — Quick Revision

| Concept                | Syntax                   |
| ---------------------- | ------------------------ |
| Dictionary create      | `{}`                     |
| Value access           | `data[key]`              |
| Safe access            | `data.get(key)`          |
| Default value          | `data.get(key, default)` |
| Check key              | `key in data`            |
| Keys                   | `data.keys()`            |
| Values                 | `data.values()`          |
| Pairs                  | `data.items()`           |
| Add/update             | `data[key] = value`      |
| Merge                  | `a \| b`                 |
| Update                 | `a.update(b)`            |
| Delete                 | `del data[key]`          |
| Dictionary constructor | `dict(...)`              |
| Unpack dictionary      | `**data`                 |
| Default dictionary     | `defaultdict(...)`       |
| Ordered dictionary     | `OrderedDict(...)`       |
| Combinations           | `product(...)`           |

---

# Most Important Points

### 1. `[]` vs `.get()`

```python
data["temperature"]
```

Missing key → `KeyError`

```python
data.get("temperature")
```

Missing key → `None`

---

### 2. `get()` with default

```python
data.get("temperature", 0)
```

Missing key → `0`

---

### 3. `.items()`

```python
for key, value in data.items():
    print(key, value)
```

Key aur value dono ek saath milte hain.

---

### 4. `|` merge

```python
result = a | b
```

New merged dictionary.

---

### 5. `update()`

```python
a.update(b)
```

Original `a` modify hota hai.

---

### 6. `**` dictionary unpacking

```python
result = {
    **a,
    **b
}
```

Dictionary ke key-value pairs spread/unpack ho jate hain.

---

### 7. `defaultdict`

```python
from collections import defaultdict

counts = defaultdict(int)
```

Missing key ke liye default value automatically provide kar sakta hai.

---

### 8. `dict()` constructor

```python
data = dict(name="Ali", age=30)
```

Dictionary create karne ka alternate method hai.

---

### 9. `product()`

```python
from itertools import product

product([1, 2], ["A", "B"])
```

All possible combinations generate karta hai.

---

# Chapter 19 ka Mental Model

Dictionary ko is tarah yaad rakhein:

```text
                 DICTIONARY
                      │
        ┌─────────────┼─────────────┐
        ↓             ↓             ↓
       Key          Value        Key-Value
        │             │             │
     access         data         .items()
        │
        ├── data[key]
        └── data.get(key)
        
        Operations
             │
     ┌───────┼────────┐
     ↓       ↓        ↓
   merge   update   unpack
     │       │        │
     |     update()   **
```

Aur sab se important rule:

```text
Dictionary = Key → Value
```

Agar key exist nahi karti:

```python
data[key]
```

→ `KeyError`

Safe access:

```python
data.get(key)
```

Multiple dictionaries combine:

```python
a | b
```

ya:

```python
{**a, **b}
```

Default values ke liye:

```python
defaultdict
```

Aur all possible combinations ke liye:

```python
itertools.product()
```
