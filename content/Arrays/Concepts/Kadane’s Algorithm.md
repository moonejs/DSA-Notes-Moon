
>**Big -ve + Small +ve = -ve

If the sum of a subarray becomes negative, it will only reduce the sum of any future subarray — so we discard it.

`Agar add karne pe negative number a rha hai to isse acha 0 le lete hai`

so we will a run only one loop and track the Current sum(CS) and MaxSum(m)

![[Kadane's Algo(D)]]

```
currSum=max(nums[i],currSum+nums[i])
maxSum=max(currSum,maxSum)
```

---
or 
```
currSum += nums[i];
maxSum = max(currSum, maxSum);
if (currSum < 0) {
    currSum = 0;
}

```

[[Maximum Subarray]]
