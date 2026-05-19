# UCF Assisted Learnubg Lab Python Loops, Bv Victor S, Based on Python 2. Maybe compatible with future Verisions |Updated from 2011-2026 by Victor S|

# Printing Patterns with Nested Loops in Python

A short guide. Each section shows the pattern, the code, and a brief note on what's happening.

---

## The basic idea

A pattern is rows and columns of characters. You need two loops: one for the rows, one for the columns inside each row.

The outer loop walks down the pattern row by row. The inner loop builds each row character by character. After the inner loop finishes one row, you print a newline and the outer loop moves to the next row.

---

## Pattern 1: Solid square

```
* * * * *
* * * * *
* * * * *
* * * * *
* * * * *
```

Code:

```python
size = 5
for row in range(size):
    for col in range(size):
        print("*", end=" ")
    print()
```

The outer loop runs `size` times, once per row. The inner loop runs `size` times per row, printing a `*` each iteration. `end=" "` keeps the cursor on the same line with a space after each character. `print()` at the end of the outer loop prints a newline and moves to the next row.

---

## Pattern 2: Right triangle (increasing)

```
*
* *
* * *
* * * *
* * * * *
```

Code:

```python
size = 5
for row in range(size):
    for col in range(row + 1):
        print("*", end=" ")
    print()
```

The inner loop's range now depends on `row`. Row 0 prints 1 star, row 1 prints 2, and so on. This is the key trick: the inner loop's count is a function of the outer loop's counter.

---

## Pattern 3: Right triangle (decreasing)

```
* * * * *
* * * *
* * *
* *
*
```

Code:

```python
size = 5
for row in range(size):
    for col in range(size - row):
        print("*", end=" ")
    print()
```

Same trick as before, just reversed. Row 0 prints `size - 0 = 5` stars; row 4 prints `size - 4 = 1` star.

---

## Pattern 4: Centered pyramid

```
        *
      * * *
    * * * * *
  * * * * * * *
* * * * * * * * *
```

Code:

```python
size = 5
for row in range(size):
    for space in range(size - row - 1):
        print(" ", end=" ")
    for col in range(2 * row + 1):
        print("*", end=" ")
    print()
```

Two inner loops, run one after the other. The first prints leading spaces; the second prints stars. The number of stars per row is `2 * row + 1` (1, 3, 5, 7, 9), which produces the odd-number sequence that makes the pyramid centered.

---

## Pattern 5: Inverted pyramid

```
* * * * * * * * *
  * * * * * * *
    * * * * *
      * * *
        *
```

Code:

```python
size = 5
for row in range(size):
    for space in range(row):
        print(" ", end=" ")
    for col in range(2 * (size - row) - 1):
        print("*", end=" ")
    print()
```

Same structure as the pyramid, with the spaces and stars formulas inverted. Spaces increase as rows go down; stars decrease.

---

## Pattern 6: Number triangle

```
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
```

Code:

```python
size = 5
for row in range(size):
    for col in range(row + 1):
        print(col + 1, end=" ")
    print()
```

Same shape as Pattern 2, but instead of printing `*`, print the loop counter `col + 1`. The `+ 1` is because `range` starts at 0 and we want to start at 1.

---

## Pattern 7: Multiplication table

```
1   2   3   4   5
2   4   6   8   10
3   6   9   12  15
4   8   12  16  20
5   10  15  20  25
```

Code:

```python
size = 5
for row in range(1, size + 1):
    for col in range(1, size + 1):
        print(f"{row * col:<4}", end="")
    print()
```

The value printed depends on both loop counters: `row * col`. `f"{row * col:<4}"` left-pads each number to 4 characters so the columns line up.

---

## The pattern behind the patterns

Every nested-loop pattern follows the same recipe:

1. The **outer loop** controls rows. It runs once per row.
2. The **inner loop(s)** build each row. The count and content depend on which row you're on.
3. The relationship between the outer counter and the inner loop is where the shape comes from. Constant inner range gives a rectangle. Inner range tied to outer counter gives a triangle.
4. `print(..., end=" ")` keeps things on one line. Plain `print()` ends the row.

Once you see the recipe, every pattern is a variation on it.

---

If you have any questions, or want [other examples](https://github.com/DatJavaClass/UCFCECS_ALL_PYTHON_LOOPS.git) please reach out to DatJavaClass or Victor S. On Slack
