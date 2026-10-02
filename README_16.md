# Chapter 16: Loops

Python mein **Loop** ka use kisi code ko baar-baar execute karne ke liye hota hai.

Misal ke taur par, agar tumhein 100 work orders ke numbers print karne hain, to 100 `print()` statements likhne ki zaroorat nahi. Loop se ye kaam automatically ho sakta hai.

Python mein do basic loops hain:

1. `for` loop
2. `while` loop

---

## 16.1: Break and Continue in Loops

`break` aur `continue` dono loop ke flow ko control karte hain, lekin inka kaam different hai.

* `break` poore loop ko foran terminate kar deta hai.
* `continue` current iteration ko skip karke next iteration par chala jata hai.

### 1. `break` statement

Example:

```python
for number in range(1, 6):
    if number == 3:
        break

    print(number)
```

Output:

```text
1
2
```

Step-by-step:

1. `number` ki value `1` hai. Condition false hai, is liye `1` print hota hai.
2. `number` ki value `2` hai. Condition false hai, is liye `2` print hota hai.
3. `number` ki value `3` hai. Condition true hai, is liye `break` execute hota hai.
4. Loop terminate ho jata hai. `4` aur `5` process nahi hote.

### Work order example

Maan lo tum work orders ki list mein kisi specific work order ko search kar rahe ho. Milte hi search rokni hai.

```python
work_orders = ["WO101", "WO102", "WO103", "WO104"]

for wo in work_orders:
    if wo == "WO103":
        print("Work order found")
        break

    print("Checking:", wo)
```

Output:

```text
Checking: WO101
Checking: WO102
Work order found
```

`WO103` milne ke baad loop terminate ho gaya.

### 2. `continue` statement

`continue` current iteration ka baqi code skip karta hai aur loop ki next iteration start karta hai.

```python
for number in range(1, 6):
    if number == 3:
        continue

    print(number)
```

Output:

```text
1
2
4
5
```

Jab `number == 3` hota hai, `continue` execute hota hai. Is wajah se `print(number)` us iteration mein execute nahi hota.

### Work order example

Maan lo kuch work orders mein equipment ID missing hai. Tum un records ko skip karna chahte ho.

```python
work_orders = ["WO101", "", "WO103", "", "WO105"]

for wo in work_orders:
    if wo == "":
        continue

    print("Processing:", wo)
```

Output:

```text
Processing: WO101
Processing: WO103
Processing: WO105
```

Empty strings skip ho gayi hain.

### `break` vs `continue`

| `break`                                  | `continue`                                                 |
| ---------------------------------------- | ---------------------------------------------------------- |
| Poora loop terminate karta hai.          | Sirf current iteration skip karta hai.                     |
| Loop ke baad wala code execute hota hai. | Loop next iteration se continue hota hai.                  |
| Search result milne par useful hai.      | Invalid ya unwanted records skip karne ke liye useful hai. |

---

## 16.2: For Loops

`for` loop kisi iterable object ke elements par ek-ek karke iterate karta hai.

Iterable examples:

* `list`
* `tuple`
* `set`
* `string`
* `dictionary`
* `range`

### Basic syntax

```python
for variable in iterable:
    # loop body
```

`variable` har iteration mein iterable ka next element receive karta hai.

### Example: `range()`

```python
for number in range(5):
    print(number)
```

Output:

```text
0
1
2
3
4
```

`range(5)` numbers `0` se `4` tak generate karta hai. `5` include nahi hota.

### `range(start, stop)`

```python
for number in range(1, 6):
    print(number)
```

Output:

```text
1
2
3
4
5
```

* `start = 1`
* `stop = 6`
* Stop value include nahi hoti.

### `range(start, stop, step)`

```python
for number in range(2, 11, 2):
    print(number)
```

Output:

```text
2
4
6
8
10
```

Yahan `step=2` ka matlab har iteration mein 2 add hoga.

Negative step se reverse counting kar sakte hain:

```python
for number in range(5, 0, -1):
    print(number)
```

Output:

```text
5
4
3
2
1
```

### String ke saath `for` loop

```python
equipment_id = "AHU101"

for character in equipment_id:
    print(character)
```

Output:

```text
A
H
U
1
0
1
```

Loop string ke har character par iterate karta hai.

### `for` loop kab use karein?

Jab tumhein pata ho ke kis iterable ke elements par kaam karna hai, ya kitni baar loop chalana hai, to `for` loop useful hota hai.

