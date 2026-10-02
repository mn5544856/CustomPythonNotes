# Chapter 28: Tuple

Python mein **tuple** ek ordered collection hai jo multiple values ko ek single object mein store karta hai.

Basic example:

```python
numbers = (10, 20, 30, 40)
```

Tuple mein:

* Order maintain hota hai.
* Indexing available hoti hai.
* Duplicate values allowed hoti hain.
* Tuple **immutable** hota hai.
* Tuple different data types ke elements rakh sakta hai.

Example:

```python
data = ("AHU-001", 24, True, 1250.5)
```

Yahan ek hi tuple mein:

```text
str
int
bool
float
```

stored hain.

---

# Section 28.1: Tuple

Tuple create karne ka normal syntax:

```python
my_tuple = (10, 20, 30)
```

Parentheses generally tuple ko represent karti hain.

```python
numbers = (10, 20, 30)

print(numbers)
```

Output:

```text
(10, 20, 30)
```

## Parentheses hamesha required nahi

Python mein comma tuple banane ke liye important hai.

```python
numbers = 10, 20, 30
```

Ye bhi tuple hai:

```python
print(numbers)
```

Output:

```text
(10, 20, 30)
```

## Single-element tuple

Yahan beginners aksar mistake karte hain:

```python
number = (10)
```

Ye tuple nahi hai.

```python
print(type(number))
```

Output:

```text
<class 'int'>
```

Single-element tuple ke liye comma required hai:

```python
number = (10,)
```

Ab:

```python
print(type(number))
```

Output:

```text
<class 'tuple'>
```

Isliye:

```python
(10)    # int
(10,)   # tuple
```

**Single-item tuple mein comma important hai.**

---

# Section 28.2: Tuples Are Immutable

**Immutable** ka matlab hai:

> Tuple create hone ke baad uske existing elements ko change nahi kar sakte.

Example:

```python
numbers = (10, 20, 30)

numbers[0] = 100
```

Ye error dega:

```text
TypeError: 'tuple' object does not support item assignment
```

Yani:

```python
numbers[0] = 100
```

allowed nahi hai.

## List vs Tuple

List:

```python
numbers = [10, 20, 30]

numbers[0] = 100

print(numbers)
```

Output:

```text
[100, 20, 30]
```

Tuple:

```python
numbers = (10, 20, 30)

numbers[0] = 100
```

Error.

Comparison:

| Feature          | List       | Tuple                           |
| ---------------- | ---------- | ------------------------------- |
| Ordered          | Yes        | Yes                             |
| Mutable          | Yes        | No                              |
| Indexing         | Yes        | Yes                             |
| Duplicate values | Yes        | Yes                             |
| `append()`       | Yes        | No                              |
| `remove()`       | Yes        | No                              |
| Hashable         | Usually no | Often yes, if elements hashable |

---

## Tuple ko modify kaise karein?

Tuple directly modify nahi hota.

Agar zaroorat ho to new tuple create karein:

```python
numbers = (10, 20, 30)

numbers = (100,) + numbers[1:]

print(numbers)
```

Output:

```text
(100, 20, 30)
```

Yahan original tuple modify nahi hua. Ek **new tuple** create hua.

---

## Tuple ke andar mutable object

Ek important advanced point:

Tuple immutable hai, lekin tuple ke andar koi mutable object ho sakta hai.

Example:

```python
data = ([10, 20], "AHU")
```

Hum tuple ka first element replace nahi kar sakte:

```python
data[0] = [30, 40]
```

Ye error dega.

Lekin first element khud ek list hai, aur list mutable hai:

```python
data[0].append(30)

print(data)
```

Output:

```text
([10, 20, 30], 'AHU')
```

Yani:

> Tuple ka structure immutable hai, lekin uske andar stored mutable object apni internal state change kar sakta hai.

---

# Section 28.3: Packing and Unpacking Tuples

## Tuple Packing

Multiple values ko ek tuple mein pack karna:

```python
equipment = "AHU-001", "Level 10", 24
```

Python isko tuple bana deta hai:

```python
print(equipment)
```

Output:

