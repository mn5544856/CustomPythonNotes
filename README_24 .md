# Chapter 24: Linked Lists

Linked List ek linear data structure hai jismein data **nodes** ki form mein store hota hai. Har node mein data aur aglay node ka reference hota hai.

Python ki normal `list` mein elements indexes ke zariye access hote hain. Linked List mein nodes references ke zariye connected hotay hain.

## 1. Linked List ka basic structure

Singly Linked List ke har node mein do cheezein hoti hain:

1. **Data:** Node mein stored value.
2. **Next:** Agle node ka reference.

Example:

```text
Head
 |
 v
[10 | next] -> [20 | next] -> [30 | None]
```

* `Head` pehle node ko point karta hai.
* Pehle node ka `next` doosre node ko point karta hai.
* Doosre node ka `next` teesre node ko point karta hai.
* Aakhri node ka `next` `None` hota hai, kyun ke uske baad koi node nahi.

## 2. Python mein Node class banana

Python mein hum `class` use karke node bana sakte hain.

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```

Explanation:

* `class Node`: Node naam ki class define karta hai.
* `__init__()`: Naya node banne par initialize hota hai.
* `self.data`: Node ka actual data store karta hai.
* `self.next = None`: Shuru mein node kisi aglay node se connected nahi hota.

Ab node banate hain:

```python
node1 = Node(10)
node2 = Node(20)

print(node1.data)
print(node1.next)
```

Output:

```text
10
None
```

Abhi `node1` aur `node2` alag hain. Unhein connect karne ke liye:

```python
node1.next = node2

print(node1.next.data)
```

Output:

```text
20
```

Ab `node1` ka `next` `node2` ko point karta hai.

## 3. Section 24.1: Single Linked List Example

Singly Linked List mein har node sirf aglay node ka reference rakhta hai.

Pehle `Node` class banate hain:

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```

Ab teen nodes create karte hain:

```python
node1 = Node(10)
node2 = Node(20)
node3 = Node(30)
```

Nodes ko connect karte hain:

```python
node1.next = node2
node2.next = node3
```

Ab structure kuch is tarah hai:

```text
node1             node2             node3
  |                 |                 |
  v                 v                 v
[10 | next] ----> [20 | next] ----> [30 | None]
```

Linked List ka starting node `head` kehlata hai.

```python
head = node1
```

Ab `head` se poori list access ki ja sakti hai.

## 4. Linked List ko traverse karna

Traverse ka matlab hai list ke tamam nodes ko ek ek karke visit karna.

```python
current = head

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

Step-by-step:

1. `current = head` se pehle node par aate hain.
2. `current.data` se us node ka data print hota hai.
3. `current = current.next` se aglay node par move karte hain.
4. Jab `current` `None` ho jata hai, loop khatam ho jata hai.

<box border={{size:1,color:"#16a34a"}} radius="lg" padding={3} gap={1}>
**Important:** Linked List mein next node tak pohanchne ke liye current node ka `next` reference use hota hai. Is mein normal Python list ki tarah `index` se direct access nahi hota. </box>

## 5. Complete Singly Linked List example

Ab `Node` aur `LinkedList` dono classes banate hain.

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)

        if self.head is None:
            self.head = new_node
            return

        current = self.head

        while current.next is not None:
            current = current.next

        current.next = new_node

    def display(self):
        current = self.head

        while current is not None:
            print(current.data, end=" -> ")
            current = current.next

        print("None")


my_list = LinkedList()

my_list.append(10)
my_list.append(20)
my_list.append(30)

my_list.display()
```

Output:

```text
10 -> 20 -> 30 -> None
```

### Code ki explanation

**`__init__()`**

```python
def __init__(self):
    self.head = None
```

Nayi Linked List banne par us mein koi node nahi hota. Isliye `head` ki value `None` hoti hai.

**`append()`**

```python
def append(self, data):
    new_node = Node(data)
```

Naya node create hota hai.

Agar list empty hai:

```python
if self.head is None:
    self.head = new_node
    return
```

Naya node hi pehla node ban jata hai.

Agar list empty nahi hai:

```python
current = self.head

while current.next is not None:
    current = current.next
```

Loop aakhri node tak jata hai.

Phir:

```python
current.next = new_node
```

