---

# **Week – 1 CT Course Notes**

---

## 1. Introduction to Datasets

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

**Modifications:**

* If we need only boys’ marks.
* If we need only girls’ marks.
* If we need boys’ and girls’ marks separately.

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
* Arithmetic (`+ - * /`) does **not** make sense for count.

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

---

### (b) List

* A **sequence of elements**, usually of the same datatype.
* Examples:

  * **ScoresList** → list of `Scores` records
  * **ParagraphWordsList** → list of `WordInPara` records
  * **ShoppingBillList** → list of `Item` records

---

## **Summary**

* A datatype defines valid **values** and **operations**.
* **Basic datatypes**: Integer, Boolean, Character, String.
* **Subtypes** restrict ranges and permitted operations (e.g., Marks, Count, Gender).
* **Transformations** allow mapping between integer/float and human-readable formats (e.g., Date, Fractional marks).
* **Record**: collection of named fields (possibly different datatypes).
* **List**: sequence of elements of the same datatype, enabling representation of datasets.

---

Do you want me to also create a **condensed revision sheet (1–2 pages)** from this master document for quick exam preparation?

