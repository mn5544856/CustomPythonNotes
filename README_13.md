# Chapter 13: Variable Scope and Binding

## Scope kya hota hai?

**Scope** ka matlab hai:

> Kisi variable ka woh area jahan Python us variable ko access kar sakta hai.

Example:

```python
def test():
    name = "Muhammad"
    print(name)

test()
```

Yahan `name` function ke andar bana hai.

Isliye `name` ka scope function ke andar hai.

Function ke bahar:

```python
print(name)
```

error dega, kyunki `name` function ke local scope mein hai.

---

# Python ke important scopes

Python mein commonly ye scopes samjhe jate hain:

```text
Local
  ↓
Enclosing
  ↓
Global
  ↓
Built-in
```

Python variable ko lookup karte waqt commonly **LEGB rule** use karta hai:

```text
L = Local
E = Enclosing
G = Global
B = Built-in
```

Isko hum chapter mein examples ke through samjhenge.

---

# 13.1 Nonlocal Variables

`nonlocal` nested functions ke case mein use hota hai.

Sabse pehle nested function samjho:

```python
def outer():
    x = 10

    def inner():
        print(x)

    inner()

outer()
```

Output:

```text
10
```

`inner()` ke andar `x` directly local nahi hai.

Python `outer()` ke enclosing scope mein `x` dhoond leta hai.

---

## `nonlocal` kab use hota hai?

Agar inner function ko enclosing function ke variable ki **value change** karni ho, to `nonlocal` use karte hain.

Example:

```python
def outer():
    count = 0

    def inner():
        nonlocal count
        count += 1
        print(count)

    inner()
    inner()

outer()
```

Output:

```text
1
2
```

Yahan:

```python
nonlocal count
```

ka matlab hai:

> `count` ko new local variable mat samjho; outer function wale `count` ko use karo.

---

## Agar `nonlocal` na lagao

```python
def outer():
    count = 0

    def inner():
        count += 1

    inner()

outer()
```

Ye error dega:

```text
UnboundLocalError
```

Kyun?

Python dekhta hai:

```python
count += 1
```

Aur samajhta hai ke `inner()` ke andar `count` local variable hai.

Lekin us local variable ko value assign hone se pehle read kiya ja raha hai.

Isliye error.

---

## Practical example

Work-order counter:

```python
def create_counter():
    count = 0

    def next_work_order():
        nonlocal count
        count += 1
        return count

    return next_work_order
```

Ab:

```python
counter = create_counter()

print(counter())
print(counter())
print(counter())
```

Output:

```text
1
2
3
```

`count` outer function mein hai, lekin inner function usko modify kar raha hai.

Is case mein `nonlocal` useful hai.

---

# 13.2 Global Variables

**Global variable** function ke bahar define hota hai.

Example:

```python
company = "ABC"

def show_company():
    print(company)

show_company()
```

Output:

```text
ABC
```

Function ne global variable ko read kiya.

---

## Global variable ko modify karna

Agar function ke andar global variable ko change karna ho:

```python
company = "ABC"

def change_company():
    global company
    company = "XYZ"

change_company()

print(company)
```

Output:

```text
XYZ
```

Yahan:

```python
global company
```

Python ko batata hai:

> Is function mein `company` local variable nahi hai; global `company` ko modify karo.

---

## `global` ke baghair

```python
company = "ABC"

def change_company():
    company = "XYZ"

change_company()

print(company)
```

Output:

```text
ABC
```

Kyun?

Function ke andar:

```python
company = "XYZ"
```

ek **new local variable** create hua.

Global `company` change nahi hua.

---

## Important difference

```python
company = "ABC"

def test():
    print(company)
```

Yahan global variable ko **read** karne ke liye `global` ki zaroorat nahi.

Lekin:

```python
company = "ABC"

def test():
    global company
    company = "XYZ"
```

Global variable ko **modify** karne ke liye `global` chahiye.

---

# 13.3 Local Variables

Function ke andar create hone wala variable normally **local variable** hota hai.

Example:

```python
def calculate():
    temperature = 25
    print(temperature)

calculate()
```

Yahan:

```python
temperature
```

local variable hai.

Function ke bahar:

```python
print(temperature)
```

error:

```text
NameError
```

Kyunki `temperature` ka scope `calculate()` ke andar hai.

---

## Har function ka apna local scope

```python
def first():
    value = 10
    print(value)


def second():
    value = 20
    print(value)


first()
second()
```

Output:

```text
10
20
```

Dono functions mein variable ka naam same hai:

```python
value
```

Lekin dono separate local variables hain.

---

## Local variable global variable ko hide kar sakta hai

Example:

```python
temperature = 20

def check():
    temperature = 30
    print(temperature)

check()

print(temperature)
```

Output:

```text
30
20
```

Function ke andar:

```python
temperature = 30
```

local variable hai.

Global:

```python
temperature = 20
```

alag variable hai.

Isko kabhi kabhi **shadowing** bhi kaha jata hai.

