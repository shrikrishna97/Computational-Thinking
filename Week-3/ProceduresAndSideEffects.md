## 1. Extracting Data from Cards into Tables 

### 1.1 The Mental Model: Physical Cards to Structured Tables

In Weeks 1 and 2, our computations operated on physical **piles of cards**.

* Each **card** represents a single **unit of information** (an entity/record).
  
* Each card possesses distinct **attributes** or **fields** (e.g., ID, Name, Marks).
  
* When we stack all identical-schema cards together, we naturally form a **dataset**, visualised as a **two-dimensional Table**:
  * **Columns** - Attributes / Fields.
  * **Rows** - Individual Cards / Records.
    

```
       Physical Cards Pile                     Tabular Dataset Representation
  ┌─────────────────────────┐               ┌───────┬─────────┬────────┬───────┐
  │ Card 10: Kavya, F, 204  │  ══════════>  │ Card  │  Name   │ Gender │ Total │
  ├─────────────────────────┤               ├───────┼─────────┼────────┼───────┤
  │ Card 24: Siddharth, M   │               │  10   │  Kavya  │   F    │  204  │
  ├─────────────────────────┤               │  24   │ Sidd... │   M    │  189  │
  │ Card 31: Ananya, F, 230 │               │  31   │ Ananya  │   F    │  230  │
  └─────────────────────────┘               └───────┴─────────┴────────┴───────┘
```

### 1.2 Dataset: Scores Table

Each row has a fixed, uniform set of columns:

| Card ID | Name | Gender | DoB | City | Mathematics | Physics | Chemistry | Total |
| :---: | :--- | :---: | :---: | :--- | :---: | :---: | :---: | :---: |
| **10** | Kavya | F | 12 Jan | Chennai | 64 | 72 | 68 | **204** |
| **24** | Siddharth | M | 26 Dec | Madurai | 44 | 60 | 85 | **189** |
| **31** | Ananya | F | 05 Aug | Coimbatore | 78 | 80 | 72 | **230** |
| **45** | Rahul | M | 19 Oct | Chennai | 82 | 65 | 71 | **218** |


### 1.3 The Real-World Challenge: Shopping Bills & Multi-Table Design
> **Important Question:**  
> *"What happens if a card contains a variable number of items, like a grocery shopping bill?"*

Consider a supermarket bill:
* Fixed header: `Bill ID`, `Shop Name`, `Customer Name`, `Bill Total`.
  
* Variable line items: Some customers buy 2 items; others buy 25 items!
  

#### > The Bad Design: Single Flat Table

If we attempt to flatten everything into one table:

| Bill ID | Shop | Customer | Item | Category | Qty | Price | Cost | Bill Total |
| :---: | :--- | :--- | :--- | :--- | :---: | :---: | :---: | :---: |
| **5** | Big Bazaar | Akshaya | Trousers | Apparel | 2 | 870 | 1740 | **4174** |
| **5** | Big Bazaar | Akshaya | Shirts | Apparel | 1 | 1350 | 1350 | **4174** |
| **5** | Big Bazaar | Akshaya | Detergent | Household | 0.5 | 270 | 135 | **4174** |
| **5** | Big Bazaar | Akshaya | T-Shirts | Apparel | 4 | 220 | 880 | **4174** |
| **5** | Big Bazaar | Akshaya | Noodles | Food | 3 | 23 | 69 | **4174** |

**Critical Flaws with the Flat Table:**
1. **Severe Data Redundancy:** `Shop`, `Customer`, and `Bill Total` are duplicated on every single row.
2. **Storage Inefficiency:** Storing duplicate strings over thousands of items wastes significant memory.

#### > The Clean Solution: Multiple Tables Linked by a Key

Split the dataset into **two relational tables** linked by a shared identifier (`Bill ID`):

**Table 1: Bill Summary (Fixed attributes per bill)**
| Bill ID | Shop | Customer | Total |
| :---: | :--- | :--- | :---: |
| **5** | Big Bazaar | Akshaya | 4174 |
| **6** | SV Stores | Srivatsan | 567 |

