
https://leetcode.com/problems/search-a-2d-matrix/description/

### Brute force approach

`we will look for the target by going one by one to every index `

### approach 2

`we will apply binary search row wise`

then the time complexity will `nlog(n)`

### approach 3

#### Stair Case search


![[StairCase1.svg]]



These are the two **Amazing** positions because

Start from a corner where you can **eliminate one full row or column** in each step.

#### Algo

Step 1: Start at `(0, n-1)`

| Condition        | Action      | Why                  |
| ---------------- | ----------- | -------------------- |
| `current == key` | ✅ Found     | Done                 |
| `key < current`  | ⬅ Move left | All below are bigger |
| `key > current`  | ⬇ Move down | All left are smaller |

Suppose target is `33`

![[StarCase2.svg]]


```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int i = 0;
        int n=matrix.length;
        int j = matrix[0].length - 1;
        while(i<n && j>=0){
            int current = matrix[i][j];
            if(target<current){
                j--;
            }
            else if(target>current){
                i++;
            }
            else{
                return true;
            }
        }
        return false;
    }
}
```

