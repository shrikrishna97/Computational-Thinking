# **Week 5 - Introducing Lists & List Operations**

---

## 1. Introducing Lists

### 1.1 Why Do We Need Collections?
Up to now, our variables could only hold a single value at a time (like `count = 0`, `max = 0`, or `Sum = 0`).

However, in many real situations, we need to keep track of a **collection of values**:
* List of students with highest marks in Physics.
* List of customers who bought food items from SV Stores.
* List of nouns that follow an adjective in a text.

The simplest collection is a **List**:
* A list is an ordered **sequence of values**.
* A single variable name refers to the entire sequence.

---

### 1.2 Notation and Basic Operations

1. **Writing a list:** Written inside square brackets separated by commas.
  * `[1, 13, 2]` (numbers)
  * `["Vedanayagam", "cane", "Monday", "school"]` (words/strings)
  * `[]` represents an **empty list** (a list with 0 items).

2. **Appending two lists (`++`):**
  * If `l1` is `[1, 13]` and `l2` is `[2, 17, 1]`, then:
    `l1 ++ l2` is `[1, 13, 2, 17, 1]`

3. **Extending a list with a single item `x`:**
  * To add item `x` to the end of list `l`, put `x` inside brackets and append:
    `l = l ++ [x]`

---

### 1.3 Constructing Lists from Tables

#### Example 1: Students born in May
```plaintext
mayList = []
while (Table 1 has more rows) {
    Read the first row X in Table 1
    if (X.MonthOfBirth == "May") {
        mayList = mayList ++ [X.Seqno]
    }
    Move X to Table 2
}
```

#### Example 2: Students from Chennai
```plaintext
chennaiList = []
while (Table 1 has more rows) {
    Read the first row X in Table 1
    if (X.TownCity == "Chennai") {
        chennaiList = chennaiList ++ [X.Seqno]
    }
    Move X to Table 2
}
```

---

### 1.4 Iterating Over Lists with `foreach`

To process each element of a list, we use the `foreach` loop:

```plaintext
foreach x in l {
    // Do something with x
}
```
* `x` takes each value in the list `l` one by one, from left to right.

#### Finding Common Elements (Nested `foreach`):
Suppose we want to find all students who were **born in May AND are from Chennai**:

```plaintext
mayChennaiList = []
foreach x in mayList {
    foreach y in chennaiList {
        if (x == y) {
            mayChennaiList = mayChennaiList ++ [x]
        }
    }
}
```

---

## 2. Operations on Data Using Lists: Top Students Example

### 2.1 Problem: Finding Overall Toppers Across All Subjects
We want to find students who are doing well in **all three subjects** (Mathematics, Physics, Chemistry):
* A student is a topper in a subject if their mark is >= the third highest mark in that subject.
* Goal: Find students who are in the top three across **all three subjects**.

### 2.2 Step 1: Constructing the Subject Topper Lists
We first find the cutoff mark for each subject using `TopThreeMarks(Subj)` (from Week 3), then collect student IDs into subject lists:

```plaintext
cutoffMaths = TopThreeMarks(Mathematics)
cutoffPhys  = TopThreeMarks(Physics)
cutoffChem  = TopThreeMarks(Chemistry)

mathsList = []
physList  = []
chemList  = []

while (Table 1 has more rows) {
    Read the first row X in Table 1
    if (X.Mathematics >= cutoffMaths) {
        mathsList = mathsList ++ [X.SeqNo]
    }
    if (X.Physics >= cutoffPhys) {
        physList = physList ++ [X.SeqNo]
    }
    if (X.Chemistry >= cutoffChem) {
        chemList = chemList ++ [X.SeqNo]
    }
    Move X to Table 2
}
```

---

### 2.3 Step 2: Finding Common Students Across All Three Lists

We do this in two stages using nested iteration:

#### Stage A: Common between Maths and Physics
```plaintext
mathsPhysList = []
foreach x in mathsList {
    foreach y in physList {
        if (x == y) {
            mathsPhysList = mathsPhysList ++ [x]
        }
    }
}
```

#### Stage B: Common between (Maths & Physics) and Chemistry
```plaintext
mathsPhysChemList = []
foreach x in mathsPhysList {
    foreach y in chemList {
        if (x == y) {
            mathsPhysChemList = mathsPhysChemList ++ [x]
        }
    }
}
```