```text
('AHU-001', 'Level 10', 24)
```

Ye **tuple packing** hai.

Explicit parentheses bhi use kar sakte hain:

```python
equipment = ("AHU-001", "Level 10", 24)
```

---

## Tuple Unpacking

Tuple ke elements ko multiple variables mein assign karna:

```python
equipment = ("AHU-001", "Level 10", 24)

equipment_id, floor, temperature = equipment

print(equipment_id)
print(floor)
print(temperature)
```

Output:

```text
AHU-001
Level 10
24
```

Yahan:

```text
equipment
   ↓
("AHU-001", "Level 10", 24)
   ↓
   ├── equipment_id
   ├── floor
   └── temperature
```

Isko **unpacking** kehte hain.

---

## Number of variables match hona chahiye

Ye:

```python
data = (10, 20, 30)

a, b = data
```

error dega, kyun ke 3 values hain lekin variables 2.

Isi tarah:

```python
a, b, c, d = data
```

bhi error dega.

Normally:

```text
values ki quantity = variables ki quantity
```

honi chahiye.

---

## Starred unpacking

Aap `*` use karke multiple remaining values collect kar sakte hain.

```python
numbers = (10, 20, 30, 40, 50)

first, *middle, last = numbers

print(first)
print(middle)
print(last)
```

Output:

```text
10
[20, 30, 40]
50
```

Notice karein:

```python
middle
```

tuple nahi, **list** hoti hai.

---

# Function se Multiple Values Return Karna

Python mein function multiple values return kar sakta hai.

```python
def get_equipment():
    return "AHU-001", "Level 10", 24
```

Actually function ek tuple return kar raha hai.

```python
result = get_equipment()

print(result)
```

Output:

```text
('AHU-001', 'Level 10', 24)
```

Ya directly unpack:

```python
equipment_id, floor, temperature = get_equipment()
```

Ye Python mein bohat common pattern hai.

---

# Section 28.4: Built-in Tuple Functions

Tuple ke saath Python ke kuch built-in functions commonly use hote hain.

## `len()`

```python
numbers = (10, 20, 30, 40)

print(len(numbers))
```

Output:

```text
4
```

---

## `max()`

```python
numbers = (10, 50, 20, 40)

print(max(numbers))
```

Output:

```text
50
```

---

## `min()`

```python
numbers = (10, 50, 20, 40)

print(min(numbers))
```

Output:

```text
10
```

---

## `sum()`

```python
numbers = (10, 20, 30)

print(sum(numbers))
```

Output:

```text
60
```

---

## `sorted()`

```python
numbers = (40, 10, 30, 20)

result = sorted(numbers)

print(result)
```

Output:

```text
[10, 20, 30, 40]
```

Important:

`sorted()` **list return karta hai**, tuple nahi.

Agar sorted tuple chahiye:

```python
result = tuple(sorted(numbers))

print(result)
```

Output:

```text
(10, 20, 30, 40)
```

---

## `tuple()`

`tuple()` kisi iterable ko tuple mein convert kar sakta hai.

```python
numbers = [10, 20, 30]

result = tuple(numbers)

print(result)
```

Output:

```text
(10, 20, 30)
```

String par:

```python
result = tuple("ABC")

print(result)
```

Output:

```text
('A', 'B', 'C')
```

---

## `any()` aur `all()`

```python
values = (True, True, False)

print(any(values))
print(all(values))
```

Output:

```text
True
False
```

`any()`:

> Kya kam az kam ek value truthy hai?

`all()`:

> Kya tamam values truthy hain?

---

## Tuple methods

Tuple ke do important methods hain:

```python
count()
index()
```

### `count()`

```python
numbers = (10, 20, 10, 30, 10)

print(numbers.count(10))
```

Output:

```text
3
```

### `index()`

```python
numbers = (10, 20, 30, 40)

print(numbers.index(30))
```

Output:

```text
2
```

`index()` first matching occurrence ka index return karta hai.

---

# Section 28.5: Tuple Are Element-wise Hashable and Equatable

Ye section thoda advanced hai.

