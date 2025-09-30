

# **Week – 2**

**Flowcharts**
Pictorial representation of computational process

**Eg:** Counting the number of cards

<img width="500" height="450" alt="image" src="https://github.com/user-attachments/assets/24c836ce-03a2-4d82-9b3c-af816745e311" />

---

**→ Node types:**

1. **Process** (Indicated in rectangular box)
2. **Decision** (Indicated in diamond shape box)
3. **Terminal** (Used for start and end, indicated by oval)

**→ Arrows indicate operation flow**

---

### Pros and cons of Flowcharts

**Advantages:**

* Visual representation of computation
* Easy to understand

**Disadvantages:**

* *Size:* Complex processes generate large flowcharts
* *Collaboration:* Sharing pictures in editable format
* *Versions:* Compare changes between flowcharts

### **From pictures to text:**

**Describing the previous process in words**

**Step 0** Start

**Step 1** Initialize Count to 0

**Step 2** Check cards in Pile 1

**Step 3** If no more cards, go to step 8

**Step 4** If yes, Pick a card X from Pile 1

**Step 5** Move X to Pile 2

**Step 6** Increment Count

**Step 7** Go back to step 2

**Step 8** End

    Is this step wise wording helping us ? it tells us about the future step then about the past step again to be executed. We don't want that !! lets what can be done...

---

**Programming language**

* Succinct notation for computational processes

* Better textual representation for

    **conditional execution**
    
    **Step 3** If no more cards, go to Step 8
    
    **Step 4** Pick a card X from Pile 1 ( we want to write it somewhere in text that step 4 depends on step 3 to be executed )
    
    **AND Repeated execution**
    
    **Step 2** Check cards in Pile 1
    
    .
    
    .
    
    .
    
    **Step 7** Go back to step 2 ( we also want to write the from step 2 to step 6 needs to be repeated again and again, which is not written in flow chart )

---

# **Pseudocode**

```
Start
Count = 0
while (Pile 1 has more cards) {
    Pick a card X from Pile 1
    Move X to Pile 2
    Increment Count
}
End
```

1. Assign a value to a variable
2. Repeat steps while condition holds
3. Mark start and end of repeated block

---

**Summary**

* Flowcharts are easy to read, visual descriptions of procedures, but they are cumbersome; hard to share and edit.
  
* Writing down steps in a text is an alternative.
  
* Tune the notation to capture standard features:

  * Assigning values to variables
    
  * Conditional execution
    
  * Repeated execution

---

# **Pseudocode: Iteration and Filtering**

## **Counting cards**

```
Start
Count = 0
while (Pile 1 has more cards) {
    Pick a card X from Pile 1
    Move X to Pile 2
    Increment Count
}
End
```

---

**• Will dispense with Start and End henceforth**

    And now let's modify the pseudocode to get the sum of maths marks...

## **Sum of Maths marks**

```
Sum = 0
while (Pile 1 has more cards) {
    Pick a card X from Pile 1
    Move X to Pile 2
    Sum = Sum + X.Maths
}
```

---

<img width="500" height="450" alt="image" src="https://github.com/user-attachments/assets/4ebf2a5e-79e0-4913-9f98-48328c8a73c1" />

---

### ▪️ Update Sum: assignment statement

* Sum on right is current value
* Sum on left is updated value
* `=` is not mathematical equality

---

### ▪️ Increment: `Count = Count + 1`

* `x.Maths`: Maths marks in card `x`

---

## **Sum of Boys' Maths marks**

```plaintext
Sum = 0  
while (Pile 1 has more cards) {  
    Pick a card x from Pile 1  
    Move x to Pile 2  
    if (x.Gender == M) {  
        Sum = Sum + x.Maths  
    }  
}
```

**Flowchart:**

<img width="500" height="450" alt="image" src="https://github.com/user-attachments/assets/97147801-3c2b-4595-958a-284fb2f883f2" />


---

### ▪️ Conditional execution error

### ▪️ Equality (`==`) vs Assignment (`=`)

---

## **Sum of Boys' and Girls' Maths marks**

```plaintext
BoySum = 0  
GirlSum = 0  
while (Pile 1 has more cards) {  
    Pick a card x  
    Move x to Pile 2  
    if (x.Gender == M) {  
        BoySum = BoySum + x.Maths  
    } else {  
        GirlSum = GirlSum + x.Maths  
    }  
}
```

**Flowchart:**

<img width="500" height="450" alt="image" src="https://github.com/user-attachments/assets/363bd178-9035-492c-a04d-7d638d968f31" />


---

▪️ Alternative branch for conditional

---

## **Finding the card with maximum Maths marks**

```plaintext
MaxM = 0  
MaxCard = -1  

while (Pile 1 has more cards) {  
    Pick a card x from Pile 1  
    Move x to Pile 2  
    if (x.Maths > MaxM) {  
        MaxM = x.Maths  
        MaxCard = x.Id  
    }  
}
```

---

### **Flowchart:**

<img width="500" height="450" alt="image" src="https://github.com/user-attachments/assets/7a6c4afc-cc63-4cb3-b938-54be84457145" />



---

### **Summary**

#### ▪️ Assignment statement

* `Count = 0`
* `Sum = Sum + x.Maths`

#### ▪️ Conditional execution

* **Once**

  * `if (condition) { ... }`
  * `if (condition) { ... } else { ... }`
* **Repeatedly**

  * `while (condition) { ... }`

#### ▪️ Equality (`==`) vs Assignment (`=`)

* `if (x.Gender == M)`

---