**Table 2: Bill Line Items (One row per purchased item)**
| Bill ID | Item | Category | Qty | Price | Cost |
| :---: | :--- | :--- | :---: | :---: | :---: |
| **5** | Trousers | Apparel | 2 | 870 | 1740 |
| **5** | Shirts | Apparel | 1 | 1350 | 1350 |
| **5** | Detergent | Household | 0.5 | 270 | 135 |
| **5** | T-Shirts | Apparel | 4 | 220 | 880 |
| **5** | Noodles | Food | 3 | 23 | 69 |
| **6** | Carrots | Vegetables | 1.5 | 50 | 75 |
| **6** | Soap | Toiletries | 4 | 32 | 128 |

> **Key Takeaway for Students:**  
> A shared identifier (like Bill ID) lets us link related tables without repeating data or wasting space


---


## 2. Procedures

### 2.1 Why Do We Need Procedures?
In Week 2, if we wanted to find:
1. Total marks scored by Boys in Mathematics,
2. Total marks scored by Girls in Chemistry,
3. Total marks scored by Boys in Physics...

We had to **copy-paste the entire while-loop three times**, merely swapping variable names.

* **Code Bloat:** 30 lines of repeated code.
* **Maintenance Nightmare:** If our iteration logic has a single issue, we must fix it in multiple places.

A **Procedure** is a named, reusable pseudocode template that performs a specific computation on inputs (**parameters**) and yields an output (**return value**).

### 2.2 Syntax & Structure of a Procedure

```plaintext
Procedure ProcedureName(param1, param2, ...)
    // 1. Local Initialization
    // 2. Core Computation / Loop
    return(result)
end ProcedureName
```

### 2.3 Example 1: Summing Marks with Value & Field Parameters

In this pseudocode, parameters can be:
1. **Values** (e.g., `'M'`, `'F'`).
2. **Field Names** (e.g., `Mathematics`, `Physics`, `Total`).

```plaintext
Procedure SumMarks(gen, fld)
    Sum = 0
    while (Pile 1 has more cards) {
        Pick a card X from Pile 1
        Move X to Pile 2
        if (X.Gender == gen) {
            Sum = Sum + X.fld        // fld is accessed on card X
        }
    }
    return(Sum)
end SumMarks
```

#### Calling the Procedure:

```plaintext
BoysMathSum  = SumMarks("M", Mathematics)
GirlsChemSum = SumMarks("F", Chemistry)
BoysTotalSum = SumMarks("M", Total)

OverallSum   = BoysMathSum + GirlsChemSum
```

---

### 2.4 Example 2: Comparative Analysis with `MaxMarks(fld)`

```plaintext
Procedure MaxMarks(fld)
    max = 0
    while (Pile 1 has more cards) {
        Pick a card X from Pile 1
        Move X to Pile 2
        if (X.fld > max) {
            max = X.fld
        }
    }
    return(max)
end MaxMarks
```

> Note: Now watch the lectures and solve Three Prize Problem with the above understanding. 


---

## 3. Side Effects in Procedures 

### 3.1 What is a Side Effect?
A **Side Effect** means that while a procedure is running, it makes changes to data **outside** the procedure itself.

### 3.2 Passing a Deck as a Third Parameter
In `SumMarks(gen, fld)`, we assumed the deck was always fixed (`Pile 1`).  
To make it work for any deck, we pass `Deck` as a third parameter:

```plaintext
Procedure SumMarks(gen, fld, Deck)
    Sum = 0
    while (Deck has more cards) {
        Pick a card X from Deck
        Move X to SeenDeck
        if (X.Gender == gen) {
            Sum = Sum + X.fld
        }
    }
    return(Sum)
end SumMarks
```

#### What happened to `Deck`?
* Cards moved from `Deck` to `SeenDeck`.
* At the end of the procedure, **`Deck` is empty!**
* This is an unintended side effect.
* Therefore, the procedure **must restore `Deck`** before returning:
  ```plaintext
  Restore Deck from SeenDeck
  return(Sum)
  ```