---

# 13.4 The `del` command

`del` ka use Python mein kisi variable/reference ko remove karne ke liye kiya ja sakta hai.

Example:

```python
name = "Muhammad"

print(name)

del name
```

Ab:

```python
print(name)
```

karoge to:

```text
NameError
```

aayega.

Kyunki `name` ka binding remove ho chuka hai.

---

## `del` list item

`del` sirf variables ke liye nahi hai.

List:

```python
numbers = [10, 20, 30, 40]
```

Index `1` remove:

```python
del numbers[1]
```

Ab:

```python
print(numbers)
```

Output:

```text
[10, 30, 40]
```

---

## List ka slice delete karna

```python
numbers = [10, 20, 30, 40, 50]

del numbers[1:4]

print(numbers)
```

Output:

```text
[10, 50]
```

`1:4` mein indexes:

```text
1 → 20
2 → 30
3 → 40
```

remove ho gaye.

---

## Dictionary se item delete

```python
equipment = {
    "id": "AHU-01",
    "floor": 10,
    "status": "Running"
}

del equipment["floor"]

print(equipment)
```

Output:

```text
{'id': 'AHU-01', 'status': 'Running'}
```

---

## `del` aur `None` same nahi hain

Ye important difference hai.

```python
x = None
```

Variable `x` **exist karta hai**.

Bas uski value `None` hai.

Lekin:

```python
del x
```

variable ka binding remove karta hai.

So:

```text
x = None
```

means:

> Variable exists, value `None` hai.

Aur:

```text
del x
```

means:

> Is name ka binding remove karo.

---

# 13.5 Functions skip class scope when looking up names

Ye thoda advanced topic hai.

Suppose:

```python
class Equipment:
    status = "Running"

    def show(self):
        def inner():
            print(status)

        inner()
```

Yahan `inner()` `status` ko automatically class scope se nahi uthata.

Python ka normal name lookup:

```text
Local
↓
Enclosing function
↓
Global
↓
Built-in
```

**Class scope is lookup chain ka normal enclosing function scope nahi hai.**

Isliye class ke andar defined variable ko method ke andar normally class variable ki tarah direct naam se access nahi karte.

Correct approach:

```python
class Equipment:
    status = "Running"

    def show(self):
        print(self.status)
```

Yahan:

```python
self.status
```

object/class attribute ko explicitly access kar raha hai.

---

## Example

```python
class AHU:
    status = "Running"

    def show_status(self):
        print(self.status)


ahu = AHU()

ahu.show_status()
```

Output:

```text
Running
```

Yahan `self.status` use kiya gaya hai.

---

# 13.6 Local vs Global Scope

Ab local aur global ko compare karte hain.

## Global

Function ke bahar:

```python
company = "ABC"
```

Ye global variable hai.

## Local

Function ke andar:

```python
def test():
    name = "Muhammad"
```

`name` local variable hai.

---

## Example

```python
company = "ABC"

def work():
    employee = "Ali"

    print(company)
    print(employee)

work()
```

Output:

```text
ABC
Ali
```

Function global `company` ko read kar sakta hai.

Lekin:

```python
print(employee)
```

function ke bahar nahi chalega.

---

# Global variable ko local variable se shadow karna

```python
status = "Global"

def test():
    status = "Local"
    print(status)

test()

print(status)
```

Output:

```text
Local
Global
```

Function ke andar local `status` mil gaya, isliye Python ne global `status` ko use nahi kiya.

---

# LEGB Rule

Python name lookup ko samajhne ke liye **LEGB** yaad rakho:

```text
L → Local
E → Enclosing
G → Global
B → Built-in
```

Example:

```python
x = "global"

def outer():
    x = "enclosing"

    def inner():
        x = "local"
        print(x)

    inner()

outer()
```

Output:

```text
local
```

Python ko `x` sabse pehle Local scope mein mil gaya.

---

## Local na ho

```python
x = "global"

def outer():
    x = "enclosing"

    def inner():
        print(x)

    inner()

outer()
```

Output:

```text
enclosing
```

`inner()` mein local `x` nahi tha.

Python enclosing scope mein gaya.

---

## Local aur enclosing dono na ho

```python
x = "global"

def outer():

    def inner():
        print(x)

    inner()

outer()
```

Output:

```text
global
```

Python global scope mein `x` dhoond leta hai.

---

## Global bhi na ho

Agar `x` kahin nahi hai:

```python
def test():
    print(x)

test()
```

Output:

```text
NameError
```

Python ne:

```text
Local
↓
Enclosing
↓
Global
↓
Built-in
```

mein `x` nahi paya.

---

# 13.7 Binding Occurrence

Ab **binding** samjho.

Python mein kisi name ko kisi object/value ke saath associate karna **binding** kehlata hai.

Example:

```python
x = 10
```

Yahan:

```text
x
↓
10
```

`x` name ko `10` object ke saath bind kiya gaya.

---

## Assignment creates a binding

