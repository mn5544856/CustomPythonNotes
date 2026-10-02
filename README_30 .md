# Chapter 30: Files & Folders I/O

Python mein **Files & Folders I/O** ka matlab hai Python program se:

* file read karna
* file write karna
* file append karna
* file/folder ka path check karna
* folders ke andar files find karna
* directories copy karna
* files copy karna
* file mein text replace karna
* file empty hai ya nahi check karna

Ye concepts automation aur data-processing scripts mein bohat important hain.

Example:

```text
Work Orders
    │
    ├── WO1001
    │     ├── report.txt
    │     └── checklist.csv
    │
    ├── WO1002
    │     └── report.txt
    │
    └── WO1003
          └── checklist.csv
```

Python se hum is poore structure ko manage kar sakte hain.

---

# Section 30.1: File Modes

File open karte waqt Python ko batana hota hai ke file ko kis purpose ke liye open karna hai.

Basic syntax:

```python
open("filename", "mode")
```

Common modes:

| Mode  | Meaning         |
| ----- | --------------- |
| `"r"` | Read            |
| `"w"` | Write           |
| `"a"` | Append          |
| `"x"` | Create new file |
| `"b"` | Binary mode     |
| `"t"` | Text mode       |
| `"+"` | Read + Write    |

---

## `"r"` — Read

```python
with open("data.txt", "r") as file:
    data = file.read()

print(data)
```

`"r"` ka matlab:

> Existing file ko read karna.

Agar file exist nahi karti:

```text
FileNotFoundError
```

aayega.

---

## `"w"` — Write

```python
with open("data.txt", "w") as file:
    file.write("Hello")
```

Agar file exist nahi karti, Python create kar dega.

Agar file already exist karti hai, `"w"` **existing content ko overwrite** kar deta hai.

Example pehle file:

```text
Hello
World
```

Code:

```python
with open("data.txt", "w") as file:
    file.write("New data")
```

Ab file:

```text
New data
```

ho jayegi.

### Important

`"w"` use karte waqt careful rahein kyun ke old content overwrite ho sakta hai.

---

## `"a"` — Append

Append ka matlab:

> Existing content ke end mein new content add karna.

```python
with open("data.txt", "a") as file:
    file.write("New line\n")
```

Agar file:

```text
Line 1
Line 2
```

thi, to ab:

```text
Line 1
Line 2
New line
```

---

## `"x"` — Create

```python
with open("new_file.txt", "x") as file:
    file.write("Hello")
```

`"x"` new file create karta hai.

Agar file already exist karti ho:

```text
FileExistsError
```

aayega.

Ye useful hai jab aap accidentally existing file overwrite nahi karna chahte.

---

## `"b"` — Binary

Binary files ke liye:

```python
with open("image.jpg", "rb") as file:
    data = file.read()
```

`rb`:

```text
r = read
b = binary
```

Binary files:

* images
* PDFs
* ZIP files
* executable files

etc. ho sakti hain.

---

## `"t"` — Text

Text mode:

```python
with open("data.txt", "rt") as file:
    data = file.read()
```

Usually `"t"` explicitly likhne ki zaroorat nahi hoti.

```python
open("data.txt", "r")
```

default text mode use karta hai.

---

## `"r+"` — Read and Write

```python
with open("data.txt", "r+") as file:
    data = file.read()
```

`r+` existing file ko read aur write dono ke liye open karta hai.

File ka exist karna zaroori hai.

---

## `"w+"` — Write and Read

```python
with open("data.txt", "w+") as file:
    file.write("Hello")
    file.seek(0)
    print(file.read())
```

`w+` file ko overwrite/create karta hai aur read/write dono allow karta hai.

---

# Section 30.2: Reading a File Line-by-Line

Large file ke liye poori file memory mein load karna hamesha necessary nahi.

Best pattern:

```python
with open("equipment.txt", "r") as file:
    for line in file:
        print(line.strip())
```

Suppose:

```text
AHU-001
AHU-002
VAV-001
VAV-002
```

Output:

```text
AHU-001
AHU-002
VAV-001
VAV-002
```

