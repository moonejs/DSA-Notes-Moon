we will use **Pivot and Partition**

![[Pivot & Partition]]



what we will do we will assign a variable `i=-1` it's only work is `to place the smallest element in the array then pivot it will only try to do that`

i will only update when `arr[i]<=pivot`
and swap the element 

something like that 

![[Quick Sort(D).svg]]

and we will repeat the same for left and right part 

```java
public void quickSort(int si, int ei, int[] arr) {
    if (si >= ei) {
        return;
    }

    int pivot = arr[ei];
    int i = si - 1;

    for (int j = si; j < ei; j++) {
        if (arr[j] <= pivot) {
            i++;
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }

    // place pivot at correct position
    i++;
    int temp = arr[i];
    arr[i] = arr[ei];
    arr[ei] = temp;

    quickSort(si, i - 1, arr);
    quickSort(i + 1, ei, arr);
}

```

My python version

```python
def quickSort(si,ei,arr):
	if si>=ei:
		return arr
	pivot = arr[ei]
	i=si-1
	for j in range(si,ei):
		if arr[j]<=pivot:
			i+=1
			arr[i], arr[j] = arr[j], arr[i]
	
	i+=1
	arr[i],arr[ei]=arr[ei],arr[i]
	
	quickSort(si,i-1,arr)
	quickSort(i+1,ei,arr)
	return arr
```



#### Time Complexity

Same as lecture:

Best case: O(n log n)  
Worst case: O(n²)  
Average: O(n log n)

![[Pasted image 20260223233803.png]]


What Costs Time in Quicksort?

>Partitioning with respect to the pivot takes O(n)

Because we scan the entire subarray once.

So each level of recursion costs **linear time**.

That part is clear.


#### Best Case Analysis

When does best case happen?

👉 When pivot is the **median**

That means:

- Left side = n/2 elements
    
- Right side = n/2 elements


![[Pasted image 20260223234753.png]]

#### Worst Case

Worst case happens when:

- Pivot is always **smallest** OR
    
- Pivot is always **largest**
    

Then partition sizes become:

- 0 elements
    
- n − 1 element


![[Pasted image 20260223234835.png]]
#### Average Case (This Is The Interesting Part)
![[Pasted image 20260223234915.png]]


![[Pasted image 20260223234933.png]]

|Case|Partition Split|Recurrence|Time|
|---|---|---|---|
|Best|Balanced|2T(n/2)+n|O(n log n)|
|Average|Random splits|Expected|O(n log n)|
|Worst|0 and n−1|T(n-1)+n|O(n²)|
Worst case depth = n  
Average depth = log n

That’s the real reason for the difference.