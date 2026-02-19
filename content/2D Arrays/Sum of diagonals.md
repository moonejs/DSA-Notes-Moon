
https://leetcode.com/problems/matrix-diagonal-sum/description/

for primary diagonals we will calculate `i==j` 

for secondary diagonal we can find the pattern

and for that `i+j==n-1`

```java
class Solution {
    public int diagonalSum(int[][] mat) {
        int r=mat.length-1;
        int sum=0;
        for(int i =0 ;i<=r;i++){
            for(int j=0;j<=r;j++){
                if(j==i || j==(r-i)){
                    sum+=mat[i][j];
                }
            }
        }
        return sum;  
    }

}
```


**But we also have better solutions for it**

as we have square matrix so we can also run only one single loop

```java
class Solution {

    public int diagonalSum(int[][] mat) {
        int n=mat.length;
        int sum=0;
        for(int i =0 ;i<n;i++){
           sum+=mat[i][i];
           sum+=mat[i][n-1-i];
        }
        if(n%2==0){
            return sum;
        }
        return sum-mat[n/2][n/2];  

    }

}
```

