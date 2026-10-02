# Chapter 6: Date Formatting

## Section 6.1 — Time Between Two Date-Times

Is section mein hum seekhenge ke **do date-time objects ke darmiyan kitna time guzra hai** kaise calculate karte hain.

Ye concept aapke liye particularly useful hai:

* Work Order duration
* PPM completion time
* HVAC maintenance duration
* Equipment downtime
* Response time
* Start time → End time analysis

---

# 1. Basic concept

Suppose:

```text
Start = 09:00
End   = 11:30
```

To time difference:

```text
2 hours 30 minutes
```

Python mein is difference ko represent karne ke liye:

```python
timedelta
```

use hota hai.

Mental model:

```text
datetime
   -
datetime
   ↓
timedelta
```

---

# 2. Basic example

```python
from datetime import datetime

start = datetime(2026, 10, 2, 9, 0)
end = datetime(2026, 10, 2, 11, 30)

difference = end - start

print(difference)
```

Output:

```text
2:30:00
```

Yani:

```text
2 hours
30 minutes
```

---

# 3. `timedelta` kya hai?

`timedelta` ek **duration** represent karta hai.

Example:

```python
from datetime import timedelta

duration = timedelta(
    days=2,
    hours=3,
    minutes=20
)

print(duration)
```

Output:

```text
2 days, 3:20:00
```

Important distinction:

```text
datetime
↓
Ek specific date/time

timedelta
↓
Do times ke darmiyan duration
```

Example:

```text
2026-10-02 09:00
```

ek datetime hai.

```text
2 hours 30 minutes
```

ek duration/timedelta hai.

---

# 4. Difference ko variables mein store karna

```python
from datetime import datetime

start = datetime(2026, 10, 2, 9, 0)
end = datetime(2026, 10, 2, 11, 30)

duration = end - start

print("Duration:", duration)
```

Output:

```text
Duration: 2:30:00
```

---

# 5. Total seconds

Agar duration ko **total seconds** mein chahiye:

```python
seconds = duration.total_seconds()

print(seconds)
```

Output:

```text
9000.0
```

Kyun?

```text
2 hours = 7200 seconds
30 minutes = 1800 seconds

7200 + 1800 = 9000
```

---

# 6. Total minutes

Total minutes:

```python
minutes = duration.total_seconds() / 60

print(minutes)
```

Output:

```text
150.0
```

Yani:

```text
2 hours 30 minutes
=
150 minutes
```

---

# 7. Total hours

Total hours:

```python
hours = duration.total_seconds() / 3600

print(hours)
```

Output:

```text
2.5
```

Yani:

```text
2 hours 30 minutes
=
2.5 hours
```

---

# 8. Practical Work Order example

Suppose:

```text
Work Order Start:
09:15

Work Order Complete:
12:45
```

Python:

```python
from datetime import datetime

start = datetime(2026, 10, 2, 9, 15)
end = datetime(2026, 10, 2, 12, 45)

duration = end - start

print("Duration:", duration)
print("Minutes:", duration.total_seconds() / 60)
print("Hours:", duration.total_seconds() / 3600)
```

Output:

```text
Duration: 3:30:00
Minutes: 210.0
Hours: 3.5
```

---

# 9. HVAC example

Suppose AHU maintenance:

```text
Maintenance Start = 08:30
Maintenance End   = 10:00
```

```python
from datetime import datetime

start = datetime(2026, 10, 2, 8, 30)
end = datetime(2026, 10, 2, 10, 0)

duration = end - start

print("AHU maintenance duration:", duration)
```

Output:

```text
AHU maintenance duration: 1:30:00
```

Total minutes:

```python
print("Total minutes:", duration.total_seconds() / 60)
```

Output:

```text
Total minutes: 90.0
```

---

# 10. Dates ke darmiyan difference

Sirf time nahi, dates ka difference bhi calculate kar sakte hain.

```python
from datetime import date

start = date(2026, 10, 1)
end = date(2026, 10, 10)

difference = end - start

print(difference)
```

Output:

```text
9 days, 0:00:00
```

Yahan:

```text
1 Oct → 10 Oct
```

ke darmiyan **9 days** hain.

---

# 11. `.days`

Agar sirf number of days chahiye:

```python
print(difference.days)
```

Output:

```text
9
```

Example:

```python
from datetime import date

start = date(2026, 10, 1)
end = date(2026, 10, 10)

days = (end - start).days

print(days)
```

Output:

```text
9
```

---

# 12. Important: `.days` aur `total_seconds()` same nahi hain

