---

# **Week – 1 CT Course Notes**

---

## 1. Introduction to [Datasets](https://drive.google.com/drive/folders/1JBRSlac2hxKgfYLcoII7pGEd8g3fFi_q)

* A **dataset** is a structured collection of data.
* A dataset is usually made of **records**, and each record consists of **fields** (with names and values).
* Example datasets:

  * **Scores** – records of students’ marks
  * **Paragraph Words** – records of words in a paragraph
  * **Shopping Bill** – records of items purchased
  * **Train** - records of train
    
---

## 2. Concept of Variables, Iterators, and Filtering

### Variables

* A **variable** is a name given to a value. And this keeps on changing as the computaion goes on.
  
  Example:
  `marks = 95
  `
  
   `marks = 100
  `

---
  
 ## Extra: **Constant vs Changing Variable: Exam Marks Processing**

### 1. Constant Variable

A **constant variable** is one whose value does **not change** during computation.

**Example:**

```
MAX_MARKS = 100
```

* This represents the maximum marks a student can score in the exam.
* No matter how many students we process, `MAX_MARKS` will always stay `100`.

---

### 2. Changing Variable

A **changing variable** is one whose value **keeps changing** as computation proceeds.

**Example:**

```
highestScore = 0
```

* Initially set to 0.
* As we go through the list of student marks, we update `highestScore` if we find a student with more marks.

---


### Iterators

* An **iterator** is a variable that allows traversal( repetition ) through elements of a dataset, one by one.
  
  Example: moving through each student’s marks in a `Scores` DataSet.

### Filtering

* **Filtering** is applying conditions to select only required records.
  
  Example: Select students with `marks > 50`.
  
### Description of the Iterator

1. **Initialization step**: Arrange all the cards in an “unseen” pile.
2. **Continue or Exit**: If there are no more cards in the unseen pile, we exit; otherwise, we continue.
3. **Repeat step**: Pick an element from the unseen pile, perform the required operation, and then move it to another “seen” pile.
4. **Go back** to Step 2.  

---

## 3. Iterations Using Combination of Filtering Conditions

* Iteration = **repeated traversal** over dataset elements.
  
* Filtering conditions may be combined with logical operators:

  * `AND`, `OR`, `NOT`
    
* Example:
  Select students such that
  `marks > 50 AND gender = 'F'`

---

 ## 4. Introduction to Flowcharts

  ### What is a Flowchart?
  
  * A flowchart is a graphical representation of an algorithm.
  * Used by programmers as a program-planning tool to solve problems.
  * Consists of symbols connected with arrows to show the flow of data and processing.
  * The process of drawing a flowchart is called *flowcharting*.
  
  ### Commonly Used Symbols
  
  | Symbol                       | Purpose                        | Description                                   |
  | ---------------------------- | ------------------------------ | --------------------------------------------- |
  | Rectangle (Process/Activity) | Represents a set of operations | Used for arithmetic or data processing steps. |
  | Arrow (Flowline)             | Shows order of execution       | Indicates flow of control.                    |
  | Diamond (Decision)           | Represents a decision point    | Determines which path the program will take.  |
  | Oval (Terminal)              | Start or End                   | Indicates beginning or end of program.        |
  | Parallelogram (Input/Output) | Input/Output                   | Input from devices or output to screen.       |
  | Circle (Connector)           | Continuation                   | Used when flowchart spans multiple pages.     |
  
  ---
  ### Pictorial View
  <img width="988" height="538" alt="image" src="https://github.com/user-attachments/assets/c420bab0-ff07-4015-8d00-5d93c3fe137a" />


  ### Advantages of Flowcharts
  
  * Easy to communicate the logic of a system.
  * Acts as a guide or blueprint during program design.
  * Helps in debugging process.
  * Makes analysis of programs easier.
  * Provides better documentation.
  
  ### Disadvantages of Flowcharts
  
  * Difficult to draw for large and complex programs.
  * No standard for determining level of detail.
  * Difficult to reproduce.
  * Difficult to modify once drawn.
  
  ---

## 5. Flowchart Example

