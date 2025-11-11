# Side Effects in Pseudocode for Lists and Dictionaries

> **📚 Reference**: This document is based on [Lecture 8.5 - Side effects in pseudocodes for lists and dictionaries.pdf](./Lecture%208.5%20-%20Side%20effects%20in%20pseudocodes%20for%20lists%20and%20dictionaries.pdf)

## Introduction to Side Effects

When we introduced procedures, we discussed the issue of **side effects** in the context of cards or tables. A side effect occurs when we pass a data structure (like a stack of cards or a table) to a procedure, and changes made inside the procedure are reflected outside. This change may or may not be required or intended.

Now that we're dealing with lists and dictionaries, we need to be aware of this problem and make conscious decisions about when to use side effects.

---

## Example 1: Finding Duplicates in Two Lists

### Basic Approach (Nested Loops)

Consider the problem of finding items duplicated across two lists:

```
overlap(l1, l2)
    overlap = []
    foreach x in l1
        foreach y in l2
            if x == y
                append x to overlap
    return overlap
```

**Complexity**: If both lists have `n` elements, the outer loop runs `n` times and the inner loop runs `n` times, resulting in **O(n²)** time complexity.

### Optimized Approach for Sorted Lists

If the lists are sorted, we can optimize significantly. For example:
- `l1 = [1, 2, 6, 8, 9]`
- `l2 = [2, 5, 8, 11]`

**Strategy**: 
- Scan through `l1` normally
- For `l2`, don't restart from the beginning each time
- Stop scanning `l2` when we reach a number ≥ the current number in `l1`
- Resume from where we left off for the next element

### Pseudocode with Side Effect

```
Procedure FindOverlap2(l1, l2)
    overlap = []
    foreach x in l1{
        y = first(l2)
        while(y < x){
            l2 = rest(l2)
            y = first(l2)
        }
        if(x == y){
            overlap = overlap ++ [x]
            l2 = rest(l2)
        }
    }
    return(overlap)
End FindOverlap2
```

**Complexity**: O(n + n) = O(n) - much better than O(n²)!

**Problem**: By repeatedly replacing `l2` with `rest(l2)`, we are destroying the second argument. This is an **undesirable side effect** - the caller expects both lists to remain intact.

### Solution: Make a Local Copy

```
Procedure FindOverlap2(l1, l2)
    overlap = []
    myl2 = l2  // Make a local copy
    foreach x in l1{
        y = first(myl2)
        while(y < x){
            myl2 = rest(myl2)
            y = first(myl2)
        }
        if(x == y){
            overlap = overlap ++ [x]
            myl2 = rest(myl2)
        }
    }
    return(overlap)
End FindOverlap2
```

Now `l2` remains untouched while we benefit from the efficient algorithm using our private copy `myl2`.

---

## Example 2: Removing a Key from a Dictionary

Sometimes a side effect is the **intended behavior**.

### Approach 1: With Side Effect (In-Place Update)

```
removeKey(d, k)
    myD = {}  // Create new empty dictionary
    foreach key in d
        if key != k
            myD[key] = d[key]
    d = myD  // Update original dictionary
```

This procedure modifies the dictionary `d` directly. The side effect is **expected and documented** - the caller knows their dictionary will be updated in place.

### Approach 2: Without Side Effect (Return New Dictionary)

```
removeKey(d, k)
    myD = {}  // Create new empty dictionary
    foreach key in d
        if key != k
            myD[key] = d[key]
    return myD  // Return new dictionary, don't modify original
```

Usage:
```
d = removeKey(d, keyToRemove)  // Reassign to update
```

The original dictionary is not modified; instead, a new dictionary is returned, and the caller can reassign it if they want the update.

---

## When Are Side Effects Appropriate?

### Situations Where Side Effects Are Intended:
1. **Deleting from a dictionary**: Updating the dictionary in place
2. **Sorting a list**: Sorting the list directly rather than creating a new sorted list
3. **Other in-place modifications**: When the purpose is to modify the data structure

### Key Requirement: Documentation
If a procedure performs a side effect, it **must be clearly documented** so users know the argument will be modified.

---

## Best Practices

### 1. Avoiding Unintended Side Effects
When you want computational benefits from modifying an argument but don't want it visible to the caller:
- **Make a local copy** of the argument
- Perform all updates on the local copy
- The original argument remains untouched

### 2. Intentional Side Effects
When the side effect is the intended behavior:
- **Document it clearly** in the procedure description
- Make sure users know the argument will be modified in place

### 3. Alternative Without Side Effects
For procedures that could use side effects:
- **Return a new collection** with the modifications
- The caller can reassign: `collection = updateProcedure(collection, params)`
- This approach gives the caller control over whether to keep the original

---

## Summary

| Aspect | Unintended Side Effect | Intended Side Effect | No Side Effect |
|--------|----------------------|---------------------|----------------|
| **Example** | Efficient overlap finding | Delete dictionary key | Return new sorted list |
| **Approach** | Make local copy | Modify in place | Return new collection |
| **Documentation** | Document that no side effect occurs | Document that argument is modified | Document return value |
| **Usage** | `result = overlap(l1, l2)` | `removeKey(d, k)` | `newList = sort(oldList)` |

**Key Takeaway**: Be aware of side effects when working with collections. Make conscious decisions about whether to use them, and always document the behavior clearly for users of your procedures.