Tuple equality **element-by-element** check hoti hai.

Example:

```python
a = (10, 20, 30)
b = (10, 20, 30)

print(a == b)
```

Output:

```text
True
```

Python compare karta hai:

```text
10 == 10
20 == 20
30 == 30
```

Sab equal hain, isliye tuples equal hain.

---

## Order bhi important hai

```python
a = (10, 20, 30)
b = (30, 20, 10)

print(a == b)
```

Output:

```text
False
```

Values same hain, lekin order different hai.

Tuple comparison element-by-element aur order ke mutabiq hoti hai.

---

## Hashable Tuple

Tuple aksar **hashable** hota hai, isliye dictionary key ya set element ban sakta hai — **lekin sirf tab jab tuple ke tamam elements hashable hon**.

Example:

```python
location = ("Level 10", "AHU-001")

data = {
    location: "Running"
}

print(data[location])
```

Output:

```text
Running
```

Yahan tuple dictionary key ban gaya.

---

## Tuple with list is not hashable

Ye:

```python
data = ([10, 20], "AHU")
```

hashable tuple nahi hai, kyun ke iske andar list hai aur list unhashable hai.

```python
my_set = {data}
```

Error dega:

```text
TypeError: unhashable type: 'list'
```

Rule:

```text
Tuple
 ↓
har element hashable?
 ↓
Yes → tuple hashable ho sakta hai
No  → tuple hashable nahi
```

Example hashable:

```python
(10, "AHU", True)
```

Example not hashable:

```python
([10, 20], "AHU")
```

---

# Element-wise Comparison

Tuples ko `<`, `>`, `<=`, `>=` se bhi compare kar sakte hain.

```python
a = (10, 20)
b = (10, 30)

print(a < b)
```

Output:

```text
True
```

Python pehle first elements compare karega:

```text
10 == 10
```

Equal hain, to next elements compare honge:

```text
20 < 30
```

True hai.

Isliye:

```text
(10, 20) < (10, 30)
```

True.

---

# Section 28.6: Indexing Tuples

Tuple ordered hota hai, isliye indexing available hai.

```python
equipment = (
    "AHU-001",
    "Level 10",
    24,
    "Running"
)
```

Index:

```text
Index:     0          1          2          3
Value:   AHU-001   Level 10     24       Running
```

Access:

```python
print(equipment[0])
```

Output:

```text
AHU-001
```

```python
print(equipment[2])
```

Output:

```text
24
```

---

## Negative Indexing

```python
print(equipment[-1])
```

Output:

```text
Running
```

```python
print(equipment[-2])
```

Output:

```text
24
```

Same rule jo lists mein tha:

```text
-1 → last
-2 → second last
-3 → third last
```

---

## Slicing Tuples

Tuple slicing bhi support karta hai.

```python
numbers = (10, 20, 30, 40, 50)

print(numbers[1:4])
```

Output:

```text
(20, 30, 40)
```

Important:

Slicing ka result tuple hota hai.

```python
result = numbers[1:4]

print(type(result))
```

Output:

```text
<class 'tuple'>
```

---

## Step ke saath slicing

```python
numbers = (0, 1, 2, 3, 4, 5)

print(numbers[::2])
```

Output:

```text
(0, 2, 4)
```

Reverse:

```python
print(numbers[::-1])
```

Output:

```text
(5, 4, 3, 2, 1, 0)
```

---

# Section 28.7: Reversing Elements

Tuple ko reverse karne ke liye slicing:

```python
numbers = (10, 20, 30, 40)

reversed_numbers = numbers[::-1]

print(reversed_numbers)
```

Output:

```text
(40, 30, 20, 10)
```

Yahan `[::-1]`:

> Last element se first element ki taraf move karta hai.

---

## `reversed()` Function

Python ka `reversed()` bhi use kar sakte hain:

```python
numbers = (10, 20, 30, 40)

result = reversed(numbers)

print(tuple(result))
```

Output:

```text
(40, 30, 20, 10)
```

Difference:

```python
numbers[::-1]
```

directly new tuple deta hai.

```python
reversed(numbers)
```

