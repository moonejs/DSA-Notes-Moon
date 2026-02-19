
### Problem 
https://leetcode.com/problems/maximum-subarray/description/

### Brute Force Approach 

### 1.
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum=Integer.MIN_VALUE;
        for(int i=0;i<nums.length;i++){
	        for(int j=i;j<nums.length;j++){
		        int currSum=0;
		        for(int k=i;k<=j;k++){
			        currSum+=nums[k];
		        }
		        if(currSum>maxSum){
			        maxSum=currSum;
		        }
	        }
        }
        return maxSum;
    }

}

```

#### Time complexity
**Time Complexity = O(n³)**  
**Space Complexity = O(1)**
### 2.
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum=Integer.MIN_VALUE;
        for(int i=0;i<nums.length;i++){
	        int currSum=0;
	        for(int j=i;j<nums.length;j++){
		        currSum+=nums[j];
		        maxSum=Math.max(currSum,maxSum);
	        }
        }
        return maxSum;
    }

}
```

#### Time & Space Complexity

- **Time Complexity:** `O(n²)`
    
- **Space Complexity:** `O(1)`


### Prefix Sum 

[[Prefix Sum]]

To find the sum of a subarray from **index 2 to 4**:

```text
sum(2 → 4) = prefix[4] - prefix[1]
```

![[max sub array Prefix sum(D)]]

`prefix[4]` contains sum of elements from `0 → 4`

`prefix[1]` contains sum of elements from `0 → 1`

so we have to subtract `end - (start-1)`

```
sum(start → end) = prefix[end] - prefix[start - 1]
```

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int[] prefix=new int[nums.length];
        int maxSum=Integer.MIN_VALUE;
        prefix[0]=nums[0];
        for(int i=1;i<nums.length;i++){
            prefix[i]=nums[i]+prefix[i-1];
        }
        for(int i=0;i<nums.length;i++){
            int currSum=0;
            for(int j=i;j<nums.length;j++){
                if(i==0){
                    currSum=prefix[j];
                }
                else{
                    currSum=prefix[j]-prefix[i-1];
                }
                maxSum=Math.max(currSum,maxSum);
            }
        }
        return maxSum;

    }

}
```

#### Time & Space Complexity

- **Time Complexity:** `O(n²)`
    
- **Space Complexity:** `O(n)`


### Kadane's Algorithm 

![[Kadane’s Algorithm]]


```java
	class Solution {
    public int maxSubArray(int[] nums) {
        int currSum = 0;
        int maxSum = Integer.MIN_VALUE;
        for (int i = 0; i < nums.length; i++) {
            currSum += nums[i];
            maxSum = Math.max(currSum, maxSum);
            if (currSum < 0) {
                currSum = 0;
            }
        }
        return maxSum;

    }

}
```

---
or 
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int currSum=nums[0];
        int maxSum=nums[0];
        for(int i=1;i<nums.length;i++){
            currSum=Math.max(nums[i],currSum+nums[i]);
            maxSum=Math.max(currSum,maxSum);
        }
        return maxSum;
    }

}
```