Aakhri node ko naye node se connect kar diya jata hai.

**`display()`**

Ye method `head` se start karke har node ka data print karta hai, jab tak `None` na mil jaye.

## 6. Linked List mein beginning par node add karna

Beginning par node add karne ke liye naye node ka `next` purane `head` ko point karega. Phir `head` ko naye node par set karenge.

```python
def prepend(self, data):
    new_node = Node(data)
    new_node.next = self.head
    self.head = new_node
```

Is method ko `LinkedList` class ke andar add karein.

Example:

```python
my_list = LinkedList()

my_list.append(20)
my_list.append(30)

my_list.prepend(10)

my_list.display()
```

Output:

```text
10 -> 20 -> 30 -> None
```

Yahan `10` beginning mein add hua.

## 7. Linked List aur Python list ka comparison

| Feature                 | Python `list`                        | Singly Linked List               |
| ----------------------- | ------------------------------------ | -------------------------------- |
| Structure               | Dynamic array                        | Connected nodes                  |
| Element access          | Index se                             | Nodes traverse karke             |
| First element           | `items[0]`                           | `head.data`                      |
| Next element            | `items[1]`                           | `node.next`                      |
| Beginning par insertion | Aksar baqi elements shift hotay hain | Head reference update hota hai   |
| End par insertion       | Amortized O(1)                       | Tail reference na ho to O(n)     |
| Extra memory            | Elements ke references               | Har node ka `next` reference bhi |
| Direct indexing         | Haan                                 | Nahi                             |

Linked List har situation mein Python list se behtar nahi hoti. Python ki built-in list aksar general-purpose programming ke liye zyada convenient hoti hai.

## 8. Linked List ki time complexity

`n` se murad list mein nodes ki tadaad hai.

| Operation                       | Singly Linked List |
| ------------------------------- | -----------------: |
| Head access                     |               O(1) |
| Beginning par insert            |               O(1) |
| Kisi index tak traverse         |               O(n) |
| End par append, tail ke baghair |               O(n) |
| End par append, tail ke saath   |               O(1) |
| Kisi value ko search karna      |               O(n) |

`O(1)` ka matlab operation ka time list ke size ke saath significantly nahi badhta. `O(n)` ka matlab worst case mein tamam nodes visit karne par sakte hain.

## 9. Practical example: Equipment nodes

Maan lein hum HVAC equipment IDs ko linked list mein store karna chahte hain.

```python
equipment = LinkedList()

equipment.append("AHU-001")
equipment.append("AHU-002")
equipment.append("VAV-001")

equipment.display()
```

Output:

```text
AHU-001 -> AHU-002 -> VAV-001 -> None
```

Is example mein har node ek equipment ID store karta hai aur `next` aglay equipment node ko point karta hai.

Real-world applications mein linked lists tab useful ho sakti hain jab nodes ke darmiyan insertion aur deletion ki zaroorat ho aur un nodes ka reference pehle se available ho.

---

# Practice Exercises

**Exercise 1:** `Node` class banayein aur `10`, `20`, `30` ke teen nodes ko manually connect karein. `head` se start karke tamam values print karein.

**Exercise 2:** `LinkedList` class mein `append()` method banayein jo empty aur non-empty dono lists handle kare.

**Exercise 3:** `prepend()` method banayein jo list ke beginning mein naya node add kare.

**Exercise 4:** Is structure ko code mein banayein:

```text
Head
 |
 v
[AHU-01] -> [AHU-02] -> [AHU-03] -> None
```

Phir tamam equipment IDs print karein.

---

# Chapter 24: Final Summary

* Linked List ek linear data structure hai.
* Har node mein data aur next node ka reference hota hai.
* Singly Linked List mein har node sirf aglay node ko point karta hai.
* `head` pehle node ka reference hota hai.
* Aakhri node ka `next` `None` hota hai.
* `while` loop se nodes traverse kiye ja sakte hain.
* `append()` end par node add karta hai.
* `prepend()` beginning par node add karta hai.
* Linked List mein direct indexing nahi hoti; nodes tak pohanchne ke liye traversal karna parta hai.

**Core concept:** Linked List mein nodes apne `next` references ke zariye connected hotay hain. Pehle node se shuru karke references follow karte hue baqi nodes tak pohancha jata hai.