---

## 16.3: Iterating over Lists

List ke elements ko ek-ek karke access karne ke liye `for` loop use kar sakte hain.

```python
equipment = ["AHU", "FCU", "VAV"]

for item in equipment:
    print(item)
```

Output:

```text
AHU
FCU
VAV
```

Har iteration mein `item` ko list ka next element milta hai.

### List ke elements par operation

```python
temperatures = [22, 25, 28, 30]

for temp in temperatures:
    print(temp + 1)
```

Output:

```text
23
26
29
31
```

Yahan original list change nahi hoti. Sirf har value mein `1` add karke result print hota hai.

### List ke indexes ke saath iteration

Agar element ke saath uska index bhi chahiye, to `enumerate()` use karo.

```python
equipment = ["AHU", "FCU", "VAV"]

for index, item in enumerate(equipment):
    print(index, item)
```

Output:

```text
0 AHU
1 FCU
2 VAV
```

Agar counting `1` se start karni ho:

```python
for index, item in enumerate(equipment, start=1):
    print(index, item)
```

Output:

```text
1 AHU
2 FCU
3 VAV
```

### List ko modify karna

Loop ke dauran original list mein elements add ya remove karna unexpected results de sakta hai.

Misal ke taur par, list se elements remove karte hue usi list par iterate karne se kuch elements skip ho sakte hain.

Safer approach: list ki copy par iterate karo.

```python
numbers = [1, 2, 3, 4, 5]

for number in numbers.copy():
    if number % 2 == 0:
        numbers.remove(number)

print(numbers)
```

Output:

```text
[1, 3, 5]
```

`numbers.copy()` ek separate list banata hai. Loop copy par chalta hai, jab ke removal original list se hoti hai.

Agar sirf filtered list chahiye, to list comprehension bhi use kar sakte ho:

```python
numbers = [1, 2, 3, 4, 5]

odd_numbers = [number for number in numbers if number % 2 != 0]

print(odd_numbers)
```

Output:

```text
[1, 3, 5]
```

---

## 16.4: Loops with an `else` Clause

Python mein `for` aur `while` loops ke saath `else` clause bhi use ho sakta hai.

Loop ka `else` tab execute hota hai jab loop normally complete ho jaye, yani `break` se terminate na hua ho.

### `for` loop ke saath `else`

```python
for number in range(3):
    print(number)
else:
    print("Loop completed")
```

Output:

```text
0
1
2
Loop completed
```

Loop normally complete hua, is liye `else` execute hua.

### `break` ke saath `else`

```python
for number in range(5):
    if number == 3:
        break

    print(number)
else:
    print("Loop completed")
```

Output:

```text
0
1
2
```

Yahan `break` ki wajah se loop terminate hua. Is liye loop ka `else` execute nahi hua.

### Search example

```python
work_orders = ["WO101", "WO102", "WO103"]
target = "WO105"

for wo in work_orders:
    if wo == target:
        print("Work order found")
        break
else:
    print("Work order not found")
```

Output:

```text
Work order not found
```

Loop poori list check karta hai. Agar target mil jaye to `break` execute hota hai aur `else` skip ho jata hai. Agar target na mile aur loop normally complete ho, to `else` execute hota hai.

### Important difference

Loop ka `else` `if` ke `else` se different hai.

* `if/else`: condition ke result ke mutabiq execute hota hai.
* `for/else` ya `while/else`: loop normally complete hone par execute hota hai.

`continue` loop ke `else` ko prevent nahi karta. Sirf `break` normal completion ko rokta hai.

---

## 16.5: The `pass` Statement

`pass` Python ka null operation hai. Iska matlab hai: **kuch bhi nahi karo**.

Jab Python syntax ke liye statement zaroori ho, lekin tum abhi koi action nahi likhna chahte, to `pass` use kar sakte ho.

### Basic example

```python
if True:
    pass
```

Ye valid code hai. `pass` ki wajah se koi action perform nahi hota.

Agar block ke andar kuch bhi na likho:

```python
if True:
```

To Python `IndentationError` ya syntax-related error dega, kyun ke block empty hai.

### Loop mein `pass`

```python
for number in range(5):
    pass

print("Loop finished")
```

Output:

```text
Loop finished
```

Loop 5 iterations chala, lekin har iteration mein koi operation nahi hua.

### Function mein `pass`

```python
def check_equipment():
    pass
```