Suppose:

```python
from datetime import timedelta

duration = timedelta(
    days=2,
    hours=5
)
```

Agar:

```python
print(duration.days)
```

Output:

```text
2
```

Lekin:

```python
print(duration.total_seconds())
```

total duration return karega:

```text
190800.0
```

Calculation:

```text
2 days = 172800 seconds
5 hours = 18000 seconds

Total = 190800 seconds
```

Isliye:

```text
.days
```

sirf **whole days component** deta hai.

Jab complete duration chahiye:

```python
total_seconds()
```

use karo.

---

# 13. Negative duration

Agar end time start time se pehle ho:

```python
from datetime import datetime

start = datetime(2026, 10, 2, 12, 0)
end = datetime(2026, 10, 2, 10, 0)

difference = end - start

print(difference)
```

Output:

```text
-1 day, 22:00:00
```

Ye initially confusing lag sakta hai.

Actually iska mathematical meaning:

```text
-2 hours
```

hai.

Check:

```python
print(difference.total_seconds() / 3600)
```

Output:

```text
-2.0
```

---

# 14. Positive duration chahiye to `abs()`

Agar direction important nahi hai aur sirf elapsed time chahiye:

```python
duration = abs(end - start)

print(duration)
```

Output:

```text
2:00:00
```

Lekin work-order systems mein negative duration ko automatically hide karna hamesha sahi nahi hota.

Negative value kabhi data-entry error indicate kar sakti hai:

```text
Start = 12:00
End   = 10:00
```

Isliye business logic ke hisaab se validate karna better hai.

---

# 15. Timezone-aware datetime ke saath

Agar dates/time different timezones mein hain, timezone-aware datetime use karna important hai.

Example:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

