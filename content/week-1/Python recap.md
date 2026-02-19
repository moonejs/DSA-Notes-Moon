## What is GCD (HCF)?

**GCD(m, n)** = Greatest Common Divisor  
→ The biggest number that divides **both** `m` and `n`

Examples:

- `gcd(8, 12) = 4`
    
- `gcd(18, 25) = 1`
    
- `gcd(7, 13) = 1` (no common factor except 1)
    

Important facts:

- GCD **always exists** because `1` divides everything
    
- `gcd(m, n) ≤ min(m, n)`
    

That means:  
You only need to check numbers from `1` to `min(m, n)`

Let's us say 

m=12 n=8

```
Check 1 → divides both? ✅  
Check 2 → divides both? ✅  
Check 3 → divides both? ❌  
Check 4 → divides both? ✅  
Check 5 → ❌  
Check 6 → ❌  
Check 7 → ❌  
Check 8 → ❌  

```

Common factors = `[1, 2, 4]`  
The **last one** is the **GCD**

```python
def gcd(m,n):
	cf=[]
	for i in range(1,min(m,n)+1):
		if (n%i==0) and (m%i==0):
			cf.append(i)
	return cf[-1]
```


### Optimization: Why list is useless?

We only need the **last common factor**  
Why store the whole list?

so we can use only one variable that will store the last element

```python
def gcd(m,n):
	result=1
	for i in range(1,min(m,n)+1):
		if( m%i==0) and (n%i==0):
			result=i
	return result
```


>Both methods take time proportional to `min(m, n)`

```
gcd(1000000, 1000000)
→ loop runs 1 million times 

```


yes we can do better 

If `d` divides both `m` and `n`:

```
m = a·d  
n = b·d  
```

then:
`m-n=(a-b)*d`

Any common divisor of `m` and `n`  
also divides `m - n`

so,
Instead of solving `gcd(m, n)`  
we can solve a **smaller problem**:

`gcd(n, m - n)`

because gcd will remain the same

This is **recursion**:  
solve a problem using a smaller version of itself.

```python
def gcd(m,n):
	(a,b) = (max(m,n),min(m,n))
	if a%b==0:
		return b
	else:	
		gcd(b,a-b)
```

### `if a % b == 0:`

This checks:

> Does the smaller number **b divide** the bigger number **a** exactly?

12 % 6 == 0   → True  
12 % 8 == 4   → False

If it divides exactly, then:

> **b is the GCD**

Why?  
Because:

- b divides a
    
- b divides itself
    
- No number bigger than b can divide b  
    So b is the **largest common divisor**


but this is also slow

we will use **Euclid’s Algorithm**

### Euclid’s Algorithm

When `n` does **not** divide `m`:

`m = q·n + r   (quotient q, remainder r)

If `d` divides both `m` and `n`,  
then `d` also divides the remainder `r`.

So:

> gcd(m, n) = gcd(n, m % n)

This is the heart of **Euclid’s Algorithm**.`

```python
def gcd(m, n):
    (a, b) = (max(m, n), min(m, n))
    if a % b == 0:
        return b
    else:
        return gcd(b, a % b)
```

Dry run

gcd(2, 9999)

```
a = 9999, b = 2
9999 % 2 = 1
→ gcd(2, 1)
```

```
a = 2, b = 1
2 % 1 = 0
→ return 1
```

Done in **2 steps**

---

Professor teaches the concept of **Prime Number** and **factors** 

so 

First, we will **compute the list of factors of n**  
Then we will check if that list is exactly `[1, n]`

```python
def factors(n):
	fl=[]
	for i in range(1,n+1):
		if (n%i)==0;
			fl.append(i)
	return fl
```

so now we will check if number is prime (using factor list)

n is prime **if and only if**  
factors(n) == [1, n]

```python
def prime(n):
	return (factors(n)==[1,n])
```

#### Listing **all primes up to m** (using a `for` loop)

```python
def allPrimes(m):
	pl=[]
	for i in range(1,m+1):
		if prime(i):
			pl.append(i)
	return pl
```

#### First **m** primes

###### Why `for` loop is NOT enough here?
Because:

- We **don’t know** how far numbers go to get first `m` primes  
    (e.g., 1000th prime is ~7919 — not obvious!)


we will use **while** loop

```python
def mPrimes(m):
	( count,i,pl)=(0,1,[])
	while(count<m):
		if prime(i):
			count+=1
			pl.append(i)
		i+=1
	return pl

```

---
#### Faster way to check if a number is prime

## Problem with old method (Concept)

Old method:

- Find **all factors** of `n`
    
- Then check if factors list is `[1, n]`
    

Problem:

- If `n` is big (like 1,000,000), you check **every number from 1 to n** 
    
- That’s slow.
    

> We don’t need **all** factors.  
> We only need to know:  
>  Is there **any factor between 2 and n−1**?

If **yes** → not prime  
If **no** → prime

```python
def prime(n):
	result=True
	for i in range(2,n):
		if (n%i==0):
			result=False
	return result	
```

we can improve this by using **`break`** 

```python
def prime(n):
	result=True
	for i in range(2,n):
		if(n%i==0):
			result=False
			break
	return result
```

we are assuming **n>=2** so careful

### Why can we stop at √n?

Think of factors in **pairs**:

`n = a × b`

Then:

- one factor is **small**
    
- the other factor is **big**

```
36 = 2 × 18
36 = 3 × 12
36 = 4 × 9
36 = 6 × 6   ← √36 = 6
```

after this factors are repeating itself 

>If n has any factor at all,  
it must have **at least one factor ≤ √n**

```python
def prime(n):
	(result,i)=(True,2)
	while(result and i<=n**0.5)
		if(n%i==0):
			result=False
		i+=1
	return result
```

so this method is faster again we have to handle the edge cases

---
### What are “prime gaps”?

Instead of listing primes,  
let’s look at the **difference between consecutive primes**

Primes:

```
2, 3, 5, 7, 11, 13, 17, 19, 23, 29 ...
```

Difference

```
3 - 2 = 1  
5 - 3 = 2  
7 - 5 = 2  
11 - 7 = 4  
13 - 11 = 2  
17 - 13 = 4  
19 - 17 = 2  
23 - 19 = 4  
29 - 23 = 6  
```

So differences are:

```
[1, 2, 2, 4, 2, 4, 2, 4, 6, ...]
```

Special case:

- Difference = 2 → called **twin primes**  
    Examples:
    
    - (3,5)
        
    - (5,7)
        
    - (11,13)
        
    - (17,19)

Professor also talked about dictionary

let's find out How many times does each difference occur?

```python
def primediffs(n):
	lastprime=2
	pd={}
	for i in range(3,n+1):
		if prime(i):
			d=i-lastprime
			lastprime=i
			pd[d]=pd.get(d,0)+1
	return pd
```