```python
name = "Muhammad"
```

`name` bind hua `"Muhammad"` se.

Phir:

```python
name = "Ali"
```

Ab `name` new value se bind ho gaya.

---

## Function parameter bhi binding create karta hai

```python
def greet(name):
    print(name)
```

Jab:

```python
greet("Muhammad")
```

call hota hai, parameter:

```python
name
```

argument:

```text
"Muhammad"
```

se bind hota hai.

---

## Loop variable bhi binding create karta hai

```python
for equipment in ["AHU-01", "AHU-02", "AHU-03"]:
    print(equipment)
```

Har iteration mein:

```python
equipment
```

current item se bind hota hai.

---

## Import bhi binding create karta hai

```python
import math
```

Yahan:

```text
math
```

name module object se bind hota hai.

Agar:

```python
import math as m
```

likho:

```text
m
```

module se bind hota hai.

---

## `class` definition bhi binding create karti hai

```python
class Equipment:
    pass
```

Ab:

```text
Equipment
```

class object se bind hai.

---

## `def` bhi binding create karta hai

```python
def calculate():
    return 10
```

Yahan:

```text
calculate
```

function object se bind hota hai.

---

# Binding aur assignment ko simple example se samjho

```python
x = 10
```

Isko beginner level par:

> `x` mein `10` store hua.

keh sakte ho.

Lekin technically Python mein:

> Name `x` object `10` ko refer/bind karta hai.

Phir:

```python
x = 20
```

Ab `x` `20` object ko refer karta hai.

---

# Important: Variable box nahi hai

Beginner mental model:

```text
x = 10
```

ko aksar box samjha jata hai:

```text
┌─────┐
│  x  │
│ 10  │
└─────┘
```

Python mein better mental model:

```text
x ─────→ 10
```

`x` ek **name/reference** hai jo object ko point/bind karta hai.

---

# Scope + Binding ka combined example

```python
x = "global"

def outer():
    x = "enclosing"

    def inner():
        x = "local"
        print(x)

    inner()

outer()
```

Yahan 3 different bindings hain:

```text
Global:
x → "global"

Enclosing:
x → "enclosing"

Local:
x → "local"
```

`inner()` ke andar Python ko local `x` mil gaya.

Isliye output:

```text
local
```

---

# `global` vs `nonlocal`

Ye dono confuse mat karna.

| Keyword    | Kis scope ko target karta hai?   |
| ---------- | -------------------------------- |
| `global`   | Global scope                     |
| `nonlocal` | Nearest enclosing function scope |

Example:

```python
x = 10

def test():
    global x
    x = 20
```

`global x` → global `x`.

Nested example:

```python
def outer():
    x = 10

    def inner():
        nonlocal x
        x = 20

    inner()
    print(x)

outer()
```

Output:

```text
20
```

`nonlocal x` → outer function ka `x`.

---

# Practical Work-Order Example

Global configuration:

```python
BASE_FOLDER = "D:/work_orders"

def create_folder(work_order):
    print(BASE_FOLDER)
    print(work_order)
```

`BASE_FOLDER` global hai.

`work_order` function parameter hai aur local scope mein available hai.

Call:

```python
create_folder("WO-1001")
```

Output:

```text
D:/work_orders
WO-1001
```

Agar function ke andar:

```python
BASE_FOLDER = "D:/other"
```

likho, to normally global value change nahi hogi.

Agar global value change karni ho:

```python
global BASE_FOLDER
```

use karna padega.

---

# Important Best Practice

`global` aur `nonlocal` useful hain, lekin unnecessarily use nahi karna chahiye.

Aksar better design hota hai:

```python
def calculate(value):
    result = value * 2
    return result
```

Instead of global state:

```python
result = 0

def calculate(value):
    global result
    result = value * 2
```

Pehla version zyada predictable aur maintainable hota hai.

---

# Chapter 13 Quick Summary

### Scope

Variable **kahan accessible hai**.

### Local

Function ke andar ka variable:

```python
def test():
    x = 10
```

### Global

Function ke bahar ka variable:

```python
x = 10
```

### Enclosing

Nested function ke outer function ka scope.

### `global`

Global variable ko function ke andar modify karne ke liye:

```python
global x
```

### `nonlocal`

Outer/enclosing function ke variable ko nested function se modify karne ke liye:

```python
nonlocal x
```

### `del`

Name, list item, dictionary item, etc. ka binding/reference remove kar sakta hai:

```python
del x
```

### LEGB

```text
L → Local
E → Enclosing
G → Global
B → Built-in
```

### Binding

Name ko object ke saath associate karna:

```python
x = 10
```

```text
x ───→ 10
```

### Final mental model

```text
Python ko koi variable/name mile
          ↓
     Local scope?
          ↓ No
    Enclosing scope?
          ↓ No
     Global scope?
          ↓ No
      Built-in?
          ↓ No
       NameError
```

Is chapter ka sabse important concept **LEGB + `global` + `nonlocal`** hai.