**Task:** Find total maths marks of all students from a record sheet.

**Steps (Flowchart Logic):**

1. Start.
2. Initialize `Sum = 0`.
3. Check if there are cards in Pile 1.

   * If no → End.
   * If yes → Pick a card X from Pile 1.
4. Move X to Pile 2.
5. Add card X’s Maths score to Sum.
6. Go back to Step 3.

**Modifications( You can try ):**

* If we need only boys’ marks.
* If we need only girls’ marks.
* If we need boys’ and girls’ marks separately.

<img width="1013" height="577" alt="image" src="https://github.com/user-attachments/assets/790c4294-202b-43f6-be65-467958173fa5" />

---

## 6. Sanity of Data

* Data is organized into cards, each storing one data item.
* Each card can have multiple elements:

  * Numbers (e.g., marks)
  * Sequence of characters (e.g., name, bill item)

### Observations

* Restrictions on values:

  * Marks must lie between 0 and 100.
  * Names cannot contain invalid characters.

* Constraints on operations:

  * Addition of marks is possible, but multiplication may not make sense.
  * Names can be compared (e.g., one name with another → Boolean True/False).
  * Names cannot be added together.

---

## 7. Introduction to Datatypes

### Concept of Data Types

* By associating a **data type** with a data element, we define:
* When we specify a variable’s type, we describe constraints on the values it can store and the valid operations.

* **Datatype** defines:

  * The **values** a variable can take
  * The **operations** that can be applied

### Basic Data Types

1. **Boolean**

   * Values: True or False
   * Operations: AND, OR, NOT
   * Result type: Boolean

2. **Integer**

   * Values: … -3, -2, -1, 0, 1, 2, 3 …
   * Operations: +, -, \*, /, <, >, %
   * Result type: Integer or Boolean

3. **Character**

   * Values: Alphanumeric (A–Z, a–z, 0–9)
   * Special characters: , . ; ’ " / & % \$ # @ !
   * Operations: Limited (comparisons possible)
   * Result type: Boolean

4. **String**

   * Values: Any sequence of characters
   * Operations: Membership test (e.g., `char in string?`)
   * Result type: Boolean


---

## 8. Subtypes of Basic Datatypes

### (a) Marks

* Range: `0, 1, 2, … 100`
* Operations: `=`, `<`, `>`
* Result type:

  * Marks
  * Boolean

---

### (b) Count

* Range: `0, 1, 2, …`
* Operations: `=`, `<`, `>`
* Result type:

  * Count
  * Boolean
* Arithmetic (`* /`) does **not** make sense for count.

---

### (c) Gender (Subtype of Character)

* Values: `M` or `F`
* Operations: `=`
* Result type: Boolean

---

### (d) String Subtypes

* **Names** → strings without special characters (e.g., city names)
* **Words** → strings with alphanumeric + `. , ;`
* **Category** → limited set of values (e.g., `"Noun"`, `"Verb"`, `"Adjective"`)

---

## 9. Transformation of Sub-datatypes

### (a) Date (Subtype of Integer)

* Range: `0 … 365`
* Base values:

  * `0 = 1 Jan`
  * `1 = 2 Jan`
  * `31 = 1 Feb`
* Operations:

  * `print(date)` → String
  * `<`, `>` → Boolean
* Example:

  * `print(0)` = `"1 Jan"`
  * `print(31)` = `"1 Feb"`

---

### (b) Fractional Marks

* Represented by **Float** datatype (real numbers).
* Constraint: usually up to **2 decimal places** (e.g., 76.05).
* Alternative representation:

  * Multiply by 100 when storing → becomes integer
  * Divide by 100 when printing → restores decimal
* Example:

  * Store `62.5` as `6250`
  * `print(6250)` → `"62.5"`

---

## 10. Introduction to Complex Datatypes

### (a) Record (Struct / Tuple)

* A datatype with **multiple fields**, each with:

  * Name
  * Value
  * Datatype specification
* Ensures **sanity** of individual fields.
  
**Example: Item Record**

