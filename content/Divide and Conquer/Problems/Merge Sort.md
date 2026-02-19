we will use **Divide and Conquer** Algo

![[Divide and Conquer]]
#### 1. Divide

>to divide we will find the mid and divide till we get the easiest problem to solve

>tab tak divide karenge jab sabse simple unit nahi a jati array ki

![[Divide and Conquer/Diagram/Merge Sort.md#^group=UFr5jFx8GEPZt9lHujHw6|100%]]

`mid = si+(ei-si)/2`

#### 2.

`mergeSort(left)`

`mergeSort(right)`

means somehow we will find the left sorted part and right sorted part

we will do this with the help of recursion

#### 3. Merge

then we will merge the left sorted part and right sorted part

we will make a temporary array to add sorted elements and then back copy into that particular array

Let's take a look 

![[Divide and Conquer/Diagram/Merge Sort.md#^group=P542YZzI8073qG5XtzbzR|100%]]

![[DSA/Divide and Conquer/Diagram/Merge Sort|Merge Sort]]


```java

class Solution {
    public void merge(int[] arr, int si, int mid, int ei){
        int [] temp = new int[ei - si + 1];
        int i = si;
        int j = mid + 1;
        int k = 0;

        while(i <= mid & j <= ei){
            if(arr[i] < arr[j]){
                temp[k] = arr[i++];
            } else {
                temp[k] = arr[j++];
            }
            k++;
        }

        while(i <= mid){
            temp[k++] = arr[i++];
        }
        while(j <= ei){
            temp[k++] = arr[j++];
        }

        for(int t = 0, s = si; t < temp.length; t++, s++){
            arr[s] = temp[t];
        }
    }

    public void mergeSort(int[] arr , int si , int ei){
        if(si >= ei){
            return;
        }
        int mid = si + ((ei - si) / 2);
        mergeSort(arr, si, mid);
        mergeSort(arr, mid + 1, ei);
        merge(arr, si, mid, ei);
    }

    public int[] sortArray(int[] nums) {
        mergeSort(nums, 0, nums.length - 1);
        return nums;
    }
}

public class MainClass {
    public static void main(String[] args) {
        Solution sol = new Solution();
        int[] nums = {5, 2, 3, 1};

        sol.sortArray(nums);

        for(int x : nums){
            System.out.print(x + " ");
        }
    }
}
```

Time complexity

- `O(nlog(n))`

space

- `O(n)`

![[Pasted image 20260216112541.png]]

```python
def merge(A,B):
    (m,n) = (len(A),len(B))
    (C,i,j,k) = ([],0,0,0)

    while k < m+n:

        if i == m:
            C.extend(B[j:])
            k = k + (n-j)

        elif j == n:
            C.extend(A[i:])
            k = k + (m-i)

        elif A[i] < B[j]:
            C.append(A[i])
            (i,k) = (i+1,k+1)

        else:
            C.append(B[j])
            (j,k) = (j+1,k+1)

    return(C)

```

![[Pasted image 20260216125411.png]]
![[Pasted image 20260216125427.png]]

![[Pasted image 20260216125438.png]]

![[Pasted image 20260216125453.png]]


![[Pasted image 20260216125506.png]]

![[Pasted image 20260216125525.png]]

![[Pasted image 20260216125548.png]]

![[Pasted image 20260216125600.png]]



For merge sort, total calls =

**2n−12n**

Important fact:

**Number of merge operations = number of internal nodes**

For merge sort:

Total merges = n - 1