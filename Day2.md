# Python — Loops

## Topics Covered

- `while` loop
- `break`
- `continue`
- Sentinel-controlled loops
- Input-controlled loops
- Accumulator pattern
- Counter pattern
- Minimum / Maximum pattern
- Average calculation
- Series generation
- Range traversal
- Password attempt control
- Variable swapping

---

# 1. `while` Loop

A `while` loop repeatedly executes a block of code **as long as a condition is `True`**.

## Syntax

```python
while condition:
    # logic
```

Example:

```python
i = 1

while i <= 5:
    print(i)
    i += 1
```

Output:

```text
1
2
3
4
5
```

---

# 2. How a `while` Loop Works

Consider:

```python
i = 1

while i <= 5:
    print(i)
    i += 1
```

### Trace

```text
i = 1

Check: 1 <= 5 → True
Print 1
i = 2

Check: 2 <= 5 → True
Print 2
i = 3

Check: 3 <= 5 → True
Print 3
i = 4

Check: 4 <= 5 → True
Print 4
i = 5

Check: 5 <= 5 → True
Print 5
i = 6

Check: 6 <= 5 → False
Stop
```

### Important

A `while` loop needs something that eventually makes the condition `False`.

```python
i += 1
```

Without it:

```python
while i <= 5:
    print(i)
```

the loop can become infinite.

---

# 3. `for` vs `while`

## `for`

Use when the number of iterations is generally known.

```python
for i in range(1, 6):
    print(i)
```

## `while`

Use when repetition depends on a condition or user input.

```python
num = int(input())

while num >= 0:
    num = int(input())
```

### Mental Model

```text
for
↓
"Repeat this for these values"

while
↓
"Keep repeating while this condition is true"
```

---

# 4. `break`

`break` immediately terminates the loop.

## Syntax

```python
while condition:

    if another_condition:
        break
```

Example:

```python
while True:

    num = int(input())

    if num == 0:
        break

    print(num)
```

If the user enters:

```text
10
20
30
0
```

the loop stops at `0`.

---

# 5. `continue`

`continue` skips the current iteration and moves to the next iteration.

Example:

```python
for i in range(1, 6):

    if i == 3:
        continue

    print(i)
```

Output:

```text
1
2
4
5
```

When `i == 3`:

```text
continue
   ↓
skip print()
   ↓
next iteration
```

---

# 6. `break` vs `continue`

```text
break
  ↓
STOP THE ENTIRE LOOP

continue
  ↓
SKIP CURRENT ITERATION
  ↓
CONTINUE LOOP
```

Example:

```python
for i in range(1, 6):

    if i == 3:
        continue

    if i == 5:
        break

    print(i)
```

Trace:

```text
i = 1 → print
i = 2 → print
i = 3 → continue
i = 4 → print
i = 5 → break
```

Output:

```text
1
2
4
```

---

# 7. Problem 1 — While Loop

Basic `while` loop:

```python
i = 1

while i <= 5:
    print(i)
    i += 1
```

### Pattern

```python
initialization

while condition:
    logic
    update
```

Remember:

```text
Initialize
   ↓
Check
   ↓
Execute
   ↓
Update
   ↓
Check again
```

---

# 8. Problem 2 — Skip Negative Numbers, Stop at Zero

Requirement:

- Negative → skip
- Zero → stop
- Positive → process

### Code

```python
numbers = [10, -5, 20, -3, 30, 0, 40]

for num in numbers:

    if num < 0:
        continue

    if num == 0:
        break

    print(num)
```

### Trace

```text
10 → positive → print
-5 → negative → continue
20 → positive → print
-3 → negative → continue
30 → positive → print
0  → break
40 → never reached
```

Output:

```text
10
20
30
```

### Important Concept

`continue` and `break` have different jobs:

```text
negative → continue
zero     → break
positive → process
```

---

# 9. Problem 3 — Keep Asking Until Negative

Requirement:

> Keep taking numbers until a negative number is entered. Print the sum of all non-negative numbers.

### Code

```python
total = 0

while True:

    num = int(input("Enter number: "))

    if num < 0:
        break

    total += num

print("Sum =", total)
```

