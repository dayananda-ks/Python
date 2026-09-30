# Python — Conditional Statements & `for` Loop

## Day Topic

**Conditional Statements & `for` Loop**

This README covers:

- `for` loop
- `range()`
- Forward iteration
- Reverse iteration
- List indexing
- `if`, `elif`, `else`
- `%` modulo operator
- Multiplication tables
- Natural-number sums
- FizzBuzz
- Input handling
- Recursion
- Basic problem-solving patterns

---

# 1. `for` Loop in Python

A `for` loop is used when we want to execute a block of code repeatedly for every value in a sequence.

### Syntax

```python
for variable in sequence:
    # logic
```

Example:

```python
for i in range(1, 6):
    print(i)
```

### Output

```text
1
2
3
4
5
```

---

# 2. Understanding `range()`

`range()` generates a sequence of numbers.

### Syntax

```python
range(start, stop, step)
```

Important:

> The `stop` value is NOT included.

Example:

```python
range(1, 6)
```

produces:

```text
1 2 3 4 5
```

### Three forms

```python
range(stop)
range(start, stop)
range(start, stop, step)
```

Examples:

```python
range(5)
```

```text
0 1 2 3 4
```

```python
range(2, 7)
```

```text
2 3 4 5 6
```

```python
range(2, 10, 2)
```

```text
2 4 6 8
```

---

# 3. Forward `for` Loop

A forward loop moves from a smaller value to a larger value.

### Syntax

```python
for variable in range(start, end + 1):
    # logic
```

Example:

```python
for i in range(1, 6):
    print(i)
```

### Trace

```text
range(1, 6)
        ↓
      1 2 3 4 5
```

| Iteration | `i` | Output |
|---|---:|---:|
| 1 | 1 | 1 |
| 2 | 2 | 2 |
| 3 | 3 | 3 |
| 4 | 4 | 4 |
| 5 | 5 | 5 |

---

# 4. Reverse / Decrementing Loop

To move backwards, use a negative `step`.

### Syntax

```python
for variable in range(start, end - 1, -1):
    # logic
```

Example:

```python
for i in range(5, 0, -1):
    print(i)
```

### Output

```text
5
4
3
2
1
```

### Important Rule

For a decreasing loop:

```text
start > stop
```

and:

```text
step < 0
```

---

# 5. Conditional Statements

Conditional statements allow a program to make decisions.

Python provides:

```python
if
elif
else
```

### Syntax

```python
if condition:
    # logic
elif condition:
    # logic
else:
    # logic
```

Example:

```python
num = 10

if num > 0:
    print("Positive")
elif num < 0:
    print("Negative")
else:
    print("Zero")
```

### Trace

```text
num = 10
   ↓
num > 0 ?
   ↓
True
   ↓
Positive
```

Only the matching block executes.

---

# 6. Modulo Operator `%`

The modulo operator returns the remainder.

### Syntax

```python
a % b
```

Example:

```python
10 % 3
```

Result:

```text
1
```

because:

```text
10 ÷ 3 = 3 remainder 1
```

## Checking Even/Odd

```python
if num % 2 == 0:
    print("Even")
else:
    print("Odd")
```

### Trace

For:

```text
num = 8
```

```text
8 % 2
 ↓
0
 ↓
Even
```

For:

```text
num = 7
```

```text
7 % 2
 ↓
1
 ↓
Odd
```

---

# 7. Problem 1 — Display Numbers from -10 to -1

### Code

```python
for i in range(-10, 0):
    print(i)
```

### Trace

```text
range(-10, 0)
      ↓
-10 -9 -8 -7 -6 -5 -4 -3 -2 -1
```

### Output

```text
-10
-9
-8
-7
-6
-5
-4
-3
-2
-1
```

---

# 8. Problem 2 — Print `Done` After Successful Loop

### Code

```python
for i in range(5):
    print(i)

print("Done")
```

### Trace

```text
range(5)
   ↓
0 1 2 3 4
   ↓
loop finishes
   ↓
Done
```

### Output

```text
0
1
2
3
4
Done
```

The important concept is that the statement:

```python
print("Done")
```

is outside the loop.

Therefore it executes after the loop completes.

---

# 9. Problem 3 — Multiplication Table

### Input

```text
5
```

### Code

```python
num = int(input("Enter number: "))

for i in range(1, 11):
    print(num, "x", i, "=", num * i)
```