### 3.3 What About the Order of Cards?
* When cards are moved back from `SeenDeck` to `Deck`, `SeenDeck` is usually in **reverse order**.
* **Does disturbing the order matter?**
  * **For adding marks:** It does not matter! The sum of marks is the same in any order.
  * **When sorting:** Sometimes the side effect is the goal itself (for example, arranging cards in decreasing order of `Total`).
  * **For text and word cards:** Disturbing the order is very bad!


### 3.4 Case Study: Pronoun Resolution in Text

Consider the Words Dataset :

> *"It was Monday morning. Swaminathan was reluctant to open his eyes. He considered Monday specially unpleasant in the calendar..."*

#### The Goal:
* Fix a pronoun (for example, `"He"`).
* Search the text before the pronoun **backwards**.
* Stop at the nearest name (which is `"Swaminathan"`).

#### The Procedure: `FindMatch(before, pronoun, after)`
Notice that this procedure has **three parameters**:
1. `before` — the words appearing before the pronoun.
2. `pronoun` — the pronoun card we want to match (e.g., `"He"`).
3. `after` — the words appearing after the pronoun.

```
  [before: words before "He"]   ──>  [pronoun: "He"]  ──>  [after: words after "He"]
```

#### Why No Side Effects are Allowed Here:
* `FindMatch` must **not disturb `before` and `after`**.
* The sequence of words and their positions must stay **exactly the same**.
* If the procedure scrambles or reverses the word cards, the entire paragraph gets destroyed, and future word searches will fail!
* **Here, no side effects should happen.**

---

### 3.5 Summary of Side Effects

| Type of Side Effect | What it Means | Example |
| :--- | :--- | :--- |
| **No guarantee needed (Tolerable)** | Sequence may change slightly, but computation does not depend on order. | Adding up marks (`SumMarks`). |
| **No side effect tolerated (Avoid)** | Data and order must not be disturbed at all. | Pronoun matching (`FindMatch`). |
| **Desired side effect (Goal)** | Changing the data/order is the actual purpose of the procedure. | Sorting a deck in decreasing order of Total. |


---

## 4. Interface vs. Implementation 

### 4.1 The Architectural Contract

| Concept | What It Means | Analogy |
| :--- | :--- | :--- |
| **Interface** | **What** the procedure does, the parameters it takes, what it returns, and its "side-effect" guarantees. | A car's steering wheel, pedals, and gearstick. |
| **Implementation** | **How** the logic is written inside the procedure block. | The internal combustion engine or electric motor under the hood. |

```
                       ┌───────────────────────────────────────────────┐
                       │                   CALLER                      │
                       └──────────────────────┬────────────────────────┘
                                              │ Calls SumMarks("M", Maths)
                                              ▼
                       ┌───────────────────────────────────────────────┐
                       │          INTERFACE / CONTRACT                 │
                       │ Inputs: gen (Value), fld (Field)              │
                       │ Output: Integer Sum                           │
                       │ Guarantee: Pile 1 order & count restored      │
                       └──────────────────────┬────────────────────────┘
                                              │ Implementation details hidden
                                              ▼
                       ┌───────────────────────────────────────────────┐
                       │          INTERNAL IMPLEMENTATION              │
                       │ Can use while loop, recursion, temporary piles│
                       │ Can be optimized without breaking caller!     │
                       └───────────────────────────────────────────────┘
```

---



## 5. Quick Review Cheat Sheet

```
╔═════════════════════════════════════════════════════════════════════════════╗
║                             WEEK 3 CHEAT SHEET                              ║
╠═════════════════════════════════════════════════════════════════════════════╣
║ 1. Table Schema      : Cards = Rows, Attributes = Columns.                  ║
║ 2. Multi-Table Design: Avoid duplication of header data by linking tables   ║
║                        via unique keys (e.g., Bill ID).                     ║
║ 3. Procedure         : Reusable computational template with formal params   ║
║                        and a return value.                                  ║
║ 4. Parameters        : Can be values ("M") or field attributes (Total).     ║
║ 5. Interface         : The public contract (What inputs, outputs, rules).   ║
║ 6. Implementation    : The private internal code (How it's achieved).       ║
║ 7. Side Effects      : External state changes; must be intentional and      ║
║                        controlled.                                          ║
╚═════════════════════════════════════════════════════════════════════════════╝
```
