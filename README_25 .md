# Chapter 25: Linked List Node

Linked List ka basic building block **Node** hota hai.

Agar humare paas:

```text
[10] -> [20] -> [30] -> None
```

to yahan `10`, `20`, aur `30` alag-alag nodes ke andar stored hain.

Har node normally do important cheezein rakhta hai:

1. **data** — actual value
2. **next** — aglay node ka reference

Structure:

```text
        Node
     +---------+
     | data    |
     | next    |
     +---------+
```

Example:

```text
[10 | next] -> [20 | next] -> [30 | None]
```

---

# Section 25.1: Write a Simple Linked List Node in Python

Python mein simple Node banane ke liye hum `class` use kar sakte hain.

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```

Ab is code ko line-by-line samjhte hain.

## Step 1: Class create karna

```python
class Node:
```

Yahan hum `Node` naam ki class create kar rahe hain.

Class ko ek **blueprint** samajh sakte hain.

Is blueprint se hum multiple nodes bana sakte hain.

---

## Step 2: Constructor

```python
def __init__(self, data):
```

`__init__()` constructor hai.

Jab hum `Node()` ka naya object create karte hain, `__init__()` automatically call hota hai.

Example:

```python
node1 = Node(10)
```

Python internally constructor ko `10` ke saath call karega.

---

## Step 3: Data store karna

```python
self.data = data
```

Yahan jo value constructor ko mili hai, woh node ke `data` attribute mein store ho jati hai.

Example:

```python
node1 = Node(10)

print(node1.data)
```

Output:

```text
10
```

Agar:

```python
node2 = Node("AHU-001")
```

to:

```python
print(node2.data)
```

Output:

```text
AHU-001
```

Iska matlab Node sirf numbers ke liye nahi hai. Woh strings, dictionaries, objects etc. bhi store kar sakta hai.

---

# Step 4: `next` attribute

```python
self.next = None
```

`next` aglay node ka reference store karega.

Naya node banate waqt abhi koi next node nahi hai, isliye:

```python
self.next = None
```

Example:

```python
node1 = Node(10)

print(node1.next)
```

Output:

```text
None
```

Abhi structure:

```text
[10 | None]
```

---

# Step 5: Do nodes ko connect karna

Ab hum do nodes banate hain:

```python
node1 = Node(10)
node2 = Node(20)
```

Initially:

```text
node1              node2
  |                  |
  v                  v
[10 | None]        [20 | None]
```

Ab:

```python
node1.next = node2
```

Ab structure:

```text
[10 | next] -> [20 | None]
```

Ab `node1.next` mein `node2` ka reference stored hai.

Check karein:

```python
print(node1.next)
```

Output kuch is tarah ka hoga:

```text
<__main__.Node object at 0x...>
```

Ye normal hai.

Agar humein aglay node ka data chahiye:

```python
print(node1.next.data)
```

Output:

```text
20
```

Yahan important chain samjhein:

```python
node1
```

pehla node hai.

```python
node1.next
```

doosra node hai.

```python
node1.next.data
```

doosre node ka data hai.

---

# Three Nodes Connect Karna

Ab teen nodes banate hain:

```python
node1 = Node(10)
node2 = Node(20)
node3 = Node(30)
```

Connect:

```python
node1.next = node2
node2.next = node3
```

Structure:

```text
node1             node2             node3
  |                 |                 |
  v                 v                 v
[10 | next] ----> [20 | next] ----> [30 | None]
```

Ab:

```python
print(node1.data)
print(node1.next.data)
print(node1.next.next.data)
```

Output:

```text
10
20
30
```

Isko chain ki tarah dekhein:

```text
node1
  |
  v
node1.next
  |
  v
node1.next.next
```

Aur:

```python
node1.next.next
```

`node3` ko refer karta hai.

Isliye:

```python
node1.next.next.data
```

`30` return karta hai.

---

# `None` ka Role

Last node ka `next` normally `None` hota hai.

```text
[10] -> [20] -> [30] -> None
```

Iska matlab:

```text
30 ke baad koi node nahi hai.
```

Traversal mein isi `None` ko stopping condition ke taur par use karte hain.

```python
current = node1

while current is not None:
    print(current.data)
    current = current.next