### Trace

For `num = 5`:

```text
i = 1 → 5 × 1 = 5
i = 2 → 5 × 2 = 10
i = 3 → 5 × 3 = 15
...
i = 10 → 5 × 10 = 50
```

### Output

```text
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
5 x 6 = 30
5 x 7 = 35
5 x 8 = 40
5 x 9 = 45
5 x 10 = 50
```

---

# 10. Problem 4 — Cube of Every Number

Given `n`, print the cube of every number from `1` to `n`.

### Code

```python
n = int(input("Enter n: "))

for i in range(1, n + 1):
    cube = i ** 3
    print("Current Number is :", i, "and the cube is", cube)
```

### Example

Input:

```text
3
```

### Trace

```text
i = 1
1 ** 3 = 1

i = 2
2 ** 3 = 8

i = 3
3 ** 3 = 27
```

### Output

```text
Current Number is : 1 and the cube is 1
Current Number is : 2 and the cube is 8
Current Number is : 3 and the cube is 27
```

---

# 11. Problem 5 — Print Elements at Odd Index Positions

Python lists use **zero-based indexing**.

Example:

```python
numbers = [10, 20, 30, 40, 50, 60]
```

Indexes:

```text
Value:   10  20  30  40  50  60
Index:    0   1   2   3   4   5
```

Odd indexes are:

```text
1, 3, 5
```

### Code

```python
numbers = [10, 20, 30, 40, 50, 60]

for i in range(1, len(numbers), 2):
    print(numbers[i])
```

### Trace

```text
len(numbers) = 6

range(1, 6, 2)
      ↓
1 3 5
```

Then:

```text
numbers[1] → 20
numbers[3] → 40
numbers[5] → 60
```

### Output

```text
20
40
60
```

---

# 12. Problem 6 — Multiplication Table from 1 to 10

This is the same fundamental technique as Problem 3.

```python
n = int(input())

for i in range(1, 11):
    print(n * i)
```

The key pattern is:

```text
fixed number × changing loop variable
```

---

# 13. Problem 7 — Sum of Natural Numbers

Natural numbers:

```text
1, 2, 3, 4, ...
```

### Code

```python
n = int(input("Enter n: "))

total = 0

for i in range(1, n + 1):
    total = total + i

print("Sum =", total)
```

### Trace

For:

```text
n = 5
```

Initial:

```text
total = 0
```

Iteration 1:

```text
total = 0 + 1
      = 1
```

Iteration 2:

```text
total = 1 + 2
      = 3
```

Iteration 3:

```text
total = 3 + 3
      = 6
```

Iteration 4:

```text
total = 6 + 4
      = 10
```

Iteration 5:

```text
total = 10 + 5
      = 15
```

### Output

```text
Sum = 15
```

### Technique

This is called an **accumulator pattern**.

```python
total = 0

for i in range(...):
    total = total + i
```

You will use this pattern heavily in DSA.

---

# 14. Problem 8 — FizzBuzz

Rules:

```text
Multiple of 3       → Fizz
Multiple of 5       → Buzz
Multiple of 3 & 5   → FizzBuzz
Otherwise            → number
```

### Code

```python
for i in range(1, 51):

    if i % 3 == 0 and i % 5 == 0:
        print("FizzBuzz")

    elif i % 3 == 0:
        print("Fizz")

    elif i % 5 == 0:
        print("Buzz")

    else:
        print(i)
```

### Important

Check the combined condition first:

```python
i % 3 == 0 and i % 5 == 0
```

Otherwise, `15` would match the multiple-of-3 condition first.

### Trace for 15

```text
15 % 3 == 0 → True
15 % 5 == 0 → True

True AND True
      ↓
FizzBuzz
```

---

# 15. Problem 9 — Reverse a List

### Method 1 — `range()`

```python
numbers = [10, 20, 30, 40, 50]

for i in range(len(numbers) - 1, -1, -1):
    print(numbers[i])
```

### Trace

```text
len(numbers) = 5

len(numbers) - 1 = 4
```

Therefore:

```text
range(4, -1, -1)
        ↓
4 3 2 1 0
```

Access:

```text
numbers[4] → 50
numbers[3] → 40
numbers[2] → 30
numbers[1] → 20
numbers[0] → 10
```

### Output

```text
50
40
30
20
10
```

---

# 16. Problem 10 — Odd or Even

