# Chapter 4: Comments and Documentation

Python mein code sirf computer ke liye nahi hota. Code ko **human-readable** bhi banana zaroori hai, taake future mein aap khud ya koi aur developer samajh sake ke code kya kar raha hai.

Is purpose ke liye Python mein do important concepts hain:

1. **Comments**
2. **Documentation / Docstrings**

---

# Section 4.1: Single Line, Inline and Multiline Comments

## 1. Comment kya hota hai?

**Comment** code ke andar likha hua aisa text hota hai jise Python execute nahi karta.

Comment ka main purpose hota hai:

* code ko explain karna
* kisi logic ka reason batana
* future mein code samajhne mein help karna
* debugging ke waqt temporary code disable karna

Python mein comment `#` se start hota hai.

### Example

```python
# This is a comment

print("Hello")
```

Output:

```text
Hello
```

Python ne:

```python
# This is a comment
```

ko execute nahi kiya.

---

# 2. Single-Line Comment

Jab comment ek line mein ho, use **single-line comment** kehte hain.

```python
# Store employee name
name = "Muhammad"

print(name)
```

Yahan:

```python
# Store employee name
```

sirf explanation hai.

Python actual mein execute karega:

```python
name = "Muhammad"
print(name)
```

---

# 3. Comment code se pehle

Aksar comment us code se pehle likha jata hai jise woh explain kar raha ho.

```python
# Store equipment temperature
temperature = 22.5

print(temperature)
```

Yahan comment bata raha hai ke neeche wali variable kis purpose ke liye hai.

---

# 4. Inline Comment

**Inline comment** woh comment hai jo code ki same line par likha jata hai.

Example:

```python
temperature = 22.5  # Room temperature
```

Yahan:

```python
temperature = 22.5
```

actual code hai.

Aur:

```python
# Room temperature
```

comment hai.

### Important

`#` ke baad wali cheez Python execute nahi karta.

Example:

```python
age = 25  # Employee age
```

Python sirf:

```python
age = 25
```

ko execute karega.

---

# 5. Single-Line Comment ka Practical Example

Maintenance data mein:

```python
equipment_id = "MEP-AHU-001"  # AHU equipment ID
temperature = 22.5            # Current room temperature
status = "Running"             # Equipment status
```

Isse code dekhne wale ko quickly samajh aa jata hai ke variables ka purpose kya hai.

---

# 6. Code ko Comment Out Karna

Comments ka ek aur useful purpose hai: kisi code line ko temporarily disable karna.

Example:

```python
name = "Muhammad"

# print(name)

print("Program finished")
```

Output:

```text
Program finished
```

`print(name)` execute nahi hua kyunki uske start mein `#` laga hua hai.

Isko **commenting out code** kehte hain.

---

# 7. Multiple Lines ko Comment Karna

Agar multiple lines hain:

```python
# name = "Muhammad"
# age = 25
# department = "Maintenance"
```

Teenon lines comments hain.

Python inko execute nahi karega.

VS Code mein multiple selected lines ko comment/uncomment karne ke liye usually:

