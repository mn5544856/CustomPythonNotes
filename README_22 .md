# Chapter 22: List Slicing (Selecting Parts of Lists)

Python mein **slicing** ka use list ke kisi specific part ko select karne ke liye hota hai.

Example:

```python
numbers = [10, 20, 30, 40, 50, 60]

print(numbers[1:4])
```

Output:

```text
[20, 30, 40]
```

Yahan `1:4` ka matlab hai index `1` se start karo aur index `4` se pehle ruk jao.

Slicing ka basic syntax:

```python
my_list[start:stop:step]
```

| Parameter | Meaning                                       |
| --------- | --------------------------------------------- |
| `start`   | Kis index se start karna hai                  |
| `stop`    | Kis index se pehle rukna hai                  |
| `step`    | Kitne index ke gap se items select karne hain |

Teeno parameters optional hain.

---

# Section 22.1: Using the Third "Step" Argument

Slicing ka third argument `step` hota hai.

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(numbers[::2])
```

Output:

```text
[0, 2, 4, 6, 8]
```

`step = 2` ka matlab hai har doosra element select karo.

### Step 1: Step 1

```python
numbers = [0, 1, 2, 3, 4, 5]

print(numbers[::1])
```

Output:

```text
[0, 1, 2, 3, 4, 5]
```

`step = 1` mein har element select hota hai.

### Step 2: Step 2

```python
print(numbers[::2])
```

Output:

```text
[0, 2, 4]
```

Indexes:

```text
Index:   0  1  2  3  4  5
Value:   0  1  2  3  4  5
         ↑     ↑     ↑
```

### Step 3: Step 3

```python
print(numbers[::3])
```

Output:

```text
[0, 3]
```

Indexes `0` aur `3` select hue.

### Start aur step ek saath

```python
numbers = [10, 20, 30, 40, 50, 60, 70]

print(numbers[1::2])
```

Output:

```text
[20, 40, 60]
```

Explanation:

* `start = 1`: index 1 se start.
* `stop` omitted: list ke end tak.
* `step = 2`: har doosra index.

### Start, stop aur step ek saath

```python
numbers = [10, 20, 30, 40, 50, 60, 70]

print(numbers[1:6:2])
```

Output:

```text
[20, 40, 60]
```

Selected indexes:

```text
1, 3, 5
```

Index `6` include nahi hoga.

### Negative step

Negative `step` ka matlab reverse direction mein move karna hai.

```python
numbers = [10, 20, 30, 40, 50, 60]

print(numbers[::-1])
```

Output:

```text
[60, 50, 40, 30, 20, 10]
```

Negative step ke saath start aur stop bhi specify kar sakte hain:

```python
print(numbers[5:1:-1])
```

Output:

```text
[60, 50, 40, 30]
```

Yahan:

* `start = 5`: last index se start.
* `stop = 1`: index 1 se pehle rukna.
* `step = -1`: peeche ki taraf move karna.

### Negative step ke saath important rule

```python
numbers = [10, 20, 30, 40, 50]
```

Ye:

```python
print(numbers[4:1:-1])
```

Output:

```text
[50, 40, 30]
```

Lekin:

```python
print(numbers[1:4:-1])
```

Output:

```text
[]
```

Kyun ke `start = 1` se peeche jaate hue `stop = 4` tak pahunchna possible nahi.

**Yaad rakhein:** Positive step aage move karta hai aur negative step peeche.

---

# Section 22.2: Selecting a Sublist from a List

Slicing ka sab se common use list ka specific portion select karna hai.

```python
equipment = [
    "AHU-001",
    "AHU-002",
    "AHU-003",
    "AHU-004",
    "AHU-005"
]
```

### First three elements

```python
print(equipment[0:3])
```

Output:

```text
['AHU-001', 'AHU-002', 'AHU-003']
```

### Index 2 se index 4 tak

```python
print(equipment[2:5])
```

Output:

```text
['AHU-003', 'AHU-004', 'AHU-005']
```

`stop` index `5` hai, lekin woh include nahi hota.

### Start omitted

```python
print(equipment[:3])
```

Output:

```text
['AHU-001', 'AHU-002', 'AHU-003']
```

Start omit karne par slicing beginning se start hoti hai.

### Stop omitted

```python
print(equipment[2:])
```

Output:

```text
['AHU-003', 'AHU-004', 'AHU-005']
```

Stop omit karne par list ke end tak select hota hai.

### Dono omitted

```python
print(equipment[:])
```

Output:

```text
['AHU-001', 'AHU-002', 'AHU-003', 'AHU-004', 'AHU-005']
```

`equipment[:]` ek shallow copy banata hai.

```python
copy_equipment = equipment[:]

copy_equipment[0] = "AHU-999"