Core technique:

```python
num = int(input())

if num % 2 == 0:
    print("Even")
else:
    print("Odd")
```

### Decision Tree

```text
              Number
                 |
             num % 2
              /   \
             0    non-zero
             |       |
           Even     Odd
```

---

# 17. Problem 11 — Even or Odd

The same fundamental concept applies:

```python
if n % 2 == 0:
    # even
else:
    # odd
```

The important operation is:

```python
%
```

which gives the remainder.

---

# 18. Problem 12 — Positive, Negative or Zero

### Code

```python
num = int(input())

if num > 0:
    print("Positive")

elif num < 0:
    print("Negative")

else:
    print("Zero")
```

### Trace

For:

```text
num = -5
```

```text
-5 > 0 → False
-5 < 0 → True
          ↓
       Negative
```

---

# 19. Problem 13 — Greatest of Three Numbers

### Code

```python
a = int(input())
b = int(input())
c = int(input())

if a >= b and a >= c:
    print(a)

elif b >= a and b >= c:
    print(b)

else:
    print(c)
```

### Technique

This uses:

```text
comparison operators
+
logical AND
+
if / elif / else
```

---

# 20. Problem 14 — Leap Year

A year is a leap year when:

```text
divisible by 400
OR
divisible by 4 AND not divisible by 100
```

### Code

```python
year = int(input())

if year % 400 == 0:
    print("Leap Year")

elif year % 100 == 0:
    print("Not a Leap Year")

elif year % 4 == 0:
    print("Leap Year")

else:
    print("Not a Leap Year")
```

### Example

```text
2024 % 4 = 0
```

Therefore:

```text
2024 → Leap Year
```

---

# 21. Problem 15 — Print 1 to N Without Loop

This introduces **recursion**.

### Code

```python
def print_numbers(n):

    if n == 0:
        return

    print_numbers(n - 1)
    print(n)


n = int(input())
print_numbers(n)
```

For:

```text
n = 3
```

### Call Trace

```text
print_numbers(3)
    ↓
print_numbers(2)
    ↓
print_numbers(1)
    ↓
print_numbers(0)
    ↓
return
```

Now the calls return:

```text
print 1
print 2
print 3
```

### Output

```text
1
2
3
```

---

# 22. Problem 16 — Print N to 1 Without Loop

### Code

```python
def print_numbers(n):

    if n == 0:
        return

    print(n)
    print_numbers(n - 1)


n = int(input())
print_numbers(n)
```

For:

```text
n = 3
```

Trace:

```text
print 3
 ↓
print 2
 ↓
print 1
 ↓
print_numbers(0)
 ↓
return
```

Output:

```text
3
2
1
```

---

# 23. Recursion Pattern

Every basic recursion problem contains:

### 1. Base Case

```python
if n == 0:
    return
```

### 2. Recursive Call

```python
print_numbers(n - 1)
```

Without a base case, recursion can continue indefinitely.

---

# 24. Problem 17 — Multiplication Table

General pattern:

```python
n = int(input())

for i in range(1, 11):
    print(n * i)
```

The important idea is:

```text
loop variable changes
number remains fixed
```

---

# 25. Problem 18 — Reverse Coding

The important technique behind many reverse-number problems is:

```python
digit = n % 10
n = n // 10
```

Example:

```text
n = 1234
```

First iteration:

```text
1234 % 10 = 4
1234 // 10 = 123
```

Second:

```text
123 % 10 = 3
123 // 10 = 12
```

Third:

```text
12 % 10 = 2
12 // 10 = 1
```

Fourth:

```text
1 % 10 = 1
1 // 10 = 0
```

Digits obtained:

```text
4 3 2 1
```

This technique is extremely important for DSA.

---

# 26. Problem 19 — Calculator

A calculator problem generally uses:

```text
input
+
operator
+
conditional statement
```

Example:

```python
a = int(input())
b = int(input())
operator = input()

if operator == "+":
    print(a + b)

elif operator == "-":
    print(a - b)

elif operator == "*":
    print(a * b)

elif operator == "/":
    print(a / b)

else:
    print("Invalid operator")
```

### Decision Flow

```text
operator
    |
    +---- "+" → addition
    |
    +---- "-" → subtraction
    |
    +---- "*" → multiplication
    |
    +---- "/" → division
    |
    +---- other → invalid
```

---