> **General Rule for Combining Multiple Lists:**
> If we have 4 lists (`list1`, `list2`, `list3`, `list4`):
> 1. Combine `list1` and `list2` -> `list12`
> 2. Combine `list3` and `list4` -> `list34`
> 3. Combine `list12` and `list34` -> common items across all 4 lists.

---

## 3. Standard List Functions (Tutorial 5.1)

Below are the 6 fundamental list procedures, their definitions, examples, and pseudocode implementations.

---

### 3.1 `length(l)`
Counts the total number of elements in list `l`.

* **Example:** `length([20, 30, 40, 50, 10])` is `5`
* **Pseudocode:**
```plaintext
length(l) {
    count = 0
    foreach x in l {
        count = count + 1
    }
    return(count)
}
```

---

### 3.2 `first(l)`
Returns the first element of list `l`.

* **Example:** `first([20, 30, 40, 50, 10])` is `20`
* **Pseudocode:**
```plaintext
first(l) {
    foreach x in l {
        return(x)
    }
}
```
*(Notice: The `return(x)` statement runs on the very first iteration, immediately exiting with the first element!)*

---

### 3.3 `last(l)`
Returns the last element of list `l`.

* **Example:** `last([20, 30, 40, 50, 10])` is `10`
* **Pseudocode:**
```plaintext
last(l) {
    foreach x in l {
        e = x
    }
    return(e)
}
```
*(Notice: `e` only keeps track of the last item seen. When the loop finishes, `e` holds the final element.)*

---

### 3.4 `rest(l)`
Returns a new list containing all elements of `l` **except the first element**.

* **Example:** `rest([20, 30, 40, 50, 10])` is `[30, 40, 50, 10]`
* **Pseudocode:**
```plaintext
rest(l) {
    found = False
    restList = []
    foreach x in l {
        if (found) {
            restList = restList ++ [x]
        }
        else {
            found = True
        }
    }
    return(restList)
}
```
*(How it works: For the first item, `found` is `False`, so it skips appending and sets `found = True`. For all remaining items, `found` is `True`, so they are appended.)*

---

### 3.5 `init(l)`
Returns a new list containing all elements of `l` **except the last element**.

* **Example:** `init([20, 30, 40, 50, 10])` is `[20, 30, 40, 50]`
* **Pseudocode:**
```plaintext
init(l) {
    found = False
    initList = []
    foreach x in l {
        if (found) {
            initList = initList ++ [prev]
        }
        else {
            found = True
        }
        prev = x
    }
    return(initList)
}
```
*(How it works: We delay appending each element by one step using `prev`. The last element is stored into `prev`, but the loop ends before it can be appended!)*

---

### 3.6 `member(l, e)`
Checks if an element `e` is present in list `l`. Returns `True` if found, `False` otherwise.

* **Example:**
* `member([20, 30, 40, 50], 30)` is `True`
* `member([20, 30, 40, 50], 10)` is `False`

* **Pseudocode:**
```plaintext
member(l, e) {
    foreach x in l {
        if (e == x) {
            return(True)
        }
    }
    return(False)
}
```

---

## 4. Quick Review Cheat Sheet

```
+----------------------------------------------------------------------------+
|                         LISTS (WEEK 5) CHEAT SHEET                         |
+----------------------------------------------------------------------------+
| 1. List               : Ordered sequence of values in [x1, x2, ..., xn].     |
| 2. Empty List         : [] (a list with no elements).                       |
| 3. Combine Lists      : l1 ++ l2 merges two lists together.               |
| 4. Add One Element    : l = l ++ [x] appends item x to list l.               |
| 5. Loop over List     : foreach x in l { ... } visits every item.           |
| 6. Common Elements    : Use nested foreach loops to find matching items.    |
| 7. List Functions     :                                                     |
|    * length(l)        : Total count of elements in l.                       |
|    * first(l)         : Returns the first element.                         |
|    * last(l)          : Returns the last element.                          |
|    * rest(l)          : List of all elements except the first.              |
|    * init(l)          : List of all elements except the last.               |
|    * member(l, e)     : Returns True if element e is in list l.             |
+----------------------------------------------------------------------------+
```
