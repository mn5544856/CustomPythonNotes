# Chapter 5: Date and Time

Python mein **date aur time** handle karne ke liye sabse important module hai:

```python
datetime
```

Is chapter mein hum seekhenge:

* String ko datetime mein convert karna
* Timezone-aware datetime banana
* Do dates/times ka difference nikalna
* Time zones switch karna
* Date mein days/months add/subtract karna
* Timestamp ko datetime mein convert karna
* ISO 8601 format
* Text ke andar se date/time extract karna
* Dates par loop chalana

---

# Section 5.1: Parsing a String into a Timezone-Aware Datetime Object

## 1. Parsing kya hota hai?

**Parsing** ka matlab hai kisi text/string ko read karke usko meaningful Python object mein convert karna.

Example:

```text
"2026-10-02 09:30:00"
```

Ye sirf ek **string** hai.

Python isko automatically datetime nahi samajhta.

Humein isko convert karna hota hai:

```text
String
   ↓
Parsing
   ↓
datetime object
```

---

# 2. Simple datetime

Python ka `datetime` module import karein:

```python
from datetime import datetime
```

Ab string:

```python
date_string = "2026-10-02 09:30:00"
```

ko parse kar sakte hain:

```python
date_string = "2026-10-02 09:30:00"

dt = datetime.strptime(
    date_string,
    "%Y-%m-%d %H:%M:%S"
)

print(dt)
```

Output:

```text
2026-10-02 09:30:00
```

Yahan:

```python
strptime()
```

ka matlab hai:

**string → datetime**

---

# 3. Format string ko samjhein

Ye part important hai:

```python
"%Y-%m-%d %H:%M:%S"
```

Har symbol date/time ke ek part ko represent karta hai.

| Code | Meaning              | Example |
| ---- | -------------------- | ------- |
| `%Y` | 4-digit year         | `2026`  |
| `%m` | month                | `10`    |
| `%d` | day                  | `02`    |
| `%H` | hour, 24-hour format | `09`    |
| `%M` | minute               | `30`    |
| `%S` | second               | `00`    |

Isliye:

```text
2026-10-02 09:30:00
```

ka format hai:

```text
%Y-%m-%d %H:%M:%S
```

---

# 4. Timezone-aware datetime kya hota hai?

Ab ek important concept:

**Timezone-aware datetime**

Agar datetime mein sirf:

```text
2026-10-02 09:30:00
```

hai, to Python ko ye nahi pata ke ye time **Riyadh**, **London**, **New York** ya kisi aur timezone ka hai.

Ye **naive datetime** hai.

Timezone ke saath:

```text
2026-10-02 09:30:00 +03:00
```

ab Python ko pata hai ke datetime ka timezone offset `+03:00` hai.

Ye **timezone-aware datetime** hai.

---

# 5. `zoneinfo` module

Modern Python mein timezone handling ke liye `zoneinfo` bahut useful hai.

Import:

```python
from zoneinfo import ZoneInfo
```

Example:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Output approximately:

```text
2026-10-02 09:30:00+03:00
```

Yahan:

```python
ZoneInfo("Asia/Riyadh")
```

ne datetime ko Riyadh timezone ke saath attach kiya.

---

# 6. String mein timezone ho to?

Suppose humein ye string mili:

```text
2026-10-02T09:30:00+03:00
```

Ismein already timezone information hai:

```text
+03:00
```

Python mein isko parse karne ka simple modern tareeqa:

```python
from datetime import datetime

date_string = "2026-10-02T09:30:00+03:00"

dt = datetime.fromisoformat(date_string)

print(dt)
```

Output:

```text
2026-10-02 09:30:00+03:00
```

Ab ye **timezone-aware datetime** hai.

---

# 7. `fromisoformat()` ko samjhein

Method:

```python
datetime.fromisoformat()
```

ISO-format string ko datetime object mein convert kar sakta hai.

Example:

```python
date_string = "2026-10-02T09:30:00+03:00"

dt = datetime.fromisoformat(date_string)
```

Flow:

```text
"2026-10-02T09:30:00+03:00"
              ↓
       fromisoformat()
              ↓
     datetime object
              ↓
2026-10-02 09:30:00+03:00
```

---

# 8. `T` kya hai?

ISO 8601 format mein aksar:

```text
2026-10-02T09:30:00+03:00
```

mein `T` date aur time ko separate karta hai.

```text
2026-10-02
    ↓
   Date

T
↓
Separator

09:30:00
   ↓
  Time

+03:00
   ↓
Timezone offset
```

---

# 9. UTC ka example

UTC ko represent karne ke liye ISO timestamp mein `Z` bhi use hota hai.

Example:

```text
2026-10-02T06:30:00Z
```

`Z` ka matlab UTC timezone hai.

Modern Python mein:

```python
from datetime import datetime

dt = datetime.fromisoformat(
    "2026-10-02T06:30:00Z"
)

print(dt)
```

Yahan result timezone-aware datetime hoga.

---

# 10. `strptime()` vs `fromisoformat()`

Ye difference yaad rakhna important hai.

### `strptime()`

Jab aapko string ka format pata ho:

```python
from datetime import datetime

text = "2026-10-02 09:30:00"

dt = datetime.strptime(
    text,
    "%Y-%m-%d %H:%M:%S"
)
```

### `fromisoformat()`

Jab input ISO-style format mein ho:

```python
from datetime import datetime

text = "2026-10-02T09:30:00+03:00"

dt = datetime.fromisoformat(text)
```

Simple rule:

```text
Known custom format
       ↓
   strptime()

ISO 8601 format
       ↓
fromisoformat()
```

---

# 11. Practical HVAC Example

Suppose Honeywell/Building Management System se timestamp mila:

```text
2026-10-02T09:30:00+03:00
```

Hum usko Python datetime mein convert kar sakte hain:

```python
from datetime import datetime

timestamp = "2026-10-02T09:30:00+03:00"

dt = datetime.fromisoformat(timestamp)

print(dt)
```

Ab hum datetime par calculations kar sakte hain.

For example:

```python
print(dt.year)
print(dt.month)
print(dt.day)
print(dt.hour)
print(dt.minute)
```

Output:

```text
2026
10
2
9
30
```

---

# 12. Check karna ke datetime timezone-aware hai ya nahi

Datetime mein:

```python
tzinfo
```

check kar sakte hain.

Example:

```python
from datetime import datetime

dt = datetime.fromisoformat(
    "2026-10-02T09:30:00+03:00"
)

print(dt.tzinfo)
```

Agar timezone present hai, `tzinfo` empty nahi hoga.

Simple concept:

```text
tzinfo is None
      ↓
Naive datetime

tzinfo is not None
      ↓
Timezone-aware datetime
```

---

# 13. Naive vs Aware

### Naive

```python
from datetime import datetime

dt = datetime(2026, 10, 2, 9, 30)

print(dt)
```

Ismein timezone nahi hai.

### Aware

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Ismein timezone hai.

---

# 14. Important Warning

Naive aur aware datetimes ko directly compare ya subtract karna problem create kar sakta hai.

Example concept:

```text
Naive datetime
      +
Aware datetime
      ↓
Problem
```

Isliye agar application multiple countries/timezones ke saath kaam karti hai, to timezone-aware datetimes use karna generally safer hota hai.

---

# 15. Real Data Example

Suppose CSV mein ye data hai:

```text
Equipment,Timestamp
AHU-001,2026-10-02T09:30:00+03:00
AHU-002,2026-10-02T10:15:00+03:00
```

Python mein:

```python
from datetime import datetime

timestamp = "2026-10-02T09:30:00+03:00"

dt = datetime.fromisoformat(timestamp)

print(dt)
```

Ab timestamp sirf text nahi raha.

Ye actual Python **datetime object** ban gaya.

Iska benefit ye hai ke hum baad mein:

* difference calculate kar sakte hain
* timezone convert kar sakte hain
* days add/subtract kar sakte hain
* date filter kar sakte hain
* dates par loop chala sakte hain

Ye sab Chapter 5 ke next sections mein aayega.

---

# Section 5.1 — Quick Revision

### Parsing

```text
String
 ↓
Parsing
 ↓
datetime object
```

### Custom format

```python
datetime.strptime(text, format)
```

Example:

```python
datetime.strptime(
    "2026-10-02 09:30:00",
    "%Y-%m-%d %H:%M:%S"
)
```

### ISO format

```python
datetime.fromisoformat(text)
```

Example:

```python
datetime.fromisoformat(
    "2026-10-02T09:30:00+03:00"
)
```

### Timezone

```python
from zoneinfo import ZoneInfo

ZoneInfo("Asia/Riyadh")
```

### Naive

```text
Timezone information nahi
```

### Aware

```text
Timezone information present
```

---

# Practice

### Exercise 1

Is string ko datetime mein convert karein:

```python
text = "2026-12-25 18:45:30"
```

Hint:

```python
datetime.strptime()
```

---

### Exercise 2

Is ISO timestamp ko parse karein:

```python
text = "2026-12-25T18:45:30+03:00"
```

Hint:

```python
datetime.fromisoformat()
```

---

### Exercise 3

Riyadh timezone ke saath datetime banayein:

```text
2026
December
25
18:45
```

Hint:

```python
ZoneInfo("Asia/Riyadh")
```

---

## Section 5.1 ka Golden Concept

**Date/time string sirf text hoti hai.**

```text
"2026-10-02T09:30:00+03:00"
```

`fromisoformat()` ke baad:

```text
datetime object
```

ban jata hai.

Aur agar timezone information bhi ho:

```text
Timezone-aware datetime
```

ban jata hai.
# Section 5.2: Constructing Timezone-Aware Datetimes

Pichle section mein humne existing string ko parse karke timezone-aware datetime banaya tha.

Ab hum **directly Python mein timezone-aware datetime construct** karenge.

---

# 1. Sabse pehle: `datetime` kya hai?

Python mein:

```python
from datetime import datetime
```

ke baad hum manually datetime bana sakte hain:

```python
dt = datetime(2026, 10, 2, 9, 30)
```

Yahan:

```text
2026 → year
10   → month
2    → day
9    → hour
30   → minute
```

Lekin is datetime mein **timezone nahi hai**.

Ye **naive datetime** hai.

---

# 2. Timezone kaise add karein?

Modern Python mein `zoneinfo` use karna recommended hai.

```python
from datetime import datetime
from zoneinfo import ZoneInfo
```

Ab:

```python
dt = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Output:

```text
2026-10-02 09:30:00+03:00
```

Yahan:

```python
tzinfo=ZoneInfo("Asia/Riyadh")
```

ne datetime ko **Riyadh timezone** ke saath construct kiya.

---

# 3. `tzinfo` kya hai?

`tzinfo` datetime ko batata hai:

> "Ye datetime kis timezone ke context mein hai?"

Example:

```python
tzinfo=ZoneInfo("Asia/Riyadh")
```

Matlab:

```text
Datetime
   +
Riyadh timezone
   ↓
Timezone-aware datetime
```

---

# 4. `ZoneInfo` kya karta hai?

`ZoneInfo` Python ko named timezone provide karta hai.

Example:

```python
ZoneInfo("Asia/Riyadh")
```

Riyadh timezone.

Kuch aur examples:

```python
ZoneInfo("Asia/Karachi")
ZoneInfo("Europe/London")
ZoneInfo("America/New_York")
Asia/Dubai
Asia/Tokyo
```

Ye **IANA timezone names** hain.

---

# 5. Offset aur Timezone mein difference

Ye distinction important hai.

Aapko output mein:

```text
+03:00
```

dikh sakta hai.

Ye **UTC offset** hai.

Lekin:

```python
ZoneInfo("Asia/Riyadh")
```

ek **timezone identifier** hai.

Simple example:

```text
Asia/Riyadh
    ↓
Timezone

+03:00
    ↓
Current UTC offset
```

Timezone rules zyada information provide karte hain, sirf fixed offset nahi.

---

# 6. Current Date/Time with Timezone

Agar current Riyadh time chahiye:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

now = datetime.now(ZoneInfo("Asia/Riyadh"))

print(now)
```

Example output:

```text
2026-10-02 09:30:15.123456+03:00
```

Yahan:

```python
datetime.now()
```

ki jagah:

```python
datetime.now(ZoneInfo("Asia/Riyadh"))
```

use kiya.

Isse returned datetime timezone-aware hota hai.

---

# 7. `datetime.now()` vs `datetime.now(ZoneInfo(...))`

### Naive

```python
from datetime import datetime

now = datetime.now()

print(now)
```

Example:

```text
2026-10-02 09:30:15.123456
```

Timezone information nahi.

### Aware

```python
from datetime import datetime
from zoneinfo import ZoneInfo

now = datetime.now(
    ZoneInfo("Asia/Riyadh")
)

print(now)
```

Example:

```text
2026-10-02 09:30:15.123456+03:00
```

Timezone information present.

---

# 8. UTC Timezone

UTC ke liye:

```python
from datetime import datetime, timezone

now = datetime.now(timezone.utc)

print(now)
```

Example:

```text
2026-10-02 06:30:15.123456+00:00
```

Yahan:

```python
timezone.utc
```

UTC timezone provide karta hai.

---

# 9. Riyadh aur UTC ka relation

Riyadh ka standard offset:

```text
UTC +03:00
```

Isliye agar:

```text
UTC     = 06:30
Riyadh  = 09:30
```

to dono **same moment** ko represent kar sakte hain.

```text
06:30 UTC
   ↓
09:30 Riyadh
```

Clock time different hai, lekin actual moment same hai.

---

# 10. `datetime(...)` se aware datetime