# 27. Problem 20 — Basic Input / Output

Python input:

```python
name = input()
```

Input is initially treated as a string.

For integer input:

```python
num = int(input())
```

For floating-point input:

```python
num = float(input())
```

Output:

```python
print(num)
```

---

# 28. Taking Multiple Inputs

### One line

Input:

```text
10 20
```

Code:

```python
a, b = map(int, input().split())
```

Process:

```text
input()
 ↓
"10 20"
 ↓
split()
 ↓
["10", "20"]
 ↓
map(int, ...)
 ↓
10, 20
```

---

# 29. Swapping Two Numbers

Python makes swapping very simple.

```python
a = 10
b = 20

a, b = b, a
```

After swapping:

```text
a = 20
b = 10
```

Python uses **multiple assignment / tuple unpacking**.

---

# 30. Core Python Techniques Learned

You have actually learned several important programming techniques through these problems.

## Technique 1 — Counting Loop

```python
for i in range(1, n + 1):
```

Used for:

- printing numbers
- tables
- sums
- cubes
- counting problems

---

## Technique 2 — Accumulator

```python
total = 0

for i in range(1, n + 1):
    total += i
```

Used when repeatedly building a result.

---

## Technique 3 — Conditional Decision

```python
if condition:
    ...
elif condition:
    ...
else:
    ...
```

Used for:

- positive/negative
- greatest number
- leap year
- calculator
- FizzBuzz

---

## Technique 4 — Modulo

```python
n % 2
```

Used for:

- even/odd
- divisibility
- FizzBuzz
- extracting digits
- leap year

---

## Technique 5 — Reverse Iteration

```python
range(start, stop, -1)
```

Used for:

- reverse numbers
- reverse lists
- countdowns

---

## Technique 6 — Index-Based Traversal

```python
for i in range(len(numbers)):
    print(numbers[i])
```

Used when the **index** is required.

---

## Technique 7 — Recursion

```python
def solve(n):

    if n == 0:
        return

    solve(n - 1)
```

Used when a problem can be broken into smaller versions of itself.

---

# 31. Python Syntax Cheat Sheet

```python
# Variable
x = 10

# Input
x = int(input())

# Output
print(x)

# If
if x > 0:
    print("Positive")

# If / elif / else
if x > 0:
    print("Positive")
elif x < 0:
    print("Negative")
else:
    print("Zero")

# For loop
for i in range(1, 11):
    print(i)

# Reverse loop
for i in range(10, 0, -1):
    print(i)

# List
numbers = [10, 20, 30]

# List indexing
print(numbers[0])

# List length
len(numbers)

# Modulo
x % 2

# Power
x ** 3

# Integer division
x // 10

# Function
def add(a, b):
    return a + b
```

---

# 32. Problems Covered

| # | Concept |
|---|---|
| 1 | Negative range |
| 2 | `for` loop completion |
| 3 | Multiplication table |
| 4 | Cube |
| 5 | Odd indexes |
| 6 | Multiplication table |
| 7 | Accumulator / sum |
| 8 | FizzBuzz |
| 9 | Reverse list |
| 10 | Even/Odd |
| 11 | Even/Odd |
| 12 | Positive/Negative/Zero |
| 13 | Greatest of three |
| 14 | Leap year |
| 15 | Recursion |
| 16 | Reverse recursion |
| 17 | Multiplication table |
| 18 | Digit extraction |
| 19 | Conditional calculator |
| 20 | Input/Output |
| 21 | Multiple-line input |
| 22 | Swap numbers |

---

# 33. Main Learning Pattern

Most beginner programming problems can be broken into:

```text
INPUT
  ↓
PROCESS
  ↓
CONDITION / LOOP
  ↓
OUTPUT
```

Example:

```python
n = int(input())

total = 0

for i in range(1, n + 1):

    if i % 2 == 0:
        total += i

print(total)
```

Here:

```text
Input       → n
Loop        → for
Condition   → if
Modulo      → %
Accumulator → total
Output      → print()
```

This combination forms the foundation for DSA.

---

# 34. Important Note

Do not memorize the programs individually.

Learn the patterns:

```text
for + range()
if + elif + else
% → divisibility
total += value → accumulator
range(..., -1) → reverse traversal
list[index] → indexed access
function + base case → recursion
```

Once these patterns are understood, many beginner DSA problems become variations of the same techniques.