Ye function define ho gaya, lekin abhi koi kaam nahi karta.

Baad mein function ka code likh sakte ho.

### `pass` vs `continue`

| `pass`                                       | `continue`                                     |
| -------------------------------------------- | ---------------------------------------------- |
| Koi operation nahi karta.                    | Current iteration ka baqi code skip karta hai. |
| Loop ko khud se affect nahi karta.           | Loop ko next iteration par le jata hai.        |
| Empty block ko valid banane mein useful hai. | Kuch iterations skip karne ke liye useful hai. |

Example:

```python
for number in range(3):
    if number == 1:
        pass

    print(number)
```

Output:

```text
0
1
2
```

`pass` ke baad `print()` execute hota hai.

Lekin:

```python
for number in range(3):
    if number == 1:
        continue

    print(number)
```

Output:

```text
0
2
```

`continue` ki wajah se `1` print nahi hota.

---

## 16.6: Iterating over Dictionaries

Dictionary mein data `key: value` pairs ki form mein hota hai.

Example:

```python
equipment = {
    "AHU101": "Running",
    "FCU201": "Stopped",
    "VAV301": "Running"
}
```

### 1. Dictionary keys par iterate karna

```python
for key in equipment:
    print(key)
```

Output:

```text
AHU101
FCU201
VAV301
```

Direct dictionary par loop chalane se keys milti hain.

Explicitly `.keys()` bhi use kar sakte ho:

```python
for key in equipment.keys():
    print(key)
```

### 2. Dictionary values par iterate karna

`.values()` se values milti hain.

```python
for value in equipment.values():
    print(value)
```

Output:

```text
Running
Stopped
Running
```

### 3. Keys aur values dono par iterate karna

`.items()` har iteration mein key aur value ka pair deta hai.

```python
for key, value in equipment.items():
    print(key, value)
```

Output:

```text
AHU101 Running
FCU201 Stopped
VAV301 Running
```

Yahan `key` mein equipment ID aur `value` mein status aata hai.

### Practical example: Running equipment count

```python
equipment = {
    "AHU101": "Running",
    "FCU201": "Stopped",
    "VAV301": "Running"
}

count = 0

for equipment_id, status in equipment.items():
    if status == "Running":
        count += 1

print("Running equipment:", count)
```

Output:

```text
Running equipment: 2
```

### Dictionary values update karna

```python
equipment = {
    "AHU101": "Running",
    "FCU201": "Stopped"
}

for equipment_id in equipment:
    equipment[equipment_id] = "Checked"

print(equipment)
```

Output:

```text
{'AHU101': 'Checked', 'FCU201': 'Checked'}
```

Existing keys ki values update karna loop ke dauran aam tor par theek hai. Lekin dictionary mein keys add ya remove karte hue usi dictionary par iterate karna `RuntimeError` de sakta hai. Aisi situation mein `list(equipment)` ya `list(equipment.items())` par iterate karo.

---

## 16.7: The "Half Loop" do-while

Kuch programming languages mein `do-while` loop hota hai. Is mein loop body kam az kam ek baar execute hoti hai, phir condition check hoti hai.

Python mein built-in `do-while` loop nahi hai.

Lekin `while True` aur `break` ke combination se same behavior achieve kar sakte hain.

### Basic example

```python
while True:
    number = int(input("Enter a number: "))

    print("You entered:", number)

    if number == 0:
        break
```

Agar user `5`, phir `3`, phir `0` enter kare, output kuch is tarah hoga:

```text
Enter a number: 5
You entered: 5
Enter a number: 3
You entered: 3
Enter a number: 0
You entered: 0
```

Loop body pehle execute hoti hai. Uske baad `number == 0` check hota hai.

Is liye ye `do-while` jaisa behavior hai.

### `while True` ka flow

1. Loop start hota hai.
2. Input liya jata hai.
3. Code execute hota hai.
4. Condition check hoti hai.
5. Agar condition true ho, `break` loop terminate karta hai.
6. Warna next iteration start hoti hai.

### Input validation example

```python
while True:
    status = input("Enter status: ")

    if status in ("Running", "Stopped"):
        break

    print("Invalid status. Try again.")

print("Selected status:", status)
```

User jab tak valid status enter nahi karta, loop input mangta rahega.

**Note:** `int(input())` mein agar user number ke bajaye text enter kare, to `ValueError` aa sakta hai. Real applications mein input validation ke saath `try/except` bhi use karna chahiye.

