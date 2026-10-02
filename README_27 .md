# Chapter 27: `heapq`

Python mein `heapq` ek built-in module hai jo **heap queue**, yani **priority queue**, implement karne ke liye use hota hai.

Import:

```python
import heapq
```

`heapq` ka naam:

```text
heap + queue
```

se bana hai.

Is module ka important concept hai:

> **Min-heap**

Python ka `heapq` by default **min-heap** maintain karta hai.

Iska matlab heap ka smallest element root/first position par hota hai.

---

# Heap kya hota hai?

Heap ek special data structure hai jisme elements ko aise arrange kiya jata hai ke minimum ya maximum priority wala element efficiently access kiya ja sake.

Python ka `heapq` **min-heap** use karta hai.

Example:

```python
import heapq

numbers = [5, 2, 8, 1, 3]

heapq.heapify(numbers)

print(numbers)
```

Output exact sorted list nahi hoti. Example output:

```text
[1, 2, 8, 5, 3]
```

Important baat:

```text
numbers[0]
```

smallest element hoga:

```python
print(numbers[0])
```

Output:

```text
1
```

Heap ka matlab ye **nahi** hai ke poori list sorted hoti hai.

Heap ka important rule hai:

```text
smallest element → index 0
```

---

# Section 27.1: Largest and Smallest Items in a Collection

`heapq` mein `nlargest()` aur `nsmallest()` functions available hain.

Import:

```python
import heapq
```

Syntax:

```python
heapq.nlargest(n, iterable)
heapq.nsmallest(n, iterable)
```

Yahan:

* `n` → kitne items chahiye.
* `iterable` → list, tuple, set etc.

---

## `nsmallest()`

Example:

```python
import heapq

numbers = [10, 5, 8, 20, 3, 15]

result = heapq.nsmallest(3, numbers)

print(result)
```

Output:

```text
[3, 5, 8]
```

Yahan:

```python
heapq.nsmallest(3, numbers)
```

ka matlab:

> Collection ke 3 smallest elements do.

Result ascending order mein milta hai.

---

## `nlargest()`

Ab largest elements:

```python
import heapq

numbers = [10, 5, 8, 20, 3, 15]

result = heapq.nlargest(3, numbers)

print(result)
```

Output:

```text
[20, 15, 10]
```

Yani:

```text
nlargest(3)
```

→ 3 largest values.

---

## `min()` aur `nsmallest()` mein difference

Agar sirf **ek smallest value** chahiye:

```python
min(numbers)
```

Agar multiple smallest values chahiye:

```python
heapq.nsmallest(3, numbers)
```

Example:

```python
numbers = [10, 5, 8, 20, 3, 15]

print(min(numbers))
print(heapq.nsmallest(3, numbers))
```

Output:

```text
3
[3, 5, 8]
```

Isi tarah:

```python
max(numbers)
```

sirf largest value deta hai.

Aur:

```python
heapq.nlargest(3, numbers)
```

3 largest values deta hai.

---

# Objects ke saath `nlargest()` aur `nsmallest()`

Real-world data mein values aksar dictionaries ya objects ki form mein hoti hain.

Example:

```python
equipment = [
    {"id": "AHU-001", "temperature": 22},
    {"id": "AHU-002", "temperature": 29},
    {"id": "AHU-003", "temperature": 25},
    {"id": "AHU-004", "temperature": 31}
]
```

Humein highest temperature wale 2 equipment chahiye.

```python
import heapq

result = heapq.nlargest(
    2,
    equipment,
    key=lambda item: item["temperature"]
)

print(result)
```

Output:

```text
[
    {'id': 'AHU-004', 'temperature': 31},
    {'id': 'AHU-002', 'temperature': 29}
]
```

Yahan:

```python
key=lambda item: item["temperature"]
```

batata hai ke comparison `temperature` ke basis par karna hai.

---

## Lowest temperature wale 2 equipment

```python
result = heapq.nsmallest(
    2,
    equipment,
    key=lambda item: item["temperature"]
)

print(result)
```

Output:

```text
[
    {'id': 'AHU-001', 'temperature': 22},
    {'id': 'AHU-003', 'temperature': 25}
]
```

Yani:

```text
nsmallest → low values
nlargest   → high values
```

---

# `heapq` aur `sorted()` ka difference

Agar humein poori collection sort karni hai:

```python
sorted(numbers)
```

useful hai.

Agar humein sirf top few items chahiye:

```python
heapq.nsmallest()
heapq.nlargest()
```

useful ho sakte hain.

Example:

```python
numbers = [10, 5, 8, 20, 3, 15]
```

Poora sorted result:

```python
print(sorted(numbers))
```

Output:

```text
[3, 5, 8, 10, 15, 20]
```

Sirf 3 smallest:

```python
print(heapq.nsmallest(3, numbers))
```

Output:

```text
[3, 5, 8]
```

Sirf 3 largest:

```python
print(heapq.nlargest(3, numbers))
```

Output:

```text
[20, 15, 10]
```

**Conceptually:** Agar aapko sirf top/bottom `N` items chahiye aur collection badi hai, heap-based approach useful ho sakti hai; agar poora ordered collection chahiye, `sorted()` zyada natural choice hai.

---

# Section 27.2: Smallest Item in a Collection

`heapq` ka basic min-heap behavior samajhne ke liye `heapify()` important hai.

Example:

```python
import heapq

numbers = [7, 2, 9, 1, 5]

heapq.heapify(numbers)

print(numbers[0])
```

Output:

```text
1
```

`heapify()` existing list ko **in-place min-heap** mein convert karta hai.

```python
heapq.heapify(numbers)
```

ke baad:

```python
numbers[0]
```

smallest element hota hai.

---

# Smallest Item ko Remove Karna: `heappop()`

Heap ka smallest item remove karne ke liye:

```python
heapq.heappop(heap)
```

Example:

```python
import heapq

numbers = [5, 2, 8, 1, 3]

heapq.heapify(numbers)

smallest = heapq.heappop(numbers)

print(smallest)
print(numbers)
```

Output:

```text
1
[2, 3, 8, 5]
```

Pehle:

```text
[1, ...]
```

tha.

`heappop()` ne smallest `1` remove kar diya.

Ab next smallest `2` hai.

```python
print(heapq.heappop(numbers))
```

Output:

```text
2
```

Phir:

```python
print(heapq.heappop(numbers))
```

Output:

```text
3
```

Yani repeatedly `heappop()` karne se values smallest se largest ki taraf nikalti hain.

---

# `heappush()`

Existing heap mein new item add karne ke liye:

```python
heapq.heappush(heap, item)
```

Example:

```python
import heapq

numbers = [2, 5, 8]

heapq.heapify(numbers)

heapq.heappush(numbers, 1)

print(numbers)
print(numbers[0])
```

Output:

```text
[1, 2, 8, 5]
1
```

New value `1` add hui aur heap property maintain hui.

---

# `heappush()` + `heappop()`

Example:

```python
import heapq

heap = []

heapq.heappush(heap, 30)
heapq.heappush(heap, 10)
heapq.heappush(heap, 20)

print(heap)

print(heapq.heappop(heap))
print(heapq.heappop(heap))
print(heapq.heappop(heap))
```

Output:

```text
[10, 30, 20]
10
20
30
```

Heap list visually sorted nahi hai:

```text
[10, 30, 20]
```

Lekin smallest item hamesha:

```python
heap[0]
```

par available hai.

---

# Priority Queue Example

Heap ka ek practical use **priority queue** hai.

Maan lein work orders ki priority:

```text
1 = High
2 = Medium
3 = Low
```

Hum tuple store kar sakte hain:

```python
import heapq

work_orders = []

heapq.heappush(work_orders, (2, "WO-102"))
heapq.heappush(work_orders, (1, "WO-101"))
heapq.heappush(work_orders, (3, "WO-103"))

print(heapq.heappop(work_orders))
```

Output:

```text
(1, 'WO-101')
```

Kyun?

Heap tuple ko pehle element ke basis par compare karta hai:

```text
(1, "WO-101")
(2, "WO-102")
(3, "WO-103")
```