```

Output:

```text
10
20
30
```

Jab `current` last node ke baad `None` ho jata hai:

```python
current is None
```

to loop stop ho jata hai.

---

# Complete Simple Example

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


node1 = Node(10)
node2 = Node(20)
node3 = Node(30)

node1.next = node2
node2.next = node3

current = node1

while current is not None:
    print(current.data)
    current = current.next
```

Output:

```text
10
20
30
```

---

# Node ko Diagram se Samjhein

Code:

```python
node1 = Node("AHU-001")
node2 = Node("AHU-002")

node1.next = node2
```

Memory relationship ko conceptually:

```text
node1
  |
  v
+------------------+
| data = AHU-001   |
| next ------------|------+
+------------------+      |
                          v
                    +------------------+
                    | data = AHU-002   |
                    | next = None      |
                    +------------------+
```

Yahan `node1.next` directly `"AHU-002"` nahi rakhta.

Ye **Node object ka reference** rakhta hai.

Isi wajah se:

```python
node1.next.data
```

likhne par hum doosre node ka data access kar sakte hain.

---

# Node mein Different Data Store Karna

Node ka `data` kisi bhi Python object ko hold kar sakta hai.

### Integer

```python
node = Node(100)
```

### String

```python
node = Node("AHU-001")
```

### Dictionary

```python
node = Node({
    "id": "AHU-001",
    "floor": "Level 10"
})
```

Phir:

```python
print(node.data["id"])
```

Output:

```text
AHU-001
```

### List

```python
node = Node([10, 20, 30])
```

Yani Node class khud data type ko restrict nahi karti.

---

# `data` aur `next` ka Difference

Ye distinction bohat important hai:

```python
node = Node(10)
```

Is node mein:

```text
data = 10
next = None
```

`data`:

> Node ke andar actual information.

`next`:

> Agle Node object ka reference.

Example:

```python
node1 = Node(10)
node2 = Node(20)

node1.next = node2
```

Ab:

```text
node1.data       → 10
node1.next       → node2
node1.next.data  → 20
```

---

# Common Mistake

Kuch beginners ye kar dete hain:

```python
node1.next = 20
```

Ye technically possible hai, lekin phir `next` mein Node object ke bajaye integer aa gaya.

```python
print(node1.next)
```

Output:

```text
20
```

Lekin:

```python
print(node1.next.data)
```

error dega, kyun ke integer ke paas `.data` attribute nahi hai.

Linked List mein normally:

```python
node1.next = node2
```

hona chahiye.

Yani:

```text
Node -> Node -> Node
```

na ke:

```text
Node -> integer
```

---

# Node aur Linked List ka Relationship

Is chapter ka sabse important concept:

```text
Node = ek building block
Linked List = connected Nodes ki chain
```

Example:

```text
Node       Node       Node
 ↓          ↓          ↓
[10]  ->   [20]  ->   [30]  -> None
```

Sirf ek Node:

```python
node = Node(10)
```

Connected nodes:

```python
node1 = Node(10)
node2 = Node(20)
node3 = Node(30)

node1.next = node2
node2.next = node3
```

Ab ye ek **Singly Linked List structure** ban gaya.

---

# Practice Exercise

## Exercise 1

`Node` class banayein:

```python
class Node:
    ...
```

Phir:

```text
100 -> 200 -> 300 -> None
```

ki chain banayein.

## Exercise 2

Is chain se `300` print karein:

```python
print(????????)
```

## Exercise 3

Ek Node banayein jiska data ho:

```text
"AHU-001"
```

Phir print karein:

```text
AHU-001
```

## Exercise 4

Ek Node mein dictionary store karein:

```python
{
    "equipment_id": "VAV-001",
    "floor": "Level 10"
}
```

Phir sirf `equipment_id` print karein.

---

# Final Mental Model

Linked List Node ko bas is formula se yaad rakhein:

```text
Node = data + next
```

Python:

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```

Phir:

```python
node1 = Node(10)
node2 = Node(20)

node1.next = node2
```

Structure:

```text
[10 | next] ---> [20 | None]
```

Aur access:

```python
node1.data
```

→ `10`

```python
node1.next.data
```

→ `20`

**Core idea:** `next` actual next value nahi, balki next **Node object ka reference** hold karta hai. Isi reference chain ki wajah se multiple Nodes mil kar Linked List banate hain.
