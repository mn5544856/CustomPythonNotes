# Chapter 17: Arrays

## Sab se pehle: Python Array kya hai?

Python mein do cheezen alag samajhna bohat important hai:

### 1. `list`

```python
numbers = [10, 20, 30, 40]
```

List mein different types ki values bhi ho sakti hain:

```python
data = [10, "AHU", 25.5, True]
```

### 2. `array.array`

Python ka `array` module **same data type** ki values ka collection banata hai.

```python
from array import array

numbers = array("i", [10, 20, 30, 40])
```

Yahan:

```text
array("i", ...)
```

mein `"i"` **type code** hai.

`"i"` ka matlab integer array hai.

Example:

```python
from array import array

numbers = array("i", [10, 20, 30, 40])

print(numbers)
```

Output:

```text
array('i', [10, 20, 30, 40])
```

### Array ka basic concept

Socho:

```text
List:
[10, 20, 30, 40]

Array:
array('i', [10, 20, 30, 40])
```

Dono mein multiple values hain, lekin `array.array` type-restricted hota hai.

---

# 17.1: Access Individual Elements Through Indexes

Array ke individual elements ko **index** se access kar sakte hain.

Python indexing `0` se start hoti hai.

```python
from array import array

numbers = array("i", [10, 20, 30, 40])

print(numbers[0])
print(numbers[1])
print(numbers[2])
print(numbers[3])
```

Output:

```text
10
20
30
40
```

Index:

```text
Value:    10   20   30   40
Index:     0    1    2    3
```

### Negative indexing

```python
print(numbers[-1])
print(numbers[-2])
```

Output:

```text
40
30
```

`-1` last element hota hai.

### Index ko modify karna

Array mutable hota hai.

```python
numbers[1] = 200

print(numbers)
```

Output:

```text
array('i', [10, 200, 30, 40])
```

Lekin new value same compatible type ki honi chahiye.

---

# 17.2: Basic Introduction to Arrays

Array module import karne ke liye:

```python
from array import array
```

Phir array create karo:

```python
numbers = array("i", [10, 20, 30])
```

## Type Code

Array ka important concept **type code** hai.

Common examples:

| Type code | General meaning |
| --------- | --------------- |
| `"b"`     | signed char     |
| `"B"`     | unsigned char   |
| `"h"`     | signed short    |
| `"i"`     | signed int      |
| `"I"`     | unsigned int    |
| `"l"`     | signed long     |
| `"f"`     | float           |
| `"d"`     | double          |

Beginner ke liye sab se important examples:

```python
array("i", [10, 20, 30])
```

Integer array.

```python
array("f", [10.5, 20.5, 30.5])
```

Float array.

```python
array("d", [10.5, 20.5, 30.5])
```

Double-precision floating-point array.

### Integer array mein string nahi daal sakte

```python
from array import array

numbers = array("i", [10, 20, 30])

numbers.append("AHU")
```

Ye error dega, kyun ke `"i"` integer type ke liye hai.

### Float array

```python
temperatures = array("f", [22.5, 23.5, 24.5])

print(temperatures)
```

Output kuch is tarah hoga:

```text
array('f', [22.5, 23.5, 24.5])
```

Floating-point representation ki wajah se kuch values display mein slightly different nazar aa sakti hain.

---

# 17.3: Append Any Value to the Array Using `append()`

`append()` array ke **end** mein ek value add karta hai.

```python
from array import array

numbers = array("i", [10, 20, 30])

numbers.append(40)

print(numbers)
```

Output:

```text
array('i', [10, 20, 30, 40])
```

Pehle:

```text
10 20 30
```

`append(40)` ke baad:

```text
10 20 30 40
```

### HVAC example

```python
from array import array

temperatures = array("f", [22.5, 23.0, 24.5])

temperatures.append(25.0)

print(temperatures)
```

Yahan new temperature end mein add ho gaya.

### Important

`append()` ek waqt mein **one item** add karta hai.

```python
numbers.append(50)
```

Correct.

---

# 17.4: Insert Value in an Array Using `insert()`

`insert()` kisi specific index par value add karta hai.

Syntax:

```python
array.insert(index, value)
```

Example:

```python
from array import array

numbers = array("i", [10, 20, 40])

numbers.insert(2, 30)

print(numbers)
```

Output:

```text
array('i', [10, 20, 30, 40])
```

Pehle:

```text
Index:  0   1   2
Value: 10  20  40
```

`insert(2, 30)` ke baad:

```text
Index:  0   1   2   3
Value: 10  20  30  40
```

### Beginning mein insert

```python
numbers.insert(0, 5)

print(numbers)
```

Output:

```text
array('i', [5, 10, 20, 30, 40])
```

