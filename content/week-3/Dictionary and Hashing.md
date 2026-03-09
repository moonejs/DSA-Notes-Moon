
### What is a Dictionary?

A dictionary is simply:

> A collection of key–value pairs

|Key|Value|
|---|---|
|"name"|"Rahul"|
|"age"|20|

##### Random Access (Very Important ⚡)

>Access time is the same for all keys

That means:

- Whether dictionary has 5 elements
    
- Or 5,00,000 elements
    

Accessing:

```python
D["age"]
```

takes **constant time → O(1)** (on average)

This is VERY powerful.


### How is a Dictionary Implemented Internally?

- The underlying storage is an **array**
    
- Keys have to be mapped to `{0,1,2,...,n-1}`
    
- Given a key `k`, convert it to an offset `i`
    
- Use a **hash function**


##### Dictionary is Actually an Array Inside

Even though we write:

```python
D = {"name": "Rahul", "age": 20}
```

Internally Python does something like:

```python
A = [None, None, None, None, None, None, None]
```

It creates a fixed-size array.

Why?

Because:

 Accessing `A[i]` takes **O(1)** time.

That’s the secret.

##### But We Are Using Keys, Not Indices!

Array needs **numbers** like:

```
0,1,2,3,4...
```

But dictionary keys are:

```
"name"
"age"
"city"
```

So how do we convert `"name"` into a number?

That is where the **hash function** comes in.


### What is a Hash Function?


h : S → X  
Maps a set of values S to a small range of integers X = {0,1,2,...,n-1}


**A hash function converts a key into an integer index.**

Example (imaginary):

```
h("name") = 3
h("age")  = 1
h("city") = 5
```

So internally:

```python
A[3] = ("name", "Rahul")
A[1] = ("age", 20)
A[5] = ("city", "Delhi")
```


##### Why Not Store Directly Without Hash?
Because:

- Keys are strings
    
- Arrays only accept integer indices
    

So:

> Dictionary = Array + Hash Function

This is called a **Hash Table**


- Dictionary internally uses an array
    
- Keys are converted into indices
    
- Conversion is done using a hash function
    
- This structure is called a Hash Table

### Collision in Hash Tables

>Typically |X| << |S|, so there will be collisions  
h(s) = h(s′), s ≠ s′

######  Why Do Collisions Happen?

Remember:

- Hash function converts keys → numbers
    
- Array size is limited (say size = 10)
    
- But possible keys are unlimited (infinite strings)
    

So different keys can map to the same index.

Example:

```
h("cat") = 3
h("dog") = 3
```
Now both want to go to index 3.

That is called a:

Collision

![[Pasted image 20260225165440.png]]


- Collision = Two different keys map to same index
    
- Collisions are unavoidable
    
- Good hash function reduces collisions
    
- We need strategies to handle collisions


#### That leads to two major strategies

1. **Open Addressing (Closed Hashing)**
2. **Open Hashing (Chaining)**


### Open Addressing (Closed Hashing)

>Open addressing (closed hashing)  
Probe a sequence of alternate slots in the same array

When collision happens:

Instead of storing multiple values in same slot,

👉 We **search for another empty slot** in the same array.

This searching process is called:

**Probing**


- Open addressing = find another empty slot
    
- Probing = searching for next available index
    
- Everything stored inside same array
    
- Linear probing is simplest method
    
- Too many collisions → clustering problem

### Open Hashing (Chaining)

>Open hashing  
Each slot in the array points to a list of values  
Insert into the list for the given slot

nstead of finding another empty slot (like open addressing),

 We allow **multiple elements at the same index**.

How?

Each array position stores a **list** (or linked list).

So:

Array index → List of key-value pairs


|Feature|Open Addressing|Open Hashing|
|---|---|---|
|Collision handling|Find next empty slot|Store list at same index|
|Extra memory|No|Yes (lists)|
|Clustering problem|Yes|No|
|Implementation|Slightly complex|Easier|

- Open hashing = Chaining
    
- Each array index stores a list
    
- Collision handled by adding to list
    
- Average time is O(1) with good hash function


##### Why Dictionary Keys Must Be Immutable

>Dictionary keys in Python must be immutable  
If value changes, hash also changes!

**What is Immutable?**
The value **cannot be changed after creation**

Examples of immutable types:

- `int`
    
- `float`
    
- `string`
    
- `tuple` (if it contains immutable elements)
    

Examples of mutable types:

- `list`
    
- `set`
    
- `dictionary`

Remember how dictionary works:

1. Compute `h(key)`
    
2. Store value at index `h(key)`
    
3. Later, to retrieve:
    
    - Compute `h(key)` again
        
    - Go to that index
        

So the hash value of the key must remain **constant**.


Dictionary = Hash Table  
Hash Table needs stable hash value  
Stable hash value requires immutable keys


- Dictionary keys must be immutable
    
- Because hash value must remain constant
    
- Mutable objects change → hash changes → dictionary breaks
    
- Lists cannot be keys
    
- Strings, ints, tuples can be keys