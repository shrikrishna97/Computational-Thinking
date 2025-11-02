# **Week 6 – Lists: Sorting & Hypothesis Testing**

---

## **1. Arranging Lists in Order (Sorting)**

### **Why Sort a List?**

Sorting often makes later computations easier:

* Finding **top k** values
* Detecting **duplicates**
* **Grouping** data by percentiles (top quarter, next quarter, etc.)

Many efficient sorting algorithms exist.
We begin with a simple, intuitive one — **Insertion Sort**.

---

### **Idea of Insertion Sort**

We construct a **second, sorted list**:

1. Start with an **empty** list.
2. Take the next value from the original list.
3. **Insert** it into the correct position in the second (sorted) list.
4. Repeat until all elements are inserted.

---

## **2. Inserting into a Sorted List**

We have a list `l` (sorted in ascending order) and want to insert a new element `x` so that the order remains correct.

### **Logic**

* Move items from `l` into a new list until we find where `x` belongs.
* Insert `x`.
* Copy the remaining elements.
* Handle **boundary cases** carefully:

  * `l` is empty
  * `x` is smaller than all elements
  * `x` is larger than all elements

---

### **Pseudocode – SortedListInsert**

```text
Procedure SortedListInsert(l, x)
    newList = []
    inserted = False
    foreach z in l {
        if (not(inserted)) {
            if (x < z) {
                newList = newList ++ [x]
                inserted = True
            }
        }
        newList = newList ++ [z]
    }
    if (not(inserted)) {
        newList = newList ++ [x]
    }
    return(newList)
End SortedListInsert
```

---

## **3. Insertion Sort Algorithm**

Once insertion is defined, **sorting** becomes simple.

### **Algorithm**

1. Start with an empty `sortedList`.
2. For every element `z` in the original list `l`, insert `z` into `sortedList` using `SortedListInsert`.
3. Return `sortedList`.

---

### **Pseudocode – InsertionSort**

```text
Procedure InsertionSort(l)
    sortedList = []
    foreach z in l {
        sortedList = SortedListInsert(sortedList, z)
    }
    return(sortedList)
End InsertionSort
```

---

### **Key Property (Invariant)**

> At every stage, the `sortedList` remains sorted.

* Empty list `[]` is sorted.
* Inserting into a sorted list produces a sorted list.

---

## **4. Summary of Sorting Concepts**

| Concept              | Description                                        |
| -------------------- | -------------------------------------------------- |
| **Sorting**          | Arranging items in increasing or decreasing order  |
| **Insertion Sort**   | Repeatedly insert each item into a new sorted list |
| **Assumption**       | List sorted in **ascending** order                 |
| **Descending order** | Reverse the comparison condition                   |

---

# **Let’s Understand Hypothesis and Hypothesis Testing**

### **Definition: Hypothesis**

A **hypothesis** is an **assumption or prediction** made about a situation or data that we want to verify through reasoning or testing.
It is like a **guess** based on limited information that we later check using evidence or computation.

**Example:**

> “Students who score high in Mathematics will also score high in Physics.”
> This is a *hypothesis* — an assumption that we can test using data.

---

### **Definition: Hypothesis Testing**

**Hypothesis testing** is the **process of checking** whether a hypothesis is **true or false** using available data and logical reasoning (algorithms).

**Steps in Computational Thinking:**

1. **Formulate** a hypothesis (the assumption to test).
2. **Collect and analyze** data using computational tools like lists, sorting, and comparisons.
3. **Confirm or reject** the hypothesis based on observed results.

---

### **Example**

Suppose we have:

```text
Math = [40, 60, 70, 80, 90]
Physics = [42, 65, 72, 85, 88]
```

**Hypothesis:**
Students good in Maths are also good in Physics.

We can **test** this by comparing the ranks or grades.
If they largely match, the hypothesis is **supported**; otherwise, it is **rejected**.

---

### **In short**

| Term                   | Meaning                                                          |
| ---------------------- | ---------------------------------------------------------------- |
| **Hypothesis**         | A statement or assumption to be tested                           |
| **Hypothesis Testing** | The computational process of verifying that statement using data |

---

## **5. Correlating Marks in Mathematics and Physics**

### **Goal**

To **test the hypothesis**:

> “Students who perform well in Mathematics perform **at least as well** in Physics.”

---

### **Data Representation**

* Students receive grades **{A, B, C, D}** in both subjects.
* “Perform well in Maths” → Grade **B or above**.
* “At least as well in Physics” → Physics grade ≥ Maths grade.

---

## **Extracting and Sorting Student Marks**

