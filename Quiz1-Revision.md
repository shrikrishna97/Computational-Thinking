Sep 25 Term: [Mock quiz 1](https://seek.onlinedegree.iitm.ac.in/courses/ns_25t3_cs1001?id=393)


# **CT Quick Notes (Weeks 1 – 4)**

---

## **WEEK 1 — Datasets, Variables & Datatypes**

### 🔹 **Dataset**

* Structured collection of related data (records).
* Each record = fields (name + value).
* Examples: *Scores dataset, Shopping bill, Train records.*

---

### 🔹 **Variables**

* A name to store a value that can change.

  ```python
  marks = 95
  marks = 100
  ```
* **Constant variable:** fixed value (e.g., `MAX_MARKS = 100`)
* **Changing variable:** can update (e.g., `highestScore = 0`)

---

### 🔹 **Iterator**

* Accesses each record **one by one** from a dataset.
  **Steps:**

1. Initialize (pile 1 = unseen cards)
2. Pick one → process → move to pile 2
3. Repeat until done

---

### 🔹 **Filtering**

Select only those records that satisfy a condition.

```python
marks > 50
gender == 'F'
marks > 50 AND gender == 'F'
```

---

## 🔹 **Flowcharts**

| Symbol           | Meaning        |
| ---------------- | -------------- |
| Oval          | Start / End    |
| Rectangle      | Process        |
| Diamond       | Decision       |
| Parallelogram | Input / Output |
| Arrow         | Flow direction |

**Pros:** Easy to visualize, clear logic

**Cons:** Hard to modify for large programs

---

### 🔹 **Example: Total Maths Marks**

Steps:

1. Start
2. `Sum = 0`
3. Pick card from pile
4. Add Maths marks to Sum
5. Repeat till no cards left
6. End

---

### 🔹 **Sanity of Data**

* **Value restriction:** e.g., Marks ∈ [0, 100]
* **Operation restriction:** e.g., Names cannot be added.

---

### 🔹 **Data Types**

| Type      | Example       | Allowed Operations        |
| --------- | ------------- | ------------------------- |
| Boolean   | True/False    | AND, OR, NOT              |
| Integer   | 1, 2, 3       | +, -, *, /, <, >          |
| Character | 'A', 'B', '1' | Compare                   |
| String    | "Alice", "CS" | Membership, Concatenation |

---

### 🔹 **Subtypes**

| Subtype | Range    | Note            |
| ------- | -------- | --------------- |
| Marks   | 0–100    | Comparison only |
| Count   | 0, 1, 2… | No division     |
| Gender  | M/F      | Char type       |
| Name    | Strings  | Alphabetic      |

---

### 🔹 **Complex Data Types**

**Record (Struct):**
Stores multiple fields:

```python
Item = { itemName: "Milk", quantity: 2, unitPrice: 25.5, totalPrice: 51.0 }
```

**List:**
Sequence of similar records.

```python
ItemList = [Item1, Item2, Item3]
```

---

**Summary (Week 1):**

* Dataset = collection of records
* Flowchart = visual logic
* Datatypes define valid values
* Record = multiple fields
* List = sequence of similar elements

---

## **WEEK 2 — Flowcharts to Pseudocode**

### 🔹 **Flowchart**

Pictorial representation using process, decision, and terminal nodes.

**Pros:** Easy to read
**Cons:** Hard to edit/share

---

### 🔹 **Stepwise Text**

Written description of flowchart steps — bridge to pseudocode.

---

### 🔹 **Pseudocode**

Text form of algorithm, easy to modify & close to programming syntax.

**Examples:**

1. **Count Cards**

```plaintext
Count = 0
while (Pile 1 has more cards) {
    Pick card X
    Move X to Pile 2
    Count = Count + 1
}
```

2. **Sum of Maths Marks**

```plaintext
Sum = 0
while (Pile 1 has more cards) {
    Pick card X
    Move X to Pile 2
    Sum = Sum + X.Maths
}
```

3. **Boys’ Marks**

```plaintext
Sum = 0
while (Pile 1 has cards) {
    Pick x
    if (x.Gender == M)
        Sum = Sum + x.Maths
}
```

4. **Max Marks**

```plaintext
MaxM = 0
MaxCard = -1
while (Pile 1 has cards) {
    Pick x
    if (x.Maths > MaxM) {
        MaxM = x.Maths
        MaxCard = x.Id
    }
}
```

---

### 🔹 **Key Constructs**

| Concept     | Symbol        | Meaning        |
| ----------- | ------------- | -------------- |
| Assignment  | `=`           | Store value    |
| Comparison  | `==`          | Equality check |
| Conditional | `if` / `else` | Decision       |
| Iteration   | `while`       | Repetition     |

---

**Summary (Week 2):**

* Flowchart → Stepwise Text → Pseudocode → Real Code
* Pseudocode = structured logic
* Loops & conditions drive computation

---

## **WEEK 3 — Extracting Data & Procedures**

### 🔹 **Extracting Data from Cards**

* Each **card = unit of information**
* Has **attributes:** Card ID, Name, Gender, Subject Marks, Total
* Combine all cards → one **table (dataset)**

| Card ID | Name | Gender | Physics | Chemistry | Total |
| ------- | ---- | ------ | ------- | --------- | ----- |

---

### 🔹 **Procedures**

Reusable pseudocode templates for common computations.

* Used to **modularize** pseudocode (avoid repetition)
* **Parameters:** specify input context (value or field name)
* **Return value:** gives output of computation

**Example:**

```plaintext
SumMarks(M, Total)
GirlsChemSum = SumMarks(F, Chemistry)
UpdateMarks(17, Physics, 88)
```

**Key Idea:**
If a process is used repeatedly (e.g., summing marks), make it a **procedure**.

---

### 🔹 **Benefits of Procedures**

* Reuse logic across tasks
* Easier maintenance
* Improved readability
* Centralized updates (improve once → all benefit)

---

### 🔹 **Interface vs Implementation**

| Term               | Meaning                                                                   |
| ------------------ | ------------------------------------------------------------------------- |
| **Interface**      | The contract — what the procedure does, what inputs & outputs it expects. |
| **Implementation** | The actual code that performs the operation.                              |

**Interface includes:**

* Parameters to be passed
* Value returned
* Allowed side effects (if any)

**Implementation can change**, but interface must remain same for existing calls to work.

---

### 🔹 **Side Effects**

Changes in global data caused by procedure execution.

* **Allowed:** if predictable and needed (e.g., sort deck)
* **Avoid:** if computation should be pure (e.g., calculate marks)

**Examples:**

* No side effect: Sum of marks
* Tolerable side effect: Reverse a deck
* Desired side effect: Sort dataset

---

**Summary (Week 3):**

* Procedure = modular, reusable logic block
* Interface defines *what* it does; implementation defines *how*
* Keep track of parameters, return values, and side effects
* Reuse procedures for cleaner pseudocode

---

## **WEEK 4 — Nested Iterations & Binning**

### 🔹 **Nested Iteration**

Loop inside another loop → total iterations = outer × inner.

**Example:**

```python
for i in List1:
    for j in List2:
        # process pair (i, j)
```

| Concept   | Normal Iteration | Nested Iteration                |
| --------- | ---------------- | ------------------------------- |
| Loops     | One              | Two or more                     |
| Execution | N times          | N × M times                     |
| Use Case  | Simple dataset   | Pairwise comparison, matrix ops |

---

### 🔹 **Binning**

Grouping similar data values into ranges (bins) → reduces computation and noise.

**Steps:**

1. Sort data
2. Divide into equal bins
3. Process each bin

| Range  | Category  |
| ------ | --------- |
| 0–20   | Poor      |
| 21–40  | Average   |
| 41–60  | Good      |
| 61–80  | Very Good |
| 81–100 | Excellent |

---

### 🔹 **Comparison Reduction**

Without binning:

For N items:
```
Number of comparisons = 1/2 × N × (N - 1)
```

With K bins:

Total number of comparisons:
```
K × 1/2 × (N / K) × ((N / K) - 1) = 1/2 × N × ((N / K) - 1)
```

**Reduction factor:**
```
Factor of reduction = (1/2 × N × (N - 1)) / (1/2 × N × ((N / K) - 1))
                    = (N - 1) / ((N / K) - 1)
```

**Example:**
N = 9, K = 3 → Reduction factor = 4 → 36 comparisons → only 9 needed.

---

**Summary (Week 4):**

* Nested Iteration = loop inside loop
* Binning = group similar data to reduce work
* Reduces comparisons & simplifies analysis

---

# **Overall Summary (Weeks 1–4)**

| Topic            | Key Idea                                   |
| ---------------- | ------------------------------------------ |
| Dataset          | Collection of records                      |
| Variable         | Name for a data value                      |
| Flowchart        | Visual algorithm                           |
| Pseudocode       | Text-based logic                           |
| Procedure        | Reusable logic block                       |
| Interface        | Defines what a procedure expects & returns |
| Implementation   | Actual working of the procedure            |
| Nested Iteration | Loop within loop                           |
| Binning          | Grouping to reduce computation             |

---