### Example Input

```text
10
20
30
-5
```

### Trace

```text
total = 0

10 → total = 10
20 → total = 30
30 → total = 60
-5 → break
```

Output:

```text
Sum = 60
```

### Technique

This is called a **sentinel-controlled loop**.

The sentinel is:

```text
negative number
```

The sentinel tells the program:

> Stop accepting input.

---

# 10. Problem 4 — Ask for Name Until `END`

### Code

```python
while True:

    name = input("Enter name: ")

    if name == "END":
        break

    print(name)

print("I am done.")
```

### Input

```text
Daya
Rahul
Anu
END
```

### Trace

```text
Daya → print
Rahul → print
Anu → print
END → break
```

Output:

```text
Daya
Rahul
Anu
I am done.
```

### Pattern

```python
while True:

    value = input()

    if value == sentinel:
        break

    process(value)
```

This pattern is extremely common.

---

# 11. Problem 5 — Test Average

Requirements:

1. Keep accepting grades.
2. Stop when grade is negative.
3. Add valid grades.
4. Count courses.
5. Calculate average.
6. Print letter grade.

### Code

```python
total = 0
count = 0

while True:

    grade = float(input("Enter grade: "))

    if grade < 0:
        break

    total += grade
    count += 1

if count > 0:

    average = total / count

    print("Average =", average)

    if average >= 90:
        print("A")
    elif average >= 80:
        print("B")
    elif average >= 70:
        print("C")
    elif average >= 60:
        print("D")
    else:
        print("F")

else:
    print("No grades entered.")
```

### Trace

Suppose:

```text
90
80
70
-1
```

Initial:

```text
total = 0
count = 0
```

Grade `90`:

```text
total = 90
count = 1
```

Grade `80`:

```text
total = 170
count = 2
```

Grade `70`:

```text
total = 240
count = 3
```

Grade `-1`:

```text
break
```

Average:

```text
240 / 3 = 80
```

Therefore:

```text
B
```

### Important Pattern

This combines two patterns:

```text
Accumulator → total
Counter     → count
```

---

# 12. Problem 6 — Series

Series:

```text
105 98 91 ... 7
```

Observe the difference:

```text
105 → 98 = -7
98 → 91 = -7
91 → 84 = -7
```

So the step is:

```text
-7
```

### Code

```python
i = 105

while i >= 7:
    print(i)
    i -= 7
```

Output:

```text
105
98
91
84
77
70
63
56
49
42
35
28
21
14
7
```

### Pattern Recognition

Whenever a series is given:

```text
105 98 91 ...
```

first calculate:

```text
98 - 105 = -7
```

That gives the step.

---

# 13. Problem 7 — Difference Between Sum of First N Odd and Even Numbers

Suppose:

```text
N = 3
```

First 3 odd numbers:

```text
1 + 3 + 5 = 9
```

First 3 even numbers:

```text
2 + 4 + 6 = 12
```

Difference:

```text
9 - 12 = -3
```

### Code

```python
n = int(input())

odd_sum = 0
even_sum = 0

i = 1

while i <= n:

    odd_sum += (2 * i - 1)
    even_sum += (2 * i)

    i += 1

difference = odd_sum - even_sum

print("Difference =", difference)
```

### Trace for `n = 3`

```text
i = 1
odd  = 2(1)-1 = 1
even = 2(1)   = 2

i = 2
odd  = 3
even = 4

i = 3
odd  = 5
even = 6
```

Sums:

```text
odd_sum  = 1 + 3 + 5 = 9
even_sum = 2 + 4 + 6 = 12
```

Difference:

```text
9 - 12 = -3
```

---

# 14. Problem 8 — Display Numbers in a Defined Range

Suppose the user gives:

```text
start = 5
end = 10
```

### Code

```python
start = int(input("Enter start: "))
end = int(input("Enter end: "))

while start <= end:

    print(start)

    start += 1
```

Output:

```text
5
6
7
8
9
10
```

### Trace

```text
start = 5

5 <= 10 → print 5
start = 6

6 <= 10 → print 6
start = 7

...

10 <= 10 → print 10
start = 11

11 <= 10 → False
stop
```

