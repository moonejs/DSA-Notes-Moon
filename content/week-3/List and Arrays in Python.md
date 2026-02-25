
### Python List is NOT a Linked List

Very important correction from the slide:

> Python lists are not implemented as flexible linked lists
> 

This is extremely important.

Even though we studied linked lists before…

Python’s built-in `list` is actually:

 **A dynamic array.**


### How Python List Actually Works

Internally:

1. Python allocates a fixed block of memory (like an array).
    
2. It keeps track of how many elements are used.
    
3. If the list overflows:
    
    - It doubles the size.
        
    - Copies elements into new larger block.
        

So Python list behaves like: **Dynamic Array**
Not a linked list.


#### Why append() Is Fast

> l.append() and l.pop() are constant time, amortised — O(1)

Let’s understand this carefully.

---

##### What Is Amortised O(1)?

Most of the time:

```python
l.append(x)
```

just puts element at next free slot.

Time = O(1)

But sometimes:

- Array becomes full
    
- Python creates new array of double size
    
- Copies all elements
    

That takes O(n).

But this happens rarely.

So average cost per append is O(1).

This idea is called:

👉 Amortised Analysis

#### Insertion in Python List

>Insertion/deletion require time O(n)

Why?

Because if you insert in middle:

l.insert(2, 99)

All elements after index 2 must shift.

Shifting = O(n)


#### Python List Behaves More Like Array

> Effectively, Python lists behave more like arrays than lists

That means:

✔ Random access O(1)  
✔ Insert middle O(n)  
✔ Delete middle O(n)

Exactly like arrays.

>[!Important]
>Python lists are **mutable**.

If multiple variables reference the same object,  
changing one changes all.

This is a deep concept.

###### What Does This Do?

```python
A = [[0]*3]*3
```

It creates 3 references to the same L.

So memory looks like:

```
        ┌─────────────┐
A[0] ──►│ 0  0  0     │
A[1] ──►│ 0  0  0     │  (same list)
A[2] ──►│ 0  0  0     │
        └─────────────┘
```

All three rows are the same object.

##### What Happens If You Modify One?

```python
A[0][1] = 5
print(A)
```

Output becomes:

```python
[[0,5,0],
 [0,5,0],
 [0,5,0]]
```

Because they all point to the same list.

The issue is:

👉 Python list multiplication copies references, not inner objects.

This is called **aliasing**.

**Always use list comprehension:**

```python
A = [[0 for i in range(3)] for j in range(3)]
```

Now memory looks like:

```
A[0] → [0,0,0]
A[1] → [0,0,0]
A[2] → [0,0,0]
```

Each row is a separate object.

Now changing one row will NOT affect others.

### NumPy Arrays

> The NumPy library provides arrays as a basic type.

So now we move from:

Python lists (dynamic arrays)

to

👉 **NumPy arrays** (true numerical arrays)