---

## `strip()` kyun?

File mein line normally newline ke saath aati hai:

```python
"AHU-001\n"
```

`strip()`:

```python
line.strip()
```

banata hai:

```python
"AHU-001"
```

---

## `readline()`

Sirf ek line:

```python
with open("equipment.txt") as file:
    line = file.readline()
    print(line)
```

Agar dobara:

```python
line = file.readline()
```

karoge to next line milegi.

---

## `readlines()`

```python
with open("equipment.txt") as file:
    lines = file.readlines()

print(lines)
```

Ye list return karta hai:

```python
[
    "AHU-001\n",
    "AHU-002\n",
    "VAV-001\n"
]
```

Large files ke liye `readlines()` memory consume kar sakta hai.

Line-by-line iteration zyada suitable hoti hai.

---

# Section 30.3: Iterate Files Recursively

Ab maan lein folder structure:

```text
WorkOrders/
    WO1001/
        report.txt
        checklist.csv

    WO1002/
        report.txt

    WO1003/
        photos/
            image1.jpg
```

Aapko har subfolder ke andar recursively files find karni hain.

Modern Python mein `pathlib.Path.rglob()` useful hai.

```python
from pathlib import Path

base = Path("WorkOrders")

for file in base.rglob("*"):
    if file.is_file():
        print(file)
```

Output:

```text
WorkOrders/WO1001/report.txt
WorkOrders/WO1001/checklist.csv
WorkOrders/WO1002/report.txt
WorkOrders/WO1003/photos/image1.jpg
```

`rglob()` recursively subdirectories mein search karta hai.

---

## Sirf `.csv` files

```python
from pathlib import Path

base = Path("WorkOrders")

for file in base.rglob("*.csv"):
    print(file)
```

Ye sirf CSV files dhoondega.

---

## `os.walk()`

Recursive traversal ke liye traditional approach:

```python
import os

for root, directories, files in os.walk("WorkOrders"):
    for filename in files:
        print(os.path.join(root, filename))
```

Modern Python mein `pathlib` generally cleaner lagta hai.

---

# Section 30.4: Getting the Full Contents of a File

Complete file read karne ka simple method:

```python
with open("data.txt", "r") as file:
    content = file.read()

print(content)
```

`read()`:

> Current file position se remaining content read karta hai.

---

## Character limit ke saath

```python
with open("data.txt") as file:
    content = file.read(100)
```

Yahan maximum approximately 100 characters read honge.

---

## `Path.read_text()`

`pathlib` se aur simple:

```python
from pathlib import Path

file = Path("data.txt")

content = file.read_text()

print(content)
```

Encoding explicitly specify karna better practice ho sakta hai:

```python
content = file.read_text(encoding="utf-8")
```

---

# Section 30.5: Writing to a File

## Basic `write()`

```python
with open("data.txt", "w") as file:
    file.write("Hello World")
```

File:

```text
Hello World
```

---

## Newline ke saath

`write()` automatically newline add nahi karta.

Isliye:

```python
with open("data.txt", "w") as file:
    file.write("Line 1\n")
    file.write("Line 2\n")
```

File:

```text
Line 1
Line 2
```

---

## Multiple lines

```python
lines = [
    "AHU-001\n",
    "AHU-002\n",
    "VAV-001\n"
]

with open("equipment.txt", "w") as file:
    file.writelines(lines)
```

`writelines()` list ke elements ko write karta hai.

Important:

`writelines()` khud newline add nahi karta.

Isliye list mein `\n` hona chahiye agar separate lines chahiye.

---

## `Path.write_text()`

```python
from pathlib import Path

Path("data.txt").write_text(
    "Hello World",
    encoding="utf-8"
)
```

---

## Append

Existing file mein data add karna:

```python
with open("log.txt", "a") as file:
    file.write("Work order completed\n")
```

Logs ke liye append useful hai.

---

# Section 30.6: Check Whether a File or Path Exists

`pathlib` recommended:

```python
from pathlib import Path

path = Path("data.txt")

print(path.exists())
```

Agar file/folder exist karta hai:

```text
True
```

warna:

```text
False
```

---

## Check file specifically

```python
if path.is_file():
    print("This is a file")
```

---

## Check directory specifically

```python
if path.is_dir():
    print("This is a directory")
```

---

## Complete example

```python
from pathlib import Path

path = Path("data.txt")

if not path.exists():
    print("Path does not exist")
elif path.is_file():
    print("It is a file")
elif path.is_dir():
    print("It is a directory")
```

---

## Practical Work-Order Example

```python
from pathlib import Path

folder = Path("WorkOrders/WO1001")

if folder.exists():
    print("Work order folder exists")
else:
    print("Folder does not exist")
```

Folder create karna:

```python
folder.mkdir(parents=True, exist_ok=True)
```

`parents=True`:

> Zaroorat ho to parent directories bhi create karo.

`exist_ok=True`:

> Folder already exist ho to error mat do.

---

# Section 30.7: Random File Access Using `mmap`

`mmap` ka matlab:

> Memory-mapped file.

Normal file reading mein:

```python
file.read()
```

use karte hain.

`mmap` mein file ko memory ke saath map kiya ja sakta hai, jis se large files ke specific portions ko efficiently access karna useful ho sakta hai.

Import:

```python
import mmap
```

Example:

```python
import mmap

with open("data.txt", "r+b") as file:
    with mmap.mmap(file.fileno(), 0) as mm:
        print(mm[0:20])
```

Yahan:

```python
file.fileno()
```

file ka underlying file descriptor deta hai.

Aur:

```python
mmap.mmap(...)
```

file ko memory-map karta hai.

---

## `mmap` mein search

Suppose file mein:

```text
AHU-001
AHU-002
VAV-001
```

search karna:

```python
import mmap

with open("data.txt", "rb") as file:
    with mmap.mmap(file.fileno(), 0, access=mmap.ACCESS_READ) as mm:
        if mm.find(b"AHU-002") != -1:
            print("Found")
```

Output:

```text
Found
```

Notice:

```python
b"AHU-002"
```

ye **bytes** hai, string nahi.

---

## `mmap` kab use karein?

Normal small/medium text file ke liye:

```python
open()
read()
```

usually enough hai.

`mmap` zyada relevant ho sakta hai jab:

* file bohat large ho
* random access karna ho
* specific regions search/access karne hon
* low-level/high-performance file processing required ho

Beginner projects mein `mmap` ki zaroorat usually nahi hoti.

---

# Section 30.8: Replacing Text in a File

Suppose file:

```text
AHU-001 is Running
AHU-002 is Running
```

Aur `"Running"` ko `"Stopped"` se replace karna hai.

Simple approach:

```python
from pathlib import Path

path = Path("equipment.txt")

text = path.read_text(encoding="utf-8")

text = text.replace("Running", "Stopped")

path.write_text(text, encoding="utf-8")
```

Ab file:

```text
AHU-001 is Stopped
AHU-002 is Stopped
```

---

## `str.replace()`

Important:

```python
text.replace(old, new)
```

original string ko mutate nahi karta.

Ye **new string return** karta hai.

Isliye:

```python
text.replace("Running", "Stopped")
```

likh kar result ko ignore nahi karna chahiye agar change save karna hai.

Correct:

```python
text = text.replace("Running", "Stopped")
```

---

## File mein specific equipment replace karna

```python
from pathlib import Path

path = Path("equipment.txt")

text = path.read_text(encoding="utf-8")

text = text.replace("AHU-001", "AHU-101")

path.write_text(text, encoding="utf-8")
```

---

# Section 30.9: Checking if a File is Empty

File exist karti hai lekin empty hai ya nahi check karna.

## Method 1: `read_text()`

```python
from pathlib import Path

path = Path("data.txt")

if path.read_text(encoding="utf-8") == "":
    print("File is empty")
else:
    print("File has content")
```

Lekin large file ke liye poori file read karna unnecessary ho sakta hai.

---

## Method 2: File size

```python
from pathlib import Path

path = Path("data.txt")

if path.stat().st_size == 0:
    print("File is empty")
else:
    print("File is not empty")
```