---

# 15. Problem 9 — Sum Until User Enters 0

Here:

```text
0
```

is the sentinel.

### Code

```python
total = 0

while True:

    num = int(input("Enter number: "))

    if num == 0:
        break

    total += num

print("Sum =", total)
```

Example:

```text
10
20
30
0
```

Trace:

```text
total = 0

10 → 10
20 → 30
30 → 60
0  → break
```

Output:

```text
Sum = 60
```

---

# 16. Problem 10 — Count Positive and Negative Numbers

Stop when the user enters `0`.

### Code

```python
positive_count = 0
negative_count = 0

while True:

    num = int(input("Enter number: "))

    if num == 0:
        break

    if num > 0:
        positive_count += 1

    elif num < 0:
        negative_count += 1

print("Positive numbers =", positive_count)
print("Negative numbers =", negative_count)
```

### Example

Input:

```text
10
-5
20
-3
7
0
```

### Trace

```text
10  → positive_count = 1
-5  → negative_count = 1
20  → positive_count = 2
-3  → negative_count = 2
7   → positive_count = 3
0   → break
```

Output:

```text
Positive numbers = 3
Negative numbers = 2
```

---

# 17. Problem 11 — Largest and Smallest of N Positive Numbers

This introduces the **minimum/maximum pattern**.

### Code

```python
n = int(input("How many numbers? "))

i = 0
largest = None
smallest = None

while i < n:

    num = int(input("Enter positive number: "))

    if largest is None:
        largest = num
        smallest = num

    else:

        if num > largest:
            largest = num

        if num < smallest:
            smallest = num

    i += 1

print("Largest =", largest)
print("Smallest =", smallest)
```

### Example

```text
N = 5

10
25
3
40
15
```

### Trace

First:

```text
largest = 10
smallest = 10
```

Next `25`:

```text
25 > 10
largest = 25
```

Next `3`:

```text
3 < 10
smallest = 3
```

Next `40`:

```text
40 > 25
largest = 40
```

Next `15`:

```text
no change
```

Final:

```text
Largest = 40
Smallest = 3
```

---

# 18. Problem 12 — Series `2 22 222 ...`

Example:

```text
N = 5
```

Output:

```text
2
22
222
2222
22222
```

### Technique

Instead of creating strings, we can use mathematics.

```text
2
22
222
2222
```

Pattern:

```text
previous × 10 + 2
```

### Code

```python
n = int(input())

value = 0

i = 1

while i <= n:

    value = value * 10 + 2

    print(value)

    i += 1
```

### Trace

Initial:

```text
value = 0
```

Iteration 1:

```text
0 × 10 + 2 = 2
```

Iteration 2:

```text
2 × 10 + 2 = 22
```

Iteration 3:

```text
22 × 10 + 2 = 222
```

Iteration 4:

```text
222 × 10 + 2 = 2222
```

---

# 19. Problem 13 — Natural Even Numbers Starting From N

There are two possible interpretations.

If `n` itself should be the starting point and we need even numbers:

```python
n = int(input())

if n % 2 != 0:
    n += 1

count = int(input("How many values? "))

i = 0

while i < count:

    print(n)

    n += 2
    i += 1
```

### Example

Input:

```text
n = 5
count = 5
```

Since `5` is odd:

```text
5 + 1 = 6
```

Output:

```text
6
8
10
12
14
```

### Technique

Once an even number is found:

```python
n += 2
```

generates the next even number.

---

# 20. Problem 14 — Swap Without Third Variable

Python has:

```python
a, b = b, a
```

But if the goal is to understand the underlying arithmetic technique:

### Addition/Subtraction Method

```python
a = 10
b = 20

a = a + b
b = a - b
a = a - b
```

### Trace

Initial:

```text
a = 10
b = 20
```

Step 1:

```text
a = 10 + 20
a = 30
```

Step 2:

```text
b = 30 - 20
b = 10
```

Step 3:

```text
a = 30 - 10
a = 20
```

Final:

```text
a = 20
b = 10
```

### Important

This technique can overflow fixed-width integer types in some languages, so it is mainly useful for understanding the concept.

