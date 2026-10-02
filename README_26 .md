# Chapter 26: `filter()`

Python ka `filter()` function kisi iterable ke elements mein se sirf woh elements select karta hai jinke liye given condition `True` return karti hai.

Basic syntax:

```python
filter(function, iterable)
```

Yahan:

* `function` → har item par condition check karta hai.
* `iterable` → list, tuple, set ya koi doosra iterable.
* `filter()` → ek **filter object / iterator** return karta hai.

Usually result ko list mein dekhne ke liye:

```python
list(filter(...))
```

use karte hain.

---

# Section 26.1: Basic Use of `filter`

Sab se simple example:

```python
numbers = [1, 2, 3, 4, 5, 6]

def is_even(number):
    return number % 2 == 0

result = filter(is_even, numbers)

print(list(result))
```

Output:

```text
[2, 4, 6]
```

### Step-by-step

Original list:

```text
[1, 2, 3, 4, 5, 6]
```

`filter()` har number ko `is_even()` function mein bhejta hai.

```text
1 → False
2 → True
3 → False
4 → True
5 → False
6 → True
```

Sirf `True` wale elements result mein aate hain:

```text
[2, 4, 6]
```

## Lambda ke saath

Chhoti condition ke liye `lambda` use kar sakte hain:

```python
numbers = [1, 2, 3, 4, 5, 6]

result = filter(lambda x: x % 2 == 0, numbers)

print(list(result))
```

Output:

```text
[2, 4, 6]
```

Yahan:

```python
lambda x: x % 2 == 0
```

ka matlab hai:

> `x` even hai to `True`, warna `False`.

---

## Strings ko filter karna

```python
names = ["Ali", "Ahmed", "Usman", "A"]

result = filter(lambda name: len(name) > 2, names)

print(list(result))
```

Output:

```text
['Ali', 'Ahmed', 'Usman']
```

`"A"` ki length `2` se greater nahi hai, isliye woh remove ho gaya.

---

## HVAC example

Maan lein temperature readings hain:

```python
temperatures = [21, 24, 28, 31, 35]
```

Humein sirf `30` se greater temperatures chahiye:

```python
high_temperatures = filter(
    lambda temp: temp > 30,
    temperatures
)

print(list(high_temperatures))
```

Output:

```text
[31, 35]
```

---

# `filter()` ka result directly print karne par

Ye important hai:

```python
numbers = [1, 2, 3, 4]

result = filter(lambda x: x > 2, numbers)

print(result)
```

Output kuch is type ka hoga:

```text
<filter object at 0x...>
```

Isliye values dekhne ke liye:

```python
print(list(result))
```

Output:

```text
[3, 4]
```

`filter()` immediately normal list return nahi karta. Ye filter object return karta hai jo iterable/iterator ki tarah consume hota hai.

---

# Section 26.2: Filter Without Function

`filter()` mein function ko `None` bhi diya ja sakta hai:

```python
filter(None, iterable)
```

Is case mein Python har element ki **truthiness** check karta hai.

Example:

```python
values = [0, 1, False, True, "", "Hello", None, 5]

result = filter(None, values)

print(list(result))
```

Output:

```text
[1, True, 'Hello', 5]
```

Yahan falsy values remove ho gayi:

```text
0
False
""
None
```

Aur truthy values bach gayi:

```text
1
True
"Hello"
5
```

## Truthy aur Falsy

Common falsy values:

```python
False
None
0
0.0
""
[]
()
{}
set()
```

Baaki bohat si values truthy hoti hain.

Example:

```python
data = ["AHU-001", "", None, "VAV-001", "", "FCU-001"]

clean_data = list(filter(None, data))

print(clean_data)
```

Output:

```text
['AHU-001', 'VAV-001', 'FCU-001']
```

Ye empty strings aur `None` ko remove kar deta hai.

### Important caution

`filter(None, data)` **saari falsy values remove karta hai**.

Agar aap `0` ko preserve karna chahte hain, to `filter(None, ...)` use nahi karna chahiye.

Example:

```python
values = [0, 1, 2, None, 3]

print(list(filter(None, values)))
```

Output:

```text
[1, 2, 3]
```

`0` bhi remove ho gaya.

