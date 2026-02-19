***Notes By moon***

![[Binary-Search]]


### Binary_search using REcursion


```python
def binary_Search(v,l):
	if l==[]:
		return False
	mid=len(L)//2
	
	if l[mid]==v:
		return True
	
	if v<l[mid]:
		return binary_serach(v,l[:mid])
	else:
		return binary_search(v,l[mid+1:])
```


```python
def binary_search(v,L):
	start=0
	end=len(L)-1
	while(start<=end):
		mid=(start+end)//2	
		if L[mid]==v:
			return True
		elif v<L[mid]:
			end=mid-1
		else:
			start=mid+1
	return False
```


#### Important Python Detail

```python
L[:mid]
```

This creates a new list.

List slicing in Python costs time.

Copying k elements takes:

**O(k)**

First call:  
Copies n/2 elements.

Second call:  
Copies n/4 elements.

Third call:  
Copies n/8 elements.

Total copying work:

n/2+n/4+n/8+...n/2 + n/4 + n/8 + ...n/2+n/4+n/8+...

That sum equals:

n

So total slicing cost = O(n)

Recursive binary search in THIS form:

 O(n)  
(not O(log n)!)

Because slicing costs linear time overall.


#### Correct Efficient Version (Using Indices)

```python
def binary_search(L,v,start,end):
	if (start>end):
		return False
	mid=(start+end)//2
	
	if L[mid]==v:
		return True
	elfi v<L[mid]:
		return binary_search(L,v,start,mid-1)
	else:
		return binary_search(L,v,mid+1,end)
```


 


