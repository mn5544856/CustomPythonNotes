# Chapter 23: `groupby()`

Python mein `groupby()` function `itertools` module ka part hai.

Iska use data ko kisi common key ke mutabiq groups mein divide karne ke liye hota hai.

Import:

```python
from itertools import groupby
```

Basic syntax:

```python
groupby(iterable, key=None)
```

* `iterable`: list, tuple ya koi doosra iterable.
* `key`: optional function jo batati hai ke items ko kis basis par group karna hai.

**Important:** `groupby()` sirf ek jaisi consecutive values ko ek group mein rakhta hai. Agar same values list mein alag-alag jagah par hon, to woh separate groups ban sakti hain.

---

# Section 23.1: Example 4 — Basic Grouping

Sab se pehle simple example dekhte hain.

```python
from itertools import groupby

numbers = [1, 1, 2, 2, 2, 3, 1, 1]

for key, group in groupby(numbers):
    print(key, list(group))
```

Output:

```text
1 [1, 1]
2 [2, 2, 2]
3 [3]
1 [1, 1]
```

### Step-by-step explanation

`groupby(numbers)` list ke consecutive equal elements ko group karta hai.

Pehla group:

```python
1 [1, 1]
```

Doosra group:

```python
2 [2, 2, 2]
```

Teesra group:

```python
3 [3]
```

Aakhri mein `1` dobara aata hai. Kyun ke woh pehle wale `1` ke saath consecutive nahi hai, isliye naya group banta hai.

<box border={{size:1,color:"#16a34a"}} background="surface" radius="lg" padding={3} gap={1}>
**Yaad rakhein:** `groupby()` poori list mein same values dhoond kar ek group nahi banata. Ye sirf adjacent, yani saath-saath aane wali values ko group karta hai. </box>

## Sorting ke saath `groupby()`

Agar aap chahte hain ke same values ek hi group mein aayen, to pehle data sort kar sakte hain.

```python
from itertools import groupby

numbers = [1, 1, 2, 2, 2, 3, 1, 1]

numbers.sort()

for key, group in groupby(numbers):
    print(key, list(group))
```

Output:

```text
1 [1, 1, 1, 1]
2 [2, 2, 2]
3 [3]
```

Sorting ke baad same values ek saath aa gayi hain, isliye har unique value ka ek group bana.

---

# Section 23.2: Example 2 — Grouping with a Key Function

`groupby()` ka `key` parameter use karke hum complex data ko kisi specific property ke mutabiq group kar sakte hain.

Example: Work orders ko status ke mutabiq group karna.

```python
from itertools import groupby

work_orders = [
    {"id": "WO-101", "status": "Open"},
    {"id": "WO-102", "status": "Open"},
    {"id": "WO-103", "status": "Closed"},
    {"id": "WO-104", "status": "Closed"},
    {"id": "WO-105", "status": "Open"}
]

for status, group in groupby(
    work_orders,
    key=lambda item: item["status"]
):
    print(status, list(group))
```

Output:

```text
Open [{'id': 'WO-101', 'status': 'Open'},
      {'id': 'WO-102', 'status': 'Open'}]

Closed [{'id': 'WO-103', 'status': 'Closed'},
        {'id': 'WO-104', 'status': 'Closed'}]

Open [{'id': 'WO-105', 'status': 'Open'}]
```

Yahan `lambda item: item["status"]` har work order ka status return karta hai.

Lekin aakhri `Open` pehle `Open` group ke saath nahi mila, kyun ke beech mein `Closed` work orders thay.

## Key function ke saath sorting

Agar har status ke work orders ek hi group mein chahiye, to status ke mutabiq sort karein.

```python
from itertools import groupby

work_orders = [
    {"id": "WO-101", "status": "Open"},
    {"id": "WO-102", "status": "Open"},
    {"id": "WO-103", "status": "Closed"},
    {"id": "WO-104", "status": "Closed"},
    {"id": "WO-105", "status": "Open"}
]

work_orders.sort(key=lambda item: item["status"])

for status, group in groupby(
    work_orders,
    key=lambda item: item["status"]
):
    print(status)

    for work_order in group:
        print(" ", work_order["id"])
```

Output:

```text
Closed
  WO-103
  WO-104
Open
  WO-101
  WO-102
  WO-105
```

Ab pehle `Closed` aur phir `Open` ke work orders hain.

**Note:** `sort()` original list ko modify karta hai. Agar original order preserve karna ho, to `sorted()` use karein:

```python
sorted_orders = sorted(
    work_orders,
    key=lambda item: item["status"]
)
```

## HVAC example: Equipment ko floor ke mutabiq group karna

```python
from itertools import groupby

equipment = [
    {"id": "AHU-01", "floor": "Level 1"},
    {"id": "AHU-02", "floor": "Level 1"},
    {"id": "AHU-03", "floor": "Level 2"},
    {"id": "AHU-04", "floor": "Level 2"},
    {"id": "AHU-05", "floor": "Level 1"}
]

equipment.sort(key=lambda item: item["floor"])

for floor, group in groupby(
    equipment,
    key=lambda item: item["floor"]
):
    print(floor)

    for item in group:
        print(" ", item["id"])
```

