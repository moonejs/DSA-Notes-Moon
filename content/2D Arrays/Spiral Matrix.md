
https://leetcode.com/problems/spiral-matrix/description/

For this question we will maintain 4 variables

- `Top` ---- `starting Column`
- `Bottom` --- `ending Row`
- `left` ---- `starting row`
- `right` --- `ending Column`

and our whole 1 loop will end when we iterate

![[Spiral matrix.svg|40%]]


![[SprialMatrix-2.svg]]


we must have to take care about the edge cases

```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ans = new ArrayList<>();
        int sR=0;
        int eR=matrix.length-1;
        int sC=0;
        int eC=matrix[0].length-1;
        while(sR<=eR && sC<=eC){
            for(int j = sC;j<=eC;j++){
                ans.add(matrix[sR][j]);
            }
            sR++;
            for(int j = sR;j<=eR;j++){
                ans.add(matrix[j][eC]);
            }
            eC--;
            if(sR<=eR){
                for(int j = eC;j>=sC;j--){
                    ans.add(matrix[eR][j]);
                }
                eR--;
            }
            if(sC<=eC){
                for(int j = eR;j>=sR;j--){
                    ans.add(matrix[j][sC]);
                }
                sC++;
            }
        }
        return ans;
    }
}
```