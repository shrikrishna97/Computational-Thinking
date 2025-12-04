# **Recursion, DFS, BFS, and DFS Using Recursion – Notes**

# **0. Basic Terminology**

### **Node / Vertex**

A point in a graph. Example: A, B, C, etc.

### **Edge**

A connection between two nodes.

### **Neighbour**

If two nodes share an edge, they are neighbours.

### **Graph**

A collection of nodes connected by edges.

### **Adjacency Matrix**

A table that represents graph connections.
If `graph[i][j] == 1`, it means there is an edge between node `i` and node `j`.

Example:

```
    A B C
A [ 0 1 1 ]
B [ 1 0 0 ]
C [ 1 0 0 ]
```

### **Visited Dictionary**

A record of which nodes have been explored during DFS.
Example: `{A: True, B: True}`.

---

# **Data Structures Used in Graph Search**

### **Stack (Used by DFS)**

A stack is a data structure where elements are added and removed from **one end only**.

It follows **LIFO**: Last In, First Out.
Example: A stack of plates — you remove the topmost plate first.

*Recursion also uses an internal stack to manage function calls.*

### **Queue (Used by BFS)**

A queue allows adding at one end and removing from the other.

It follows **FIFO**: First In, First Out.
Example: A line of people waiting at a ticket counter — the first person in line is served first.

---

# **1. Recursion**

## 1.1 What is Recursion?

Recursion is a technique in which a function calls itself to solve a smaller version of the same problem.
Many mathematical and computational problems can be defined inductively, which makes recursion a natural fit.

A recursive definition always consists of two parts:

### **Base Case**

A simplest form of the problem, solved directly.

### **Recursive Step (Inductive Step)**

The problem is reduced to a smaller instance and solved using the same function.

---

## 1.2 Analogy: Chocolate Wrapper Chain

Imagine you have a chain of chocolate wrappers stuck together.
To find information about the last wrapper:

1. Look at the first wrapper.
2. If it is the only wrapper → stop (base case).
3. Otherwise, remove the first wrapper and repeat with the remaining chain (recursive step).

This illustrates how recursion reduces a problem step-by-step until it reaches the base case.

---

## 1.3 Numerical Example (From Lecture 11.5)

### Factorial Function

Definition:

* 0! = 1 (base case)
* n! = n × (n − 1)! (recursive step)

### Pseudocode:

```
Procedure Factorial(n)
    if (n == 0) {
        return(1)
    }
    else {
        return(n * Factorial(n-1))
    }
End Factorial
```

### Execution Diagram:

```
Factorial(4)
 → 4 * Factorial(3)
        → 3 * Factorial(2)
               → 2 * Factorial(1)
                       → 1 * Factorial(0)
                               → 1  (base case)
```

---

## 1.4 List Example (From Lecture 11.5)

### Sum of Elements in a List

Definition:

* If the list is empty → sum is 0
* Otherwise → sum = first(l) + sum(rest(l))

### Pseudocode:

```
Procedure Listsum(l)
    if (l == []) {
        return(0)
    }
    else {
        return(first(l) + Listsum(rest(l)))
    }
End Listsum
```

---

## 1.5 Key Points About Recursion

* The base case must be clearly defined; otherwise, recursion will not terminate.
* The input must get smaller with each recursive call.
* Recursive functions suspend their computation until the recursive call completes.

---

# **2. Graph Search: BFS and DFS**

Graphs consist of vertices (nodes) connected by edges.
Graph search helps determine which nodes are reachable from a given starting node.

Two classical search strategies are:

* **BFS (Breadth First Search)**
* **DFS (Depth First Search)**

---

# **3. Breadth First Search (BFS)**

BFS explores the graph level by level.

1. Start with the initial node.
2. Visit all its neighbours (distance 1).
3. Visit neighbours of those neighbours (distance 2).
4. Continue level by level.

It uses a **queue**, ensuring that nodes are explored in increasing order of distance from the start.

---

# **4. Depth First Search (DFS)**

DFS explores as deeply as possible before backtracking.

Based on Lecture 11.6, DFS follows this pattern:

1. Start from node *i*.
2. Visit a neighbour *j*.
3. Suspend work on *i* and explore *j* instead.
4. Continue until reaching a node with no unexplored neighbours.
5. Backtrack to the nearest node that still has unvisited neighbours.
6. Repeat until all reachable nodes are explored.

DFS uses recursion, which internally uses a stack, matching DFS behaviour naturally.

---

# **4.1 DFS Exploration Diagram**

Example graph:

```
    A
   / \
  B   C
  |   |
  D   E
```

DFS starting at A:

```
A → B → D → (backtrack) → A → C → E
```

Backtracking happens one step at a time, not all the way to the beginning at once.

---

# **5. DFS Using Recursion (From Lecture 11.6)**

DFS maintains a dictionary called `visited` to track explored nodes.

### Pseudocode from Lecture 11.6:

```
Procedure DFS(graph, visited, i)

    visited[i] = True

    foreach j in columns(graph) {
        if (graph[i][j] == 1 and not(isKey(visited, j))) {
            visited = DFS(graph, visited, j)
        }
    }

    return(visited)
End DFS
```

### Explanation 

* `graph` is an adjacency matrix.
* `visited` records which nodes are already explored.
* For each neighbour `j` of node `i`:

  * If there is an edge (`graph[i][j] == 1`)
  * And `j` has not been visited
  * Then DFS recursively explores `j`.

This recursion ensures DFS explores deeply, and returns (backtracks) when there are no more neighbours.

---

# **5.1 Example Execution (Summarized from PDF)**

If DFS starts at node 4:

```
DFS(graph, visited, 4)
 → DFS(graph, visited, 1)
     → DFS(graph, visited, 2)
         → DFS(graph, visited, 3)
             → ...
```

Eventually all reachable nodes from 4 will appear in the `visited` dictionary.

---

# **6. Relationship Between Recursion and DFS**

DFS works naturally with recursion because both follow the same pattern:

* Go deeper into the problem
* Suspend the current computation
* Resume after the deeper computation returns

Backtracking in DFS corresponds exactly to returning from recursive calls.

---

# **7. Summary of the Concepts**

* **Recursion** involves breaking a problem into smaller instances and solving those instances using the same function.
* Every recursive function has a **base case** and a **recursive step**.
* **BFS** explores a graph level by level using a queue.
* **DFS** explores a graph deeply using recursion or a stack.
* The DFS algorithm maintains a `visited` dictionary and recursively explores each unvisited neighbour.
* DFS is especially suitable for recursion because recursive calls naturally handle backtracking.

---
