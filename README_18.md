# Chapter 18: Multidimensional Arrays

## Multidimensional Array kya hota hai?

Normal list mein values ek sequence mein hoti hain:

```python
numbers = [10, 20, 30, 40]
```

Lekin jab ek list ke andar doosri list ho, to usay **nested list** kehte hain.

```python
numbers = [
    [10, 20],
    [30, 40]
]
```

Is tarah ki list ko 2D list kaha jata hai.

Python mein built-in multidimensional `array` type nahi hota. Aam tor par multidimensional data ko **lists ke andar lists** ke zariye represent kiya jata hai.

---

## 18.1: Lists in Lists

### Step 1: Simple nested list

```python
numbers = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

print(numbers)
```

Output:

```text
[[10, 20, 30], [40, 50, 60], [70, 80, 90]]
```

Is list mein 3 inner lists hain. Har inner list mein 3 numbers hain.

Isay table ki tarah samajh sakte ho:

<box border={{size:1,color:"#16a34a"}} radius="lg" padding={3} gap={2}>

  <title size="lg" textAlign="center">2D List (3 × 3)</title>
  <grid columns={3} gap={1}>
    {#each [10,20,30,40,50,60,70,80,90] as n,i}
      <grid-item>
        <box background="surface-tertiary" radius="md" padding={3} align="center">
          <title size="xl">{n}</title>
          <caption>Row {Math.floor(i/3)}, Col {i%3}</caption>
        </box>
      </grid-item>
    {/each}
  </grid>
  <caption textAlign="center">Row aur column indexes 0 se start hote hain.</caption>
</box>

### Step 2: Row access karna

Nested list mein pehla index outer list ki row ko select karta hai.

```python
numbers = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

print(numbers[0])
print(numbers[1])
print(numbers[2])
```

Output:

```text
[10, 20, 30]
[40, 50, 60]
[70, 80, 90]
```

* `numbers[0]` pehli inner list deta hai.
* `numbers[1]` doosri inner list deta hai.
* `numbers[2]` teesri inner list deta hai.

### Step 3: Individual element access karna

Agar kisi specific row aur column ki value chahiye, to do indexes use karo.

Syntax:

```python
list_name[row_index][column_index]
```

Example:

```python
numbers = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

print(numbers[0][0])
print(numbers[0][1])
print(numbers[1][2])
print(numbers[2][1])
```

Output:

```text
10
20
60
80
```

Samjho:

```python
numbers[1][2]
```

Iska matlab:

1. `numbers[1]` se doosri row select karo: `[40, 50, 60]`
2. Is row mein `[2]` se teesra element select karo: `60`

### Step 4: Nested list mein value change karna

Lists mutable hoti hain, is liye nested list ke elements ko modify kar sakte ho.

```python
numbers = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

numbers[1][2] = 600

print(numbers)
```

Output:

```text
[[10, 20, 30], [40, 50, 600], [70, 80, 90]]
```

`numbers[1][2]` doosri row ka teesra element hai. Iski value `60` se `600` ho gayi.

### Step 5: Nested list par loop chalana

Agar har row ko print karna ho, to simple `for` loop use kar sakte ho.

```python
numbers = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

for row in numbers:
    print(row)
```

Output:

```text
[10, 20, 30]
[40, 50, 60]
[70, 80, 90]
```

Agar har individual element print karna ho, to nested loops use karo.

```python
for row in numbers:
    for value in row:
        print(value)
```

Output:

```text
10
20
30
40
50
60
70
80
90
```

Yahan:

* Outer loop ek row select karta hai.
* Inner loop us row ke har element par iterate karta hai.

### Step 6: Row aur column indexes ke saath loop

`enumerate()` se row aur column indexes bhi mil sakte hain.

```python
numbers = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

for row_index, row in enumerate(numbers):
    for col_index, value in enumerate(row):
        print(row_index, col_index, value)
```

Output:

```text
0 0 10
0 1 20
0 2 30
1 0 40
1 1 50
1 2 60
2 0 70
2 1 80
2 2 90
```

Is tarah tum har value ki position bhi jaan sakte ho.

### Step 7: HVAC example — Floors aur temperatures

Maan lo ek building ke 3 floors par 3 rooms ke temperature readings hain.

```python
temperatures = [
    [22.5, 23.0, 24.0],
    [21.5, 22.0, 23.5],
    [24.0, 25.0, 26.0]
]

for floor_index, floor in enumerate(temperatures, start=1):
    print("Floor:", floor_index)

    for room_index, temp in enumerate(floor, start=1):
        print("Room:", room_index, "Temperature:", temp)
```

Output:

```text
Floor: 1
Room: 1 Temperature: 22.5
Room: 2 Temperature: 23.0
Room: 3 Temperature: 24.0
Floor: 2
Room: 1 Temperature: 21.5
Room: 2 Temperature: 22.0
Room: 3 Temperature: 23.5
Floor: 3
Room: 1 Temperature: 24.0
Room: 2 Temperature: 25.0
Room: 3 Temperature: 26.0
```

Yahan outer list floors ko represent kar rahi hai aur har inner list us floor ke rooms ki readings rakhti hai.

### Step 8: Har row ka sum aur average

Nested lists mein calculations bhi kar sakte ho.

```python
temperatures = [
    [22, 24, 26],
    [20, 22, 24],
    [25, 26, 27]
]

for floor_index, floor in enumerate(temperatures, start=1):
    total = sum(floor)
    average = total / len(floor)

    print("Floor:", floor_index)
    print("Total:", total)
    print("Average:", average)
```

Output:

```text
Floor: 1
Total: 72
Average: 24.0
Floor: 2
Total: 66
Average: 22.0
Floor: 3
Total: 78
Average: 26.0
```

`sum(floor)` row ke tamam numbers ka sum deta hai aur `len(floor)` us row mein elements ki tadaad deta hai.

---

## 18.2: Lists in Lists in Lists in...

Jab ek list ke andar list ho aur us list ke andar bhi list ho, to hum **3D nested list** bana sakte hain.

### Step 1: 3D list create karna

```python
data = [
    [
        [1, 2, 3],
        [4, 5, 6]
    ],
    [
        [7, 8, 9],
        [10, 11, 12]
    ]
]

print(data)
```

Output:

```text
[[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]]
```

Is structure ko 3D list kehte hain, kyun ke is mein teen levels of indexing hain.

Isay aise samjho:

* Pehla index: group select karta hai.
* Doosra index: group ke andar row select karta hai.
* Teesra index: row ke andar element select karta hai.

### Step 2: 3D list ke elements access karna

```python
data = [
    [
        [1, 2, 3],
        [4, 5, 6]
    ],
    [
        [7, 8, 9],
        [10, 11, 12]
    ]
]

print(data[0])
print(data[0][1])
print(data[0][1][2])
```

Output:

```text
[[1, 2, 3], [4, 5, 6]]
[4, 5, 6]
6
```

`data[0][1][2]` ko step-by-step dekho:

1. `data[0]` pehla group select karta hai.
2. `[1]` us group ki doosri row select karta hai.
3. `[2]` us row ka teesra element select karta hai.

Result `6` hai.

### Step 3: 3D list mein value change karna

```python
data = [
    [
        [1, 2, 3],
        [4, 5, 6]
    ],
    [
        [7, 8, 9],
        [10, 11, 12]
    ]
]

data[1][0][1] = 80

print(data)
```

Output:

```text
[[[1, 2, 3], [4, 5, 6]], [[7, 80, 9], [10, 11, 12]]]
```

`data[1][0][1]` doosre group ki pehli row ka doosra element hai. Iski value `8` se `80` ho gayi.

### Step 4: 3D list par nested loops

3D list ke har element ko access karne ke liye teen loops use kar sakte ho.

```python
data = [
    [
        [1, 2, 3],
        [4, 5, 6]
    ],
    [
        [7, 8, 9],
        [10, 11, 12]
    ]
]

for group in data:
    for row in group:
        for value in row:
            print(value)
```

Output:

```text
1
2
3
4
5
6
7
8
9
10
11
12
```

Har loop ek level handle karta hai.

### Step 5: 3D list ka practical HVAC example

Maan lo building mein 2 floors hain, har floor par 2 AHUs hain, aur har AHU ke 3 temperature sensors hain.

```python
temperatures = [
    [
        [22.5, 23.0, 24.0],
        [21.5, 22.0, 23.0]
    ],
    [
        [24.0, 25.0, 26.0],
        [22.0, 23.5, 24.5]
    ]
]
```

Structure:

```text
Floor 1
    AHU 1 → [22.5, 23.0, 24.0]
    AHU 2 → [21.5, 22.0, 23.0]

Floor 2
    AHU 1 → [24.0, 25.0, 26.0]
    AHU 2 → [22.0, 23.5, 24.5]
```

Ab har sensor ki reading print karte hain:

```python
for floor_index, floor in enumerate(temperatures, start=1):
    for ahu_index, ahu in enumerate(floor, start=1):
        for sensor_index, temp in enumerate(ahu, start=1):
            print(
                "Floor:", floor_index,
                "AHU:", ahu_index,
                "Sensor:", sensor_index,
                "Temperature:", temp
            )
```

Output:

```text
Floor: 1 AHU: 1 Sensor: 1 Temperature: 22.5
Floor: 1 AHU: 1 Sensor: 2 Temperature: 23.0
Floor: 1 AHU: 1 Sensor: 3 Temperature: 24.0
Floor: 1 AHU: 2 Sensor: 1 Temperature: 21.5
Floor: 1 AHU: 2 Sensor: 2 Temperature: 22.0
Floor: 1 AHU: 2 Sensor: 3 Temperature: 23.0
Floor: 2 AHU: 1 Sensor: 1 Temperature: 24.0
Floor: 2 AHU: 1 Sensor: 2 Temperature: 25.0
Floor: 2 AHU: 1 Sensor: 3 Temperature: 26.0
Floor: 2 AHU: 2 Sensor: 1 Temperature: 22.0
Floor: 2 AHU: 2 Sensor: 2 Temperature: 23.5
Floor: 2 AHU: 2 Sensor: 3 Temperature: 24.5
```

### Step 6: 3D list mein total aur average

Agar tamam sensor readings ka average chahiye:

```python
temperatures = [
    [
        [22, 23, 24],
        [21, 22, 23]
    ],
    [
        [24, 25, 26],
        [22, 23, 24]
    ]
]

total = 0
count = 0

for floor in temperatures:
    for ahu in floor:
        for temp in ahu:
            total += temp
            count += 1

average = total / count

print("Total:", total)
print("Count:", count)
print("Average:", average)
```

Output:

```text
Total: 279
Count: 12
Average: 23.25
```

Yahan teen nested loops tamam readings par iterate kar rahe hain.

---

# 2D aur 3D Lists ka Comparison

| Feature    | 2D List                    | 3D List                                    |
| ---------- | -------------------------- | ------------------------------------------ |
| Structure  | List ke andar lists        | List ke andar lists, phir unke andar lists |
| Indexes    | 2                          | 3                                          |
| Example    | `data[1][2]`               | `data[1][0][2]`                            |
| Common use | Table, matrix              | Multiple tables ya grouped data            |
| Loops      | Aam tor par 2 nested loops | Aam tor par 3 nested loops                 |

## Jagah aur indexes ka mental model

2D list:

```python
data[row][column]
```

3D list:

```python
data[group][row][column]
```

4D list mein ek aur index add ho sakta hai:

```python
data[block][group][row][column]
```

Isi tarah aur dimensions bhi ban sakti hain. Lekin dimensions barhne ke saath data ko samajhna aur maintain karna mushkil ho sakta hai.

---

# Important: Nested Lists mein Shared References

Ek common Python mistake se bachna zaroori hai.

Is code ko dekho:

```python
matrix = [[0] * 3] * 3

matrix[0][0] = 99

print(matrix)
```

Output:

```text
[[99, 0, 0], [99, 0, 0], [99, 0, 0]]
```

Tumne sirf pehli row ka pehla element change karna chaha tha, lekin teeno rows change ho gayin.

Kyun?

`[[0] * 3] * 3` mein same inner list ka reference teen baar use hota hai.

### Correct method

List comprehension use karo:

```python
matrix = [[0] * 3 for _ in range(3)]

matrix[0][0] = 99

print(matrix)
```

Output:

```text
[[99, 0, 0], [0, 0, 0], [0, 0, 0]]
```

Ab har row ek separate list hai.

---

# Practice Exercises

## Exercise 1: 2D list indexing

Is code ka output batao:

```python
data = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

print(data[0][2])
print(data[2][1])
```

## Exercise 2: Value modify karna

Is list mein `50` ko `500` se replace karo.

```python
data = [
    [10, 20],
    [30, 40],
    [50, 60]
]
```

## Exercise 3: Nested loops

Aisa code likho jo is 2D list ke tamam numbers print kare:

```python
numbers = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

## Exercise 4: Row average

Har row ka average print karne ke liye code likho:

```python
temperatures = [
    [20, 22, 24],
    [25, 26, 27],
    [21, 23, 25]
]
```

## Exercise 5: 3D list indexing

Is code ka output batao:

```python
data = [
    [[1, 2], [3, 4]],
    [[5, 6], [7, 8]]
]

print(data[1][0][1])
```

## Exercise 6: Shared references

Is code ka output kya hoga aur kyun?

```python
matrix = [[0] * 2] * 2

matrix[1][0] = 5

print(matrix)
```

---

# Final Summary

* **Multidimensional list** ek aisi list hai jiske andar doosri lists hoti hain.
* 2D list mein aam tor par rows aur columns hote hain.
* 2D list ke elements ko `data[row][column]` se access karte hain.
* 3D list mein ek extra level hota hai: `data[group][row][column]`.
* Har nested level ke liye ek loop use kar sakte hain.
* `enumerate()` se indexes aur values dono mil sakte hain.
* Nested lists mutable hoti hain, is liye unke elements modify kiye ja sakte hain.
* `[[0] * 3] * 3` jaisi construction shared references create kar sakti hai. Independent rows ke liye list comprehension use karo.
* Dimensions barhne par nested lists ko samajhna mushkil ho sakta hai. Scientific numerical computing mein NumPy arrays bhi use hote hain.