Each record = `[StudentId, Marks]`

We need to build two lists — one for **Maths** and one for **Physics**.

### **Procedure – BuildMarksList**

```text
Procedure BuildMarksList(field)
    marksList = []
    while (Table1 has more rows) {
        Read the first row X in Table1
        marksList = marksList ++ [[X.SeqNo, X.field]]
        Move X to Table2
    }
    return(marksList)
End BuildMarksList
```

Then:

```text
mathsList = BuildMarksList(Mathematics)
physicsList = BuildMarksList(Physics)
```

---

## **Sorting Student Records by Marks**

Use **Insertion Sort** to sort both lists.
Each list item is `[id, marks]`, so comparison must be based on **marks** (the second value).

### **Modified SortedListInsert**

```text
Procedure SortedListInsert(l, x)
    newList = []
    inserted = False
    foreach z in l {
        if (not(inserted)) {
            if (last(x) < last(z)) {
                newList = newList ++ [x]
                inserted = True
            }
        }
        newList = newList ++ [z]
    }
    if (not(inserted)) {
        newList = newList ++ [x]
    }
    return(newList)
End SortedListInsert
```

---

### **Helper Functions**

| Function   | Description      | Example                     |
| ---------- | ---------------- | --------------------------- |
| `first(l)` | first element    | `first([1,2,3,4]) = 1`      |
| `last(l)`  | last element     | `last([1,2,3,4]) = 4`       |
| `rest(l)`  | all except first | `rest([1,2,3,4]) = [2,3,4]` |
| `init(l)`  | all except last  | `init([1,2,3,4]) = [1,2,3]` |

---

## **Assigning Grades Using Quartiles**

We divide the sorted list into **four parts**:
A (top 25%), B (next 25%), C (next 25%), D (bottom 25%).

### **Procedure – SimpleGradeAssignment**

```text
Procedure SimpleGradeAssignment(l)
    q4 = classSize/4, q3 = classSize/2, q2 = 3*classSize/4
    gradeA, gradeB, gradeC, gradeD = [], [], [], []
    position = 0
    foreach x in l {
        if (position > q2) {
            gradeA = gradeA ++ [first(x)]
        }
        if (position > q3 and position <= q2) {
            gradeB = gradeB ++ [first(x)]
        }
        if (position > q4 and position <= q3) {
            gradeC = gradeC ++ [first(x)]
        }
        if (position <= q4) {
            gradeD = gradeD ++ [first(x)]
        }
        position = position + 1
    }
    return([gradeA, gradeB, gradeC, gradeD])
End SimpleGradeAssignment
```

---

### **Assigning Grades for Each Subject**

```text
mathsGrades   = SimpleGradeAssignment(sortedMathsList)
physicsGrades = SimpleGradeAssignment(sortedPhysicsList)

mathsAGrades = first(mathsGrades)
mathsBGrades = first(rest(mathsGrades))
mathsCGrades = last(init(mathsGrades))
mathsDGrades = last(mathsGrades)

physicsAGrades = first(physicsGrades)
physicsBGrades = first(rest(physicsGrades))
physicsCGrades = last(init(physicsGrades))
physicsDGrades = last(physicsGrades)
```

---

## **Testing the Hypothesis**

Check how many students with high Maths grades (A or B) also perform **at least as well** in Physics.

### **Pseudocode**

```text
foreach x in mathsBGrades {
    found = False
    foreach y in physicsAGrades {
        if (x == y) {
            confirm = confirm ++ [x]
            found = True
            exitloop
        }
    }
    if (not(found)) {
        foreach y in physicsBGrades {
            if (x == y) {
                confirm = confirm ++ [x]
                found = True
                exitloop
            }
        }
    }
    if (not(found)) {
        reject = reject ++ [x]
    }
}
```

After checking both A and B lists:

```text
if length(confirm) / (length(confirm) + length(reject)) is high,
the hypothesis is supported.
```

---

## **6. Final Summary**

| Concept                 | Description                                                         |
| ----------------------- | ------------------------------------------------------------------- |
| **Sorting**             | Organizes data and helps identify quartiles                         |
| **Insertion Sort**      | Builds a sorted list by inserting each element in order             |
| **Modified Comparison** | Compare marks when sorting `[id, marks]` pairs                      |
| **List Functions**      | `first`, `last`, `rest`, `init` help extract data from lists        |
| **Grade Assignment**    | Divides data into quartiles (A, B, C, D)                            |
| **Hypothesis Testing**  | Checks if strong Maths students perform at least as well in Physics |
| **exitloop**            | Used to stop a `foreach` loop early                                 |

---