---

## 16.8: Looping and Unpacking

Python mein loop ke andar tuple ya list ke elements ko unpack kar sakte hain.

Unpacking ka matlab hai ek collection ke elements ko multiple variables mein assign karna.

### Tuple unpacking

```python
equipment = [
    ("AHU101", "Running"),
    ("FCU201", "Stopped"),
    ("VAV301", "Running")
]

for equipment_id, status in equipment:
    print(equipment_id, status)
```

Output:

```text
AHU101 Running
FCU201 Stopped
VAV301 Running
```

Har tuple mein do elements hain. Python unhein `equipment_id` aur `status` mein unpack karta hai.

### List unpacking

```python
records = [
    ["WO101", "AHU", "Open"],
    ["WO102", "FCU", "Closed"]
]

for work_order, equipment, status in records:
    print(work_order, equipment, status)
```

Output:

```text
WO101 AHU Open
WO102 FCU Closed
```

### Unpacking ke liye elements ki tadaad

Agar tuple mein 3 elements hain, to aam tor par 3 variables chahiye.

```python
record = ("WO101", "AHU", "Open")

work_order, equipment, status = record

print(work_order)
print(equipment)
print(status)
```

Output:

```text
WO101
AHU
Open
```

Agar variables aur elements ki tadaad match na kare, to `ValueError` aa sakta hai.

### Star unpacking

`*` ka use karke multiple elements ko ek list mein collect kar sakte hain.

```python
record = ("WO101", "AHU", "Open", "Level 4")

work_order, *details = record

print(work_order)
print(details)
```

Output:

```text
WO101
['AHU', 'Open', 'Level 4']
```

Loop mein bhi star unpacking use ho sakti hai:

```python
records = [
    ("WO101", "AHU", "Open", "Level 4"),
    ("WO102", "FCU", "Closed", "Level 5")
]

for work_order, *details in records:
    print(work_order, details)
```

Output:

```text
WO101 ['AHU', 'Open', 'Level 4']
WO102 ['FCU', 'Closed', 'Level 5']
```

---

## 16.9: Iterating Different Portions of a List with Different Step Size

Python mein list slicing ke zariye list ke different portions par different step size ke saath iterate kar sakte hain.

Slicing ka syntax:

```python
list[start:stop:step]
```

* `start`: kis index se shuru karna hai.
* `stop`: kis index se pehle rukna hai.
* `step`: kitne indexes skip karne hain.

### Basic slicing

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(numbers[::2])
```

Output:

```text
[0, 2, 4, 6, 8]
```

`step=2` ki wajah se har doosra element select hota hai.

### Different step sizes

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

for number in numbers[::2]:
    print(number)
```

Output:

```text
0
2
4
6
8
```

Ab step `3` use karo:

```python
for number in numbers[::3]:
    print(number)
```

Output:

```text
0
3
6
9
```

### List ke different portions

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

for number in numbers[:5:2]:
    print(number)
```

Output:

```text
0
2
4
```

Yahan:

* `start` default `0` hai.
* `stop` `5` hai, jo include nahi hota.
* `step` `2` hai.

### Negative step

Negative step se reverse direction mein iterate kar sakte hain.

```python
numbers = [0, 1, 2, 3, 4, 5]

for number in numbers[::-1]:
    print(number)
```

Output:

```text
5
4
3
2
1
0
```

`[::-1]` list ko reverse order mein access karta hai.

**Important:** Slicing ek nayi list banati hai. Agar list bohat bari ho, to memory usage ka khayal rakho. Sirf iterate karna ho to `range()` ya `reversed()` bhi useful ho sakte hain.

---

## 16.10: While Loop

`while` loop tab tak execute hota hai jab tak uski condition `True` rahe.

### Basic syntax

```python
while condition:
    # loop body
```

Python pehle condition check karta hai. Agar condition `True` ho, to body execute hoti hai. Agar condition `False` ho, to loop body execute nahi hoti.

### Basic example

```python
number = 1

while number <= 5:
    print(number)
    number += 1
```

Output:

```text
1
2
3
4
5
```

Step-by-step:

1. `number = 1`
2. Condition `number <= 5` check hoti hai.
3. Condition true hai, is liye `number` print hota hai.
4. `number += 1` value mein 1 add karta hai.
5. Condition dobara check hoti hai.
6. Jab `number` ki value `6` hoti hai, condition false ho jati hai aur loop stop ho jata hai.

### Infinite loop

Agar condition kabhi false na ho, to loop continuously chalta reh sakta hai.

Example:

```python
number = 1

