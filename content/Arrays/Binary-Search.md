> [!important]
> Binary Search works only on a **sorted array**.

### Intuition
###### **Dictionary Example**

- A dictionary is already **sorted alphabetically**
- If you want to search for **“Mango”**:
    - You don’t start from page 1
    - You open the **middle**
    - If the word is **before Mango**, go to the **Left half**
    - If it is **after Mango**, go to the **Right half**

  **Binary Search** is a  technique used to find an element in a **sorted array** by **repeatedly dividing the search space into half**.
### How It Works

We maintain **three pointers**:

- `start` → beginning of array
    
- `end` → last index of array
    
- `mid` → middle element

At each step:
- Compare the **key** with `arr[mid]`
- Decide which **half to keep**
- Discard the other half
### Pseudocode

```text
start=0
end=n-1

while(start<=end){
	mid=(start+end)/2
	if(key==arr[mid]){
		return mid
	}
	elif (key<arr[mid]){
		end=mid-1
	}
	else{
		start=mid+1
	}
	
}
```



![[Binary Search (D).svg]]

### Code

```java

int binarySearch (int [] arr,int key){
	int start=0;
	int end=arr.length-1;
	while(start<=end){
		int mid=(start+end)/2;
		if(key<arr[mid]){
			end=mid-1;
		}
		else if(key>arr[mid]){
			start=mid+1;
		}
		else{
			return mid;
		}
	}
	return -1;
}
```
## Time & Space Complexity
- Best case: O(1)
- Average case: O(log n)
- Worst case: O(log n)
- Space complexity: O(1)