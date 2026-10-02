# Chapter 15: Comparisons

Python mein **comparison operators** do values ya expressions ka comparison karne ke liye use hote hain.

Comparison ka result aam tor par Boolean value hota hai:

* `True` — condition sahi hai.
* `False` — condition ghalat hai.

Example:

```python
a = 10
b = 20

print(a < b)
print(a == b)
```

Output:

```text
True
False
```

`a`, `b` se chhota hai, is liye pehla result `True` hai. Dono equal nahi hain, is liye doosra result `False` hai.

## 15.1 Chain Comparisons

Python mein hum ek hi expression mein multiple comparisons chain kar sakte hain.

Example:

```python
temperature = 25

print(20 < temperature < 30)
```

Output:

```text
True
```

Iska matlab hai:

```python
20 < temperature and temperature < 30
```

Dono conditions `True` honi chahiye.

Agar temperature `35` ho:

```python
temperature = 35

print(20 < temperature < 30)
```

Output:

```text
False
```

Kyun ke `35 < 30` false hai.

### Multiple comparisons

```python
temperature = 25

print(10 < temperature < 30 < 40)
```

Output:

```text
True
```

Python is expression ko is tarah evaluate karta hai:

```python
10 < temperature
temperature < 30
30 < 40
```

Tamam comparisons true hon to poora expression `True` hota hai.

### Work order example

```python
priority = 3

if 1 <= priority <= 5:
    print("Valid priority")
else:
    print("Invalid priority")
```

Output:

```text
Valid priority
```

Yahan priority `1` se `5` ke darmiyan honi chahiye, dono limits included hain.

### Chained comparison aur `and`

Ye dono expressions equivalent hain:

```python
1 <= priority <= 5
```

```python
1 <= priority and priority <= 5
```

Lekin chained comparison zyada concise aur readable hota hai.

**Important:** Python chained comparisons ko mathematical notation ki tarah samajhta hai. Ye `1 <= priority <= 5` ko `(1 <= priority) <= 5` ki tarah evaluate nahi karta.

---

## 15.2 Comparison by `is` vs `==`

Python mein `is` aur `==` dono compare karte hain, lekin inka purpose different hai.

* `==` values ki equality check karta hai.
* `is` check karta hai ke dono references **same object** ko point kar rahe hain ya nahi.

### `==` example

```python
a = [10, 20, 30]
b = [10, 20, 30]

print(a == b)
```

Output:

```text
True
```

Dono lists ki values same hain, is liye `==` ka result `True` hai.

### `is` example

```python
a = [10, 20, 30]
b = [10, 20, 30]

print(a is b)
```

Output:

```text
False
```

Dono lists ki values same hain, lekin ye memory mein separate objects hain.

### Same object ka example

```python
a = [10, 20, 30]
b = a

print(a == b)
print(a is b)
```

Output:

```text
True
True
```

Yahan `b = a` se koi nayi list create nahi hoti. `a` aur `b` dono same list object ko refer karte hain.

### `is` aur mutable objects

```python
a = [10, 20]
b = a

b.append(30)

print(a)
print(b)
```

Output:

```text
[10, 20, 30]
[10, 20, 30]
```

Dono variables same list ko refer kar rahe hain. Is liye `b` mein change karne se `a` ke through bhi updated list nazar aati hai.

### `None` ke saath `is`

Python mein `None` check karne ke liye `is` use karna recommended hai.

```python
result = None

if result is None:
    print("No result available")
```

Output:

```text
No result available
```

Agar check karna ho ke value `None` nahi hai:

```python
if result is not None:
    print("Result available")
```

**Yaad rakho:**

| Operator | Kya check karta hai?          |
| -------- | ----------------------------- |
| `==`     | Values equal hain ya nahi     |
| `is`     | Dono same object hain ya nahi |
| `!=`     | Values equal nahi hain        |
| `is not` | Dono same object nahi hain    |

Strings, lists aur numbers ki value compare karne ke liye aam tor par `==` use karo. `is` ko object identity aur `None` checks ke liye use karo.

---

## 15.3 Greater than or less than

Python mein greater than aur less than ke liye ye operators use hote hain:

| Operator | Meaning                                    |
| -------- | ------------------------------------------ |
| `>`      | Greater than — se bara                     |
| `<`      | Less than — se chhota                      |
| `>=`     | Greater than or equal to — bara ya barabar |
| `<=`     | Less than or equal to — chhota ya barabar  |

### Greater than `>`

```python
a = 20
b = 10

print(a > b)
```

Output:

```text
True
```

Kyun ke `20`, `10` se bara hai.

Agar values equal hon:

```python
a = 10
b = 10

print(a > b)
```

Output:

```text
False
```

`>` equal values ko include nahi karta.

### Less than `<`

```python
a = 10
b = 20

print(a < b)
```

Output:

```text
True
```

Kyun ke `10`, `20` se chhota hai.

### Greater than or equal to `>=`