### End par insert

```python
numbers.insert(len(numbers), 50)
```

Lekin end par value add karne ke liye normally:

```python
numbers.append(50)
```

zyada simple hai.

---

# 17.5: Extend Python Array Using `extend()`

`extend()` multiple values ko array ke end mein add karta hai.

```python
from array import array

numbers = array("i", [10, 20, 30])

numbers.extend([40, 50, 60])

print(numbers)
```

Output:

```text
array('i', [10, 20, 30, 40, 50, 60])
```

### `append()` vs `extend()`

Ye difference yaad rakho:

```python
numbers.append(40)
```

Ek item add karta hai.

```python
numbers.extend([40, 50, 60])
```

Multiple items add karta hai.

Conceptually:

```text
append  → one item
extend  → multiple items
```

### Type restriction

Agar array integer ka hai:

```python
numbers = array("i", [10, 20])

numbers.extend([30, 40])
```

Correct.

Lekin:

```python
numbers.extend([30, "AHU"])
```

Type compatibility issue create karega.

---

# 17.6: Add Items from List into Array Using `fromlist()`

`fromlist()` Python list ke elements ko array mein add karta hai.

```python
from array import array

numbers = array("i", [10, 20])

values = [30, 40, 50]

numbers.fromlist(values)

print(numbers)
```

Output:

```text
array('i', [10, 20, 30, 40, 50])
```

Yahan:

```python
values = [30, 40, 50]
```

normal Python list hai.

Aur:

```python
numbers.fromlist(values)
```

list ke elements array mein add kar deta hai.

### `extend()` aur `fromlist()`

Dono multiple values add kar sakte hain:

```python
numbers.extend([30, 40])
```

aur:

```python
numbers.fromlist([30, 40])
```

Basic use case mein similar result mil sakta hai.

Lekin `fromlist()` specifically **list** ko array mein add karne ke liye designed hai.

---

# 17.7: Remove Any Array Element Using `remove()`

`remove()` specified value ki **first occurrence** remove karta hai.

```python
from array import array

numbers = array("i", [10, 20, 30, 20])

numbers.remove(20)

print(numbers)
```

Output:

```text
array('i', [10, 30, 20])
```

Sirf pehla `20` remove hua.

Pehle:

```text
10 20 30 20
```

Baad mein:

```text
10 30 20
```

### Agar value exist na kare

```python
numbers.remove(100)
```

Agar `100` array mein nahi hai, to `ValueError` aayega.

Safe check:

```python
if 100 in numbers:
    numbers.remove(100)
```

---

# 17.8: Remove Last Array Element Using `pop()`

`pop()` array se element remove karta hai aur removed value return karta hai.

Agar index na diya jaye, to last element remove hota hai.

```python
from array import array

numbers = array("i", [10, 20, 30, 40])

last = numbers.pop()

print(last)
print(numbers)
```

Output:

```text
40
array('i', [10, 20, 30])
```

### Specific index ka element remove karna

```python
numbers = array("i", [10, 20, 30, 40])

value = numbers.pop(1)

print(value)
print(numbers)
```

Output:

```text
20
array('i', [10, 30, 40])
```

Index `1` par `20` tha, is liye woh remove hua.

### `remove()` vs `pop()`

| Method          | Kaam                                                 |
| --------------- | ---------------------------------------------------- |
| `remove(value)` | Value ko remove karta hai                            |
| `pop()`         | Last item remove karke return karta hai              |
| `pop(index)`    | Specific index ka item remove karke return karta hai |

---

# 17.9: Fetch Any Element Through Its Index Using `index()`

`index()` kisi value ka index return karta hai.

```python
from array import array

numbers = array("i", [10, 20, 30, 40])

position = numbers.index(30)

print(position)
```

Output:

```text
2
```

Kyun ke:

```text
Index:  0   1   2   3
Value: 10  20  30  40
```

`30` ka index `2` hai.

### Duplicate values

```python
numbers = array("i", [10, 20, 30, 20])

print(numbers.index(20))
```

Output:

```text
1
```

`index()` first matching occurrence ka index return karta hai.

### Value na mile

```python
numbers.index(100)
```

To `ValueError` aayega.

Safe approach:

```python
if 100 in numbers:
    print(numbers.index(100))
```

---

# 17.10: Reverse a Python Array Using `reverse()`

`reverse()` array ke elements ka order reverse kar deta hai.

```python
from array import array

numbers = array("i", [10, 20, 30, 40])

numbers.reverse()

print(numbers)
```

Output:

```text
array('i', [40, 30, 20, 10])
```

Pehle:

```text
10 20 30 40
```

Baad mein:

```text
40 30 20 10
```

### Important

`reverse()` original array ko modify karta hai.