print(equipment)
print(copy_equipment)
```

Output:

```text
['AHU-001', 'AHU-002', 'AHU-003', 'AHU-004', 'AHU-005']
['AHU-999', 'AHU-002', 'AHU-003', 'AHU-004', 'AHU-005']
```

Original list change nahi hui.

Lekin nested lists ke case mein shallow copy ke andar wali lists shared ho sakti hain.

### Negative indexes se sublist

```python
numbers = [10, 20, 30, 40, 50, 60]

print(numbers[-4:-1])
```

Output:

```text
[30, 40, 50]
```

Negative indexing mein:

* `-1` last element
* `-2` second-last
* `-3` third-last

### Practical example: Work orders

```python
work_orders = [
    "WO-1001",
    "WO-1002",
    "WO-1003",
    "WO-1004",
    "WO-1005",
    "WO-1006"
]
```

Pehle 3 work orders:

```python
first_three = work_orders[:3]
```

Last 2 work orders:

```python
last_two = work_orders[-2:]
```

Beech ke work orders:

```python
middle = work_orders[2:4]
```

Slicing original list ko modify nahi karti. Ye selected elements ki new list return karti hai.

---

# Section 22.3: Reversing a List with Slicing

Slicing se list reverse karne ka sab se simple tareeqa:

```python
numbers = [10, 20, 30, 40, 50]

reversed_numbers = numbers[::-1]

print(reversed_numbers)
```

Output:

```text
[50, 40, 30, 20, 10]
```

`[::-1]` ka matlab:

* Start omitted: reverse direction ke mutabiq end se start.
* Stop omitted: beginning tak.
* Step `-1`: ek ek index peeche.

### Original list change nahi hoti

```python
numbers = [1, 2, 3, 4]

reversed_numbers = numbers[::-1]

print(numbers)
print(reversed_numbers)
```

Output:

```text
[1, 2, 3, 4]
[4, 3, 2, 1]
```

Original list same rehti hai.

### `reverse()` ke saath comparison

```python
numbers = [1, 2, 3, 4]

numbers.reverse()

print(numbers)
```

Output:

```text
[4, 3, 2, 1]
```

Difference:

| Method              | Behavior                           |
| ------------------- | ---------------------------------- |
| `numbers[::-1]`     | New reversed list return karta hai |
| `numbers.reverse()` | Original list ko modify karta hai  |
| `reversed(numbers)` | Reverse iterator return karta hai  |

Agar original list ko preserve karna hai, slicing useful hai.

### HVAC example

```python
temperatures = [22, 23, 24, 25, 26]

latest_first = temperatures[::-1]

print(latest_first)
```

Output:

```text
[26, 25, 24, 23, 22]
```

Agar readings chronological order mein hain, to slicing se unka reverse order mil sakta hai.

Lekin yaad rahe, ye sirf list ka order reverse karta hai. Ye timestamps ko sort ya validate nahi karta.

---

# Section 22.4: Shifting a List Using Slicing

List shifting ka matlab elements ko ek ya zyada positions aage ya peeche move karna hai.

Example:

```python
numbers = [1, 2, 3, 4, 5]
```

Humein list ko right side par ek position shift karna hai, aur last element ko beginning mein lana hai.

Expected result:

```text
[5, 1, 2, 3, 4]
```

### Right shift by one

```python
numbers = [1, 2, 3, 4, 5]

shifted = numbers[-1:] + numbers[:-1]

print(shifted)
```

Output:

```text
[5, 1, 2, 3, 4]
```

Isko step-by-step samjhein.

Pehla slice:

```python
numbers[-1:]
```

Output:

```text
[5]
```

Doosra slice:

```python
numbers[:-1]
```

Output:

```text
[1, 2, 3, 4]
```

Dono lists concatenate:

```python
[5] + [1, 2, 3, 4]
```

Result:

```text
[5, 1, 2, 3, 4]
```

### Left shift by one

Ab list ko left side par ek position shift karte hain.

Expected result:

```text
[2, 3, 4, 5, 1]
```

Code:

```python
numbers = [1, 2, 3, 4, 5]

shifted = numbers[1:] + numbers[:1]

print(shifted)
```

Output:

```text
[2, 3, 4, 5, 1]
```

Step-by-step:

```python
numbers[1:]
```

Result:

```text
[2, 3, 4, 5]
```

Aur:

```python
numbers[:1]
```

Result:

```text
[1]
```

Combine:

```python
[2, 3, 4, 5] + [1]
```

Final result:

```text
[2, 3, 4, 5, 1]
```

### Right shift by two

```python
numbers = [1, 2, 3, 4, 5]

shifted = numbers[-2:] + numbers[:-2]

print(shifted)
```

Output:

```text
[4, 5, 1, 2, 3]
```

Yahan last two elements beginning mein aa gaye.

### Left shift by two

```python
numbers = [1, 2, 3, 4, 5]

shifted = numbers[2:] + numbers[:2]