| Field        | Datatype | Example Value |
| ------------ | -------- | ------------- |
| `itemName`   | String   | `"Milk"`      |
| `quantity`   | Integer  | `2`           |
| `unitPrice`  | Float    | `25.50`       |
| `totalPrice` | Float    | `51.00`       |

So, one **Item Record** looks like:

```
Item = { itemName: "Milk", quantity: 2, unitPrice: 25.50, totalPrice: 51.00 }
```

This is a **Record** datatype.

---

### (b) List

* A **sequence of elements**, usually of the same datatype.
* Examples:

  * **ScoresList** → list of `Scores` records
  * **ParagraphWordsList** → list of `WordInPara` records
  * **ShoppingBillList** → list of `Item` records
 
Here, our shopping bill will be a **List of Item Records**.

**Example: ItemList (List of Items)**

```
ItemList = [
    { itemName: "Milk", quantity: 2, unitPrice: 25.50, totalPrice: 51.00 },
    { itemName: "Bread", quantity: 1, unitPrice: 30.00, totalPrice: 30.00 },
    { itemName: "Eggs", quantity: 12, unitPrice: 6.00, totalPrice: 72.00 }
]
```

Now, let’s define the **ShoppingBill Record**.
This is another **Record**, but one of its fields is itself a **List** of items.

| Field        | Datatype   | Example Value |
| ------------ | ---------- | ------------- |
| `billNo`     | Integer    | `101`         |
| `customer`   | String     | `"Alice"`     |
| `date`       | Date       | `"12 Sep"`    |
| `items`      | List(Item) | `ItemList`    |
| `grandTotal` | Float      | `153.00`      |

**Example: ShoppingBill Record**

```
ShoppingBill = {
    billNo: 101,
    customer: "Alice",
    date: "12 Sep",
    items: [
        { itemName: "Milk", quantity: 2, unitPrice: 25.50, totalPrice: 51.00 },
        { itemName: "Bread", quantity: 1, unitPrice: 30.00, totalPrice: 30.00 },
        { itemName: "Eggs", quantity: 12, unitPrice: 6.00, totalPrice: 72.00 }
    ],
    grandTotal: 153.00
}
```

---
**List of Shopping Bills**

Finally, a supermarket will have **many shopping bills**.
So we define a **ShoppingBillList**, which is a **List of ShoppingBill Records**.

**Example: ShoppingBillList**

```
ShoppingBillList = [
    {
        billNo: 101,
        customer: "Alice",
        date: "12 Sep",
        items: [
            { itemName: "Milk", quantity: 2, unitPrice: 25.50, totalPrice: 51.00 },
            { itemName: "Bread", quantity: 1, unitPrice: 30.00, totalPrice: 30.00 },
            { itemName: "Eggs", quantity: 12, unitPrice: 6.00, totalPrice: 72.00 }
        ],
        grandTotal: 153.00
    },
    {
        billNo: 102,
        customer: "Bob",
        date: "13 Sep",
        items: [
            { itemName: "Rice", quantity: 5, unitPrice: 40.00, totalPrice: 200.00 },
            { itemName: "Oil", quantity: 1, unitPrice: 120.00, totalPrice: 120.00 }
        ],
        grandTotal: 320.00
    }
]
```

---
**Note:**

1. **Record Datatype** = Collection of fields.

   * Example: `Item` with `itemName`, `quantity`, `unitPrice`, `totalPrice`.

2. **List Datatype** = Sequence of elements of the same type.

   * Example: `ItemList` = list of multiple `Item` Records.

3. **Nested Datatypes**:

   * A **ShoppingBill Record** contains a field `items` which is a **List of Item Records**.
   * A **ShoppingBillList** is a list of **ShoppingBill Records**.

---

## **Summary**

* A datatype defines valid **values** and **operations**.
* **Basic datatypes**: Integer, Boolean, Character, String.
* **Subtypes** restrict ranges and permitted operations (e.g., Marks, Count, Gender).
* **Transformations** allow mapping between integer/float and human-readable formats (e.g., Date, Fractional marks).
* **Record**: collection of named fields (possibly different datatypes or sometimes same).
* **List**: sequence of elements of the same datatype, enabling representation of datasets.

---




