
>just like cards we place a new incoming card in it's correct position in sorted cards

**Pick an element from unsorted part and insert it into the correct place in sorted part**


![[Insertion sort 1.svg]]

```java
for(int i=1;i<arr.length;i++){
	int curr=arr[i];
	int prev=i-1;
	while(prev>=0 && curr<arr[prev]){
		arr[prev+1]=arr[prev];
		prev--;
	}
	arr[prev+1]=curr;
	
}
```

```python
def insertionSort(arr):
	for i in range(1,len(arr)):
		curr=arr[i]
		prev=i-1
		while prev>=0 and curr<arr[prev]:
			arr[prev+1]=arr[prev]
			prev-=1
		arr[prev+1]=curr
	return L
```

We assume left side is already sorted.

This is called an **Invariant**.

Invariant means:

> Before each step, L[:i] is already sorted.

Then we insert L[i] in correct place.

##### Lecture code

```python
def InsertionSort(L):
    n = len(L)
    if n < 1:
        return(L)
    for i in range(n):
        j = i
        while(j > 0 and L[j] < L[j-1]):
            (L[j],L[j-1]) = (L[j-1],L[j])
            j = j-1
    return(L)

```

**Time Complexity**

Inner loop worst case:

- First element → 0 steps
    
- Second → 1 step
    
- Third → 2 steps
    
- ...
    
- nth → n-1 steps

`0 + 1 + 2 + ... + (n-1)
`
`n(n-1)/2
`
Which is:
`O(n²)
`

**Insertion Sort is NOT always O(n²)**

- If list is already sorted:

Condition `L[j] < L[j-1]` is FALSE immediately.

So inner loop runs 0 times.

Total time ≈ O(n)

 This is why insertion sort is very good for almost sorted lists.


| Feature                 | Selection | Insertion |
| ----------------------- | --------- | --------- |
| Worst Case              | O(n²)     | O(n²)     |
| Best Case               | O(n²)     | O(n)      |
| Good for nearly sorted? | ❌ No      | ✅ Yes     |