# Chapter 8: Set

Python mein `set` ek collection type hai jo **unique elements** store karta hai.

Example:

```python
skills = {"Python", "HVAC", "Python", "Power BI"}

print(skills)
```

Output mein `"Python"` sirf ek baar hoga:

```text
{'Python', 'HVAC', 'Power BI'}
```

Set ki main properties:

* duplicates allowed nahi
* indexing nahi hoti
* unordered collection
* mutable
* set ke elements hashable hone chahiye

---

# 8.1 Operations on Sets

Set ke saath kuch important mathematical operations hote hain:

1. Union `|`
2. Intersection `&`
3. Difference `-`
4. Symmetric Difference `^`

Inko practical example se samjho.

## Example sets

```python
python_users = {"Ali", "Ahmed", "Muhammad", "Omar"}

powerbi_users = {"Ahmed", "Muhammad", "Khalid", "Sami"}
```

Ab dono sets mein kuch common aur kuch different users hain.

---

## 1. Union `|`

**Union = dono sets ke saare unique elements.**

```python
all_users = python_users | powerbi_users

print(all_users)
```

Concept:

```text
Python users
     +
Power BI users
     ↓
All unique users
```

Duplicates automatically remove ho jayenge.

Agar:

```text
A = {1, 2, 3}
B = {3, 4, 5}
```

to:

```python
A | B
```

result:

```text
{1, 2, 3, 4, 5}
```

---

## 2. Intersection `&`

**Intersection = jo elements dono sets mein common hain.**

```python
common_users = python_users & powerbi_users

print(common_users)
```

Agar:

```text
A = {1, 2, 3}
B = {3, 4, 5}
```

to:

```python
A & B
```

result:

```text
{3}
```

Mental model:

```text
A
   ┌─────────────┐
   │  common     │
   └─────────────┘
B
```

Yani **common elements**.

---

## 3. Difference `-`

Difference ka matlab:

> Pehle set mein jo hain, lekin doosre set mein nahi.

```python
python_only = python_users - powerbi_users
```

Example:

```text
A = {1, 2, 3}
B = {3, 4, 5}
```

```python
A - B
```

result:

```text
{1, 2}
```

Lekin:

```python
B - A
```

result:

```text
{4, 5}
```

**Order important hai.**

```text
A - B ≠ B - A
```

---

## 4. Symmetric Difference `^`

Iska matlab:

> Dono sets ke elements jo sirf ek set mein hain, common elements nahi.

Example:

```python
A = {1, 2, 3}
B = {3, 4, 5}

print(A ^ B)
```

Result:

```text
{1, 2, 4, 5}
```

`3` remove ho gaya kyun ke wo dono mein common tha.

Mental model:

```text
A only + B only
      ↓
Symmetric Difference
```

---

# 8.2 Get the Unique Elements of a List

Ye `set` ka bohat common practical use hai.

Suppose list mein duplicates hain:

```python
equipment = [
    "AHU-01",
    "VAV-01",
    "AHU-01",
    "FCU-01",
    "VAV-01"
]
```

Humein sirf unique equipment IDs chahiye.

Simply:

```python
unique_equipment = set(equipment)

print(unique_equipment)
```

Result mein har ID sirf ek baar hogi.

Concept:

```text
List
↓
set()
↓
Duplicates removed
↓
Unique elements
```

---

## Set ko dobara list mein convert karna

Agar final result list chahiye:

```python
unique_equipment = list(set(equipment))

print(unique_equipment)
```

Ab `unique_equipment` list hai.

```python
print(type(unique_equipment))
```

Output:

```text
<class 'list'>
```

### Important

Set unordered hota hai, isliye resulting list ka order guaranteed nahi hota.

Agar order bhi maintain karna hai, modern Python mein ek simple approach:

```python
unique_equipment = list(dict.fromkeys(equipment))
```

Isse first occurrence ka order preserve hota hai.

Example:

```python
equipment = [
    "AHU-01",
    "VAV-01",
    "AHU-01",
    "FCU-01",
    "VAV-01"
]

unique_equipment = list(dict.fromkeys(equipment))

print(unique_equipment)
```

Result:

```text
['AHU-01', 'VAV-01', 'FCU-01']
```

---

# 8.3 Set of Sets

Yahan ek important concept hai.

Normally set ke andar mutable `set` nahi rakh sakte.

Ye invalid hai:

```python
outer = {
    {"A", "B"},
    {"C", "D"}
}
```

Kyun?

Because normal `set` **mutable** hota hai aur set ke elements ko hashable hona chahiye.

---

## `frozenset`

Agar set ke andar set jaisa collection rakhna ho, to `frozenset` use kar sakte ho.