**Ctrl + /**

use kiya ja sakta hai.

---

# 8. Multiline Comments

Python mein officially separate `multiline comment` syntax nahi hai.

Lekin multiple lines ko `#` se comment kiya ja sakta hai:

```python
# This program reads
# equipment data
# and checks the status.
```

Ye proper Python comments hain.

---

## Triple Quotes ka Important Difference

Aapne triple quotes dekhe honge:

```python
"""
This looks like
a multiline comment.
"""
```

Lekin technically ye **comment nahi** hai.

Ye ek **string literal** hai.

Agar ye kisi function, class ya module ke beginning mein ho, to Python isko **docstring** ke taur par use kar sakta hai.

Example:

```python
def calculate_total():
    """
    Calculate the total amount.
    """
    pass
```

Yahan triple-quoted text **docstring** hai.

Is concept ko hum Section 4.3 mein detail mein dekhenge.

---

# Comment vs Docstring

| Comment                               | Docstring                                            |
| ------------------------------------- | ---------------------------------------------------- |
| `#` se start                          | Usually `""" """`                                    |
| Python execute nahi karta             | Python object ki documentation ka part ban sakta hai |
| Code explain karne ke liye            | Function/class/module explain karne ke liye          |
| `help()` se normally access nahi hota | `help()` se access ho sakta hai                      |
| Short explanation ke liye useful      | Formal documentation ke liye useful                  |

---

# Section 4.2: Programmatically Accessing Docstrings

Ab hum **docstring** ko samjhte hain.

## 1. Docstring kya hota hai?

**Docstring = Documentation String**

Ye string hoti hai jo kisi:

* module
* function
* class
* method

ko explain karti hai.

Example:

```python
def add(a, b):
    """Return the sum of two numbers."""
    return a + b
```

Yahan:

```python
"""Return the sum of two numbers."""
```

function ki **docstring** hai.

---

# 2. `__doc__`

Python mein kisi object ki documentation programmatically access karne ke liye:

```python
__doc__
```

use kar sakte hain.

Example:

```python
def add(a, b):
    """Return the sum of two numbers."""
    return a + b

print(add.__doc__)
```

Output:

```text
Return the sum of two numbers.
```

Yani hum program ke andar se function ki documentation read kar sakte hain.

---

# 3. `help()` aur `__doc__`

Dono documentation se related hain.

Example:

```python
def add(a, b):
    """Return the sum of two numbers."""
    return a + b
```

Ab:

```python
print(add.__doc__)
```

Output:

```text
Return the sum of two numbers.
```

Aur:

```python
help(add)
```

Output mein function ki documentation bhi show hogi.

### Simple difference

```text
__doc__
    ↓
Sirf docstring access karta hai

help()
    ↓
Detailed help/documentation display karta hai
```

---

# 4. Module ki Docstring Access Karna

Agar kisi Python file ke top par docstring ho:

```python
"""
Equipment management utilities.
"""

def get_status():
    return "Running"
```

To module ki documentation:

```python
print(__doc__)
```

se access ho sakti hai.

---

# 5. Class ki Docstring

```python
class Equipment:
    """Represent a piece of equipment."""

    pass
```

Ab:

```python
print(Equipment.__doc__)
```

Output:

```text
Represent a piece of equipment.
```

---

# 6. Method ki Docstring

```python
class Equipment:

    def start(self):
        """Start the equipment."""
        print("Equipment started")
```

Access:

```python
print(Equipment.start.__doc__)
```

Output:

```text
Start the equipment.
```

---

# Section 4.3: Write Documentation Using Docstrings

Ab hum seekhte hain ke **proper docstrings kaise likhte hain**.

---

# 1. Function mein Docstring

Basic structure:

```python
def function_name():
    """Explain what the function does."""
    
    # function code
```

Example:

```python
def calculate_total(price, quantity):
    """Calculate total price."""
    
    return price * quantity
```

Yahan docstring function ka purpose explain kar rahi hai.

---

# 2. Docstring Function ke andar kahan hoti hai?

Docstring **function body ki first statement** honi chahiye.

Correct:

```python
def calculate_total(price, quantity):
    """Calculate total price."""
    return price * quantity
```

Agar pehle koi aur statement aa jaye:

```python
def calculate_total(price, quantity):
    print("Starting")
    """Calculate total price."""
    return price * quantity
```

to ye function ki official docstring nahi banegi.

Isliye rule yaad rakhein:

```text
def
 ↓
Docstring FIRST
 ↓
Function code
```

---

# 3. Useful Function Documentation

Simple function:

```python
def calculate_total(price, quantity):
    """Calculate total price."""
    return price * quantity
```

Lekin complex function ke liye documentation zyada detailed honi chahiye.

Example:

```python
def calculate_total(price, quantity):
    """
    Calculate the total price.

    Parameters:
        price: Price of one item.
        quantity: Number of items.

    Returns:
        Total price.
    """
    return price * quantity
```

Ab function ko read karne wale ko easily samajh aa raha hai:

* function kya karta hai
* input kya hai
* output kya hai

---

# 4. Parameters

Function:

```python
def calculate_total(price, quantity):
```

mein:

```text
price
quantity
```

parameters hain.

Docstring mein unko explain kar sakte hain:

```python
"""
Calculate the total price.

Parameters:
    price: Price of one item.
    quantity: Number of items.

Returns:
    Total price.
"""
```

---

# 5. Return Value

Function:

```python
def calculate_total(price, quantity):
    """Calculate total price."""
    return price * quantity
```

Yahan function result return karta hai.

Docstring mein:

```text
Returns:
    Total price.
```

likh kar explain kar sakte hain.

---

# 6. Practical Equipment Example

Suppose hum equipment ka status check karna chahte hain:

```python
def check_equipment_status(status):
    """
    Check whether equipment is running.

    Parameters:
        status: Current equipment status.

    Returns:
        True if equipment is running, otherwise False.
    """
    
    return status == "Running"
```

Use:

```python
result = check_equipment_status("Running")

print(result)
```

Output:

```text
True
```

Documentation:

```python
print(check_equipment_status.__doc__)
```

se function ki documentation bhi mil jayegi.

---

# 7. Class Documentation

Classes ke liye bhi docstring use hoti hai.

```python
class Equipment:
    """
    Represent a maintenance equipment item.
    """

    def __init__(self, equipment_id, status):
        self.equipment_id = equipment_id
        self.status = status
```

Ab:

```python
print(Equipment.__doc__)
```

Output:

```text
Represent a maintenance equipment item.
```

---

# 8. Module Documentation

Ek Python file ke top par module ki documentation likh sakte hain.

Example `equipment.py`:

```python
"""
Utilities for managing equipment data.
"""

def get_equipment_status():
    return "Running"
```

Module ke top par jo docstring hai woh **module docstring** hai.

---

# 9. Good Documentation ka Rule

Documentation likhte waqt sirf ye na likhein:

```python
def calculate_total(price, quantity):
    """Function."""
```

Ye technically documentation hai, lekin useful nahi.

Better:

```python
def calculate_total(price, quantity):
    """Calculate total price from unit price and quantity."""
```

Aur complex function:

```python
def calculate_total(price, quantity):
    """
    Calculate the total price.

    Parameters:
        price: Price of one item.
        quantity: Number of items.

    Returns:
        Total price.
    """
    return price * quantity
```

---

# 10. Comment aur Docstring kab use karein?

### Comment

Jab aap code ki **implementation/logic** explain karna chahte hain.

```python
# Skip the header row
rows = output_data[1:]
```

Comment bata raha hai ke ye line kyun hai.

### Docstring

Jab aap **function/class/module ka purpose** document karna chahte hain.

```python
def create_work_order_folder(work_order):
    """Create a folder for the specified work order."""
```

---

# 11. Aapke Python Automation Context ka Example

Suppose aapke paas work-order folders create karne ka function hai:

```python
def create_work_order_folders(output_data):
    """
    Create folders for work orders.

    Parameters:
        output_data: Work-order data including the header row.

    Returns:
        None.
    """

    rows = output_data[1:]

    for row in rows:
        print(row)
```

Yahan:

```python
"""
Create folders for work orders.
...
"""
```

function ki documentation hai.

Aur:

```python
# Skip the header row
rows = output_data[1:]
```

implementation comment hai.

Dono ka purpose different hai.

---

# 12. Ek Important Rule

**Comment ye bataye ke code kyun kar raha hai.**

Bad comment:

```python
# Add 1 to x
x = x + 1
```

Code already obvious hai.

Better comment:

```python
# Move to the next work-order row
x = x + 1
```

Yani comment ko useful information deni chahiye.

---

# 13. Complete Example

```python
"""
Utilities for processing equipment data.
"""


def calculate_total(price, quantity):
    """
    Calculate the total price.

    Parameters:
        price: Price of one item.
        quantity: Number of items.

    Returns:
        Total price.
    """

    # Multiply unit price by quantity
    total = price * quantity

    return total


price = 100
quantity = 5

total = calculate_total(price, quantity)

print(total)
```

Output:

```text
500
```

Documentation access:

```python
print(calculate_total.__doc__)
```

---

# Chapter 4 — Quick Revision

## Comments

```python
# This is a comment
```

Python comment ko execute nahi karta.

### Inline comment

```python
temperature = 22.5  # Room temperature
```

### Multiple-line comments

```python
# Line 1
# Line 2
# Line 3
```

---

## Docstrings

Function:

```python
def add(a, b):
    """Return the sum of two numbers."""
    return a + b
```

Access:

```python
print(add.__doc__)
```

Help:

```python
help(add)
```

---

## Module Docstring

```python
"""
Equipment data utilities.
"""
```

---

## Class Docstring

```python
class Equipment:
    """Represent an equipment item."""
```

---

# Sabse Important Difference

```text
COMMENT
   ↓
# ...
   ↓
Code/logic ko explain karta hai


DOCSTRING
   ↓
""" ... """
   ↓
Function/Class/Module ko document karta hai
   ↓
__doc__ aur help() se access ho sakta hai
```

### Golden Rule

**`#` → Comment**

**`""" """` → Docstring**

**`__doc__` → Docstring ko programmatically read karna**

**`help()` → Documentation ko inspect karna**

Chapter 4 ke teen sections ka core concept yehi hai.
