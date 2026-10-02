# Chapter 7: Enum

## Enum kya hota hai?

`Enum` ka matlab **Enumeration** hai.

Enum ka use tab hota hai jab kisi variable ke liye **limited aur predefined values** hon.

Example: Equipment ka status sirf ye ho sakta hai:

```text
RUNNING
STOPPED
FAULT
MAINTENANCE
```

Instead of random strings use karne ke:

```python
status = "RUNNING"
```

hum Enum bana sakte hain:

```python
Status.RUNNING
```

Isse code zyada **clear, controlled aur readable** hota hai.

---

# 7.1 Creating an Enum

## 1. Modern Python mein Enum

Python 3 mein `enum` standard library ka part hai.

Import:

```python
from enum import Enum
```

Phir Enum class create:

```python
from enum import Enum

class Status(Enum):
    RUNNING = 1
    STOPPED = 2
    FAULT = 3
    MAINTENANCE = 4
```

Yahan:

```text
Status
 ├── RUNNING
 ├── STOPPED
 ├── FAULT
 └── MAINTENANCE
```

Ye values **Enum members** kehlati hain.

---

# 2. Enum member access karna

```python
print(Status.RUNNING)
```

Output:

```text
Status.RUNNING
```

Sirf actual value chahiye:

```python
print(Status.RUNNING.value)
```

Output:

```text
1
```

Aur member ka name:

```python
print(Status.RUNNING.name)
```

Output:

```text
RUNNING
```

So:

```text
Status.RUNNING
      │
      ├── .name  → "RUNNING"
      │
      └── .value → 1
```

---

# 3. Enum kyun use karte hain?

Suppose normal strings use kar rahe hain:

```python
status = "RUNNING"
```

Problem ye ho sakti hai:

```python
status = "running"
```

ya:

```python
status = "Runing"
```

ya:

```python
status = "RUN"
```

Python in strings ko automatically valid/invalid nahi samjhega.

Enum mein predefined members hote hain:

```python
Status.RUNNING
Status.STOPPED
Status.FAULT
Status.MAINTENANCE
```

Isliye allowed choices clearly define ho jati hain.

---

# 4. Enum ko variable mein store karna

```python
current_status = Status.RUNNING

print(current_status)
```

Output:

```text
Status.RUNNING
```

Check:

```python
print(type(current_status))
```

Output roughly:

```text
<enum 'Status'>
```

---

# 5. Enum member compare karna

```python
current_status = Status.RUNNING

if current_status == Status.RUNNING:
    print("Equipment is running")
```

Output:

```text
Equipment is running
```

Ye important pattern hai:

```python
if status == Status.FAULT:
    print("Check equipment")
```

---

# 6. Enum values ka type

Humne likha:

```python
class Status(Enum):
    RUNNING = 1
    STOPPED = 2
    FAULT = 3
```

Yahan values integers hain.

```python
print(Status.FAULT.value)
```

Output:

```text
3
```

Lekin:

```python
print(type(Status.FAULT))
```

Enum member hai.

Aur:

```python
print(type(Status.FAULT.value))
```

Output:

```text
<class 'int'>
```

Yani:

```text
Status.FAULT
     ↓
 Enum member

Status.FAULT.value
     ↓
    3
     ↓
   int
```

---

# 7. String values ke saath Enum

Enum values integers hona zaroori nahi.

```python
from enum import Enum

class Status(Enum):
    RUNNING = "running"
    STOPPED = "stopped"
    FAULT = "fault"
```

Ab:

```python
print(Status.RUNNING.value)
```

Output:

```text
running
```

Ye APIs, JSON aur configuration data mein useful ho sakta hai.

---

# 8. Enum se value ko member mein convert karna

Suppose:

```python
class Status(Enum):
    RUNNING = "running"
    STOPPED = "stopped"
    FAULT = "fault"
```

Agar input string hai:

```python
status_text = "fault"
```

To:

```python
status = Status(status_text)
```

Ab:

```python
print(status)
```

Output:

```text
Status.FAULT
```

Aur:

```python
print(status.name)
```

Output:

```text
FAULT
```

Yani:

```text
"fault"
   ↓
Status("fault")
   ↓
Status.FAULT
```

---

# 9. Invalid value

Agar:

```python
status = Status("broken")
```

aur `"broken"` Enum mein defined nahi hai, to Python `ValueError` raise karega.

Iska benefit ye hai ke invalid values detect ho sakti hain.

---

# 10. Python 2.4 through 3.3 ka kya matlab hai?

Aapki book mein section ka naam:

**"Creating an enum (Python 2.4 through 3.3)"**

hai.

Iska reason historical hai.

Python ke old versions mein modern built-in `enum` module available nahi tha.

Modern Python mein:

```python
from enum import Enum
```

use karna chahiye.

Aap current Python 3 use kar rahe ho, to **old workaround ki zaroorat nahi**.

---

# 11. 7.2 Iteration

Enum ke members par `for` loop laga sakte hain.

Example:

```python
from enum import Enum

class Status(Enum):
    RUNNING = 1
    STOPPED = 2
    FAULT = 3
    MAINTENANCE = 4

for status in Status:
    print(status)
```

Output:

```text
Status.RUNNING
Status.STOPPED
Status.FAULT
Status.MAINTENANCE
```

Yahan:

```python
for status in Status:
```

ka matlab hai:

> `Status` Enum ke har member ko one-by-one `status` variable mein lao.

---

# 12. `.name` aur `.value` ke saath iteration

Agar names chahiye:

```python
for status in Status:
    print(status.name)
```

Output:

```text
RUNNING
STOPPED
FAULT
MAINTENANCE
```

Agar values chahiye:

```python
for status in Status:
    print(status.value)
```

Output:

```text
1
2
3
4
```

Dono:

```python
for status in Status:
    print(status.name, status.value)
```

Output:

```text
RUNNING 1
STOPPED 2
FAULT 3
MAINTENANCE 4
```

---

# 13. Enum ko list mein convert karna

```python
statuses = list(Status)

print(statuses)
```

Result:

```text
[
    Status.RUNNING,
    Status.STOPPED,
    Status.FAULT,
    Status.MAINTENANCE
]
```

Ab:

```python
print(len(statuses))
```

Output:

```text
4
```

---

# 14. Practical HVAC example

HVAC equipment ke operating modes define karte hain:

```python
from enum import Enum

class HVACMode(Enum):
    OFF = 0
    COOLING = 1
    HEATING = 2
    FAN_ONLY = 3
    AUTO = 4
```

Ab:

```python
mode = HVACMode.COOLING

print(mode)
```

Output:

```text
HVACMode.COOLING
```

Check:

```python
if mode == HVACMode.COOLING:
    print("Cooling mode active")
```

Output:

```text
Cooling mode active
```

---

# 15. HVAC modes par iteration

```python
for mode in HVACMode:
    print(mode.name, mode.value)
```

Output:

```text
OFF 0
COOLING 1
HEATING 2
FAN_ONLY 3
AUTO 4
```

Ye useful ho sakta hai jab aap available modes ko display, validate ya process karna chahte ho.

---

# 16. Work Order example

Work-order priority ke liye Enum:

```python
from enum import Enum

class Priority(Enum):
    LOW = 1
    MEDIUM = 2
    HIGH = 3
    CRITICAL = 4
```

Use:

```python
priority = Priority.CRITICAL

if priority == Priority.CRITICAL:
    print("Immediate attention required")
```

Output:

```text
Immediate attention required
```

Iteration:

```python
for priority in Priority:
    print(priority.name)
```

Output:

```text
LOW
MEDIUM
HIGH
CRITICAL
```

---

# 17. Enum aur normal variable mein difference

Normal:

```python
status = "RUNNING"
```

Enum:

```python
status = Status.RUNNING
```

Enum ka benefit:

```text
Normal string
    ↓
Free-form value
    ↓
Typos possible

Enum
    ↓
Predefined members
    ↓
Clear choices
```

---

# 18. Important: Enum values ko automatically compare mat karo

Agar:

```python
class Status(Enum):
    RUNNING = 1
    STOPPED = 2
```

To:

```python
Status.RUNNING == 1
```

normal `Enum` mein `False` hota hai.

Correct comparison:

```python
Status.RUNNING == Status.RUNNING
```

Ya agar actual value compare karni ho:

```python
Status.RUNNING.value == 1
```

Yani:

```text
Enum member
Status.RUNNING

Actual value
Status.RUNNING.value
```

Dono same cheez nahi hain.

---

# 19. Enum ka main mental model

```text
Enum
 │
 ├── RUNNING
 ├── STOPPED
 ├── FAULT
 └── MAINTENANCE
```

Har member ke paas:

```text
.name
.value
```

Example:

```text
Status.FAULT
     │
     ├── name  → "FAULT"
     │
     └── value → 3
```

Iteration:

```python
for status in Status:
    ...
```

means:

```text
RUNNING
   ↓
STOPPED
   ↓
FAULT
   ↓
MAINTENANCE
```

one by one process karna.

---

# Quick Revision

### Enum create:

```python
from enum import Enum

class Status(Enum):
    RUNNING = 1
    STOPPED = 2
    FAULT = 3
```

### Member:

```python
Status.RUNNING
```

### Name:

```python
Status.RUNNING.name
```

Result:

```text
RUNNING
```

### Value:

```python
Status.RUNNING.value
```

Result:

```text
1
```

### Value → Enum member:

```python
Status(1)
```

Result:

```text
Status.RUNNING
```

### Iterate:

```python
for status in Status:
    print(status)
```

### Names iterate:

```python
for status in Status:
    print(status.name)
```

### Values iterate:

```python
for status in Status:
    print(status.value)
```

## Sabse important concept

```text
Enum = predefined, limited choices
```

For example:

```text
HVACMode
├── OFF
├── COOLING
├── HEATING
├── FAN_ONLY
└── AUTO
```

Isliye Enum particularly **status, mode, priority, category, direction, state** jaisi fixed choices ke liye useful hai.