`frozenset` = **immutable set**

Example:

```python
group1 = frozenset({"A", "B"})
group2 = frozenset({"C", "D"})

groups = {group1, group2}

print(groups)
```

Yahan:

```text
groups
  ↓
set
 ├── frozenset({"A", "B"})
 └── frozenset({"C", "D"})
```

---

## `set` vs `frozenset`

| Feature                            | `set` | `frozenset` |
| ---------------------------------- | ----- | ----------- |
| Unique elements                    | Yes   | Yes         |
| Mutable                            | Yes   | No          |
| `add()`                            | Yes   | No          |
| `remove()`                         | Yes   | No          |
| Hashable                           | No    | Yes         |
| Set ke andar element ban sakta hai | No    | Yes         |

---

## Practical example

Suppose equipment ke skills ke groups hain:

```python
hvac_skills = frozenset({"HVAC", "BMS"})
electrical_skills = frozenset({"Electrical", "Testing"})

skill_groups = {
    hvac_skills,
    electrical_skills
}
```

Yahan har `frozenset` ek individual group ko represent karta hai.

---

# 8.4 Set Operations using Methods and Builtins

Set operations sirf operators se nahi, **methods** se bhi kar sakte ho.

Example:

```python
A = {1, 2, 3}
B = {3, 4, 5}
```

---

## Union method

Operator:

```python
A | B
```

Method:

```python
A.union(B)
```

Dono same conceptual result dete hain:

```text
{1, 2, 3, 4, 5}
```

---

## Intersection method

Operator:

```python
A & B
```

Method:

```python
A.intersection(B)
```

Result:

```text
{3}
```

---

## Difference method

Operator:

```python
A - B
```

Method:

```python
A.difference(B)
```

Result:

```text
{1, 2}
```

---

## Symmetric difference method

Operator:

```python
A ^ B
```

Method:

```python
A.symmetric_difference(B)
```

Result:

```text
{1, 2, 4, 5}
```

---

# 5. Built-in functions

Set ke saath kuch built-in functions bhi useful hain.

## `len()`

Number of unique elements:

```python
skills = {"Python", "HVAC", "Power BI"}

print(len(skills))
```

Output:

```text
3
```

---

## `max()`

```python
numbers = {10, 20, 30, 40}

print(max(numbers))
```

Output:

```text
40
```

---

## `min()`

```python
print(min(numbers))
```

Output:

```text
10
```

---

## `sum()`

```python
print(sum(numbers))
```

Output:

```text
100
```

Ye numeric sets ke liye useful hai.

---

# 6. Membership testing

`in` bohat useful hai:

```python
skills = {"Python", "HVAC", "Power BI"}

print("Python" in skills)
```

Output:

```text
True
```

Aur:

```python
print("Java" in skills)
```

Output:

```text
False
```

`not in`:

```python
print("Java" not in skills)
```

Output:

```text
True
```

---

# 7. `issubset()`

Check karta hai ke ek set ke **saare elements** doosre set mein hain ya nahi.

```python
A = {1, 2}
B = {1, 2, 3, 4}

print(A.issubset(B))
```

Output:

```text
True
```

Operator bhi hai:

```python
A <= B
```

---

# 8. `issuperset()`

Check karta hai ke first set doosre set ke saare elements contain karta hai ya nahi.

```python
A = {1, 2, 3, 4}
B = {1, 2}

print(A.issuperset(B))
```

Output:

```text
True
```

Operator:

```python
A >= B
```

---

# 9. `isdisjoint()`

Check karta hai ke dono sets mein **koi common element nahi**.

```python
A = {1, 2}
B = {3, 4}

print(A.isdisjoint(B))
```

Output:

```text
True
```

Lekin:

```python
A = {1, 2}
B = {2, 3}

print(A.isdisjoint(B))
```

Output:

```text
False
```

Kyun ke `2` common hai.

---

# 10. Operations ka complete table

```python
A = {1, 2, 3}
B = {3, 4, 5}
```

| Operation            | Operator | Method                      | Result        |
| -------------------- | -------- | --------------------------- | ------------- |
| Union                | `A \| B` | `A.union(B)`                | `{1,2,3,4,5}` |
| Intersection         | `A & B`  | `A.intersection(B)`         | `{3}`         |
| Difference           | `A - B`  | `A.difference(B)`           | `{1,2}`       |
| Symmetric difference | `A ^ B`  | `A.symmetric_difference(B)` | `{1,2,4,5}`   |
| Subset               | `A <= B` | `A.issubset(B)`             | Boolean       |
| Superset             | `A >= B` | `A.issuperset(B)`           | Boolean       |
| Disjoint             | —        | `A.isdisjoint(B)`           | Boolean       |