Ye naya reversed array return karne ke bajaye existing array ko reverse karta hai.

---

# 17.11: Get Array Buffer Information Using `buffer_info()`

`buffer_info()` array ke internal buffer ke baare mein information deta hai.

Example:

```python
from array import array

numbers = array("i", [10, 20, 30, 40])

print(numbers.buffer_info())
```

Output environment ke mutabiq different ho sakta hai, for example:

```text
(12345678, 4)
```

Yahan generally tuple mein:

```text
(address, length)
```

information hoti hai.

* Pehla number: memory buffer ka address
* Doosra number: array mein elements ki count

Example:

```text
(12345678, 4)
```

ka matlab roughly:

```text
buffer address → 12345678
number of elements → 4
```

### Important beginner point

Usually normal Python programming mein tumhein `buffer_info()` ki zaroorat nahi hoti.

Ye low-level memory/buffer related information ke liye useful hai.

Is liye is method ko abhi conceptually samajhna enough hai.

---

# 17.12: Check Number of Occurrences Using `count()`

`count()` batata hai ke koi value array mein kitni baar present hai.

```python
from array import array

numbers = array("i", [10, 20, 20, 30, 20])

print(numbers.count(20))
```

Output:

```text
3
```

Kyun ke `20` teen baar hai.

### Another example

```python
temperatures = array("i", [25, 25, 26, 27, 25])

print(temperatures.count(25))
```

Output:

```text
3
```

### `count()` aur `index()`

```text
count(value)
```

batata hai:

> Value kitni baar hai?

```text
index(value)
```

batata hai:

> First matching value kis index par hai?

---

# 17.13: Convert Array to String Using `tostring()`

Yahan book ka terminology thoda old hai.

Older Python versions mein:

```python
tostring()
```

use hota tha.

Modern Python 3 mein iske equivalent method:

```python
tobytes()
```

hai.

Example:

```python
from array import array

numbers = array("B", [65, 66, 67])

data = numbers.tobytes()

print(data)
```

Output:

```text
b'ABC'
```

Yahan:

```text
65 → A
66 → B
67 → C
```

ASCII/byte representation ki wajah se bytes `b'ABC'` nazar aa rahe hain.

### Important distinction

`tobytes()` **normal Python string (`str`) return nahi karta**.

Ye `bytes` return karta hai.

```python
data = numbers.tobytes()

print(type(data))
```

Output:

```text
<class 'bytes'>
```

Is liye:

```text
array → bytes
```

na ke:

```text
array → str
```

Book agar `tostring()` keh rahi hai, to modern Python 3 mein:

```python
tobytes()
```

yaad rakho.

---

# 17.14: Convert Array to a Python List Using `tolist()`

`tolist()` array ko normal Python `list` mein convert karta hai.

```python
from array import array

numbers = array("i", [10, 20, 30])

my_list = numbers.tolist()

print(my_list)
print(type(my_list))
```

Output:

```text
[10, 20, 30]
<class 'list'>
```

Pehle:

```text
array('i', [10, 20, 30])
```

Conversion ke baad:

```text
[10, 20, 30]
```

### Practical example

```python
from array import array

temperatures = array("f", [22.5, 23.0, 24.5])

temperature_list = temperatures.tolist()

print(temperature_list)
```

Ab `temperature_list` normal Python list hai.

### Kab useful hai?

Agar kisi function ko specifically Python `list` chahiye, to:

```python
array_data.tolist()
```

use kar sakte ho.

---

# 17.15: Append a String to Char Array Using `fromstring()`

Ye section bhi old Python terminology use karta hai.

Older Python versions mein:

```python
fromstring()
```

use hota tha.

Modern Python 3 mein iska replacement:

```python
frombytes()
```

hai.

## Character/byte array

Example:

```python
from array import array

letters = array("b")

letters.frombytes(b"ABC")

print(letters)
```

Output conceptually:

```text
array('b', [65, 66, 67])
```

Yahan:

```text
A → 65
B → 66
C → 67
```

### `frombytes()` kya karta hai?

Ye bytes ko array ke elements mein add karta hai.

```text
bytes
  ↓
frombytes()
  ↓
array
```

Aur reverse:

```text
array
  ↓
tobytes()
  ↓
bytes
```

### Example

```python
from array import array

letters = array("B")

letters.frombytes(b"ABC")

print(letters)
print(letters.tobytes())
```

Output:

```text
array('B', [65, 66, 67])
b'ABC'
```

---

# `tostring()` vs `tobytes()`

Book mein agar tum dekho:

```python
array.tostring()
```

to modern Python 3 mein use:

```python
array.tobytes()
```

samjho.

Similarly:

```python
array.fromstring(...)
```

