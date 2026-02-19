
> pick the smallest(from unsorted ), put it at the starting

then again 
we will pick the smallest from the remaining and put it after the first one means in sorted section

![[selection sort(D)#^group=-ayCdgeJDnevXcTQ5n6r_|50%]]

```java
for(int i=0;i<arr.length-1;i++){
	int min = i;
	for(int j=i+1;j<arr.length;j++){
		if(arr[j]<arr[min]){
			min=j;
		}
	}
	int temp=arr[i];
	arr[i]=arr[min];
	arr[min]=temp;
	
}
```



```python
def selectionSort(L):
	n=len(L)
	if n<1:
		return L
	
	for i in range(n):
		mn=i
		for j in range(i+1,n):
			if L[j]<L[mn]:
				mn=j;
		(L[i],L[mn])=(L[mn],l[i])
	return L	
```

![[Pasted image 20260214151328.png]]

Selection Sort is ALWAYS O(n²).

Even if:

- List already sorted
    
- List reverse sorted
    
- List random
    

It always scans the remaining list fully.

No early stopping.


>[!question]
>If n = 1000, Approximately how many comparisons will Selection Sort make?



![[Pasted image 20260214151644.png]]


|Situation|Formula|
|---|---|
|1 to n|n(n+1)/2|
|1 to n-1|n(n-1)/2|

>[!important]
>A sorting algorithm is **stable** if:

👉 **Equal elements keep their original relative order.**