---

# 21. Problem 15 — Password With Maximum 3 Attempts

Requirement:

- Password is predefined.
- User gets maximum 3 attempts.
- Correct password → access granted.
- Three wrong attempts → locked.

### Code

```python
curr_password = "python123"

attempts = 0

while attempts < 3:

    password = input("Enter password: ")

    if password == curr_password:
        print("Password correct. Access granted.")
        break

    attempts += 1

    print("Wrong password.")

else:
    print("Account locked.")
```

### Trace — Correct Password

Suppose:

```text
curr_password = python123
```

Input:

```text
python123
```

Comparison:

```text
password == curr_password
        ↓
       True
        ↓
Access granted
        ↓
break
```

---

### Trace — Three Wrong Attempts

Input:

```text
abc
xyz
hello
```

```text
attempts = 0

abc
 ↓
wrong
 ↓
attempts = 1

xyz
 ↓
wrong
 ↓
attempts = 2

hello
 ↓
wrong
 ↓
attempts = 3
```

Condition:

```text
attempts < 3
```

becomes:

```text
3 < 3 → False
```

The loop ends.

Output:

```text
Account locked.
```

---

# 22. Python `while ... else`

This is an interesting Python feature.

```python
while condition:

    if success:
        break

else:
    # executes if loop ended normally
```

In the password example:

```python
while attempts < 3:

    ...

    if password == curr_password:
        break

else:
    print("Account locked.")
```

The `else` executes only when the loop finishes **without `break`**.

This behavior does not have a direct Java equivalent.

---

# 23. Core Patterns Learned

## Pattern 1 — Basic While Loop

```python
i = 0

while i < n:
    # logic
    i += 1
```

---

## Pattern 2 — Infinite Loop + Break

```python
while True:

    value = input()

    if value == sentinel:
        break

    # process
```

This is one of the most useful input patterns.

---

## Pattern 3 — Sentinel-Controlled Loop

```python
while True:

    num = int(input())

    if num == 0:
        break

    # process num
```

The sentinel is:

```text
0
```

---

## Pattern 4 — Accumulator

```python
total = 0

while condition:
    total += value
```

Used for:

- sum
- total marks
- total price
- average

---

## Pattern 5 — Counter

```python
count = 0

while condition:

    if condition:
        count += 1
```

Used for:

- counting positive numbers
- counting negative numbers
- counting even numbers
- counting occurrences

---

## Pattern 6 — Maximum

```python
if num > largest:
    largest = num
```

---

## Pattern 7 — Minimum

```python
if num < smallest:
    smallest = num
```

---

## Pattern 8 — Skip

```python
if condition:
    continue
```

---

## Pattern 9 — Stop

```python
if condition:
    break
```

---

## Pattern 10 — Series

If:

```text
2
22
222
2222
```

then:

```python
value = value * 10 + 2
```

---

# 24. Complete Concept Map

```text
LOOPS
│
├── for
│   ├── fixed iteration
│   ├── range()
│   └── traversal
│
└── while
    │
    ├── condition-controlled
    ├── user-input controlled
    ├── sentinel-controlled
    │
    ├── break
    │   └── terminate loop
    │
    └── continue
        └── skip current iteration


LOOP PATTERNS
│
├── Accumulator
│   └── total += value
│
├── Counter
│   └── count += 1
│
├── Maximum
│   └── largest = max
│
├── Minimum
│   └── smallest = min
│
└── Series
    └── previous value → next value
```

---

# 25. Most Important Mental Model

When you see a `while` problem, ask these questions:

```text
1. What should I initialize?
        ↓
2. What condition keeps the loop running?
        ↓
3. What should happen inside the loop?
        ↓
4. What changes every iteration?
        ↓
5. What stops the loop?
```

Example:

> Keep entering numbers until 0 and calculate their sum.

Think:

```text
Initialize
total = 0

Loop condition
while True

Input
num

Stop condition
num == 0

Process
total += num
```

Then write:

```python
total = 0

while True:

    num = int(input())

    if num == 0:
        break

    total += num

print(total)
```

This is the real skill: **convert the English problem into a loop pattern.**