ka modern Python 3 equivalent:

```python
array.frombytes(...)
```

hai.

| Old terminology | Modern Python 3 |
| --------------- | --------------- |
| `tostring()`    | `tobytes()`     |
| `fromstring()`  | `frombytes()`   |

Ye difference important hai kyun ke old books/examples mein `tostring()` aur `fromstring()` mil sakte hain.

---

# Array ke Important Methods — Complete Revision

Ab chapter ke methods ko ek table mein dekho:

| Method             | Kaam                                               |
| ------------------ | -------------------------------------------------- |
| `append(x)`        | End mein ek value add karta hai                    |
| `insert(i, x)`     | Specific index par value add karta hai             |
| `extend(iterable)` | Multiple values add karta hai                      |
| `fromlist(list)`   | List ke elements array mein add karta hai          |
| `remove(x)`        | First matching value remove karta hai              |
| `pop()`            | Last element remove karta hai aur return karta hai |
| `pop(i)`           | Specific index ka element remove karta hai         |
| `index(x)`         | First matching value ka index return karta hai     |
| `reverse()`        | Array ko in-place reverse karta hai                |
| `buffer_info()`    | Internal buffer information deta hai               |
| `count(x)`         | Value ki occurrences count karta hai               |
| `tobytes()`        | Array ko bytes mein convert karta hai              |
| `tolist()`         | Array ko Python list mein convert karta hai        |
| `frombytes()`      | Bytes ko array mein add karta hai                  |

---

# Array ka Complete Practical Example

Ab ek hi example mein kai methods use karte hain:

```python
from array import array

temperatures = array("i", [22, 23, 24])

print("Original:", temperatures)

temperatures.append(25)
print("After append:", temperatures)

temperatures.insert(1, 21)
print("After insert:", temperatures)

temperatures.extend([26, 27])
print("After extend:", temperatures)

print("Index of 24:", temperatures.index(24))

print("Count of 25:", temperatures.count(25))

removed = temperatures.pop()
print("Removed:", removed)
print("After pop:", temperatures)

temperatures.reverse()
print("After reverse:", temperatures)

temperature_list = temperatures.tolist()
print("As list:", temperature_list)
```

Possible output:

```text
Original: array('i', [22, 23, 24])
After append: array('i', [22, 23, 24, 25])
After insert: array('i', [22, 21, 23, 24, 25])
After extend: array('i', [22, 21, 23, 24, 25, 26, 27])
Index of 24: 3
Count of 25: 1
Removed: 27
After pop: array('i', [22, 21, 23, 24, 25, 26])
After reverse: array('i', [26, 25, 24, 23, 21, 22])
As list: [26, 25, 24, 23, 21, 22]
```

---

# Array vs List — Sabse Important Difference

Beginner ke liye ye distinction yaad rakhna bohat zaroori hai.

### List

```python
data = [10, 20, "AHU", 25.5]
```

Different types rakh sakti hai.

### Array

```python
from array import array

data = array("i", [10, 20, 30])
```

Specified type ke elements rakhta hai.

| Feature              | `list` | `array.array` |
| -------------------- | ------ | ------------- |
| Different data types | Haan   | Normally nahi |
| Indexing             | Haan   | Haan          |
| Mutable              | Haan   | Haan          |
| `append()`           | Haan   | Haan          |
| `insert()`           | Haan   | Haan          |
| `remove()`           | Haan   | Haan          |
| `pop()`              | Haan   | Haan          |
| `reverse()`          | Haan   | Haan          |
| `count()`            | Haan   | Haan          |
| `index()`            | Haan   | Haan          |
| `tolist()`           | N/A    | Haan          |
| `buffer_info()`      | N/A    | Haan          |
| Type restriction     | Nahi   | Haan          |

---

# Important Mental Model

Array ko is tarah yaad rakho:

```text
from array import array
        ↓
array("i", [10, 20, 30])
        ↓
   integer array
```

Phir:

```text
append()     → end mein add
insert()     → specific position par add
extend()     → multiple values add
fromlist()   → list → array
remove()     → value remove
pop()        → index/last item remove + return
index()      → value ka index
reverse()    → order reverse
count()      → occurrence count
tolist()     → array → list
tobytes()    → array → bytes
frombytes()  → bytes → array
buffer_info()→ internal buffer information
```

## Sabse Important Modern Python 3 Note

Book purani terminology use kar sakti hai:

```python
tostring()
fromstring()
```

Modern Python 3 mein:

```python
tobytes()
frombytes()
```

use karo.

Is chapter ka core idea ye hai:

> **`array.array` ek mutable, indexed, type-restricted collection hai jo same type ke primitive values ko efficiently store kar sakta hai.**