Complete example:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(
    year=2026,
    month=10,
    day=2,
    hour=9,
    minute=30,
    second=0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Output:

```text
2026-10-02 09:30:00+03:00
```

Named arguments use karne se code aur readable ho jata hai.

---

# 11. `date` aur `datetime` mein difference

Ye bhi important hai.

### `date`

Sirf date:

```python
from datetime import date

d = date(2026, 10, 2)

print(d)
```

Output:

```text
2026-10-02
```

### `datetime`

Date + time:

```python
from datetime import datetime

dt = datetime(2026, 10, 2, 9, 30)

print(dt)
```

Output:

```text
2026-10-02 09:30:00
```

### Timezone-aware datetime

```text
2026-10-02 09:30:00+03:00
```

---

# 12. Important: `date` mein timezone nahi hota

`date` sirf calendar date represent karta hai:

```text
2026-10-02
```

Timezone ka concept normally `datetime` ke saath relevant hota hai.

---

# 13. `time` object

Python mein sirf time bhi represent kar sakte hain:

```python
from datetime import time

t = time(9, 30, 15)

print(t)
```

Output:

```text
09:30:15
```

Lekin complete timestamp ke liye:

```python
datetime
```

use hota hai.

---

# 14. `datetime.combine()`

Kabhi date aur time alag variables mein hote hain.

Example:

```python
from datetime import date, time, datetime

d = date(2026, 10, 2)
t = time(9, 30)

dt = datetime.combine(d, t)

print(dt)
```

Output:

```text
2026-10-02 09:30:00
```

Ab timezone bhi add karna ho to:

```python
from datetime import date, time, datetime
from zoneinfo import ZoneInfo

d = date(2026, 10, 2)
t = time(9, 30)

dt = datetime.combine(
    d,
    t,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Output:

```text
2026-10-02 09:30:00+03:00
```

---

# 15. HVAC Practical Example

Suppose a maintenance schedule hai:

```text
Date: 2026-10-02
Inspection Time: 09:30
Location: Riyadh
```

Python:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

inspection = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(inspection)
```

Output:

```text
2026-10-02 09:30:00+03:00
```

Ab Python ko pata hai:

* date kya hai
* time kya hai
* timezone kya hai

---

# 16. Work Order Example

Suppose work order ka start time:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

work_order_start = datetime(
    2026,
    10,
    2,
    8,
    15,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(work_order_start)
```

Output:

```text
2026-10-02 08:15:00+03:00
```

Later hum end time ke saath difference calculate kar sakte hain.

Ye **Section 5.3** mein aayega.

---

# 17. Timezone-aware datetime ko check karna

```python
print(work_order_start.tzinfo)
```

Output timezone object hoga.

Aap ye bhi check kar sakte hain:

```python
if work_order_start.tzinfo is not None:
    print("Timezone-aware")
```

Output:

```text
Timezone-aware
```

---

# 18. `replace()` se `tzinfo` attach karna — Important Difference

Aap technically ye bhi kar sakte hain:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(2026, 10, 2, 9, 30)

dt = dt.replace(
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Result:

```text
2026-10-02 09:30:00+03:00
```

Lekin yahan ek important concept hai:

`replace(tzinfo=...)` existing clock time ko **convert nahi karta**.

Ye bas timezone information attach karta hai.

---

# 19. `replace()` vs `astimezone()`

Ye difference future sections ke liye bahut important hai.

### `replace()`

Timezone information attach/change karta hai **without converting the represented clock time**.

```python
dt.replace(tzinfo=ZoneInfo("Asia/Riyadh"))
```

### `astimezone()`

Same actual moment ko doosre timezone mein convert karta hai.

```python
dt.astimezone(ZoneInfo("Europe/London"))
```

Simple mental model:

```text
replace()
   ↓
Timezone information attach/change

astimezone()
   ↓
Same moment ko doosre timezone mein convert
```

`astimezone()` ko hum Section 5.5 mein detail se dekhenge.

---

# 20. Common Mistake

Beginners kabhi ye karte hain:

```python
dt = datetime.now()

dt.replace(
    tzinfo=ZoneInfo("Asia/Riyadh")
)
```

Lekin `datetime` objects immutable hote hain.

Isliye `replace()` ka result store karna hota hai:

```python
dt = dt.replace(
    tzinfo=ZoneInfo("Asia/Riyadh")
)
```

Ya directly:

```python
dt = datetime.now(
    ZoneInfo("Asia/Riyadh")
)
```

---

# 21. Best Practical Pattern

Agar aapko current Riyadh datetime chahiye:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

riyadh_now = datetime.now(
    ZoneInfo("Asia/Riyadh")
)

print(riyadh_now)
```

Agar fixed date/time banana hai:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Ye clean aur readable approach hai.

---

# Section 5.2 — Quick Revision

## Naive datetime

```python
dt = datetime(2026, 10, 2, 9, 30)
```

Result:

```text
2026-10-02 09:30:00
```

Timezone nahi.

---

## Timezone-aware datetime

```python
dt = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)
```

Result:

```text
2026-10-02 09:30:00+03:00
```

Timezone present.

---

## Current timezone-aware time

```python
datetime.now(
    ZoneInfo("Asia/Riyadh")
)
```

---

## UTC

```python
datetime.now(timezone.utc)
```

---

## Main concepts

```text
datetime
   ↓
Date + Time

ZoneInfo
   ↓
Named Timezone

tzinfo
   ↓
Timezone information inside datetime

Aware datetime
   ↓
Date + Time + Timezone context
```

---

# Practice

### Exercise 1

Riyadh timezone ke saath ye datetime create karein:

```text
2026-11-15 14:30:00
```

---

### Exercise 2

Current Riyadh time print karein.

---

### Exercise 3

Ek UTC datetime banayein:

```text
2026-11-15 11:30:00 UTC
```

---

### Exercise 4

Check karein ke datetime timezone-aware hai ya nahi:

```python
if dt.tzinfo is not None:
    print("Aware")
else:
    print("Naive")
```

---

# Final Concept

Section 5.1 mein:

```text
String
 ↓
Parse
 ↓
Timezone-aware datetime
```

Section 5.2 mein:

```text
Year + Month + Day + Time + Timezone
              ↓
     datetime object
```

Example:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(
    2026, 10, 2, 9, 30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)
```

Ab ye ek **timezone-aware datetime** hai.
# Section 5.3: Computing Time Differences

Aksar programming mein humein ye calculate karna hota hai:

* Work order kitni der chala?
* Equipment kitne hours running raha?
* Do timestamps ke beech kitne minutes hain?
* Ek date se doosri date tak kitne days hain?

Python mein is kaam ke liye important object hai:

```python id="x7n4q2"
timedelta
```

---

# 1. `timedelta` kya hai?

`timedelta` ka matlab hai:

> **Time duration / time difference**

Example:

```text id="p8q1az"
10:00
 ↓
12:30
```

Difference:

```text id="1v7x8m"
2 hours 30 minutes
```

Ye duration `timedelta` represent kar sakta hai.

---

# 2. Import karna

```python id="m5zq8r"
from datetime import datetime, timedelta
```

Ab hum `timedelta` use kar sakte hain.

---

# 3. Do datetime ka difference

Example:

```python id="d2h6kp"
from datetime import datetime

start = datetime(2026, 10, 2, 9, 0)
end = datetime(2026, 10, 2, 11, 30)

difference = end - start

print(difference)
```

Output:

```text id="v9f4sx"
2:30:00
```

Yani:

```text id="h2m8kd"
2 hours 30 minutes
```

---

# 4. Result ka type

```python id="x3f5mz"
print(type(difference))
```

Output:

```text id="4q8b7c"
<class 'datetime.timedelta'>
```

Yani:

```text id="z9y2qa"
datetime - datetime
       ↓
timedelta
```

---

# 5. `timedelta` ko hours mein convert karna

Agar humein total seconds pata karne hain:

```python id="k4m1xp"
print(difference.total_seconds())
```

Output:

```text id="s8d2we"
9000.0
```

2 hours 30 minutes:

```text id="w5r9ta"
2 × 3600 = 7200
30 × 60 = 1800

7200 + 1800 = 9000 seconds
```

---

# 6. Total Minutes

```python id="j7c3qn"
minutes = difference.total_seconds() / 60

print(minutes)
```

Output:

```text id="v2f6kd"
150.0
```

Yani:

```text id="k1s7pl"
2 hours 30 minutes
       ↓
150 minutes
```

---

# 7. Total Hours

```python id="q8m3az"
hours = difference.total_seconds() / 3600

print(hours)
```

Output:

```text id="y4c9xn"
2.5
```

---

# 8. Work Order Example

Suppose maintenance work order:

```text id="d8w5sm"
Start: 08:15
End:   11:45
```

Python:

```python id="f3n7qx"
from datetime import datetime

start = datetime(2026, 10, 2, 8, 15)
end = datetime(2026, 10, 2, 11, 45)

duration = end - start

print(duration)
```

Output:

```text id="p7c2va"
3:30:00
```

Total hours:

```python id="r6k1hy"
hours = duration.total_seconds() / 3600

print(hours)
```

Output:

```text id="e2q9mz"
3.5
```

Yani work order duration:

**3.5 hours**

---

# 9. `timedelta` manually banana

Hum khud bhi duration create kar sakte hain.

```python id="u3b7pk"
from datetime import timedelta

duration = timedelta(
    hours=3,
    minutes=30
)

print(duration)
```

Output:

```text id="c8x2nr"
3:30:00
```

---

# 10. Different Units

`timedelta()` mein commonly:

```python id="j5m8qa"
days
seconds
microseconds
milliseconds
minutes
hours
weeks
```

use kar sakte hain.

Example:

```python id="t2k9vf"
duration = timedelta(
    days=2,
    hours=5,
    minutes=30
)

print(duration)
```

Output:

```text id="n7x4ps"
2 days, 5:30:00
```

---

# 11. Date mein Difference

`timedelta` sirf time ke liye nahi, dates ke liye bhi use hota hai.

```python id="b4q8md"
from datetime import date

start = date(2026, 10, 1)
end = date(2026, 10, 10)

difference = end - start

print(difference)
```

Output:

```text id="w6z1ka"
9 days, 0:00:00
```

Yani dates ke beech:

**9 days**

---

# 12. Negative Difference

Agar end pehle aa jaye:

```python id="r9f2wx"
from datetime import datetime

start = datetime(2026, 10, 10, 10, 0)
end = datetime(2026, 10, 10, 8, 0)

difference = end - start

print(difference)
```

Output:

```text id="a3k7mv"
-1 day, 22:00:00
```

Ye thoda confusing lag sakta hai.

Iska actual meaning:

```text id="q5n8bd"
-2 hours
```

Check karein:

```python id="v6p2cx"
print(difference.total_seconds() / 3600)
```

Output:

```text id="r4m9za"
-2.0
```

---

# 13. Absolute Difference

Agar humein sirf positive difference chahiye:

```python id="e7c3ky"
absolute_difference = abs(difference)

print(absolute_difference)
```

Output:

```text id="u2m5pf"
2:00:00
```

Yani direction ignore karke sirf duration chahiye.

---

# 14. Datetime + Timedelta

`timedelta` ka use sirf subtraction ke liye nahi hota.

Datetime mein duration **add** bhi kar sakte hain.

```python id="m8q4vz"
from datetime import datetime, timedelta

start = datetime(2026, 10, 2, 9, 0)

future = start + timedelta(hours=3)

print(future)
```

Output:

```text id="x1k6sd"
2026-10-02 12:00:00
```

Yani:

```text id="f5r2ja"
09:00
 +
3 hours
 ↓
12:00
```

---

# 15. Datetime - Timedelta

Isi tarah subtract:

```python id="c9v3mx"
from datetime import datetime, timedelta

start = datetime(2026, 10, 2, 12, 0)

earlier = start - timedelta(hours=3)

print(earlier)
```

Output:

```text id="z7k1qp"
2026-10-02 09:00:00
```

---

# 16. Days Add Karna

```python id="n4s8wt"
from datetime import datetime, timedelta

date_time = datetime(2026, 10, 2, 9, 0)

new_date = date_time + timedelta(days=5)

print(new_date)
```

Output:

```text id="m2x6rc"
2026-10-07 09:00:00
```

---

# 17. Weeks Add Karna

```python id="y8q3lm"
from datetime import datetime, timedelta

date_time = datetime(2026, 10, 2)

new_date = date_time + timedelta(weeks=2)

print(new_date)
```

Output:

```text id="p4k7zn"
2026-10-16 00:00:00
```

---

# 18. Timezone-Aware Datetimes ke Saath Difference

Pichle section mein humne timezone-aware datetime banaya tha.

Ab unka difference nikal sakte hain.

```python id="s5d9ka"
from datetime import datetime
from zoneinfo import ZoneInfo

start = datetime(
    2026, 10, 2, 8, 0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

end = datetime(
    2026, 10, 2, 11, 30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

difference = end - start

print(difference)
```

Output:

```text id="c7m2qx"
3:30:00
```

---

# 19. Different Timezones ka Difference

Timezone-aware datetime ka ek powerful feature ye hai ke Python different timezones ko account kar sakta hai.

Example:

```python id="k9f3wb"
from datetime import datetime
from zoneinfo import ZoneInfo

riyadh = datetime(
    2026, 10, 2, 12, 0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

london = datetime(
    2026, 10, 2, 10, 0,
    tzinfo=ZoneInfo("Europe/London")
)

difference = riyadh - london

print(difference)
```

October mein London ka UTC offset season ke according change ho sakta hai, isliye named timezones (`ZoneInfo`) use karna important hai.

Core idea:

```text id="p3r7xm"
Timezone-aware datetime
          ↓
Python actual instants compare kar sakta hai
```

---

# 20. `total_seconds()` Bahut Important Hai

Agar duration:

```python id="w8n2kc"
duration = timedelta(
    days=1,
    hours=2,
    minutes=30
)
```

hai, to:

```python id="d5q9vt"
duration.total_seconds()
```

poori duration ko seconds mein convert karta hai.

Phir aap:

```python id="f6m3za"
seconds = duration.total_seconds()

minutes = seconds / 60
hours = seconds / 3600
```

kar sakte hain.

---

# 21. `.days` ka Important Difference

`timedelta` mein:

```python id="e2j7rp"
duration.days
```

sirf **whole days** deta hai.

Example:

```python id="v4k8ms"
from datetime import timedelta

duration = timedelta(
    days=2,
    hours=5
)

print(duration.days)
```

Output:

```text id="n3x9qa"
2
```

Lekin:

```python id="q7c2wd"
print(duration.total_seconds() / 3600)
```

Output:

```text id="s6m1pk"
53.0
```

Yani total duration **53 hours** hai.

Isliye total duration nikalne ke liye `total_seconds()` zyada useful hota hai.

---

# 22. `.seconds` se सावधान

`timedelta.seconds` ko total seconds samajhna common mistake hai.

Example:

```python id="k3m8vf"
duration = timedelta(
    days=2,
    hours=5
)

print(duration.seconds)
```

Output:

```text id="q9x2ld"
18000
```

Ye sirf remaining time ke seconds hain:

```text id="v5n7cs"
5 hours
= 18,000 seconds
```

Ye **total 53 hours** ke seconds nahi hain.

Total ke liye:

```python id="h4p6za"
duration.total_seconds()
```

use karein.

---

# 23. Practical Maintenance Example

Suppose equipment inspection:

```text id="c8m2xy"
Start:
2026-10-02 08:20

End:
2026-10-02 10:50
```

Python:

```python id="j7v4pq"
from datetime import datetime

start = datetime(2026, 10, 2, 8, 20)
end = datetime(2026, 10, 2, 10, 50)

duration = end - start

print("Duration:", duration)
print("Minutes:", duration.total_seconds() / 60)
print("Hours:", duration.total_seconds() / 3600)
```

Output:

```text id="w2n9kc"
Duration: 2:30:00
Minutes: 150.0
Hours: 2.5
```

Ye work-order analysis mein kaafi useful hai.

---

# 24. Common Pattern

Jab bhi do timestamps ka difference chahiye:

```python id="z8q3lm"
end - start
```

Result:

```text id="r5x7na"
timedelta
```

Phir:

```python id="a4k9vp"
difference.total_seconds()
```

se total seconds.

Hours:

```python id="d6m2qw"
difference.total_seconds() / 3600
```

Minutes:

```python id="h7c5xs"
difference.total_seconds() / 60
```

---

# Section 5.3 — Quick Revision

## Difference

```python id="n8v3kp"
difference = end - start
```

Result:

```text id="e5q1mz"
timedelta
```

---

## Duration banana

```python id="s2f7xc"
timedelta(
    days=2,
    hours=3,
    minutes=30
)
```

---

## Add duration

```python id="m6q9wa"
dt + timedelta(hours=3)
```

---

## Subtract duration

```python id="j4x8nt"
dt - timedelta(days=2)
```

---

## Total seconds

```python id="p7c2md"
difference.total_seconds()
```

---

## Total hours

```python id="r9v5kb"
difference.total_seconds() / 3600
```

---

## Total minutes

```python id="t3n6qx"
difference.total_seconds() / 60
```

---

# Golden Mental Model

```text id="u8m4za"
datetime
    +
datetime
    ↓
subtract (-)
    ↓
timedelta
    ↓
duration
```

Aur:

```text id="k5q2wp"
datetime
    +
timedelta
    ↓
future datetime
```

ya:

```text id="v7n3cx"
datetime
    -
timedelta
    ↓
past datetime
```

### Sabse important:

**`datetime` = ek specific date/time**

**`timedelta` = do times ka duration/difference**

**`total_seconds()` = duration ko total seconds mein convert karta hai**
# Section 5.4: Basic datetime Objects Usage

Pichle sections mein humne seekha:

* String → `datetime`
* Timezone-aware datetime
* `timedelta`
* Do datetimes ka difference

Ab hum dekhenge ke ek `datetime` object ke saath basic operations kaise karte hain.

---

# 1. Basic datetime banana

Sabse pehle:

```python
from datetime import datetime
```

Ab datetime create karein:

```python
dt = datetime(2026, 10, 2, 9, 30, 15)

print(dt)
```

Output:

```text
2026-10-02 09:30:15
```

Is datetime mein:

```text
2026 → year
10   → month
2    → day
9    → hour
30   → minute
15   → second
```

---

# 2. `year`

Datetime ka year nikalne ke liye:

```python
print(dt.year)
```

Output:

```text
2026
```

---

# 3. `month`

```python
print(dt.month)
```

Output:

```text
10
```

---

# 4. `day`

```python
print(dt.day)
```

Output:

```text
2
```

---

# 5. `hour`

```python
print(dt.hour)
```

Output:

```text
9
```

---

# 6. `minute`

```python
print(dt.minute)
```

Output:

```text
30
```

---

# 7. `second`

```python
print(dt.second)
```

Output:

```text
15
```

---

# 8. Microseconds

Datetime mein microseconds bhi ho sakte hain.

```python
dt = datetime(
    2026,
    10,
    2,
    9,
    30,
    15,
    500000
)

print(dt.microsecond)
```

Output:

```text
500000
```

1 second = 1,000,000 microseconds.

Normally everyday applications mein microseconds ki zaroorat nahi hoti, lekin logging aur high-precision systems mein useful ho sakte hain.

---

# 9. Weekday

Datetime se ye bhi pata kar sakte hain ke date week ke kis din hai.

```python
dt = datetime(2026, 10, 2)

print(dt.weekday())
```

`weekday()` mein:

```text
Monday    = 0
Tuesday   = 1
Wednesday = 2
Thursday  = 3
Friday    = 4
Saturday  = 5
Sunday    = 6
```

Isliye agar result `4` aaye to Friday hai.

---

# 10. `isoweekday()`

Ek alternative:

```python
print(dt.isoweekday())
```

Ismein:

```text
Monday    = 1
Tuesday   = 2
Wednesday = 3
Thursday  = 4
Friday    = 5
Saturday  = 6
Sunday    = 7
```

### Difference

```text
weekday()
    Monday = 0

isoweekday()
    Monday = 1
```

---

# 11. Date ko format karna — `strftime()`

Aksar datetime ko apne desired format mein display karna hota hai.

Iske liye:

```python
strftime()
```

use hota hai.

Example:

```python
dt = datetime(2026, 10, 2, 9, 30)

formatted = dt.strftime("%Y-%m-%d")

print(formatted)
```

Output:

```text
2026-10-02
```

---

# 12. Date + Time Format

```python
formatted = dt.strftime(
    "%Y-%m-%d %H:%M:%S"
)

print(formatted)
```

Output:

```text
2026-10-02 09:30:00
```

---

# 13. `strptime()` vs `strftime()`

Ye dono easily confuse hote hain.

### `strptime()`

**String → datetime**

```python
dt = datetime.strptime(
    "2026-10-02",
    "%Y-%m-%d"
)
```

Flow:

```text
String
  ↓
strptime()
  ↓
datetime
```

### `strftime()`

**datetime → String**

```python
text = dt.strftime("%Y-%m-%d")
```

Flow:

```text
datetime
   ↓
strftime()
   ↓
String
```

### Golden Rule

```text
strptime
    ↓
parse string

strftime
    ↓
format datetime
```

---

# 14. Common Formatting Codes

| Code | Meaning       | Example   |
| ---- | ------------- | --------- |
| `%Y` | 4-digit year  | `2026`    |
| `%y` | 2-digit year  | `26`      |
| `%m` | month         | `10`      |
| `%d` | day           | `02`      |
| `%H` | 24-hour       | `09`      |
| `%I` | 12-hour       | `09`      |
| `%M` | minute        | `30`      |
| `%S` | second        | `15`      |
| `%p` | AM/PM         | `AM`      |
| `%A` | full weekday  | `Friday`  |
| `%a` | short weekday | `Fri`     |
| `%B` | full month    | `October` |
| `%b` | short month   | `Oct`     |

---

# 15. Human-Friendly Format

Suppose:

```python
dt = datetime(2026, 10, 2, 9, 30)
```

Humans ke liye:

```python
print(
    dt.strftime("%d %B %Y, %I:%M %p")
)
```

Output:

```text
02 October 2026, 09:30 AM
```

Yani same datetime ko different formats mein display kar sakte hain.

---

# 16. `date()` aur `time()`

Datetime object se sirf date part:

```python
dt = datetime(2026, 10, 2, 9, 30)

print(dt.date())
```

Output:

```text
2026-10-02
```

Sirf time part:

```python
print(dt.time())
```

Output:

```text
09:30:00
```

Yani:

```text
datetime
   ↓
 ┌───────┐
 │ date  │
 │ time  │
 └───────┘
```

---

# 17. Compare Datetimes

Datetimes ko compare bhi kar sakte hain.

```python
from datetime import datetime

dt1 = datetime(2026, 10, 2, 9, 0)
dt2 = datetime(2026, 10, 2, 10, 0)

print(dt1 < dt2)
```

Output:

```text
True
```

Matlab `dt1`, `dt2` se pehle hai.

---

# 18. Comparison Operators

Datetime ke saath:

```text
<
>
<=
>=
==
!=
```

use kar sakte hain.

Example:

```python
if dt1 < dt2:
    print("dt1 is earlier")
```

Output:

```text
dt1 is earlier
```

---

# 19. Practical Work Order Example

Suppose do timestamps hain:

```python
from datetime import datetime

start = datetime(2026, 10, 2, 8, 30)
end = datetime(2026, 10, 2, 11, 45)

if start < end:
    print("Start time is before end time")
```

Output:

```text
Start time is before end time
```

Ye validation ke liye useful hai.

---

# 20. Current Date and Time

Current local datetime:

```python
from datetime import datetime

now = datetime.now()

print(now)
```

Example:

```text
2026-10-02 09:35:12.456789
```

Ismein current date aur time milta hai.

---

# 21. Current Date

Agar sirf current date chahiye:

```python
today = datetime.now().date()

print(today)
```

Example:

```text
2026-10-02
```

---

# 22. Current Time

Sirf current time:

```python
current_time = datetime.now().time()

print(current_time)
```

Example:

```text
09:35:12.456789
```

---

# 23. Timezone-aware Current Time

Agar specific timezone chahiye:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

now = datetime.now(
    ZoneInfo("Asia/Riyadh")
)

print(now)
```

Example:

```text
2026-10-02 09:35:12+03:00
```

Ye Section 5.2 ke concept ko use kar raha hai.

---

# 24. `replace()`

Datetime ke kisi part ko change karne ke liye `replace()` use kar sakte hain.

Example:

```python
dt = datetime(2026, 10, 2, 9, 30)

new_dt = dt.replace(hour=15)

print(new_dt)
```

Output:

```text
2026-10-02 15:30:00
```

Original `dt` change nahi hua.

```python
print(dt)
```

Output:

```text
2026-10-02 09:30:00
```

Ye important hai:

**datetime immutable hota hai.**

Isliye `replace()` ka result new variable mein store karna hota hai agar aapko use karna hai.

---

# 25. Multiple Parts Change Karna

```python
new_dt = dt.replace(
    year=2027,
    month=1,
    day=15,
    hour=14
)

print(new_dt)
```

Result:

```text
2027-01-15 14:30:00
```

---

# 26. `isoformat()`

Datetime ko ISO 8601 style string mein convert karne ke liye:

```python
dt = datetime(2026, 10, 2, 9, 30)

print(dt.isoformat())
```

Output:

```text
2026-10-02T09:30:00
```

Timezone-aware datetime:

```python
from zoneinfo import ZoneInfo

dt = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt.isoformat())
```

Output:

```text
2026-10-02T09:30:00+03:00
```

---

# 27. `str()` se Datetime ko String Banana

```python
text = str(dt)

print(text)
```

Ye datetime ka string representation deta hai.

Lekin agar aapko **specific format** chahiye, to:

```python
dt.strftime(...)
```

use karein.

---

# 28. Practical HVAC Log Example

Suppose ek HVAC log mein timestamp hai:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

log_time = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)
```

Equipment:

```python
equipment_id = "AHU-001"
temperature = 22.5
status = "Running"
```

Ab readable log:

```python
print(
    equipment_id,
    log_time.strftime("%Y-%m-%d %H:%M:%S"),
    temperature,
    status
)
```

Output:

```text
AHU-001 2026-10-02 09:30:00 22.5 Running
```

Ye CSV/logging applications mein useful pattern hai.

---

# 29. Datetime se Data Filter Karna

Suppose:

```python
log_time = datetime(2026, 10, 2, 9, 30)
```

Hum check kar sakte hain:

```python
if log_time.hour >= 9:
    print("Morning log")
```

Output:

```text
Morning log
```

Ya:

```python
if log_time.date() == datetime(2026, 10, 2).date():
    print("Today's log")
```

---

# 30. Important: Datetime Comparison

Agar dono datetime **naive** hain:

```python
dt1 < dt2
```

theek hai.

Agar dono **aware** hain:

```python
aware1 < aware2
```

bhi theek hai.

Lekin naive aur aware ko directly compare karna generally error dega.

Isliye:

```text
Naive + Naive
       ✓

Aware + Aware
       ✓

Naive + Aware
       ✗
```

Timezone-based applications mein consistent datetime handling zaroori hai.

---

# Section 5.4 — Quick Revision

## Parts nikalna

```python
dt.year
dt.month
dt.day
dt.hour
dt.minute
dt.second
dt.microsecond
```

---

## Weekday

```python
dt.weekday()
```

Monday = `0`

```python
dt.isoweekday()
```

Monday = `1`

---

## Date/time separate karna

```python
dt.date()
dt.time()
```

---

## Formatting

```python
dt.strftime("%Y-%m-%d")
```

**datetime → string**

---

## Parsing

```python
datetime.strptime(text, format)
```

**string → datetime**

---

## ISO format

```python
dt.isoformat()
```

**datetime → ISO string**

---

## Compare

```python
dt1 < dt2
dt1 > dt2
dt1 == dt2
```

---

## Change a datetime

```python
new_dt = dt.replace(hour=15)
```

Original datetime unchanged rehta hai.

---

# Golden Mental Model

```text
datetime object
      │
      ├── .year
      ├── .month
      ├── .day
      ├── .hour
      ├── .minute
      └── .second
```

Aur conversion:

```text
String
  ↓
strptime()
  ↓
datetime
  ↓
strftime()
  ↓
String
```

Aur ISO:

```text
datetime
   ↓
isoformat()
   ↓
ISO 8601 string
```

### Sabse important 4 cheezein:

**`strptime()` → String ko datetime banata hai**

**`strftime()` → datetime ko formatted string banata hai**

**`timedelta` → duration/difference**

**`ZoneInfo` → timezone information**
# Section 5.5: Switching Between Time Zones

Suppose ek meeting Riyadh time ke mutabiq:

```text
2026-10-02 09:00
```

hai.

Agar humein isi **same moment** ko London ya Karachi time mein dekhna ho, to timezone conversion karni padegi.

Python mein is kaam ke liye:

```python
astimezone()
```

use hota hai.

---

# 1. Timezone Conversion ka Basic Concept

Maan lein:

```text
Riyadh:
09:00

   ↓ convert

London:
07:00
```

Yahan humne meeting ka actual moment change nahi kiya.

Sirf **displayed local time** change hua.

Mental model:

```text
Same actual moment
       │
       ├── Riyadh → 09:00
       ├── London → 07:00
       └── Karachi → 11:00
```

---

# 2. Required Imports

```python
from datetime import datetime
from zoneinfo import ZoneInfo
```

---

# 3. Riyadh ka Timezone-Aware Datetime

```python
dt = datetime(
    2026,
    10,
    2,
    9,
    0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Output:

```text
2026-10-02 09:00:00+03:00
```

Ye datetime Riyadh timezone mein hai.

---

# 4. London Time mein Convert Karna

Ab:

```python
london_time = dt.astimezone(
    ZoneInfo("Europe/London")
)

print(london_time)
```

October mein London daylight-saving rules ki wajah se UTC offset `+01:00` ho sakta hai, isliye result:

```text
2026-10-02 07:00:00+01:00
```

ho sakta hai.

Important point:

```text
Riyadh 09:00 +03:00
        ↓
same instant
        ↓
London 07:00 +01:00
```

---

# 5. `astimezone()` ka Main Purpose

Syntax:

```python
datetime_object.astimezone(target_timezone)
```

Example:

```python
london_time = dt.astimezone(
    ZoneInfo("Europe/London")
)
```

Matlab:

> Is datetime ko target timezone ke local time mein convert karo.

---

# 6. Karachi Time

Isi datetime ko Karachi timezone mein:

```python
karachi_time = dt.astimezone(
    ZoneInfo("Asia/Karachi")
)

print(karachi_time)
```

October mein Karachi UTC+05:00 hota hai, isliye result:

```text
2026-10-02 11:00:00+05:00
```

---

# 7. Tokyo Time

```python
tokyo_time = dt.astimezone(
    ZoneInfo("Asia/Tokyo")
)

print(tokyo_time)
```

Japan UTC+09:00 use karta hai, isliye:

```text
2026-10-02 15:00:00+09:00
```

---

# 8. Complete Example

```python
from datetime import datetime
from zoneinfo import ZoneInfo

riyadh = datetime(
    2026,
    10,
    2,
    9,
    0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

london = riyadh.astimezone(
    ZoneInfo("Europe/London")
)

karachi = riyadh.astimezone(
    ZoneInfo("Asia/Karachi")
)

tokyo = riyadh.astimezone(
    ZoneInfo("Asia/Tokyo")
)

print("Riyadh :", riyadh)
print("London :", london)
print("Karachi:", karachi)
print("Tokyo  :", tokyo)
```

Conceptual output:

```text
Riyadh : 2026-10-02 09:00:00+03:00
London : 2026-10-02 07:00:00+01:00
Karachi: 2026-10-02 11:00:00+05:00
Tokyo  : 2026-10-02 15:00:00+09:00
```

---

# 9. Same Moment ka Concept

Ye sabse important part hai.

Suppose:

```text
Riyadh = 09:00 +03:00
London = 07:00 +01:00
Karachi = 11:00 +05:00
```

Clock times different hain.

Lekin actual moment:

```text
SAME
```

hai.

Isliye timezone conversion ko aise samjhein:

```text
               SAME MOMENT
                    │
       ┌────────────┼────────────┐
       ↓            ↓            ↓
    Riyadh       London       Karachi
     09:00        07:00         11:00
```

---

# 10. `replace()` aur `astimezone()` ka Difference

Ye bahut important hai.

## `replace(tzinfo=...)`

```python
dt = dt.replace(
    tzinfo=ZoneInfo("Asia/Riyadh")
)
```

Ye existing clock time ko change nahi karta.

Agar:

```text
09:00
```

hai to woh:

```text
09:00
```

hi rahega.

Bas timezone information attach/change hoti hai.

---

## `astimezone()`

```python
dt = dt.astimezone(
    ZoneInfo("Europe/London")
)
```

Ye **same actual moment** ko London ke local clock time mein convert karta hai.

Example:

```text
Riyadh 09:00
     ↓ astimezone()
London 07:00
```

---

# 11. Simple Comparison

```text
replace()
   ↓
Clock time ko preserve karta hai
Timezone information change/attach karta hai


astimezone()
   ↓
Same actual moment preserve karta hai
Clock time target timezone ke mutabiq change karta hai
```

---

# 12. `replace()` ka Dangerous Misuse

Suppose:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(
    2026,
    10,
    2,
    9,
    0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)
```

Ab agar aap:

```python
wrong = dt.replace(
    tzinfo=ZoneInfo("Europe/London")
)
```

karte hain, to Python clock ko:

```text
09:00
```

hi rakhega.

Yani ye **timezone conversion nahi** hai.

Aapne bas datetime ko ye keh diya:

> Is 09:00 ko London timezone ka samjho.

Isliye actual timezone conversion ke liye:

```python
dt.astimezone(...)
```

use karein.

---

# 13. UTC mein Convert Karna

UTC mein convert karne ke liye:

```python
from datetime import timezone

utc = dt.astimezone(timezone.utc)

print(utc)
```

Riyadh:

```text
09:00 +03:00
```

UTC:

```text
06:00 +00:00
```

---

# 14. UTC ko Common Reference Samjhein

Multiple countries ki systems mein UTC ek common reference hota hai.

Example:

```text
Riyadh
   ↓
UTC +03:00

Karachi
   ↓
UTC +05:00

Tokyo
   ↓
UTC +09:00
```

Aap kisi timestamp ko UTC mein convert kar sakte hain:

```python
utc = dt.astimezone(timezone.utc)
```

---

# 15. BMS / HVAC Practical Example

Suppose Honeywell BMS log:

```text
2026-10-02T09:30:00+03:00
```

Riyadh timezone mein hai.

Python:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

log = datetime.fromisoformat(
    "2026-10-02T09:30:00+03:00"
)

london = log.astimezone(
    ZoneInfo("Europe/London")
)

print("Riyadh :", log)
print("London :", london)
```

Ye useful ho sakta hai agar maintenance system Saudi Arabia mein ho aur reporting server ya team kisi aur timezone mein ho.

---

# 16. Work Order Example

Suppose work order start:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

start = datetime(
    2026,
    10,
    2,
    8,
    15,
    tzinfo=ZoneInfo("Asia/Riyadh")
)
```

Aapko UK team ke liye same event dikhana ho:

```python
uk_time = start.astimezone(
    ZoneInfo("Europe/London")
)

print(uk_time)
```

Aapko original `start` ka actual moment nahi badalna pada.

---

# 17. Multiple Timezone Conversion

Ek datetime ko baar-baar convert bhi kar sakte hain:

```python
riyadh = datetime(
    2026,
    10,
    2,
    9,
    0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

london = riyadh.astimezone(
    ZoneInfo("Europe/London")
)

tokyo = riyadh.astimezone(
    ZoneInfo("Asia/Tokyo")
)
```

Har object same moment ko different local timezone mein represent karta hai.

---

# 18. Timezone ka Naam Check Karna

Datetime ka timezone:

```python
print(dt.tzinfo)
```

Aur UTC offset:

```python
print(dt.utcoffset())
```

Example:

```text
+03:00:00
```

---

# 19. `tzname()`

Timezone ka short name dekhne ke liye:

```python
print(dt.tzname())
```

Result timezone rules ke according ho sakta hai.

Named `ZoneInfo` use karne ka benefit ye hai ke Python timezone rules ko handle kar sakta hai.

---

# 20. Daylight Saving Time

Kuch countries mein **Daylight Saving Time (DST)** hota hai.

Example:

```text
Europe/London
America/New_York
```

mein seasonal offset changes ho sakte hain.

Isi liye:

```python
ZoneInfo("Europe/London")
```

jaise named timezone ko use karna fixed:

```python
timezone(timedelta(...))
```

se different aur aksar zyada appropriate hota hai.

Riyadh mein normal civil time UTC+03:00 hai aur seasonal DST transition nahi hoti.

---

# 21. Fixed Offset Timezone

Kabhi aapko sirf fixed offset chahiye.

Example:

```python
from datetime import timezone, timedelta

fixed = timezone(
    timedelta(hours=3)
)
```

Ab:

```python
dt = datetime(
    2026,
    10,
    2,
    9,
    0,
    tzinfo=fixed
)
```

Lekin named timezone:

```python
ZoneInfo("Asia/Riyadh")
```

location-based timezone rules ko represent karta hai.

---

# 22. Important Rule

Agar aapko:

> "Ye exact moment Saudi Arabia mein kitne baje tha?"

jaisa question hai, to timezone-aware datetime + `astimezone()` useful hai.

Example:

```python
london_time.astimezone(
    ZoneInfo("Asia/Riyadh")
)
```

---

# 23. Reverse Conversion

London se Riyadh:

```python
riyadh = london.astimezone(
    ZoneInfo("Asia/Riyadh")
)

print(riyadh)
```

Aap kisi bhi aware datetime ko doosre timezone mein convert kar sakte hain.

---

# 24. Common Mistake

Ye:

```python
dt.replace(
    tzinfo=ZoneInfo("Europe/London")
)
```

aur ye:

```python
dt.astimezone(
    ZoneInfo("Europe/London")
)
```

same kaam nahi karte.

Yaad rakhein:

```text
replace()
    ↓
"Is clock reading ko is timezone se associate karo"


astimezone()
    ↓
"Is same moment ko target timezone mein dikhao"
```

---

# Section 5.5 — Quick Revision

### Timezone-aware datetime

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(
    2026,
    10,
    2,
    9,
    0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)
```

---

### Convert to London

```python
london = dt.astimezone(
    ZoneInfo("Europe/London")
)
```

---

### Convert to Karachi

```python
karachi = dt.astimezone(
    ZoneInfo("Asia/Karachi")
)
```

---

### Convert to UTC

```python
from datetime import timezone

utc = dt.astimezone(timezone.utc)
```

---

### Important difference

```text
replace(tzinfo=...)
        ↓
Timezone attach/change
Clock time preserve


astimezone(...)
        ↓
Timezone conversion
Same actual moment preserve
```

---

# Golden Mental Model

```text
             SAME ACTUAL MOMENT
                     │
          ┌──────────┼──────────┐
          ↓          ↓          ↓
       Riyadh     London     Karachi
       09:00       07:00      11:00
       +03:00      +01:00     +05:00
```

Clock reading **change ho sakti hai**, lekin actual moment **same** rehta hai.

### Sabse important function:

```python
astimezone()
```

**`astimezone()` = same moment ko doosre timezone ke local time mein convert karna.**
# Section 5.6: Simple Date Arithmetic

**Date arithmetic** ka matlab hai kisi date ke saath calculation karna.

Jaise:

* Aaj se 7 din baad kaun si date hogi?
* Work order ki due date 10 din baad kya hogi?
* Maintenance last date se 30 din pehle kaun si date thi?
* Inspection date ke 2 weeks baad next inspection kab hogi?

Python mein iske liye mainly:

```python
timedelta
```

use hota hai.

---

# 1. `date` Import Karna

Python ke `datetime` module mein `date` available hai:

```python
from datetime import date, timedelta
```

Ab hum date create kar sakte hain:

```python
d = date(2026, 10, 2)

print(d)
```

Output:

```text
2026-10-02
```

---

# 2. Date Mein Days Add Karna

Suppose date hai:

```python
from datetime import date, timedelta

d = date(2026, 10, 2)
```

Ab 7 days add:

```python
new_date = d + timedelta(days=7)

print(new_date)
```

Output:

```text
2026-10-09
```

Yani:

```text
2026-10-02
     +
   7 days
     ↓
2026-10-09
```

---

# 3. Date Se Days Subtract Karna

Agar 7 days pehle ki date chahiye:

```python
old_date = d - timedelta(days=7)

print(old_date)
```

Output:

```text
2026-09-25
```

Mental model:

```text
date + timedelta
       ↓
future date

date - timedelta
       ↓
past date
```

---

# 4. Weeks Add Karna

`timedelta()` mein `weeks` bhi use kar sakte hain.

```python
d = date(2026, 10, 2)

new_date = d + timedelta(weeks=2)

print(new_date)
```

Output:

```text
2026-10-16
```

2 weeks = 14 days.

Equivalent:

```python
d + timedelta(days=14)
```

---

# 5. Multiple Values Ek Saath

Aap days aur weeks dono specify kar sakte hain:

```python
result = d + timedelta(
    weeks=1,
    days=3
)

print(result)
```

Calculation:

```text
1 week = 7 days
7 + 3 = 10 days
```

Result:

```text
2026-10-12
```

---

# 6. Hours, Minutes, Seconds

`timedelta` sirf days aur weeks ke liye nahi hai.

Ye bhi use kar sakte hain:

```python
timedelta(
    days=1,
    hours=5,
    minutes=30,
    seconds=10
)
```

Example:

```python
from datetime import datetime, timedelta

dt = datetime(2026, 10, 2, 9, 0)

new_dt = dt + timedelta(hours=5)

print(new_dt)
```

Output:

```text
2026-10-02 14:00:00
```

---

# 7. `date` Aur `datetime` Mein Difference

Ye distinction important hai.

### `date`

Sirf calendar date:

```python
date(2026, 10, 2)
```

Result:

```text
2026-10-02
```

### `datetime`

Date + time:

```python
datetime(2026, 10, 2, 9, 30)
```

Result:

```text
2026-10-02 09:30:00
```

Isliye:

```text
date
↓
2026-10-02


datetime
↓
2026-10-02 09:30:00
```

---

# 8. Today's Date

Current date lene ke liye:

```python
from datetime import date

today = date.today()

print(today)
```

Example output:

```text
2026-10-02
```

Output actual run ke waqt ki date par depend karega.

---

# 9. 30 Days From Today

Example:

```python
from datetime import date, timedelta

today = date.today()

future_date = today + timedelta(days=30)

print("Today:", today)
print("After 30 days:", future_date)
```

Concept:

```text
Today
  +
30 days
  ↓
Future Date
```

Ye work-order scheduling mein useful hai.

---

# 10. 30 Days Before Today

```python
past_date = today - timedelta(days=30)

print("30 days before:", past_date)
```

Iska use historical records filter karne mein ho sakta hai.

Example:

> Last 30 days ke work orders nikalne hain.

---

# 11. Work Order Example

Suppose preventive maintenance complete hui:

```python
from datetime import date, timedelta

completed_date = date(2026, 10, 2)

due_date = completed_date + timedelta(days=30)

print("Completed:", completed_date)
print("Next Due:", due_date)
```

Output:

```text
Completed: 2026-10-02
Next Due: 2026-11-01
```

Yahan humne simple date arithmetic use ki.

---

# 12. PPM Example

Suppose HVAC equipment ka PPM har 7 din mein hai:

```python
from datetime import date, timedelta

last_ppm = date(2026, 10, 2)

next_ppm = last_ppm + timedelta(days=7)

print("Last PPM:", last_ppm)
print("Next PPM:", next_ppm)
```

Output:

```text
Last PPM: 2026-10-02
Next PPM: 2026-10-09
```

Agar monthly interval exactly **calendar month** ke hisaab se hai, to `timedelta(days=30)` hamesha correct replacement nahi hota. Is point ko Section 5.8 mein detail se dekhenge.

---

# 13. Date Difference

Do dates ko subtract kar sakte hain:

```python
from datetime import date

start = date(2026, 10, 2)
end = date(2026, 10, 12)

difference = end - start

print(difference)
```

Output:

```text
10 days, 0:00:00
```

`difference` ka type:

```python
print(type(difference))
```

Output:

```text
<class 'datetime.timedelta'>
```

Yani date subtraction ka result `timedelta` hota hai.

---

# 14. Difference Ke Days

Agar sirf number of days chahiye:

```python
print(difference.days)
```

Output:

```text
10
```

Example:

```python
start = date(2026, 10, 2)
end = date(2026, 10, 20)

days = (end - start).days

print(days)
```

Output:

```text
18
```

---

# 15. Future Date Check Karna

Aap dates compare bhi kar sakte hain.

```python
from datetime import date

today = date.today()
due_date = date(2026, 10, 10)

if due_date > today:
    print("Due date is in the future")
```

Basic comparison operators:

```text
<    less than
>    greater than
<=   less than or equal
>=   greater than or equal
==   equal
!=   not equal
```

---

# 16. Overdue Work Order Example

Suppose:

```python
from datetime import date

today = date(2026, 10, 15)
due_date = date(2026, 10, 10)
```

Check:

```python
if due_date < today:
    print("Work order is overdue")
```

Output:

```text
Work order is overdue
```

Logic:

```text
Due Date < Today
      ↓
Overdue
```

---

# 17. Due Today

```python
if due_date == today:
    print("Due today")
```

Agar dono dates same hain to work order aaj due hai.

---

# 18. Days Remaining

Suppose:

```python
from datetime import date

today = date(2026, 10, 2)
due_date = date(2026, 10, 12)

remaining = (due_date - today).days

print("Days remaining:", remaining)
```

Output:

```text
Days remaining: 10
```

Ye dashboard ya work-order automation mein kaafi useful concept hai.

---

# 19. Negative Days

Agar due date already pass ho chuki hai:

```python
today = date(2026, 10, 15)
due_date = date(2026, 10, 10)

remaining = (due_date - today).days

print(remaining)
```

Output:

```text
-5
```

`-5` ka matlab:

```text
Due date 5 days pehle thi.
```

Isliye negative result ko overdue indicator ki tarah use kiya ja sakta hai.

---

# 20. `timedelta` Object Store Karna

Aap directly bhi kar sakte hain:

```python
from datetime import timedelta

duration = timedelta(days=30)

print(duration)
```

Output:

```text
30 days, 0:00:00
```

Phir:

```python
from datetime import date

start = date(2026, 10, 2)

end = start + duration

print(end)
```

Output:

```text
2026-11-01
```

---

# 21. Date Arithmetic Chain Karna

Aap multiple calculations kar sakte hain:

```python
from datetime import date, timedelta

d = date(2026, 10, 2)

d = d + timedelta(days=7)
d = d + timedelta(days=14)

print(d)
```

Calculation:

```text
Oct 2
 + 7 days
   ↓
Oct 9

 + 14 days
   ↓
Oct 23
```

Output:

```text
2026-10-23
```

---

# 22. Important: Month = 30 Days Nahi

Beginners aksar ye karte hain:

```python
date + timedelta(days=30)
```

aur assume karte hain:

> 1 month add ho gaya.

Lekin technically:

```text
1 month ≠ always 30 days
```

Example:

```text
January → 31 days
February → 28/29 days
April → 30 days
```

Isliye agar requirement hai:

> "Exactly one calendar month baad"

to `timedelta(days=30)` har situation mein correct nahi hoga.

Is topic ko hum **Section 5.8 — Subtracting months from a date accurately** mein detail se dekhenge.

---

# 23. `timedelta` Ke Common Arguments

```python
timedelta(
    days=10,
    seconds=30,
    microseconds=500,
    milliseconds=100,
    minutes=20,
    hours=5,
    weeks=2
)
```

Commonly used:

```text
weeks
days
hours
minutes
seconds
```

---

# 24. HVAC Maintenance Example

Suppose AHU inspection:

```python
from datetime import date, timedelta

inspection_date = date(2026, 10, 2)

next_inspection = inspection_date + timedelta(
    weeks=1
)

print("Inspection:", inspection_date)
print("Next:", next_inspection)
```

Output:

```text
Inspection: 2026-10-02
Next: 2026-10-09
```

Agar inspection har 2 weeks hai:

```python
next_inspection = inspection_date + timedelta(
    weeks=2
)
```

---

# 25. Work Order Data Example

Suppose CSV se date string mili:

```text
2026-10-02
```

Pehle usko `date` object mein convert kar sakte hain:

```python
from datetime import date

work_order_date = date.fromisoformat(
    "2026-10-02"
)

print(work_order_date)
```

Output:

```text
2026-10-02
```

Phir 14 days add:

```python
from datetime import timedelta

next_date = work_order_date + timedelta(days=14)

print(next_date)
```

Output:

```text
2026-10-16
```

Ye real data processing mein bohat common pattern hai:

```text
String
  ↓
date object
  ↓
date arithmetic
  ↓
new date
```

---

# 26. Date Arithmetic Ka Mental Model

Isko yaad rakhein:

```text
date + timedelta
       ↓
future date


date - timedelta
       ↓
past date


date - date
       ↓
timedelta
```

Example:

```python
d1 + timedelta(days=10)
```

→ future date

```python
d1 - timedelta(days=10)
```

→ past date

```python
d2 - d1
```

→ duration / difference

---

# 27. Quick Practice

### Question 1

```python
from datetime import date, timedelta

d = date(2026, 10, 2)

result = d + timedelta(days=5)

print(result)
```

Answer:

```text
2026-10-07
```

---

### Question 2

```python
d = date(2026, 10, 20)

result = d - timedelta(days=8)

print(result)
```

Answer:

```text
2026-10-12
```

---

### Question 3

```python
start = date(2026, 10, 2)
end = date(2026, 10, 17)

print((end - start).days)
```

Answer:

```text
15
```

---

# Section 5.6 — Final Summary

### `date`

Calendar date:

```python
date(2026, 10, 2)
```

### `timedelta`

Duration:

```python
timedelta(days=7)
```

### Future date

```python
d + timedelta(days=7)
```

### Past date

```python
d - timedelta(days=7)
```

### Difference

```python
d2 - d1
```

Result:

```text
timedelta
```

### Number of days

```python
(d2 - d1).days
```

### Most important pattern

```text
Date + Duration = Future Date

Date - Duration = Past Date

Date - Date = Duration
```

Aur ek important warning:

```text
30 days
≠
always 1 calendar month
```

Calendar months ko accurately handle karna next relevant sections mein aur specifically **5.8** mein dekhenge.
# Section 5.7: Converting Timestamp to Datetime

## 1. Timestamp Kya Hota Hai?

Programming mein **timestamp** aksar ek numeric value hoti hai jo kisi specific moment ko represent karti hai.

Sabse common type hai:

**Unix timestamp / Unix time**

Ismein time ko generally:

> **1 January 1970, 00:00:00 UTC**

se guzre hue **seconds** ke form mein represent kiya jata hai.

Example:

```python
timestamp = 0
```

ka matlab:

```text
1970-01-01 00:00:00 UTC
```

---

# 2. Timestamp Ka Example

Ek timestamp:

```python
timestamp = 178... 
```

jaisi large number ho sakti hai.

Insaan ke liye ye number samajhna mushkil hota hai.

Datetime:

```text
2026-10-02 09:30:00
```

zyada readable hai.

Isliye data processing mein aksar:

```text
Timestamp
    ↓
Datetime
```

conversion karni padti hai.

---

# 3. `datetime.fromtimestamp()`

Python mein local timezone ke according timestamp convert karne ke liye:

```python
datetime.fromtimestamp()
```

use kar sakte hain.

Example:

```python
from datetime import datetime

timestamp = 1780349400

dt = datetime.fromtimestamp(timestamp)

print(dt)
```

Yahan `dt` ek `datetime` object hoga.

**Important:** exact output timestamp ki value aur computer ke local timezone par depend karega.

---

# 4. UTC Mein Convert Karna

Agar timestamp ko specifically **UTC** mein convert karna hai, to:

```python
from datetime import datetime, timezone

timestamp = 1780349400

dt = datetime.fromtimestamp(
    timestamp,
    tz=timezone.utc
)

print(dt)
```

Result timezone-aware datetime hoga:

```text
YYYY-MM-DD HH:MM:SS+00:00
```

---

# 5. Riyadh Time Mein Convert Karna

Agar timestamp kisi server se aaya hai aur humein Riyadh local time chahiye:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

timestamp = 1780349400

dt = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Ab result Riyadh timezone ke according hoga.

Mental model:

```text
Unix Timestamp
      ↓
fromtimestamp()
      ↓
Timezone-aware datetime
      ↓
Asia/Riyadh
```

---

# 6. `fromtimestamp()` Ka Syntax

Basic:

```python
datetime.fromtimestamp(timestamp)
```

Timezone ke saath:

```python
datetime.fromtimestamp(
    timestamp,
    tz=timezone
)
```

Example:

```python
dt = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)
```

---

# 7. UTC Timestamp Aur Local Time

Unix timestamp ka important benefit ye hai ke ye ek **absolute moment** ko represent karta hai.

Example:

```text
Timestamp
    ↓
same instant
    ├── UTC
    ├── Riyadh
    ├── Karachi
    └── Tokyo
```

Sirf local clock reading change hoti hai.

---

# 8. Same Timestamp Ko Different Timezones Mein

```python
from datetime import datetime
from zoneinfo import ZoneInfo

timestamp = 1780349400

riyadh = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)

karachi = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Karachi")
)

tokyo = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Tokyo")
)

print("Riyadh :", riyadh)
print("Karachi:", karachi)
print("Tokyo  :", tokyo)
```

Teenon datetime different clock times show karenge, lekin represent **same actual moment** karte hain.

---

# 9. `fromtimestamp()` vs `utcfromtimestamp()`

Python mein ek purana/common function:

```python
datetime.utcfromtimestamp()
```

bhi milta hai.

Lekin modern timezone-aware code mein better approach hai:

```python
datetime.fromtimestamp(
    timestamp,
    tz=timezone.utc
)
```

Example:

```python
from datetime import datetime, timezone

dt = datetime.fromtimestamp(
    timestamp,
    tz=timezone.utc
)
```

Iska fayda ye hai ke result explicitly **timezone-aware** hota hai.

---

# 10. Timestamp Se Date Nikalna

Suppose timestamp convert kiya:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)
```

Sirf date chahiye:

```python
d = dt.date()

print(d)
```

Result:

```text
YYYY-MM-DD
```

Yani:

```text
timestamp
    ↓
datetime
    ↓
date
```

---

# 11. Timestamp Se Time Nikalna

Sirf time chahiye:

```python
t = dt.time()

print(t)
```

Yani:

```text
datetime
   ↓
time
```

---

# 12. Timestamp Float Bhi Ho Sakta Hai

Timestamp sirf integer nahi hota.

Example:

```python
timestamp = 1780349400.5
```

`.5` fractional second ko represent karta hai.

Python:

```python
dt = datetime.fromtimestamp(
    timestamp,
    tz=timezone.utc
)
```

microseconds tak information preserve kar sakta hai.

---

# 13. Milliseconds Timestamp

Ye practical point **bahut important** hai.

Kabhi API ya JavaScript se timestamp **milliseconds** mein milta hai.

Example:

```text
1780349400000
```

Ye seconds nahi, milliseconds ho sakta hai.

Python ka `fromtimestamp()` normally **seconds** expect karta hai.

Isliye milliseconds ko:

```python
timestamp_ms = 1780349400000

timestamp = timestamp_ms / 1000
```

karna padega.

Phir:

```python
dt = datetime.fromtimestamp(
    timestamp,
    tz=timezone.utc
)
```

---

# 14. Seconds vs Milliseconds

Yaad rakhein:

```text
Unix timestamp:
seconds

JavaScript Date.now():
milliseconds
```

Example:

```python
timestamp_ms = 1780349400000

timestamp_seconds = timestamp_ms / 1000
```

Phir conversion.

Agar milliseconds ko directly `fromtimestamp()` mein de diya, to Python usko seconds samjhega aur date bahut door future mein chali jayegi ya platform-specific range error aa sakta hai.

---

# 15. Practical API Example

Suppose API response:

```python
data = {
    "equipment": "AHU-01",
    "timestamp": 1780349400
}
```

Timestamp extract:

```python
timestamp = data["timestamp"]
```

Riyadh datetime:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Ab raw numeric timestamp ki jagah readable datetime mil gaya.

---

# 16. HVAC Data Example

Suppose BMS/export system se:

```python
record = {
    "equipment": "AHU-01",
    "timestamp": 1780349400,
    "temperature": 22.5
}
```

Timestamp convert:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

timestamp = record["timestamp"]

dt = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)

print("Equipment:", record["equipment"])
print("Time:", dt)
print("Temperature:", record["temperature"])
```

Concept:

```text
Raw BMS Data
     ↓
timestamp
     ↓
datetime
     ↓
Riyadh local time
```

Ye logs aur trend analysis mein useful hai.

---

# 17. Work Order Example

Suppose database mein:

```python
work_order = {
    "wo": "WO-1001",
    "created_timestamp": 1780349400
}
```

Convert:

```python
created = datetime.fromtimestamp(
    work_order["created_timestamp"],
    tz=ZoneInfo("Asia/Riyadh")
)

print(created)
```

Ab aap:

```python
created.year
created.month
created.day
created.hour
created.minute
```

jaise attributes use kar sakte hain.

---

# 18. Timestamp Se Date Arithmetic

Timestamp ko datetime mein convert karne ke baad aap Section 5.6 wali arithmetic bhi kar sakte hain.

```python
from datetime import datetime, timedelta
from zoneinfo import ZoneInfo

dt = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)

next_date = dt + timedelta(days=7)

print(next_date)
```

Yani:

```text
Timestamp
    ↓
Datetime
    ↓
+ 7 days
    ↓
Future datetime
```

---

# 19. Timestamp Ko Wapas Timestamp Banana

Agar aapke paas datetime hai aur timestamp wapas chahiye:

```python
timestamp = dt.timestamp()

print(timestamp)
```

Example:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

timestamp = dt.timestamp()

print(timestamp)
```

`timestamp()` seconds since Unix epoch return karta hai, generally float form mein.

---

# 20. Round Trip

Ye concept important hai:

```text
timestamp
    ↓
fromtimestamp()
    ↓
datetime
    ↓
timestamp()
    ↓
timestamp
```

Example:

```python
dt = datetime.fromtimestamp(
    timestamp,
    tz=timezone.utc
)

new_timestamp = dt.timestamp()
```

Original aur converted timestamp essentially same instant ko represent karenge, subject to normal floating-point precision details.

---

# 21. `fromtimestamp()` vs `fromisoformat()`

Dono ka kaam different hai.

### `fromisoformat()`

Jab input string ISO format mein ho:

```python
text = "2026-10-02T09:30:00+03:00"

dt = datetime.fromisoformat(text)
```

Flow:

```text
ISO String
   ↓
fromisoformat()
   ↓
datetime
```

### `fromtimestamp()`

Jab input Unix timestamp ho:

```python
timestamp = 1780349400

dt = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)
```

Flow:

```text
Unix Timestamp
      ↓
fromtimestamp()
      ↓
datetime
```

---

# 22. Comparison Table

| Input                         | Function          | Result           |
| ----------------------------- | ----------------- | ---------------- |
| `"2026-10-02T09:30:00+03:00"` | `fromisoformat()` | datetime         |
| `"02/10/2026"`                | `strptime()`      | datetime         |
| Unix timestamp                | `fromtimestamp()` | datetime         |
| datetime                      | `strftime()`      | formatted string |
| datetime                      | `isoformat()`     | ISO string       |
| datetime                      | `timestamp()`     | Unix timestamp   |

Ye table yaad rakhna useful hai.

---

# 23. Common Mistake — Seconds vs Milliseconds

Agar API:

```python
timestamp = 1780349400000
```

de rahi hai aur aap:

```python
datetime.fromtimestamp(timestamp)
```

kar dete hain, to problem ho sakti hai.

Pehle identify karein:

```text
seconds?
milliseconds?
```

Agar milliseconds hain:

```python
timestamp = timestamp_ms / 1000
```

Phir convert karein.

---

# 24. Common Mistake — Local Time Assume Karna

Ye:

```python
dt = datetime.fromtimestamp(timestamp)
```

system ke local timezone par depend kar sakta hai.

Agar aapko predictable timezone-aware result chahiye, explicitly timezone dena better hai:

```python
dt = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)
```

Ya UTC:

```python
dt = datetime.fromtimestamp(
    timestamp,
    tz=timezone.utc
)
```

---

# 25. Best Practice

Agar application multiple countries/timezones mein data handle karti hai, to generally:

```text
Store/communicate:
UTC / timezone-aware timestamps

Display:
User/location ke local timezone mein
```

Example:

```text
Database
   ↓
UTC timestamp
   ↓
Application
   ↓
Asia/Riyadh
   ↓
User ko local time
```

Ye approach timezone-related confusion kam karti hai.

---

# 26. Mini Practice

### Question 1

Timestamp ko UTC datetime mein convert karein:

```python
timestamp = 1780349400
```

Answer:

```python
from datetime import datetime, timezone

dt = datetime.fromtimestamp(
    timestamp,
    tz=timezone.utc
)

print(dt)
```

---

### Question 2

Riyadh timezone use karein:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

---

### Question 3

Datetime se Unix timestamp:

```python
timestamp = dt.timestamp()
```

---

# Section 5.7 — Final Summary

### Unix timestamp

Usually:

```text
Seconds since
1970-01-01 00:00:00 UTC
```

### Timestamp → datetime

```python
datetime.fromtimestamp(
    timestamp,
    tz=ZoneInfo("Asia/Riyadh")
)
```

### UTC

```python
datetime.fromtimestamp(
    timestamp,
    tz=timezone.utc
)
```

### Datetime → timestamp

```python
dt.timestamp()
```

### Milliseconds

Agar input milliseconds mein hai:

```python
timestamp_seconds = timestamp_ms / 1000
```

phir:

```python
datetime.fromtimestamp(
    timestamp_seconds,
    tz=timezone.utc
)
```

### Main mental model

```text
Unix Timestamp
      ↓
fromtimestamp()
      ↓
Timezone-aware datetime
      ↓
date / time / arithmetic / formatting
```

Aur reverse:

```text
datetime
    ↓
timestamp()
    ↓
Unix Timestamp
```

**Important:** `fromtimestamp()` ke saath timezone explicitly dena especially useful hai jab aap predictable timezone-aware result chahte hain.
# Section 5.8: Subtracting Months from a Date Accurately

## 1. Problem Kya Hai?

Suppose hamare paas date hai:

```python
from datetime import date

d = date(2026, 3, 31)
```

Ab hum kehna chahte hain:

> Is date se **1 month pehle** ki date kya hai?

Beginner naturally soch sakta hai:

```python
d - timedelta(days=30)
```

Lekin ye approach har case mein correct nahi hoti.

Kyun?

Kyuki har month ke days same nahi hote:

```text
January   → 31
February  → 28 / 29
March     → 31
April     → 30
May       → 31
```

Isliye:

```text
1 month ≠ always 30 days
```

---

# 2. `timedelta` Month Support Nahi Karta

`timedelta` mein aap likh sakte hain:

```python
timedelta(days=30)
```

Lekin:

```python
timedelta(months=1)
```

valid nahi hai.

Example:

```python
from datetime import timedelta

x = timedelta(months=1)
```

Ye error dega, kyunki `timedelta` months/years ko directly represent nahi karta.

Reason simple hai:

> Month ki length fixed nahi hoti.

---

# 3. Calendar Month Kya Hota Hai?

Calendar month ka matlab hai month number ko change karna.

Example:

```text
2026-10-15
     ↓
1 month before
     ↓
2026-09-15
```

Yahan exactly calendar month change hua.

Another example:

```text
2026-05-20
     ↓
1 month before
     ↓
2026-04-20
```

---

# 4. `dateutil` Ka Use

Calendar months ko accurately handle karne ke liye commonly:

```python
dateutil
```

library use ki jati hai.

Agar installed nahi hai:

```text
python -m pip install python-dateutil
```

Phir:

```python
from dateutil.relativedelta import relativedelta
```

---

# 5. One Month Subtract Karna

Example:

```python
from datetime import date
from dateutil.relativedelta import relativedelta

d = date(2026, 10, 15)

result = d - relativedelta(months=1)

print(result)
```

Output:

```text
2026-09-15
```

Yani:

```text
October 15
    ↓
1 month back
    ↓
September 15
```

---

# 6. Multiple Months Subtract Karna

2 months:

```python
result = d - relativedelta(months=2)
```

Agar:

```text
2026-10-15
```

hai:

```text
2026-08-15
```

milega.

3 months:

```python
result = d - relativedelta(months=3)
```

Result:

```text
2026-07-15
```

---

# 7. Months Add Bhi Kar Sakte Hain

`relativedelta` sirf subtraction ke liye nahi hai.

```python
result = d + relativedelta(months=1)
```

Example:

```text
2026-10-15
     ↓
+ 1 month
     ↓
2026-11-15
```

---

# 8. Main Difference

### `timedelta`

Duration-based calculation:

```python
d + timedelta(days=30)
```

### `relativedelta`

Calendar-based calculation:

```python
d + relativedelta(months=1)
```

Mental model:

```text
timedelta
   ↓
fixed duration


relativedelta
   ↓
calendar-aware duration
```

---

# 9. Month-End Problem

Ab ek interesting case.

Suppose:

```python
d = date(2026, 3, 31)
```

1 month subtract karein:

```python
result = d - relativedelta(months=1)
```

Result:

```text
2026-02-28
```

Kyun?

February 2026 mein 31st day nahi hai.

Python valid calendar date maintain karta hai.

```text
March 31
   ↓
February mein 31 nahi hai
   ↓
February 28
```

---

# 10. Leap Year Example

Leap year mein February ke 29 days ho sakte hain.

Example:

```python
d = date(2024, 3, 31)

result = d - relativedelta(months=1)

print(result)
```

Result:

```text
2024-02-29
```

Kyunki 2024 leap year hai.

```text
2024
 ↓
Leap Year
 ↓
February = 29 days
```

---

# 11. Ye `timedelta(days=30)` Se Different Hai

Suppose:

```python
d = date(2026, 3, 31)
```

Using:

```python
d - timedelta(days=30)
```

aap calendar month subtraction nahi kar rahe.

Aap simply:

> 30 actual days subtract

kar rahe hain.

Ye result calendar-month logic se different ho sakta hai.

Compare:

```python
d - timedelta(days=30)
```

versus:

```python
d - relativedelta(months=1)
```

**Purpose different hai.**

---

# 12. Work Order Example

Suppose ek work order ki date:

```python
from datetime import date
from dateutil.relativedelta import relativedelta

work_order_date = date(2026, 10, 2)

previous_month = work_order_date - relativedelta(
    months=1
)

print(previous_month)
```

Output:

```text
2026-09-02
```

Agar aapko:

> Previous calendar month ki same day

chahiye, `relativedelta(months=1)` suitable approach hai.

---

# 13. PPM Example

Suppose equipment ka maintenance:

```text
2026-10-15
```

aur aapko 3 calendar months pehle ka date chahiye:

```python
from dateutil.relativedelta import relativedelta

previous = work_order_date - relativedelta(
    months=3
)
```

Result:

```text
2026-07-15
```

---

# 14. Month-End PPM Example

Suppose:

```python
ppm_date = date(2026, 5, 31)
```

1 month back:

```python
previous = ppm_date - relativedelta(
    months=1
)
```

Result:

```text
2026-04-30
```

Kyunki April mein 31st nahi hota.

Ye calendar arithmetic ka important feature hai.

---

# 15. Months + Days

`relativedelta` mein months aur days dono specify kar sakte hain:

```python
result = d + relativedelta(
    months=1,
    days=5
)
```

Example:

```text
October 15
    ↓
+ 1 month
    ↓
November 15
    ↓
+ 5 days
    ↓
November 20
```

---

# 16. Years Bhi

`relativedelta` years ke saath bhi kaam karta hai:

```python
result = d + relativedelta(years=1)
```

Example:

```text
2026-10-15
    ↓
+ 1 year
    ↓
2027-10-15
```

Subtract:

```python
result = d - relativedelta(years=1)
```

---

# 17. Months Aur Years Saath

```python
result = d + relativedelta(
    years=1,
    months=2
)
```

Matlab:

```text
+ 1 year
+ 2 months
```

---

# 18. Last Month Ka Date

Suppose:

```python
d = date(2026, 10, 15)
```

Previous month:

```python
previous_month = d - relativedelta(months=1)
```

Result:

```text
2026-09-15
```

---

# 19. Previous Month Ki First Date

Agar requirement hai:

> Previous month ki first date

to month arithmetic ke baad:

```python
previous_month = d - relativedelta(months=1)

first_day = previous_month.replace(day=1)

print(first_day)
```

For:

```text
2026-10-15
```

result:

```text
2026-09-01
```

Yahan:

```python
replace(day=1)
```

sirf day ko `1` karta hai.

---

# 20. Current Month Ki First Date

```python
first_day = d.replace(day=1)

print(first_day)
```

Agar:

```text
2026-10-15
```

hai:

```text
2026-10-01
```

milega.

---

# 21. Month Arithmetic + `datetime`

Ye sirf `date` ke saath nahi, `datetime` ke saath bhi kaam karta hai.

```python
from datetime import datetime
from dateutil.relativedelta import relativedelta

dt = datetime(2026, 10, 15, 9, 30)

previous = dt - relativedelta(months=1)

print(previous)
```

Output:

```text
2026-09-15 09:30:00
```

Time bhi preserve hua.

---

# 22. Timezone-Aware Datetime Ke Saath

Timezone-aware datetime bhi use kar sakte hain:

```python
from datetime import datetime
from zoneinfo import ZoneInfo
from dateutil.relativedelta import relativedelta

dt = datetime(
    2026,
    10,
    15,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

previous = dt - relativedelta(months=1)

print(previous)
```

Result approximately:

```text
2026-09-15 09:30:00+03:00
```

Yahan calendar month subtraction ho rahi hai.

---

# 23. `relativedelta` vs `timedelta`

| Feature                    | `timedelta` | `relativedelta` |
| -------------------------- | ----------- | --------------- |
| Days                       | Yes         | Yes             |
| Weeks                      | Yes         | Yes             |
| Hours                      | Yes         | Yes             |
| Minutes                    | Yes         | Yes             |
| Seconds                    | Yes         | Yes             |
| Months                     | No          | Yes             |
| Years                      | No          | Yes             |
| Calendar-aware month logic | No          | Yes             |

Simple rule:

```text
Days/hours/minutes
        ↓
timedelta


Months/years/calendar arithmetic
        ↓
relativedelta
```

---

# 24. Important Installation Point

`timedelta` Python ke standard library ka part hai:

```python
from datetime import timedelta
```

Koi installation nahi chahiye.

Lekin:

```python
from dateutil.relativedelta import relativedelta
```

ke liye `python-dateutil` package install karna pad sakta hai:

```text
python -m pip install python-dateutil
```

---

# 25. Practical Maintenance Example

Suppose PPM schedule:

```python
from datetime import date
from dateutil.relativedelta import relativedelta

last_ppm = date(2026, 10, 31)

next_ppm = last_ppm + relativedelta(
    months=1
)

print("Last PPM:", last_ppm)
print("Next PPM:", next_ppm)
```

Result:

```text
Last PPM: 2026-10-31
Next PPM: 2026-11-30
```

Yahan calendar-month logic important hai.

---

# 26. Database/Data Analysis Example

Suppose records mein date:

```python
record_date = date(2026, 10, 2)
```

Aap previous 3 calendar months ka starting point nikalna chahte hain:

```python
start_date = record_date - relativedelta(
    months=3
)

print(start_date)
```

Output:

```text
2026-07-02
```

Ye reporting/data filtering mein useful hai.

---

# 27. Common Beginner Mistake

❌ Agar requirement hai **one calendar month**:

```python
date - timedelta(days=30)
```

Blindly use mat karein.

✅ Calendar month ke liye:

```python
date - relativedelta(months=1)
```

Use karein.

Lekin agar requirement literally hai:

> 30 days before

to:

```python
date - timedelta(days=30)
```

bilkul appropriate hai.

Difference requirement ka hai.

---

# 28. Requirement Ko Pehle Samjhein

Agar user kahe:

### "30 days before"

```python
timedelta(days=30)
```

### "1 month before"

```python
relativedelta(months=1)
```

### "1 year before"

```python
relativedelta(years=1)
```

Ye distinction real applications mein important hai.

---

# 29. Quick Practice

### Question 1

```python
d = date(2026, 10, 15)

result = d - relativedelta(months=1)

print(result)
```

Answer:

```text
2026-09-15
```

---

### Question 2

```python
d = date(2026, 3, 31)

result = d - relativedelta(months=1)

print(result)
```

Answer:

```text
2026-02-28
```

---

### Question 3

```python
d = date(2024, 3, 31)

result = d - relativedelta(months=1)

print(result)
```

Answer:

```text
2024-02-29
```

Kyunki 2024 leap year hai.

---

# Section 5.8 — Final Summary

## Fixed duration

```python
timedelta(days=30)
```

Matlab:

> Exactly 30 days.

## Calendar month

```python
relativedelta(months=1)
```

Matlab:

> One calendar month.

## Subtract month

```python
d - relativedelta(months=1)
```

## Add month

```python
d + relativedelta(months=1)
```

## Subtract year

```python
d - relativedelta(years=1)
```

## Add year

```python
d + relativedelta(years=1)
```

### Golden Rule

```text
30 days
   ≠
1 calendar month
```

Aur:

```text
timedelta
   ↓
fixed duration


relativedelta
   ↓
calendar-aware duration
```

### Maintenance example

```python
from datetime import date
from dateutil.relativedelta import relativedelta

last_ppm = date(2026, 10, 31)

next_ppm = last_ppm + relativedelta(
    months=1
)

print(next_ppm)
```

Result:

```text
2026-11-30
```

Isliye monthly schedules, billing dates, subscription dates, PPM schedules aur calendar-based reporting mein **calendar month vs fixed number of days** ka difference samajhna zaroori hai.
# Section 5.9: Parsing an Arbitrary ISO 8601 Timestamp with Minimal Libraries

## 1. ISO 8601 Kya Hai?

**ISO 8601** date aur time represent karne ka international standard format hai.

Common example:

```text
2026-10-02T09:30:00
```

Yahan:

```text
2026 → Year
10   → Month
02   → Day
T    → Date aur time ke beech separator
09   → Hour
30   → Minute
00   → Second
```

Agar timezone offset bhi ho:

```text
2026-10-02T09:30:00+03:00
```

Yahan:

```text
+03:00
```

timezone offset hai.

---

# 2. "Arbitrary" Ka Matlab Kya Hai?

Yahan **arbitrary** ka matlab random nahi hai.

Matlab:

> Input ISO 8601 format ke different valid forms mein aa sakta hai.

For example:

```text
2026-10-02
```

ya:

```text
2026-10-02T09:30:00
```

ya:

```text
2026-10-02T09:30:00+03:00
```

ya:

```text
2026-10-02T06:30:00Z
```

Humein in formats ko handle karna ho sakta hai.

---

# 3. Sabse Simple Method: `fromisoformat()`

Modern Python mein built-in:

```python
datetime.fromisoformat()
```

bahut useful hai.

Import:

```python
from datetime import datetime
```

Example:

```python
text = "2026-10-02T09:30:00"

dt = datetime.fromisoformat(text)

print(dt)
```

Output:

```text
2026-10-02 09:30:00
```

Yahan external library ki zaroorat nahi.

---

# 4. ISO Timestamp with Timezone

Example:

```python
text = "2026-10-02T09:30:00+03:00"

dt = datetime.fromisoformat(text)

print(dt)
```

Output:

```text
2026-10-02 09:30:00+03:00
```

Ab `dt` **timezone-aware** datetime hai.

Check:

```python
print(dt.tzinfo)
```

---

# 5. `Z` Ka Matlab

ISO 8601 mein:

```text
Z
```

ka matlab hota hai:

```text
UTC
```

Example:

```text
2026-10-02T06:30:00Z
```

Matlab:

```text
2026-10-02 06:30 UTC
```

Modern Python versions mein:

```python
from datetime import datetime

text = "2026-10-02T06:30:00Z"

dt = datetime.fromisoformat(text)

print(dt)
```

`Z` ko UTC ke taur par parse kiya ja sakta hai.

Result:

```text
2026-10-02 06:30:00+00:00
```

---

# 6. `Z` Ko `+00:00` Mein Convert Karna

Agar compatibility concern ho ya aap explicitly offset notation use karna chahte hon:

```python
text = "2026-10-02T06:30:00Z"

text = text.replace("Z", "+00:00")

dt = datetime.fromisoformat(text)

print(dt)
```

Output:

```text
2026-10-02 06:30:00+00:00
```

Concept:

```text
Z
↓
+00:00
↓
UTC
```

Lekin agar aapka Python version directly `Z` support karta hai, to unnecessary replacement ki zaroorat nahi.

---

# 7. Date-Only ISO String

ISO input sirf date bhi ho sakta hai:

```text
2026-10-02
```

Use:

```python
from datetime import date

d = date.fromisoformat("2026-10-02")

print(d)
```

Output:

```text
2026-10-02
```

Yahan `datetime.fromisoformat()` ke bajaye:

```python
date.fromisoformat()
```

use karna natural hai.

---

# 8. Date Aur Datetime Mein Difference

```text
2026-10-02
```

→ `date`

```text
2026-10-02T09:30:00
```

→ `datetime`

Example:

```python
from datetime import date, datetime

d = date.fromisoformat("2026-10-02")

dt = datetime.fromisoformat(
    "2026-10-02T09:30:00"
)
```

---

# 9. ISO String With Fractional Seconds

Timestamp mein milliseconds/microseconds bhi ho sakte hain:

```text
2026-10-02T09:30:00.123456
```

Python:

```python
from datetime import datetime

text = "2026-10-02T09:30:00.123456"

dt = datetime.fromisoformat(text)

print(dt)
```

Output:

```text
2026-10-02 09:30:00.123456
```

Yahan:

```text
.123456
```

microseconds hain.

---

# 10. Milliseconds

Input:

```text
2026-10-02T09:30:00.123Z
```

Parse:

```python
text = "2026-10-02T09:30:00.123Z"

dt = datetime.fromisoformat(text)

print(dt)
```

Result conceptually:

```text
2026-10-02 09:30:00.123000+00:00
```

Python datetime internally microsecond precision use karta hai.

---

# 11. Offset Ke Saath Fractional Seconds

Example:

```text
2026-10-02T09:30:00.123+03:00
```

Parse:

```python
text = "2026-10-02T09:30:00.123+03:00"

dt = datetime.fromisoformat(text)

print(dt)
```

Output:

```text
2026-10-02 09:30:00.123000+03:00
```

---

# 12. `T` Ka Alternative

ISO 8601 mein date aur time ke beech separator commonly:

```text
T
```

hota hai.

Example:

```text
2026-10-02T09:30:00
```

Python `fromisoformat()` kuch compatible formats mein space separator bhi accept kar sakta hai:

```python
text = "2026-10-02 09:30:00"

dt = datetime.fromisoformat(text)

print(dt)
```

Output:

```text
2026-10-02 09:30:00
```

Lekin jab actual ISO timestamp generate/communicate karna ho, `T` wala standard representation common hai.

---

# 13. ISO 8601 Ka Main Benefit

Suppose API response mein:

```python
data = {
    "created_at": "2026-10-02T09:30:00+03:00"
}
```

String ko directly datetime mein:

```python
dt = datetime.fromisoformat(
    data["created_at"]
)
```

convert kar sakte hain.

No custom format string required.

Compare this with `strptime()`:

```python
dt = datetime.strptime(
    text,
    "%Y-%m-%dT%H:%M:%S%z"
)
```

Dono possible hain, lekin ISO input ke liye `fromisoformat()` simpler hai.

---

# 14. `strptime()` vs `fromisoformat()`

### `strptime()`

Jab aapko format explicitly define karna ho:

```python
datetime.strptime(
    text,
    "%d/%m/%Y %H:%M"
)
```

Example input:

```text
02/10/2026 09:30
```

---

### `fromisoformat()`

Jab input ISO format mein ho:

```python
datetime.fromisoformat(
    "2026-10-02T09:30:00+03:00"
)
```

Simple rule:

```text
Known custom format
        ↓
strptime()


ISO 8601 format
        ↓
fromisoformat()
```

---

# 15. Timezone-Aware Check

Parse karne ke baad:

```python
dt = datetime.fromisoformat(
    "2026-10-02T09:30:00+03:00"
)
```

Check:

```python
if dt.tzinfo is not None:
    print("Timezone-aware")
```

Output:

```text
Timezone-aware
```

Agar:

```python
dt = datetime.fromisoformat(
    "2026-10-02T09:30:00"
)
```

to timezone information nahi hai.

Ye **naive datetime** hai.

---

# 16. Important: ISO String Without Timezone

Ye:

```text
2026-10-02T09:30:00
```

timezone nahi batata.

Ye:

```text
2026-10-02T09:30:00+03:00
```

timezone offset batata hai.

Aur:

```text
2026-10-02T06:30:00Z
```

UTC batata hai.

Compare:

| ISO input                   | Timezone? |
| --------------------------- | --------- |
| `2026-10-02`                | No        |
| `2026-10-02T09:30:00`       | No        |
| `2026-10-02T09:30:00+03:00` | Yes       |
| `2026-10-02T06:30:00Z`      | Yes, UTC  |

---

# 17. Parsed Datetime Ko Riyadh Time Mein Convert Karna

Suppose API se UTC timestamp mila:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

text = "2026-10-02T06:30:00Z"

dt = datetime.fromisoformat(text)

riyadh = dt.astimezone(
    ZoneInfo("Asia/Riyadh")
)

print(riyadh)
```

Concept:

```text
UTC
06:30
 ↓
Asia/Riyadh
09:30
```

Yahan Section 5.5 ka `astimezone()` kaam aa raha hai.

---

# 18. HVAC/BMS Example

Suppose BMS API:

```python
record = {
    "equipment": "AHU-01",
    "timestamp": "2026-10-02T06:30:00Z",
    "temperature": 22.5
}
```

Timestamp parse:

```python
from datetime import datetime

dt = datetime.fromisoformat(
    record["timestamp"]
)

print(dt)
```

Ab Riyadh time:

```python
from zoneinfo import ZoneInfo

riyadh_time = dt.astimezone(
    ZoneInfo("Asia/Riyadh")
)

print(riyadh_time)
```

Ab aapke paas:

```text
Equipment
AHU-01

Temperature
22.5

Timestamp
Riyadh local time
```

Ye real-world equipment data processing mein useful hai.

---

# 19. Work Order CSV/API Example

Suppose:

```python
row = {
    "work_order": "WO-1001",
    "created_at": "2026-10-02T09:15:30+03:00"
}
```

Convert:

```python
dt = datetime.fromisoformat(
    row["created_at"]
)

print(dt)
```

Ab date/time operations kar sakte hain:

```python
print(dt.year)
print(dt.month)
print(dt.day)
print(dt.hour)
```

---

# 20. Invalid ISO String

Agar input invalid ho:

```python
text = "hello"

dt = datetime.fromisoformat(text)
```

Python exception dega:

```text
ValueError
```

Real data processing mein `try/except` useful hai:

```python
from datetime import datetime

text = "hello"

try:
    dt = datetime.fromisoformat(text)
    print(dt)

except ValueError:
    print("Invalid ISO timestamp")
```

Output:

```text
Invalid ISO timestamp
```

---

# 21. Function Bana Lena

Agar aap baar-baar ISO timestamp parse kar rahe hain:

```python
from datetime import datetime

def parse_iso_timestamp(text):
    return datetime.fromisoformat(text)
```

Use:

```python
dt = parse_iso_timestamp(
    "2026-10-02T09:30:00+03:00"
)

print(dt)
```

Ye code ko reusable bana deta hai.

---

# 22. UTC Normalization

Multiple sources se timestamps aa rahe hon to unko UTC mein normalize karna useful ho sakta hai.

```python
from datetime import datetime, timezone

text = "2026-10-02T09:30:00+03:00"

dt = datetime.fromisoformat(text)

utc = dt.astimezone(timezone.utc)

print(utc)
```

Concept:

```text
Source timestamp
      ↓
fromisoformat()
      ↓
aware datetime
      ↓
astimezone(UTC)
      ↓
common reference
```

---

# 23. ISO 8601 → Datetime → ISO 8601

Aap parsed datetime ko dobara ISO string mein convert kar sakte hain:

```python
text = "2026-10-02T09:30:00+03:00"

dt = datetime.fromisoformat(text)

new_text = dt.isoformat()

print(new_text)
```

Result:

```text
2026-10-02T09:30:00+03:00
```

Flow:

```text
ISO String
    ↓
fromisoformat()
    ↓
datetime
    ↓
isoformat()
    ↓
ISO String
```

---

# 24. `fromisoformat()` Aur External Libraries

Basic ISO 8601 parsing ke liye modern Python mein:

```python
from datetime import datetime
```

enough ho sakta hai.

Aapko har ISO timestamp ke liye `dateutil` install karne ki zaroorat nahi.

Ye Section 5.9 ka main idea hai:

> **Minimum libraries use karo jab built-in Python functionality sufficient ho.**

---

# 25. Lekin "Arbitrary" Ka Limit Hai

Ye important hai.

`fromisoformat()` ko:

> "har possible date/time string automatically parse karne wala parser"

nahi samajhna chahiye.

Example:

```text
02 Oct 2026 at 9:30 AM
```

ye normal ISO 8601 representation nahi hai.

Iske liye custom parsing ya doosri library ki zaroorat ho sakti hai.

So:

```text
ISO 8601 input
    ↓
fromisoformat()
```

best simple approach hai.

Lekin:

```text
Natural language / arbitrary human text
    ↓
different parsing approach
```

chahiye.

---

# 26. `dateutil.parser` Kab Useful Ho Sakta Hai?

Agar input highly variable ho:

```text
October 2, 2026 9:30 AM
02/10/2026 09:30
Oct 2 2026 09:30
```

to `dateutil.parser` jaise tools useful ho sakte hain.

Lekin ye **Section 5.9 ka primary approach nahi** hai.

Section 5.9 ka focus:

```text
ISO 8601
   ↓
built-in Python
   ↓
minimal dependencies
```

---

# 27. Important Examples

### Example 1 — Date

```python
datetime.fromisoformat(
    "2026-10-02"
)
```

### Example 2 — Date + Time

```python
datetime.fromisoformat(
    "2026-10-02T09:30:00"
)
```

### Example 3 — Offset

```python
datetime.fromisoformat(
    "2026-10-02T09:30:00+03:00"
)
```

### Example 4 — UTC

```python
datetime.fromisoformat(
    "2026-10-02T06:30:00Z"
)
```

### Example 5 — Fractional seconds

```python
datetime.fromisoformat(
    "2026-10-02T09:30:00.123456+03:00"
)
```

---

# 28. Quick Revision

## ISO string → datetime

```python
dt = datetime.fromisoformat(text)
```

## Date-only ISO string

```python
d = date.fromisoformat(text)
```

## UTC timestamp

```text
...Z
```

## UTC offset

```text
+03:00
```

## Check timezone

```python
dt.tzinfo
```

## Convert timezone

```python
dt.astimezone(
    ZoneInfo("Asia/Riyadh")
)
```

## Convert back to ISO

```python
dt.isoformat()
```

---

# 29. Golden Mental Model

```text
ISO 8601 String
       │
       ▼
fromisoformat()
       │
       ▼
datetime object
       │
       ├── date/time attributes
       ├── comparison
       ├── timedelta arithmetic
       ├── timezone conversion
       └── isoformat()
```

Example:

```text
"2026-10-02T06:30:00Z"
            ↓
     fromisoformat()
            ↓
2026-10-02 06:30:00+00:00
            ↓
      astimezone()
            ↓
2026-10-02 09:30:00+03:00
```

---

# Section 5.9 — Final Rule

Agar aapko **ISO 8601 timestamp** mil raha hai, pehle ye try karein:

```python
from datetime import datetime

dt = datetime.fromisoformat(text)
```

Agar timezone included hai:

```text
+03:00
```

ya:

```text
Z
```

to resulting datetime timezone-aware ho sakta hai.

Phir zaroorat ke mutabiq:

```python
dt.astimezone(...)
```

se doosre timezone mein convert kar sakte hain.

**Short formula:**

```text
ISO 8601
   ↓
fromisoformat()
   ↓
datetime
   ↓
astimezone() if needed
```
# 5.10 Get an ISO 8601 Timestamp

Is section mein hum seekhenge ke Python mein **current date/time ko ISO 8601 format** mein kaise convert karte hain.

Ye especially useful hai jab aap:

* API ke saath kaam kar rahe hon
* HVAC/BMS logs store kar rahe hon
* Work-order timestamps save kar rahe hon
* CSV/JSON data bana rahe hon
* Different systems ke darmiyan date/time exchange kar rahe hon

---

## 1. ISO 8601 kya hai?

ISO 8601 date aur time represent karne ka ek **standard format** hai.

Example:

```text
2026-10-02T09:30:00
```

Iska matlab:

```text
2026-10-02  → Date
T           → Date aur time ko separate karta hai
09:30:00    → Time
```

Agar timezone bhi included ho:

```text
2026-10-02T09:30:00+03:00
```

Yahan:

```text
+03:00
```

timezone offset hai.

---

# 2. `isoformat()` method

Python ka `datetime` object ek built-in method provide karta hai:

```python
isoformat()
```

Example:

```python
from datetime import datetime

dt = datetime(2026, 10, 2, 9, 30, 15)

print(dt.isoformat())
```

Output:

```text
2026-10-02T09:30:15
```

Yani:

```text
datetime object
      ↓
isoformat()
      ↓
ISO 8601 string
```

---

# 3. Current date/time ko ISO format mein lena

Agar current date/time chahiye:

```python
from datetime import datetime

now = datetime.now()

print(now)
print(now.isoformat())
```

Example output:

```text
2026-10-02 09:30:15.123456
2026-10-02T09:30:15.123456
```

Notice karo:

Normal representation:

```text
2026-10-02 09:30:15
```

ISO representation:

```text
2026-10-02T09:30:15
```

Difference mainly ye hai ke ISO format mein date aur time ke darmiyan `T` hota hai.

---

# 4. Timezone-aware ISO timestamp

Real-world applications mein timezone important hota hai.

Example: Riyadh time.

```python
from datetime import datetime
from zoneinfo import ZoneInfo

now = datetime.now(ZoneInfo("Asia/Riyadh"))

print(now)
print(now.isoformat())
```

Example:

```text
2026-10-02 09:30:15.123456+03:00
```

ISO format:

```text
2026-10-02T09:30:15.123456+03:00
```

Ab timestamp mein timezone bhi included hai.

---

# 5. `+03:00` ka kya matlab hai?

Saudi Arabia ka standard UTC offset:

```text
UTC+03:00
```

Isliye Riyadh ka timezone-aware timestamp kuch is tarah ho sakta hai:

```text
2026-10-02T09:30:00+03:00
```

Meaning:

```text
Date       = 2026-10-02
Time       = 09:30:00
UTC offset = +03:00
```

---

# 6. UTC ka ISO timestamp

Applications mein UTC bohat commonly use hota hai.

Python:

```python
from datetime import datetime, timezone

now = datetime.now(timezone.utc)

print(now)
print(now.isoformat())
```

Example:

```text
2026-10-02 06:30:00+00:00
2026-10-02T06:30:00+00:00
```

`+00:00` ka matlab:

```text
UTC
```

---

# 7. `Z` kya hota hai?

ISO 8601 mein UTC ko aksar:

```text
Z
```

se represent kiya jata hai.

Example:

```text
2026-10-02T06:30:00Z
```

`Z` ka matlab:

```text
UTC
```

Yani:

```text
2026-10-02T06:30:00Z
```

aur:

```text
2026-10-02T06:30:00+00:00
```

dono UTC ko represent karte hain.

Python ka `isoformat()` commonly `+00:00` produce karta hai:

```python
from datetime import datetime, timezone

dt = datetime.now(timezone.utc)

print(dt.isoformat())
```

Output:

```text
2026-10-02T06:30:00+00:00
```

Agar kisi API ko specifically `Z` chahiye ho, to:

```python
iso = dt.isoformat().replace("+00:00", "Z")

print(iso)
```

Output:

```text
2026-10-02T06:30:00Z
```

---

# 8. `isoformat()` vs `strftime()`

Dono datetime ko string mein convert kar sakte hain, lekin purpose different hai.

### `isoformat()`

Standard ISO format ke liye:

```python
dt.isoformat()
```

Example:

```text
2026-10-02T09:30:15+03:00
```

### `strftime()`

Custom format ke liye:

```python
dt.strftime("%d-%m-%Y %H:%M:%S")
```

Output:

```text
02-10-2026 09:30:15
```

### Simple rule

```text
Standard machine-friendly format
        ↓
    isoformat()

Custom display format
        ↓
    strftime()
```

---

# 9. Example: HVAC log

Suppose AHU ka temperature log save karna hai.

```python
from datetime import datetime
from zoneinfo import ZoneInfo

timestamp = datetime.now(ZoneInfo("Asia/Riyadh"))

temperature = 22.5

print("Timestamp:", timestamp.isoformat())
print("Temperature:", temperature)
```

Example:

```text
Timestamp: 2026-10-02T09:30:15.123456+03:00
Temperature: 22.5
```

Ab aapka log machine-readable hai.

Example JSON data:

```python
data = {
    "timestamp": timestamp.isoformat(),
    "temperature": temperature
}

print(data)
```

Output:

```text
{
    'timestamp': '2026-10-02T09:30:15.123456+03:00',
    'temperature': 22.5
}
```

---

# 10. Work-order example

Suppose work order create hone ka time save karna hai:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

created_at = datetime.now(ZoneInfo("Asia/Riyadh"))

work_order = {
    "work_order": "WO-10025",
    "created_at": created_at.isoformat()
}

print(work_order)
```

Example:

```text
{
    'work_order': 'WO-10025',
    'created_at': '2026-10-02T09:30:15.123456+03:00'
}
```

Ye format CSV, JSON, database aur API systems mein useful hota hai.

---

# 11. ISO timestamp ko dobara datetime mein convert karna

Section 5.9 mein humne `fromisoformat()` dekha tha.

Yahan dono ko pair ki tarah samjho:

```python
dt.isoformat()
```

datetime → string

Aur:

```python
datetime.fromisoformat(text)
```

string → datetime

Example:

```python
from datetime import datetime

dt = datetime(2026, 10, 2, 9, 30)

text = dt.isoformat()

print(text)

new_dt = datetime.fromisoformat(text)

print(new_dt)
```

Output:

```text
2026-10-02T09:30:00
2026-10-02 09:30:00
```

Mental model:

```text
datetime
   │
   │ isoformat()
   ↓
ISO 8601 string
   │
   │ fromisoformat()
   ↓
datetime
```

---

# 12. Date-only ISO format

Agar sirf `date` chahiye:

```python
from datetime import date

today = date.today()

print(today)
print(today.isoformat())
```

Example:

```text
2026-10-02
2026-10-02
```

Date ka ISO format:

```text
YYYY-MM-DD
```

---

# 13. Microseconds ko remove karna

Kabhi aapko seconds tak timestamp chahiye aur microseconds nahi.

Example:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

now = datetime.now(ZoneInfo("Asia/Riyadh"))

iso = now.replace(microsecond=0).isoformat()

print(iso)
```

Output:

```text
2026-10-02T09:30:15+03:00
```

Iska benefit ye hai ke timestamp clean aur short hota hai.

---

# 14. Naive vs timezone-aware

Ye bohat important concept hai.

### Naive datetime

```python
from datetime import datetime

dt = datetime.now()

print(dt.isoformat())
```

Example:

```text
2026-10-02T09:30:15
```

Ismein timezone information nahi hai.

### Aware datetime

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime.now(ZoneInfo("Asia/Riyadh"))

print(dt.isoformat())
```

Example:

```text
2026-10-02T09:30:15+03:00
```

Ismein timezone included hai.

Comparison:

| Type  | Example                     |
| ----- | --------------------------- |
| Naive | `2026-10-02T09:30:15`       |
| Aware | `2026-10-02T09:30:15+03:00` |
| UTC   | `2026-10-02T06:30:15+00:00` |

Real systems mein timezone-aware timestamps generally zyada useful hote hain.

---

# 15. Practical BMS/HVAC example

Suppose BMS se har 5 minutes mein AHU data aa raha hai.

```python
from datetime import datetime
from zoneinfo import ZoneInfo

timestamp = datetime.now(ZoneInfo("Asia/Riyadh"))

ahu_data = {
    "equipment_id": "AHU-01",
    "temperature": 22.4,
    "fan_status": "ON",
    "timestamp": timestamp.isoformat()
}

print(ahu_data)
```

Example:

```text
{
    'equipment_id': 'AHU-01',
    'temperature': 22.4,
    'fan_status': 'ON',
    'timestamp': '2026-10-02T09:30:15.123456+03:00'
}
```

Ab har reading ke saath exact timestamp aur timezone bhi available hai.

---

# 16. `isoformat()` ko yaad rakhne ka simple rule

```text
datetime
    ↓
.isoformat()
    ↓
ISO 8601 string
```

Example:

```python
dt.isoformat()
```

Result:

```text
2026-10-02T09:30:00+03:00
```

Aur reverse:

```python
datetime.fromisoformat(text)
```

---

# Quick Revision

### ISO 8601 datetime:

```text
2026-10-02T09:30:00+03:00
```

### Current datetime:

```python
datetime.now()
```

### Current Riyadh datetime:

```python
datetime.now(ZoneInfo("Asia/Riyadh"))
```

### Datetime → ISO string:

```python
dt.isoformat()
```

### ISO string → datetime:

```python
datetime.fromisoformat(text)
```

### UTC:

```python
datetime.now(timezone.utc)
```

### UTC ko `Z` mein:

```python
dt.isoformat().replace("+00:00", "Z")
```

### Main difference:

```text
isoformat() → standard ISO representation
strftime()  → custom formatting
```

**Sabse important concept:** Agar aap APIs, databases, BMS/HVAC logs ya work-order systems ke saath kaam kar rahe hain, to timezone-aware ISO 8601 timestamps bohat useful hote hain.
# 5.11 Parsing a String with a Short Time Zone Name into a Timezone-Aware Datetime Object

## 1. Problem kya hai?

Kabhi date/time humein is tarah string mein milta hai:

```text
2026-10-02 09:30:00 AST
```

Yahan:

```text
2026-10-02 → Date
09:30:00   → Time
AST        → Short timezone name
```

Hum chahte hain ke is string ko Python ke **timezone-aware `datetime` object** mein convert karein.

---

# 2. Short timezone name kya hota hai?

Timezone ko kabhi short name se represent kiya jata hai:

```text
UTC
EST
EDT
CST
PST
AST
```

Example:

```text
2026-10-02 09:30:00 UTC
```

Lekin yahan ek important problem hai:

**Short timezone names globally unique nahi hote.**

For example, `AST` different regions ke liye use ho sakta hai.

Isliye sirf:

```text
AST
```

dekh kar Python ko hamesha accurately pata nahi hota ke kaunsa geographic timezone hai.

---

# 3. `strptime()` directly timezone name ke saath?

Python mein `strptime()` mein `%Z` timezone name ke liye use hota hai:

```python
from datetime import datetime

text = "2026-10-02 09:30:00 UTC"

dt = datetime.strptime(text, "%Y-%m-%d %H:%M:%S %Z")

print(dt)
```

Lekin important point:

`%Z` ka behavior limited hai.

Timezone name recognize ho bhi sakta hai aur nahi bhi, aur recognized timezone ka full timezone database information automatically available hona guaranteed nahi hai.

Isliye production code mein sirf short name par depend karna risky ho sakta hai.

---

# 4. Sabse reliable approach

Agar aapko pata hai ke short name kis actual timezone ko represent karta hai, to pehle us name ko **IANA timezone name** mein map karna better approach hai.

Example:

```text
AST → America/Halifax
```

Agar source system ne explicitly define kiya hai ke `AST` ka matlab `America/Halifax` hai, to hum mapping bana sakte hain.

```python
from datetime import datetime
from zoneinfo import ZoneInfo

text = "2026-10-02 09:30:00"

dt = datetime.strptime(text, "%Y-%m-%d %H:%M:%S")

dt = dt.replace(tzinfo=ZoneInfo("America/Halifax"))

print(dt)
```

Example output:

```text
2026-10-02 09:30:00-03:00
```

Ab ye **timezone-aware datetime** hai.

---

# 5. `replace(tzinfo=...)` yahan kya kar raha hai?

Ye point Section 5.2 se yaad rakho.

```python
dt.replace(tzinfo=ZoneInfo("America/Halifax"))
```

Iska matlab:

> Is existing clock time ko specified timezone ke saath associate karo.

Agar:

```text
09:30
```

tha to clock time `09:30` hi rahega.

Timezone information add hogi.

```text
Before:
2026-10-02 09:30:00

After:
2026-10-02 09:30:00-03:00
```

---

# 6. `replace()` aur `astimezone()` ka difference

Ye bohat important hai.

### `replace()`

```python
dt.replace(tzinfo=ZoneInfo("Asia/Riyadh"))
```

Timezone information **attach** karta hai.

Clock time change nahi karta.

### `astimezone()`

```python
dt.astimezone(ZoneInfo("Asia/Riyadh"))
```

Ek existing instant ko doosre timezone mein **convert** karta hai.

Clock time change ho sakta hai.

Simple rule:

```text
replace()
    ↓
Timezone attach/replace
Clock time same

astimezone()
    ↓
Timezone conversion
Actual instant same
Clock time may change
```

---

# 7. Short name ko mapping se handle karna

Suppose external system ye data bhejta hai:

```text
2026-10-02 09:30:00 AST
```

Aur documentation kehti hai:

```text
AST = America/Halifax
```

Hum mapping bana sakte hain:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

timezone_map = {
    "AST": "America/Halifax"
}

text = "2026-10-02 09:30:00 AST"

date_part, timezone_name = text.rsplit(" ", 1)

dt = datetime.strptime(
    date_part,
    "%Y-%m-%d %H:%M:%S"
)

dt = dt.replace(
    tzinfo=ZoneInfo(timezone_map[timezone_name])
)

print(dt)
```

Example:

```text
2026-10-02 09:30:00-03:00
```

---

# 8. `rsplit()` kyun use kiya?

Hamari string:

```text
2026-10-02 09:30:00 AST
```

mein last part timezone hai.

```python
date_part, timezone_name = text.rsplit(" ", 1)
```

`1` ka matlab hai:

> Right side se sirf ek split karo.

Result:

```text
date_part
↓
2026-10-02 09:30:00

timezone_name
↓
AST
```

Phir:

```python
datetime.strptime(
    date_part,
    "%Y-%m-%d %H:%M:%S"
)
```

date/time parse karta hai.

---

# 9. Agar timezone `UTC` ho?

UTC easiest case hai.

```python
from datetime import datetime, timezone

text = "2026-10-02 06:30:00"

dt = datetime.strptime(
    text,
    "%Y-%m-%d %H:%M:%S"
)

dt = dt.replace(tzinfo=timezone.utc)

print(dt)
```

Output:

```text
2026-10-02 06:30:00+00:00
```

---

# 10. Short timezone ko offset mein convert karna

Kabhi source system short name deta hai:

```text
AST
```

Lekin aapko final data mein:

```text
-03:00
```

chahiye.

Ye automatically assume nahi karna chahiye.

Pehle source documentation se determine karo:

```text
AST
↓
Kaunsa geographic timezone?
↓
IANA timezone
↓
ZoneInfo
↓
Correct UTC offset
```

Ye approach daylight-saving changes ko bhi properly handle kar sakti hai.

---

# 11. HVAC/BMS practical example

Suppose ek external BMS log file mein timestamp aa raha hai:

```text
2026-10-02 09:30:00 AST
```

Aapka Python program isko parse karta hai.

```python
from datetime import datetime
from zoneinfo import ZoneInfo

timezone_map = {
    "AST": "America/Halifax"
}

log = "2026-10-02 09:30:00 AST"

date_text, tz_name = log.rsplit(" ", 1)

dt = datetime.strptime(
    date_text,
    "%Y-%m-%d %H:%M:%S"
)

dt = dt.replace(
    tzinfo=ZoneInfo(timezone_map[tz_name])
)

print("Parsed:", dt)
```

Ab aapke paas timezone-aware object hai.

Usko Riyadh timezone mein convert kar sakte ho:

```python
riyadh_time = dt.astimezone(
    ZoneInfo("Asia/Riyadh")
)

print(riyadh_time)
```

Yahan `astimezone()` actual moment ko Riyadh timezone mein convert karega.

---

# 12. Short timezone names ki sabse important problem

Suppose koi system bhejta hai:

```text
2026-10-02 09:30:00 CST
```

Sirf `CST` dekh kar blindly assume karna dangerous hai.

`CST` different geographic contexts mein use ho sakta hai.

Isliye production system mein preferably:

```text
America/Chicago
```

ya:

```text
Asia/Shanghai
```

jaisa full IANA timezone identifier use karna better hota hai, depending on the source's actual meaning.

---

# 13. IANA timezone kya hai?

IANA timezone identifiers examples:

```text
Asia/Riyadh
Asia/Karachi
Asia/Tokyo
Europe/London
America/New_York
America/Chicago
UTC
```

Python:

```python
from zoneinfo import ZoneInfo

riyadh = ZoneInfo("Asia/Riyadh")
```

Ye geographic timezone rules ko represent karta hai.

Short name:

```text
AST
```

ke muqable mein:

```text
Asia/Riyadh
```

zyada explicit hota hai — although, obviously, ye dono same timezone ko represent nahi karte; example sirf identifier ki form samajhne ke liye hai.

---

# 14. `ZoneInfo` use karna

Example:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

dt = datetime(
    2026,
    10,
    2,
    9,
    30,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

print(dt)
```

Output:

```text
2026-10-02 09:30:00+03:00
```

Ye directly timezone-aware datetime banata hai.

---

# 15. Better input format kya hai?

Agar aap khud koi system design kar rahe hain, to:

```text
2026-10-02 09:30:00 AST
```

ke bajaye preferably:

```text
2026-10-02T09:30:00+03:00
```

ya UTC:

```text
2026-10-02T06:30:00Z
```

use karna better hota hai.

Reason:

```text
Short timezone
      ↓
Potential ambiguity

Numeric offset / UTC
      ↓
Much clearer
```

Aur Section 5.9 mein humne isi tarah ke ISO timestamps ke liye:

```python
datetime.fromisoformat()
```

dekha tha.

---

# 16. Important distinction

Ye teen cheezen alag hain:

### 1. Short timezone name

```text
AST
EST
CST
```

Potentially ambiguous.

### 2. Numeric UTC offset

```text
+03:00
-03:00
+05:00
```

Specific offset batata hai.

### 3. IANA timezone

```text
Asia/Riyadh
America/New_York
Europe/London
```

Geographic timezone rules represent karta hai.

---

# 17. Quick workflow

Agar input ho:

```text
2026-10-02 09:30:00 AST
```

to conceptual workflow:

```text
String
   ↓
Timezone name separate karo
   ↓
AST ka actual meaning determine karo
   ↓
IANA timezone mapping
   ↓
datetime.strptime()
   ↓
timezone attach karo
   ↓
Timezone-aware datetime
   ↓
astimezone() if conversion needed
```

---

# 18. Common mistake

Ye blindly mat karo:

```python
dt = datetime.strptime(
    text,
    "%Y-%m-%d %H:%M:%S %Z"
)
```

aur assume mat karo ke har short timezone correctly resolve ho jayega.

Agar source controlled hai aur documented mapping available hai, explicit mapping zyada reliable approach hai.

---

# Final Summary

### Short timezone:

```text
AST
EST
CST
```

### `%Z`

`strptime()` mein timezone name parse karne ke liye use hota hai, lekin short names ki limitations hain.

### Better approach:

```python
ZoneInfo("America/Halifax")
```

jaisi explicit IANA timezone information use karo.

### `replace()`

```python
dt.replace(tzinfo=zone)
```

Timezone attach karta hai; clock time ko convert nahi karta.

### `astimezone()`

```python
dt.astimezone(zone)
```

Same actual moment ko doosre timezone mein convert karta hai.

### Best practical formats

```text
2026-10-02T09:30:00+03:00
```

ya:

```text
2026-10-02T06:30:00Z
```

Short timezone names ke muqable mein ye generally zyada unambiguous hain.
# 5.12 Fuzzy Datetime Parsing

## 1. Fuzzy datetime parsing kya hota hai?

Ab tak humne dekha:

```python
datetime.fromisoformat()
```

Ye tab useful hai jab input properly formatted ho:

```text
2026-10-02T09:30:00+03:00
```

Lekin real-world data hamesha itna clean nahi hota.

Example:

```text
Maintenance completed on October 2, 2026 at 9:30 AM.
```

Ya:

```text
Work order closed on 02/10/2026 09:30.
```

Ya:

```text
AHU inspection was completed yesterday at 10:30 AM.
```

In cases mein **fuzzy parsing** useful hoti hai.

Simple words mein:

> Fuzzy datetime parsing ka matlab hai text ke andar se date/time ko identify karke datetime object banana.

---

# 2. Normal parsing vs fuzzy parsing

### Normal parsing

Aapko exact format pata hai:

```text
2026-10-02 09:30:00
```

To:

```python
datetime.strptime(
    text,
    "%Y-%m-%d %H:%M:%S"
)
```

use kar sakte ho.

### Fuzzy parsing

Input human-style ho:

```text
Maintenance completed on October 2, 2026 at 9:30 AM.
```

To exact format manually define karna difficult ho sakta hai.

Is situation mein parsing library help kar sakti hai.

---

# 3. `dateutil` library

Python standard library mein ek highly flexible natural-language datetime parser nahi hai.

Commonly used external library:

```text
python-dateutil
```

Install:

```text
python -m pip install python-dateutil
```

Phir:

```python
from dateutil import parser
```

---

# 4. Simple example

```python
from dateutil import parser

text = "October 2, 2026 9:30 AM"

dt = parser.parse(text)

print(dt)
```

Output:

```text
2026-10-02 09:30:00
```

Yani:

```text
Human-readable text
        ↓
parser.parse()
        ↓
datetime object
```

---

# 5. Different formats

Same information different formats mein aa sakti hai.

Example:

```python
from dateutil import parser

text1 = "2026-10-02 09:30"
text2 = "October 2, 2026 9:30 AM"
text3 = "02 Oct 2026 09:30"
```

Teeno ko parse kiya ja sakta hai:

```python
print(parser.parse(text1))
print(parser.parse(text2))
print(parser.parse(text3))
```

Possible output:

```text
2026-10-02 09:30:00
2026-10-02 09:30:00
2026-10-02 09:30:00
```

Ye fuzzy parsing ki power hai.

---

# 6. Text ke andar datetime

Ab actual **fuzzy** example:

```python
from dateutil import parser

text = "Maintenance completed on October 2, 2026 at 9:30 AM."

dt = parser.parse(text, fuzzy=True)

print(dt)
```

`fuzzy=True` parser ko allow karta hai ke woh unnecessary words ko ignore kare.

Concept:

```text
Maintenance completed on
        ↓
     ignore

October 2, 2026 at 9:30 AM
        ↓
      parse
```

Result:

```text
2026-10-02 09:30:00
```

---

# 7. `fuzzy=True` ka purpose

Suppose string:

```text
"AHU-01 inspection completed on 02 Oct 2026 at 14:30."
```

Code:

```python
from dateutil import parser

text = "AHU-01 inspection completed on 02 Oct 2026 at 14:30."

dt = parser.parse(text, fuzzy=True)

print(dt)
```

Output:

```text
2026-10-02 14:30:00
```

Yahan:

```text
AHU-01
inspection
completed
on
at
```

jaise words important datetime information nahi hain.

Parser relevant date/time information identify karta hai.

---

# 8. Practical Work Order example

Suppose aapke CSV data mein comment column hai:

```text
"PM completed on 02 Oct 2026 at 14:30"
```

Aap date extract karna chahte ho:

```python
from dateutil import parser

comment = "PM completed on 02 Oct 2026 at 14:30"

dt = parser.parse(comment, fuzzy=True)

print(dt)
```

Output:

```text
2026-10-02 14:30:00
```

Ab aap is datetime ko:

* database mein save
* CSV mein convert
* duration calculate
* Power BI ke liye prepare

kar sakte ho.

---

# 9. HVAC example

Suppose BMS maintenance notes:

```text
note = "AHU-03 filter replaced on October 2, 2026 at 8:45 AM"
```

Code:

```python
from dateutil import parser

note = "AHU-03 filter replaced on October 2, 2026 at 8:45 AM"

dt = parser.parse(note, fuzzy=True)

print(dt)
```

Output:

```text
2026-10-02 08:45:00
```

Ab aapke paas proper `datetime` object hai.

---

# 10. `fuzzy_with_tokens=True`

Kabhi aap sirf datetime nahi, balki ye bhi dekhna chahte ho ke parser ne kaunsa text ignore kiya.

Iske liye:

```python
from dateutil import parser

text = "Maintenance completed on October 2, 2026 at 9:30 AM."

dt, ignored = parser.parse(
    text,
    fuzzy_with_tokens=True
)

print(dt)
print(ignored)
```

Possible result:

```text
2026-10-02 09:30:00
('Maintenance completed on ', ' at ', '.')
```

Yahan:

```text
dt
↓
Parsed datetime

ignored
↓
Woh text jo datetime ka part nahi tha
```

Ye debugging/data-cleaning mein useful ho sakta hai.

---

# 11. Timezone ka issue

Fuzzy parser date/time ko parse kar sakta hai, lekin timezone handling ko carefully samajhna zaroori hai.

Example:

```text
"October 2, 2026 9:30 AM +03:00"
```

```python
from dateutil import parser

text = "October 2, 2026 9:30 AM +03:00"

dt = parser.parse(text)

print(dt)
```

Result timezone-aware ho sakta hai:

```text
2026-10-02 09:30:00+03:00
```

Ab:

```python
print(dt.tzinfo)
```

timezone information show karega.

---

# 12. Timezone abbreviation ka caution

Agar text mein:

```text
AST
EST
CST
PST
```

jaisi abbreviation ho, to ambiguity ho sakti hai.

Example:

```text
"02 Oct 2026 09:30 CST"
```

`CST` multiple geographic meanings rakh sakta hai.

Isliye important systems mein preferably:

```text
+03:00
```

ya:

```text
Z
```

ya proper IANA timezone:

```text
Asia/Riyadh
```

use karna better hai.

Ye Section 5.11 ke concept se directly related hai.

---

# 13. `dayfirst=True`

Date:

```text
02/10/2026
```

ambiguous ho sakti hai.

Kya iska matlab:

```text
2 October 2026
```

hai?

Ya:

```text
10 February 2026
```

?

Parser ko direction batayi ja sakti hai:

```python
from dateutil import parser

text = "02/10/2026"

dt = parser.parse(
    text,
    dayfirst=True
)

print(dt)
```

Output:

```text
2026-10-02 00:00:00
```

Yahan `dayfirst=True` ka matlab:

```text
DD/MM/YYYY
```

interpretation prefer karo.

---

# 14. `yearfirst=True`

Agar input:

```text
2026/10/02
```

jaisa ho, `yearfirst=True` use kiya ja sakta hai:

```python
dt = parser.parse(
    "2026/10/02",
    yearfirst=True
)
```

---

# 15. Important: fuzzy parsing magic nahi hai

Fuzzy parser powerful hai, lekin har text correctly understand karega, ye assume nahi karna chahiye.

Example:

```text
"Next Friday"
```

ya:

```text
"yesterday"
```

jaise relative expressions ka behavior context/current time par depend kar sakta hai.

Production systems mein important dates ke liye input format ko controlled rakhna zyada reliable hota hai.

---

# 16. Invalid text

Agar parser ko valid date/time nahi milti:

```python
from dateutil import parser

text = "hello world"

dt = parser.parse(text)
```

To exception aa sakti hai:

```text
ParserError
```

Isliye user/external data ke saath error handling useful hai.

```python
from dateutil import parser

text = "hello world"

try:
    dt = parser.parse(text, fuzzy=True)
    print(dt)
except (ValueError, OverflowError):
    print("Date/time nahi mili")
```

---

# 17. Data cleaning example

Suppose aapke paas work-order comments hain:

```python
comments = [
    "PM completed on 02 Oct 2026 at 09:30",
    "Inspection completed on October 3, 2026 at 14:00",
    "No date available"
]
```

Aap loop se parse kar sakte ho:

```python
from dateutil import parser

for comment in comments:
    try:
        dt = parser.parse(comment, fuzzy=True)
        print(dt)
    except (ValueError, OverflowError):
        print("No valid date:", comment)
```

Possible output:

```text
2026-10-02 09:30:00
2026-10-03 14:00:00
No valid date: No date available
```

Ye data-cleaning automation mein useful technique hai.

---

# 18. `strptime()` vs fuzzy parser

| Method                    | Best use                          |
| ------------------------- | --------------------------------- |
| `strptime()`              | Exact known format                |
| `fromisoformat()`         | ISO 8601 input                    |
| `dateutil.parser.parse()` | Flexible/human-style datetime     |
| `fuzzy=True`              | Text ke andar datetime find karna |

Examples:

### Exact format

```python
datetime.strptime(
    text,
    "%Y-%m-%d %H:%M:%S"
)
```

### ISO

```python
datetime.fromisoformat(text)
```

### Flexible text

```python
parser.parse(text)
```

### Text + extra words

```python
parser.parse(text, fuzzy=True)
```

---

# 19. Real-world rule

Aapke automation/data-processing work mein ye hierarchy useful hai:

```text
Input clean aur ISO hai?
        ↓
fromisoformat()

Exact known format hai?
        ↓
strptime()

Human-style / mixed format hai?
        ↓
dateutil.parser.parse()

Datetime text ke andar embedded hai?
        ↓
parse(..., fuzzy=True)
```

---

# 20. Complete practical example

Suppose work-order note:

```python
note = "Work order WO-1025 completed on October 2, 2026 at 3:45 PM."
```

Datetime extract karna:

```python
from dateutil import parser

note = "Work order WO-1025 completed on October 2, 2026 at 3:45 PM."

dt = parser.parse(note, fuzzy=True)

print("Datetime:", dt)
print("ISO:", dt.isoformat())
```

Output:

```text
Datetime: 2026-10-02 15:45:00
ISO: 2026-10-02T15:45:00
```

Yahan humne Section 5.12 aur Section 5.10 ke concepts ko combine kiya:

```text
Human text
    ↓
fuzzy parser
    ↓
datetime
    ↓
isoformat()
    ↓
ISO string
```

---

# 21. Important caution for production data

Fuzzy parsing convenient hai, lekin automated business systems mein blindly use nahi karna chahiye.

For example:

```text
02/10/2026
```

ambiguous ho sakta hai.

Aur:

```text
10/02/2026
```

ka meaning bhi region ke hisaab se different ho sakta hai.

Agar source system controlled hai, to best approach usually ye hai:

```text
Controlled input
       ↓
Known format
       ↓
Explicit parser
       ↓
Reliable datetime
```

Fuzzy parsing ko messy/uncontrolled text ke liye use karo.

---

# Quick Revision

### Exact format:

```python
datetime.strptime(text, format)
```

### ISO 8601:

```python
datetime.fromisoformat(text)
```

### Flexible datetime:

```python
parser.parse(text)
```

### Text ke andar datetime:

```python
parser.parse(text, fuzzy=True)
```

### Extra ignored text bhi dekhna:

```python
parser.parse(
    text,
    fuzzy_with_tokens=True
)
```

### Ambiguous DD/MM/YYYY:

```python
parser.parse(
    text,
    dayfirst=True
)
```

### Error handling:

```python
try:
    dt = parser.parse(text, fuzzy=True)
except (ValueError, OverflowError):
    print("Invalid date")
```

## Sabse important concept

```text
Clean standard input
       ↓
fromisoformat()

Known exact format
       ↓
strptime()

Messy human text
       ↓
dateutil.parser

Datetime embedded inside text
       ↓
fuzzy=True
```
# 5.13 Iterate Over Dates

## 1. Iterate ka kya matlab hai?

Programming mein **iterate** ka matlab hai:

> Ek collection ya sequence ke items ko one-by-one process karna.

Example:

```python
for number in [1, 2, 3]:
    print(number)
```

Output:

```text id="f6y2k8"
1
2
3
```

Dates ke saath bhi hum isi tarah `for` loop use kar sakte hain.

---

# 2. Date ko loop mein kaise iterate karein?

Suppose humein:

```text id="q8g8gk"
1 October
2 October
3 October
4 October
5 October
```

print karna hai.

Hum `date` aur `timedelta` use karenge:

```python id="9b8p4r"
from datetime import date, timedelta

start = date(2026, 10, 1)
end = date(2026, 10, 5)

current = start

while current <= end:
    print(current)
    current += timedelta(days=1)
```

Output:

```text id="d6x8j2"
2026-10-01
2026-10-02
2026-10-03
2026-10-04
2026-10-05
```

---

# 3. Code ko step-by-step samjho

### Start date

```python id="r4m6xk"
start = date(2026, 10, 1)
```

Matlab:

```text id="3zq9m5"
1 October 2026
```

### End date

```python id="z5j1qk"
end = date(2026, 10, 5)
```

Matlab:

```text id="7x3y2p"
5 October 2026
```

### Current date

```python id="g3w8z1"
current = start
```

Initially:

```text id="3h2x7s"
current = 2026-10-01
```

### Loop

```python id="q1t9bc"
while current <= end:
```

Jab tak current date end date se chhoti ya equal hai, loop chalega.

### Print

```python id="h5j8z2"
print(current)
```

### Next date

```python id="k7p3qm"
current += timedelta(days=1)
```

Iska matlab:

```text id="r8h2fv"
current = current + 1 day
```

---

# 4. `timedelta(days=1)` ka role

Ye:

```python id="2v0y5c"
timedelta(days=1)
```

exactly **1 day ka duration** represent karta hai.

Example:

```python id="5v6x8n"
from datetime import date, timedelta

d = date(2026, 10, 1)

d = d + timedelta(days=1)

print(d)
```

Output:

```text id="q1g5cd"
2026-10-02
```

Phir:

```python id="w6t3qa"
d = d + timedelta(days=1)
```

Output:

```text id="o9v4kc"
2026-10-03
```

---

# 5. Dates ko reverse direction mein iterate karna

Agar aapko dates backward chahiye:

```text id="n8w6cz"
5 October
4 October
3 October
2 October
1 October
```

to negative `timedelta` use kar sakte hain:

```python id="j4z5x8"
from datetime import date, timedelta

current = date(2026, 10, 5)
end = date(2026, 10, 1)

while current >= end:
    print(current)
    current -= timedelta(days=1)
```

Output:

```text id="q3r8yw"
2026-10-05
2026-10-04
2026-10-03
2026-10-02
2026-10-01
```

---

# 6. Weekly dates

Har din ke bajaye agar **har 7 days** mein date chahiye:

```python id="5w2v8a"
from datetime import date, timedelta

start = date(2026, 10, 1)
end = date(2026, 10, 31)

current = start

while current <= end:
    print(current)
    current += timedelta(days=7)
```

Output:

```text id="2n7j4m"
2026-10-01
2026-10-08
2026-10-15
2026-10-22
2026-10-29
```

Yahan:

```python id="7h4m1s"
timedelta(days=7)
```

har iteration mein 7 days add kar raha hai.

---

# 7. PPM example

Suppose kisi equipment ka PPM har 7 days mein karna hai.

Start:

```text id="v7x4k2"
1 October 2026
```

End:

```text id="m9z1qa"
31 October 2026
```

Code:

```python id="q5d7w8"
from datetime import date, timedelta

start = date(2026, 10, 1)
end = date(2026, 10, 31)

current = start

while current <= end:
    print("PPM Date:", current)
    current += timedelta(days=7)
```

Output:

```text id="x6c8p1"
PPM Date: 2026-10-01
PPM Date: 2026-10-08
PPM Date: 2026-10-15
PPM Date: 2026-10-22
PPM Date: 2026-10-29
```

Ye basic scheduling logic hai.

---

# 8. Daily checklist example

Suppose October ke har din checklist generate karni hai:

```python id="v8m2r6"
from datetime import date, timedelta

start = date(2026, 10, 1)
end = date(2026, 10, 5)

current = start

while current <= end:
    print("Daily Checklist:", current)
    current += timedelta(days=1)
```

Output:

```text id="g3r9z7"
Daily Checklist: 2026-10-01
Daily Checklist: 2026-10-02
Daily Checklist: 2026-10-03
Daily Checklist: 2026-10-04
Daily Checklist: 2026-10-05
```

---

# 9. Date ke saath weekday bhi nikalna

Aap date ke saath day name bhi show kar sakte ho.

```python id="h6n1v4"
from datetime import date, timedelta

start = date(2026, 10, 1)
end = date(2026, 10, 5)

current = start

while current <= end:
    print(current, current.strftime("%A"))
    current += timedelta(days=1)
```

Output:

```text id="j5c2m8"
2026-10-01 Thursday
2026-10-02 Friday
2026-10-03 Saturday
2026-10-04 Sunday
2026-10-05 Monday
```

Yahan:

```python id="b3z9m2"
strftime("%A")
```

full weekday name deta hai.

---

# 10. Sirf weekdays iterate karna

Suppose maintenance sirf Monday–Friday hoti hai.

Hum `weekday()` use kar sakte hain.

Remember:

```text id="d2k5m9"
Monday    = 0
Tuesday   = 1
Wednesday = 2
Thursday  = 3
Friday    = 4
Saturday  = 5
Sunday    = 6
```

Example:

```python id="r5x7n3"
from datetime import date, timedelta

start = date(2026, 10, 1)
end = date(2026, 10, 7)

current = start

while current <= end:

    if current.weekday() < 5:
        print("Working day:", current)

    current += timedelta(days=1)
```

Output:

```text id="q4w8y1"
Working day: 2026-10-01
Working day: 2026-10-02
Working day: 2026-10-05
Working day: 2026-10-06
Working day: 2026-10-07
```

Saturday aur Sunday skip ho gaye.

---

# 11. Specific weekday

Suppose aapko sirf **Friday** dates chahiye.

Friday ka `weekday()`:

```text id="h8r3v2"
4
```

Code:

```python id="k3m7x9"
from datetime import date, timedelta

start = date(2026, 10, 1)
end = date(2026, 10, 31)

current = start

while current <= end:

    if current.weekday() == 4:
        print("Friday:", current)

    current += timedelta(days=1)
```

Ye month ke saare Fridays print karega.

---

# 12. Dates ki list banana

Kabhi aap dates ko print nahi, balki list mein store karna chahte ho.

```python id="y8v4q2"
from datetime import date, timedelta

start = date(2026, 10, 1)
end = date(2026, 10, 5)

dates = []

current = start

while current <= end:
    dates.append(current)
    current += timedelta(days=1)

print(dates)
```

Output:

```text id="p6x2m8"
[
    datetime.date(2026, 10, 1),
    datetime.date(2026, 10, 2),
    datetime.date(2026, 10, 3),
    datetime.date(2026, 10, 4),
    datetime.date(2026, 10, 5)
]
```

Ab `dates` ek Python `list` hai.

---

# 13. List par `for` loop

Agar list already available hai:

```python id="x3m8q6"
for d in dates:
    print(d)
```

Ye one-by-one dates process karega.

Yani:

```text id="w7n2c4"
dates list
    ↓
for loop
    ↓
date 1
date 2
date 3
...
```

---

# 14. `date` aur `datetime` dono iterate ho sakte hain

Agar date ke saath exact time bhi chahiye:

```python id="b6y2m9"
from datetime import datetime, timedelta

start = datetime(2026, 10, 1, 9, 0)
end = datetime(2026, 10, 3, 9, 0)

current = start

while current <= end:
    print(current)
    current += timedelta(days=1)
```

Output:

```text id="v4x8n1"
2026-10-01 09:00:00
2026-10-02 09:00:00
2026-10-03 09:00:00
```

Yahan har iteration mein exactly 24 hours add ho rahe hain.

---

# 15. `timedelta` se month iterate karna?

Yahan ek important limitation hai.

Ye:

```python id="z4q8m1"
timedelta(months=1)
```

**valid nahi hai**.

`timedelta` directly months support nahi karta.

Kyun?

Kyunkay:

```text id="x8m3v7"
January → February
```

aur:

```text id="l5q2c9"
February → March
```

same number of days nahi hain.

Agar calendar months ke basis par iterate karna ho, `dateutil.relativedelta` use kiya ja sakta hai.

Example:

```python id="n6w4p8"
from datetime import date
from dateutil.relativedelta import relativedelta

current = date(2026, 1, 1)

for i in range(6):
    print(current)
    current += relativedelta(months=1)
```

Output:

```text id="q2r7x5"
2026-01-01
2026-02-01
2026-03-01
2026-04-01
2026-05-01
2026-06-01
```

Yani:

```text id="w9m3k1"
timedelta
    ↓
days/weeks etc.

relativedelta
    ↓
calendar months/years
```

---

# 16. Work-order schedule example

Suppose ek work order har 14 days mein repeat hota hai:

```python id="c7x2m5"
from datetime import date, timedelta

start = date(2026, 10, 2)
end = date(2026, 12, 31)

current = start

while current <= end:
    print("Work Order:", current)
    current += timedelta(days=14)
```

Concept:

```text id="m4z8q1"
02 Oct
   ↓ +14 days
16 Oct
   ↓ +14 days
30 Oct
   ↓ +14 days
13 Nov
   ↓
...
```

Ye recurring maintenance schedule generate karne ka basic pattern hai.

---

# 17. Date range generate karne ka reusable function

Aap is logic ko function mein bhi convert kar sakte ho:

```python id="r8k3w6"
from datetime import date, timedelta

def date_range(start, end):
    current = start

    while current <= end:
        yield current
        current += timedelta(days=1)
```

Phir:

```python id="y6m2p9"
start = date(2026, 10, 1)
end = date(2026, 10, 5)

for d in date_range(start, end):
    print(d)
```

Output:

```text id="n4x7c2"
2026-10-01
2026-10-02
2026-10-03
2026-10-04
2026-10-05
```

Yahan `yield` ka concept abhi advanced lag sakta hai. Filhaal sirf itna yaad rakho ke function dates ko one-by-one provide kar raha hai.

---

# 18. Common mistake — infinite loop

Ye code dangerous hai:

```python id="f3k8q1"
current = start

while current <= end:
    print(current)
```

Problem:

`current` kabhi change hi nahi ho raha.

Isliye condition hamesha true reh sakti hai.

Correct:

```python id="w5n2m7"
while current <= end:
    print(current)
    current += timedelta(days=1)
```

Important:

> `while` loop mein progress/update zaroor hona chahiye.

---

# 19. Common mistake — end date miss karna

Agar code:

```python id="z7c4m2"
while current < end:
```

hai to `end` date include nahi hogi.

Agar end date bhi chahiye:

```python id="x9v3k6"
while current <= end:
```

use karo.

Difference:

```text id="a2m8q5"
<

end exclude


<=

end include
```

---

# 20. Practical PPM calendar

Suppose:

```text id="p6w1r9"
Equipment = AHU-01
Start = 2026-10-01
End = 2026-10-31
Frequency = 7 days
```

Code:

```python id="v3q8m2"
from datetime import date, timedelta

equipment = "AHU-01"

start = date(2026, 10, 1)
end = date(2026, 10, 31)

current = start

while current <= end:
    print(
        equipment,
        "PPM scheduled:",
        current
    )

    current += timedelta(days=7)
```

Output:

```text id="h8x4n6"
AHU-01 PPM scheduled: 2026-10-01
AHU-01 PPM scheduled: 2026-10-08
AHU-01 PPM scheduled: 2026-10-15
AHU-01 PPM scheduled: 2026-10-22
AHU-01 PPM scheduled: 2026-10-29
```

Ye exactly woh type ka logic hai jo baad mein aap **work-order automation** mein use kar sakte ho.

---

# Quick Revision

## Daily iteration

```python id="r3v8m2"
current += timedelta(days=1)
```

## Weekly iteration

```python id="j6x1q9"
current += timedelta(days=7)
```

## Backward iteration

```python id="k8m4w3"
current -= timedelta(days=1)
```

## End date include karna

```python id="p2z7n5"
while current <= end:
```

## Weekday check

```python id="y4c8m1"
current.weekday()
```

## Monday

```text id="m7x2q4"
0
```

## Friday

```text id="w5n9c3"
4
```

## Weekend

```python id="z8r3k6"
if current.weekday() >= 5:
    ...
```

## Calendar month

```python id="q6m1v8"
relativedelta(months=1)
```

---

# Chapter 5 — Complete Mental Model

Ab Chapter 5 ke major concepts ko ek flow mein dekho:

```text id="n8x4m2"
String
  ↓
strptime()
  ↓
datetime

ISO String
  ↓
fromisoformat()
  ↓
datetime

datetime
  ↓
isoformat()
  ↓
ISO String

datetime - datetime
  ↓
timedelta

datetime + timedelta
  ↓
Future datetime

datetime - timedelta
  ↓
Past datetime

Timezone
  ↓
ZoneInfo

Timezone conversion
  ↓
astimezone()

Messy human text
  ↓
dateutil.parser

Multiple dates
  ↓
while / for loop
  ↓
timedelta
```

### Chapter 5 ki sabse important cheezen:

```text id="k3v7p1"
datetime
date
time
timedelta
timezone
ZoneInfo
strptime()
strftime()
fromisoformat()
isoformat()
astimezone()
relativedelta()
parser.parse()
```

In concepts ko samajh lene ke baad aap Python mein **date/time parsing, calculation, timezone conversion aur date-based automation** ka strong foundation bana chuke ho.