Agar sirf `None` remove karna ho:

```python
values = [0, 1, 2, None, 3]

result = filter(lambda x: x is not None, values)

print(list(result))
```

Output:

```text
[0, 1, 2, 3]
```

Ye difference bohat important hai.

---

# Section 26.3: Filter as Short-Circuit Check

`filter()` ko kabhi kabhi kisi condition ke matching items ke liye use kiya ja sakta hai.

Lekin yahan ek important concept hai:

**Agar aapko sirf ye check karna hai ke koi item condition satisfy karta hai ya nahi, to `any()` zyada direct hai.**

Example:

```python
numbers = [1, 3, 5, 8, 9]

has_even = any(
    number % 2 == 0
    for number in numbers
)

print(has_even)
```

Output:

```text
True
```

`any()` jaise hi `8` ko find karta hai, us point par result `True` ho sakta hai aur baqi values ko check karne ki zaroorat nahi hoti.

Is behavior ko **short-circuit evaluation** kehte hain.

## `filter()` ke saath comparison

Agar hum likhein:

```python
numbers = [1, 3, 5, 8, 9]

result = filter(lambda x: x % 2 == 0, numbers)

print(list(result))
```

Output:

```text
[8]
```

Yahan hum matching elements obtain kar rahe hain.

Lekin agar question sirf ye hai:

> "Kya koi even number hai?"

to:

```python
any(x % 2 == 0 for x in numbers)
```

zyada suitable hai.

### `filter()` + `next()`

Agar humein **pehla matching element** chahiye, to `filter()` ke saath `next()` useful ho sakta hai.

```python
numbers = [1, 3, 5, 8, 10]

result = filter(lambda x: x % 2 == 0, numbers)

first_even = next(result, None)

print(first_even)
```

Output:

```text
8
```

`next(result, None)` pehla matching value deta hai.

Agar koi match na mile:

```python
numbers = [1, 3, 5]

result = filter(lambda x: x % 2 == 0, numbers)

first_even = next(result, None)

print(first_even)
```

Output:

```text
None
```

Yahan `None` default value hai.

### `any()` vs `filter()`

| Requirement                             | Suitable approach            |
| --------------------------------------- | ---------------------------- |
| Matching items chahiye                  | `filter()`                   |
| Koi item condition satisfy karta hai?   | `any()`                      |
| Sab items condition satisfy karte hain? | `all()`                      |
| Pehla matching item chahiye             | `next(filter(...), default)` |

---

# Section 26.4: Complementary Function: `filterfalse`, `ifilterfalse`

`filter()` condition ke `True` items rakhta hai.

Iska opposite behavior chahiye ho to `filterfalse()` use kar sakte hain.

Modern Python mein:

```python
from itertools import filterfalse
```

Basic syntax:

```python
filterfalse(function, iterable)
```

Example:

```python
from itertools import filterfalse

numbers = [1, 2, 3, 4, 5, 6]

result = filterfalse(
    lambda x: x % 2 == 0,
    numbers
)

print(list(result))
```

Output:

```text
[1, 3, 5]
```

Normal `filter()`:

```python
filter(lambda x: x % 2 == 0, numbers)
```

gives:

```text
[2, 4, 6]
```

`filterfalse()`:

```python
filterfalse(lambda x: x % 2 == 0, numbers)
```

gives:

```text
[1, 3, 5]
```

Yani:

```text
filter      → condition True wale
filterfalse → condition False wale
```

## `filterfalse()` without function

`filter()` ki tarah `filterfalse()` mein bhi `None` use kar sakte hain.

```python
from itertools import filterfalse

values = [0, 1, False, True, "", "Hello", None]

result = filterfalse(None, values)

print(list(result))
```

Output:

```text
[0, False, '', None]
```

Yani:

```python
filter(None, values)
```

truthy values deta hai.

Aur:

```python
filterfalse(None, values)
```

falsy values deta hai.

---

# `ifilterfalse` kya hai?

Aapke book mein `filterfalse, ifilterfalse` dono likhe hain.

Ye Python versions ki wajah se hai.

**Python 3** mein `itertools.filterfalse` use hota hai:

```python
from itertools import filterfalse
```

`ifilterfalse` Python 2 ke context mein tha. Modern Python 3 code mein:

