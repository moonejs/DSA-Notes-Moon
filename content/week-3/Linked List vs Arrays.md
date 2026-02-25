
### What Is a Sequence?

>A **sequence** = ordered collection of values.

```
[10, 20, 30, 40]
```

there are **two basic ways to store sequences**


1. Lists
    
2. Arrays

If I ask you:

"How do we store a sequence inside a computer?"

What are the possible ways?

Think.

The computer only understands memory.

### Arrays

**Memory in Computer**

Computer memory is like a long row of boxes

Each box has an address.

![[Arrays-d-1.svg]]

An **array** stores elements:

> In contiguous (continuous) memory locations.

Because if we know:

- Starting address
    
- Size of each element
    

We can calculate the address of any element.

![[Pasted image 20260224112921.png]]
Arrays have a limitation:

They need **fixed size**.

When we create an array of size 4:

We reserve memory for exactly 4 elements.

If we want to insert one more element:

We cannot just expand easily.

We may need to:

- Allocate new bigger memory
    
- Copy all elements

![[Pasted image 20260224113014.png]]
![[Pasted image 20260224113035.png]]



![[Linked-List]]