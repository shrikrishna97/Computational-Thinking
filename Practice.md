# **Graph-Based Adjacency Matrix Questions Using Scores Table**

### **Pseudocode Context**

Consider a table `Scores` with student marks in three subjects: Physics (`P`), Chemistry (`C`), and Mathematics (`M`). The following pseudocode reads the table and generates adjacency matrices for each subject.

```text
D = {}
while(Table 1 has more rows){
    Read the first row X in Table 1
    D[X.SeqNo] = {"P": X.Physics, "C": X.Chemistry, "M": X.Mathematics}
    Move X to Table 2
}

matrixPh = getAdjMatrix(D, "P")
matrixCh = getAdjMatrix(D, "C")
matrixMa = getAdjMatrix(D, "M")

Procedure getAdjMatrix(D, Subject)
    n = length(keys(D))
    matrix = createMatrix(n, n)
    foreach i in rows(matrix){
        foreach j in columns(matrix){
            if(i != j){
                diff = D[i][Subject] - D[j][Subject]
                if(10 <= diff and diff <= 20){
                    matrix[i][j] = 1
                }
            }
        }
    }
    return(matrix)
End getAdjMatrix
```

---

### **Question 1 [5 Marks]**

If `matrixPh[i][j] = 1`, which of the following statements is correct?

**Options:**
(a) i scored at most 10 and at least 20 more marks in Physics than j

(b) i scored at least 10 and at most 20 more marks in Physics than j

(c) j scored at least 10 and at most 20 more marks in Physics than i

(d) j scored at most 10 and at least 20 more marks in Physics than i

---

### **Question 2 [5 Marks]**

Choose the correct statement about the adjacency matrix `matrixPh`.

**Options:**
(a) For all i, j with i != j, `matrixPh[i][j] + matrixPh[j][i] = 1`

(b) For all i, j with i != j, if `matrixPh[i][j] = 1` then `matrixPh[j][i] = 0`

(c) For all i, j with i != j, if `matrixPh[i][j] = 0` then `matrixPh[j][i] = 1`

(d) For all i, j with i != j, if `matrixPh[i][j] = 1` then `matrixPh[j][i] = 1`

(e) For all i, j with i != j, if `matrixPh[i][j] = 0` then `matrixPh[j][i] = 0`

---

### **Question 3 [5 Marks, MSQ]**

Using the matrices `matrixPh`, `matrixCh`, and `matrixMa`, we define:

```text
n = length(keys(D))
matrixHelp = createMatrix(n, n)
foreach i in rows(matrixHelp){
    foreach j in columns(matrixHelp){
        matrixHelp[i][j] = matrixPh[i][j] + matrixCh[i][j] + matrixMa[i][j]
    }
}
```

Let i and j be indices of two students. Choose all correct statements:

**Options:**
(a) `0 <= matrixHelp[i][j] <= 3`

(b) `matrixHelp[i][j] + matrixHelp[j][i] <= 3`

(c) `matrixHelp[i][j] != matrixHelp[j][i]`

(d) if `matrixHelp[i][j] = 0`, then `matrixHelp[i][j] = 3`

(e) if `matrixHelp[i][j] = 3`, then `matrixHelp[i][j] = 0`

---

### **Question 4 [4 Marks]**

At the end of the following pseudocode, `A` counts the number of **distinct pairs of students who can help each other in at least one subject**, and `B` counts the number of **distinct pairs where one can help the other in all subjects**.

Complete the pseudocode correctly:

```text
A = 0
B = 0
foreach i in rows(matrixHelp){
    foreach j in columns(matrixHelp){
        ***********************
        *** Fill the code   ***
        ***********************
    }
}
```

**Options:**

(a)

```text
if(matrixHelp[i][j] > 0 and matrixHelp[j][i] > 0){
    A = A + 1
}
if(matrixHelp[i][j] == 3){
    B = B + 1
}
```

(b)

```text
if(matrixHelp[i][j] > 0 and matrixHelp[j][i] > 0){
    A = A + 1
}
if(matrixHelp[i][j] > 2){
    B = B + 1
}
```

(c)

```text
if(i < j){
    if(matrixHelp[i][j] > 0 and matrixHelp[j][i] > 0){
        A = A + 1
    }
    if(matrixHelp[i][j] > 2){
        B = B + 1
    }
}
```

(d)

```text
if(i < j){
    if(matrixHelp[i][j] > 0 and matrixHelp[j][i] > 0){
        A = A + 1
    }
}
if(matrixHelp[i][j] > 2){
    B = B + 1
}
```

---