reverse iterator deta hai.

Agar tuple chahiye:

```python
tuple(reversed(numbers))
```

---

# `[::-1]` vs `reversed()`

| Method                     | Result           |
| -------------------------- | ---------------- |
| `numbers[::-1]`            | New tuple        |
| `reversed(numbers)`        | Reverse iterator |
| `tuple(reversed(numbers))` | New tuple        |

Example:

```python
numbers = (1, 2, 3, 4)

print(numbers[::-1])
print(tuple(reversed(numbers)))
```

Output:

```text
(4, 3, 2, 1)
(4, 3, 2, 1)
```

---

# Tuple ko Loop karna

Tuple iterable hai:

```python
equipment = ("AHU-001", "AHU-002", "VAV-001")

for item in equipment:
    print(item)
```

Output:

```text
AHU-001
AHU-002
VAV-001
```

`enumerate()` bhi use kar sakte hain:

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

# Tuple kab use karein?

Tuple useful hai jab data ka structure fixed ho.

Example:

```python
equipment = ("AHU-001", "Level 10", 24)
```

Agar ye values ek fixed record ko represent karti hain aur aap nahi chahte ke accidentally elements replace hon, tuple suitable ho sakta hai.

Function return values mein bhi tuple common hai:

```python
def get_temperature():
    return "AHU-001", 24
```

Phir:

```python
equipment_id, temperature = get_temperature()
```

---

# List vs Tuple — Final Comparison

| Feature            | List        | Tuple                         |
| ------------------ | ----------- | ----------------------------- |
| Syntax             | `[1, 2, 3]` | `(1, 2, 3)`                   |
| Ordered            | Yes         | Yes                           |
| Mutable            | Yes         | No                            |
| Indexing           | Yes         | Yes                           |
| Slicing            | Yes         | Yes                           |
| Duplicate values   | Yes         | Yes                           |
| `append()`         | Yes         | No                            |
| `remove()`         | Yes         | No                            |
| `count()`          | Yes         | Yes                           |
| `index()`          | Yes         | Yes                           |
| Can be dict key    | No          | Yes, if all elements hashable |
| Can be set element | No          | Yes, if all elements hashable |

---

# Practice Exercises

## Exercise 1 — Single Tuple

Ek single-element tuple banayein jisme:

```text
AHU-001
```

stored ho.

Check karein:

```python
type(...)
```

---

## Exercise 2 — Unpacking

Ye tuple hai:

```python
equipment = ("AHU-001", "Level 10", 24)
```

Isko teen variables mein unpack karein:

```text
equipment_id
floor
temperature
```

---

## Exercise 3 — Indexing

```python
numbers = (10, 20, 30, 40, 50)
```

Print karein:

* first element
* last element
* third element

---

## Exercise 4 — Reverse

```python
numbers = (10, 20, 30, 40, 50)
```

`[::-1]` use karke reverse karein.

Expected:

```text
(50, 40, 30, 20, 10)
```

---

## Exercise 5 — Hashability

Check karein ke ye tuple dictionary key ban sakta hai:

```python
location = ("Level 10", "AHU-001")
```

Phir ye try karein:

```python
location = (["Level 10"], "AHU-001")
```

Aur difference observe karein.

---

# Chapter 28: Final Mental Model

Tuple ko is tarah yaad rakhein:

```text
Tuple
 ↓
Ordered
 ↓
Indexed
 ↓
Immutable
 ↓
Duplicates allowed
```

Basic:

```python
data = (10, 20, 30)
```

Index:

```python
data[0]
```

→ `10`

Reverse:

```python
data[::-1]
```

→ `(30, 20, 10)`

Unpacking:

```python
a, b, c = data
```

Packing:

```python
data = a, b, c
```

Hashable tuple:

```python
(10, "AHU", True)
```

Non-hashable tuple:

```python
([10, 20], "AHU")
```

**Core idea:** Tuple ek ordered aur immutable collection hai. Jab data ka structure fixed rakhna ho, tuple useful hota hai. Iski indexing, slicing, unpacking aur element-wise comparison bilkul important concepts hain.