start = datetime(
    2026, 10, 2, 9, 0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

end = datetime(
    2026, 10, 2, 12, 0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

difference = end - start

print(difference)
```

Output:

```text
3:00:00
```

---

# 16. Different timezones ke darmiyan difference

Suppose ek event Riyadh mein:

```text
09:00 +03:00
```

aur doosra UTC mein:

```text
07:00 +00:00
```

Dono actually same instant ho sakte hain.

```python
from datetime import datetime, timezone
from zoneinfo import ZoneInfo

riyadh = datetime(
    2026, 10, 2, 9, 0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

utc = datetime(
    2026, 10, 2, 7, 0,
    tzinfo=timezone.utc
)

print(riyadh - utc)
```

Output:

```text
0:00:00
```

Kyun?

```text
Riyadh 09:00 +03:00
       ↓
UTC    06:00

```

Wait — yahan `07:00 UTC` same instant nahi hai. Is case mein difference actually 1 hour hoga.

Correct example:

```python
utc = datetime(
    2026, 10, 2, 6, 0,
    tzinfo=timezone.utc
)
```

Ab:

```text
Riyadh 09:00 +03:00
UTC    06:00 +00:00
```

Same instant hain.

Difference:

```text
0:00:00
```

**Important lesson:** timezone-aware datetimes subtract karte waqt Python actual instants ko compare karta hai.

---

# 17. Naive aur aware datetime mix mat karo

Example:

```python
from datetime import datetime
from zoneinfo import ZoneInfo

start = datetime(2026, 10, 2, 9, 0)

end = datetime(
    2026, 10, 2, 11, 0,
    tzinfo=ZoneInfo("Asia/Riyadh")
)

difference = end - start
```

Ye error de sakta hai:

```text
TypeError
```

Kyun?

```text
start
↓
naive datetime

end
↓
timezone-aware datetime
```

Python ko pata nahi ke naive datetime ko kis timezone mein interpret karna hai.

Rule:

```text
Naive + Naive
    ✓

Aware + Aware
    ✓

Naive + Aware
    ✗
```

---

# 18. Work-order SLA example

Suppose SLA hai:

```text
Maximum response time = 2 hours
```

Start:

```python
from datetime import datetime, timedelta

created = datetime(2026, 10, 2, 9, 0)
responded = datetime(2026, 10, 2, 10, 30)

duration = responded - created

sla = timedelta(hours=2)

if duration <= sla:
    print("Within SLA")
else:
    print("SLA exceeded")
```

Output:

```text
Within SLA
```

Yahan humne `timedelta` ko comparison ke liye use kiya.

---

# 19. Work-order duration ko hours mein store karna

Power BI ya database analysis ke liye kabhi duration ko numeric hours mein store karna useful hota hai.

```python
duration_hours = duration.total_seconds() / 3600
```

Example:

```text
3:30:00
```

becomes:

```text
3.5
```

Ab Power BI mein aap:

* Average duration
* Maximum duration
* Minimum duration
* Equipment-wise duration
* Technician-wise duration

jaisi analysis kar sakte ho.

---

# 20. Complete practical example

```python
from datetime import datetime

work_order = "WO-1025"

start = datetime(2026, 10, 2, 9, 15)
end = datetime(2026, 10, 2, 12, 45)

duration = end - start

hours = duration.total_seconds() / 3600
minutes = duration.total_seconds() / 60

print("Work Order:", work_order)
print("Start:", start)
print("End:", end)
print("Duration:", duration)
print("Hours:", hours)
print("Minutes:", minutes)
```

Output:

```text
Work Order: WO-1025
Start: 2026-10-02 09:15:00
End: 2026-10-02 12:45:00
Duration: 3:30:00
Hours: 3.5
Minutes: 210.0
```

---

# Quick Revision

### Do datetime objects ka difference:

```python
difference = end - start
```

Result:

```text
timedelta
```

### Total seconds:

```python
difference.total_seconds()
```

### Total minutes:

```python
difference.total_seconds() / 60
```

### Total hours:

```python
difference.total_seconds() / 3600
```

### Days:

```python
difference.days
```

### Positive duration:

```python
abs(difference)
```

### SLA comparison:

```python
if duration <= timedelta(hours=2):
    ...
```

---

# Sabse important mental model

```text
Start datetime
      +
End datetime
      ↓
     -
      ↓
   timedelta
      ↓
 ┌───────────────┐
 │ days          │
 │ seconds       │
 │ microseconds  │
 └───────────────┘
      ↓
total_seconds()
      ↓
Minutes / Hours
```

Aur yaad rakho:

```text
datetime - datetime
        ↓
    timedelta
```

`timedelta` **date/time nahi**, balki **duration** hai.
# Section 6.2 — `datetime` Object ko String mein Convert Karna

## 1. `strftime()` kya hai?

`strftime()` ka full concept hai:

**string format time**

Is method se hum `datetime` object ko apni required format ki **string** mein convert karte hain.

Basic syntax:

```python
datetime_object.strftime("format")
```

Example:

```python
from datetime import datetime

dt = datetime(2026, 10, 2, 9, 30, 15)

text = dt.strftime("%Y-%m-%d")

print(text)
```

Output:

```text
2026-10-02
```

Yahan:

```text
datetime object
      ↓
   strftime()
      ↓
    string
```

---

# 2. Basic example

```python
from datetime import datetime

dt = datetime(2026, 10, 2, 9, 30, 15)

print(dt.strftime("%Y-%m-%d"))
print(dt.strftime("%d-%m-%Y"))
print(dt.strftime("%m/%d/%Y"))
```

Output:

```text
2026-10-02
02-10-2026
10/02/2026
```

Same `datetime` hai, lekin output format different hai.

---

# 3. Format codes

`strftime()` mein `%` ke saath special codes use hote hain.

Sabse important:

| Code | Meaning       | Example   |
| ---- | ------------- | --------- |
| `%Y` | 4-digit year  | `2026`    |
| `%y` | 2-digit year  | `26`      |
| `%m` | Month number  | `10`      |
| `%d` | Day           | `02`      |
| `%H` | Hour, 24-hour | `09`      |
| `%I` | Hour, 12-hour | `09`      |
| `%M` | Minutes       | `30`      |
| `%S` | Seconds       | `15`      |
| `%p` | AM/PM         | `AM`      |
| `%A` | Full weekday  | `Friday`  |
| `%a` | Short weekday | `Fri`     |
| `%B` | Full month    | `October` |
| `%b` | Short month   | `Oct`     |

---

# 4. Date format

Agar sirf date chahiye:

```python
from datetime import datetime

dt = datetime(2026, 10, 2, 9, 30, 15)

print(dt.strftime("%Y-%m-%d"))
```

Output:

```text
2026-10-02
```

Breakdown:

```text
%Y → 2026
%m → 10
%d → 02
```

Format:

```text
%Y-%m-%d
 ↓    ↓  ↓
Year Month Day
```

---

# 5. Different date formats

### `YYYY-MM-DD`

```python
dt.strftime("%Y-%m-%d")
```

Result:

```text
2026-10-02
```

### `DD-MM-YYYY`

```python
dt.strftime("%d-%m-%Y")
```

Result:

```text
02-10-2026
```

### `DD/MM/YYYY`

```python
dt.strftime("%d/%m/%Y")
```

Result:

```text
02/10/2026
```

### `MM/DD/YYYY`

```python
dt.strftime("%m/%d/%Y")
```

Result:

```text
10/02/2026
```

Yahan dhyan rakho:

```text
DD/MM/YYYY
```

aur:

```text
MM/DD/YYYY
```

different hain.

---

# 6. Time format

Suppose:

```python
dt = datetime(2026, 10, 2, 9, 30, 15)
```

### 24-hour format

```python
print(dt.strftime("%H:%M:%S"))
```

Output:

```text
09:30:15
```

Breakdown:

```text
%H → 09
%M → 30
%S → 15
```

---

# 7. 12-hour format

Agar AM/PM format chahiye:

```python
print(dt.strftime("%I:%M:%S %p"))
```

Output:

```text
09:30:15 AM
```

Yahan:

```text
%I → 12-hour clock
%M → minutes
%S → seconds
%p → AM/PM
```

---

# 8. Full date + time

```python
print(
    dt.strftime("%Y-%m-%d %H:%M:%S")
)
```

Output:

```text
2026-10-02 09:30:15
```

Ye common format hai.

---

# 9. Human-readable format

Agar user-friendly format chahiye:

```python
print(
    dt.strftime("%d %B %Y, %I:%M %p")
)
```

Output:

```text
02 October 2026, 09:30 AM
```

Yahan:

```text
%d      → 02
%B      → October
%Y      → 2026
%I      → 09
%M      → 30
%p      → AM
```

---

# 10. Short month name

`%B` full month name deta hai:

```python
dt.strftime("%B")
```

Output:

```text
October
```

`%b` short month deta hai:

```python
dt.strftime("%b")
```

Output:

```text
Oct
```

Example:

```python
print(dt.strftime("%d %b %Y"))
```

Output:

```text
02 Oct 2026
```

---

# 11. Weekday name

Full weekday:

```python
print(dt.strftime("%A"))
```

Output:

```text
Friday
```

Short weekday:

```python
print(dt.strftime("%a"))
```

Output:

```text
Fri
```

Complete example:

```python
print(dt.strftime("%A, %d %B %Y"))
```

Output:

```text
Friday, 02 October 2026
```

---

# 12. Multiple formats ek saath

Ek hi `datetime` ko different formats mein convert kar sakte ho:

```python
from datetime import datetime

dt = datetime(2026, 10, 2, 9, 30, 15)

print(dt.strftime("%Y-%m-%d"))
print(dt.strftime("%d/%m/%Y"))
print(dt.strftime("%H:%M:%S"))
print(dt.strftime("%d %B %Y"))
print(dt.strftime("%A, %d %B %Y at %I:%M %p"))
```

Output:

```text
2026-10-02
02/10/2026
09:30:15
02 October 2026
Friday, 02 October 2026 at 09:30 AM
```

---

# 13. Apna text bhi add kar sakte ho

Format string mein normal text bhi likh sakte ho.

```python
print(
    dt.strftime("Date: %d-%m-%Y")
)
```

Output:

```text
Date: 02-10-2026
```

Another example:

```python
print(
    dt.strftime("Maintenance Date: %d %B %Y")
)
```

Output:

```text
Maintenance Date: 02 October 2026
```

---

# 14. HVAC example

Suppose AHU maintenance ka timestamp hai:

```python
from datetime import datetime

maintenance_time = datetime(
    2026, 10, 2, 9, 30, 15
)

print(
    maintenance_time.strftime(
        "%d-%m-%Y %H:%M:%S"
    )
)
```

Output:

```text
02-10-2026 09:30:15
```

Agar report mein readable format chahiye:

```python
print(
    maintenance_time.strftime(
        "%d %B %Y at %I:%M %p"
    )
)
```

Output:

```text
02 October 2026 at 09:30 AM
```

---

# 15. Work Order example

```python
from datetime import datetime

completed_at = datetime(
    2026, 10, 2, 14, 45, 30
)

work_order = "WO-1025"

print(
    work_order,
    "completed on",
    completed_at.strftime("%d-%m-%Y %H:%M")
)
```

Output:

```text
WO-1025 completed on 02-10-2026 14:45
```

---

# 16. `strftime()` aur `strptime()` ka difference

Ye dono names similar hain, isliye confusion common hai.

### `strftime()`

**datetime → string**

```python
dt.strftime("%Y-%m-%d")
```

Example:

```text
datetime
   ↓
strftime()
   ↓
"2026-10-02"
```

### `strptime()`

**string → datetime**

```python
datetime.strptime(
    "2026-10-02",
    "%Y-%m-%d"
)
```

Example:

```text
"2026-10-02"
      ↓
 strptime()
      ↓
 datetime
```

Simple trick:

```text
strftime
   ↓
f = format

strptime
   ↓
p = parse
```

Aur practical memory:

```text
strftime()  → OUT
strptime()  → IN
```

---

# 17. `strftime()` vs `isoformat()`

Dono datetime ko string bana sakte hain.

### `isoformat()`

Standard ISO 8601 format:

```python
dt.isoformat()
```

Result:

```text
2026-10-02T09:30:15
```

### `strftime()`

Aap format khud define karte ho:

```python
dt.strftime("%d/%m/%Y %H:%M")
```

Result:

```text
02/10/2026 09:30
```

Rule:

```text
Standard ISO format
      ↓
isoformat()

Custom format
      ↓
strftime()
```

---

# 18. Timezone-aware datetime

Agar datetime timezone-aware hai:

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
```

Normal `strftime()`:

```python
print(
    dt.strftime("%Y-%m-%d %H:%M:%S")
)
```

Output:

```text
2026-10-02 09:30:00
```

Notice karo ke timezone output mein automatically show nahi hua.

Timezone/offset include karne ke liye `%z` use kar sakte ho:

```python
print(
    dt.strftime("%Y-%m-%d %H:%M:%S %z")
)
```

Output:

```text
2026-10-02 09:30:00 +0300
```

Timezone abbreviation ke liye `%Z`:

```python
print(
    dt.strftime("%Y-%m-%d %H:%M:%S %Z")
)
```

Output environment/timezone implementation ke mutabiq vary kar sakta hai.

---

# 19. `%z` aur `%Z`

Ye dono important hain:

```text
%z → UTC offset
%Z → timezone name/abbreviation
```

Example:

```text
+0300
```

versus potentially:

```text
AST
```

Lekin `%Z` ke short timezone names ambiguous ho sakte hain. Section 5.11 mein humne ye issue dekha tha.

---

# 20. CSV/report example

Suppose aapko CSV mein date is format mein chahiye:

```text
02-10-2026 09:30
```

Code:

```python
formatted = dt.strftime("%d-%m-%Y %H:%M")

print(formatted)
```

Ab `formatted` ek **string** hai.

Check:

```python
print(type(formatted))
```

Output:

```text
<class 'str'>
```

Important:

```text
dt
↓
datetime object

dt.strftime(...)
↓
string
```

---

# 21. Datetime object change nahi hota

`strftime()` original datetime ko modify nahi karta.

```python
from datetime import datetime

dt = datetime(2026, 10, 2, 9, 30)

text = dt.strftime("%d/%m/%Y")

print(dt)
print(text)
```

Output:

```text
2026-10-02 09:30:00
02/10/2026
```

Original `dt` abhi bhi datetime object hai.

```python
print(type(dt))
```

Output:

```text
<class 'datetime.datetime'>
```

Aur:

```python
print(type(text))
```

Output:

```text
<class 'str'>
```

---

# 22. Common format codes yaad karo

Sab codes ek saath yaad karne ki zaroorat nahi.

Pehle ye important codes yaad karo:

```text
%Y → 2026
%m → 10
%d → 02

%H → 24-hour
%I → 12-hour
%M → minute
%S → second
%p → AM/PM
```

Phir:

```text
%A → Friday
%a → Fri
%B → October
%b → Oct
```

Aur timezone:

```text
%z → +0300
%Z → timezone name
```

---

# 23. Most useful examples

### Database-style

```python
dt.strftime("%Y-%m-%d %H:%M:%S")
```

Result:

```text
2026-10-02 09:30:15
```

### Saudi-style day/month format

```python
dt.strftime("%d/%m/%Y")
```

Result:

```text
02/10/2026
```

### Human-readable

```python
dt.strftime("%d %B %Y")
```

Result:

```text
02 October 2026
```

### 12-hour clock

```python
dt.strftime("%I:%M %p")
```

Result:

```text
09:30 AM
```

### Full report format

```python
dt.strftime("%A, %d %B %Y at %I:%M %p")
```

Result:

```text
Friday, 02 October 2026 at 09:30 AM
```

---

# 24. Important mental model

```text
datetime object
      │
      │ strftime("format")
      ↓
    string
```

Example:

```python
dt.strftime("%d-%m-%Y")
```

Means:

```text
datetime
   ↓
Day-Month-Year
   ↓
"02-10-2026"
```

Aur reverse:

```text
"02-10-2026"
      ↓
strptime()
      ↓
datetime
```

---

# Quick Revision

| Task          | Code |
| ------------- | ---- |
| Year          | `%Y` |
| Month         | `%m` |
| Day           | `%d` |
| 24-hour       | `%H` |
| 12-hour       | `%I` |
| Minute        | `%M` |
| Second        | `%S` |
| AM/PM         | `%p` |
| Full weekday  | `%A` |
| Short weekday | `%a` |
| Full month    | `%B` |
| Short month   | `%b` |
| UTC offset    | `%z` |
| Timezone name | `%Z` |

### Most important:

```python
dt.strftime("%Y-%m-%d")
```

**datetime → string**

```python
datetime.strptime(text, "%Y-%m-%d")
```

**string → datetime**

```text
strftime = OUT
strptime  = IN
```

Aur:

```python
dt.isoformat()
```

**standard ISO 8601 output** ke liye useful hai, jabke `strftime()` **custom formatting** ke liye use hota hai.
# Section 6.3 — Parsing String to `datetime` Object

## 1. Parsing kya hota hai?

**Parsing** ka matlab hai kisi `string` ko read karke usko meaningful Python object mein convert karna.

Date/time ke case mein:

```text
String
   ↓
strptime()
   ↓
datetime object
```

Example:

```python
from datetime import datetime

text = "2026-10-02 09:30:15"

dt = datetime.strptime(
    text,
    "%Y-%m-%d %H:%M:%S"
)

print(dt)
```

Output:

```text
2026-10-02 09:30:15
```

Ab `dt` ek `datetime` object hai.

---

# 2. `strptime()` kya hai?

`strptime()` ka use:

> **String ko specified format ke according `datetime` object mein convert karna.**

Syntax:

```python
datetime.strptime(string, format)
```

Example:

```python
dt = datetime.strptime(
    "2026-10-02",
    "%Y-%m-%d"
)
```

Yahan:

```text
"2026-10-02"
      ↓
  strptime()
      ↓
datetime(2026, 10, 2)
```

---

# 3. Sabse important baat

`strptime()` ko **format exactly pata hona chahiye**.

Example:

```python
text = "2026-10-02"
```

Iska format:

```python
"%Y-%m-%d"
```

So:

```python
from datetime import datetime

dt = datetime.strptime(
    text,
    "%Y-%m-%d"
)

print(dt)
```

Output:

```text
2026-10-02 00:00:00
```

Notice karo time nahi diya gaya, isliye time:

```text
00:00:00
```

ho gaya.

---

# 4. Different date formats parse karna

### Format: `YYYY-MM-DD`

```python
text = "2026-10-02"

dt = datetime.strptime(
    text,
    "%Y-%m-%d"
)

print(dt)
```

Output:

```text
2026-10-02 00:00:00
```

---

### Format: `DD-MM-YYYY`

```python
text = "02-10-2026"

dt = datetime.strptime(
    text,
    "%d-%m-%Y"
)

print(dt)
```

Output:

```text
2026-10-02 00:00:00
```

---

### Format: `DD/MM/YYYY`

```python
text = "02/10/2026"

dt = datetime.strptime(
    text,
    "%d/%m/%Y"
)

print(dt)
```

Output:

```text
2026-10-02 00:00:00
```

---

# 5. Date + Time parse karna

Suppose string:

```text
2026-10-02 09:30:15
```

Format:

```text
%Y-%m-%d %H:%M:%S
```

Code:

```python
from datetime import datetime

text = "2026-10-02 09:30:15"

dt = datetime.strptime(
    text,
    "%Y-%m-%d %H:%M:%S"
)

print(dt)
```

Output:

```text
2026-10-02 09:30:15
```

Breakdown:

```text
2026 → %Y
10   → %m
02   → %d
09   → %H
30   → %M
15   → %S
```

Space bhi format ka part hai:

```text
"%Y-%m-%d %H:%M:%S"
             ↑
           space
```

---

# 6. 12-hour time ke saath parsing

Agar input hai:

```text
02-10-2026 09:30 PM
```

To format:

```text
%d-%m-%Y %I:%M %p
```

Code:

```python
from datetime import datetime

text = "02-10-2026 09:30 PM"

dt = datetime.strptime(
    text,
    "%d-%m-%Y %I:%M %p"
)

print(dt)
```

Output:

```text
2026-10-02 21:30:00
```

Yahan:

```text
%I → 12-hour clock
%M → minute
%p → AM/PM
```

---

# 7. Important format codes

Parsing ke liye ye codes important hain:

| Code | Meaning      | Input Example |
| ---- | ------------ | ------------- |
| `%Y` | 4-digit year | `2026`        |
| `%y` | 2-digit year | `26`          |
| `%m` | Month        | `10`          |
| `%d` | Day          | `02`          |
| `%H` | 24-hour      | `21`          |
| `%I` | 12-hour      | `09`          |
| `%M` | Minute       | `30`          |
| `%S` | Second       | `15`          |
| `%p` | AM/PM        | `PM`          |
| `%A` | Full weekday | `Friday`      |
| `%B` | Full month   | `October`     |

---

# 8. String aur datetime ka difference

Initially:

```python
text = "2026-10-02"
```

`text` ek string hai:

```python
print(type(text))
```

Output:

```text
<class 'str'>
```

Ab parse karo:

```python
dt = datetime.strptime(
    text,
    "%Y-%m-%d"
)
```

Ab:

```python
print(type(dt))
```

Output:

```text
<class 'datetime.datetime'>
```

Yani:

```text
"2026-10-02"
      ↓
     str
      ↓
  strptime()
      ↓
 datetime
```

---

# 9. Parsing ke baad datetime operations

Ye iska major benefit hai.

Suppose:

```python
text = "2026-10-02 09:30:00"

dt = datetime.strptime(
    text,
    "%Y-%m-%d %H:%M:%S"
)
```

Ab aap:

```python
print(dt.year)
print(dt.month)
print(dt.day)
```

kar sakte ho.

Output:

```text
2026
10
2
```

Aap calculation bhi kar sakte ho:

```python
from datetime import timedelta

future = dt + timedelta(hours=2)

print(future)
```

Output:

```text
2026-10-02 11:30:00
```

---

# 10. Parsing aur formatting ka relation

Ye dono opposite direction mein kaam karte hain.

### String → datetime

```python
datetime.strptime()
```

### datetime → string

```python
dt.strftime()
```

Diagram:

```text
        strptime()
String ─────────────→ datetime
                         │
                         │ strftime()
                         ↓
                       String
```

Example:

```python
text = "02-10-2026"

dt = datetime.strptime(
    text,
    "%d-%m-%Y"
)

new_text = dt.strftime(
    "%Y/%m/%d"
)

print(new_text)
```

Output:

```text
2026/10/02
```

Yani humne date ka format change kar diya.

---

# 11. Invalid format se error

Suppose:

```python
text = "2026-10-02"

dt = datetime.strptime(
    text,
    "%d-%m-%Y"
)
```

Yahan problem hai.

Input:

```text
2026-10-02
```

Actually format:

```text
YYYY-MM-DD
```

hai.

Lekin humne:

```text
DD-MM-YYYY
```

bataya.

Python `ValueError` dega.

Isliye format ko input string ke saath match karna zaroori hai.

---

# 12. Invalid date

Ye bhi error dega:

```python
text = "2026-02-30"

dt = datetime.strptime(
    text,
    "%Y-%m-%d"
)
```

February 30 valid date nahi hai.

Python `ValueError` raise karega.

---

# 13. `try/except` se error handle karna

Real-world data mein invalid dates aa sakti hain.

Isliye:

```python
from datetime import datetime

text = "2026-02-30"

try:
    dt = datetime.strptime(
        text,
        "%Y-%m-%d"
    )
    print(dt)

except ValueError:
    print("Invalid date format or date")
```

Output:

```text
Invalid date format or date
```

Ye CSV, Excel, API aur work-order data cleaning mein useful hai.

---

# 14. Multiple date formats ka example

Suppose different records mein dates different formats mein aa rahi hain:

```text
2026-10-02
02-10-2026
02/10/2026
```

Har format ke liye correct format string chahiye:

```python
from datetime import datetime

a = datetime.strptime(
    "2026-10-02",
    "%Y-%m-%d"
)

b = datetime.strptime(
    "02-10-2026",
    "%d-%m-%Y"
)

c = datetime.strptime(
    "02/10/2026",
    "%d/%m/%Y"
)

print(a)
print(b)
print(c)
```

Output:

```text
2026-10-02 00:00:00
2026-10-02 00:00:00
2026-10-02 00:00:00
```

Ab teeno Python ke andar same `datetime` representation hain.

---

# 15. Practical Work Order example

Suppose work-order CSV mein:

```text
Work Order Number,Completed Date
WO-1001,02-10-2026 09:30
```

Date string:

```python
completed_text = "02-10-2026 09:30"
```

Parse:

```python
from datetime import datetime

completed_at = datetime.strptime(
    completed_text,
    "%d-%m-%Y %H:%M"
)

print(completed_at)
```

Output:

```text
2026-10-02 09:30:00
```

Ab duration calculate kar sakte ho:

```python
started_at = datetime.strptime(
    "02-10-2026 08:00",
    "%d-%m-%Y %H:%M"
)

duration = completed_at - started_at

print(duration)
```

Output:

```text
1:30:00
```

Yani:

```text
CSV string
    ↓
strptime()
    ↓
datetime
    ↓
datetime - datetime
    ↓
timedelta
```

---

# 16. Practical HVAC example

Suppose HVAC log mein timestamp:

```text
02/10/2026 14:45:30
```

Parse:

```python
from datetime import datetime

log_text = "02/10/2026 14:45:30"

log_time = datetime.strptime(
    log_text,
    "%d/%m/%Y %H:%M:%S"
)

print(log_time)
```

Output:

```text
2026-10-02 14:45:30
```

Ab aap check kar sakte ho:

```python
print(log_time.hour)
```

Output:

```text
14
```

Ya date ko dobara different format mein output kar sakte ho:

```python
print(
    log_time.strftime("%Y-%m-%d %H:%M")
)
```

Output:

```text
2026-10-02 14:45
```

---

# 17. `strptime()` timezone automatically assume nahi karta

Ye important point hai.

Agar string:

```text
2026-10-02 09:30:00
```

hai, to:

```python
dt = datetime.strptime(
    text,
    "%Y-%m-%d %H:%M:%S"
)
```

se normally **naive datetime** milega.

Check:

```python
print(dt.tzinfo)
```

Output:

```text
None
```

Agar input mein timezone/offset included ho, to timezone handling ke liye appropriate format ya `fromisoformat()`/`ZoneInfo` approach use karni hoti hai.

---

# 18. `strptime()` vs `fromisoformat()`

Dono string ko datetime mein convert kar sakte hain.

### `strptime()`

Jab format aapko explicitly define karna ho:

```python
datetime.strptime(
    "02-10-2026 09:30",
    "%d-%m-%Y %H:%M"
)
```

### `fromisoformat()`

Jab input ISO 8601 format mein ho:

```python
datetime.fromisoformat(
    "2026-10-02T09:30:00+03:00"
)
```

Simple rule:

```text
Custom known format
       ↓
   strptime()

ISO 8601 input
       ↓
fromisoformat()
```

---

# 19. Parsing ka complete workflow

Real data ke saath generally:

```text
Raw string
    ↓
Check format
    ↓
strptime()
    ↓
datetime object
    ↓
Validation / calculation
    ↓
strftime()
    ↓
Output string
```

Example:

```python
from datetime import datetime, timedelta

text = "02-10-2026 09:30"

# String → datetime
dt = datetime.strptime(
    text,
    "%d-%m-%Y %H:%M"
)

# Calculation
due_time = dt + timedelta(hours=2)

# datetime → string
result = due_time.strftime(
    "%d-%m-%Y %H:%M"
)

print(result)
```

Output:

```text
02-10-2026 11:30
```

---

# 20. Important memory trick

### `strptime`

**Parse Time**

```text
String → datetime
```

### `strftime`

**Format Time**

```text
datetime → String
```

Yaad rakho:

```text
strptime  → INPUT
strftime  → OUTPUT
```

---

# Quick Revision

```python
from datetime import datetime
```

### String → datetime

```python
dt = datetime.strptime(
    "02-10-2026 09:30",
    "%d-%m-%Y %H:%M"
)
```

### datetime → string

```python
text = dt.strftime(
    "%Y-%m-%d %H:%M"
)
```

### Error handling

```python
try:
    dt = datetime.strptime(
        text,
        "%Y-%m-%d"
    )
except ValueError:
    print("Invalid date")
```

### Main format codes

```text
%Y → 2026
%m → 10
%d → 02
%H → 24-hour
%I → 12-hour
%M → minute
%S → second
%p → AM/PM
```

### Final mental model

```text
"02-10-2026 09:30"
          │
          │ strptime()
          ↓
2026-10-02 09:30:00
          │
          │ strftime()
          ↓
"2026/10/02 09:30"
```
