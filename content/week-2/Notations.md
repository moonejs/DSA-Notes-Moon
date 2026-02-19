
***Notes By moon***

### What Is Big-O Actually Saying?


##### Big-O (Upper Bound)

We say:

>f(n) is O(g(n))


###### What is f(n)?

f(n) is just:

 **The running time of your algorithm.**

That’s it.

Earlier we were saying:

- Linear search → O(n)
    
- Nested loop → O(n²)
    
- Binary search → O(log n)
    

That running time expression?  
**That is f(n).**

If your code runs:

```python
for i in range(n):
    print(i)

```

Running time ≈ n

So here:

f(n) = n

##### what is g(n)?

g(n) is just:

 **A function we compare it with.**

We are asking:

"Does f(n) grow slower than or equal to g(n)?"

Example:

If:

f(n) = 100n + 5

We compare it with:

g(n) = n²

So we ask:

Is 100n + 5 eventually smaller than some constant × n²?

If yes → we say:

f(n) is O(n²)


Because Big-O is a general mathematical definition.

Instead of saying:

"100n + 5 is O(n²)"

We say generally:

"f(n) is O(g(n))"

Meaning:

The running time function f(n)  
is bounded above by g(n).

---
When we say:

>f(n) is O(g(n))

We mean:

 f(n) does not grow faster than g(n).

That’s it.

No magic.

---

When we say:

> A is O(B)

It means:

 **A grows slower than or equal to B (for large n).**

That’s it.

---

### Example 1

Is:

100n + 5 growing slower than n²?

For small n maybe not.

But for large n:

n² becomes huge.

100n + 5 becomes tiny compared to n².

So yes.

We say:

100n + 5 is O(n²)

Meaning:

n² grows faster.

---

If highest power of first function  
is smaller than highest power of second function

Then:

First one is O(second one)

Examples:

n is O(n²) ✅  
n² is O(n³) ✅  
n³ is O(n²) ❌

Because higher power always wins.


### Omega (Ω) — Lower Bound

This means the opposite.

When we say:

> A is Ω(B)

**A grows faster than or equal to B.**

n³ is Ω(n²) ✅  
Because n³ grows faster.


### Theta (Θ) — Exact Same Growth

When we say:

> A is Θ(B)

It means:

👉 A and B grow at the same speed.

Example:

n² + 5n is Θ(n²)

Because:

The highest power is n²  
Lower terms don’t matter.

Think like this:

Two cars are racing.

Car A speed increases like n  
Car B speed increases like n²

Eventually, car B will go much faster.

So we say:

Car A is O(car B)

Meaning:

Car A will always be slower eventually.


>For large inputs, f(x) does not grow faster than g(x).


---
![[Pasted image 20260213125058.png]]

If your algorithm has **two parts**:

• Part A takes time g₁(n)  
• Part B takes time g₂(n)

Then total time is:

👉 The slower of the two parts.

Not the sum in Big-O terms.

If one part takes 1 second  
And another part takes 1 hour

Total time is basically 1 hour.

The slowest part dominates.


| Symbol  | Meaning                  |
| ------- | ------------------------ |
| O(g(n)) | grows at most like g(n)  |
| Ω(g(n)) | grows at least like g(n) |
| Θ(g(n)) | grows exactly like g(n)  |