```python
temperature = 30

print(temperature >= 30)
```

Output:

```text
True
```

`>=` mein value ka bara hona ya equal hona dono allowed hain.

### Less than or equal to `<=`

```python
temperature = 25

print(temperature <= 30)
```

Output:

```text
True
```

### HVAC example

Maan lo AHU ka actual temperature aur maximum allowed temperature compare karna hai.

```python
actual_temp = 32
max_temp = 30

if actual_temp > max_temp:
    print("Temperature is above limit")
else:
    print("Temperature is within limit")
```

Output:

```text
Temperature is above limit
```

Agar maximum limit ko bhi acceptable rakhna ho, to `>` ki jagah `>=` ya `<=` condition ke mutabiq use kar sakte ho.

---

## 15.4 Not equal to

Python mein `!=` ka matlab hai **not equal to**.

Agar do values equal nahi hain, to result `True` hota hai.

```python
a = 10
b = 20

print(a != b)
```

Output:

```text
True
```

Dono values different hain.

Agar values equal hon:

```python
a = 10
b = 10

print(a != b)
```

Output:

```text
False
```

### Strings ke saath

```python
status = "Running"

print(status != "Stopped")
```

Output:

```text
True
```

String values case-sensitive hoti hain:

```python
print("Running" != "running")
```

Output:

```text
True
```

`Running` aur `running` different strings hain.

### Work order example

```python
status = "Open"

if status != "Closed":
    print("Work order is still active")
else:
    print("Work order is closed")
```

Output:

```text
Work order is still active
```

Yahan condition check karti hai ke status `"Closed"` ke barabar nahi hai.

---

## 15.5 Equal To

Python mein equality check karne ke liye `==` use hota hai.

**Important:** `=` aur `==` different hain.

* `=` variable ko value assign karta hai.
* `==` do values ka comparison karta hai.

### Equal values

```python
a = 10
b = 10

print(a == b)
```

Output:

```text
True
```

Dono values equal hain.

### Different values

```python
a = 10
b = 20

print(a == b)
```

Output:

```text
False
```

### Strings ke saath

```python
status = "Running"

print(status == "Running")
print(status == "Stopped")
```

Output:

```text
True
False
```

### Lists ke saath

```python
a = [1, 2, 3]
b = [1, 2, 3]

print(a == b)
```

Output:

```text
True
```

Lists ke elements same order mein equal hain, is liye result `True` hai.

Agar order different ho:

```python
a = [1, 2, 3]
b = [3, 2, 1]

print(a == b)
```

Output:

```text
False
```

Lists ordered hoti hain, is liye elements ka order bhi equality mein matter karta hai.

### Practical HVAC example

```python
ahu_status = "ON"

if ahu_status == "ON":
    print("AHU is running")
else:
    print("AHU is not running")
```

Output:

```text
AHU is running
```

Yahan `==` check karta hai ke `ahu_status` ki value `"ON"` ke equal hai ya nahi.

---

# Chapter 15: Quick Revision

| Operator | Meaning               | Example      | Result                      |
| -------- | --------------------- | ------------ | --------------------------- |
| `==`     | Equal to              | `10 == 10`   | `True`                      |
| `!=`     | Not equal to          | `10 != 20`   | `True`                      |
| `>`      | Greater than          | `20 > 10`    | `True`                      |
| `<`      | Less than             | `10 < 20`    | `True`                      |
| `>=`     | Greater than or equal | `10 >= 10`   | `True`                      |
| `<=`     | Less than or equal    | `10 <= 20`   | `True`                      |
| `is`     | Same object           | `a is b`     | Object par depend karta hai |
| `is not` | Different objects     | `a is not b` | Object par depend karta hai |

## Practice Exercises

**Exercise 1:** Output kya hoga?

```python
a = 15
b = 20

print(a < b)
print(a > b)
print(a != b)
print(a == b)
```

**Exercise 2:** Output kya hoga?

```python
temperature = 25

print(20 <= temperature <= 30)
print(temperature < 20 or temperature > 30)
```

**Exercise 3:** `is` aur `==` ka result batao.

```python
a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(a == b)
print(a is b)
print(a is c)
```

**Exercise 4:** Is code ka output kya hoga?

```python
priority = 4

if 1 <= priority <= 5:
    print("Valid")
else:
    print("Invalid")
```

**Exercise 5:** `=` aur `==` mein kya difference hai? Dono ka ek example likho.

---

## Final Summary

* Comparison operators do values ka comparison karte hain aur aam tor par `True` ya `False` return karte hain.
* `==` values ki equality check karta hai.
* `!=` values ke different hone ko check karta hai.
* `>`, `<`, `>=`, `<=` numerical ya compatible values ka comparison karte hain.
* Chained comparisons, jaise `1 <= x <= 5`, multiple comparisons ko concise banate hain.
* `is` object identity check karta hai, jab ke `==` value equality check karta hai.
* `None` check karne ke liye `is None` aur `is not None` use karo.
