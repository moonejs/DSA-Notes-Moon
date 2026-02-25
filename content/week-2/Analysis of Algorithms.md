
[[Complexity]]

***Notes By Moon***

That process of checking how good your algorithm is =  
**Analysis of Algorithm**

We don’t measure actual time in seconds.


We measure:

> How running time grows as input size grows.


|Type|Example|Speed|
|---|---|---|
|log n|Binary search|Very fast|
|n|Linear search|OK|
|n log n|Merge sort|Very good|
|n²|Nested loops|Slow|
|n³|3 nested loops|Very slow|
|2ⁿ|Subset problems|Extremely dangerous|
|n!|Permutations|Impossible|

#### What Is Input Size?

|Problem|Input Size|
|---|---|
|Sorting list|Number of elements|
|Graph|Number of vertices + edges|
|Prime checking|Number of digits|
|Matrix|Rows × Columns|

Suppose you search for 5 in list:

[5, 10, 20, 30]

You find it immediately. Fast.

But what if list is:

[10, 20, 30, 40]

Now you check everything and don’t find it.

That is **Worst Case**.

We usually analyze:

 Worst Case Time

Because:

- Average case is hard to compute.
    
- Worst case gives guarantee.


---
>for large n n² gives very large value so large time

But here is the deeper intuition:

If n doubles…

- n → 2n
    
- n² → (2n)² = 4n²
    

So time becomes **4 times bigger**.

If n becomes 10 times bigger…

- n² becomes 100 times bigger 
    

That is dangerous growth.


----
>log₂(n) = how many times you divide n by 2 until it becomes 1

Example:

n = 16

16 → 8 → 4 → 2 → 1  
Divided 4 times.

So:

log₂(16) = 4

Another example:

n = 8

8 → 4 → 2 → 1  
Divided 3 times.

So:

log₂(8) = 3


So log n basically means:

"How many times can I cut it in half?"

That’s why binary search is log n —  
because we cut the search space in half every time.

##### ignore constant factors?

Suppose:

Algorithm A → 5n  
Algorithm B → n²

For small n = 10:

5n = 50  
n² = 100

Looks close.

But for n = 1,000,000:

5n = 5,000,000  
n² = 1,000,000,000,000 

Now constant 5 doesn’t matter at all.

The growth type matters.

>[!question]
>Suppose:
>Algorithm 1 → n log n  
Algorithm 2 → n²
Which one is better when n becomes very large?
And why?


### Suppose n = 1,000

- n log n ≈ 1000 × 10 = 10,000
    
- n² = 1,000,000
    

Now increase n to 10,000

- log(10,000) ≈ 14
    
- n log n ≈ 10,000 × 14 = 140,000
    
- n² = 100,000,000 
    

See what happened?

When n increased 10 times:

- n log n increased about 14 times
    
- n² increased 100 times 
    

That’s the key difference.

Log n grows VERY slowly.

Even if n becomes 1,000,000:

log₂(1,000,000) ≈ 20

Only 20!!

That’s crazy small.

---
Imagine:

You are searching in a dictionary.

There are 1,000 pages.

Do you check page by page?

No.

You open in the middle.

Then again middle of that half.

Then again middle.

That is [[Binary-Search]]

Each time:  
You remove half the pages.

So number of steps is:  
How many times you can halve 1000 before reaching 1.

That is log₂(1000).

---
### Asymptotic Complexity

>What happens to running time when n becomes very large?

We don’t care about:

- small n like 5, 10, 20
    
- exact seconds
    
- constants like 3n or 5n
    

We care about:

 Behavior when n → very large


n³ vs n²

Higher power of n always grows faster.

So:

- n³ grows faster  
 - n² is better

>[!note]
>We only care about:
> - Highest power of n
> - Growth rate
> - Not constants.

[[Complexity]]

### Worst Case vs Average Case

Let’s understand this slowly.

Suppose you search for number 7 in:

[7, 10, 20, 30, 40]

You find it immediately → very fast.

Now suppose you search for 99:

[7, 10, 20, 30, 40]

You must check every element → slow.

So same algorithm.  
Different inputs.  
Different time.


There are 3 possibilities:

1️ Best case  
2️ Average case  
3️ Worst case

we will analyze **Worst case**

Because:

- It gives guarantee.
    
- It is easier to calculate.
    
- It tells us maximum time the algorithm may take.


For **Linear Search**

For list of size n:

|Case|Time|
|---|---|
|Best case|1|
|Worst case|n|
|Average case|Around n/2|

But in algorithm analysis…

 We focus on **worst case**

So we say:

**Linear search = `O(n)`**

When we say:

**Linear search = O(n)**  
**Binary search = O(log n)**

It means:

In worst case,

- Linear search time grows proportional to n
    
- Binary search time grows proportional to log n


>[!question]
>```python
>for i in range(n):
>	for j in range(i):
>		print(i, j)
>```

**How many times does print run?**

When:

i = 0 → inner loop runs 0 times  
i = 1 → inner loop runs 1 time  
i = 2 → inner loop runs 2 times  
i = 3 → inner loop runs 3 times  
...  
i = n-1 → inner loop runs n-1 times

So total executions =

0 + 1 + 2 + 3 + ... + (n-1)

Sum of first (n-1) numbers:

= n(n-1) / 2

Now apply Big-O rules:

- Ignore constants (½)
    
- Ignore lower term (-½n)
    

What remains?

**O(n²)**


>[!question]
>```python
>for i in range(n):
>	j = 1while j < n:
>		j = j * 2
>```



Understand the inner `while` loop

```python
j = 1
while j < n:
    j = j * 2

```

What happens to `j`?

1 → 2 → 4 → 8 → 16 → 32 → ...

Each time it **doubles**.

So the question becomes:

 How many times can we multiply by 2 before reaching n?

That is exactly:

$$
log_2(n)
$$


So the **while loop runs O(log n)** times.

Outer loop

```python
for i in range(n):
```

That runs **n times** → O(n)

For each of the n iterations,  
we run a loop that takes log n time.

$$
O(n log n)
$$
>[!important]
>`j = j * 2` or `j = j / 2` think of `log n`


>[!question]
>```python
>i = n
>while i > 1:
>	i = i // 2
>```

What happens?

n → n/2 → n/4 → n/8 → ... → 1

Each step **halves** the value.

So the question becomes:

How many times can you divide n by 2 until it becomes 1?

That is exactly:

$$
log_2(n)
$$


If you see:

- `i = i // 2`
    
- `i = i / 2`
    
- `i = i * 2`
    
- anything that **doubles or halves**
    

Immediately think:

 **O(log n)**