Output:

```text
Level 1
  AHU-01
  AHU-02
  AHU-05
Level 2
  AHU-03
  AHU-04
```

Is example mein equipment floor ke mutabiq group hua hai.

---

# Section 23.3: Example 3 — Counting Items in Groups

`groupby()` se har group mein items ki quantity bhi count kar sakte hain.

Example:

```python
from itertools import groupby

statuses = [
    "Open",
    "Open",
    "Closed",
    "Closed",
    "Closed",
    "Open"
]

for status, group in groupby(statuses):
    count = len(list(group))
    print(status, count)
```

Output:

```text
Open 2
Closed 3
Open 1
```

Yahan phir se `Open` do groups mein aaya hai, kyun ke values consecutive nahi thin.

Agar total count har status ka chahiye, to pehle sort karna hoga:

```python
from itertools import groupby

statuses = [
    "Open",
    "Open",
    "Closed",
    "Closed",
    "Closed",
    "Open"
]

statuses.sort()

for status, group in groupby(statuses):
    count = len(list(group))
    print(status, count)
```

Output:

```text
Closed 3
Open 3
```

## `groupby()` ke iterator ka important behavior

`groupby()` se milne wala `group` ek iterator hota hai. Iska data consume ho sakta hai.

Example:

```python
from itertools import groupby

numbers = [1, 1, 2, 2, 3]

for key, group in groupby(numbers):
    print(key)

    for item in group:
        print(item)
```

Output:

```text
1
1
1
2
2
2
3
3
```

Har group ko loop ke andar consume kiya ja raha hai.

Agar aap group ko baad mein use karna chahte hain, to usay foran list mein convert karein:

```python
groups = []

for key, group in groupby(numbers):
    groups.append((key, list(group)))

print(groups)
```

Output:

```text
[(1, [1, 1]), (2, [2, 2]), (3, [3])]
```

---

# `groupby()` aur `Counter` mein difference

Dono grouping ya counting ke kaam aa sakte hain, lekin unka behavior different hai.

| Feature                      | `groupby()`               | `Counter`                           |
| ---------------------------- | ------------------------- | ----------------------------------- |
| Consecutive values ke groups | Haan                      | Nahi                                |
| Same values ka total count   | Sorting ke baad aasani se | Direct                              |
| Original order ka asar       | Haan                      | Nahi                                |
| Output                       | Groups ka iterator        | Value-count dictionary jaisa object |
| Custom key function          | Haan                      | Directly nahi                       |

Example using `Counter`:

```python
from collections import Counter

statuses = [
    "Open",
    "Open",
    "Closed",
    "Closed",
    "Closed",
    "Open"
]

print(Counter(statuses))
```

Output:

```text
Counter({'Open': 3, 'Closed': 3})
```

Agar aapko sirf har status ki total quantity chahiye, to `Counter` convenient hai. Agar consecutive items ke groups process karne hain, to `groupby()` useful hai.

---

# Practice Exercises

## Exercise 1

Is list ko `groupby()` se group karein:

```python
numbers = [2, 2, 3, 3, 3, 4, 2, 2]
```

Har group ki key aur items print karein.

Expected output:

```text
2 [2, 2]
3 [3, 3, 3]
4 [4]
2 [2, 2]
```

## Exercise 2

Work orders ko status ke mutabiq group karein:

```python
work_orders = [
    {"id": "WO-201", "status": "Open"},
    {"id": "WO-202", "status": "Closed"},
    {"id": "WO-203", "status": "Open"},
    {"id": "WO-204", "status": "Closed"}
]
```

Pehle status ke mutabiq sort karein, phir `groupby()` use karein.

## Exercise 3

Equipment ko floor ke mutabiq group karein aur har floor par equipment ki quantity print karein.

```python
equipment = [
    {"id": "AHU-01", "floor": "Level 1"},
    {"id": "AHU-02", "floor": "Level 2"},
    {"id": "AHU-03", "floor": "Level 1"},
    {"id": "AHU-04", "floor": "Level 1"}
]
```

---

# Chapter 23: Final Summary

* `groupby()` `itertools` module mein hota hai.
* Ye consecutive items ko groups mein divide karta hai.
* `key` function decide karta hai ke grouping kis property par hogi.
* Agar same values ek group mein chahiye hon, to aksar pehle `sorted()` ya `list.sort()` karna hota hai.
* `groupby()` se milne wala group iterator hota hai; zaroorat par `list(group)` karein.
* Sirf total frequency count karni ho to `Counter` bhi useful hai.

**Sab se important baat:** `groupby()` ko database ke `GROUP BY` jaisa samajhne se pehle yaad rakhein ke Python ka `groupby()` default taur par sirf consecutive items ko group karta hai.
