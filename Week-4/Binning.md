# **Week 4 — Binning Method**

### **Introduction**

The **binning method** is used to smooth data or handle noisy data.
In this method:

1. The data is first **sorted**.
2. The sorted values are then **distributed into a number of buckets or bins**.

Since binning methods consult the neighborhood of values, they perform **local smoothing**.

---

**Binning example**: When displaying students’ marks in a subject, instead of listing each individual score, we group them into bins:

0–20 → Poor

21–40 → Average

41–60 → Good

61–80 → Very Good

81–100 → Excellent

---

## **Example: Comparing Each Element with All Other Elements**

For **N objects**, the number of comparisons required will be:

```
(N - 1) + (N - 2) + ... + 1 = N × (N - 1) / 2
```

This is the same as the number of ways of choosing 2 objects from N:

```
NC2 = N × (N - 1) / 2
```

### **From First Principles**

* Total number of pairs = N × N
* Remove self-comparisons (e.g., A with A):
  → N × N − N = N × (N − 1)
* Comparing A with B is the same as comparing B with A, so we are double-counting.
  → Divide by 2

Hence, the number of comparisons:

```
= 1/2 × N × (N - 1)
```

---

### **Example with 5 Elements: A, B, C, D, E**

| Element | Comparisons         |
| ------- | ------------------- |
| A       | with B, C, D, E → 4 |
| B       | with C, D, E → 3    |
| C       | with D, E → 2       |
| D       | with E → 1          |

**Total comparisons = 4 + 3 + 2 + 1 = 10**

**Formula:**

```
Number of comparisons = 1/2 × N × (N - 1)
```

---

## **Calculation of Reduction Due to Binning**

### **Without Binning**

For N items:

```
Number of comparisons = 1/2 × N × (N - 1)
```

---

### **With Binning**

If we use **K bins** of equal size:

* Number of items per bin = N / K
* Number of comparisons per bin = 1/2 × (N / K) × ((N / K) − 1)

Total number of comparisons:

```
K × 1/2 × (N / K) × ((N / K) - 1)
= 1/2 × N × ((N / K) - 1)
```

---

### **Factor of Reduction**

```
Factor of reduction = (1/2 × N × (N - 1)) / (1/2 × N × ((N / K) - 1))
                    = (N - 1) / ((N / K) - 1)
```

Example:
If N = 9 and K = 3:

```
Factor of reduction = (9 - 1) / ((9 / 3) - 1)
                    = 8 / 2
                    = 4
```

**Reduction is by a factor of 4 times**

---

## **Key Idea: Use Binning**

For **9 objects A, B, C, D, E, F, G, H, I**:

### Without binning:

```
Number of comparisons = 1/2 × 9 × (9 - 1)
                       = 36
```

### With binning into 3 bins of 3 each:

```
Comparisons per bin = 1/2 × 3 × (3 - 1) = 3
Total comparisons for all bins = 3 × 3 = 9
```

**So, the number of comparisons reduces from 36 to 9!**
**Reduced by a factor of 4 times.**

---