while number <= 5:
    print(number)
```

Is code mein `number` update nahi ho raha. Is liye condition hamesha true rahegi aur loop infinite ho jayega.

Is tarah ke loop se bachne ke liye ensure karo ke condition kisi point par false ho sake, ya zaroorat ke mutabiq `break` use karo.

### `while` loop with `break`

```python
number = 1

while number <= 10:
    if number == 5:
        break

    print(number)
    number += 1
```

Output:

```text
1
2
3
4
```

Jab `number == 5` hota hai, `break` loop terminate kar deta hai.

### `while` loop with `continue`

```python
number = 0

while number < 5:
    number += 1

    if number == 3:
        continue

    print(number)
```

Output:

```text
1
2
4
5
```

Yahan `number` ko `continue` se pehle increment kiya gaya hai. Is liye jab `number == 3` hota hai, loop skip hone ke baad bhi agle iteration mein number `4` ho jata hai.

**Important:** `continue` se pehle loop ki condition ko affect karne wali value update karna zaroori ho sakta hai. Warna infinite loop ban sakta hai.

### `while` loop with `else`

```python
number = 1

while number <= 3:
    print(number)
    number += 1
else:
    print("Loop completed")
```

Output:

```text
1
2
3
Loop completed
```

Loop normally complete hua, is liye `else` execute hua.

Agar loop `break` se terminate ho, to `else` execute nahi hota.

### `for` vs `while`

| `for` loop                                                     | `while` loop                                                |
| -------------------------------------------------------------- | ----------------------------------------------------------- |
| Iterable ke elements par iterate karta hai.                    | Condition true rehne tak chalta hai.                        |
| Lists, strings, dictionaries aur `range()` ke liye useful hai. | Jab iterations ki tadaad pehle se maloom na ho, useful hai. |
| Aksar automatic next element milta hai.                        | Condition ko update karna programmer ki zimmedari hai.      |
| Infinite loop ka risk aam tor par kam hota hai.                | Condition update na ho to infinite loop ho sakta hai.       |

---

# Chapter 16: Practice Exercises

### Exercise 1: `break`

Is code ka output likho:

```python
for number in range(1, 8):
    if number == 5:
        break
    print(number)
```

### Exercise 2: `continue`

Is code ka output likho:

```python
for number in range(1, 6):
    if number % 2 == 0:
        continue
    print(number)
```

### Exercise 3: Dictionary iteration

Code likho jo dictionary mein se sirf `Running` status wale equipment IDs print kare.

```python
equipment = {
    "AHU101": "Running",
    "FCU201": "Stopped",
    "VAV301": "Running",
    "FCU401": "Stopped"
}
```

### Exercise 4: `for` with `else`

Is code ka output batao:

```python
for number in range(3):
    if number == 5:
        break
else:
    print("Completed")
```

### Exercise 5: `while` loop

`while` loop use karke `1` se `10` tak numbers print karo.

### Exercise 6: Unpacking

Is list ke har record se work order number aur status print karo.

```python
records = [
    ("WO101", "Open"),
    ("WO102", "Closed"),
    ("WO103", "Open")
]
```

### Exercise 7: `pass` vs `continue`

In dono codes ke output mein kya difference hoga?

```python
for number in range(3):
    if number == 1:
        pass
    print(number)
```

```python
for number in range(3):
    if number == 1:
        continue
    print(number)
```

---

# Final Summary

* **Loop** kisi code ko repeatedly execute karne ke liye use hota hai.
* `for` iterable ke elements par iterate karta hai.
* `while` condition true rehne tak execute hota hai.
* `break` poora loop terminate karta hai.
* `continue` current iteration skip karta hai.
* Loop ka `else` normal completion par execute hota hai, `break` ke baad nahi.
* `pass` koi operation nahi karta; empty block ko valid banata hai.
* Dictionary par direct loop keys deta hai; `.values()` values aur `.items()` key-value pairs deta hai.
* Unpacking se tuple ya list ke elements multiple variables mein assign kar sakte hain.
* List slicing mein `start`, `stop` aur `step` se selected elements par iterate kar sakte hain.
* Python mein built-in `do-while` loop nahi hai, lekin `while True` aur `break` se similar behavior banaya ja sakta hai.