```python
filterfalse
```

use karein.

Isi tarah Python 3 mein built-in `filter()` khud lazy iterator return karta hai, jab ke Python 2 ka behavior different tha.

---

# `filter()` vs List Comprehension

Chapter 21 mein humne list comprehensions padhi thin.

Ye dono equivalent kaam kar sakte hain.

Using `filter()`:

```python
numbers = [1, 2, 3, 4, 5, 6]

even_numbers = list(
    filter(lambda x: x % 2 == 0, numbers)
)

print(even_numbers)
```

Using list comprehension:

```python
numbers = [1, 2, 3, 4, 5, 6]

even_numbers = [
    x for x in numbers
    if x % 2 == 0
]

print(even_numbers)
```

Dono output:

```text
[2, 4, 6]
```

Modern Python code mein list comprehension aksar zyada readable hoti hai, especially jab condition simple ho.

Lekin `filter()` samajhna important hai kyun ke ye functional programming aur Python ke standard library APIs mein commonly milta hai.

---

# Practical Work-Order Example

Maan lein:

```python
work_orders = [
    {"id": "WO-101", "status": "Open"},
    {"id": "WO-102", "status": "Closed"},
    {"id": "WO-103", "status": "Open"},
    {"id": "WO-104", "status": "Cancelled"}
]
```

Sirf open work orders:

```python
open_orders = filter(
    lambda wo: wo["status"] == "Open",
    work_orders
)

print(list(open_orders))
```

Output:

```text
[
    {'id': 'WO-101', 'status': 'Open'},
    {'id': 'WO-103', 'status': 'Open'}
]
```

Agar sirf IDs chahiye:

```python
open_orders = filter(
    lambda wo: wo["status"] == "Open",
    work_orders
)

open_ids = [wo["id"] for wo in open_orders]

print(open_ids)
```

Output:

```text
['WO-101', 'WO-103']
```

---

# Important: `filter()` Iterator Hai

Ye example bohat important hai:

```python
numbers = [1, 2, 3, 4]

result = filter(lambda x: x > 2, numbers)

print(list(result))
print(list(result))
```

Output:

```text
[3, 4]
[]
```

Pehli `list(result)` ne iterator ko consume kar diya.

Isliye second time:

```python
list(result)
```

empty list deta hai.

Agar result ko multiple times use karna ho:

```python
result = list(
    filter(lambda x: x > 2, numbers)
)

print(result)
print(result)
```

Output:

```text
[3, 4]
[3, 4]
```

Ab `result` normal list hai.

---

# Chapter 26: Quick Revision

| Concept         | Example                        | Meaning                     |
| --------------- | ------------------------------ | --------------------------- |
| Basic filter    | `filter(func, data)`           | Condition ke matching items |
| Convert to list | `list(filter(...))`            | Filter result ko list       |
| No function     | `filter(None, data)`           | Truthy values               |
| Opposite filter | `filterfalse(func, data)`      | Condition False wale        |
| Any match       | `any(condition for x in data)` | Koi ek match?               |
| All match       | `all(condition for x in data)` | Sab match?                  |
| First match     | `next(filter(...), None)`      | Pehla matching item         |

## Sab se important difference

```python
filter(lambda x: x > 10, numbers)
```

ka matlab:

> `10` se greater values select karo.

```python
filter(None, values)
```

ka matlab:

> Falsy values hatao aur truthy values rakho.

```python
filterfalse(lambda x: x > 10, numbers)
```

ka matlab:

> Jo values `x > 10` ko satisfy **nahi** kartin, unhein select karo.

---

# Final Mental Model

`filter()` ko simple words mein:

```text
Iterable
   ↓
har item par condition
   ↓
True  → keep
False → skip
   ↓
filtered result
```

Example:

```python
numbers = [10, 15, 20, 25, 30]

result = filter(
    lambda x: x >= 20,
    numbers
)

print(list(result))
```

Output:

```text
[20, 25, 30]
```

**Core idea:**

```python
filter(condition, data)
```

= **data mein se condition pass karne wale items nikaalo.**

Aur opposite:

```python
filterfalse(condition, data)
```

= **condition fail karne wale items nikaalo.**