Ye file ke size ko bytes mein check karta hai.

Example:

```python
print(path.stat().st_size)
```

Agar:

```text
0
```

to file empty hai.

---

## Whitespace-only file

Suppose file:

```text
   
```

technically empty nahi hai, kyun ke spaces/newline present hain.

Agar aap **meaningful text** check karna chahte hain:

```python
text = path.read_text(encoding="utf-8")

if not text.strip():
    print("No meaningful content")
```

Ye:

* empty string
* spaces
* tabs
* newlines

ko effectively empty consider karega.

---

# Section 30.10: Read a File Between a Range of Lines

Suppose file:

```text
Line 1
Line 2
Line 3
Line 4
Line 5
Line 6
Line 7
```

Aur humein Line 3 se Line 5 tak read karna hai.

Python list slicing use kar sakte hain:

```python
with open("data.txt", encoding="utf-8") as file:
    lines = file.readlines()

selected = lines[2:5]

for line in selected:
    print(line.strip())
```

Output:

```text
Line 3
Line 4
Line 5
```

Kyun?

Python indexing zero-based hai:

```text
Line 1 → index 0
Line 2 → index 1
Line 3 → index 2
Line 4 → index 3
Line 5 → index 4
```

Isliye:

```python
lines[2:5]
```

Line 3, 4, 5 deta hai.

---

## Large file ke liye

Agar file bohat large ho aur sirf lines 100–110 chahiye, poori file memory mein load karna avoid kar sakte hain.

`enumerate()`:

```python
with open("data.txt", encoding="utf-8") as file:
    for number, line in enumerate(file, start=1):
        if 100 <= number <= 110:
            print(line.strip())
        elif number > 110:
            break
```

Yahan line numbers human-friendly `1, 2, 3...` hain.

---

# Section 30.11: Copy a Directory Tree

Ek complete directory aur uske andar ke files/subdirectories ko copy karne ke liye `shutil.copytree()` useful hai.

```python
import shutil

shutil.copytree("source", "backup")
```

Agar:

```text
source/
    file1.txt
    file2.txt
    reports/
        report.csv
```

hai, to:

```text
backup/
    file1.txt
    file2.txt
    reports/
        report.csv
```

ban jayega.

---

## Destination already exist karti ho

Modern Python mein:

```python
shutil.copytree(
    "source",
    "backup",
    dirs_exist_ok=True
)
```

`dirs_exist_ok=True` ka matlab:

> Destination directory already exist ho to bhi copy continue karo.

---

## `pathlib` + `shutil`

Practical:

```python
from pathlib import Path
import shutil

source = Path("WorkOrders")
destination = Path("WorkOrders_Backup")

shutil.copytree(
    source,
    destination,
    dirs_exist_ok=True
)
```

---

# Section 30.12: Copying Contents of One File to a Different File

Ek file ko doosri file mein copy karne ke liye `shutil.copyfile()` use kar sakte hain.

```python
import shutil

shutil.copyfile("source.txt", "destination.txt")
```

Ab:

```text
source.txt
      ↓
destination.txt
```

destination mein same file contents honge.

---

## `copy()` vs `copyfile()`

`shutil.copyfile()`:

```python
shutil.copyfile("source.txt", "destination.txt")
```

mainly file contents copy karta hai.

`shutil.copy()`:

```python
shutil.copy("source.txt", "destination.txt")
```

file ko copy karta hai aur metadata ka kuch hissa bhi preserve karta hai.

---

## `copy2()`

```python
shutil.copy2("source.txt", "destination.txt")
```

`copy2()` file contents ke saath metadata ko bhi preserve karne ki koshish karta hai.

Simple comparison:

| Function     | Purpose                 |
| ------------ | ----------------------- |
| `copyfile()` | File contents copy      |
| `copy()`     | File + basic metadata   |
| `copy2()`    | File + more metadata    |
| `copytree()` | Complete directory tree |

---

# `Path` aur `os.path`

Python mein paths handle karne ke do common approaches hain.

Old/common:

```python
import os

path = os.path.join("WorkOrders", "WO1001", "report.txt")
```