print(shifted)
```

Output:

```text
[3, 4, 5, 1, 2]
```

### Shift ka general formula

List ki length `n` ho aur `k` positions shift karni hon:

Right shift:

```python
shifted = items[-k:] + items[:-k]
```

Left shift:

```python
shifted = items[k:] + items[:k]
```

Ye formulas tab straightforward hain jab `k` zero se bara ho aur list empty na ho.

### Safe shifting function

Agar shift amount list ki length se zyada ho, to modulo (`%`) se normalize kar sakte hain.

```python
def shift_right(items, steps):
    if not items:
        return []

    steps %= len(items)

    return items[-steps:] + items[:-steps]
```

Example:

```python
numbers = [1, 2, 3, 4, 5]

print(shift_right(numbers, 2))
print(shift_right(numbers, 7))
```

Output:

```text
[4, 5, 1, 2, 3]
[4, 5, 1, 2, 3]
```

`7 % 5 = 2`, isliye 7 positions ka right shift, 2 positions ke shift ke equivalent hai.

**Important:** Is function mein `steps = 0` ho to `items[-0:]` poori list deta hai aur `items[:-0]` empty list. Result phir bhi original list hoti hai.

### Empty list

```python
numbers = []

shifted = numbers[-1:] + numbers[:-1]

print(shifted)
```

Output:

```text
[]
```

Slicing empty list par bhi valid hai.

### Original list preserve karna

```python
numbers = [1, 2, 3, 4, 5]

shifted = numbers[-1:] + numbers[:-1]

print(numbers)
print(shifted)
```

Output:

```text
[1, 2, 3, 4, 5]
[5, 1, 2, 3, 4]
```

`shifted` new list hai. Original `numbers` modify nahi hui.

Agar original list ko modify karna ho:

```python
numbers[:] = numbers[-1:] + numbers[:-1]
```

Ab original list ke contents replace ho jayenge.

---

# Chapter 22: Quick Revision

| Operation         | Code                      | Result           |
| ----------------- | ------------------------- | ---------------- |
| Every second item | `items[::2]`              | Index 0, 2, 4... |
| Sublist           | `items[1:4]`              | Index 1, 2, 3    |
| Beginning se      | `items[:3]`               | First 3 items    |
| End tak           | `items[2:]`               | Index 2 se end   |
| Last two          | `items[-2:]`              | Last 2 items     |
| Reverse           | `items[::-1]`             | Reverse order    |
| Right shift 1     | `items[-1:] + items[:-1]` | Last item first  |
| Left shift 1      | `items[1:] + items[:1]`   | First item last  |
| Right shift 2     | `items[-2:] + items[:-2]` | Last 2 first     |
| Left shift 2      | `items[2:] + items[:2]`   | First 2 last     |

## Important rules

1. Slicing mein `stop` index include nahi hota.
2. Positive `step` aage move karta hai.
3. Negative `step` peeche move karta hai.
4. `step = 0` invalid hai aur `ValueError` deta hai.
5. Slicing new list return karti hai.
6. `items[:]` shallow copy banata hai.
7. Shifting mein `+` do slices ko concatenate karta hai.

---

# Practice Exercises

### Exercise 1: Step

```python
numbers = [10, 20, 30, 40, 50, 60, 70, 80]
```

Sirf index `0`, `2`, `4`, `6` ke elements slicing se select karein.

Expected output:

```text
[10, 30, 50, 70]
```

### Exercise 2: Sublist

```python
equipment = [
    "AHU-001",
    "AHU-002",
    "AHU-003",
    "AHU-004",
    "AHU-005",
    "AHU-006"
]
```

Index `2` se `4` tak ke elements select karein.

Expected output:

```text
['AHU-003', 'AHU-004']
```

### Exercise 3: Reverse

```python
work_orders = ["WO-101", "WO-102", "WO-103", "WO-104"]
```

Slicing use karke list reverse karein.

Expected output:

```text
['WO-104', 'WO-103', 'WO-102', 'WO-101']
```

### Exercise 4: Right shift

```python
numbers = [1, 2, 3, 4, 5, 6]
```

Slicing use karke right shift by 2 karein.

Expected output:

```text
[5, 6, 1, 2, 3, 4]
```

### Exercise 5: Left shift

```python
numbers = [1, 2, 3, 4, 5, 6]
```

Slicing use karke left shift by 3 karein.

Expected output:

```text
[4, 5, 6, 1, 2, 3]
```

---

# Final Mental Model

List slicing ka syntax:

```python
items[start:stop:step]
```

Isko is tarah yaad rakhein:

* `start` — kahan se shuru karna hai.
* `stop` — kahan rukna hai; ye index include nahi hota.
* `step` — kitne gap se move karna hai.

Examples:

```python
items[1:5:2]   # Start 1, stop before 5, step 2
items[::-1]    # Reverse
items[1:]      # First element ke baad se end tak
items[:-1]     # Last element ke baghair
items[-2:]     # Last 2 elements
```

Slicing sirf list ka part select karne ke liye nahi, balki **reverse, copy aur shift** karne ke liye bhi useful hai.