---

# 8.5 Sets versus Multisets

Ye section thoda conceptual hai.

## Normal Set

Set mein duplicate values allowed nahi hoti.

```python
numbers = {1, 2, 2, 3, 3, 3}

print(numbers)
```

Result:

```text
{1, 2, 3}
```

Set sirf ye remember karta hai:

```text
1 exists
2 exists
3 exists
```

Ye nahi batata ke `3` kitni baar originally aaya tha.

---

# Multiset kya hai?

**Multiset** mein duplicates allowed hote hain aur unki quantity/count important hoti hai.

Example:

```text
[1, 1, 1, 2, 2, 3]
```

Yahan:

```text
1 → 3 times
2 → 2 times
3 → 1 time
```

Normal `set` mein:

```text
{1, 2, 3}
```

ho jayega aur counts lost ho jayenge.

---

# Python mein Multiset ke liye `Counter`

Python mein `collections.Counter` multiset jaisa behavior provide karta hai.

```python
from collections import Counter

numbers = [1, 1, 1, 2, 2, 3]

counts = Counter(numbers)

print(counts)
```

Output:

```text
Counter({1: 3, 2: 2, 3: 1})
```

Yahan:

```text
1 → 3
2 → 2
3 → 1
```

preserve hota hai.

---

# Set vs Counter

| Feature            | Set        | `Counter` |
| ------------------ | ---------- | --------- |
| Unique values      | Yes        | Yes       |
| Duplicate count    | No         | Yes       |
| Frequency          | No         | Yes       |
| Membership testing | Yes        | Yes       |
| Main purpose       | Uniqueness | Counting  |

---

# Practical Equipment Example

Suppose work-order data mein equipment IDs hain:

```python
equipment = [
    "AHU-01",
    "AHU-01",
    "VAV-01",
    "FCU-01",
    "AHU-01",
    "VAV-01"
]
```

### Sirf unique equipment chahiye:

```python
unique_equipment = set(equipment)

print(unique_equipment)
```

Concept:

```text
AHU-01
VAV-01
FCU-01
```

### Har equipment kitni baar appear hua:

```python
from collections import Counter

counts = Counter(equipment)

print(counts)
```

Conceptual result:

```text
AHU-01 → 3
VAV-01 → 2
FCU-01 → 1
```

Yani:

```text
set
 ↓
"Kaun kaun se unique equipment hain?"

Counter
 ↓
"Har equipment kitni baar hai?"
```

---

# Complete Practical Example

Suppose do teams ke skills hain:

```python
team_a = {
    "HVAC",
    "BMS",
    "Electrical"
}

team_b = {
    "BMS",
    "Electrical",
    "Plumbing"
}
```

### Dono teams ke total unique skills:

```python
print(team_a | team_b)
```

### Common skills:

```python
print(team_a & team_b)
```

### Sirf Team A ke skills:

```python
print(team_a - team_b)
```

### Sirf ek team mein hone wale skills:

```python
print(team_a ^ team_b)
```

Mental model:

```text
Team A                  Team B

HVAC                     BMS
BMS                      Electrical
Electrical               Plumbing
```

Common:

```text
BMS
Electrical
```

A only:

```text
HVAC
```

B only:

```text
Plumbing
```

---

# Chapter 8 ka Main Mental Model

```text
SET
 │
 ├── Unique values
 │
 ├── No duplicates
 │
 ├── No indexing
 │
 ├── Union              |
 │
 ├── Intersection       &
 │
 ├── Difference         -
 │
 └── Symmetric Diff     ^
```

### Unique list:

```python
unique = set(my_list)
```

### Set ke andar set-like object:

```python
frozenset(...)
```

### Counting duplicates:

```python
from collections import Counter
Counter(my_list)
```

---

# Quick Revision

### Union

```python
A | B
```

**Dono ke unique elements**

### Intersection

```python
A & B
```

**Common elements**

### Difference

```python
A - B
```

**A mein hain, B mein nahi**

### Symmetric Difference

```python
A ^ B
```

**Sirf ek set mein hain, dono mein common nahi**

### Unique elements

```python
set(my_list)
```

### Count/frequency

```python
Counter(my_list)
```

### Subset

```python
A.issubset(B)
```

### Superset

```python
A.issuperset(B)
```

### No common elements

```python
A.isdisjoint(B)
```

## Sabse important difference

```text
Set
→ uniqueness important

Counter / Multiset
→ frequency/count important
```

Agar question ho:

> **"Duplicate hatao."**

Use:

```python
set()
```

Agar question ho:

> **"Har item kitni baar repeat hua?"**

Use:

```python
Counter()
```