Modern:

```python
from pathlib import Path

path = Path("WorkOrders") / "WO1001" / "report.txt"
```

`pathlib` beginner ke liye bhi readable hai aur modern Python code mein bohat useful hai.

---

# Windows Paths

Windows mein manually:

```python
path = "C:\\WorkOrders\\WO1001"
```

likhna pad sakta hai kyun ke `\` escape character hai.

Raw string:

```python
path = r"C:\WorkOrders\WO1001"
```

ya better:

```python
from pathlib import Path

path = Path(r"C:\WorkOrders\WO1001")
```

---

# Practical Work-Order Folder Example

Suppose:

```text
D:\WorkOrders
```

mein multiple work-order folders hain.

Python:

```python
from pathlib import Path

base = Path(r"D:\WorkOrders")

for path in base.rglob("*"):
    if path.is_file():
        print(path)
```

Ye recursively tamam files show karega.

---

# Practical: Work-Order Report Copy

Suppose:

```text
D:\WorkOrders\WO1001\report.txt
```

ko backup mein copy karna hai:

```python
from pathlib import Path
import shutil

source = Path(r"D:\WorkOrders\WO1001\report.txt")
destination = Path(r"D:\WorkOrders_Backup\WO1001_report.txt")

destination.parent.mkdir(parents=True, exist_ok=True)

shutil.copy2(source, destination)
```

Flow:

```text
Source file
    ↓
Check/create destination folder
    ↓
copy2()
    ↓
Backup file
```

---

# Important Safety Point: `"w"`

Sabse important file-writing warning:

```python
open("data.txt", "w")
```

existing file ko overwrite kar sakta hai.

Agar existing data preserve karna ho:

```python
open("data.txt", "a")
```

use karein.

Ya pehle carefully check karein:

```python
from pathlib import Path

path = Path("data.txt")

if not path.exists():
    path.write_text("New data", encoding="utf-8")
```

---

# Chapter 30: Quick Reference

## Read

```python
with open("data.txt", "r") as file:
    data = file.read()
```

## Read line-by-line

```python
with open("data.txt") as file:
    for line in file:
        print(line.strip())
```

## Write

```python
with open("data.txt", "w") as file:
    file.write("Hello")
```

## Append

```python
with open("data.txt", "a") as file:
    file.write("New line\n")
```

## Check existence

```python
from pathlib import Path

Path("data.txt").exists()
```

## Check file

```python
Path("data.txt").is_file()
```

## Check folder

```python
Path("WorkOrders").is_dir()
```

## Recursive files

```python
Path("WorkOrders").rglob("*")
```

## Replace text

```python
text = path.read_text()
text = text.replace("old", "new")
path.write_text(text)
```

## Check empty

```python
path.stat().st_size == 0
```

## Copy file

```python
import shutil

shutil.copy2(source, destination)
```

## Copy directory tree

```python
shutil.copytree(source, destination, dirs_exist_ok=True)
```

---

# Chapter 30: Final Mental Model

```text
                 FILES & FOLDERS
                        │
          ┌─────────────┼─────────────┐
          ↓             ↓             ↓
       READ          WRITE          PATH
          │             │             │
      read()        write()       exists()
      readline()    append()      is_file()
      iteration     writelines()  is_dir()
          │             │             │
          └─────────────┼─────────────┘
                        ↓
                     pathlib
                        +
                     shutil
                        +
                      mmap
```

### Sabse important 5 concepts:

**1. File read:**

```python
with open("data.txt") as file:
    data = file.read()
```

**2. File write:**

```python
with open("data.txt", "w") as file:
    file.write("Hello")
```

**3. File existence:**

```python
Path("data.txt").exists()
```

**4. Recursive search:**

```python
Path("WorkOrders").rglob("*.csv")
```

**5. Copy:**

```python
shutil.copy2(source, destination)
```

**Core idea:** Chapter 30 mein `open()` file ke content ke liye, `pathlib` paths/files/folders ke management ke liye, `shutil` copying ke liye, aur `mmap` specialized large-file/random-access scenarios ke liye important tools hain.