Sabse chhoti priority number `1` hai.

Isliye `WO-101` pehle nikla.

Phir:

```python
print(heapq.heappop(work_orders))
```

Output:

```text
(2, 'WO-102')
```

Phir:

```text
(3, 'WO-103')
```

Ye **priority queue** ka basic concept hai.

---

# `heapq` ka Important Rule

`heapq` by default **min-heap** hai.

Isliye:

```python
heap[0]
```

→ smallest item.

Agar largest item ko priority deni ho to commonly values ko negative ke saath store kiya jata hai.

Example:

```python
import heapq

heap = []

heapq.heappush(heap, -10)
heapq.heappush(heap, -30)
heapq.heappush(heap, -20)

largest = -heapq.heappop(heap)

print(largest)
```

Output:

```text
30
```

Lekin modern code mein sirf top `N` largest values ke liye:

```python
heapq.nlargest()
```

zyada straightforward hai.

---

# Important Methods

| Function                        | Purpose                                   |
| ------------------------------- | ----------------------------------------- |
| `heapq.heapify(list)`           | Existing list ko min-heap banata hai      |
| `heapq.heappush(heap, item)`    | Heap mein item add karta hai              |
| `heapq.heappop(heap)`           | Smallest item remove aur return karta hai |
| `heapq.nsmallest(n, data)`      | `n` smallest items deta hai               |
| `heapq.nlargest(n, data)`       | `n` largest items deta hai                |
| `heapq.heappushpop(heap, item)` | Push + smallest pop efficiently           |
| `heapq.heapreplace(heap, item)` | Smallest ko replace karta hai             |

---

# `heapify()` aur `sorted()` ko confuse na karein

Ye:

```python
numbers = [5, 1, 4, 2, 3]

numbers.sort()

print(numbers)
```

Output:

```text
[1, 2, 3, 4, 5]
```

Ye complete sorting hai.

Lekin:

```python
numbers = [5, 1, 4, 2, 3]

heapq.heapify(numbers)

print(numbers)
```

Output kuch is tarah ho sakta hai:

```text
[1, 2, 4, 5, 3]
```

Ye sorted list nahi hai.

Sirf heap property maintain hoti hai.

Isliye:

```python
heapq.heapify(numbers)
```

ko:

> "list ko sorted karna"

na samjhein.

Isko:

> "list ko min-heap structure mein convert karna"

samjhein.

---

# Practical Example: Highest Temperature

Maan lein:

```python
temperatures = [
    22,
    31,
    27,
    35,
    24,
    29,
    33
]
```

Top 3 highest temperatures:

```python
import heapq

highest = heapq.nlargest(3, temperatures)

print(highest)
```

Output:

```text
[35, 33, 31]
```

Lowest 3:

```python
lowest = heapq.nsmallest(3, temperatures)

print(lowest)
```

Output:

```text
[22, 24, 27]
```

---

# Chapter 27: Final Mental Model

`heapq` ko teen levels par samjhein:

### Level 1 — Top/Bottom items

```python
heapq.nlargest(3, data)
```

→ 3 largest.

```python
heapq.nsmallest(3, data)
```

→ 3 smallest.

### Level 2 — Min-heap

```python
heapq.heapify(data)
```

→ data ko min-heap banata hai.

```python
data[0]
```

→ smallest item.

### Level 3 — Priority Queue

```python
heapq.heappush(heap, item)
heapq.heappop(heap)
```

→ items ko priority ke order mein efficiently add/remove kar sakte hain.

**Core idea:**

```text
heapq = priority-based data structure

min-heap:
        smallest
           ↓
         heap[0]

heappop()
    ↓
smallest item remove
```

Aur agar sirf simple question ho:

> "Collection mein sabse chhota item kaunsa hai?"

to:

```python
min(data)
```

usually enough hai.

Agar:

> "Mujhe 5 smallest items chahiye"

to:

```python
heapq.nsmallest(5, data)
```

useful hai.

Agar:

> "Mujhe priority queue maintain karni hai"

to:

```python
heapq.heappush()
heapq.heappop()
```

important tools hain.
